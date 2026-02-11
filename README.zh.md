[English](README.md) | [繁體中文](README.zh.md)

# NotebookLM Mentor

一個 Claude Code 技能，作為 Google NotebookLM 的自我進化導師 — 提供有根據的功能指引、工作流程和最佳實踐，同時從互動中持續學習。

## 功能特色

NotebookLM Mentor 回答問題並指導 NotebookLM 各方面的任務：

| 請求類型 | 處理方式 |
|---|---|
| 基本操作 | 從內建核心知識回答（建立、上傳、對話） |
| 功能問題 | 查閱參考文件（語音摘要、工作室、分享） |
| 進階 / 邊界情況 | 搜尋網路取得最新資訊，再回答 |
| 實作任務 | 逐步指導，可搭配 Playwright 操作瀏覽器 |

**核心設計原則：** 如同 NotebookLM 本身，此導師以經過驗證的知識為基礎。不確定時會先搜尋、引用來源，並記錄新知以持續進步。

### 自我進化記憶

每次互動中發現的新資訊（UI 變更、功能更新、解決方案）都會自動記錄。未來的回答會運用所有累積的知識。

## 安裝

1. 將此倉庫 clone 到 Claude 技能目錄：

   ```bash
   git clone https://github.com/joneshong-skills/notebookllm-mentor.git ~/.claude/skills/notebookllm-mentor
   ```

2. 前置需求：
   - 網路搜尋功能（用於驗證最新功能和定價）
   - Playwright MCP 伺服器（可選，用於實際瀏覽器操作指導）

3. 當您詢問 NotebookLM 的用法、功能或最佳實踐，或使用觸發詞如「NotebookLM 怎麼用」、「幫我用 NotebookLM」等時，技能會自動啟動。

## 使用方式

直接自然地詢問 Claude。範例：

- *「NotebookLM 的語音摘要怎麼建立？」*
- *「免費方案的來源數量上限是多少？」*
- *「幫我建立一個筆記本來整理研究論文」*
- *「NotebookLM 裡多個主題要怎麼組織比較好？」*

## 專案結構

```
notebookllm-mentor/
├── SKILL.md                        # 技能定義、工作流程及核心知識
├── README.md                       # 英文說明
├── README.zh.md                    # 繁體中文說明（本檔案）
├── references/
│   └── features.md                 # 詳細功能參考（工作室、語音摘要、分享）
└── memory/
    └── learnings.md                # 從過去互動累積的知識
```

## 授權

MIT
