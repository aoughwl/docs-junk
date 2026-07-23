# docs-junk

The junk drawer for the [aoughwl](https://aoughwl.github.io) public sites — the
scrappy, explicit HTML/CSS/JS bits that dress up the docs and playground. This is
**not** a library or an API; it's copy-paste site chrome. Vendor what you need.

## `chrome.js` / `chrome.css`

Fancy hover tooltips (`[data-tip]`) and a unified right-click context menu.

```html
<link rel="stylesheet" href="chrome.css">
```
```js
import { initTooltips, initContextMenu } from './chrome.js'

initTooltips()   // any element with data-tip gets a floating label

initContextMenu((target) => {
  const sel = window.getSelection()?.toString() || ''
  return [
    { label: 'Copy', kb: '⌘C', off: !sel, act: () => navigator.clipboard?.writeText(sel) },
    { sep: true },
    { label: 'Copy page link', act: () => navigator.clipboard?.writeText(location.href) },
  ]
}, { allowNativeOn: 'input, textarea' })
```

Colors read from `--aui-*` (or fall back to VitePress `--vp-*`, or a dark default).
