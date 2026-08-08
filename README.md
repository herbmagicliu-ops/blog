# 燈下 · Jekyll 起手包

古典、靈性與生活的閱讀筆記。純 Markdown 寫作，GitHub Pages 免費託管，網域 dengxia.blog。

---

## 一、第一次上線（做一次就好）

1. 在 GitHub 建一個 repo（例如 `dengxia`），把本資料夾**所有檔案**推上去。
2. repo → **Settings → Pages** → Source 選 `Deploy from a branch`，分支選 `main`、資料夾 `/ (root)`，存檔。
3. 等一兩分鐘，你的站會先出現在 `https://<你的帳號>.github.io/dengxia/`。
4. **綁網域**：`CNAME` 檔已經幫你填好 `dengxia.blog`。到你的網域商後台設定 DNS：
   - 四筆 **A** 紀錄（主機填 `@`）指向：
     `185.199.108.153` / `185.199.109.153` / `185.199.110.153` / `185.199.111.153`
   - 一筆 **CNAME**（主機填 `www`）指向 `<你的帳號>.github.io`
   - （以上為 GitHub Pages 標準設定，請對照 GitHub 官方文件最新值確認。）
5. 回 Settings → Pages 的 Custom domain 填 `dengxia.blog`，等驗證通過後勾選 **Enforce HTTPS**。

DNS 生效可能要幾分鐘到幾小時。

## 二、怎麼發一篇文章

在 `_posts/` 新增一個檔案，檔名格式固定：`年-月-日-英數slug.md`。開頭貼這段，改內容就發：

```yaml
---
layout: post
title: "你的標題"
date: 2026-08-08 21:00:00 +0800
category: 古文學          # 四選一：古文學 / 靈性探索 / 宗教哲學與修行 / 時事反思
subcategory: 詩詞賞析
tags: [唐詩, 賞析]
excerpt: "一句話摘要（列表與 SEO 用）"
ads: true                # 這篇要不要顯示廣告
affiliate: false         # 有放聯盟連結就改 true，文首自動出現揭露條
---

正文從這裡開始，直接寫 Markdown。
```

commit 後 GitHub 會自動重建，網站幾分鐘內更新。

## 三、開啟 Google 廣告

1. 站上先有幾篇像樣的原創文章、`about` / `privacy` / `disclosure` 三頁都填好，再去申請 AdSense（內容太少最常被打回）。
2. 通過後，把發布商 ID（形如 `ca-pub-xxxxxxxxxxxxxxxx`）填進 `_config.yml` 的 `adsense_publisher_id`。**填了才會載入廣告，留空則全站無廣告碼。**
3. 編輯 `ads.txt`：把 `pub-0000000000000000` 換成你的 ID、刪掉註解行。確認 `https://dengxia.blog/ads.txt` 能直接打開。
4. `_includes/adsense.html` 裡的 `data-ad-slot` 換成你在 AdSense 後台建立的廣告單元編號。

## 四、聯盟行銷

單篇 front matter 設 `affiliate: true`，文首會自動帶出揭露條，不用每篇手打。記得把 `_pages/disclosure.md` 和 `privacy.md` 裡的聯絡信箱等佔位文字換成你自己的。

## 五、想從四類改回三類？

若「宗教哲學與修行」暫時併回「靈性探索」：
- `_config.yml` 的 `categories_nav` 刪掉那一列；
- 刪掉 `categories/practice.html`；
- 相關文章的 `category` 改成 `靈性探索`。
零風險，隨時可改回來。

## 檔案地圖

- `_posts/`：你日常唯一要碰的地方
- `_pages/`：關於、隱私權、揭露聲明
- `_layouts/` `_includes/`：版型與零件（廣告/聯盟開關邏輯在 `_layouts/post.html`）
- `categories/`：四個分類列表頁
- `assets/css/style.css`：全站樣式（燈下配色）
- `_config.yml`：站台設定與 AdSense ID
