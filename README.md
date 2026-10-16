# 面对面 · 一颗爱心

一个纯静态的单页小网站：两个人的照片左右相对，中间是一颗会跳动、会冒小心心的爱心。

## 线上地址

开启 GitHub Pages 后：

```
https://<你的用户名>.github.io/<仓库名>/
```

例如用户名是 `fknb`、仓库名是 `heart`，地址就是 `https://fknb.github.io/heart/`。

## 目录结构

```
双人爱心网页/
├── index.html        页面本体（结构、样式、交互全在这一个文件里）
├── images/
│   ├── boy1.png      左边的人
│   └── boy2.png      右边的人
├── README.md
└── .nojekyll         告诉 GitHub Pages 不要用 Jekyll 处理，直接按静态文件发布
```

## 本地预览

直接双击 `index.html` 用浏览器打开即可；或者在本文件夹里起一个本地服务：

```powershell
python -m http.server 8000
# 然后访问 http://localhost:8000
```

## 效果说明

- **布局**：宽屏时三栏并排 —— 左人、爱心、右人；窄屏（≤720px）自动变成上下排列，爱心仍夹在两人中间。
- **面对面**：两人的照片带轻微反向倾斜与浮动动画，视觉上朝中间靠拢。
- **爱心**：内联 SVG + 渐变填充，带心跳缩放动画、向外扩散的光环，以及从两侧飞入的小心心。
- **交互**：
  - 点爱心 → 爆出一圈小心心；
  - 「让心跳快一点」→ 心跳频率从 1.5s 提到 0.6s，再点恢复；
  - 「点我一下」→ 循环切换底部文案。
- **自适应**：手机、平板、电脑都能正常显示；若系统开启了「减弱动态效果」，动画会自动关闭。

## 想自己改

| 想改什么 | 改哪里 |
| --- | --- |
| 照片 | 直接替换 `images/boy1.png`、`images/boy2.png`（保持文件名不变即可） |
| 照片对焦位置 | `index.html` 里 `.frame img[data-fit="boy1"]` 的 `object-position` |
| 爱心颜色 | `index.html` 里 `<linearGradient id="heartGrad">` 的三个 `stop-color` |
| 主题色 / 背景 | `:root` 里的 `--accent`、`--bg` 以及 `body` 的 `radial-gradient` |
| 底部文案 | `.caption` 里的 `<h1>` 和 `<p>` |
| 名字标签 | `.name` 里的「左边的他」「右边的他」 |
