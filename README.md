# 鏡湖中醫 · 院製

靜態站：香囊、泡腳藥包、保健茶。

- **正式網址（確認後）**：https://tcmmacau.github.io/yuanzhi/
- **文案**：書面語（與天灸／四時調攝一致）
- **維護**：交由「身心課堂跟進」；改前草稿確認

## 狀態

本地草稿，**尚未** push `main`、**尚未** 啟用 GitHub Pages。
來源自 grok.me 預覽站鏡像後改 base path 為 `/yuanzhi/`。

## 本地預覽（模擬 GitHub project Pages）

```bash
mkdir -p /tmp/yuanzhi-preview
rm -rf /tmp/yuanzhi-preview/yuanzhi
cp -a /workspace/yuanzhi /tmp/yuanzhi-preview/yuanzhi
cd /tmp/yuanzhi-preview && python3 -m http.server 8765 --bind 127.0.0.1
# 瀏覽器打開 http://127.0.0.1:8765/yuanzhi/
```

詳見 `REVIEW.md`。
