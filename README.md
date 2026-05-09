# 🌌 SillyTavern V4 卡片构建器 (Ultimate Card Builder)

![Astro](https://img.shields.io/badge/Astro-5.x-ff5d01?logo=astro&logoColor=white)
![Vanilla JS](https://img.shields.io/badge/Vanilla%20JS-ES2020-f7df1e?logo=javascript&logoColor=111)
![Deploy](https://img.shields.io/badge/Deploy-Zeabur-6f5cff)

这是一个角色卡构建平台，结合语言模型接口、世界书管理、正则 UI 注入，以半流水线的方式打造 SillyTavern 角色卡。

## ✨ 核心特性 (Features)

### 🤖 双重 AI 智能流水线
- **预设提取**：支持直接导入酒馆原生 `.json` 预设，自动提取底层逻辑与文风，约束 AI 的生成方向。
- **上下文防漂移**：在自动生成世界书（Worldbook）时，底层引擎会自动捕获已存在的设定，采用“链式迭代生成”。
- **定点重写**：对单条世界书不满意？输入你的定向要求，AI 将精准锁定该条目进行局部覆盖重写。

### 📖 世界书控制 (Worldbook CRUD)
- 告别繁琐的酒馆内编辑，支持在卡片创建期就注入强大的规则。
- 完整支持酒馆角色卡规范下的高阶参数：`Strategy (触发策略)`、`Depth (挂载深度)`、`Order (插入顺序)`、`Role (系统/用户/AI)` 及 `Probability (触发概率)`。

### 📊 动态状态栏一键注入 (Status Bar Injection)
- **半 AI 构思**：只需输入角色描述，AI 会自动为你构思出极具沉浸感的监控字段（如赛博朋克风的“义体完整度、污染指数”）。
- **零代码正则注入**：一键生成并在底层卡片中写入 `regex_scripts`。导入酒馆后，AI 每次回复都会自动在末尾渲染带有赛博发光 CSS UI 的状态面板。
- **本地草稿箱**：所有进度实时静默保存至浏览器的 `localStorage`。

## 🚀 快速开始 (Getting Started)

本项目基于 [Astro](https://astro.build/) 构建，默认输出为纯静态站点。

### 1. 环境准备

确保你的电脑上安装了 Node.js 20 或更高版本。

### 2. 克隆与安装

```bash
git clone <你的仓库地址>
cd st-card-builder
npm install
```

### 3. 本地开发

```bash
npm run dev
```

### 4. 生产构建

```bash
npm run build
npm run preview
```

## ☁️ Zeabur 一键部署

这个仓库已经包含 Zeabur 静态站点部署配置：

- `zbpack.json` 指定 `npm run build` 作为构建命令。
- `zbpack.json` 指定 `dist` 为静态产物目录，Zeabur 构建完成后会用静态 Web 服务托管。
- `package.json` 固定使用 npm，并声明 Node.js 20+。

### 部署步骤

1. 将本仓库推送到 GitHub。
2. 打开 [Zeabur Dashboard](https://dash.zeabur.com/)，创建或选择一个 Project。
3. 点击 **Deploy New Service** → **GitHub**，授权并选择这个仓库。
4. Zeabur 会自动读取仓库内的 `zbpack.json`，执行 `npm run build`，并部署 `dist/`。
5. 部署完成后，在服务的 **Domain** 页面点击 **Generate Domain** 即可获得访问地址。

> 说明：当前项目的 AI 接口地址、API Key、搜索 Key 等都在浏览器端由用户自行填写并保存到 `localStorage`，因此 Zeabur 部署时不需要预设服务端环境变量。

如果你已经在 Zeabur 控制台把该项目发布成模板，可以把 Zeabur 生成的 Deploy Button 粘贴到这里，实现真正的 README 按钮式一键部署。
