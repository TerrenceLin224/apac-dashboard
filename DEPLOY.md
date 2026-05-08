# APAC Dashboard — GitHub Pages 部署說明

## 你會得到的網址格式
`https://你的帳號.github.io/apac-dashboard/`

---

## 第一次部署（約 15 分鐘，只需做一次）

### 步驟 1：建立 GitHub 帳號
前往 https://github.com 註冊帳號（如已有帳號跳過）

### 步驟 2：建立新 Repository
1. 登入後點右上角 **+** → **New repository**
2. Repository name 填入：`apac-dashboard`
3. 選擇 **Public**（GitHub Pages 免費方案需為 Public）
4. 勾選 **Add a README file**
5. 點 **Create repository**

### 步驟 3：上傳檔案
1. 進入剛建立的 repository 頁面
2. 點 **Add file** → **Upload files**
3. 將以下兩個檔案拖曳上傳：
   - `index.html`
   - `data.json`
4. 在下方 Commit changes 輸入說明（例如：`Initial upload`）
5. 點 **Commit changes**

### 步驟 4：開啟 GitHub Pages
1. 點上方 **Settings** 分頁
2. 左側選單找到 **Pages**
3. Source 選擇 **Deploy from a branch**
4. Branch 選 **main**，資料夾選 **/ (root)**
5. 點 **Save**

### 步驟 5：取得網址
等約 1–2 分鐘後，頁面上會出現：
> Your site is live at `https://你的帳號.github.io/apac-dashboard/`

複製這個網址，在任何設備的瀏覽器開啟即可。

---

## 日常更新流程（每次開會後，約 3–5 分鐘）

### 方式 A：透過 GitHub 網頁編輯（最簡單）
1. 登入 GitHub，進入 `apac-dashboard` repository
2. 點 `data.json` 檔案
3. 點右上角鉛筆圖示（Edit this file）
4. 將 Claude 提供的更新內容貼上對應位置
5. 點 **Commit changes** → **Commit changes**
6. 等約 30 秒，網頁自動更新

### 方式 B：下載修改後重新上傳
1. 下載 `data.json` 到本機
2. 用文字編輯器修改
3. 重新上傳覆蓋

---

## 每次更新的工作流程

```
開完 APAC 例會
    ↓
把會議紀錄貼給 Claude
    ↓
Claude 解析後輸出需更新的 data.json 欄位
    ↓
你複製貼上到 GitHub data.json
    ↓
Commit → 30 秒後網頁自動更新
    ↓
所有設備（手機/電腦/平板）同步看到最新內容
```

---

## data.json 結構說明

### 更新會議資訊 (meta)
```json
"meta": {
  "last_updated": "2026-05-06",   ← 每次更新改這個日期
  "gp_rate": 0.257,               ← GP Rate，如有變動再改
  ...
}
```

### 更新業務 Pipeline 數字
```json
{
  "name": "Chloe",
  "pipeline_rev_usd": 587548,   ← 改這個數字
  ...
}
```

### 更新活動看板 (Activity Board)
每個區域的 activity 欄位，item 格式如下：
```json
"presales": [
  {
    "level": "r",              ← r=紅(緊急)  y=黃(進行中)  g=綠(完成)
    "text": "TaiPost RS50 Reboot",
    "sub": "Current Issue"     ← 副標題，可不填（刪除這行即可）
  }
]
```

### 更新 HR 狀況
```json
"hr": "ITI 人才媒合面試 x10 · 5/17 · 初試 x2"
```

### 更新季度業績數字
```json
"performance": {
  "annual_gp_target": 900444,
  "q_shipped": 85000,          ← 已出貨金額
  "q_pending": 45000,          ← 待出貨金額
  "gm_estimated": 0.257,       ← 預估毛利率
  "gm_last_month": 0.261       ← 上月實際毛利率
}
```

---

## 常見問題

**Q: 網頁顯示「無法載入 data.json」？**
A: 確認 `index.html` 和 `data.json` 在同一個資料夾（repository root），且 GitHub Pages 已啟用。

**Q: 更新後網頁沒有變化？**
A: 等待 30–60 秒後強制重新整理（Ctrl+Shift+R 或 Cmd+Shift+R）。

**Q: 手機上可以看嗎？**
A: 可以，Dashboard 支援 RWD，手機瀏覽器直接開啟網址即可。

**Q: 可以分享給上層看嗎？**
A: 可以，直接傳網址即可。任何人都可以開啟，不需要登入。如需密碼保護，需升級 GitHub 方案或改用其他服務。
