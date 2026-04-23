<div align="center">
  <img src="assets/logo.jpg" width="400" alt="ACP Logo">
  <h1>Agent Collaboration Protocol (ACP)</h1>
  <p><b>The Universal State Layer for Multi-Agent Coordination</b></p>
  <p><b>AI Agent 的通用狀態層：打破平台壁壘的協作協議</b></p>
</div>

---

## 💡 The Core Concept / 核心概念

### The Problem: Context Fragmentation / 痛點：上下文碎片化
When switching between different AI platforms (e.g., from **Hermes** to **OpenClaw** or **Claude Code**), you lose the "mental state" of the previous agent. You are forced to re-explain the context, wasting both time and tokens.

當您在不同的 AI 平台之間切換（例如從 **Hermes** 切換到 **OpenClaw** 或 **Claude Code**）時，前一個 Agent 的「思考狀態」會隨之消失。您必須重新解釋背景資訊，這不僅浪費時間，更極其浪費 Token。

### The Solution: A "Shared Brain" via File System / 方案：基於檔案系統的「共享大腦」
ACP doesn't try to build a complex API bridge. Instead, it leverages the one thing every AI agent can do: **Read and Write local files.**

ACP 不嘗試建立複雜的 API 橋接。相反，它利用所有 AI Agent 共同擁有的唯一能力：**讀寫本地檔案。**

By defining a standardized `.acp/` directory, we create a **Universal State Layer** that exists *outside* any specific platform. The file system becomes the "Save Game" file for your project—any agent can "load" the state and resume exactly where the last one left off.

透過定義標準化的 `.acp/` 目錄，我們建立了一個**獨立於平台之外的「通用狀態層」**。檔案系統變成了您專案的「遊戲存檔」——任何 Agent 只要載入此狀態，就能在前任 Agent 停止的地方精準接手。

---

## 🛠️ How It Works / 運作機制

ACP converts "Chat Memory" into "Structured Assets":
ACP 將不穩定的「對話記憶」轉化為「結構化資產」：

### 1. $\text{Task Contract} \rightarrow$ The North Star / 任務契約 $\rightarrow$ 指路明燈
**Location**: `.acp/contracts/`
Instead of a vague prompt, agents agree on a **Contract** (Objective $\rightarrow$ Constraints $\rightarrow$ Definition of Done). This ensures that regardless of the platform, the goal never drifts.
不再使用模糊的提示詞，Agent 必須簽署**契約**（目標 $\rightarrow$ 約束 $\rightarrow$ 完成定義）。這確保了無論切換到哪個平台，目標永遠不會偏移。

### 2. $\text{Handoff Snapshot} \rightarrow$ The Relay Baton / 交接快照 $\rightarrow$ 接力棒
**Location**: `.acp/handoffs/`
Before a session ends, the current agent writes a **Handoff File**. It's a high-density snapshot: *"Here is where I stopped, here is why I stopped, and here is the very first thing you should do."*
在會話結束前，當前 Agent 必須撰寫**交接檔案**。這是一個高密度的狀態快照：*「我在這裡停止，停止的原因是 X，而你接手後的第一件事應該是 Y。」*

### 3. $\text{PAE Loop} \rightarrow$ The Safety Guard / PAE 迴路 $\rightarrow$ 安全護欄
**Plan $\rightarrow$ Approve $\rightarrow$ Execute**
To prevent "AI hallucination loops" during cross-platform handoffs, the protocol mandates a user-approved plan before any execution.
為了防止跨平台交接時出現「AI 幻覺迴路」，協議強制要求在執行前必須經過用戶審核的計畫。

---

## 🚀 Integration / 整合指南

### For Hermes Agent
Load the `agent-collaboration-protocol` skill. Hermes will act as the **Coordinator**, managing the `.acp/` layer and ensuring all handoffs are documented.
載入 `agent-collaboration-protocol` 技能。Hermes 將扮演 **協調者 (Coordinator)**，管理 `.acp/` 層並確保所有交接都被記錄。

### For OpenClaw / Other Agents
Since they can't "load a skill," simply give them the **Universal Instruction**:
由於其他 Agent 無法「載入技能」，請直接給予 **通用指令**：
> "Act as an ACP-compliant agent. Your shared memory is located in `.acp/`. Before starting, read the latest handoff in `.acp/handoffs/` and the contract in `.acp/contracts/`. Update the handoff file before you exit."
> 「請作為一個符合 ACP 協議的 Agent 運行。你的共享記憶位於 `.acp/` 目錄中。開始前，請讀取 `.acp/handoffs/` 中的最新快照與 `.acp/contracts/` 中的契約。在退出前，請更新交接檔案。」

---

## 📄 License
MIT License.
