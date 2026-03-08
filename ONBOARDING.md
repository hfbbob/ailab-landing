# AI 效率实验室 Landing Page - Onboarding 指南

*新成员快速开始指南*  
*最后更新：2026-03-08*

---

## 👋 欢迎加入！

这是 AI 效率实验室的 Landing Page 项目。本指南帮助你快速上手开发和贡献代码。

**预计时间**：30 分钟完成配置

---

## 📋 目录

1. [项目简介](#项目简介)
2. [开发环境配置](#开发环境配置)
3. [代码库结构](#代码库结构)
4. [开发流程](#开发流程)
5. [代码规范](#代码规范)
6. [常见问题](#常见问题)
7. [联系方式](#联系方式)

---

## 项目简介

**什么是 Landing Page？**

Landing Page 是公司的官方落地页，用于：
- 📢 展示公司定位和价值主张
- 🎯 介绍核心服务和优势
- 📧 收集潜在用户邮箱
- 🔗 提供联系方式

**技术栈**：
- HTML5 + Tailwind CSS
- Formspree（邮箱收集）
- GitHub Pages（托管）

**在线访问**：https://hfbbob.github.io/ailab-landing/

---

## 开发环境配置

### 必需工具

| 工具 | 版本 | 用途 | 下载链接 |
|------|------|------|----------|
| **Git** | 最新 | 版本控制 | https://git-scm.com |
| **文本编辑器** | 任意 | 代码编辑 | VS Code / Sublime / Notion++ |
| **浏览器** | 最新 | 预览测试 | Chrome / Firefox |

### 可选工具

| 工具 | 用途 |
|------|------|
| **VS Code** | 推荐编辑器（支持 Tailwind 智能提示） |
| **Live Server 插件** | 本地预览 |
| **Prettier** | 代码格式化 |

### 配置步骤

#### 1. 安装 Git

```bash
# macOS
brew install git

# Windows
# 下载 https://git-scm.com/download/win

# Linux
sudo apt-get install git
```

#### 2. 配置 Git 用户

```bash
git config --global user.name "你的名字"
git config --global user.email "你的邮箱@example.com"
```

#### 3. 克隆仓库

```bash
git clone https://github.com/hfbbob/ailab-landing.git
cd ailab-landing
```

#### 4. 本地预览（可选）

```bash
# 使用 Python 快速启动本地服务器
python3 -m http.server 8080

# 访问 http://localhost:8080
```

或使用 VS Code 的 Live Server 插件。

---

## 代码库结构

```
ailab-landing/
├── index.html          # 主页面（主要工作文件）
├── README.md           # 项目说明
├── TECHNICAL.md        # 技术文档
├── ONBOARDING.md       # 本文档
└── CONFIG.md           # 配置指南
```

### 核心文件说明

#### index.html

单页应用，包含所有页面内容：

| 部分 | 行号范围 | 说明 |
|------|----------|------|
| Header | ~10-25 | 导航栏 |
| Hero Section | ~27-50 | 价值主张 + CTA |
| About Section | ~52-80 | 核心优势（3 个） |
| Services Section | ~82-130 | 服务内容（4 个） |
| Newsletter Section | ~132-160 | 邮箱收集表单 |
| Contact Section | ~162-175 | 联系方式 |
| Footer | ~177-185 | 页脚 |

---

## 开发流程

### 1. 获取任务

从 CEO 或项目房间接收任务，例如：
- "修改 Hero 部分文案"
- "添加新的服务项"
- "更新联系方式"

### 2. 创建分支（可选）

小修改可直接在 `main` 分支：
```bash
git checkout main
git pull
```

大功能建议创建分支：
```bash
git checkout -b feature/new-section
```

### 3. 编辑代码

使用文本编辑器打开 `index.html`，找到对应部分修改。

**示例：修改标题**
```html
<!-- 原内容 -->
<h1>用 AI 提升工作效能</h1>

<!-- 修改后 -->
<h1>用 AI 提升 10 倍工作效率</h1>
```

### 4. 本地测试（可选）

```bash
# 启动本地服务器
python3 -m http.server 8080

# 访问 http://localhost:8080 预览
```

### 5. 提交代码

```bash
# 查看修改
git status
git diff

# 添加文件
git add index.html

# 提交（使用规范的 commit message）
git commit -m "feat: 更新 Hero 部分文案"

# 推送
git push origin main
```

### 6. 验证部署

等待 1-2 分钟后访问：
- https://hfbbob.github.io/ailab-landing/

检查修改是否生效。

---

## 代码规范

### HTML 规范

**语义化标签**：
```html
✅ 推荐
<header>...</header>
<section id="hero">...</section>
<footer>...</footer>

❌ 避免
<div class="header">...</div>
<div class="section">...</div>
```

**添加注释**：
```html
<!-- Hero Section: 价值主张 + CTA -->
<section id="hero">
  <!-- 邮箱收集表单 -->
  <form>...</form>
</section>
```

**类名顺序**（Tailwind）：
```html
✅ 推荐
<div class="flex items-center justify-between bg-white p-4 rounded-lg">

❌ 混乱
<div class="p-4 flex bg-white rounded-lg items-center justify-between">
```

### Commit Message 规范

**格式**：
```
<type>: <description>
```

**Type 类型**：

| Type | 说明 | 示例 |
|------|------|------|
| `feat` | 新功能 | `feat: 添加 FAQ 部分` |
| `fix` | 修复 bug | `fix: 修复移动端样式` |
| `docs` | 文档更新 | `docs: 更新 README` |
| `style` | 代码格式 | `style: 格式化 HTML` |
| `refactor` | 重构 | `refactor: 优化表单结构` |
| `chore` | 工具/配置 | `chore: 更新 .gitignore` |

**示例**：
```bash
✅ feat: 添加邮箱收集功能
✅ fix: 修复联系方式邮箱错误
✅ docs: 添加 Onboarding 文档
❌ 更新代码
❌ 修改了一些东西
```

### 命名规范

**Section ID**：
```html
✅ 推荐
<section id="hero">
<section id="features">
<section id="contact">

❌ 避免
<section id="Hero_Section">
<section id="123">
```

**CSS 类名**：
- 使用 Tailwind 工具类
- 避免自定义类名（除非必要）

---

## 常见问题

### Q: 修改后页面没更新？

**A**: 
1. 确认已 `git push`
2. 等待 2-5 分钟（GitHub Pages 缓存）
3. 强制刷新浏览器（Ctrl+F5 / Cmd+Shift+R）

### Q: 如何添加新板块？

**A**: 复制现有 `<section>` 结构：

```html
<!-- 复制并修改 -->
<section id="new-section" class="py-16 bg-white">
  <div class="max-w-6xl mx-auto px-4">
    <h2 class="text-3xl font-bold text-center mb-12">新标题</h2>
    <!-- 新内容 -->
  </div>
</section>
```

### Q: Tailwind 类名不生效？

**A**: 
1. 检查拼写错误
2. 确认 Tailwind CDN 加载正常
3. 查看浏览器控制台错误

### Q: 如何修改颜色主题？

**A**: 替换颜色类名：

```html
<!-- 蓝色 → 紫色 -->
<div class="bg-blue-600"> → <div class="bg-purple-600">
```

### Q: 表单提交失败？

**A**: 
1. 检查 Form ID 是否正确
2. 确认邮箱已验证
3. 查看 Formspree 后台

### Q: 如何回滚修改？

**A**: 
```bash
# 查看历史提交
git log

# 回滚到上一个版本
git revert HEAD

# 或重置（谨慎使用）
git reset --hard <commit-hash>
```

---

## 联系方式

### 团队沟通

| 渠道 | 用途 |
|------|------|
| **Matrix Room** | 日常沟通、任务分配 |
| **GitHub Issues** | Bug 报告、功能建议 |
| **GitHub PR** | 代码审查 |

### 关键人员

| 角色 | 联系人 | Matrix ID |
|------|--------|-----------|
| **CEO** | 大牛 | @manager:matrix-local.hiclaw.io:18080 |
| **CTO** | developer | @developer:matrix-local.hiclaw.io:18080 |

### 获取帮助

1. **查看文档**：`TECHNICAL.md`, `CONFIG.md`
2. **Matrix 提问**：在团队房间 @CTO
3. **GitHub Issue**：创建 Issue 描述问题

---

## ✅ Onboarding 检查清单

完成以下任务确认你已准备好：

- [ ] 已安装 Git 并配置用户
- [ ] 已克隆仓库到本地
- [ ] 已本地预览页面
- [ ] 已阅读代码规范
- [ ] 已了解提交流程
- [ ] 已加入 Matrix 团队房间

**完成？** 向 CEO 或 CTO 确认，开始你的第一个任务！

---

## 📚 进阶资源

- **Tailwind CSS 官方文档**: https://tailwindcss.com/docs
- **HTML5 语义化**: https://developer.mozilla.org/zh-CN/docs/Glossary/Semantics
- **Git 教程**: https://git-scm.com/book/zh/v2
- **GitHub Pages**: https://pages.github.com/

---

*欢迎提问，祝开发愉快！* 🚀

*维护人：developer (CTO)*
