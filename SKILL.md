---
name: ui-design
description: "UI 设计工程完整指南。基于 Emil Kowalski animations.dev 课程 + HeroUI 规范。包含动画缓动蓝图、Spring 物理、表单控件、触摸可访问性、组件设计模式、营销页面、性能优化。构建或审查界面时使用。Triggers on: design engineering, UI polish, input fields, form validation, button states, touch devices, mobile UX, accessibility, a11y, keyboard navigation, aria labels, font rendering, typography, layout shift, z-index, animations, transitions, easing, hover effects, tap targets, iOS Safari, prefers-reduced-motion, marketing pages, landing pages, dark mode, theme switching, scrollbars, gradients, shadows, virtualization, preloading, compound components, composition, props API."
---

# UI Design Engineering Skill

构建高质量 Web 界面的完整指南。基于 Emil Kowalski 的 animations.dev 设计工程课程，结合 HeroUI 组件规范。

## 五大核心原则

1. **无布局偏移** — 动态元素不导致页面跳动（hardcoded dimensions, `tabular-nums`, 不改 hover 字重）
2. **触摸优先，Hover 增强** — 先为触摸设计，44px 最小点击目标，`@media (hover: hover)` 守卫
3. **键盘导航** — Tab 只穿过可见元素，`scrollIntoView()` 保证可见性
4. **默认可访问** — 每个动画配 `prefers-reduced-motion`，每个图标按钮配 aria-label
5. **速度优于愉悦** — 产品 UI ≤ 300ms，每天 100+ 次的交互不加动画

## 模块索引

| 模块 | 文件 | 内容 |
|------|------|------|
| 🎬 动画完整指南 | `references/web-animation-design.md` | 缓动函数蓝图（6 级强度）、Spring 配置、AnimatePresence、拖拽手势、频率原则 |
| 🔧 动画实战技巧 | `references/practical-tips.md` | 按钮反馈 scale(0.97)、Hover 修复、工具提示 warm state、transform-origin |
| ✨ UI 抛光 | `references/ui-polish.md` | 排版（字重变量/tabular-nums/text-wrap:balance）、阴影代替边框、hairline 0.5px、eased 渐变、mask-image 淡出、z-index 固定刻度/isolation、深色模式 CSS 变量翻转 |
| 📝 表单控件 | `references/forms-controls.md` | label 关联、16px 防 iOS 缩放、1Password 兼容、input 装饰定位、Cmd+Enter 提交、checkbox 无死区、破坏性操作确认 |
| 👆 触摸与可访问性 | `references/touch-accessibility.md` | touch-action:manipulation、44px 伪元素扩展、video playsinline、visibilitychange 暂停计时、工具提示延迟/warm state、子菜单安全区 clip-path |
| 🧩 组件设计 | `references/component-design.md` | 复合组件 vs prop drilling、Goldilocks 定制层级、asChild/Radix Slot、forwardRef、controlled/uncontrolled 双支持、组件文件结构、反模式（prop 爆炸/boolean 汤/过早抽象）|
| 📢 营销页面 | `references/marketing-pages.md` | 禁止滚动动画/视差/轮播、sessionStorage 控制 intro、静态生成 + revalidation、CTA 登录态切换、文档站 markdown 导出 + RSS |
| ⚡ 性能 | `references/performance.md` | transform/opacity 黄金法则、虚拟化 @tanstack/react-virtual、禁 transition:all、主题切换禁过渡、React ref 避 re-render、Framer Motion 硬件加速写法、IntersectionObserver 离屏暂停 |
| 🎯 HeroUI 规范 | `references/heroui-style.md` | 配色 Token、卡片、字体、间距 |
| 🖼️ 配图资源 | `references/image-resources.md` | LobeHub Icons（品牌Logo）+ Unsplash（通用配图）|
| ✅ 审查清单 | `references/review-checklist.md` | 10 项必查 + 12 个常见错误修复 |

## 快速决策

- **要不要动画？** → 每天 100+ 次就不要（Raycast 原则）
- **用什么缓动？** → 进出场 `ease-out` / 屏幕内移动 `ease-in-out` / hover `ease`
- **多长时间？** → 微交互 100-150ms / 标准 UI 150-250ms / 模态框 200-300ms / 页面 300-400ms
- **动画什么属性？** → 只 `transform` 和 `opacity`（GPU 渲染，跳过 layout+paint）
- **要不要 border？** → 用 `box-shadow: 0 0 0 1px` 替代，retina 用 0.5px
- **要不要 Spring？** → 拖拽/可中断手势/有机界面用 Spring，普通 UI 用 CSS
- **深色模式怎么做？** → CSS 变量 + 数字刻度翻转，不用 Tailwind `dark:`
