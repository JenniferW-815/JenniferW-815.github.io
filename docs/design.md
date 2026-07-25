# Design — 个人项目主页（第一期）

> **基于模板**: [modern-resume-theme](https://github.com/sproogen/modern-resume-theme)
> **版本**: 1.0
> **日期**: 2026-07-25

---

## 1. 页面结构

```
┌─────────────────────────────────────┐
│              HEAD                   │  (head.html — meta, SEO, 样式、字体)
├─────────────────────────────────────┤
│              HEADER                 │  (header.html)
│   ┌───────────┐  ┌──────────────┐  │
│   │  姓名      │  │  社交图标    │  │
│   │  标题      │  │  邮箱/电话   │  │
│   └───────────┘  └──────────────┘  │
├─────────────────────────────────────┤
│          HERO (复用 Header)         │  — 首屏视觉重心
├─────────────────────────────────────┤
│          ABOUT 区块                 │  (about.html)
│   ┌───────────┐  ┌──────────────┐  │
│   │  头像图片  │  │  个人简介    │  │
│   └───────────┘  └──────────────┘  │
├─────────────────────────────────────┤
│          SKILLS 区块                │  (section-text.html)
│   ┌─────────────────────────────┐  │
│   │  技能描述 / 标签列表         │  │
│   └─────────────────────────────┘  │
├─────────────────────────────────────┤
│          PROJECTS 区块              │  (section-list.html, layout: left)
│   ┌─────┬───────────────────────┐  │
│   │ 项目 │  描述 + 链接 + 图标   │  │
│   │ 名称 │                       │  │
│   └─────┴───────────────────────┘  │
│   ┌─────┬───────────────────────┐  │
│   │ ...  │  （多个项目卡片）      │  │
│   └─────┴───────────────────────┘  │
├─────────────────────────────────────┤
│          CONTACT 区块               │  (footer.html + header-right)
│   ┌─────────────────────────────┐  │
│   │  邮箱 | 电话 | 社交链接      │  │
│   └─────────────────────────────┘  │
├─────────────────────────────────────┤
│             FOOTER                  │  (footer.html)
└─────────────────────────────────────┘
```

### 区块对应关系

| 区块 | 模板文件 | 数据来源 |
|------|---------|---------|
| Hero | `_includes/header.html` | `_config.yml`: name, title, social |
| About | `_includes/about.html` | `_config.yml`: about_profile_image, about_content |
| Skills | `_includes/section-text.html` | `_config.yml`: content[].layout: text |
| Projects | `_includes/section-list.html` | `_config.yml`: content[].layout: list |
| Contact | `_includes/header.html` + `_includes/footer.html` | `_config.yml`: email, phone, social |
| Layout 外壳 | `_layouts/default.html` | 自动组装所有 include |

---

## 2. 颜色方案

### 主色

| 角色 | 色值 | 用途 |
|------|------|------|
| **Primary** | `#477dca` | 链接、按钮、可点击元素 |
| **Text** | `#333333` | 正文文字、标题 |
| **Background** | `#ffffff` | 页面背景 |
| **Border** | `#CCCCCC` | 分割线、区块边界 |

### 暗色模式覆盖

| 角色 | 色值 |
|------|------|
| Background | `#222222` |
| Text | `#e6e6e6` |
| Link | `#477dca`（不变） |

> 颜色修改入口：`_sass/base.scss` (link: `#477dca`)、`_sass/type.scss` (body: `#333`)、`_sass/dark.scss`

---

## 3. 字体层级

| 元素 | 字体 | 字号 | 字重 | 行高 |
|------|------|------|------|------|
| h1 (姓名) | Roboto | 4rem | 500 | 1.2 |
| h2 (标题) | Roboto | 2rem | 300 | 1.2 |
| h3 (区块标题) | Roboto | 3rem | 300 | 1.2 |
| h4 (项目名) | Roboto | 2.5rem | 300 | 1.2 |
| 正文 / 列表 | Roboto | 1.6rem | 400 | 1.5 |
| 辅助文字 | Roboto | 1.4rem | 300 | 1.5 |

> 字体来源: Google Fonts — Roboto (100, 300, 400, 500, 700 + italic)

---

## 4. 文件映射关系

```
project-root/
├── _config.yml              ← 核心数据源（个人信息、社交、内容区块）
├── index.md                 ← 入口页面（front matter + 空内容，复用 layout）
├── _layouts/
│   └── default.html         ← 页面骨架（组装 header + about + sections + footer）
├── _includes/
│   ├── head.html            ← <head> 元信息、SEO、样式引入
│   ├── header.html          ← Hero: 姓名、标题、社交图标、联系方式
│   ├── about.html           ← About: 头像 + 个人简介
│   ├── section-list.html    ← Projects: 列表式内容区块
│   ├── section-text.html    ← Skills: 纯文本内容区块
│   ├── footer.html          ← Contact / Footer: 邮箱、引用
│   └── a.html               ← 通用外链组件 (target="_blank")
├── _sass/
│   ├── base.scss            ← 基础样式、导入外部资源
│   ├── type.scss            ← 排版规则
│   ├── button.scss          ← 按钮样式
│   ├── icons.scss           ← 图标样式
│   ├── dark.scss            ← 暗色模式
│   └── modern-resume-theme.scss ← 主样式入口 + 自定义覆盖
├── assets/
│   ├── main.scss            ← Jekyll 样式入口 (front matter)
│   ├── favicon.ico          ← 网站图标
│   └── js/
│       └── index.js         ← 暗色模式切换等交互
└── images/                  ← 图片资源（头像、项目截图等）
```

### 内容编辑流程

1. 编辑 `_config.yml` 中的个人信息（name, title, email, phone）
2. 在 `about_profile_image` 中指定头像路径
3. 在 `about_content` 中写个人简介（支持 Markdown）
4. 在 `content` 下添加 Skills（layout: text）和 Projects（layout: list）
5. 放入头像图片到 `images/` 目录
6. 提交并推送，GitHub Pages 自动构建

---

## 5. 响应式设计要求

### 断点

| 断点 | 宽度 | 行为 |
|------|------|------|
| 手机 | ≤ 767px | 单栏布局，header 居中对齐，头像全宽 |
| 平板 | 768px - 991px | 两栏混合布局 |
| 桌面 | ≥ 992px | 完整三栏/四栏布局 |

### 响应式要点

- **Header**: 手机端居中对齐，桌面端左对齐（header-left）/ 右对齐（header-right）
- **About**: 手机端头像占满宽度，桌面端头像 200x200 圆形左对齐
- **Projects (layout: left)**: 手机端项目卡片纵向堆叠，项目名称在上、描述在下
- **所有图标**: Font Awesome 自动随视口缩放
- **图片**: Bootstrap `img-responsive` 确保不溢出容器
- **打印**: @media print 规则精简字体与间距
- **触摸目标**: 链接/按钮不少于 44px 点击区域

### 验证工具

- Chrome DevTools 设备模拟器（iPhone X / iPad / 响应式模式）
- 实际真机测试（Android / iOS）
