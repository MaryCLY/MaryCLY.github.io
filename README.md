# 真理的空剧场

Mary / Mari 的个人主页，部署目标为 GitHub Pages。

## 首页

首页使用原生 HTML、CSS 和 SVG，不依赖 Hexo、JavaScript、外部字体或构建工具。
采用白底、黑灰细框和粉色票根；中间区域保留为空白。票根是装饰，不是按钮。

- `index.html`：页面内容及元信息。
- `css/home.css`：首页独立样式，包含窄屏适配。
- `favicon.svg`：粉色底的舞台门框标记，同时用于首页左上角。

## 本地预览

在仓库根目录运行（需要已安装 Python）：

```sh
python -m http.server 8000 --bind 127.0.0.1
```

访问 `http://localhost:8000`。也可以直接在浏览器打开 `index.html`。

## GitHub Pages

无需本地构建。GitHub Pages 已配置为从 `main` 分支的根目录 `/` 发布，
推送到该分支后会自动触发部署。站点地址为 https://marycly.github.io/ 。

## 旧站内容

本仓库现仅保留新首页及其资源。旧文章、归档、订阅、站点地图和旧静态资源已清理，
发布后旧页面 URL 将不再提供原内容。
如需恢复旧内容，可从 `MaryCLY/marycly.github.io_local` 源码仓库或本仓库的 Git 历史查找。
请勿继续从旧 Hexo 项目向本仓库部署，以免覆盖新首页。
