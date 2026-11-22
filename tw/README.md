# HyperFrames 台灣版（tw/）

這是 `lalawgwg99/hyperframes` fork 裡的台灣版薄層，只加文件與範本，**不改 `packages/*` 核心**，方便日後同步上游。

## 範本一覽（全部 1080×1920、9:16）

| 範本 | 秒數 | 用途 |
| --- | --- | --- |
| `9x16-product/index.html` | 15 | 產品介紹：開場、產品圖、3 個賣點、CTA（不寫價格） |
| `9x16-story/index.html` | 15 | 說書開場：書名、觀念、鉤子、提問 |
| `9x16-notice/index.html` | 12 | 活動公告：標題、時間地點、現場說明 |

## 怎麼用

```bash
# 在 fork 根目錄（需 Bun、Node >= 22）
bun run dev
# 開 Studio 後載入 tw/9x16-product/index.html，或：
npx hyperframes render tw/9x16-product/index.html -o out/product-9x16.mp4
```

實際 render 指令請以當版 CLI `--help` 為準；若指令有變，以上游文件為準。

## 規則（台灣版鐵律）

- 畫面內所有中文字都是 HTML 疊加，**不叫模型畫中文字**。
- 產品圖請用自己的官方照片，不要用 AI 生成的產品圖。
- 範本內不寫價格、不寫折扣。
- 字體：Noto Sans TC，授權 SIL OFL 1.1；範本用 Google Fonts 載入，fallback 只寫 `"Noto Sans TC", sans-serif`。不要把蘋方、微軟正黑體寫進 font-family——HyperFrames lint 會報錯（渲染器無法自動提供這些系統字型，雲端渲染會直接退回通用字型）。本機沒裝 Noto Sans TC 時會退回通用 sans-serif，排版可能跑掉，請先確認字體有載入。不要修改字型檔再重新發布。
- GSAP 是本機內嵌（各範本 `assets/gsap.min.js`，3.14.2，檔案開頭授權頭保留），不走 CDN——渲染環境若擋 CDN，動畫會整段失效；內嵌後離線也能出片。GSAP 授權見 https://gsap.com/standard-license。
- 安全區：上方留 180px（帳號列），下方留 320px（按讚、留言、字幕區），重要文字只放中間 300–1420px。

## 授權與聲明

- 本 fork 基於 [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes)，Apache License 2.0；原 `LICENSE` 已保留，修改處見本文件與各範本開頭註解。
- **非 HeyGen 官方產品**，與 HeyGen 無關，不可用 HeyGen 商標替本衍生版背書。
- 上游根目錄無 NOTICE 檔；registry 區塊內的第三方 NOTICE（如 GSAP-NOTICE.txt）用到時須保留。

## 同步上游

上游活躍期每週同步一次，或上游打 tag／重大 release 時同步：

```bash
git fetch upstream
git merge upstream/main   # 或 rebase，視對外 commit 而定
```

只碰 `tw/` 與 `README.zh-TW.md`，衝突通常很少；但上游若改 composition 掛載或 `data-width`／`data-height` 契約，範本仍可能壞，同步後要重跑一次範本驗證。
