# 搬砖叠塔 · Brick Stack

纯 HTML5 单文件网页小游戏（Canvas 2D，零依赖）。打开网页就能玩，传到任何静态空间发个链接就能分享给别人。

> 玩法：一根砖块左右移动，点击 / 空格放下，与下层对齐 —— 超出的部分被切掉掉落，切到完全没有重叠就塌楼。完美对齐 +2 分。盖得越高分越高。

## 怎么玩

- 最简单：**双击 `index.html`** —— 单文件零依赖，浏览器直接打开就能玩。
- 或本地起个服务（手机连同一 WiFi 也能扫着玩）：
  ```powershell
  python -m http.server 8090
  # 浏览器打开 http://localhost:8090/
  ```
- 操作：鼠标点击 / 触摸屏点击 / 空格键 = 放下砖块。

## 放到网上（都免费）

任选其一，上传后得到一个公开链接，发给谁都能点开玩：

- **GitHub Pages**：本目录推到仓库 → Settings → Pages → 选分支 → 得到 `https://<用户名>.github.io/<仓库>/`
- **itch.io**：把 `index.html` 打包成 zip 上传，Kind 选 HTML，勾选 "This file will be played in the browser"
- **Netlify Drop**：打开 app.netlify.com/drop，直接把文件夹拖进去
- **Vercel / Cloudflare Pages**：连仓库或拖拽部署

## 技术说明

- 单文件 `index.html`，HTML + CSS + JS 全部内联，**无外部依赖、无构建步骤**。
- 画布自适应：手机全宽、桌面限宽 480 居中；同时支持鼠标 / 触摸 / 键盘。
- 最高分用 `localStorage` 本地持久化。
- 全部玩法在一个 `Game` 类里：状态机（ready / playing / over）+ 碰撞重叠判定 + 削减 / 完美对齐 / 塌楼三分支 + 相机跟随上移。

## 后续可做

- [ ] 把碰撞 / 得分逻辑抽成纯函数 + 单测（日后换皮量产不回归）
- [ ] 分享：生成带分数的图片 / 一键复制成绩
- [ ] 变现：接 GameDistribution / GameMonetize 的 H5 广告 SDK（铺量打法）
- [ ] 换皮量产：改配色 + 文案 + 个别参数即可衍生新主题
- [ ] 想进微信小游戏时再用工具打包（逻辑通用，没锁死生态）
