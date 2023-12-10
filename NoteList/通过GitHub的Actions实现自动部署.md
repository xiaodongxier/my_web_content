# 通过GitHub的Actions实现自动部署

> - 可以实现hexo博客的自动部署
> - 可以实现Vue项目的自动打包部署

以我的 iblog 项目为例, 全自动部署流程记录如下, 方便后期查看

## 1. 准备

- iblog_dev 开发仓库
- iblog 部署仓库


## 2. iblog_dev 开发仓库相关配置



在 blog_content 仓库的设置中，转到 "Settings" -> "Secrets"，添加两个密钥：

- GH_TOKEN_BLOG: 用于访问 blog 仓库的 Personal Access Token。确保该 Token 具有读写仓库的权限。
- REPO_NAME_BLOG: blog 仓库的名称。





1. 申请 `GH_TOKEN_BLOG` 用于

在你的 iblog_dev 开发仓库中创建一个名为 `.github/workflows/build-and-deploy.yml` 的文件，并添加以下内容：

```shell
name: Build and Deploy

on:
  push:
    branches:
      - master  # 你的默认分支

jobs:
  build-and-deploy:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v2

      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: 14

      - name: Install Dependencies
        run: npm install

      - name: Build
        run: npm run build

      - name: Deploy to Blog Repository
        run: |
          git clone https://${{ secrets.GH_TOKEN_BLOG }}@github.com/{{username}}/{{depot}}.git iblog
          cd iblog
          git config --global user.email "username@gmail.com"
          git config --global user.name "username"
          rm -rf ./*
          cp -r ../dist/* .
          git add .
          git commit -m "update"
          git push
        env:
          REPO_NAME_BLOG: ${{ secrets.REPO_NAME_BLOG }}
```