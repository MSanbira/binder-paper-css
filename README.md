# binder-paper-css

A simple binder paper–like stylesheet you can use in any project.

Works both as an npm package and via CDN (jsDelivr).

## Install (npm)

```bash
npm install binder-paper-css
```

Then import the CSS in your app entry:

```js
// ESM
import 'binder-paper-css';

// or import the CSS file directly (works in Vite, Next, CRA, etc.)
import 'binder-paper-css/style.css';
```

Use the class in your markup:

```html
<div class="BPCSS-page">
  <h1>Notebook vibes ✏️</h1>
  <h2>Lines, margin and punch holes</h2>
  <p>
    This page has repeating horizontal lines, a red margin guide, and punch-hole
    effects. Typography scales by line-height to align to the grid.
  </p>
  
  <h3>Supported Elements</h3>
  <p>All text elements align to the line grid:</p>
  <ul>
    <li>Headings (h1, h2, h3) with different sizes</li>
    <li>Paragraphs with proper line spacing</li>
    <li>Ordered lists (ol) and unordered lists (ul)</li>
  </ul>
  
  <h3>RTL Support</h3>
  <p>
    When the document direction is RTL, the red margin line and holes flip
    automatically to the appropriate side.
  </p>
</div>
```

## CDN (jsDelivr)

No build step? Use the CDN:

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/binder-paper-css/style.css">
```

To lock a specific version, include it in the URL (recommended for production):

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/binder-paper-css@0.1.0/style.css">
```

## Customize

Override the provided CSS variables to tweak the look. The stylesheet defines some
global sizing variables and component-specific variables:

```css
:root {
  /* Global scale (min 12px). Changing this scales the whole sheet. */
  --BPCSS-global-font-size: max(2vmin, 12px);
  
  /* Line spacing system derived from the global scale */
  --BPCSS-line-height-num: 0.5;  /* multiplier for line spacing */
  --BPCSS-line-height-space: calc(var(--BPCSS-line-height-num) * var(--BPCSS-global-font-size));
  --BPCSS-line-height: calc(var(--BPCSS-line-height-space) + 1 * var(--BPCSS-global-font-size));
  
  /* Font family for the notebook content */
  --BPCSS-font-family: cursive;
}

.BPCSS-page {
  /* Visual appearance */
  --page-line-height: calc(0.1 * var(--BPCSS-global-font-size));   /* thickness of blue lines */
  --padding-block: calc(var(--BPCSS-line-height) * 2);
  --max-width: 50em;
  --whitespace-height: calc(var(--BPCSS-line-height) - var(--page-line-height));
  --holes-position: calc(2 * var(--BPCSS-global-font-size));       /* x-position of punch holes */
  --red-line-position: 90deg;                                      /* orientation of red margin line */
}
```

## Files

- `style.css` — the stylesheet (also the default jsDelivr entry)
- `index.js` — JS entry that imports `style.css` for bundlers
- `demo.html` — interactive demo with live controls for testing

## Supported Elements

The stylesheet provides proper line-grid alignment for:

- **Headings**: `h1`, `h2`, `h3` with different row sizes (3, 2, 1 respectively)
- **Paragraphs**: `p` elements with baseline alignment
- **Lists**: `ol` and `ul` with proper indentation and item spacing
- **List items**: `li` elements that inherit proper typography

## Notes

- **Direction-aware**: Uses the `:dir(rtl)` selector. If your document or a parent element uses `dir="rtl"`, the red margin line and punch holes will flip to the appropriate side.
- **Scalable design**: All measurements are derived from `--BPCSS-global-font-size`, so you can scale the entire design by changing a single variable.
- **Typography alignment**: All text elements align to the ruled line background for a realistic notebook appearance.
- **List support**: Both ordered and unordered lists maintain proper spacing and indentation that scales with the global font size.

## License

MIT © Matan Sanbira
