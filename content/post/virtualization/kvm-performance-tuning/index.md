---
title: "KVM 虛擬機效能調校指南"
description: "從 CPU pinning 到 virtio 優化，實戰 KVM 虛擬機效能調校技巧"
date: 2025-04-03
slug: kvm-performance-tuning
categories:
  - virtualization
tags:
  - kvm
  - qemu
  - 效能調校
  - 教學
---

## 前言

KVM 虛擬機的預設設定通常不是最佳效能。透過一些調校，可以讓 VM 跑得更快、更穩。

這篇整理我實際工作中用過的效能調校技巧。

## 1. CPU 優化

### CPU Pinning

預設情況下，vCPU 可以在任何 pCPU 上執行，這會導致 cache miss 和 NUMA 問題。

```xml
<!-- libvirt XML 設定 -->
<vcpu placement='static'>4</vcpu>
<cputune>
  <vcpupin vcpu='0' cpuset='2'/>
  <vcpupin vcpu='1' cpuset='3'/>
  <vcpupin vcpu='2' cpuset='4'/>
  <vcpupin vcpu='3' cpuset='5'/>
</cputune>
```

原則：
- **避免使用 CPU 0**（留給 host）
- **同一 NUMA node** 的 CPU 分配給同一 VM
- 查看 NUMA topology：`lscpu | grep NUMA` 或 `numactl --hardware`

### CPU 模式

```xml
<!-- 使用 host-passthrough 取得最佳 CPU 指令集支援 -->
<cpu mode='host-passthrough' check='none' migratable='on'/>
```

`host-passthrough` 直接暴露 host CPU 特性給 VM，效能最好但會影響 live migration 相容性。

## 2. 記憶體優化

### Hugepages

預設 4KB page 在大量記憶體時 TLB miss 嚴重。用 2MB hugepage 可以大幅改善：

```bash
# Host 設定 hugepages（例如分配 4GB = 2048 個 2MB pages）
echo 2048 > /proc/sys/vm/nr_hugepages

# 永久設定
echo "vm.nr_hugepages=2048" >> /etc/sysctl.conf
```

```xml
<!-- libvirt XML -->
<memoryBacking>
  <hugepages/>
</memoryBacking>
```

### NUMA Aware Memory

```xml
<numatune>
  <memory mode='strict' nodeset='0'/>
</numatune>
```

確保 VM 記憶體分配在對應的 NUMA node 上。

## 3. 儲存 I/O 優化

### virtio-blk vs virtio-scsi

| 特性 | virtio-blk | virtio-scsi |
|------|-----------|-------------|
| 效能 | 略快 | 接近 |
| 功能 | 基本 | SCSI 命令、multi-queue |
| Discard/TRIM | 支援 | 支援 |
| 熱插拔 | 有限 | 完整 |

一般用途用 `virtio-blk`，需要進階 SCSI 功能用 `virtio-scsi`。

### I/O Thread

```xml
<iothreads>2</iothreads>
<disk type='file' device='disk'>
  <driver name='qemu' type='qcow2' cache='none' io='native' ioeventfd='on'/>
  <source file='/path/to/disk.qcow2'/>
  <target dev='vda' bus='virtio'/>
  <iotune>
    <iothread>1</iothread>
  </iotune>
</disk>
```

### Cache 模式

| 模式 | 安全性 | 效能 | 適用場景 |
|------|--------|------|---------|
| `none` | ✅ 高 | ✅ 好 | **推薦** — Host cache bypass |
| `writethrough` | ✅ 高 | ❌ 慢 | 資料安全優先 |
| `writeback` | ❌ 低 | ✅ 快 | 測試環境 |
| `directsync` | ✅ 高 | ❌ 最慢 | 極端安全需求 |

## 4. 網路優化

### virtio-net + vhost-net

```xml
<interface type='bridge'>
  <source bridge='br0'/>
  <model type='virtio'/>
  <driver name='vhost' queues='4'/>
</interface>
```

`vhost-net` 把部分網路處理移到 kernel space，減少 context switch。

### Multi-queue

多 queue 可以利用多核心平行處理網路封包：

```xml
<driver name='vhost' queues='4'/>
```

VM 內部也要啟用：
```bash
ethtool -L eth0 combined 4
```

## 5. 實測參考數據

以下是典型 KVM 調校前後的效能差異（僅供參考）：

| 項目 | 調校前 | 調校後 | 提升 |
|------|--------|--------|------|
| sysbench CPU | 1200 events/s | 1450 events/s | +21% |
| fio 隨機讀 IOPS | 45K | 62K | +38% |
| iperf3 網路 | 8.2 Gbps | 9.4 Gbps | +15% |

## 總結

KVM 效能調校的核心原則：

1. **減少共享**：CPU pinning、NUMA 對齊
2. **減少開銷**：hugepages、vhost-net、io=native
3. **用 virtio**：不要模擬傳統硬體
4. **量測為王**：每個調校都要實測驗證

下一篇會講 GPU Passthrough 的設定。
