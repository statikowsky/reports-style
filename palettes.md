# Palettes

Pre-tuned `--accent` + `--accent-soft` pairs. Drop into the per-report override block in `template.html`:

```html
<style>
  :root {
    --accent:      /* pick from below */;
    --accent-soft: /* paired soft */;
  }
</style>
```

The soft variant is roughly the accent at ~92% lightness — bright enough to be a callout/pill background, muted enough not to overpower the warm `#fafaf7` page.

## Warm-editorial set (default)

| Name          | `--accent`  | `--accent-soft` | Notes                            |
|---------------|-------------|-----------------|----------------------------------|
| Editorial blue| `#245a8d`   | `#e8f0f7`       | Default. Calm, professional.     |
| Burnt rust    | `#8b3a1a`   | `#fbeee5`       | Warmer, slightly redder.         |
| Forest        | `#1f5b3b`   | `#e3f1e8`       | Natural, organic.                |
| Plum          | `#6a3e9b`   | `#ede4f7`       | Slightly playful, still subdued. |
| Slate ink     | `#3a4554`   | `#eaecf0`       | Neutral / monochrome reports.    |

## Language reports (Go / Rust / Odin trio)

Tuned to feel kin to each language's own brand color but adjusted to fit on the warm background.

| Language | `--accent`  | `--accent-soft` |
|----------|-------------|-----------------|
| Go       | `#245a8d`   | `#e8f0f7`       |
| Rust     | `#8b3a1a`   | `#fbeee5`       |
| Odin     | `#1f5b3b`   | `#e3f1e8`       |

## Picking your own

Rules of thumb:
- Pick a saturated, medium-dark accent (lightness around 30–40%). It needs to read against white card backgrounds.
- Generate the soft variant by lifting lightness to ~92–95% while keeping the hue. Online HSL pickers work fine, or in CSS terms: same hue, much lower saturation, much higher lightness.
- Test: the accent should be readable as h4 text inside a `.card`, and the soft variant should still read as background (text on top stays black) without dominating.
- Avoid pure red, pure yellow, or anything near `#000` or `#fff` — the semantic colors (warn / good / skip / danger) already cover those bands.
