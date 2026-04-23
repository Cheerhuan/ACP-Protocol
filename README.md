<div align="center">
  <img src="assets/logo.jpg" width="400" alt="ACP Logo">
  <h1>Agent Collaboration Protocol (ACP)</h1>
  <p><b>A token-efficient, cross-platform standard for multi-agent coordination.</b></p>
  <p><b>一套極致省 Token 的跨平台多 Agent 協作標準協議。</b></p>
</div>

---

## 📖 Overview / 概述

**Agent Collaboration Protocol (ACP)** is a standardized framework designed to eliminate "context loss" and "token waste" when transitioning tasks between different AI agents (e.g., Hermes $\rightarrow$ OpenClaw $\rightarrow$ Claude Code). 

**Agent Collaboration Protocol (ACP)** 是一套標準化框架，旨在解決多 AI Agent（如 Hermes $\rightarrow$ OpenClaw $\rightarrow$ Claude Code）在任務交接時常見的「上下文遺失」與「Token 浪費」問題。

Instead of relying on volatile chat histories, ACP treats the **local file system as the "Single Source of Truth"**, using structured Markdown files to maintain state and contracts.

ACP 不再依賴不穩定的對話紀錄，而是將 **「本地文件系統」視為唯一事實來源 (Single Source of Truth)**，透過結構化的 Markdown 檔案來維護狀態與契約。

---

## 🚀 Quick Start / 快速開始

### 1. Initialize the Protocol / 初始化協議
Create the `.acp` directory at your project root:
在專案根目錄建立 `.acp` 目錄：

```bash
mkdir -p .acp/{contracts,handoffs,memory}
```

### 2. Usage Workflow / 使用流程
- **Start a Task**: Create a contract in `.acp/contracts/task-name.md`.
- **Begin Task**: 建立任務契約於 `.acp/contracts/task-name.md`。
- **Hand off**: When switching agents, generate a snapshot in `.acp/handoffs/task-id.md`.
- **交接任務**: 切換 Agent 時，在 `.acp/handoffs/task-id.md` 生成狀態快照。

---

## 🛠️ Core Mechanisms / 核心機制

### 🤝 Handoff Workflow / 交接工作流
To prevent Agent B from asking "What was Agent A doing?", Agent A must leave a **Handoff File**:
為了防止 Agent B 詢問「Agent A 剛才在做什麼？」，Agent A 必須留下 **交接檔案**：

| Field / 欄位 | Description / 描述 |
| :--- | :--- |
| **Status / 狀態** | [Pending \| Blocked \| Completed] |
| **Context / 上下文** | Minimal essential facts required to resume. / 恢復工作所需的最小必要事實。 |
| **Last Action / 最後動作** | Exactly what was just executed. / 剛才執行了什麼。 |
| **Next Step / 下一步** | Explicit first action for the next agent. / 給下一個 Agent 的明確首個動作。 |

### 📝 Task Contract / 任務契約
Before any complex implementation, a **Contract** must be signed:
在進行任何複雜實作前，必須簽署 **契約**：
- **Objective / 目標**: Clear one-sentence goal. / 明確的一句話目標。
- **Constraints / 約束**: Hard limits (e.g., "No new libs"). / 硬性限制（例如：「禁止新增庫」）。
- **DoD (Definition of Done) / 完成定義**: A checklist of verifiable outcomes. / 可驗證的結果清單。

### 🔄 PAE Loop / 計畫-審核-執行迴路
To maximize token efficiency and accuracy:
為了極大化 Token 效率與準確度：
1. **Plan (計畫)** $\rightarrow$ Agent proposes a `plan.md`.
2. **Approve (審核)** $\rightarrow$ User reviews and signs off.
3. **Execute (執行)** $\rightarrow$ Agent implements the approved plan.

---

## 🌍 Cross-Platform Integration / 跨平台整合

### For Hermes Agent
Load the `agent-collaboration-protocol` skill. Hermes will automatically manage the `.acp/` directory.
載入 `agent-collaboration-protocol` 技能。Hermes 將自動管理 `.acp/` 目錄。

### For OpenClaw / Other Agents
Add the following to your System Prompt:
將以下內容加入 System Prompt：
> "Follow the Agent Collaboration Protocol (ACP). Read `.acp/contracts/` for goals and `.acp/handoffs/` for current state before starting. Update handoff files before terminating the session."
> 「請遵循 Agent Collaboration Protocol (ACP)。在開始前讀取 `.acp/contracts/` 的目標與 `.acp/handoffs/` 的狀態。在結束會話前更新交接檔案。」

---

## 📄 License / 授權
MIT License.
