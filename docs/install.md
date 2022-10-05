# 安装
1. 创建一个公开仓库
2. 添加文件 `mkdocs.yml` 并添加以下内容

```
site_name: 文档名
theme:
  name: material
  language: zh
  features:
    - navigation.instant
  palette:
    # Palette toggle for light mode
    - media: "(prefers-color-scheme: light)"
      scheme: default 
      toggle:
        icon: material/brightness-7
        name: Switch to dark mode

    # Palette toggle for dark mode
    - media: "(prefers-color-scheme: dark)"
      scheme: slate
      toggle:
        icon: material/brightness-4
        name: Switch to system preference
extra:
  generator: false
repo_url: 你的仓库
edit_uri: edit/main/docs/
plugins:
  - git-revision-date-localized:
      enable_creation_date: true
```
3. 添加文件 `` 并添加以下内容

```
name: ci 
on:
  push:
    branches:
      - master 
      - main
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - uses: actions/setup-python@v2
        with:
          python-version: 3.x
      - run: pip install mkdocs-material 
      - run: pip install mkdocs-git-revision-date-localized-plugin 
      - run: mkdocs gh-deploy --force
```
4. 现在，当新的提交推送到`master/main`分支时，静态站点会自动构建和部署。推送您的更改以查看工作流程的实际效果。

如果 GitHub 页面在几分钟后未显示，请转到存储库的设置，并确保 GitHub 页面的发布源分支设置为 。gh-pages

您的文档应很快显示在 上。<username>.github.io/<repository>
5. 在/docs文件夹开始写作 `首页index.md`

![[Fork](https://github.com/xiaoioi/mkdocs-githubActions/fork)](https://img.shields.io/badge/Fork-orange)
![[Star](https://github.com/xiaoioi/mkdocs-githubActions/)](https://img.shields.io/badge/Star-orange)