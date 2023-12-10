# 通过GitHub的Actions实现自动部署

> - 可以实现hexo博客的自动部署
> - 可以实现Vue项目的自动打包部署

以我的 iblog 项目为例, 全自动部署流程记录如下, 方便后期查看

## 1. 准备

- iblog_dev 开发仓库
- iblog 部署仓库


## 2. iblog_dev开发仓库相关配置

在你的私有仓库中创建一个名为 .github/workflows/build-and-deploy.yml 的文件，并添加以下内容：