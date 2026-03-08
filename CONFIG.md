# Landing Page 配置说明

## 1. Formspree 邮箱收集集成

### 步骤

1. **注册 Formspree**
   - 访问 https://formspree.io
   - 使用邮箱注册免费账户
   - 验证邮箱

2. **创建表单**
   - 登录后点击 "New Form"
   - 填写表单名称（如 "AI 效率实验室订阅"）
   - 设置接收邮箱（订阅邮件将发送到此邮箱）
   - 点击 "Create Form"

3. **获取 Form ID**
   - 创建成功后，表单 URL 格式：`https://formspree.io/f/xnqleybz`
   - 最后 8 位字符即为 Form ID（如 `xnqleybz`）

4. **更新代码**
   - 编辑 `index.html`
   - 找到第 77 行左右：
     ```html
     <form action="https://formspree.io/f/PLACEHOLDER_FORM_ID" method="POST">
     ```
   - 替换 `PLACEHOLDER_FORM_ID` 为你的 Form ID
   - 例如：`https://formspree.io/f/xnqleybz`

5. **推送到 GitHub**
   ```bash
   git add index.html
   git commit -m "Configure Formspree with real form ID"
   git push
   ```

6. **测试**
   - 访问 https://hfbbob.github.io/ailab-landing/
   - 在邮箱收集表单输入测试邮箱
   - 提交后检查 Formspree 后台和接收邮箱

### 免费额度

- 500 提交/月
- 7 天数据保留
- 足够 MVP 阶段使用

### 升级方案

当超过 500 提交/月时：
- 升级到 Silver 计划：$10/月（2000 提交）
- 或自建后端（Node.js + 数据库）

---

## 2. Umami Analytics 流量追踪

### 方案 A: Umami Cloud（推荐 MVP）

1. **注册 Umami Cloud**
   - 访问 https://cloud.umami.is
   - 使用 GitHub/Google 账号登录

2. **添加网站**
   - 点击 "Add Website"
   - 填写：
     - Name: AI 效率实验室
     - Domain: hfbbob.github.io
   - 点击 "Save"

3. **获取 Website ID**
   - 在网站列表中点击你的网站
   - 复制 Website ID（UUID 格式）

4. **更新代码**
   - 编辑 `index.html`
   - 找到 `<head>` 部分（约第 12 行）
   - 取消注释并替换：
     ```html
     <script async defer data-website-id="YOUR_WEBSITE_ID" src="https://cloud.umami.is/script.js"></script>
     ```

5. **推送到 GitHub**（同上）

### 方案 B: 自托管 Umami

如果需要完全控制数据：

```bash
# Docker 部署
docker run -d \
  --name umami \
  -p 3000:3000 \
  -e DATABASE_URL=postgresql://umami:umami@db:5432/umami \
  ghcr.io/umami-software/umami:postgresql-latest
```

详见：https://umami.is/docs/install

### 免费额度（Umami Cloud）

- 5,000 页面浏览/月
- 3 个网站
- 数据保留 3 个月

---

## 3. 自定义域名（可选）

### 步骤

1. **购买域名**
   - 推荐：Namecheap, Cloudflare, GoDaddy
   - 价格：~$10-15/年

2. **配置 DNS**
   - 添加 CNAME 记录：
     - Name: www
     - Value: hfbbob.github.io
   - 或 A 记录：
     - Name: @
     - Value: 185.199.108.153（GitHub Pages IP）

3. **GitHub 配置**
   - 仓库 → Settings → Pages
   - Custom domain: 输入你的域名
   - Save

4. **HTTPS**
   - GitHub 自动提供 HTTPS
   - 等待证书生成（约 5-10 分钟）

---

## 4. 验证清单

上线前检查：

- [ ] Formspree Form ID 已替换
- [ ] Umami Website ID 已配置
- [ ] 测试表单提交功能
- [ ] 测试 Analytics 追踪
- [ ] 检查所有链接正常
- [ ] 移动端显示正常

---

## 5. 后续优化建议

### 短期（1 周）
- [ ] 添加 404 错误页面
- [ ] 添加 favicon 图标
- [ ] 优化 SEO meta 标签

### 中期（1 月）
- [ ] 添加 A/B 测试（如不同 CTA 文案）
- [ ] 集成邮件营销工具（Mailchimp/ConvertKit）
- [ ] 添加社交分享按钮

### 长期
- [ ] 多语言支持（中英文）
- [ ] 博客/内容板块
- [ ] 用户登录/仪表板

---

*最后更新：2026-03-08*
