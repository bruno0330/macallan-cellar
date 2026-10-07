# 麥卡倫藏酒帳｜交接說明

## 專案現況
- 公開網站：https://bruno0330.github.io/macallan-cellar/（GitHub Pages，main 分支根目錄）
- repo：bruno0330/macallan-cellar（Public）
- 私人可編輯版：claude.ai Artifact「麥卡倫藏酒帳」（資料存在 Artifact 資料庫，可新增／修改／上傳照片）
- 收藏：18 瓶麥卡倫，總值約 NT$138,109，帳面 +3.5%（2026-10-06 行情）

## 檔案
- `index.html`：主網站。資料以 `window.__DATA` 內嵌，照片改為外部檔案路徑（見下）。GitHub 版為唯讀。
- `data.json`：同一份資料，方便閱讀與更新。
- `imgs/`：18 瓶酒的官方商品圖（`{id}.jpg` 或 `{id}.png`），非使用者實拍照。

## 資料欄位（每瓶）
id, name, series, spec, buyDate, buyPrice(NT$), mktGBP(國際拍賣落槌 £), mktTWD(台灣行情 NT$，可空), twSrc(台灣行情來源),
hkBuy(香港回收 HK$), cnBuy(大陸批發 ¥), gLow/gHigh(年漲幅 %), potential(high/mid/low), conf(high/mid/low), note,
img(官方圖相對路徑，如 `imgs/boutique2017.jpg`), imgSrc(圖片來源標註，如「The Macallan 官方網站」「Master of Malt」)
meta：fx(£→NT$)、hkd、cny、premium=1.15、landed=1.3、updated、fxDate

## 估值規則
- 市值＝mktTWD（台灣酒商最低售價）；若空，則 mktGBP × fx × 1.3（佣金＋運費稅費）
- mktGBP 的查價方式（2026-10 起）：優先找「目前買得到的最低零售現價」（Master of Malt／whiskybase／官網等，不分國家，換算成英鎊直接填入，不額外打折）；真的找不到在賣的才退回拍賣落槌價估算。兩種來源都會在該瓶 `note` 欄位寫清楚是零售價還是拍賣價、查核日期。
- 國際參考＝mktGBP × fx × 1.15（此欄位沿用舊公式，即使 mktGBP 來源改為零售價也一樣算）
- 港陸回收價只做對照，不計入總市值
- Harmony 系列年漲幅已下修為 −3%～+4%（大陸通路價全面低於定價）

## 設計（v3，已與使用者確認）
- 基底：蘋果產品頁風＋iPhone 股市 App 風；預設深色、支援淺色；暖棕底色＋金色細框／分隔線＋襯線展示字體（New York / Noto Serif TC），取代原本純黑灰的科技感
- 開場：全版封面（市值最高酒款的官方圖，視差滾動效果）＋固定標語「Macallan收藏窖」（不帶瓶數，避免瓶數變動要維護文案）
- 總值區：置中大字總值（琥珀漸層＋數字滾動進場）、四格數字卡
- 重點酒款：挑市值前 3 瓶，大圖＋故事卡（備註文字）＋價格／漲跌，左右交錯排版，取代原本橫滑卡片
- 未來價值圖：1/3/5 年切換、手指滑動查看各年預估
- 系列分布、收藏清單（照片＋名稱＋市值＋漲跌膠囊，可依市值／漲幅／最新排序、系列篩選）維持不變
- 點酒款開底部詳情頁：大圖、價格對照條、1/3/5 年預估、評估、備註、圖片來源標註
- 全頁疊一層極淡顆粒紋理（noise overlay），減少「數位模板」的乾淨感
- 酒款照片改用官方商品圖（The Macallan 官方網站／Master of Malt 等），不再用使用者實拍照；每張圖都標註來源，因為 repo 是 Public、網站公開可存取，需注意品牌圖片的版權／商標考量

## 使用者偏好
- 全程繁體中文；逐步確認對焦；提供 4–5 個選項並附最佳建議；一次只問一題；精簡額度
- 修改前先確認設計，再 push

## 待辦（可選）
- 頂部分段切換（總覽／收藏／分析）
- 定期更新行情（建議每季）：查 Just Whisky／Scotch Whisky Auctions 落槌價、FindPrice 台灣售價，更新 data 後重建 index.html
- 香港回收價待使用者詢價後填入
- 新增酒款時：到 The Macallan 官網／Master of Malt 等正規來源找官方商品圖存進 `imgs/{id}.jpg`，並在 data 的 `imgSrc` 填來源標註（使用者陸續會買新酒，不用使用者自己拍照）
