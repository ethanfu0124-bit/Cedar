# Cedar

Cedar 是一款以 **Claude** 为灵感的 Obsidian 主题——在安静的纸面上写作，在柔和的卡片工作台上管理知识。

调色板来自 Claude 的品牌色彩体系：珊瑚橙为 accent，暖纸白为书写区，暖炭灰为深色底。每一处细节都在说「你在与 Claude 共事」。

## 安装

1. 将 `manifest.json` 和 `theme.css` 复制到 vault 的 `.obsidian/themes/Cedar/`。
2. 打开 **Settings > Appearance > Themes**，选择 **Cedar**。

## Claude 专属 Callout 类型

| 类型 | 用途 |
|------|------|
| `[!thinking]` | 记录推理过程、思维链 |
| `[!prompt]` | 存储发给 Claude 的提示词 |
| `[!context]` | 背景信息、约束条件 |
| `[!response]` | Claude 的回答摘录 |
| `[!artifact]` | Claude 生成的代码、文档等产出物 |

## 设计覆盖范围

- 浅色与深色模式，以 Claude 珊瑚橙 `#D97757` 为核心 accent。
- 字体渲染优化（antialiased + optimizeLegibility），正文清晰可读。
- H1 标题居中显示；H2–H6 向 accent 与正文色收敛。
- 加粗为珊瑚调，斜体为松绿调，高亮为珊瑚暖底。
- **Callout 全面重设计**：左侧竖条 + 圆形徽章图标；5 个 Claude 专属类型 + 所有标准类型暖化。
- **代码块**：浅色/深色模式均使用深色面板，对齐 Claude.ai 代码输出风格；语法高亮使用暖色系。
- **图谱视图**：节点珊瑚，标签松绿，聚焦态 accent 高亮。
- **嵌入块**：左侧松绿竖条，与 callout 家族一脉相承。
- **Mermaid 图表**：背景、节点、边线全部接入 Cedar 变量。
- **图片**：圆角 + 微阴影。
- Properties、链接、标签、引用块、表格、水平线、task list、弹窗、滚动条全面 Claude 化。
- 窄屏自适应（900px 断点）。

## 视觉检查

将 `fixtures/theme-showcase.md` 复制到测试 vault。在浅色和深色模式下分别检查所有元素。
