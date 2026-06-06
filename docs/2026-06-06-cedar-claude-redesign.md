# Cedar × Claude 全面重设计 — 设计规格

日期：2026-06-06  
版本目标：0.3.0  
仓库：https://github.com/ethanfu0124-bit/Cedar

---

## 一、背景与目标

Cedar 是一款暖纸面风格的 Obsidian 主题。本次重设计以 Claude 为灵感来源，让每一处细节都向 Claude 的视觉语言靠拢，同时保留 Cedar 的「暖纸+圆角知识工作台」基因。

**核心原则：**
- Accent 精确对齐 Claude 品牌珊瑚橙 `#D97757`
- 所有背景色保持低饱和暖中性，不过鲜艳
- 正文文字与纸面对比清晰可读（WCAG AA 以上）
- 每个模块完成后单独 commit + push

---

## 二、色彩系统

### 浅色模式

| Token | 新值 | 说明 |
|-------|------|------|
| `--clw-accent` | `#D97757` | Claude 珊瑚橙，与 logo 同源 |
| `--clw-paper` | `#FAF9F7` | 对齐 Claude.ai 编辑区白底 |
| `--clw-shell` | `#EFECE5` | 对齐 Claude.ai 侧边栏 |
| `--clw-shell-raised` | `#F5F2EB` | 稍亮于 shell |
| `--clw-card` | `#F3EFE8` | 卡片面 |
| `--clw-card-strong` | `#FAF8F2` | 弹窗/输入框底色 |
| `--clw-border` | `#D4C8B8` | 比旧值略暖 |
| `--clw-ink` | `#1A1714` | 正文深暖黑，对比度提升 |
| `--clw-ink-muted` | `#6A5E54` | muted 文字 |
| `--clw-support` | `#7A8E88` | 松绿，与珊瑚互补 |
| `accent-h/s/l` | `22 / 57% / 57%` | HSL 对应 #D97757 |

### 深色模式

| Token | 新值 | 说明 |
|-------|------|------|
| `--clw-accent` | `#E8956A` | 深色下亮度提升 |
| `--clw-paper` | `#252119` | 对齐 Claude.ai 深色编辑区 |
| `--clw-shell` | `#1C1917` | Claude 暖炭底 |
| `--clw-shell-raised` | `#272420` | 稍亮 |
| `--clw-card` | `#2E2A25` | 卡片面 |
| `--clw-card-strong` | `#352E28` | 弹窗/输入框 |
| `--clw-border` | `#42382E` | 比旧值略暖 |
| `--clw-ink` | `#EDE5D8` | 深色正文，暖白 |
| `--clw-ink-muted` | `#A09080` | muted |
| `--clw-support` | `#8AA8A0` | 松绿深色版 |
| `accent-h/s/l` | `22 / 52% / 67%` | 深色下更亮 |

---

## 三、排版与可读性

- **H1**：`text-align: center`；颜色 `color-mix(in srgb, var(--clw-accent-hover) 60%, var(--text-normal))`
- **H2–H6**：保持原有层级，向 accent 与正文收敛
- **正文行高**：`1.68`（比旧 1.65 略宽松）
- **正文色**：`--clw-ink` 使用 `#1A1714`（浅色）/ `#EDE5D8`（深色），确保对纸面对比度充足
- **加粗**：`color-mix(in srgb, var(--clw-accent-hover) 78%, var(--text-normal))`，珊瑚系
- **斜体**：`color-mix(in srgb, var(--clw-support) 80%, var(--text-normal))`，松绿系
- **高亮 `==`**：底色 `rgba(217, 119, 87, 0.20)`，即珊瑚 20% 透明，不过鲜艳
- **删除线**：muted 色 + 珊瑚删线色
- **脚注/上下标**：珊瑚半透，`font-weight: 620`

---

## 四、Callout — 全面重设计（方案 C）

### 视觉结构

```
┌─╥─────────────────────────────┐
│ ║ 🟠 type-name                │  ← 圆形徽章 + 类型名
│ ║─────────────────────────────│
│ ║ callout 内容正文…            │
└─╨─────────────────────────────┘
  ↑ 4px 竖条，颜色 = callout 主色
```

- 左侧 4px 竖条：`callout-color` 实色
- 圆形徽章（20×20px，border-radius 50%）：`callout-color` 背景 + 白色图标
- 主体背景：`callout-color` 6–8% 透明度，不过鲜艳
- 边框：`callout-color` 38–42% 透明度

### Claude 专属类型（英文命名）

| 类型 | 颜色 | 图标 | 语义 |
|------|------|------|------|
| `thinking` | `#D97757` 珊瑚 | 💭 | 推理过程、思维链 |
| `prompt` | `#649B91` 松绿 | 📥 | 发给 Claude 的提示词 |
| `context` | `#C09A40` 琥珀 | 🗂️ | 背景信息、约束条件 |
| `response` | `#7AAA80` 橄榄绿 | 🤖 | Claude 的回答摘录 |
| `artifact` | `#8A78C0` 暖紫 | ⚗️ | Claude 生成的产出物 |

### 标准类型暖化

| 类型 | 新颜色方向 |
|------|-----------|
| `note` | 珊瑚系 `#C07848` |
| `tip` | 暖橄榄绿 `#6AAA72` |
| `warning` | 暖琥珀 `#C08840` |
| `danger` | 暖赤 `#B85858` |
| `quote` | 暖中性 `#8A8AA0` |
| `info` | 松绿系 `#5A9090` |
| `success` | 橄榄绿 `#6AAA72` |
| `question` | 暖琥珀 `#B88840` |
| `failure` | 暖赤 `#B05050` |
| `bug` | 暖赤偏紫 `#A06070` |
| `example` | 珊瑚系 `#B07848` |
| `abstract` | 松绿偏蓝 `#6090A0` |
| `todo` | accent 珊瑚 `#D97757` |

---

## 五、代码块

- **浅色/深色模式下均使用深色面板**（对齐 Claude.ai 代码输出风格）
- 顶栏：`#2A2420`（浅色模式）/ `#161210`（深色模式）
- 代码底：`#1C1917`（浅色）/ `#0F0D0C`（深色）
- 语言标签：左上角，monospace，muted 色
- Copy 按钮区域：右上角，`rgba(255,255,255,0.08)` 底
- 语法高亮方向：关键字珊瑚橙，字符串暖绿，注释退色至 muted，函数名暖米色

---

## 六、其他元素

### 引用块 blockquote
- 左侧竖条：`3px solid #D97757`
- 背景：`rgba(217,119,87,0.06)`（极淡，不过鲜艳）
- `border-radius: 0 8px 8px 0`

### 表格
- 行 hover：`rgba(217,119,87,0.06)`
- 表头底：`--clw-card`
- 整体 `border-radius: 10px`，`border-collapse: separate`

### 标签 #hashtag
- 背景：`rgba(217,119,87,0.09)`
- 边框：`rgba(217,119,87,0.28)`
- 文字：珊瑚偏深 `#904030`
- 微阴影，比现版更接近 Claude UI chip 设计

### Task List
- 勾选色：`--clw-accent`
- 勾选后：text `--text-muted` + `line-through`，删线色 `rgba(217,119,87,0.50)`

### 弹窗 / 命令面板
- 输入框焦点：accent 描边 + `0 0 0 2px rgba(217,119,87,0.20)` glow
- 选中项：`rgba(217,119,87,0.13)` 底 + 珊瑚文字

### Properties / Frontmatter
- 整体卡片 `border-radius: 10px`，`background: --clw-card-strong`
- hover 态：珊瑚淡底 + 细 accent 描边

### 滚动条
- thumb：`#D4C8B8`（浅）/ `#42382E`（深）
- hover：`#B0A090`（浅）/ `#6A5A48`（深）
- 暖调，不冷灰

### 水平线 HR
- 渐变淡出，边框色更新至 `#D4C8B8`

---

## 七、字体渲染优化

不指定字体族，仅通过渲染参数让系统字体更清晰：

```css
body {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
  font-optical-sizing: auto;
}
```

- `-webkit-font-smoothing: antialiased`：macOS 下消除次像素锯齿，字形更锐利
- `text-rendering: optimizeLegibility`：启用连字与字距微调（kerning）
- `font-optical-sizing: auto`：允许字体在不同尺寸下自动调整视觉重量
- 现有 `font-feature-settings: "kern" 1, "liga" 1, "calt" 1, "palt" 1` 保留

---

## 八、图谱视图（Graph View）

使用 Claude 调色板染色节点与边线：

- `--graph-node`：`var(--clw-ink-muted)`
- `--graph-node-focused`：`var(--clw-accent)`
- `--graph-node-unresolved`：`color-mix(in srgb, var(--clw-border) 80%, transparent)`
- `--graph-node-tag`：`var(--clw-support)`
- `--graph-node-attachment`：`color-mix(in srgb, var(--clw-accent) 60%, var(--clw-support))`
- `--graph-line`：`color-mix(in srgb, var(--clw-border) 70%, transparent)`
- `--graph-text`：`var(--clw-ink-muted)`
- `--graph-arrow`：`var(--clw-accent)`

节点形态：聚焦态用珊瑚色突出，标签节点用松绿，未解析链接用边框色淡化。

---

## 九、图片与嵌入块

### 图片

```css
.markdown-rendered img {
  border-radius: var(--clw-radius-m);
  box-shadow: var(--clw-shadow-m);
  max-width: 100%;
}
```

### 嵌入块（`![[...]]`）

与 callout 家族一致，加左侧竖条感：

- `border-left: 3px solid var(--clw-support)`
- `background: color-mix(in srgb, var(--clw-card) 60%, transparent)`
- `border-radius: 0 var(--clw-radius-m) var(--clw-radius-m) 0`
- 内边距与 blockquote 对齐

---

## 十、Mermaid 图表

接入 Cedar 变量，避免渲染时使用浏览器默认色：

- 图表背景：`var(--clw-card-strong)`
- 节点填充：`color-mix(in srgb, var(--clw-accent) 14%, var(--clw-card-strong))`
- 节点边框：`color-mix(in srgb, var(--clw-accent) 44%, var(--clw-border))`
- 节点文字：`var(--clw-ink)`
- 边线/箭头：`var(--clw-border)`
- 子图背景：`color-mix(in srgb, var(--clw-shell) 60%, transparent)`

---

## 十一、阴影体系更新

随新调色板同步更新，保持暖调：

| 变量 | 浅色新值 | 深色新值 |
|------|----------|----------|
| `--clw-shadow` | `0 18px 44px rgba(60, 40, 24, 0.13)` | `0 22px 56px rgba(0,0,0,0.36)` |
| `--clw-shadow-m` | `0 4px 12px rgba(60, 40, 24, 0.09)` | `0 4px 12px rgba(0,0,0,0.22)` |
| `--clw-shadow-s` | `0 1px 3px rgba(60, 40, 24, 0.07)` | `0 1px 3px rgba(0,0,0,0.16)` |

---

## 十二、实施顺序（8 次 commit）

1. **feat: 色彩变量层重构** — 所有 CSS 变量 + 阴影更新，manifest → `0.3.0`
2. **feat: 排版与字体渲染** — H1 居中、字体渲染优化、加粗/斜体/高亮/正文对比度
3. **feat: callout 全面重设计** — 结构 + 5 个 Claude 类型 + 标准类型暖化
4. **feat: 代码块 Claude 风格** — 深色面板 + 语言标签 + 语法高亮暖化
5. **feat: 图片、嵌入块与 Mermaid** — 圆角图片、嵌入竖条、Mermaid 接入变量
6. **feat: 图谱视图 Claude 化** — 节点/边线/文字全面接入调色板
7. **feat: 其他元素 Claude 化** — 表格/标签/弹窗/滚动条/Properties/引用块
8. **docs: 更新 README 与 About** — 说明 Claude 灵感来源，更新功能列表

每次 commit 后立即 push 到 `main`。
