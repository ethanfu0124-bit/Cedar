# Cedar

Cedar 是一款原创 Obsidian 主题，围绕温暖的纸面笔记体验与紧凑的圆角知识工作台设计。

## 安装

1. 将 `manifest.json` 和 `theme.css` 复制到 Obsidian vault 中的 `.obsidian/themes/Cedar/`。
2. 打开 **Settings > Appearance > Themes**。
3. 选择 **Cedar**。

主题安装所需的发布文件为 `manifest.json` 和 `theme.css`。

## 首版范围

- 平衡的浅色与深色模式。
- 纸面感的编辑与阅读区域。
- 圆角化的侧边栏、标签页、搜索、命令面板、弹窗、菜单与悬浮预览。
- 适配 Properties、链接、标签、引用块、callout、表格、代码块、文本选区与搜索匹配结果。

## 视觉检查

将 `fixtures/theme-showcase.md` 与 `fixtures/Internal links.md` 复制到测试 vault 的同一文件夹中。打开 `theme-showcase.md`，准备一个包含多层文件夹的文件树，然后检查：

- 浅色与深色模式下的编辑视图和阅读视图。
- 多标签页与分栏布局。
- 文件浏览器、Ribbon、状态栏与右侧边栏面板。
- 搜索、命令面板、菜单、建议列表与设置弹窗。
- 在展示笔记中悬停 `[[Internal links]]`，检查链接笔记的悬浮预览。

## 发布检查清单

- 确认主题可以从 Obsidian 主题文件夹正常加载。
- 在展示笔记中对比浅色与深色模式。
- 确认编辑视图与阅读视图的整体效果保持接近。
- 在阅读视图与 Live Preview 中检查 H1 到 H6 的标题层级。
- 在阅读视图与 Live Preview 中检查普通引用块，以及 `note`、`tip`、`warning`、`info`、`quote` callout。
- 对照 Live Preview 检查 fenced code block 与 Properties。
- 在正文和任务列表中检查加粗、斜体、行内代码、高亮、删除线、脚注、上标与下标。
- 检查多层文件夹、当前文件、标签页、分栏、Ribbon 与状态栏。
- 检查命令面板、搜索、建议列表、菜单、`[[Internal links]]` 悬浮预览、设置弹窗、文本选区与焦点环。
- 发布首版前检查窄宽度工作区。
