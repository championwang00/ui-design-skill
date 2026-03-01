# 性能优化指南

## 动画性能

**只动画 `transform` 和 `opacity`。**

避免：padding/margin/height/width、blur > 20px、深层 CSS 变量

```css
.animated { will-change: transform; }
```

## 过渡

- **永远不要** `transition: all`（意外动画+性能问题）
- 指定确切属性：`transition: transform 200ms ease-out`

## 主题切换

- 切换主题时禁用过渡，绘制后重新启用

## 布局性能

- 硬编码尺寸（图片、骨架屏、异步内容）
- `font-variant-numeric: tabular-nums` 处理动态数字
- 不要 hover 时改字重

## React 性能

- 动画在渲染周期外（refs 直接更新样式）
- Framer Motion 用 transform 字符串（硬件加速）：
  ```jsx
  // ✅ 硬件加速
  <motion.div animate={{ transform: "translateX(100px)" }} />
  // ❌ 每帧重渲染
  <motion.div animate={{ x: 100 }} />
  ```

## CSS 性能

- 避免深层组件树动画 CSS 变量
- blur() > 20px 昂贵（Safari 特别慢）

## 加载优化

- 预加载字体和首屏图像
- 静态生成博客/文档/变更日志
- 虚拟化大列表
- `IntersectionObserver` 暂停离屏操作
