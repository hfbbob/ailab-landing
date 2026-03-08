# AI 效率实验室 Landing Page - 技术文档

*最后更新：2026-03-08*

---

## 📁 项目结构

```
ailab-landing/
├── index.html          # 主页面（单页应用）
├── CONFIG.md           # 配置指南（Formspree, Umami 等）
├── TECHNICAL.md        # 本文档
├── ONBOARDING.md       # 团队 Onboarding 指南
└── README.md           # 项目说明
```

---

## 🛠️ 技术栈

### 核心选型

| 技术 | 版本 | 用途 | 选择理由 |
|------|------|------|----------|
| **HTML5** | - | 页面结构 | 语义化、SEO 友好 |
| **Tailwind CSS** | CDN v3 | 样式 | 快速开发、响应式、无需构建 |
| **Vanilla JS** | - | 交互逻辑 | 轻量、无需框架依赖 |
| **Formspree** | - | 邮箱收集 | 免费、无需后端、5 分钟集成 |
| **GitHub Pages** | - | 托管部署 | 免费、HTTPS、自动部署 |

### 技术决策说明

#### 为什么选择纯 HTML + Tailwind CSS？

**优势**：
- ✅ 零构建步骤，直接编辑 HTML
- ✅ GitHub Pages 原生支持
- ✅ 加载速度快（无 JS 框架）
- ✅ 易于维护和修改
- ✅ 团队成员无需前端经验即可修改

**对比其他方案**：

| 方案 | 优势 | 劣势 | 决策 |
|------|------|------|------|
| **纯 HTML + Tailwind** | 简单、快速 | 功能有限 | ✅ 采用（MVP） |
| **VitePress** | 文档友好、Markdown | 学习成本 | ⏸️ 后续考虑 |
| **Astro** | 性能优、组件化 | 需要构建 | ⏸️ 后续考虑 |
| **Next.js** | 功能全、SSR | 过重、需 Node.js | ❌ 不适合 MVP |

#### 为什么选择 Formspree？

**优势**：
- ✅ 免费额度够用（500 提交/月）
- ✅ 无需后端代码
- ✅ 自动转发到邮箱
- ✅ 5 分钟配置完成

**对比**：
- vs 自建后端：Formspree 无需维护
- vs Mailchimp：Formspree 更轻量
- vs Google Forms：Formspree 可自定义样式

---

## 🚀 部署流程

### GitHub Pages 自动部署

```bash
# 1. 本地修改
git add index.html
git commit -m "feat: 更新内容"

# 2. 推送到 main 分支
git push origin main

# 3. 等待 1-2 分钟，GitHub Pages 自动更新
# 访问：https://hfbbob.github.io/ailab-landing/
```

### 部署验证

```bash
# 检查页面是否更新
curl -I https://hfbbob.github.io/ailab-landing/

# 预期：HTTP 200
```

### 部署故障排查

| 问题 | 原因 | 解决方案 |
|------|------|----------|
| 404 Not Found | Pages 未启用 | Settings → Pages → 启用 |
| 页面未更新 | 缓存问题 | 等待 2 分钟或强制刷新 |
| 样式丢失 | Tailwind CDN 加载失败 | 检查网络连接 |

---

## ⚙️ 配置说明

### Formspree 邮箱收集

**配置文件**: `index.html` (约第 77 行)

```html
<form action="https://formspree.io/f/xojkvnqo" method="POST">
```

**修改步骤**:
1. 登录 https://formspree.io
2. 找到对应表单
3. 复制 Form ID
4. 替换 URL 中的 `xojkvnqo`

**测试**:
```bash
curl -X POST "https://formspree.io/f/xojkvnqo" \
  -d "email=test@example.com"
```

### Umami Analytics（可选）

**配置文件**: `index.html` (约第 12 行)

```html
<!-- 取消注释并替换 Website ID -->
<script async defer data-website-id="YOUR_ID" src="https://cloud.umami.is/script.js"></script>
```

**配置步骤**:
1. 访问 https://cloud.umami.is
2. 添加网站
3. 获取 Website ID
4. 替换 `YOUR_ID`

详见：`CONFIG.md`

---

## 📝 开发规范

### 代码风格

**HTML**:
- 使用语义化标签（`<header>`, `<section>`, `<footer>`）
- 添加注释说明各部分功能
- 类名使用 Tailwind 工具类

**CSS**:
- 优先使用 Tailwind 工具类
- 避免内联样式
- 响应式断点：`sm:`, `md:`, `lg:`

**JavaScript**:
- 使用 `const`/`let`，避免 `var`
- 添加错误处理
- 避免阻塞式操作

### 提交规范

**Commit Message 格式**:
```
<type>: <description>

[optional body]
```

**Type 类型**:
- `feat`: 新功能
- `fix`: 修复 bug
- `docs`: 文档更新
- `style`: 代码格式
- `refactor`: 重构
- `test`: 测试相关
- `chore`: 构建/工具

**示例**:
```bash
git commit -m "feat: 添加邮箱收集功能"
git commit -m "fix: 修复移动端样式问题"
git commit -m "docs: 更新配置文档"
```

---

## ❓ 常见问题 FAQ

### Q: 如何修改页面内容？

**A**: 直接编辑 `index.html`，找到对应部分修改文字即可。

```html
<!-- 修改标题 -->
<h1>新的标题</h1>
```

### Q: 如何添加新板块？

**A**: 复制现有 `<section>` 结构，修改内容和类名。

```html
<section id="new-section" class="py-16 bg-white">
  <!-- 新内容 -->
</section>
```

### Q: 如何修改颜色主题？

**A**: 修改 Tailwind 颜色类名。

```html
<!-- 蓝色主题 -->
<div class="bg-blue-600 text-white">

<!-- 紫色主题 -->
<div class="bg-purple-600 text-white">
```

### Q: Formspree 提交失败？

**A**: 检查：
1. Form ID 是否正确
2. 邮箱是否已验证
3. 是否超过免费额度

### Q: GitHub Pages 不更新？

**A**: 
1. 确认推送到 `main` 分支
2. 检查 Settings → Pages 配置
3. 等待 2-5 分钟缓存刷新

---

## 📊 性能指标

### 页面大小

| 资源 | 大小 |
|------|------|
| HTML | ~10 KB |
| Tailwind CSS (CDN) | ~30 KB (gzip) |
| JavaScript | ~1 KB |
| **总计** | **~41 KB** |

### 加载速度

- **首屏时间**: < 1 秒
- **完全加载**: < 2 秒
- **Lighthouse 分数**: 90+

### 优化建议

- [ ] 压缩图片（如有）
- [ ] 使用 WebP 格式
- [ ] 启用浏览器缓存
- [ ] 考虑本地化 Tailwind（减少 CDN 依赖）

---

## 🔗 相关链接

- **GitHub 仓库**: https://github.com/hfbbob/ailab-landing
- **在线预览**: https://hfbbob.github.io/ailab-landing/
- **Tailwind CSS**: https://tailwindcss.com
- **Formspree**: https://formspree.io
- **Umami**: https://umami.is
- **GitHub Pages**: https://pages.github.com

---

*维护人：developer (CTO)*  
*问题反馈：@developer:matrix-local.hiclaw.io:18080*
