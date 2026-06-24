# Frame Extractor · 在线视频抽帧工具

上传视频，按 **时间间隔 / 总数量 / 指定时刻** 抽取画面为图片，支持 PNG / JPG / WebP 输出和一键打包 ZIP 下载。

**全程在浏览器本地完成，视频不会上传到任何服务器。** 纯静态、无后端、无需安装。

## 本地预览

直接双击 `index.html` 即可在浏览器打开使用。

或起一个本地静态服务器（部分浏览器对 `file://` 限制更严时使用）：

```bash
python3 -m http.server 4321
# 然后访问 http://localhost:4321
```

## 部署成公网网址（免费）

这是一个纯静态站点，把本文件夹整体上传到任意静态托管平台即可拿到一个公网链接发给别人。

### 方式 A · Netlify Drop（最快，零配置）
1. 打开 https://app.netlify.com/drop
2. 把整个 `frame-extractor` 文件夹拖进网页
3. 几秒后得到形如 `https://xxx.netlify.app` 的网址

### 方式 B · Vercel
```bash
npm i -g vercel
cd frame-extractor
vercel
```
按提示完成后得到 `https://xxx.vercel.app`。

### 方式 C · Cloudflare Pages
打开 Cloudflare Pages → 上传（Direct Upload）→ 拖入本文件夹 → 得到 `https://xxx.pages.dev`。

### 方式 D · GitHub Pages
把本文件夹推到一个 GitHub 仓库，在仓库 Settings → Pages 选择分支并开启，得到 `https://用户名.github.io/仓库名`。

> 以上平台均免费，且支持绑定你自己的自定义域名。

## 文件说明

| 文件 | 作用 |
|------|------|
| `index.html` | 应用本体（HTML/CSS/JS 全部内联，单文件即可运行） |
| `favicon.svg` | 站点图标 |
| `og-image.jpg` | 社交分享缩略图（1200×630，链接发到微信/Twitter 等会显示） |
| `README.md` | 本说明 |

## 已知限制

- 浏览器只能解码其原生支持的视频编码（多数 MP4/H.264、WebM 正常）。H.265 / ProRes 等可能无法播放，如需全格式支持可改用 ffmpeg.wasm 版本。
- 抽帧采用"跳转到时间点后截图"，适用绝大多数场景；如需逐帧零遗漏的精确抽帧，同样建议 ffmpeg.wasm 方案。

## 依赖

- [JSZip](https://stuk.github.io/jszip/)（通过 CDN 加载，用于打包下载）
