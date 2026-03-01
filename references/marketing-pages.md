# 营销页面指南

## 动画

- **不要**加滚动动画（淡入、translate-Y）
- **不要**断开连接的运动（滚动劫持、非 1:1 视差、自动轮播）
- 介绍动画看过一次后禁用（用 `sessionStorage`）

## 性能

- 预加载字体防布局偏移
- 预加载首屏图像
- 博客/变更日志/文档静态生成（构建时），不按需获取

## 导航

- 标题子菜单内容在 DOM 中可见（可访问性+SEO）

## CTA 按钮

- 未登录：`"Get Started"` / `"Sign Up"`
- 已登录：`"Go to Dashboard"` / `"Open App"`

## 文档站点

- 代码片段有复制按钮
- 页面可导出 Markdown（URL 加 `.md`）
- 多视觉示例，不只是代码

## 博客/变更日志

- RSS：`/blog/rss.xml`、`/changelog/rss.xml`
- 标题用 `text-wrap: balance`

## 插图

- `aria-label` + 禁用文本选择 + 禁用 `pointer-events`
