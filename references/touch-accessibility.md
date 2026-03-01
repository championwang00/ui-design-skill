# 触摸与可访问性指南

## 触摸设备

### Hover
```css
@media (hover: hover) and (pointer: fine) {
  .element:hover { transform: scale(1.05); }
}
```
触摸设备点击会触发 hover → 只在桌面端启用。

### 触摸操作
- `touch-action: manipulation` 防止双击缩放
- 自定义手势组件禁用默认 `touch-action`

### 点击目标
- **最小 44px**（Apple/Google 指南）
- 视觉可以更小，用 padding 或伪元素扩大点击区域

### 视频
- `<video muted playsinline>` 在 iOS 自动播放不全屏

### 快捷键
- Mac 显示 `⌘`，Windows 显示 `Ctrl`

## 键盘导航

- Tab 只聚焦可见元素
- 不可见元素用 `visibility: hidden` 或 `inert`
- 键盘导航时 `scrollIntoView()` 确保可见
- 模态框：打开聚焦第一个交互元素，关闭返回触发元素

## 可访问性

- 图标按钮必须有 `aria-label`
- 装饰插图禁用文本选择和指针事件
- 每个动画都需要 `prefers-reduced-motion`
- 偏好减少运动时显示播放按钮而非自动播放
- 时间限制操作在切标签页时冻结（`visibilitychange`）

## 工具提示

- 有延迟防误触
- 顺序工具提示：第一个打开后，后续立即显示（无延迟无动画）

## 子菜单

- 用 `clip-path` 安全区域，允许对角线移动
