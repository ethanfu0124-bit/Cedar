# Cedar × Claude 全面重设计 Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Redesign the Cedar Obsidian theme to align every detail with Claude's visual language — coral palette, Claude-specific callout types, dark code panels, and optimized typography.

**Architecture:** All changes are confined to `theme.css` (CSS variables + component rules), `manifest.json` (version bump), and `README.md` (docs). Each of the 8 tasks produces one standalone commit that is immediately pushed to `main`.

**Tech Stack:** Pure CSS (Obsidian theme API), git, GitHub CLI (`gh`)

---

## File Map

| File | Action | Responsibility |
|------|--------|----------------|
| `theme.css` | Modify | All visual changes — variables, components, layout |
| `manifest.json` | Modify | Version bump 0.1.0 → 0.3.0 |
| `README.md` | Modify | Document Claude inspiration, updated feature list |

> **Visual testing:** Open the vault in Obsidian, enable Cedar theme, open `fixtures/theme-showcase.md` in split (Edit + Reading) view. Check both light and dark mode after each task.

---

## Task 1: 色彩变量层重构 + manifest 版本

**Files:**
- Modify: `theme.css` lines 1–197 (`.theme-light` and `.theme-dark` blocks + CSS comment on line 2)
- Modify: `manifest.json`

### Changes

- [ ] **Step 1: Update CSS version comment and body block**

In `theme.css`, replace lines 1–4:

```css
/*
 * Cedar v0.3.0
 * Claude-inspired warm notes — coral accent, warm paper surfaces.
 */
```

The `body` block (lines 6–37) stays unchanged — radius/border tokens are fine as-is.

- [ ] **Step 2: Replace `.theme-light` block**

Replace the entire `.theme-light` block (lines 39–117) with:

```css
.theme-light {
  --clw-shell: #efece5;
  --clw-shell-raised: #f5f2eb;
  --clw-paper: #faf9f7;
  --clw-card: #f3efe8;
  --clw-card-strong: #faf8f2;
  --clw-border: #d4c8b8;
  --clw-ink: #1a1714;
  --clw-ink-muted: #6a5e54;
  --accent-h: 20;
  --accent-s: 60%;
  --accent-l: 59%;
  --clw-accent: hsl(var(--accent-h), var(--accent-s), var(--accent-l));
  --clw-accent-hover: hsl(var(--accent-h), var(--accent-s), calc(var(--accent-l) - 4%));
  --clw-support: #7a8e88;
  --clw-selection: hsla(var(--accent-h), var(--accent-s), var(--accent-l), 0.22);
  --clw-search: hsla(var(--accent-h), var(--accent-s), var(--accent-l), 0.28);
  --clw-shadow: 0 18px 44px rgba(60, 40, 24, 0.13);
  --clw-shadow-s: 0 1px 3px rgba(60, 40, 24, 0.07);
  --clw-shadow-m: 0 4px 12px rgba(60, 40, 24, 0.09);
  --background-primary: var(--clw-paper);
  --background-primary-alt: var(--clw-shell-raised);
  --background-secondary: var(--clw-shell);
  --background-secondary-alt: var(--clw-card);
  --background-modifier-border: var(--clw-border);
  --background-modifier-hover: hsla(var(--accent-h), var(--accent-s), var(--accent-l), 0.10);
  --background-modifier-active-hover: hsla(var(--accent-h), var(--accent-s), var(--accent-l), 0.16);
  --background-modifier-form-field: var(--clw-card-strong);
  --interactive-accent: var(--clw-accent);
  --interactive-accent-hsl: var(--accent-h), var(--accent-s), var(--accent-l);
  --interactive-accent-hover: var(--clw-accent-hover);
  --text-normal: var(--clw-ink);
  --text-muted: var(--clw-ink-muted);
  --text-faint: rgba(106, 94, 84, 0.72);
  --text-on-accent: var(--clw-card-strong);
  --text-on-accent-inverted: var(--clw-ink);
  --text-accent: var(--clw-accent);
  --text-accent-hover: var(--clw-accent-hover);
  --text-selection: var(--clw-selection);
  --text-highlight-bg: var(--clw-search);
  --clw-strong: color-mix(in srgb, var(--clw-accent-hover) 76%, var(--text-normal));
  --clw-emphasis: color-mix(in srgb, var(--clw-support) 82%, var(--text-normal));
  --clw-inline-code-bg: color-mix(in srgb, var(--clw-card) 78%, var(--clw-accent));
  --clw-inline-code-border: color-mix(in srgb, var(--clw-border) 56%, var(--clw-accent));
  --clw-inline-code-text: color-mix(in srgb, var(--text-normal) 58%, var(--clw-accent-hover));
  --clw-highlight: color-mix(in srgb, var(--clw-accent) 26%, var(--clw-paper));
  --clw-quote-bg: color-mix(in srgb, var(--clw-accent) 6%, transparent);
  --clw-quote-text: color-mix(in srgb, var(--text-normal) 84%, var(--text-muted));
  --clw-code-surface: #1c1917;
  --heading-spacing: calc(var(--p-spacing) * 2.18);
  --h1-color: color-mix(in srgb, var(--clw-accent-hover) 58%, var(--text-normal));
  --h2-color: color-mix(in srgb, var(--text-normal) 82%, var(--clw-accent));
  --h3-color: color-mix(in srgb, var(--text-normal) 72%, var(--clw-accent));
  --h4-color: color-mix(in srgb, var(--text-normal) 82%, var(--clw-accent));
  --h5-color: color-mix(in srgb, var(--text-normal) 90%, var(--text-muted));
  --h6-color: color-mix(in srgb, var(--text-muted) 68%, var(--text-normal));
  --h1-letter-spacing: 0;
  --h2-letter-spacing: 0;
  --h3-letter-spacing: 0;
  --h4-letter-spacing: 0;
  --h5-letter-spacing: 0;
  --h6-letter-spacing: 0;
  --h1-line-height: 1.24;
  --h2-line-height: 1.28;
  --h3-line-height: 1.34;
  --h4-line-height: 1.42;
  --h1-size: 1.7em;
  --h2-size: 1.48em;
  --h3-size: 1.28em;
  --h4-size: 1.14em;
  --h5-size: 1.04em;
  --h6-size: 1em;
  --h1-weight: 740;
  --h2-weight: 680;
  --h3-weight: 640;
  --h4-weight: 620;
  --h5-weight: 610;
  --h6-weight: 600;
}
```

- [ ] **Step 3: Replace `.theme-dark` block**

Replace the entire `.theme-dark` block (lines 119–197) with:

```css
.theme-dark {
  --clw-shell: #1c1917;
  --clw-shell-raised: #272420;
  --clw-paper: #252119;
  --clw-card: #2e2a25;
  --clw-card-strong: #352e28;
  --clw-border: #42382e;
  --clw-ink: #ede5d8;
  --clw-ink-muted: #a09080;
  --accent-h: 22;
  --accent-s: 52%;
  --accent-l: 67%;
  --clw-accent: hsl(var(--accent-h), var(--accent-s), var(--accent-l));
  --clw-accent-hover: hsl(var(--accent-h), var(--accent-s), calc(var(--accent-l) + 5%));
  --clw-support: #8aa8a0;
  --clw-selection: hsla(var(--accent-h), var(--accent-s), var(--accent-l), 0.28);
  --clw-search: hsla(var(--accent-h), var(--accent-s), var(--accent-l), 0.34);
  --clw-shadow: 0 22px 56px rgba(0, 0, 0, 0.36);
  --clw-shadow-s: 0 1px 3px rgba(0, 0, 0, 0.16);
  --clw-shadow-m: 0 4px 12px rgba(0, 0, 0, 0.22);
  --background-primary: var(--clw-paper);
  --background-primary-alt: var(--clw-shell-raised);
  --background-secondary: var(--clw-shell);
  --background-secondary-alt: var(--clw-card);
  --background-modifier-border: var(--clw-border);
  --background-modifier-hover: hsla(var(--accent-h), var(--accent-s), var(--accent-l), 0.12);
  --background-modifier-active-hover: hsla(var(--accent-h), var(--accent-s), var(--accent-l), 0.18);
  --background-modifier-form-field: var(--clw-card-strong);
  --interactive-accent: var(--clw-accent);
  --interactive-accent-hsl: var(--accent-h), var(--accent-s), var(--accent-l);
  --interactive-accent-hover: var(--clw-accent-hover);
  --text-normal: var(--clw-ink);
  --text-muted: var(--clw-ink-muted);
  --text-faint: rgba(160, 144, 128, 0.72);
  --text-on-accent: var(--clw-ink);
  --text-on-accent-inverted: var(--clw-paper);
  --text-accent: var(--clw-accent);
  --text-accent-hover: var(--clw-accent-hover);
  --text-selection: var(--clw-selection);
  --text-highlight-bg: var(--clw-search);
  --clw-strong: color-mix(in srgb, var(--clw-accent-hover) 72%, var(--text-normal));
  --clw-emphasis: color-mix(in srgb, var(--clw-support) 84%, var(--text-normal));
  --clw-inline-code-bg: color-mix(in srgb, var(--clw-card-strong) 74%, var(--clw-accent));
  --clw-inline-code-border: color-mix(in srgb, var(--clw-border) 54%, var(--clw-accent));
  --clw-inline-code-text: color-mix(in srgb, var(--text-normal) 64%, var(--clw-accent-hover));
  --clw-highlight: color-mix(in srgb, var(--clw-accent) 30%, var(--clw-paper));
  --clw-quote-bg: color-mix(in srgb, var(--clw-accent) 8%, transparent);
  --clw-quote-text: color-mix(in srgb, var(--text-normal) 82%, var(--text-muted));
  --clw-code-surface: #0f0d0c;
  --heading-spacing: calc(var(--p-spacing) * 2.18);
  --h1-color: color-mix(in srgb, var(--clw-accent-hover) 62%, var(--text-normal));
  --h2-color: color-mix(in srgb, var(--text-normal) 66%, var(--clw-accent));
  --h3-color: color-mix(in srgb, var(--text-normal) 72%, var(--clw-accent));
  --h4-color: color-mix(in srgb, var(--text-normal) 82%, var(--clw-accent));
  --h5-color: color-mix(in srgb, var(--text-normal) 84%, var(--text-muted));
  --h6-color: color-mix(in srgb, var(--text-muted) 68%, var(--text-normal));
  --h1-letter-spacing: 0;
  --h2-letter-spacing: 0;
  --h3-letter-spacing: 0;
  --h4-letter-spacing: 0;
  --h5-letter-spacing: 0;
  --h6-letter-spacing: 0;
  --h1-line-height: 1.24;
  --h2-line-height: 1.28;
  --h3-line-height: 1.34;
  --h4-line-height: 1.42;
  --h1-size: 1.7em;
  --h2-size: 1.48em;
  --h3-size: 1.28em;
  --h4-size: 1.14em;
  --h5-size: 1.04em;
  --h6-size: 1em;
  --h1-weight: 740;
  --h2-weight: 680;
  --h3-weight: 640;
  --h4-weight: 620;
  --h5-weight: 610;
  --h6-weight: 600;
}
```

- [ ] **Step 4: Bump version in manifest.json**

Replace the entire contents of `manifest.json`:

```json
{
  "name": "Cedar",
  "version": "0.3.0",
  "minAppVersion": "1.5.0",
  "author": "UpandDown"
}
```

- [ ] **Step 5: Visual check**

Open Obsidian with Cedar theme active.
- Light mode: sidebar should be `#efece5` (warm off-white), editor `#faf9f7`, accent links coral.
- Dark mode: sidebar `#1c1917` (warm charcoal), editor `#252119`.
- Accent color should appear as warm coral-orange throughout (buttons, links, active items).

- [ ] **Step 6: Commit and push**

```bash
git add theme.css manifest.json
git commit -m "feat: realign color system to Claude palette, bump to v0.3.0"
git push origin main
```

---

## Task 2: 排版与字体渲染

**Files:**
- Modify: `theme.css` — `body` block and editor/reading surface section

- [ ] **Step 1: Add font rendering to `body` block**

In the `body` block (lines 6–37), add these properties after the last existing variable declaration (before the closing `}`):

```css
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-rendering: optimizeLegibility;
  font-optical-sizing: auto;
```

- [ ] **Step 2: Update line-height in editor section**

Find the existing rule (around line 288):
```css
.markdown-source-view.mod-cm6 .cm-scroller,
.markdown-preview-view {
  line-height: 1.65;
  font-feature-settings: "kern" 1, "liga" 1, "calt" 1, "palt" 1;
}
```

Replace with:
```css
.markdown-source-view.mod-cm6 .cm-scroller,
.markdown-preview-view {
  line-height: 1.68;
  font-feature-settings: "kern" 1, "liga" 1, "calt" 1, "palt" 1;
}
```

- [ ] **Step 3: Add H1 centering**

After the editor/reading surfaces section, add a new `/* H1 centered */` block:

```css
/* H1 centered */
.markdown-rendered h1 {
  text-align: center;
}

.markdown-source-view.mod-cm6 .HyperMD-header.HyperMD-header-1 {
  text-align: center;
}
```

- [ ] **Step 4: Visual check**

- H1 headings in both Reading and Edit view must be centered.
- Body text should appear crisper on macOS (antialiased rendering).
- Line spacing should feel slightly more airy than before.

- [ ] **Step 5: Commit and push**

```bash
git add theme.css
git commit -m "feat: optimize font rendering, center H1, increase line-height to 1.68"
git push origin main
```

---

## Task 3: Callout 全面重设计

**Files:**
- Modify: `theme.css` — `/* Structured note blocks */` section (callout rules)

- [ ] **Step 1: Replace callout structural rules**

Find and replace the entire callout block (`.callout`, `.callout-title`, `.callout-icon`, `.callout-content` rules — approximately lines 461–482):

```css
/* Callout — left stripe + badge icon */
.callout {
  border-left: 4px solid rgb(var(--callout-color));
  border-top: var(--clw-border-width) solid color-mix(in srgb, rgb(var(--callout-color)) 38%, var(--clw-border));
  border-right: var(--clw-border-width) solid color-mix(in srgb, rgb(var(--callout-color)) 38%, var(--clw-border));
  border-bottom: var(--clw-border-width) solid color-mix(in srgb, rgb(var(--callout-color)) 38%, var(--clw-border));
  border-radius: var(--clw-radius-m);
  background: color-mix(in srgb, rgb(var(--callout-color)) 7%, var(--clw-card-strong));
  box-shadow: none;
}

.callout-title {
  background: transparent;
  color: color-mix(in srgb, rgb(var(--callout-color)) 80%, var(--text-normal));
  gap: var(--size-4-2);
  padding: var(--size-4-2) var(--size-4-3);
}

.callout-icon {
  background: rgb(var(--callout-color));
  border-radius: 50%;
  width: 20px;
  height: 20px;
  min-width: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 3px;
  color: white;
}

.callout-icon svg {
  width: 12px;
  height: 12px;
  stroke: white;
  color: white;
}

.callout-content {
  color: var(--text-normal);
  padding: var(--size-4-2) var(--size-4-3) var(--size-4-3);
}
```

- [ ] **Step 2: Add Claude-specific callout types**

Append after the callout structural rules:

```css
/* Claude-specific callout types */
.callout[data-callout="thinking"] { --callout-color: 217, 119, 87; }
.callout[data-callout="prompt"]   { --callout-color: 100, 155, 145; }
.callout[data-callout="context"]  { --callout-color: 192, 154, 64; }
.callout[data-callout="response"] { --callout-color: 122, 170, 128; }
.callout[data-callout="artifact"] { --callout-color: 138, 120, 192; }
```

- [ ] **Step 3: Add standard type color overrides**

Append immediately after:

```css
/* Standard callout type color overrides — warmed to Claude palette */
.callout[data-callout="note"]                                          { --callout-color: 192, 120, 72; }
.callout[data-callout="info"]                                          { --callout-color: 90, 144, 144; }
.callout[data-callout="tip"],
.callout[data-callout="hint"]                                          { --callout-color: 106, 170, 114; }
.callout[data-callout="success"],
.callout[data-callout="check"],
.callout[data-callout="done"]                                          { --callout-color: 106, 170, 114; }
.callout[data-callout="warning"],
.callout[data-callout="caution"],
.callout[data-callout="attention"]                                     { --callout-color: 192, 136, 64; }
.callout[data-callout="failure"],
.callout[data-callout="fail"],
.callout[data-callout="missing"]                                       { --callout-color: 176, 80, 80; }
.callout[data-callout="danger"],
.callout[data-callout="error"]                                         { --callout-color: 184, 88, 88; }
.callout[data-callout="bug"]                                           { --callout-color: 160, 96, 112; }
.callout[data-callout="example"]                                       { --callout-color: 176, 120, 72; }
.callout[data-callout="quote"],
.callout[data-callout="cite"]                                          { --callout-color: 138, 138, 160; }
.callout[data-callout="question"],
.callout[data-callout="faq"],
.callout[data-callout="help"]                                          { --callout-color: 184, 136, 64; }
.callout[data-callout="abstract"],
.callout[data-callout="summary"],
.callout[data-callout="tldr"]                                          { --callout-color: 96, 144, 160; }
.callout[data-callout="todo"]                                          { --callout-color: 217, 119, 87; }
```

- [ ] **Step 4: Visual check**

In the fixture file, create or check callouts:
```
> [!thinking] thinking
> Record reasoning and thought chains here.

> [!prompt] prompt
> Store prompts sent to Claude here.

> [!note] note
> Standard note — should now appear warm coral, not cold blue.
```

Verify: left stripe visible, badge icon circular, background very subtle (not vivid), all standard types use warm colors.

- [ ] **Step 5: Commit and push**

```bash
git add theme.css
git commit -m "feat: callout full redesign — left stripe, badge icons, 5 Claude types, standard types warmed"
git push origin main
```

---

## Task 4: 代码块 Claude 风格

**Files:**
- Modify: `theme.css` — code block rules (`.markdown-rendered pre`, `.HyperMD-codeblock`)

- [ ] **Step 1: Update code block styles**

Find and replace the code block section (`.markdown-rendered pre, .HyperMD-codeblock` — approximately lines 484–494):

```css
/* Code blocks — dark surface in both light and dark mode */
.markdown-rendered pre,
.HyperMD-codeblock {
  border: var(--clw-border-width) solid color-mix(in srgb, var(--clw-code-surface) 60%, var(--clw-border));
  border-radius: var(--clw-radius-m);
  background: var(--clw-code-surface);
}

.markdown-rendered pre {
  overflow-x: auto;
  padding: 0;
}

.markdown-rendered pre code {
  display: block;
  color: #e8ddd0;
  padding: var(--size-4-4);
  line-height: 1.7;
}

/* Language label and copy button bar */
.markdown-rendered pre:has(code[class*="language-"]) {
  position: relative;
}

.copy-code-button {
  background: rgba(255, 255, 255, 0.08) !important;
  color: #a09080 !important;
  border-radius: var(--clw-radius-s) !important;
  border: none !important;
}

.copy-code-button:hover {
  background: rgba(255, 255, 255, 0.14) !important;
  color: #e8ddd0 !important;
}

/* Edit mode code blocks */
.HyperMD-codeblock {
  color: #e8ddd0;
  padding-inline: var(--size-4-4);
}

.cm-line.HyperMD-codeblock-begin,
.cm-line.HyperMD-codeblock-end {
  color: var(--clw-ink-muted);
  background: color-mix(in srgb, var(--clw-code-surface) 80%, var(--clw-shell));
}

/* Syntax highlight tokens on dark surface */
.HyperMD-codeblock .cm-keyword     { color: #e8956a; }
.HyperMD-codeblock .cm-string      { color: #a8c4a0; }
.HyperMD-codeblock .cm-comment     { color: #5a5048; }
.HyperMD-codeblock .cm-number      { color: #c4a882; }
.HyperMD-codeblock .cm-variableName { color: #d4c8b0; }
.HyperMD-codeblock .cm-typeName    { color: #b8a8e0; }
.HyperMD-codeblock .cm-operator    { color: #a09080; }
```

- [ ] **Step 2: Visual check**

Open a note with a fenced code block:
````
```typescript
const greet = (name: string) => {
  return `Hello, ${name}!`;
};
```
````

Verify: dark background in **both** light and dark mode, warm off-white text color `#e8ddd0`, copy button visible with dark styling, syntax tokens show warm colors.

- [ ] **Step 3: Commit and push**

```bash
git add theme.css
git commit -m "feat: dark code block surface for both modes, warm syntax highlight tokens"
git push origin main
```

---

## Task 5: 图片、嵌入块与 Mermaid

**Files:**
- Modify: `theme.css` — add new sections after code blocks

- [ ] **Step 1: Add image and embed styles**

After the code block section, append:

```css
/* Images */
.markdown-rendered img {
  border-radius: var(--clw-radius-m);
  box-shadow: var(--clw-shadow-m);
  max-width: 100%;
}

/* Embedded notes (![[...]]) */
.markdown-embed {
  border-left: 3px solid var(--clw-support);
  border-radius: 0 var(--clw-radius-m) var(--clw-radius-m) 0;
  background: color-mix(in srgb, var(--clw-card) 60%, transparent);
  padding: var(--size-4-2) var(--size-4-3);
  box-shadow: none;
}

.markdown-embed .markdown-embed-title {
  color: var(--clw-support);
  font-weight: 640;
  font-size: 0.92em;
}
```

- [ ] **Step 2: Add Mermaid diagram styles**

Append after the embed rules:

```css
/* Mermaid diagrams */
.markdown-rendered .mermaid {
  background: var(--clw-card-strong);
  border-radius: var(--clw-radius-m);
  border: var(--clw-border-width) solid var(--clw-border);
  padding: var(--size-4-3);
}

.markdown-rendered .mermaid svg {
  max-width: 100%;
}

.mermaid .node rect,
.mermaid .node circle,
.mermaid .node ellipse,
.mermaid .node polygon,
.mermaid .node path {
  fill: color-mix(in srgb, var(--clw-accent) 12%, var(--clw-card-strong)) !important;
  stroke: color-mix(in srgb, var(--clw-accent) 44%, var(--clw-border)) !important;
}

.mermaid .node .label,
.mermaid .nodeLabel {
  color: var(--clw-ink) !important;
}

.mermaid .edgePath .path,
.mermaid .flowchart-link {
  stroke: var(--clw-border) !important;
}

.mermaid .arrowheadPath {
  fill: var(--clw-border) !important;
  stroke: none !important;
}

.mermaid .cluster rect {
  fill: color-mix(in srgb, var(--clw-shell) 60%, transparent) !important;
  stroke: var(--clw-border) !important;
}

.mermaid .label {
  color: var(--clw-ink-muted) !important;
}
```

- [ ] **Step 3: Visual check**

- Embed a note (`![[some-note]]`) — should show a pine-green left stripe.
- Insert an image — should have rounded corners and shadow.
- Create a Mermaid diagram — should use warm card background and border:

```
‍‍‍```mermaid
graph LR
  A[Prompt] --> B[Claude]
  B --> C[Response]
```
```

- [ ] **Step 4: Commit and push**

```bash
git add theme.css
git commit -m "feat: rounded images, Claude-style embeds, Mermaid diagram theming"
git push origin main
```

---

## Task 6: 图谱视图 Claude 化

**Files:**
- Modify: `theme.css` — add graph view section

- [ ] **Step 1: Add graph view rules**

Append to `theme.css`:

```css
/* Graph view — Claude palette */
.theme-light .graph-view.color-fill            { color: var(--clw-ink-muted); }
.theme-light .graph-view.color-fill-focused    { color: var(--clw-accent); }
.theme-light .graph-view.color-fill-tag        { color: var(--clw-support); }
.theme-light .graph-view.color-fill-attachment { color: color-mix(in srgb, var(--clw-accent) 60%, var(--clw-support)); }
.theme-light .graph-view.color-fill-unresolved { color: color-mix(in srgb, var(--clw-border) 70%, transparent); }
.theme-light .graph-view.color-fill-highlight  { color: color-mix(in srgb, var(--clw-accent) 80%, transparent); }
.theme-light .graph-view.color-circle          { color: var(--clw-border); }
.theme-light .graph-view.color-line            { color: color-mix(in srgb, var(--clw-border) 70%, transparent); }
.theme-light .graph-view.color-line-highlight  { color: var(--clw-accent); }
.theme-light .graph-view.color-arrow           { color: var(--clw-accent); }
.theme-light .graph-view.color-text            { color: var(--clw-ink-muted); }

.theme-dark .graph-view.color-fill            { color: var(--clw-ink-muted); }
.theme-dark .graph-view.color-fill-focused    { color: var(--clw-accent); }
.theme-dark .graph-view.color-fill-tag        { color: var(--clw-support); }
.theme-dark .graph-view.color-fill-attachment { color: color-mix(in srgb, var(--clw-accent) 60%, var(--clw-support)); }
.theme-dark .graph-view.color-fill-unresolved { color: color-mix(in srgb, var(--clw-border) 70%, transparent); }
.theme-dark .graph-view.color-fill-highlight  { color: color-mix(in srgb, var(--clw-accent) 80%, transparent); }
.theme-dark .graph-view.color-circle          { color: var(--clw-border); }
.theme-dark .graph-view.color-line            { color: color-mix(in srgb, var(--clw-border) 70%, transparent); }
.theme-dark .graph-view.color-line-highlight  { color: var(--clw-accent); }
.theme-dark .graph-view.color-arrow           { color: var(--clw-accent); }
.theme-dark .graph-view.color-text            { color: var(--clw-ink-muted); }
```

- [ ] **Step 2: Visual check**

Open the Graph view. Verify:
- Regular nodes: muted warm brown.
- Focused/hovered node: coral accent.
- Tag nodes: pine-green (`--clw-support`).
- Connecting lines: subtle warm border color.
- Arrows: coral accent.

- [ ] **Step 3: Commit and push**

```bash
git add theme.css
git commit -m "feat: graph view nodes and edges themed to Claude palette"
git push origin main
```

---

## Task 7: 其他元素 Claude 化

**Files:**
- Modify: `theme.css` — blockquote, tags, modal/prompt, properties, scrollbar, HR, checklist, table

- [ ] **Step 1: Update blockquote**

Find the `blockquote` rule in the `/* Structured note blocks */` section and update:

```css
.markdown-rendered blockquote {
  border-inline-start: 3px solid var(--clw-accent);
  border-radius: 0 var(--clw-radius-s) var(--clw-radius-s) 0;
  background: var(--clw-quote-bg);
  color: var(--blockquote-color);
  padding: var(--size-4-2) var(--size-4-3);
}
```

- [ ] **Step 2: Update tags**

Find `.tag, .cm-hashtag` and replace with:

```css
.tag,
.cm-hashtag {
  border: var(--clw-border-width) solid color-mix(in srgb, var(--clw-accent) 28%, var(--clw-border));
  border-radius: var(--clw-radius-s);
  background: color-mix(in srgb, var(--clw-accent) 9%, var(--clw-card-strong));
  box-shadow: var(--clw-shadow-s);
  color: color-mix(in srgb, var(--clw-accent-hover) 70%, var(--text-normal));
  padding-inline: 0.42em;
}
```

- [ ] **Step 3: Update modal/prompt inputs**

Find `input[type="text"]:focus` block and replace the entire inputs+controls section:

```css
/* Inputs and controls */
input[type="text"],
input[type="search"],
textarea,
select,
.search-input-container input,
.prompt-input {
  border: var(--clw-border-width) solid var(--clw-border);
  border-radius: var(--clw-radius-s);
  background: var(--background-modifier-form-field);
}

input[type="text"]:focus,
input[type="search"]:focus,
textarea:focus,
select:focus,
.search-input-container input:focus,
.prompt-input:focus {
  border-color: var(--interactive-accent);
  box-shadow: 0 0 0 2px color-mix(in srgb, var(--interactive-accent) 20%, transparent);
}

button,
.mod-cta,
.dropdown {
  border-radius: var(--clw-radius-s);
}

.suggestion-item.is-selected,
.menu-item.selected,
.menu-item:hover {
  background: var(--background-modifier-active-hover);
  color: color-mix(in srgb, var(--clw-accent) 80%, var(--text-normal));
}
```

- [ ] **Step 4: Update properties hover state**

Find `.metadata-property:hover` and update:

```css
.metadata-property:hover {
  border-color: color-mix(in srgb, var(--clw-accent) 28%, transparent);
  background: color-mix(in srgb, var(--clw-accent) 6%, transparent);
}
```

- [ ] **Step 5: Update scrollbar**

Find `::-webkit-scrollbar-thumb` and replace the scrollbar section:

```css
/* Custom scrollbar */
::-webkit-scrollbar {
  width: 6px;
  height: 6px;
}

::-webkit-scrollbar-track {
  background: transparent;
}

::-webkit-scrollbar-thumb {
  background: var(--clw-border);
  border-radius: 99px;
}

::-webkit-scrollbar-thumb:hover {
  background: var(--clw-ink-muted);
}
```

(The scrollbar section is already structured this way; just confirm the color references now resolve to the new warm values from Task 1.)

- [ ] **Step 6: Update table row hover**

Find `.markdown-rendered tr:hover td` and update:

```css
.markdown-rendered tr:hover td {
  background: color-mix(in srgb, var(--clw-accent) 6%, transparent);
}
```

- [ ] **Step 7: Visual check**

Verify in the fixture file:
- Blockquote has coral left bar, very subtle warm background.
- `#tags` show warm coral chip styling.
- Command palette input focus glow is coral.
- Selected menu items have coral tint.
- Table row hover is very faint coral.
- Properties hover shows coral border.

- [ ] **Step 8: Commit and push**

```bash
git add theme.css
git commit -m "feat: blockquote, tags, modal, properties, table all aligned to Claude palette"
git push origin main
```

---

## Task 8: README 与 About 更新

**Files:**
- Modify: `README.md`

- [ ] **Step 1: Replace README.md**

```markdown
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
```

- [ ] **Step 2: Visual check**

Confirm the README renders correctly on GitHub — check the callout table and feature list.

- [ ] **Step 3: Commit and push**

```bash
git add README.md
git commit -m "docs: update README to document Claude inspiration, new callout types, v0.3.0 feature list"
git push origin main
```

---

## Self-Review Checklist

- [x] **Spec § 一 (色彩系统)** → Task 1 covers all light/dark variables including shadow updates
- [x] **Spec § 三 (排版)** → Task 2 covers font rendering, H1 center, line-height, ink color
- [x] **Spec § 四 (Callout)** → Task 3 covers structure + 5 Claude types + all standard types
- [x] **Spec § 五 (代码块)** → Task 4 covers dark surface, copy button, syntax tokens
- [x] **Spec § 九 (图片/嵌入)** → Task 5 Step 1
- [x] **Spec § 十 (Mermaid)** → Task 5 Step 2
- [x] **Spec § 八 (图谱视图)** → Task 6
- [x] **Spec § 六其他 (blockquote/table/tags/modal/properties/scrollbar)** → Task 7
- [x] **Spec § 七 (字体渲染)** → Task 2 Step 1
- [x] **Spec § 十一 (阴影)** → Task 1 (shadow variables updated in `.theme-light` and `.theme-dark`)
- [x] **manifest version** → Task 1 Step 4
- [x] **README** → Task 8
