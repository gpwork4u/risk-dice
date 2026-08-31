# 風險骰 · Risk Die

二十面（d20）風險骰網頁 — **十九面大吉，一面大凶**。
使用 Three.js（WebGL）繪製、cannon-es 做剛體物理模擬，結果由真實物理決定。

- Icosahedron 幾何體 + `ConvexPolyhedron` 剛體：骰子從空中拋下，受重力翻滾、彈跳、摩擦後自然停下
- 隱形圍牆與淺碗位能，確保骰子落定在畫面正中央
- 落定後讀取「哪一面朝上」判定吉凶（凶面每次載入隨機分配，機率貨真價實 1/20），並微幅扶正
- 骰面以 Canvas 動態刻上「吉／凶」字樣，碰撞時以 WebAudio 播放落地聲
- 塵埃粒子、柔和陰影、噪點顆粒氛圍；支援 `prefers-reduced-motion` 與鍵盤操作（Space / Enter）

純靜態單檔 `index.html`，無建置步驟，Three.js 與 cannon-es 由 CDN 載入。

## 本地預覽

```sh
python3 -m http.server 8000
# 開啟 http://localhost:8000
```

## 部署到 GitHub Pages

```sh
git init
git add .
git commit -m "feat: physics-based d20 risk die"
gh repo create risk-dice --public --source=. --push
```

然後到 GitHub repo 的 **Settings → Pages**：

- Source 選 **Deploy from a branch**
- Branch 選 `main`、資料夾選 `/ (root)`

約一分鐘後即可在 `https://<username>.github.io/risk-dice/` 看到頁面。
