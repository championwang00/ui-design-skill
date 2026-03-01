# UI 审查清单

## 必查项

- [ ] 动态内容无布局偏移
- [ ] 每个动画有 `prefers-reduced-motion` 支持
- [ ] 触摸目标 ≥ 44px
- [ ] 触摸设备禁用 hover 效果
- [ ] 键盘导航正常
- [ ] 图标按钮有 `aria-label`
- [ ] 表单 Enter/Cmd+Enter 提交
- [ ] 输入字体 ≥ 16px（防 iOS 缩放）
- [ ] 无 `transition: all`
- [ ] z-index 用固定比例

## 常见错误速查

| 错误 | 修复 |
|------|------|
| `transition: all` | 指定确切属性 |
| 触摸设备 hover | `@media (hover: hover)` |
| hover 改字重 | 用一致字重+颜色区分 |
| 动画 height/width | 用 transform + opacity |
| 无减少运动 | 加 `prefers-reduced-motion` |
| `z-index: 9999` | 固定比例或 `isolation` |
| 自定义页面滚动条 | 只在小组件中 |
| 图标按钮无标签 | 加 `aria-label` |
| 输入 < 16px | 至少 16px |
