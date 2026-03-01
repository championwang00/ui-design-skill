# HeroUI v3 设计规范参考

基于 HeroUI v3（前 NextUI）的设计语言。用于纯 CSS 项目时的风格参考。

## 设计 Token

### 配色（OKLCH）

```css
/* HeroUI 默认主题 */
--accent-hue: 253.83;
--accent-chroma: 0.195;
--accent-lightness: 0.6204;
--accent: oklch(0.62 0.195 253.83);  /* 紫蓝色 */
```

### 浅色模式

```css
--bg: #fafafa;
--surface: #f0f0f3;           /* 卡片背景 */
--surface-secondary: #e8e8ec;  /* 次级表面 */
--foreground: #11181c;
--muted: #71717a;
--muted-light: #a1a1aa;
```

### 圆角

```css
--radius-none: 0;
--radius-xs: 6px;
--radius-sm: 8px;
--radius-md: 12px;
--radius-lg: 16px;
--radius-xl: 24px;    /* 卡片默认 rounded-3xl */
```

### 阴影

```css
/* HeroUI 使用 shadow-surface，非常轻微 */
--shadow-sm: 0 1px 3px rgba(0,0,0,0.04), 0 1px 2px rgba(0,0,0,0.02);
--shadow-md: 0 4px 14px rgba(0,0,0,0.06), 0 1px 3px rgba(0,0,0,0.04);
```

## 卡片

**核心特征：无描边。**

```css
.card {
  background: var(--surface);
  border-radius: 24px;          /* rounded-3xl */
  padding: 16px;
  /* 无 border */
  /* 轻微或无阴影 */
}
```

### 卡片变体（语义化）

| 变体 | 用途 | 背景 |
|------|------|------|
| transparent | 嵌套卡片 | 透明 |
| default | 标准 | surface |
| secondary | 中等突出 | surface-secondary |
| tertiary | 高突出 | surface-tertiary |

## 字体

```css
font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
-webkit-font-smoothing: antialiased;
```

### 字重

| 用途 | 字重 |
|------|------|
| 正文 | 400 |
| 标签/强调 | 500 |
| 小标题 | 600 |
| 大标题 | 700 |

## 间距

- 卡片内边距：16px
- 卡片间距：10–12px
- 区块间距：24–28px
- 页面边距：24px（移动端 16px）

## 按钮

```css
.btn {
  border: none;
  border-radius: 12px;
  padding: 8px 20px;
  font-weight: 600;
  font-size: 14px;
  cursor: pointer;
  transition: background 0.2s ease;
}
```

## Tab 切换

```css
.tabs {
  display: inline-flex;
  background: var(--surface);
  border-radius: 12px;
  padding: 4px;
}
.tab {
  border-radius: 10px;
  padding: 8px 20px;
  font-weight: 600;
}
.tab.active {
  background: #fff;
  box-shadow: 0 1px 3px rgba(0,0,0,0.04);
}
```

## 响应式

```css
/* 移动端断点 */
@media (max-width: 640px) {
  .grid { grid-template-columns: 1fr; }
  /* 减小内边距 */
}

/* 触摸设备 */
@media (hover: hover) and (pointer: fine) {
  /* 只在桌面端添加 hover 效果 */
}
```

## 页面最大宽度

```css
max-width: 960px;  /* 内容区 */
margin: 0 auto;
```
