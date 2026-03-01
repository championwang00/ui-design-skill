# 表单与控件指南

## 输入框

- 点击标签应聚焦输入（`for` 或包装）
- 用正确的 `type`：email, password, tel, url, number, search
- 禁用 `spellcheck` 和 `autocomplete`（大多数场景）
- 禁用 1Password：`data-1p-ignore`
- 输入装饰（图标）绝对定位在输入上，点击聚焦输入
- **字体 ≥ 16px**（防止 iOS Safari 自动缩放）
- 模态框中自动聚焦输入，但触摸设备不要（避免弹键盘）

## 表单

- 用 `<form>` 包装，支持 Enter 提交
- `Cmd+Enter`（Mac）/ `Ctrl+Enter`（Win）提交文本区域
- 用登录用户数据预填充

## 按钮

- 始终用 `<button>`，不要给 `<div>` 加 click
- 提交后禁用防重复请求
- 有快捷键时在按钮上显示
- `:active` 加 `scale(0.97)` 增加按压感

## 复选框

- 标签和控件之间的空间也应可点击（无死区）

## 破坏性操作

- 需要确认对话框
- 用模态框而非 `confirm()`

## 错误处理

- 错误消息显示在出错的字段附近（并置原则）
