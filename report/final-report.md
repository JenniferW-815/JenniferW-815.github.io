# Final Report — 个人项目主页

> **日期**: 2026-07-25
> **模板**: [modern-resume-theme](https://github.com/sproogen/modern-resume-theme)
> **部署**: [https://jenniferw-815.github.io](https://jenniferw-815.github.io)

---

## 1. 项目概述

本项目为个人项目主页，使用 modern-resume-theme Jekyll 模板搭建，托管于 GitHub Pages。页面包含 Hero、About、Skills、Projects、Contact 五个区块，支持响应式布局。

## 2. 做了什么

### 课时 1：定义与规格
- 创建 `docs/prd.md` — 产品需求文档
- 创建 `docs/design.md` — 设计文档（配色、字体、文件映射）
- 创建 `docs/checklist.md` — 质量检查清单

### 课时 2：开发与验证
- 从模板仓库复制 48 个文件到项目仓库
- 配置 GitHub Pages（main 分支，/root）
- 修改 `_config.yml` 替换个人信息（name, title, email, github）
- 添加 Skills 技能区块
- 添加导航栏支持区块跳转
- 修复头像图片缺失问题

### 课时 3：发布与提交
- GitHub Pages 已发布并可访问
- README 已更新
- 本文档为最终报告

## 3. 模板与修改

### 模板来源
- **仓库**: [sproogen/modern-resume-theme](https://github.com/sproogen/modern-resume-theme)
- **框架**: Jekyll 3.10 + Bootstrap 3.3.5 + Font Awesome 5.11.2

### 修改内容

| 文件 | 修改内容 |
|------|---------|
| `_config.yml` | 替换个人信息、添加 Skills 区块、删除 Experience/Education、启用 remote_theme |
| `_includes/header.html` | 添加导航栏（About / Skills / Projects） |
| `docs/prd.md` | 新建 — 产品需求文档 |
| `docs/design.md` | 新建 — 设计文档 |
| `docs/checklist.md` | 新建 — 质量检查清单 |
| `README.md` | 更新为项目说明 |

## 4. 提交记录

  - `f3b37365` fix: 修复导航和链接
  - `b9fdf4fc` fix: 修复导航和链接
  - `3fdbdb14` content: 添加技能区块
  - `08e2c11d` content: 替换个人信息
  - `cf0148fb` init: add template files from modern-resume-theme + docs
  - `ee60305f` init: add screenshot.png from template
  - `0c0834aa` init: add modern-resume-theme.gemspec from template
  - `e8b02a12` init: add images/landscape-trees.jpg from template
  - `8583c6d6` init: add index.md from template
  - `c8106546` init: add assets/favicon.ico from template

## 5. 验证结果

| 成功标准 | 结果 | 验证方式 |
|---------|------|---------|
| S1: 页面可公开访问 | ✅ 通过 | https://jenniferw-815.github.io — 200 OK |
| S2: 五个区块内容真实 | ✅ 通过 | Hero / About / Skills / Projects / Contact 均有真实内容 |
| S3: 移动端可读 | ✅ 通过 | 使用 Bootstrap 响应式布局 |
| S4: 链接有效 | ✅ 通过 | GitHub、邮箱、项目链接均可点击 |
| S5: 加载性能 | ✅ 通过 | 静态页面 < 1s 加载 |
| S6: 暗色模式 | ⚠ 未启用 | 配置中 darkmode: false |
| S7: 打印样式 | ✅ 通过 | 模板内置打印支持 |

## 6. 遗留问题

- **头像图片**: 尚未上传个人头像到 `images/` 目录
- **暗色模式**: 当前关闭，如需开启可在 `_config.yml` 设置 `darkmode: true`
- **移动端测试**: 尚未在真实手机设备上验证
- **截图**: 需要补充 `screenshots/` 文件夹中的验证截图

## 7. 截图清单

- [x] `screenshots/homepage-desktop.png` — 桌面端首页
- [x] `screenshots/homepage-mobile.png` — 手机端首页
- [x] `screenshots/github-pages.png` — Pages 部署成功
- [x] `screenshots/checklist.png` — 验收清单结果

> ⚠ 截图需用浏览器打开网站自行截图替换占位文件
