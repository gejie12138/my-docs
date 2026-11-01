# 我的技术文档

使用 MkDocs 和 Material 主题构建文档，通过 GitHub Actions 部署到 GitHub Pages。

## 目录结构

```text
my-docs/
├── docs/
│   ├── index.md
│   ├── about.md
│   ├── guide.md
│   └── api.md
├── .github/
│   └── workflows/
│       └── deploy.yml
├── mkdocs.yml
└── README.md
```

## 本地预览

在 my-docs 目录下运行：

```powershell
python -m pip install mkdocs-material
python -m mkdocs serve
```

访问终端输出的本地地址。只构建静态文档时运行 `python -m mkdocs build`，输出位于 `site/`。

## 部署到 GitHub Pages

1. 将 my-docs 目录中的内容作为 GitHub 仓库根目录上传，确保 `.github/workflows/deploy.yml` 位于仓库根目录下。
2. 工作流按课件配置监听 `main` 分支。如果实际使用 `master`，请将 deploy.yml 中 `branches` 下的 `main` 改为 `master`。
3. 推送文档或配置变更后，在仓库 Actions 页面查看部署结果；也可以通过 Run workflow 手动触发。
4. 首次部署成功后，在仓库 Settings → Pages 中选择 Deploy from a branch，分支选择 `gh-pages`，目录选择 `/ (root)`，保存。

工作流在课件示例基础上补充了部署所需的 `contents: write` 权限、手动触发入口，以及工作流文件自身的变更触发条件。
