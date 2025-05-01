---
title: "Conventional Commits 筆記"
date: "2025-05-01T15:32:00+08:00"
tags: ["commit","git"]
#title_images: ["/photo1.png", "/photo2.png",]
#ending_images: ["/photo3.png", "/photo4.png", "/photo5.png",]
author: "holla"
slug: "conventional_commits"
draft: false
---

## 筆記：學會 Conventional Commits，讓 Git 提交訊息變整齊

最近翻 Git 紀錄，發現自己以前的提交訊息亂七八糟，像是「改了點東西」這種，真的看不懂自己在幹嘛。😅 在朋友提醒下看到 **Conventional Commits** 這招，超簡單，能讓訊息變整齊，還能跟工具串起來。來記下重點，免得忘！

### 這是啥？

就是一套約好的提交訊息格式，長這樣：

```
<類型>[可選範圍]: <描述>

[可選正文]

[可選腳註]
```

- **類型**：這次提交是幹啥，比如 `feat`（加新東西）、`fix`（修 Bug）。
- **範圍**：改了哪塊，比如 `api`、`ui`（可以不寫）。
- **描述**：一句話說清楚做了啥。
- **正文**：想多記點細節就放這。
- **腳註**：記大事，比如關 Issue。

試個範例：

```
feat(api): add user signup endpoint

Added POST /signup API and updated docs.
Closes #15
```

### 常用的類型

- `feat`：新功能
- `fix`：修 Bug
- `docs`：改文件
- `style`：調格式，不影響程式
- `refactor`：整理程式碼
- `test`：加測試
- `chore`：雜事（像更新套件）

### 為啥想用？

- 訊息整齊，看起來舒服，翻紀錄不頭痛。
- 能跟工具串連，自動弄變更日誌，省時間。
- 馬上知道每次提交在搞啥，不用猜。

### 怎麼搞？

1. 去 [官方網站](https://www.conventionalcommits.org/) 瞄一下，簡單到不行。
2. 試試工具：
   - **Commitizen**：幫忙一步步寫訊息。
   - **Semantic Release**：自動整理更新紀錄。
3. 跟團隊聊聊，乾脆大家都用這套。

### 提醒自己

- 描述短點，50 字內最好。
- 國際專案用英文，比較統一。
- 大改動記得寫 `BREAKING CHANGE`，像 `BREAKING CHANGE: drop old API`。

### 感想

這招真的不難，感覺像幫 Git 提交訊息整理房間，以後紀錄乾淨又清楚。個人專案先試試，之後推給團隊，應該能讓大家少翻點白眼。😂 繼續練起來！