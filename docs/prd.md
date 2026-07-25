# PRD — 个人项目主页（第一期）

> **仓库模板**: [modern-resume-theme](https://github.com/sproogen/modern-resume-theme) (Jekyll)
> **版本**: 1.0
> **日期**: 2026-07-25

---

## 1. 项目目标

建立一个**可长期更新的个人项目主页**，以简洁、现代的方式集中展示个人履历、技能树与项目作品。页面基于 Jekyll + GitHub Pages 搭建，无需后端，纯静态托管，便于持续维护与版本管理。

---

## 2. 用户场景

| 角色 | 场景 | 需求 |
|------|------|------|
| **同学** | 浏览个人项目与技能，了解近期动态 | 快速找到项目列表、技能标签 |
| **教师 / 导师** | 评估学生能力与项目经验 | 查看 About、Skills、Projects 详情 |
| **未来项目伙伴** | 判断是否适合合作，获取联系方式 | 查看技能匹配度、Contact 信息 |
| **招聘方** | 快速筛选候选人 | 浏览履历、技能、项目链接 |

---

## 3. 本期范围

### 3.1 功能区块

| 区块 | 说明 | 对应模板元件 |
|------|------|-------------|
| **Hero** | 头像 + 姓名 + 标题 + 社交链接 | `header.html` / `_config.yml` (name, title, social) |
| **About** | 个人简介 + 照片 | `about.html` / `site.about_content` |
| **Skills** | 技能清单（技术栈 / 工具） | `section-text.html` 或 `section-list.html` |
| **Projects** | 项目卡片（含链接、描述） | `section-list.html` layout: left |
| **Contact** | 邮箱、电话、社交入口 | `footer.html` + `header-right` |

### 3.2 本期不做

- ❌ 用户登录 / 注册系统
- ❌ 数据库存储
- ❌ 在线支付
- ❌ 复杂后台管理系统
- ❌ 采集访客隐私数据
- ❌ 评论 / 留言功能
- ❌ 多语言国际化

---

## 4. 成功标准

| # | 标准 | 验证方式 |
|---|------|---------|
| S1 | 页面可通过公网访问 | 浏览器打开 GitHub Pages 域名 |
| S2 | 所有展示内容真实、无占位文本 | 目视检查 Hero / About / Skills / Projects / Contact |
| S3 | 在移动端（≤767px）可读且布局合理 | Chrome DevTools 切换设备模拟器 |
| S4 | 所有外部链接（社交、项目）可点击且有效 | 逐一点击验证 |
| S5 | 页面加载无明显延迟（静态页 < 3s） | DevTools Network 面板 |
| S6 | 暗色模式切换正常（如启用） | 点击暗色开关验证 |
| S7 | 打印样式可用 | Ctrl+P 打印预览 |

---

## 5. 技术约束

- **静态站点生成器**: Jekyll (Ruby)
- **托管平台**: GitHub Pages
- **CSS 预处理器**: Sass (SCSS)
- **响应式框架**: Bootstrap 3.3.5
- **图标库**: Font Awesome 5.11.2
- **字体**: Google Fonts — Roboto
- **不支持**: PHP、Node.js 后端、数据库

---

## 6. 数据流

```
用户浏览器 ──HTTP──> GitHub Pages CDN
                         │
                    ┌────┴────┐
                    │ Jekyll  │  (构建时生成静态 HTML)
                    │ 构建    │
                    └────┬────┘
                         │
              ┌──────────┼──────────┐
              │          │          │
         _config.yml  _includes/  _sass/
         (内容数据)  (页面片段)  (样式)
```

- 所有内容修改只需编辑 `_config.yml` 中的 YAML 字段
- 不改动模板源码即可完成内容更新

---

## 7. 未来规划（后续迭代）

| 版本 | 计划内容 |
|------|---------|
| v1.1 | 博客 / 文章模块 |
| v1.2 | 作品集画廊（图片/视频） |
| v2.0 | 自定义主题色切换 |
