# Cedar

Cedar 是一款原创 Obsidian 主题——在安静的纸面上写作，在柔和的卡片工作台上管理知识。

浅色模式以暖中性灰为底、纸白为书写区、赤陶为点缀；深色模式以暖炭灰为底、石墨纸为书写区、铜色为点缀。两端同等设计投入，不做偏废。

## 安装

1. 将 `manifest.json` 和 `theme.css` 复制到 vault 的 `.obsidian/themes/Cedar/`。
2. 打开 **Settings > Appearance > Themes**，选择 **Cedar**。

## 覆盖范围

- 浅色与深色模式，所有表面均通过 CSS 变量统一调色。
- 纸面感的编辑与阅读区域，固定最大行宽，舒适的正文行高。
- H1–H6 手稿式标题层级，有序列表采用十进制 → 小写字母 → 小写罗马循环编号。
- 圆角卡片式侧边栏、标签页、搜索、命令面板、弹窗、菜单与悬浮预览。
- Properties、链接、标签、引用块、callout（note / tip / warning / info / quote）、表格、代码块。
- 行内语法全覆盖：加粗、斜体、行内代码、高亮、删除线、脚注、上下标、内外链接。
- 交互元素统一 `cursor: pointer` 反馈，编辑区保持原生光标行为。
- 窄屏自适应（900px 断点），编辑器与侧边栏在窄窗口下仍可用。

## 视觉检查

将 `fixtures/theme-showcase.md` 与 `fixtures/Internal links.md` 复制到测试 vault 的同一文件夹。打开 `theme-showcase.md`，准备多层文件夹的文件树，在浅色和深色模式下分别检查：

- 编辑视图与阅读视图的整体一致性。
- H1–H6 标题层级、有序与无序列表层级。
- 加粗、斜体、加粗斜体、行内代码、高亮、删除线、脚注、上下标、内外链接。
- 引用块与 `note` / `tip` / `warning` / `info` / `quote` callout。
- 表格、fenced code block、Properties、水平线、嵌入。
- 文件浏览器、标签页、分栏、Ribbon、状态栏。
- 搜索、命令面板、建议列表、菜单、`[[Internal links]]` 悬浮预览、设置弹窗。
- 交互元素光标反馈（标签页、导航项、按钮、下拉框、关闭按钮、设置侧边栏等）。
- 窄窗口布局。
