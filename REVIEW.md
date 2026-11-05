# 院製站遷移審閱（/yuanzhi/）

**日期**：2026-11-05（Asia/Macau）  
**草稿路徑**：`/workspace/yuanzhi`  
**來源**：`https://grove-fern-rocket-sky.grok.me`（僅鏡像；**不做** grok.me 轉址）  
**目標**：`https://tcmmacau.github.io/yuanzhi/`（確認後才上線）

## 頁面清單

### 首頁
- `/yuanzhi/` — 院製總覽、分類篩選、注意事項

### 香囊（2）
| slug | 名稱 |
|------|------|
| tongqiao | 通竅提神香囊 |
| anshen | 安神助眠香囊 |

### 泡腳藥包（1）
| slug | 名稱 |
|------|------|
| aijiang | 艾薑溫經外洗包 |

### 保健茶（12）
| slug | 名稱 |
|------|------|
| tea-yangwei | 養胃茶 |
| tea-pingbu | 平補茶 |
| tea-jinbu | 進補茶 |
| tea-zibu | 滋補茶 |
| tea-guihua | 桂花雪梨茶 |
| tea-juhua | 菊花解脂茶 |
| tea-hugan | 護肝明目茶 |
| tea-taohua | 桃花清腸茶 |
| tea-rose | 玫瑰八寶茶 |
| tea-ningxin | 寧心養顏茶 |
| tea-yiling | 薏苓祛濕茶 |
| tea-juju | 菊苣平酸茶 |

產品詳頁檔案：`fang/<slug>.html` 與 `fang/<slug>/index.html`（雙寫，方便本地與 Pages 無副檔名路徑）。

## 已下架（院內制劑，不可對外宣傳）

以下內容已自公開站頁移除（頁面、目錄、介紹、對照入口）：

| slug | 名稱 |
|------|------|
| dingtong | 定痛膏 |
| xiaozhong | 消腫膏 |
| wash-joint | 中藥外洗一方 |
| wash-pain | 中藥外洗二方 |
| wash-sinew | 中藥外洗三方 |

對應 `products/plaster-*.jpg`、`products/wash-joint|pain|sinew.jpg` 仍留在倉庫但已無頁面引用。

## 資產統計（下架後）

- `fang/` 詳頁：15 款 × 雙寫 = 30 個 HTML
- `products/` 圖片仍含未引用的貼膏／外洗一二三方圖
- `assets/` JS/CSS **7** 個
- 另有 `favicon.svg`、`og.jpg`、`404.html`、`.nojekyll`

## Base path 修正

- HTML：`/assets`、`/products`、`/fang`、`/?kind=`、`/favicon` → `/yuanzhi/...`
- `og:image` / canonical → `https://tcmmacau.github.io/yuanzhi/...`
- JS：`basepath:`/yuanzhi``（TanStack Router）
- **未**改寫 router 的 `to:`/`/fang/$slug``（由 basepath 處理）

## 確認後上線（勿提前執行）

用戶明確同意後，才 push / merge `main`、啟用或更新 GitHub Pages。
