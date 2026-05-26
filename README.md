# reports-style

A warm, editorial visual style for long-form HTML reports — analyses, plans, design docs, comparison pages.

## What's here

- **`style.css`** — the stylesheet. Drop-in via `<link rel="stylesheet" href="style.css">`. Override `--accent` and `--accent-soft` in a per-report `<style>` block to re-skin the visual rhythm.
- **`template.html`** — a starter report that uses every supported component once, so it acts as both a copy-paste starting point and living documentation.
- **`palettes.md`** — pre-tuned accent / accent-soft color pairs.

## Quick start

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<title>My report</title>
<link rel="stylesheet" href="style.css">
<style>
  :root {
    --accent: #245a8d;
    --accent-soft: #e8f0f7;
  }
</style>
</head>
<body>
  <h1>My report</h1>
  <p class="subtitle">One-line description.</p>
  <!-- … -->
</body>
</html>
```

For an index/landing page, add `class="landing"` to `<body>` — narrower max-width, slightly larger body type, and the `a.lcard` clickable cards become idiomatic.

## Design recipe

### Palette (warm "paper" feel, not stark)

Stable neutrals — leave alone:

| Token             | Value      | Used for                          |
|-------------------|------------|-----------------------------------|
| `--bg`            | `#fafaf7`  | Page background (warm off-white)  |
| `--fg`            | `#1c1c1c`  | Body text (softer than pure black)|
| `--muted`         | `#5a5a5a`  | Secondary text, h4 eyebrows       |
| `--line`          | `#d8d4cb`  | Dividers, borders (warm beige)    |
| `--table-head`    | `#f0ede5`  | Table header row                  |
| `--code-bg`       | `#ececea`  | Inline code background            |

Accent — override per report (see `palettes.md`):

| Token             | Default    | Used for                                              |
|-------------------|------------|-------------------------------------------------------|
| `--accent`        | `#245a8d`  | Card h4, links, default phase-block / callout border  |
| `--accent-soft`   | `#e8f0f7`  | `.callout` background, `.pill.p2` background          |

Semantic accents — generally stable across reports:

| Token             | Value      | Used for                              |
|-------------------|------------|---------------------------------------|
| `--good` / `-soft`| `#166534` / `#dcfce7` | Recommendations, "go" signals |
| `--warn` / `-soft`| `#b54708` / `#fef3c7` | Caveats, gotchas             |
| `--skip` / `-soft`| `#6b7280` / `#f1f5f9` | "Out of scope"               |
| `--danger`/`-soft`| `#991b1b` / `#fde2e2` | Critical / "do not"          |

### Typography

- System stack: `-apple-system, BlinkMacSystemFont, "SF Pro Text", Helvetica, Arial`
- 15px / 1.55 body (16px on landing pages)
- 30px h1, 22px h2, 17px h3
- **h4 is an eyebrow label**, not a body heading — uppercase, tracked-out (`letter-spacing: 0.04em`), muted color
- Code in `"SF Mono", Menlo, Consolas` at 13px
- Subtle negative letter-spacing on headings (`-0.01em` on h1, `-0.005em` on h2)

### Layout rules

- `max-width: 1100px` for reports, `900px` for landing pages — never edge-to-edge
- Generous whitespace: 48px above h2, 28px above h3, 18px between phase blocks
- White content surfaces on the warm background, 1px beige border, 8px radius
- **Left-border accent strips** (4–6px solid color) are the main visual rhythm — used for `.phase-block`, `.callout`, `.verdict`, `a.lcard`

## Component cheat sheet

| Class                       | What it is                                                                       |
|-----------------------------|----------------------------------------------------------------------------------|
| `.subtitle`                 | Muted lede paragraph under the h1                                                |
| `.toc`                      | Table-of-contents box (white card with thin border)                              |
| `.grid`                     | Responsive auto-fit grid; pair with `.card`                                      |
| `.twocol`                   | Two-column block, collapses on narrow screens                                    |
| `.card`                     | White panel, thin border, 8px radius; h4 inside takes the accent                 |
| `.callout`                  | Inline highlighted note; left strip + soft background; `.warn` / `.good` variants|
| `.phase-block`              | Numbered section panel with a colored left strip (use `.p1` / `.p2` / `.p3` / `.p4` / `.skip` to pick the strip color) |
| `.phase-header`             | Flex container for `<pill>` + `<h3>` at the top of a phase block                 |
| `.pill`                     | Tiny rounded badge; phase variants `.p1` `.p2` `.p3` `.p4` `.skip`              |
| `.verdict`                  | Closing recommendation block (always green; signals the final positive call)     |
| `.meta` / `.small`          | Muted helper text (13px)                                                         |
| `a.lcard`                   | Full-bleed clickable card for landing pages; takes a `.title`, `.desc`, `.filename` |
| `.eyebrow`                  | Small uppercase section label for landing pages                                  |
| `body.landing`              | Add to `<body>` on index pages — narrower max-width, slightly larger body type   |

## How to re-skin a report

Two lines:

```css
:root {
  --accent: #1f5b3b;       /* new hue */
  --accent-soft: #e3f1e8;  /* same hue lifted to ~92% lightness */
}
```

That cascades through links, card h4 color, the default `.phase-block` / `.callout` / `a.lcard` left-strip, the `.pill.p2` background, and the TOC link color. No other CSS edits needed.

## What this style is and isn't

**Is:** an editorial-feeling style for long-form analysis, plans, and design docs. Designed to read on screen as if it were printed — warm background, generous whitespace, restrained color use.

**Isn't:** a UI framework. There are no buttons, forms, modals, or interactive states beyond the lcard hover. Don't try to build an app with this.

## Inspirations

Stripe Press / Tufte CSS (editorial restraint, warm paper feel), Linear and Vercel docs (white-card-on-tinted-bg layout, generous spacing), iA Writer / Bear Notes (warm-neutral palette over pure grayscale).
