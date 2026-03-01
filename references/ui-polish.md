# UI 抛光指南

## 排版

### 字体渲染
- 始终：`-webkit-font-smoothing: antialiased`

### 防止布局偏移
- **字体粗细**：永远不要在 hover/选中时改变字重，用颜色区分
- **表格数字**：`font-variant-numeric: tabular-nums`（计数器、价格、计时器）
- **文本换行**：标题用 `text-wrap: balance`

### 字母间距
- 大文本 → 紧字母间距
- 小文本 → 松字母间距

### 排版字符
- `…` 非 `...`（省略号）
- `'` 非 `'`（卷曲撇号）
- `"` `"` 非 `"`（卷曲引号）

## 视觉设计

### 阴影代替边框
```css
box-shadow: 0 0 0 1px rgba(0, 0, 0, 0.08);
```
比普通 border 更好地融入背景。

### 细线边框
Retina 用 0.5px：
```css
--border-width: 1px;
@media (-webkit-min-device-pixel-ratio: 2) {
  --border-width: 0.5px;
}
```

### 渐变
- 用缓动渐变替代线性渐变（更平滑无条带）
- 淡入淡出优先用 `mask-image` 而非渐变
- **不要**在可滚动内容上加淡入淡出

### 滚动条
- 不要替换页面滚动条
- 只在小元素（代码片段）中自定义

### 焦点轮廓
- 不改默认轮廓颜色（灰/黑/白以外的颜色会冲突）

## 布局

### Z-Index
- 用固定比例，不要 `z-index: 9999`
- 用 `isolation: isolate` 创建堆叠上下文

### 安全区域
```css
padding-bottom: env(safe-area-inset-bottom);
```

### 滚动边距
```css
scroll-margin-top: 80px; /* 锚点链接留空间 */
```

### 网格文本截断
- 用 `line-clamp` 截断

## 深色模式

- 用数值比例 CSS 变量，不用 Tailwind `dark:` 手动调
- 装饰元素禁用 `pointer-events`
- 刷新不应闪烁（用 localStorage 存主题状态）
