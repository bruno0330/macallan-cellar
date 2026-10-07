# 麥卡倫藏酒帳｜交接說明

## 專案現況
- 公開網站：https://bruno0330.github.io/macallan-cellar/（GitHub Pages，main 分支根目錄）
- repo：bruno0330/macallan-cellar（Public）
- 私人可編輯版：claude.ai Artifact「麥卡倫藏酒帳」（資料存在 Artifact 資料庫，可新增／修改／上傳照片）
- 收藏：18 瓶麥卡倫，總值約 NT$138,109，帳面 +3.5%（2026-10-06 行情）

## 檔案
- `index.html`：單一檔案網站。資料與照片以 `window.__DATA` 內嵌（照片為 JPEG data URI）。GitHub 版為唯讀。
- `data.json`：同一份資料（不含照片），方便閱讀與更新。

## 資料欄位（每瓶）
id, name, series, spec, buyDate, buyPrice(NT$), mktGBP(國際拍賣落槌 £), mktTWD(台灣行情 NT$，可空), twSrc(台灣行情來源),
hkBuy(香港回收 HK$), cnBuy(大陸批發 ¥), gLow/gHigh(年漲幅 %), potential(high/mid/low), conf(high/mid/low), note, img
meta：fx(£→NT$)、hkd、cny、premium=1.15、landed=1.3、updated、fxDate

## 估值規則
- 市值＝mktTWD（台灣酒商最低售價）；若空，則 mktGBP × fx × 1.3（佣金＋運費稅費）
- 國際參考＝mktGBP × fx × 1.15
- 港陸回收價只做對照，不計入總市值
- Harmony 系列年漲幅已下修為 −3%～+4%（大陸通路價全面低於定價）

## 設計（已與使用者確認）
- 蘋果產品頁風＋iPhone 股市 App 風；預設深色、支援淺色
- 頂部霧化導覽、置中大字總值（琥珀漸層＋數字滾動進場）、可滑動產品卡、四格數字卡
- 未來價值圖：1/3/5 年切換、手指滑動查看各年預估
- 清單：照片＋名稱＋市值＋漲跌膠囊，可依市值／漲幅／最新排序、系列篩選
- 點酒款開底部詳情頁：大圖、價格對照條、1/3/5 年預估、評估、備註
- 使用者實拍照片（不去背、不用官方圖）

## 使用者偏好
- 全程繁體中文；逐步確認對焦；提供 4–5 個選項並附最佳建議；一次只問一題；精簡額度
- 修改前先確認設計，再 push

## 待辦（可選）
- 頂部分段切換（總覽／收藏／分析）
- 定期更新行情（建議每季）：查 Just Whisky／Scotch Whisky Auctions 落槌價、FindPrice 台灣售價，更新 data 後重建 index.html
- 香港回收價待使用者詢價後填入
