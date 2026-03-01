# 组件设计指南

## 复合组件

**何时用：** 多元素共享隐式状态、带插槽的组件、需要灵活组合
**何时不用：** 固定结构简单组件、1-3 个 props、结构不变

## 组合优于配置

```jsx
// ✅ 组合
<Card>
  <Card.Header><Card.Title>Title</Card.Title></Card.Header>
  <Card.Content>Content</Card.Content>
  <Card.Footer><Button>Action</Button></Card.Footer>
</Card>

// ❌ 配置对象
<Card header={{ title: "Title" }} content="..." footer={{ actions: [...] }} />
```

## Props API

- 一致命名：`disabled` 非 `isDisabled`
- 布尔用肯定名：`open` 非 `isNotClosed`
- 事件用 `on` 前缀：`onChange` 非 `handleChange`
- 简单用 children，复杂用 render props

## 可定制性（Goldilocks）

1. **变体**：primary, secondary, destructive
2. **大小**：sm, md, lg
3. **className**：一次性定制逃生舱
4. **asChild**：渲染为不同元素（Radix 模式）

## 最佳实践

- 始终转发 refs
- 展开剩余 props（`...rest`）
- 合理默认值（80% 用例）
- 支持受控和非受控
- 复杂组件用错误边界包装

## 反模式

- ❌ Props 爆炸 → 用 children/composition
- ❌ 布尔变体 → 用显式变体字符串
- ❌ 过早抽象 → 复制粘贴 2-3 次再抽象

## 文件结构

```
components/button/
├── button.tsx
├── button.test.tsx
└── index.ts
```
