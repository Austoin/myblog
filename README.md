# 博客操作文档

## 快速开始

### 1. 启动开发服务器
```bash
cd myblog
../bin/hugo server
```
- 自动监控文件更改
- 访问：http://localhost:1313/

### 2. 构建生产版本
```bash
cd myblog
../bin/hugo
```
- 生成静态文件到 `public/` 目录

---

## 文章管理

### 创建新文章
```bash
cd myblog
../bin/hugo new posts/文章名.md
```

### 文章Front Matter说明
```yaml
+++
title: "文章标题"
date: '2024-01-01'
draft: false  # 是否为草稿
categories: ["技术"]  # 分类
tags: ["CSS", "HTML"]  # 标签
+++
```

---

## 常用命令

| 命令 | 说明 |
|------|------|
| `hugo server` | 启动开发服务器 |
| `hugo` | 构建静态文件 |
| `hugo new posts/xxx.md` | 创建新文章 |
| `hugo list drafts` | 列出草稿 |
| `hugo -D` | 包括草稿构建 |

---

## 配置说明

### 主要配置文件：`hugo.toml`

```toml
baseURL = 'https://example.org/'
languageCode = 'zh-cn'
title = '我的博客'
theme = 'stack'

[params]
  mainSections = ["posts"]

[params.sidebar]
  emoji = "😄"
  subtitle = "副标题"
  
[menu.main]
  [[menu.main]]
    name = "首页"
    url = "/"
```

---

## 添加功能

### 1. 添加菜单项
在 `hugo.toml` 的 `[menu.main]` 部分添加：
```toml
[[menu.main]]
  name = "页面名"
  url = "/页面路径/"
  weight = 5  # 排序
```

### 2. 添加社交链接
在 `hugo.toml` 的 `[menu.social]` 部分添加：
```toml
[[menu.social]]
  identifier = "github"
  name = "GitHub"
  url = "https://github.com/你的用户名"
  params = { icon = "brand-github", newTab = true }
```

### 3. 添加分类/标签
创建文件 `content/categories/分类名/_index.md`：
```yaml
---
title: "分类名"
description: "描述"
---
```

---

## 文件结构

```
myblog/
├── assets/          # 资源文件（SCSS、图片等）
│   └── img/         # 图片目录
│       └── avatar.png  # 头像
├── content/         # 内容文件
│   ├── posts/       # 文章目录
│   ├── page/        # 页面目录（archives、links等）
│   ├── categories/  # 分类目录
│   └── tags/        # 标签目录
├── static/          # 静态文件（背景图片等）
│   └── background.jpg  # 背景图片
├── themes/          # 主题目录
├── hugo.toml        # 配置文件
└── public/          # 构建输出目录
```

---

## 背景图片

将图片放入 `myblog/static/background.jpg` 即可作为博客背景。

---

## 常见问题

**Q: 如何修改头像？**
A: 替换 `myblog/assets/img/avatar.png` 文件

**Q: 如何修改主题颜色？**
A: 在 `hugo.toml` 中修改 `params.sidebar` 相关配置

**Q: 开发服务器不更新？**
A: 尝试 `Ctrl+C` 停止后重新运行 `hugo server`
