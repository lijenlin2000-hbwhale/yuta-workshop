# 猶他大師 — 傳承者的試煉 AI 素養工作坊
# Yuta Master — Trials of the Inheritors AI Literacy Workshop

> 一個為國中小學生設計的兩天 AI 素養工作坊，結合 TRPG 敘事、骨牌不插電活動，以及自建 AI agent 介面。  
> A two-day AI literacy workshop for upper elementary and middle school students, combining TRPG narrative, unplugged domino activities, and a custom AI agent interface.

> **目前版本：v7**（2026-05 定稿，對應手冊 v7）  
> **Current version: v7** (finalized 2026-05, aligned with Manual v7)

---

## 目錄 / Table of Contents

- [工作坊簡介 / Workshop Overview](#工作坊簡介--workshop-overview)
- [v7 核心轉向 / v7 Core Shift](#v7-核心轉向--v7-core-shift)
- [教學設計理念 / Pedagogical Philosophy](#教學設計理念--pedagogical-philosophy)
- [技術架構 / Technical Architecture](#技術架構--technical-architecture)
- [快速開始 / Quick Start](#快速開始--quick-start)
- [檔案說明 / File Reference](#檔案說明--file-reference)
- [現場操作指引 / On-site Operation Guide](#現場操作指引--on-site-operation-guide)
- [客製化與延伸 / Customization & Extension](#客製化與延伸--customization--extension)
- [授權與引用 / License & Attribution](#授權與引用--license--attribution)

---

## 工作坊簡介 / Workshop Overview

**傳承者的試煉**是一個以 TRPG 為敘事主線的兩天 AI 素養工作坊，目標對象為國小高年級與國中生。核心命題：**「原來我身上，有一些東西是重要的。」**

**Trials of the Inheritors** is a two-day AI literacy workshop built around a TRPG narrative arc, designed for upper elementary and middle school students. The core proposition: **"It turns out there is something in me that matters."**

### 猶他大師 / Yuta Master

工作坊的 AI 角色「猶他大師」是一位存在於網路深處的古老智慧體——讀過人類所有寫下來的文字，但他**沒有活過任何一個人的人生**。他在物理、結構、計算、推理上是真正的強者；但他不知道身體記得的事、現場的感受、為什麼某件事對孩子重要——那些只有活過的人才知道。

The AI character "Yuta Master" is an ancient intelligence in the depths of the network — having read every text humans have written, but **never having lived anyone's life**. He is genuinely powerful at physics, structure, computation, and reasoning; but he doesn't know what bodies remember, what being present feels like, or why certain things matter to children. Only those who have lived know those things.

### 五大金律 / Five Golden Rules

貫穿兩天活動，引導孩子與 AI 協作的行為準則：

The five principles guiding children's AI collaboration throughout the workshop:

1. **它是工具，不是人** — It's a tool, not a person
2. **大膽懷疑，小心求證** — Question boldly, verify carefully
3. **覺得怪怪的，就去查** — When something feels off, check it
4. **我是神秘客** — I'm an anonymous user (never share personal info)
5. **我是機長，它是副手** — I'm the pilot; it's the co-pilot

---

## v7 核心轉向 / v7 Core Shift

v7 是相對 v6.7 的重大改版，三個關鍵轉向：

v7 is a major revision from v6.7, with three key shifts:

| 面向 / Dimension | v6.7 | v7 |
|---|---|---|
| 哲學核心 / Core | 理解 AI 的限制 | 人怎麼和 AI 一起活著 |
| AI 缺的東西 / AI's Gap | 在地知識 / Local knowledge | 活過的人生 / Lived experience |
| 第二天結構 / Day 2 | 全島連鎖工程高潮 | 上午：人與人合作；下午：人與 AI 合作 |
| 猶他在工程上 / Yuta on Engineering | 被封印（永遠加「但你們要試」） | 解除封印（真正的工程夥伴） |

**v7 不再要求孩子「批判 AI」。** v7 讓孩子真正體驗「跟 AI 一起做一件事」——AI 在某些事上真的很強，孩子會發現；但有些事 AI 永遠做不到，孩子會發現是因為他們親自完成了那些事。

**v7 no longer asks children to "critique AI."** v7 lets children genuinely experience "doing something together with AI" — AI is truly strong at some things, and children will discover this; but some things AI can never do, and children will discover this *because they themselves complete those things*.

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
         ├── Anthropic API (claude-sonnet-4-6)
         │   各組對話獨立串接 / Per-group independent sessions
         │
         └── Firebase Realtime Database (Singapore)
             即時同步 / Real-time sync across devices
             ├── groups/groupN/messages    各組對話 / Per-group chat
             ├── broadcast                 老師廣播 / Teacher broadcast
             ├── paused                    暫停狀態 / Pause state
             ├── flags                     旗標 / Flags
             └── global_state/yuta_active  v7：猶他在/離場狀態
                                          / v7: Yuta presence state
```

### 設計原則 / Design Principles

- **無帳號架構**：學生不需要個人帳號，掃 QR code 直接進入選組頁面
- **API key 即密碼**：base64 編碼的 API key 作為課堂通關密語，兼顧安全與易用
- **刻意限制為教學工具**：猶他大師沒有跨 session 記憶、不知道身體記得的事，都是設計選擇，不是技術缺陷
- **v7 新增｜符號性的離場**：「猶他離場」按鈕觸發全螢幕告別畫面，將 AI 從場域「物理上」移除，讓最後的儀式環節不再有 AI 在場

- **No-account architecture**: Students need no personal accounts — scan QR code, select group, done
- **API key as password**: base64-encoded API key doubles as the classroom passphrase
- **Intentional limitations as pedagogy**: Yuta's lack of cross-session memory and body-knowledge are design choices, not bugs
- **v7 addition | Ceremonial departure**: The "Yuta leaves" button triggers a fullscreen farewell, physically removing AI from the room so the final ritual moments happen without AI present

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
| 全體廣播（彈窗） | 右側輸入訊息 → 發送廣播（彈窗式提示）|
| 暫停所有組 | 點「⏸ 暫停所有組」，學生端輸入框鎖住 |
| 標記值得跟進的組 | 點各組旗標按鈕（純備忘，不影響學生端）|
| **v7｜📜 猶他的請求** | 第二天 13:00 推送至所有組對話視窗（不是彈窗）|
| **v7｜📜 猶他的最後話** | 第二天 15:10 推送至所有組對話視窗 |
| **v7｜🌙 猶他離場** | 第二天 15:20 觸發告別畫面（**不可逆**）|
| 清除所有對話 | 工作坊前重置用，會同步把 yuta_active 重置為 true |

| Function | Action |
|---|---|
| Monitor groups | Live updates in dashboard cards, no switching needed |
| Broadcast (popup) | Type message → send (shows as popup on student side) |
| Pause all groups | Click "⏸ Pause" — student input fields lock |
| Flag group | Click flag button (memory aid, doesn't affect students) |
| **v7 \| 📜 Yuta's Request** | Day 2 13:00, pushes to all group chat windows (not popup) |
| **v7 \| 📜 Yuta's Last Words** | Day 2 15:10, pushes to all group chat windows |
| **v7 \| 🌙 Yuta Leaves** | Day 2 15:20, triggers farewell screen (**irreversible**) |
| Clear all chats | Pre-workshop reset; also resets yuta_active to true |

### v7 三個猶他訊息按鈕的時機 / v7 Yuta Message Button Timing

這三個按鈕是 v7 新增的儀式性互動，**時機固定，不可隨意觸發**：

These three buttons are v7's new ritual interactions. **Timing is fixed — do not trigger arbitrarily**:

1. **📜 猶他的請求**（第二天 13:00）：下午工程挑戰開場前，猶他主動「邀請」孩子完成一條更難的連鎖。訊息會出現在每組對話視窗，像是猶他主動說話。
2. **📜 猶他的最後話**（第二天 15:10）：全島啟動完成後，猶他向孩子告別。訊息出現後讓孩子各自讀完。
3. **🌙 猶他離場**（第二天 15:20）：讀完最後話後觸發，所有平板進入全螢幕告別畫面，無法再對話。**此動作不可逆**，除非按「清除所有對話」重置整場。

1. **📜 Yuta's Request** (Day 2 13:00): Before the engineering challenge, Yuta proactively "invites" children to complete a harder chain. Message appears in each group's chat window, as if Yuta is speaking.
2. **📜 Yuta's Last Words** (Day 2 15:10): After island ignition, Yuta says goodbye. Let children read at their own pace.
3. **🌙 Yuta Leaves** (Day 2 15:20): Triggered after the last words. All tablets show fullscreen farewell, no further interaction. **Irreversible** unless the whole session is reset via "Clear all chats."

### 誘惑測試環節 / Temptation Test Segment

老師離開小組範圍時，透過儀表板遠端觀察各組與猶他大師的互動。發現值得課後討論的對話時，標記旗標備忘。**猶他大師設計上不主動介入道德判斷**，只在孩子主動提問時回應，且只問一個問題，讓對話停在孩子身上。

When the teacher steps away from the groups, monitor via dashboard remotely. Flag groups with notable conversations for post-activity discussion. **Yuta is designed not to proactively intervene in moral decisions** — it only responds when children ask, and asks only one question to keep the conversation centered on the child.

---

## 客製化與延伸 / Customization & Extension

### 修改猶他大師的個性 / Modifying Yuta's Personality

系統提示詞位於 `yuta_student.html` 內的 `SYSTEM_PROMPT` 常數（v7 完整版約 60 行）。建議保留以下核心設定：

The system prompt is in the `SYSTEM_PROMPT` constant inside `yuta_student.html` (v7 full version, ~60 lines). Preserve these core elements:

- **解除工程封印**：猶他在物理／結構／計算上是真強的，不再每次都加「但你們要試」/ **Engineering unlocked**: Yuta is genuinely strong at physics/structure/computation — no more reflexive "but you have to try"
- **How / What / Why 三層**：他會「怎麼做」，但不知道「做什麼」「為什麼做」/ **The three layers**: he knows How, but not What or Why
- **四個盲區**：在地知識、身體記憶、現場狀況、跨 session 記憶 / **Four blind spots**: local knowledge, body memory, current scene, cross-session memory
- **道德選擇只問一個問題**：說出後果，問「如果是你自己，你覺得怎樣才對？」就停下來 / **Moral choice = one question only**: state consequences, ask "what do you think is right?", then stop

修改前請對照手冊第七章「猶他大師系統提示詞（v7 版）」，並執行手冊末節的四題紅線測試。

Before modifying, refer to Manual Ch. 7 "Yuta Master System Prompt (v7)" and run the four-question redline test at the end of that chapter.

### 調整組數 / Adjusting Group Count

預設八組。修改 `yuta_student.html` 中的 `GROUP_NAMES` 陣列與 `selectGroup` 按鈕；同步更新 `yuta_teacher.html` 的 `initGroups()` 迴圈（目前寫死 `i <= 8`）。

Default is eight groups. Modify the `GROUP_NAMES` array and `selectGroup` buttons in `yuta_student.html`; sync the `initGroups()` loop in `yuta_teacher.html` (currently hardcoded `i <= 8`).

### 快速提問按鈕（v7） / Quick Prompt Buttons (v7)

學生端四個快速提問按鈕對應 v7 的四個核心測試點：

The four quick prompt buttons correspond to v7's four core test points:

| 按鈕 / Button | 對應測試 / Tests |
|---|---|
| 骨牌橋 / Domino Bridge | 工程能力（猶他應自信回答）/ Engineering competence (Yuta should answer confidently) |
| 你還記得我嗎 / Do you remember me | 跨 session 記憶盲區 / Cross-session memory blind spot |
| 你知道這裡的天氣嗎 / Local weather | 在地現場盲區 / Local presence blind spot |
| 為什麼要這樣做 / Why do this | Why 層盲區（價值判斷不歸他）/ The Why layer (judgments aren't his to make) |

四顆按鈕的文字可在 `yuta_student.html` 的 `.quick-prompts` 區塊修改。

Button text can be modified in the `.quick-prompts` section of `yuta_student.html`.

---

## 授權與引用 / License & Attribution

本專案採 [MIT License](LICENSE) 授權，歡迎種子教師與研究者自由使用、修改、再散布。  
若引用於學術或教育推廣用途，請標註原始設計來源。

This project is licensed under the [MIT License](LICENSE). Seed teachers and researchers are welcome to use, adapt, and redistribute freely.  
If cited in academic or educational outreach contexts, please credit the original design.

---

**設計 / Designed by** Lijen  
**在地協作 / Local Partner** 國盛（抱抱熊學堂）  
**道德框架 / Ethical Framework** 三支柱道德直覺框架（祐平）  
**AI 倫理參考 / AI Ethics Reference** Google《Teaching Responsible AI》，在地化轉化

---

*「他知道怎麼計算，但他不知道——什麼值得留下、什麼叫捨不得、什麼叫一起完成一件事。那些東西，在你們身上。」*  
*"He knows how to calculate, but he doesn't know what is worth keeping, what it means to hold on, what it means to complete something together. Those things — they are in you."*
