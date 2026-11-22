# HyperFrames 台灣版

> 非 HeyGen 官方產品。本 fork 基於 [heygen-com/hyperframes](https://github.com/heygen-com/hyperframes)，Apache License 2.0，原 `LICENSE` 已保留。修改處：新增 `tw/` 目錄與本文件。

HyperFrames 是免費開源的 AI 影片編輯器：用 HTML、CSS、動畫寫影片，逐幀都能改。台灣版只做一件事：**讓台灣人做 9:16 直式短影片更快**，不動渲染引擎。

## 台灣版多了什麼

- 3 個 9:16 繁中範本（`tw/`）：產品介紹、說書開場、活動公告，1080×1920。
- 畫面內中文字全部 HTML 疊加，不叫模型畫中文字；產品圖請用自己的官方照片。
- 字體 Noto Sans TC（SIL OFL 1.1），附 fallback 清單；安全區已標好（上 180px、下 320px）。

詳見 [`tw/README.md`](tw/README.md)，旁白方案見 [`tw/VOICEOVER.md`](tw/VOICEOVER.md)。

## 環境門檻（先老實講）

- 本倉庫是完整 monorepo，約 550 MB；`git clone` 與 `bun install` 需要時間與磁碟空間。
- 需 Bun、Node >= 22；基本使用不需環境變數，選用整合才需 `GEMINI_API_KEY`。

```bash
bun run dev          # 開 Studio
npx hyperframes render tw/9x16-product/index.html -o out/product-9x16.mp4
```

實際 render 指令請以當版 CLI `--help` 為準。

## 上游

- 上游：https://github.com/heygen-com/hyperframes
- 授權：Apache License 2.0
- 同步：上游活躍期每週一次，或打 tag／重大 release 時同步；只改 `tw/` 與本文件，同步後重跑範本驗證。
