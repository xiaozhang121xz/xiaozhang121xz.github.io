# 技术札记｜Hugo + PaperMod

这是为 `xiaozhang121xz/xiaozhang121xz.github.io` 准备的中文技术博客项目。

- 网站地址：<https://xiaozhang121xz.github.io/>
- 技术栈：Hugo + PaperMod + GitHub Pages + GitHub Actions
- 内容格式：Markdown
- 主题：PaperMod（部署时由 GitHub Actions 自动拉取上游主题）

## 目录结构

```text
.
├── .github/workflows/deploy.yml
├── archetypes/default.md
├── content/
│   ├── about.md
│   ├── archives.md
│   ├── search.md
│   └── posts/
│       ├── welcome/index.md
│       └── harness/context-compression.md
├── hugo.yaml
└── README.md
```

## 上传到你的 GitHub 仓库

1. 下载并解压这个 ZIP。
2. 打开仓库：<https://github.com/xiaozhang121xz/xiaozhang121xz.github.io>
3. 选择 **Add file → Upload files**。
4. 上传解压后目录中的**所有文件和文件夹**，注意要包含隐藏目录 `.github`。
5. 在页面下方填写提交说明，例如 `Initialize Hugo PaperMod blog`，然后提交到 `main` 分支。

请上传项目根目录里的内容，不要把整个外层文件夹再套一层上传，否则 GitHub Actions 可能找不到 `hugo.yaml`。

## 启用 GitHub Pages

上传完成后：

1. 进入仓库 **Settings → Pages**。
2. 在 **Build and deployment → Source** 中选择 **GitHub Actions**。
3. 进入仓库 **Actions** 页面，查看 `Deploy Hugo site to GitHub Pages` 工作流。
4. 等待 Build 和 Deploy 两个 Job 都成功。
5. 打开 <https://xiaozhang121xz.github.io/> 查看网站。

第一次部署可能需要几分钟。如果 Actions 失败，点进失败的 Job 查看日志。

## 本地预览（可选）

需要先安装 Hugo Extended（建议使用当前稳定版，PaperMod 要求较新的 Hugo）。

然后在项目根目录运行：

```bash
git clone --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
hugo server -D
```

浏览器打开终端提示的本地地址，通常是 `http://localhost:1313/`。

## 如何写新文章

推荐使用 Hugo 命令：

```bash
hugo new content posts/my-first-note.md
```

如果本地没有安装主题，先按上面的步骤 clone PaperMod。创建文章后，把 front matter 中的 `draft: true` 改成 `draft: false`，再编辑正文。

也可以直接复制 `archetypes/default.md` 的结构，在 `content/posts/` 下新建 Markdown 文件。

文章示例：

```yaml
---
title: "我的新文章"
date: 2026-11-22
draft: false
description: "一句话摘要"
tags: ["Agent", "LLM"]
categories: ["技术实践"]
---
```

## 搜索、归档与分类

- 搜索：`/search/`（PaperMod 内置搜索，首页 JSON 索引）
- 归档：`/archives/`
- 分类：`/categories/`
- 标签：`/tags/`

## 主题更新

部署工作流每次构建都会从 PaperMod 上游仓库拉取最新默认分支。若希望固定主题版本以保证构建结果长期可复现，可将 workflow 中的 `git clone` 改为 checkout 指定 tag 或 commit。

## 常见问题

### 网站 404

检查 Pages 的 Source 是否设为 **GitHub Actions**，并确认 Actions 的 Deploy Job 成功。

### Actions 找不到 Hugo 配置或没有内容

确认 `hugo.yaml` 位于仓库根目录，而不是多套了一层文件夹。

### 搜索没有结果

等待部署完成后再试；确认 `hugo.yaml` 的首页输出包含 `JSON`，且文章的 `draft` 为 `false`。

### 如何修改网站名称

编辑根目录 `hugo.yaml` 中的 `title`、`params.description` 和 `params.homeInfoParams`。

---

## 内容来源说明

`content/posts/harness/context-compression.md` 根据你提供的《harness 压缩》转录整理，保留其主要论点与结构；其中语音识别明显不准确的词按上下文作了必要规范化。关于 PaperMod/Hugo 的版本和行为，请以各项目官方文档为准。
