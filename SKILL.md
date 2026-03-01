---
name: ui-design
description: UI 设计工程完整指南。包含 Emil Kowalski 动画课程、HeroUI 规范、表单控件、触摸可访问性、组件设计、营销页面、性能优化。构建或审查界面时使用。
---

# UI Design Skill

构建高质量 Web 界面的完整指南。

## 五大核心原则

1. **无布局偏移** — 动态元素不导致页面跳动
2. **触摸优先，Hover 增强** — 先为触摸设计，桌面端加 hover
3. **键盘导航** — Tab 一致且直观
4. **默认可访问** — 不是可选项
5. **速度优于愉悦** — 产品 UI 快且实用

## 模块索引

| 模块 | 文件 | 内容 |
|------|------|------|
| 🎬 动画完整指南 | `references/web-animation-design.md` | 缓动函数蓝图、Spring 动画、性能、可访问性（Emil Kowalski 课程）|
| 🔧 动画实战技巧 | `references/practical-tips.md` | 按钮反馈、Hover 修复、工具提示、触摸目标、视觉技巧 |
| ✨ UI 抛光 | `references/ui-polish.md` | 排版、阴影vs边框、渐变、深色模式、z-index |
| 📝 表单控件 | `references/forms-controls.md` | 输入框、按钮、错误处理 |
| 👆 触摸与可访问性 | `references/touch-accessibility.md` | 44px 目标、键盘导航、ARIA |
| 🧩 组件设计 | `references/component-design.md` | 复合组件、Props API、反模式 |
| 📢 营销页面 | `references/marketing-pages.md` | 滚动动画禁忌、CTA、文档站点 |
| ⚡ 性能 | `references/performance.md` | transform/opacity、虚拟化、预加载 |
| 🎯 HeroUI 规范 | `references/heroui-style.md` | 配色 Token、卡片、字体、间距 |
| 🖼️ 配图资源 | `references/image-resources.md` | LobeHub Icons（品牌Logo）+ Unsplash（通用配图）|
| ✅ 审查清单 | `references/review-checklist.md` | 10 项必查 + 常见错误 |

## 快速决策

- **要不要动画？** → 每天 100+ 次就不要
- **用什么缓动？** → 默认 `ease-out`
- **多长时间？** → ≤ 300ms
- **动画什么属性？** → 只 `transform` 和 `opacity`
- **要不要 border？** → 用阴影替代
