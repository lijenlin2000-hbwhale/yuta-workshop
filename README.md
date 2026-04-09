# 猶他大師 — 傳承者的試煉 AI 素養工作坊
# Yuta Master — Trials of the Inheritors AI Literacy Workshop

> 一個為偏鄉國中小學生設計的兩天 AI 素養工作坊，結合 TRPG 敘事、骨牌不插電活動，以及自建 AI agent 介面。  
> A two-day AI literacy workshop for rural elementary and middle school students, combining TRPG narrative, unplugged domino activities, and a custom AI agent interface.

---

## 目錄 / Table of Contents

- [工作坊簡介 / Workshop Overview](#工作坊簡介--workshop-overview)
- [教學設計理念 / Pedagogical Philosophy](#教學設計理念--pedagogical-philosophy)
- [技術架構 / Technical Architecture](#技術架構--technical-architecture)
- [快速開始 / Quick Start](#快速開始--quick-start)
- [檔案說明 / File Reference](#檔案說明--file-reference)
- [現場操作指引 / On-site Operation Guide](#現場操作指引--on-site-operation-guide)
- [客製化與延伸 / Customization & Extension](#客製化與延伸--customization--extension)
- [授權與引用 / License & Attribution](#授權與引用--license--attribution)

---

## 工作坊簡介 / Workshop Overview

**傳承者的試煉**是一個以 TRPG 為敘事主線的兩天 AI 素養工作坊，目標對象為國小高年級與國中生。核心理念是：**讓孩子成為擁有在地知識的專家，而不是被 AI 教導的學習者。**

**Trials of the Inheritors** is a two-day AI literacy workshop built around a TRPG narrative arc, designed for upper elementary and middle school students. The core premise: **children are the experts with irreplaceable local knowledge — the AI needs them, not the other way around.**

### 猶他大師 / Yuta Master

工作坊的 AI 角色「猶他大師」是一位知識淵博的古老智者，但**刻意缺乏在地文化智慧**。這個設計讓孩子成為補足 AI 知識空缺的人，建立主體感與批判距離。

The AI character "Yuta Master" is an ancient sage with vast knowledge, but **deliberately lacks local cultural wisdom**. This design positions children as the ones filling the AI's knowledge gaps — building agency and critical distance.

### 五大金律 / Five Golden Rules

貫穿兩天活動，引導孩子與 AI 協作的行為準則：

The five principles guiding children's AI collaboration throughout the workshop:

1. **它是工具，不是人** — It's a tool, not a person
2. **大膽懷疑，小心求證** — Question boldly, verify carefully
3. **覺得怪怪的，就去查** — When something feels off, check it
4. **我是神秘客** — I'm an anonymous user (never share personal info)
5. **我是機長，它是副手** — I'm the pilot; it's the co-pilot

---

## 教學設計理念 / Pedagogical Philosophy

### 道德直覺三支柱 / Three Pillars of Moral Intuition

本工作坊的道德教育不依賴規則宣講，而是透過故事與體驗建立**直覺**。

This workshop builds **moral intuition** through story and experience — not through rules and lectures.

| 支柱 / Pillar | 機制 / Mechanism | 操作重點 / Key Design |
|---|---|---|
| 身份錨定 / Identity Anchoring | 行為是身份的投影 | 讓孩子認同「傳承者」身份，再連結道德選擇 |
| 道德美學 / Moral Aesthetics | 用美感取代對錯 | 不說「這樣做是錯的」，說「這樣做很遜」 |
| 誘惑測試 / Temptation Testing | 無監控時刻的自我主宰 | 讓孩子體驗守住原則後的自我肯定感 |

### 不插電優先 / Unplugged First

骨牌活動在 AI 介入前建立概念基礎，避免角色混淆，加深意義。四個任務層次：  
Pattern Recognition → Problem Solving → Computational Thinking → Creative Integration

Domino activities establish conceptual grounding *before* the AI is introduced — preventing role confusion and deepening meaning. Four task levels:  
Pattern Recognition → Problem Solving → Computational Thinking → Creative Integration

---

## 技術架構 / Technical Architecture

```
GitHub Pages (靜態部署 / Static hosting)
│
├── yuta_student.html     學生端介面 / Student interface
├── yuta_teacher.html     老師儀表板 / Teacher dashboard
└── [yuta_qrcode.html]    QR code 頁面，本機生成，不上傳 / QR page, local only
         │
         ├── Anthropic API (claude-sonnet-4-20250514)
         │   各組對話獨立串接 / Per-group independent sessions
         │
         └── Firebase Realtime Database (Singapore)
             即時同步 / Real-time sync across devices
```

### 設計原則 / Design Principles

- **無帳號架構**：學生不需要個人帳號，掃 QR code 直接進入選組頁面
- **API key 即密碼**：base64 編碼的 API key 作為課堂通關密語，兼顧安全與易用
- **刻意限制為教學工具**：猶他大師的知識空缺、無跨 session 記憶，都是設計選擇，不是技術缺陷

- **No-account architecture**: Students need no personal accounts — scan QR code, select group, done
- **API key as password**: base64-encoded API key doubles as the classroom passphrase
- **Intentional limitations as pedagogy**: Yuta's knowledge gaps and lack of cross-session memory are design choices, not bugs

---

## 快速開始 / Quick Start

### 前置需求 / Prerequisites

- Anthropic API key（[申請 / Apply](https://console.anthropic.com/)）
- Firebase 專案（免費方案即可 / Free tier sufficient）
- GitHub 帳號（用於 Pages 部署 / for Pages deployment）

### 部署步驟 / Deployment Steps

**1. Fork 或 Clone 此 repo**

```bash
git clone https://github.com/lijenlin2000-hbwhale/yuta-workshop.git
cd yuta-workshop
```

**2. 設定 Firebase / Configure Firebase**

在 [Firebase Console](https://console.firebase.google.com/) 建立新專案，啟用 Realtime Database（選 Singapore 節點）。

Create a new project in Firebase Console, enable Realtime Database (select Singapore region).

將 Firebase config 填入 `yuta_student.html` 與 `yuta_teacher.html` 對應位置：

Fill in your Firebase config in both HTML files:

```javascript
const firebaseConfig = {
  apiKey: "your-firebase-api-key",
  authDomain: "your-project.firebaseapp.com",
  databaseURL: "https://your-project-default-rtdb.asia-southeast1.firebasedatabase.app",
  projectId: "your-project-id",
  // ...
};
```

> **注意 / Note**：Firebase config 公開於程式碼中屬正常設計，以 Database Rules 控管權限即可。  
> Firebase config being public in code is by design — control access via Database Rules instead.

**3. 設定 Database Rules / Set Database Rules**

```json
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
```

> 正式活動前可依需求收緊規則。/ Tighten rules before production use if needed.

**4. 部署至 GitHub Pages / Deploy to GitHub Pages**

推送至 `main` branch，在 repo Settings → Pages 選擇 `main` branch 部署。

Push to `main` branch, then go to repo Settings → Pages and select `main` branch.

**5. 本機產生 QR code 頁面 / Generate QR page locally**

以文字編輯器開啟 `yuta_qrcode_template.html`，填入你的 API key，存為 `yuta_qrcode.html`，**本機列印後刪除，不上傳 GitHub**。

Open `yuta_qrcode_template.html` in a text editor, fill in your API key, save as `yuta_qrcode.html`, **print locally and delete — do not push to GitHub**.

**6. 測試 / Test**

用三台裝置模擬現場：電腦開老師儀表板，兩台行動裝置各選不同組，測試對話同步、廣播、暫停功能。

Use three devices to simulate the classroom: computer as teacher dashboard, two mobile devices each selecting a different group. Test chat sync, broadcast, and pause functions.

---

## 檔案說明 / File Reference

| 檔案 / File | 說明 / Description | 是否上傳 GitHub / Push to GitHub |
|---|---|---|
| `yuta_student.html` | 學生端對話介面 / Student chat interface | ✅ 是 / Yes |
| `yuta_teacher.html` | 老師即時監控儀表板 / Teacher monitoring dashboard | ✅ 是 / Yes |
| `yuta_qrcode_template.html` | QR code 頁面範本（不含 key）/ QR page template (no key) | ✅ 是 / Yes |
| `yuta_qrcode.html` | 含 API key 的 QR 頁面，本機生成 / QR page with key, local only | ❌ 否 / No |

---

## 現場操作指引 / On-site Operation Guide

### 開場前 / Before the Session

1. 老師端開啟儀表板，確認 Firebase 連線（右側活動紀錄出現 heartbeat）
2. 列印 QR code 頁面，分組張貼或統一展示
3. 確認所有平板能正常掃碼進入選組頁面

1. Open the teacher dashboard, confirm Firebase connection (check activity log on the right)
2. Print the QR code page; post by group or display centrally
3. Confirm all tablets can scan and reach the group selection page

### 課程中 / During the Session

| 功能 / Function | 操作 / Action |
|---|---|
| 觀察各組對話 | 儀表板各格即時顯示，無需切換 |
| 全體廣播 | 右側輸入訊息 → 發送廣播 |
| 暫停所有組 | 點「⏸ 暫停所有組」，學生端輸入框鎖住 |
| 標記值得跟進的組 | 點各組旗標按鈕（純備忘，不影響學生端）|
| 清除所有對話 | 點「清除所有對話」→ 確認（活動段落結束時使用）|

### 誘惑測試環節 / Temptation Test Segment

老師離開小組範圍時，透過儀表板遠端觀察各組與猶他大師的互動。發現值得課後討論的對話時，標記旗標備忘。**猶他大師設計上不主動介入道德判斷**，只在孩子主動提問時回應，且只問一個問題，讓對話停在孩子身上。

When the teacher steps away from the groups, monitor via dashboard remotely. Flag groups with notable conversations for post-activity discussion. **Yuta is designed not to proactively intervene in moral decisions** — it only responds when children ask, and asks only one question to keep the conversation centered on the child.

---

## 客製化與延伸 / Customization & Extension

### 修改猶他大師的個性 / Modifying Yuta's Personality

系統提示詞位於 `yuta_student.html` 頂端的 `YUTA_SYSTEM_PROMPT` 變數。建議保留以下核心設定：

The system prompt is in the `YUTA_SYSTEM_PROMPT` variable at the top of `yuta_student.html`. Preserve these core elements:

- 缺乏在地知識的設定（讓孩子成為專家）/ Lack of local knowledge (makes children the experts)
- 無跨 session 記憶（體驗 AI 的真實限制）/ No cross-session memory (experiencing real AI limitations)
- 道德選擇時只問一個問題 / Ask only one question during moral choices

### 調整組數 / Adjusting Group Count

預設八組。修改 `yuta_student.html` 中的 `MAX_GROUPS` 常數，並同步更新 `yuta_teacher.html` 的儀表板格數。

Default is eight groups. Modify `MAX_GROUPS` in `yuta_student.html` and update the dashboard grid in `yuta_teacher.html` accordingly.

### 快速提問按鈕 / Quick Prompt Buttons

學生端四個快速提問按鈕對應四個核心教學限制。可在 `yuta_student.html` 的 `QUICK_PROMPTS` 陣列中修改按鈕文字與對應提問內容。

The four quick prompt buttons correspond to four core teaching limitations. Modify button text and prompt content in the `QUICK_PROMPTS` array in `yuta_student.html`.

---

## 授權與引用 / License & Attribution

本專案採 [MIT License](LICENSE) 授權，歡迎種子教師與研究者自由使用、修改、再散布。  
若引用於學術或教育推廣用途，請標註原始設計來源。

This project is licensed under the [MIT License](LICENSE). Seed teachers and researchers are welcome to use, adapt, and redistribute freely.  
If cited in academic or educational outreach contexts, please credit the original design.

---

**設計 / Designed by** Lijen  
**在地協作 / Local Partner** 國盛（抱抱熊學堂）  
**道德框架 / Ethical Framework** 三支柱道德直覺框架  祐平
**AI 倫理參考 / AI Ethics Reference** Google《Teaching Responsible AI》，在地化轉化

---

*「它知道很多，但它不知道骨牌倒下的聲音有多美。那個，只有你知道。」*  
*"It knows a lot — but it doesn't know how beautiful the sound of falling dominoes is. Only you know that."*
