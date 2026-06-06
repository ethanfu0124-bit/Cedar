# Cedar

Cedar 是一款以 **Claude** 为灵感的 Obsidian 主题——在安静的纸面上写作，在柔和的卡片工作台上管理知识。

调色板来自 Claude 的品牌色彩体系：珊瑚橙为 accent，暖纸白为书写区，暖炭灰为深色底。每一处细节都在说「你在与 Claude 共事」。

## 安装

1. 将 `manifest.json` 和 `theme.css` 复制到 vault 的 `.obsidian/themes/Cedar/`。
2. 打开 **Settings > Appearance > Themes**，选择 **Cedar**。

## Claude 专属 Callout 类型

| 类型 | 颜色 | 用途 |
|------|------|------|
| `[!thinking]` | 珊瑚橙 | 记录推理过程、思维链 |
| `[!prompt]` | 松绿 | 存储发给 Claude 的提示词 |
| `[!context]` | 琥珀 | 背景信息、约束条件 |
| `[!response]` | 橄榄绿 | Claude 的回答摘录 |
| `[!artifact]` | 暖紫 | Claude 生成的代码、文档等产出物 |

Callout 使用左侧竖条 + 圆形徽章图标设计，所有标准类型均已暖化至 Claude 调色板。

## 设计覆盖范围

**色彩与排版**
- 浅色与深色模式，以 Claude 珊瑚橙 `#D97757` 为核心 accent。
- 字体渲染优化：antialiased、optimizeLegibility、optical sizing、kerning。
- H1 标题居中，H2–H3 使用 geometricPrecision 渲染；H2–H6 颜色向 accent 收敛。
- 加粗为珊瑚调，斜体为松绿调，高亮 `==` 为珊瑚半透明覆盖层，深色模式下清晰可见。
- 列表标记按嵌套层级依次：accent → 松绿 → muted → faint。
- 多级有序列表：decimal → lower-alpha → lower-roman 自动切换。

**代码**
- 代码块：浅色模式暖纸底色，深色模式深色面板；复制按钮在两种模式下均清晰可见。
- 语法高亮：关键字珊瑚橙，字符串暖绿，注释淡灰，变量名松绿；所有色值符合 WCAG AA 对比度标准。
- 编辑与阅读模式语法高亮保持一致（同时接管 CodeMirror 与 Prism 着色）。
- 行内代码：珊瑚底色 + 细边框；编辑模式下定界符独立渲染，视觉干净。

**结构元素**
- **Callout**：左侧 4px 竖条 + 圆形徽章图标；5 个 Claude 专属类型 + 所有标准类型暖化。
- **引用块**：accent 竖条 + 极淡珊瑚底，支持通过 `--blockquote-border-color` 自定义。
- **嵌入块**：左侧松绿竖条，与 callout 家族一脉相承。
- **表格**：圆角 + 行 hover 珊瑚淡底 + 数字等宽对齐。
- **数学公式**：MathJax / KaTeX 均支持；行内公式带珊瑚色调，块级公式超宽时横向滚动。
- **Mermaid 图表**：背景、节点、边线全部接入 Cedar 变量。
- **图片**：圆角 + 微阴影。

**工作区**
- **图谱视图**：节点 muted，聚焦珊瑚，标签松绿，未解析链接淡化。
- **Canvas**：暖色背景，节点圆角卡片，选中态 accent 光晕。
- **文件树**：nav 缩进引导线接入 `--clw-border`。
- **活跃标签页**：底部 accent 描边指示器。
- **扩展 Task 状态**：`-` 取消、`>` 转发、`!` 紧急、`?` 存疑、`/` 进行中、`*` 加星。
- Properties、链接、标签、弹窗、命令面板、滚动条全面 Claude 化。

## 自定义

主题使用标准 Obsidian CSS 变量，可通过 CSS 片段覆盖：

```css
/* 示例：修改引用块边框颜色 */
:root {
  --blockquote-border-color: #your-color;
}
```

## 版本

**v0.3.1** — Contrast & consistency pass: WCAG AA syntax colors, Prism reading-mode parity, visible copy button

## 视觉检查

将 `fixtures/theme-showcase.md` 复制到测试 vault。在浅色和深色模式下分别检查所有元素。
