# HeroUI v3 设计规范参考

> **更新于 2026-03-22** — 基于 HeroUI v3 RC4（前 NextUI），完全重写版。
> 官网：https://heroui.com | Figma Kit：https://www.figma.com/community/file/1546526812159103429

## v3 核心变化（vs v2）

| 维度 | v2 | v3 |
|------|-----|-----|
| CSS 框架 | Tailwind v3 | **Tailwind CSS v4** |
| 无障碍基础 | React Aria hooks | **React Aria Components**（完整组件级） |
| 组件架构 | Props 驱动 | **Compound Components**（可组合子组件） |
| React 版本 | React 18 | **React 19** |
| 平台 | Web only | **Web + React Native** |
| 组件数量 | ~40 | **75+ Web / 37 Native** |
| AI 友好 | 无 | **API 专为 AI 代码生成设计** |
| 定制方式 | Tailwind utilities | **Tailwind + CSS 变量 + BEM + Slot 组合** |

### 新增组件（v3 新增）

InputOTP · TagGroup · Menu · SubMenu · InputGroup · SearchField · ListGroup · Slider · TextArea · Label · Description

### 关键特性

- **虚拟化**：Table 和 ListBox 内置虚拟滚动（@tanstack/react-virtual）
- **Tree-shaken**：只打包你用的组件
- **HeroUI Chat**：文本生成应用（heroui.chat）
- **HeroUI Native**：React Native 组件库
- **UI for LLMs**：MCP 平台即将上线

## API 约定

继承 React Aria 风格：
- `isDisabled` / `isReadOnly` / `isRequired`（非 `disabled`）
- `onPress`（非 `onClick`，处理键盘+触摸统一事件）
- `onSelectionChange` / `onOpenChange`

## 设计 Token

### 配色（OKLCH）

```css
/* HeroUI 默认主题 - 紫蓝色调 */
--accent-hue: 253.83;
--accent-chroma: 0.195;
--accent-lightness: 0.6204;
--accent: oklch(0.62 0.195 253.83);
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
/* HeroUI 使用极轻阴影，非描边 */
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
  /* 无 border，用 surface 色差区分层级 */
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

v3 新增 `outline` 变体。

## Compound Component 模式（v3 核心）

v3 所有复杂组件采用复合组件架构：

```jsx
// v2 - Props 驱动
<Select items={items} renderItem={(item) => ...} />

// v3 - Compound Components（可组合）
<Select>
  <SelectTrigger>
    <SelectValue />
  </SelectTrigger>
  <SelectPopover>
    <SelectListBox>
      <SelectItem>Option 1</SelectItem>
    </SelectListBox>
  </SelectPopover>
</Select>
```

**优势：**
- 每个子组件独立可定制（className / style / ref）
- 不需要 renderProps 或 slot props
- IDE 自动补全更好
- AI 生成代码更准确（结构化语义明确）

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

## 定制层级（v3）

v3 提供四级定制深度：

1. **Tailwind utilities** — 直接在 className 覆盖
2. **CSS 变量** — 全局主题 token 覆盖
3. **BEM 修饰符** — 组件级 slot 样式
4. **Compound 组合** — 重组子组件结构

```jsx
// 层级 1：Tailwind
<Button className="bg-blue-500 rounded-full" />

// 层级 2：CSS 变量
<HeroUIProvider style={{ '--heroui-primary': 'oklch(0.7 0.2 250)' }}>

// 层级 3：Slot 定制
<Card classNames={{ base: "...", header: "...", body: "..." }} />

// 层级 4：完全重组
<Card>
  <CardHeader>{/* 自定义结构 */}</CardHeader>
  <CardBody>{/* 自定义结构 */}</CardBody>
</Card>
```

## 响应式

```css
@media (max-width: 640px) {
  .grid { grid-template-columns: 1fr; }
}

/* 触摸设备守卫 */
@media (hover: hover) and (pointer: fine) {
  /* 只在桌面端添加 hover 效果 */
}
```

## 页面最大宽度

```css
max-width: 960px;
margin: 0 auto;
```

## 无障碍（v3 内置）

基于 React Aria Components，开箱即用：
- **焦点管理**：自动 focus trap、focus ring
- **键盘导航**：Arrow keys / Tab / Escape 全支持
- **屏幕阅读器**：aria-label / aria-describedby 自动注入
- **WCAG 合规**：颜色对比度、touch target ≥ 44px

## 参考链接

- 官网文档：https://heroui.com/docs/react/getting-started
- GitHub：https://github.com/heroui-inc/heroui
- Figma Kit v3：https://www.figma.com/community/file/1546526812159103429
- Discord：https://discord.gg/9b6yyZKmH4
- HeroUI Chat（AI 生成）：https://heroui.chat
- Tailwind Play 示例（纯 CSS）：https://play.tailwindcss.com/vMYXzKPyUx
