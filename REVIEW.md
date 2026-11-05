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

### 貼膏（2）
| slug | 名稱 |
|------|------|
| dingtong | 定痛膏 |
| xiaozhong | 消腫膏 |

### 泡腳藥包（4）
| slug | 名稱 |
|------|------|
| wash-joint | 中藥外洗一方 |
| wash-pain | 中藥外洗二方 |
| wash-sinew | 中藥外洗三方 |
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

## 資產統計

- 約 **73** 個檔案（含雙寫的 fang index）
- 體積約 **7.6 MB**
- `products/` 圖片 **21** 張（含 hero）
- `assets/` JS/CSS **7** 個
- 另有 `favicon.svg`、`og.jpg`、`404.html`、`.nojekyll`

## Base path 修正

- HTML：`/assets`、`/products`、`/fang`、`/?kind=`、`/favicon` → `/yuanzhi/...`
- `og:image` / canonical → `https://tcmmacau.github.io/yuanzhi/...`
- JS：`basepath:`/yuanzhi``（TanStack Router，對齊 beauty 站做法）
- JS 內媒體路徑：`/products/`、`/assets/` → `/yuanzhi/products|assets/`
- **未**改寫 router 的 `to:`/`/fang/$slug``（由 basepath 處理）
- 已移除 grok.com extensions、`grok-project-id`、`__grok` manifest / apple-touch 連結
- 保留 Google Fonts（Noto Sans/Serif TC）外連

## 本地煙測（已做）

在 `/tmp/yuanzhi-preview` 以 `python3 -m http.server 8765` 模擬前綴：

- `/yuanzhi/index.html` → 200
- `/yuanzhi/fang/tongqiao/` → 200
- `/yuanzhi/products/hero.jpg` → 200
- 首頁內 **48** 個 `/yuanzhi/...` 引用全部 200，**0** broken

客戶端路由（分類 `?kind=`、詳頁切換）建議用瀏覽器再點一次確認。

## 已知／留意

- 來源站為 SPA + SSR HTML；分類篩選靠 query（`?kind=sachet` 等），需 JS。
- 未帶入 beauty 的 GoatCounter；上線後如要統計可另加。
- 未建立 GitHub repo、**未** push、**未** 開 Pages。
- 現場 `https://tcmmacau.github.io/yuanzhi/` 應仍為 404（遷移時已核對）。
- **不做** 舊 grok.me 轉址（用戶未對外正式發佈該 URL）。

## 本地預覽指令

```bash
mkdir -p /tmp/yuanzhi-preview
rm -rf /tmp/yuanzhi-preview/yuanzhi
cp -a /workspace/yuanzhi /tmp/yuanzhi-preview/yuanzhi
cd /tmp/yuanzhi-preview && python3 -m http.server 8765 --bind 127.0.0.1
# 打開 http://127.0.0.1:8765/yuanzhi/
```

## 確認後上線（勿提前執行）

用戶明確同意後，建議指令：

```bash
cd /workspace/yuanzhi
# 若尚未有遠端：
gh repo create TCMMACAU/yuanzhi --public --source=. --remote=origin --push=false
# 或先建空 repo 再：
git remote add origin git@github.com:TCMMACAU/yuanzhi.git

# 推 main（首次）
git checkout -B main
git push -u origin main

# 啟用 GitHub Pages（從 main 根目錄）
gh api -X POST repos/TCMMACAU/yuanzhi/pages \
  -f build_type=workflow 2>/dev/null || true
# 經典設定：Settings → Pages → Deploy from branch → main / (root)
gh api -X PUT repos/TCMMACAU/yuanzhi/pages \
  -f build_type=legacy \
  -f source[branch]=main \
  -f source[path]=/

# 核對
curl -sI https://tcmmacau.github.io/yuanzhi/ | head
```

上線後：交「身心課堂跟進」維護（改前草稿確認、書面語規則）。
