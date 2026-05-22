# Cedar

Cedar is an original Obsidian theme built around a warm paper editor and a compact rounded-card knowledge workbench.

## Install

1. Copy `manifest.json` and `theme.css` into `.obsidian/themes/Cedar/` in an Obsidian vault.
2. Open **Settings > Appearance > Themes**.
3. Select **Cedar**.

Theme installation requires the `theme.css` file created by the styling tasks.

## First Release Scope

- Balanced light and dark modes.
- Paper-like editor and reading surfaces.
- Rounded sidebar, tab, search, command, modal, menu, and hover-preview surfaces.
- Styled properties, links, tags, quotes, callouts, tables, code blocks, text selection, and search matches.

## Visual Check

Copy `fixtures/theme-showcase.md` and `fixtures/Internal links.md` into the same folder in a test vault. Open `theme-showcase.md`, create a busy file tree with nested folders, and inspect:

- Edit and reading modes in light and dark mode.
- Multiple tabs and split panes.
- File explorer, Ribbon, status bar, and right sidebar panels.
- Search, command palette, menus, suggestions, and settings modal.
- Hover `[[Internal links]]` in the showcase note to inspect the linked-note hover preview.

## Release Checklist

- Confirm the theme loads from an Obsidian theme folder.
- Compare light and dark modes on the showcase note.
- Verify edit and reading views stay visually close.
- Verify the H1 through H6 heading hierarchy in Reading view and Live Preview.
- Verify plain quotes and `note`, `tip`, `warning`, `info`, and `quote` callouts in Reading view and Live Preview.
- Verify fenced code blocks and Properties against Live Preview.
- Verify bold, italic, inline code, highlight, strikethrough, footnotes, superscript, and subscript in prose and task list text.
- Verify nested folders, active files, tabs, split panes, Ribbon, and status bar.
- Verify command palette, search, suggestions, menus, the `[[Internal links]]` hover preview, settings modal, selection, and focus rings.
- Check a narrow workspace before publishing the first release.
