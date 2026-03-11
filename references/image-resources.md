# 配图与图标资源指南

项目中需要配图时，按以下方案选择资源。

---

## 〇、UI 图标 — Iconoir（网页开发默认）

**网页/Web 应用中的 UI 图标首选库。** 1671 个免费开源 SVG 线性图标。

### 地址
- 官网：https://iconoir.com/
- GitHub：https://github.com/iconoir-icons/iconoir
- CDN：`https://cdn.jsdelivr.net/gh/iconoir-icons/iconoir/icons/`

### 使用方式

**SVG 内联（推荐，最轻量）：**
```html
<!-- 从 iconoir.com 复制 SVG 代码直接内联 -->
<svg width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5">
  <!-- path data -->
</svg>
```

**React 组件：**
```bash
npm install iconoir-react
```
```jsx
import { Search, Settings, Mail } from 'iconoir-react';
<Search width={20} height={20} />
```

**CSS/Font（无框架场景）：**
```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/gh/iconoir-icons/iconoir/css/iconoir.css">
<i class="iconoir-search"></i>
```

### 样式规范
- 默认尺寸：24×24
- 线宽：1.5px（与 UI 文字协调）
- 颜色跟随 `currentColor`，自动继承父元素文字色

### 优先级
**Iconoir > Heroicons > Lucide > 其他。** 除非项目已有其他图标库，否则默认用 Iconoir。

---

## 〇.五、3D 插画图标 — Thiings.co

**大尺寸装饰图标：** 飞书群头像、网站空状态图、功能模块封面。

### 地址
- 官网：https://www.thiings.co/things
- 图片源（Vercel Blob Storage）：`https://lftz25oez4aqbxpq.public.blob.vercel-storage.com/`

### 使用方式
1. 在官网搜索关键词
2. 从页面提取 blob URL（不要用 `_next/image` 压缩版）
3. 直接下载原始 PNG（1024×1024，透明背景）

### 适用场景
| 场景 | 推荐 |
|------|------|
| 飞书群头像 | ✅ Thiings.co |
| 网站空状态插画 | ✅ Thiings.co |
| 按钮/导航小图标 | ❌ 用 Iconoir |
| 功能模块封面 | ✅ Thiings.co |

---

## 一、品牌/模型 Logo — LobeHub Icons

AI 模型、云服务等品牌 Logo 的统一图标库。

### CDN 地址

```
https://registry.npmmirror.com/@lobehub/icons-static-png/latest/files/{theme}/{name}.png
```

### 主题目录选择

| 页面背景 | 使用目录 | 说明 |
|----------|----------|------|
| 浅色/白色 | `light/` | 图标为深色，在白色背景上可见 |
| 深色/黑色 | `dark/` | 图标为浅色，在深色背景上可见 |

### 彩色版

命名规则：`{name}-color.png`

**注意：** 不是所有品牌都有彩色版。无彩色版时 fallback 到原版。

| 品牌 | 图标名 | 彩色版 |
|------|--------|--------|
| Claude (Anthropic) | `claude-color` | ✅ |
| OpenAI | `openai` | ❌ 无彩色版 |
| Gemini (Google) | `gemini-color` | ✅ |
| DeepSeek | `deepseek-color` | ✅ |
| Kimi (Moonshot) | `kimi-color` | ✅ |
| AWS | `aws-color` | ✅ |

### 使用示例

```html
<!-- 白色背景 + 彩色 Claude logo -->
<img src="https://registry.npmmirror.com/@lobehub/icons-static-png/latest/files/light/claude-color.png" />
```

### 推荐样式

```css
.brand-icon {
  width: 32px;
  height: 32px;
  border-radius: 8px;
  object-fit: contain;
  background: #fff;     /* 统一纯白底色 */
  padding: 4px;
  flex-shrink: 0;
}
```

### 发现更多图标

浏览完整图标库：https://lobehub.com/icons

---

## 二、通用配图 — Unsplash

适用于卡片封面、页面 Banner、功能模块配图。

### URL 格式

```
https://images.unsplash.com/{photo-id}?w={width}&h={height}&fit=crop&q=80
```

### 参数说明

| 参数 | 说明 | 推荐值 |
|------|------|--------|
| `w` | 宽度 | 560（卡片）/ 960（Banner） |
| `h` | 高度 | 240（卡片）/ 400（Banner） |
| `fit` | 裁剪模式 | `crop` |
| `q` | 质量 | 80 |

### 推荐风格

- **Minimalist** — 简洁抽象
- **Abstract** — 渐变、几何色块
- **Gradient** — 彩色渐变

### 布局规则

```css
.card-image {
  width: 100%;
  height: 120px;           /* 卡片配图 */
  object-fit: cover;
  display: block;
}

.card {
  overflow: hidden;         /* 图片与卡片无缝衔接 */
  border-radius: 24px;
}
```

- 图片高度：卡片 120px，Banner 200px
- `object-fit: cover` 自适应裁剪
- 卡片 `overflow: hidden` 确保圆角裁剪图片
- 使用 `loading="lazy"` 延迟加载

### 注意事项

1. **验证可用性**：上线前确认所有图片 URL 返回 200（Unsplash 图片可能下架）
2. **固定 photo-id**：为每个条目分配固定 ID，不要用随机图片（避免刷新闪烁）
3. **fallback**：设置 `onerror` 处理图片加载失败
4. **间距**：图片与卡片 padding 保持一致

### 示例

```html
<div class="card">
  <img class="card-image"
    src="https://images.unsplash.com/photo-1618005182384-a83a8bd57fbe?w=560&h=240&fit=crop&q=80"
    alt="" loading="lazy" />
  <div class="card-body">
    <!-- 内容 -->
  </div>
</div>
```
