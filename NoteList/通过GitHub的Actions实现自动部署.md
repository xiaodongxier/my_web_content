# 通过GitHub的Actions实现自动部署

> - 可以实现hexo博客的自动部署
> - 可以实现Vue项目的自动打包部署

以我的 iblog 项目为例, 全自动部署流程记录如下, 方便后期查看

## 1. 准备

- iblog_dev 开发仓库
- iblog 部署仓库


## 2. iblog_dev 开发仓库相关配置


在 iblog_dev 仓库的设置中，转到 "Settings" -> "Secrets"，添加两个密钥：

- GH_TOKEN_BLOG: 用于访问 blog 仓库的 Personal Access Token。确保该 Token 具有读写仓库的权限。
- REPO_NAME_BLOG: iblog 仓库的名称。



### 生成个人访问令牌：

1. 进入 GitHub，点击右上角的头像，选择 "Settings"（设置）。
2. 在左侧导航栏中，选择 "Developer settings"（开发者设置）。
3. 在 Developer settings 页面上，选择 "Personal access tokens"（个人访问令牌）。
4. 点击 "Generate token"（生成令牌）。
5. 提供一个说明，选择需要的权限（在这里，至少选择 `repo` 权限以允许读写仓库）。
6. 点击 "Generate token"。
7. 复制生成的个人访问令牌。请记住，令牌只在生成时显示一次，确保保存好。

### 在 GitHub Actions 中使用个人访问令牌：

在 GitHub 仓库中，将个人访问令牌添加为一个 secret，然后在 GitHub Actions 配置文件中引用这个 secret。

1. 进入 GitHub 仓库。
2. 在仓库导航栏中，点击仓库的名称。
3. 在仓库的上方导航栏中，点击 "Settings"（设置）选项。
4. 在左侧导航栏中选择 "Secrets"（密钥）。
5. 点击 "New repository secret"（新建仓库密钥）。
6. 在 "Name" 中输入 `GH_TOKEN_BLOG`，然后在 "Value" 中粘贴之前复制的个人访问令牌。
7. 点击 "Add secret"（添加密钥）。
8. 在你的 GitHub Actions 配置文件（例如 `.github/workflows/build-and-deploy.yml`）中，使用 `${{ secrets.GH_TOKEN_BLOG }}` 引用该个人访问令牌，例如：




















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