<div align="center">

# Agent Collaboration Protocol (ACP) 🤝

<img src="assets/logo.jpg" width="400" alt="ACP Logo">

**The Universal State Layer for Multi-Agent Coordination.**
**AI Agent 的通用狀態層：打破平台壁壘的協作協議。**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Platform: Hermes](https://img.shields.io/badge/Platform-Hermes-blue)](https://github.com/cheerhuan)
[![Platform: OpenClaw](https://img.shields.io/badge/Platform-OpenClaw-green)](https://github.com/cheerhuan)

</div>

---

## 📌 Table of Contents | 目錄
- [💡 Core Concept | 核心概念](#-the-core-concept--核心概念)
- [🛠️ How It Works | 運作機制](#-how-it-works--運作機制)
- [🚀 Integration | 整合指南](#-integration--整合指南)
- [📄 License | 授權](#-license)

---

## 💡 Core Concept | 核心概念

### ⚠️ The Problem: Context Fragmentation | 痛點：上下文碎片化
When switching between different AI platforms (e.g., from **Hermes** to **OpenClaw** or **Claude Code**), you lose the "mental state" of the previous agent. You are forced to re-explain the context, wasting both time and tokens.

當您在不同的 AI 平台之間切換（例如從 **Hermes** 切換到 **OpenClaw** 或 **Claude Code**）時，前一個 Agent 的「思考狀態」會隨之消失。您必須重新解釋背景資訊，這不僅浪費時間，更極其浪費 Token。

### ✅ The Solution: A "Shared Brain" via File System | 方案：基於檔案系統的「共享大腦」
ACP doesn't try to build a complex API bridge. Instead, it leverages the one thing every AI agent can do: **Read and Write local files.**

ACP 不嘗試建立複雜的 API 橋接。相反，它利用所有 AI Agent 共同擁有的唯一能力：**讀寫本地檔案。**

By defining a standardized `.acp/` directory, we create a **Universal State Layer** that exists *outside* any specific platform. The file system becomes the "Save Game" file for your project—any agent can "load" the state and resume exactly where the last one left off.

透過定義標準化的 `.acp/` 目錄，我們建立了一個**獨立於平台之外的「通用狀態層」**。檔案系統變成了您專案的「遊戲存檔」——任何 Agent 只要載入此狀態，就能在前任 Agent 停止的地方精準接手。

---

## 🛠️ How It Works | 運作機制

ACP converts "Chat Memory" into "Structured Assets":
ACP 將不穩定的「對話記憶」轉化為「結構化資產」：

| Component | Purpose | 說明 |
| :--- | :--- | :--- |
| **Task Contract** | **The North Star** | Located in `.acp/contracts/`. Ensures that regardless of the platform, the goal never drifts. <br> 位於 `.acp/contracts/`。確保無論切換到哪個平台，目標永遠不會偏移。 |
| **Handoff Snapshot** | **The Relay Baton** | Located in `.acp/handoffs/`. A high-density snapshot of where the last agent stopped and why. <br> 位於 `.acp/handoffs/`。記錄前任 Agent 停止的位置與原因的高密度快照。 |
| **PAE Loop** | **The Safety Guard** | **Plan $\rightarrow$ Approve $\rightarrow$ Execute**. Mandates a user-approved plan before any execution to prevent hallucination loops. <br> **計畫 $\rightarrow$ 審核 $\rightarrow$ 執行**。強制要求在執行前必須經過用戶審核，防止 AI 幻覺迴路。 |

---

## 🚀 Integration | 整合指南

### 📦 For Hermes Agent
Load the `agent-collaboration-protocol` skill. Hermes will act as the **Coordinator**, managing the `.acp/` layer and ensuring all handoffs are documented.
載入 `agent-collaboration-protocol` 技能。Hermes 將扮演 **協調者 (Coordinator)**，管理 `.acp/` 層並確保所有交接都被記錄。

### 📦 For OpenClaw / Other Agents
Since they can't "load a skill," simply give them the **Universal Instruction**:
由於其他 Agent 無法「載入技能」，請直接給予 **通用指令**：

> **"Act as an ACP-compliant agent. Your shared memory is located in `.acp/`. Before starting, read the latest handoff in `.acp/handoffs/` and the contract in `.acp/contracts/`. Update the handoff file before you exit."**
> **「請作為一個符合 ACP 協議的 Agent 運行。你的共享記憶位於 `.acp/` 目錄中。開始前，請讀取 `.acp/handoffs/` 中的最新快照與 `.acp/contracts/` 中的契約。在退出前，請更新交接檔案。」**

---

## 📄 License | 授權
MIT License.
MIT 授權。
