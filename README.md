# WorldBrief · 世界速览

> **中文世界信息聚合仪表盘 — 一屏速览 8 大源**
>
> [koala73/worldmonitor](https://github.com/koala73/worldmonitor) 的中文版 — 更轻、更聚焦中国用户、单文件可部署。

[![GitHub stars](https://img.shields.io/github/stars/fast118/worldbrief?style=social)](https://github.com/fast118/worldbrief/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![No Build](https://img.shields.io/badge/build-none-success)](https://github.com/fast118/worldbrief)
[![Single File](https://img.shields.io/badge/files-1-blue)](https://github.com/fast118/worldbrief)

---

## 这是什么

**单文件 HTML**，打开即用 / 部署到 GitHub Pages 即可访问。

聚合 8 大中文/英文信息源，**5 分钟自动刷新**，支持 AI 一句话摘要。

| 数据源 | 类型 | 刷新策略 |
|---|---|---|
| 🔥 微博热搜 | 中文社交 | 5 min |
| 💡 知乎热榜 | 中文问答 | 5 min |
| 📊 36氪热榜 | 中文创投 | 5 min |
| 🟠 Hacker News | 海外技术 | 5 min |
| ⭐ GitHub Trending | 开源热度 | 5 min |
| 📺 B站热门 | 中文视频 | 5 min |
| 🎵 抖音热搜 | 中文短视频 | 5 min |
| 🌍 全球地震 | 灾害监测 | 5 min |

---

## vs worldmonitor

| 维度 | worldmonitor | worldbrief |
|---|---|---|
| 文件数 | 1000+ | **1** |
| 构建工具 | Vite + Tauri + 276 protos | **无** |
| 部署 | Vercel / Docker / Electron | **GitHub Pages / 双击打开** |
| 数据源 | 500+ 英文 | **8 个中文/海外高频** |
| AI 摘要 | Groq / OpenRouter / Ollama | **api.skillai.top（国内直连）** |
| 主题变体 | 6 个 (world/tech/finance/...) | **1 个，专注中文** |
| 地图 | globe.gl + deck.gl | **无地图，更快** |
| 语言 | 24 种 | **中文 + 海外技术英文** |
| 协议 | AGPL v3 | **MIT** |
| 目标用户 | 全球情报分析 | **中国开发者 / 投资人 / 自媒体** |

**Worldbrief 的优势：**
- 零依赖 / 零构建 — 下载即用
- 中文优先 — 数据源、UI、AI 全中文
- 单页加载 — 5 秒看完
- 隐私友好 — 一切跑在客户端或你自己的 api.skillai.top

---

## 快速开始

### 方式 1：直接打开（最简单）
```bash
git clone https://github.com/fast118/worldbrief.git
cd worldbrief
# 双击 index.html
```

### 方式 2：本地 HTTP server
```bash
# Python
py -m http.server 8000
# 或 Node
npx http-server -p 8000
```
访问 http://localhost:8000

### 方式 3：GitHub Pages（推荐）
1. 推到 `fast118/worldbrief` 仓库
2. Settings → Pages → Source 选 `main` 分支
3. 几分钟后访问 `https://fast118.github.io/worldbrief/`

---

## 自定义

### 关闭 AI 摘要
右上角下拉 → "AI 摘要: 关闭"

### 修改 API base URL
编辑 `index.html`：
```js
const SKILLAI_BASE = 'https://api.skillai.top';
// 改为你的自部署地址
const SKILLAI_BASE = 'https://your-api.example.com';
```

### 增删数据源
在 `SOURCES` 数组里加/删对象即可：
```js
{
  id: 'toutiao', emoji: '📰', name: '今日头条', limit: 15,
  url: encodeURIComponent('https://www.toutiao.com/hot-event/hot-board/?origin=toutiao_pc'),
  transform: (j) => (j.data || []).map((x) => ({
    title: x.Title || x.title,
    url: x.Url || x.url,
    meta: x.HotValue || ''
  }))
}
```

### 更换 CORS 代理
默认用 [allorigins.win](https://allorigins.win)。如需自建：
```js
const PROXY = 'https://your-cors-proxy.example.com/?url=';
```

---

## 技术栈

- **HTML + CSS + Vanilla JS** — 零依赖
- **fetch API + AbortController** — 并发请求
- **CSS Grid + Flexbox** — 响应式布局
- **Dark mode by default** — 护眼
- **AllOrigins / api.skillai.top** — CORS + AI

总代码量：**~ 350 行**（含 HTML + CSS + JS）

---

## 路线图

- [x] v0.1.0: 8 大源聚合 + AI 摘要
- [ ] v0.2.0: 用户自选数据源（点击卡片收藏）
- [ ] v0.3.0: 关键词告警（如关注 "关税"、"地震"）
- [ ] v0.4.0: 时间轴视图（看趋势）
- [ ] v0.5.0: 浏览器扩展版

---

## 致谢

- [koala73/worldmonitor](https://github.com/koala73/worldmonitor) — 项目灵感来源
- [allorigins.win](https://allorigins.win/) — 免费 CORS 代理
- [api.skillai.top](https://api.skillai.top) — 国内 AI 推理中转
- 微博 / 知乎 / 36kr / B站 / 抖音 / Hacker News / GitHub / 中国地震台网 — 数据源

---

## 许可

MIT — 自由使用、修改、商用。
挂个 star 就够了 🙏

---

**如果觉得有用，欢迎：**
- ⭐ Star
- 🐛 提 Issue
- 🔀 提 PR
- 📣 分享给身边的朋友