# 技术札记｜Hugo + PaperMod（参考风格版）

本项目为 `https://xiaozhang121xz.github.io/` 准备，采用 Hugo + PaperMod + GitHub Pages。

首页和文章页采用简洁、窄版、无卡片边框的技术博客排版；自定义样式写在 `assets/css/extended/custom.css`，不直接复制参考站未声明许可的定制源码。PaperMod 主题本身为 MIT 许可：https://github.com/adityatelange/hugo-PaperMod/。

## 部署

1. 下载并解压本项目。
2. 打开 GitHub Desktop，选择 `xiaozhang121xz.github.io` 仓库，点击 Show in Finder。
3. 将本项目解压后的**内部全部文件**复制到仓库根目录并覆盖同名文件；确认 `.github` 隐藏目录也复制进去。
4. 回到 GitHub Desktop，检查变更，填写 `Use reference-inspired PaperMod styling`，点击 Commit to main，再点击 Push origin。
5. 在 GitHub 仓库 Settings → Pages 中将 Source 设为 GitHub Actions。
6. 在 Actions 中确认部署工作流成功后访问 https://xiaozhang121xz.github.io/。

## 本地预览（可选）

安装 Hugo Extended 后，在项目根目录执行：

```bash
git clone --depth=1 https://github.com/adityatelange/hugo-PaperMod.git themes/PaperMod
hugo server -D
```

## 写新文章

在 `content/posts/` 下创建 Markdown 文件，设置 `draft: false` 后提交即可。

## 目录

- `content/posts/`：文章
- `assets/css/extended/custom.css`：站点自定义样式
- `hugo.yaml`：网站配置
- `.github/workflows/deploy.yml`：自动部署
