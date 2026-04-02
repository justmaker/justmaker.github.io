---
title: "2026 AI 平台調研：哪些平台支援完全自訂 Agent？"
description: "從雲端平台到開源框架，評估 13 個支援逐行撰寫 agent 邏輯的 AI 平台，附比較表、Top 5 推薦與選擇建議。"
date: 2026-04-02
slug: custom-agent-platforms-2026
categories:
  - ai-tools
tags:
  - agent
  - langgraph
  - pydantic-ai
  - crewai
  - mastra
  - ai-framework
---

## 前言

「完全自訂 Agent」是什麼意思？不是在 GUI 上拖拉 prompt template，而是**逐行撰寫 agent 邏輯**——決定什麼時候呼叫哪個工具、怎麼處理結果、失敗了怎麼重試、哪些行為絕對不允許。

這篇調研針對 2025–2026 年市面上的 AI 平台，找出哪些真正支援這件事。

---

## 平台比較表

| 平台 | 自訂程度 | 語言 | 自訂 Tools | Multi-Agent | State 管理 | 部署 | 定價 | 成熟度 |
|---|---|---|---|---|---|---|---|---|
| **LangGraph** | ⭐⭐⭐⭐⭐ | Python, JS/TS | ✅ | ✅ | ✅ Checkpointing + 記憶 | Self-hosted / Cloud | MIT；LangSmith 按量 | ✅ Production |
| **AutoGen (Microsoft)** | ⭐⭐⭐⭐⭐ | Python | ✅ | ✅ 核心就是 multi-agent | ✅ 對話歷史 | Self-hosted / Azure | MIT | ✅ Production |
| **Semantic Kernel** | ⭐⭐⭐⭐⭐ | Python, C#, Java | ✅ Plugin 系統 | ✅ | ✅ Memory store | Self-hosted / Azure | MIT | ✅ Production |
| **Pydantic AI** | ⭐⭐⭐⭐⭐ | Python | ✅ decorator 即 tool | ⚠️ 基本支援 | ⚠️ 手動管理 | Self-hosted | MIT | ✅ Production |
| **Mastra** | ⭐⭐⭐⭐⭐ | TypeScript | ✅ | ✅ | ✅ 內建 memory + RAG | Self-hosted / Node | Apache 2.0 | ✅ Production |
| **CrewAI** | ⭐⭐⭐⭐ | Python | ✅ | ✅ Crew 協作 | ✅ | Self-hosted / Cloud | MIT；Cloud 按量 | ✅ Production |
| **smolagents** | ⭐⭐⭐⭐ | Python | ✅ | ✅ | ⚠️ 基本 | Self-hosted | Apache 2.0 | 🔬 Experimental |
| **AWS Bedrock Agents** | ⭐⭐⭐ | 任何 Lambda 語言 | ✅ Lambda functions | ⚠️ 有限 | ✅ Session state | Cloud (AWS) | 按用量 | ✅ Production |
| **Google Vertex AI ADK** | ⭐⭐⭐⭐ | Python | ✅ | ✅ | ✅ Session + memory | Cloud (GCP) | 按用量 | ✅ Production |
| **Azure AI Agent Service** | ⭐⭐⭐⭐ | Python, C# | ✅ | ✅ SK 整合 | ✅ Thread-based | Cloud (Azure) | 按用量 | ✅ Production |
| **Salesforce Agentforce** | ⭐⭐ | Apex | ✅ Apex actions | ⚠️ 有限 | ✅ CRM 內建 | Cloud (Salesforce) | 企業授權 $2/conv | ✅ CRM 場景 |
| **ServiceNow AI Agents** | ⭐⭐ | JS (ServiceNow) | ✅ Scripted REST | ⚠️ 有限 | ✅ 平台內建 | Cloud (ServiceNow) | 企業授權 | ✅ ITSM 場景 |
| **OpenClaw** | ⭐⭐⭐⭐⭐ | TypeScript / Shell | ✅ MCP tools | ✅ Subagent spawn | ✅ Memory files | Self-hosted | 開源 | ✅ Production |

---

## Top 5 推薦

### 🥇 LangGraph

業界事實標準的 low-level agent 框架。以**有向圖（graph）** 為核心抽象，每個節點都是你自己寫的函式。

**核心優勢：**
- **Durable execution**：agent 中途失敗可從 checkpoint 恢復，不用重跑
- **Human-in-the-loop**：可在任何節點暫停讓人類介入、審核、修改 state
- **完整記憶**：短期 working memory + 跨 session 的長期記憶
- Python + JavaScript 雙語言

**適合：** 需要 durable execution、複雜多步驟 workflow、需要 human approval 的場景

```python
from langgraph.graph import StateGraph, END

def agent_node(state):
    # 你的自訂邏輯，完全掌控
    ...

def safety_guard(state):
    # 硬規則：在 code 裡攔截，LLM 繞不過
    if state["action"] == "delete" and state["target"].startswith("prod"):
        return {**state, "blocked": True}
    return state

graph = StateGraph(AgentState)
graph.add_node("agent", agent_node)
graph.add_node("guard", safety_guard)
graph.add_node("execute", execute_node)
graph.add_edge("agent", "guard")
graph.add_conditional_edges("guard", lambda s: "blocked" if s.get("blocked") else "execute")
```

---

### 🥈 Semantic Kernel (Microsoft)

三語言支援（Python / C# / Java）是業界獨一無二的優勢，Plugin 系統讓 tool 定義極其靈活。

**核心優勢：**
- **三語言**：後端 .NET 團隊終於有了一流選擇
- **Filter/Hook 系統**：`IFunctionInvocationFilter` 可以在任何 function call 前後插入 validation
- **深度 Azure 整合**，但不綁定 Azure
- 適合企業級合規場景

**適合：** 企業 .NET/Java 開發團隊、需要與 Azure 生態整合

---

### 🥉 Pydantic AI

最 Pythonic 的 agent 框架。**「讓 AI 開發獲得 FastAPI 的感覺」** 是它的設計目標。

**核心優勢：**
- **沒有多餘抽象**：用 `@agent.tool` decorator 定義 tool，用 Pydantic model 定義輸出結構
- **Result validator**：可以攔截、驗證任何 LLM 輸出，不符規則就重試
- **Type-safe**：型別錯誤在執行期自動 raise，不靠 LLM 自覺
- **Model-agnostic**：支援 40+ provider，包含 Anthropic、OpenAI、GitHub Models

```python
from pydantic_ai import Agent
from pydantic import BaseModel

class JiraResolve(BaseModel):
    fix_version: str      # 少一個欄位 → ValidationError → 自動重試
    build_number: str
    build_path: str
    root_cause: str
    solution: str

agent = Agent('anthropic:claude-sonnet-4-6', result_type=JiraResolve)

@agent.tool
async def get_build_info(ctx, issue_key: str) -> str:
    # 你自己寫的邏輯，不是 prompt
    ...

@agent.result_validator
async def validate(ctx, result: JiraResolve) -> JiraResolve:
    if not result.build_path.startswith(r"\\172.17.25.251"):
        raise ValueError("Build path 格式錯誤")  # ← Code 強制，不是 prompt
    return result
```

**適合：** Python 開發者、想要最小框架 overhead、重視型別安全

---

### 4. Mastra

TypeScript 生態目前最成熟的 agent 框架，由 Gatsby 原始團隊開發，YC W25。

**核心優勢：**
- **TypeScript-native**：型別推導、IDE 智能提示全程支援
- **40+ provider model routing**：一個介面換任何 LLM
- **內建 memory + RAG**：不用自己串 vector store
- **Workflow 系統**：複雜的 multi-step pipeline 用 code 定義每個步驟
- 可無縫整合 React / Next.js

```typescript
import { Agent } from '@mastra/core/agent';

export const myAgent = new Agent({
  id: 'my-agent',
  name: 'My Custom Agent',
  instructions: 'You are a specialized assistant for...',
  model: 'anthropic/claude-sonnet-4-6',
  tools: { myCustomTool },  // 完全自訂 tool
});
```

**適合：** TypeScript 開發者、前後端整合場景

---

### 5. CrewAI

Multi-agent 協作做得最好，Flows 系統提供 event-driven 的細粒度控制。

**核心優勢：**
- **10 萬+ 認證開發者**，社群資源豐富
- **Flows**：event-driven、狀態機式的 agent 協作，可精確控制每一步
- **Crews**：定義角色（researcher、writer、reviewer）自動協作
- **CrewAI Cloud**：一鍵部署

**適合：** Multi-agent 角色扮演、需要自動分工的複雜任務

---

## 關鍵洞察：Prompt 是建議，Code 是法律

這是選擇 agent 框架最重要的認知：

```
❌ 把規則放在 system prompt / AGENTS.md / memory 文件
   → LLM 可能忽略、context window 滿了沒載入、長對話後被沖淡

✅ 把規則寫進 agent code（tool validation、result validator、guard node）
   → 不管 LLM 怎麼想，code 就是不讓它過
```

**哪些規則應該放 code？**
- 不允許刪除 production 資源
- 必填欄位強制驗證
- 只允許操作特定範圍的資源（例如指定 Confluence space）
- Git 推送前驗證帳號身份
- 公開平台不能出現特定關鍵字

**哪些規則放 prompt 就夠？**
- 回覆語言偏好（繁體中文）
- 回覆風格與長度
- 格式要求（如超連結格式）

---

## 給開發者的選擇建議

| 你的情況 | 推薦方向 |
|---|---|
| Python 開發者，要逐行控制 agent | **Pydantic AI**（最少抽象）或 **LangGraph**（複雜場景） |
| TypeScript 開發者 | **Mastra** |
| 企業 .NET / Java 團隊 | **Semantic Kernel** |
| 需要 multi-agent 角色協作 | **CrewAI** |
| 需要 durable execution、長時間任務 | **LangGraph** |
| 已在用雲端平台（AWS / GCP / Azure） | 對應的 agent service，但 agent logic 建議用純框架寫再部署 |
| CRM / ITSM 整合場景 | Salesforce Agentforce / ServiceNow（但自訂程度有限） |

**核心建議：避開 no-code agent builder，選擇 code-first 框架。** 2025–2026 的 agent 框架已經足夠 production-ready，開源選項完全可用。真正的控制權在於能不能在 code 層面定義 agent 行為，而不是靠 prompt 希望 AI 自覺遵守規則。
