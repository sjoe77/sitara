# Sitara Design System

Enterprise-grade CSS component library for **Banks**, **FinTechs**, and **Insurance** companies.

Zero JavaScript dependencies. Drop in one CSS file and build production-ready interfaces immediately.

**[Live Showcase →](https://sjoe77.github.io/sitara/showcase/)**

---

## Why Sitara?

| Feature | Details |
|---|---|
| **CSS-only** | No runtime JS, no framework coupling — works with React, Vue, Angular, plain HTML |
| **Theme system** | Three pre-built themes (Banking, FinTech, Insurance) switchable with a single `data-theme` attribute |
| **Accessible** | ARIA patterns, keyboard navigation, and focus management built in |
| **Responsive** | Mobile-first, collapses gracefully at every breakpoint |
| **Batteries included** | App shell (banner + sidebar), icon library, full form suite, data tables, workflow tracker |

---

## Quick Start

### Option 1 — Copy the file (recommended for getting started)

```html
<!DOCTYPE html>
<html lang="en" data-theme="banking">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>My App</title>
  <link rel="stylesheet" href="path/to/sitara.css">
</head>
<body>
  <button class="st-btn st-btn--primary">Get Started</button>
</body>
</html>
```

### Option 2 — npm

```bash
npm install sitara-ds
```

```html
<link rel="stylesheet" href="node_modules/sitara-ds/src/sitara.css">
```

Or import in your bundler:

```js
import 'sitara-ds/src/sitara.css';
```

### Option 3 — CDN (jsDelivr)

```html
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/sitara-ds/src/sitara.css">
```

---

## Themes

Apply a theme by setting `data-theme` on any ancestor element (commonly `<html>`):

```html
<!-- Banking: deep navy + gold -->
<html data-theme="banking">

<!-- FinTech: violet + cyan -->
<html data-theme="fintech">

<!-- Insurance: forest teal + amber -->
<html data-theme="insurance">

<!-- Default: indigo -->
<html>
```

Themes can be scoped to any element — not just `<html>`:

```html
<div data-theme="fintech">
  <!-- Everything inside uses the FinTech palette -->
</div>
```

---

## App Shell

Sitara ships a complete application shell. Wrap your app like this:

```html
<input type="checkbox" id="st-sidebar-toggle">

<div class="st-app">

  <!-- Top banner -->
  <header class="st-banner" role="banner">
    <label for="st-sidebar-toggle" class="st-banner__hamburger">…</label>
    <a href="/" class="st-banner__logo">…</a>
    <div class="st-banner__spacer"></div>
    <div class="st-banner__actions">…</div>
  </header>

  <!-- Left sidebar -->
  <nav class="st-sidebar" aria-label="Main navigation">
    <div class="st-sidebar__nav">…</div>
  </nav>

  <!-- Main content -->
  <main class="st-app__main">
    <div class="st-content">…</div>
  </main>

</div>
```

The sidebar collapse is **CSS-only** — powered by the `<input type="checkbox">` trick. No JavaScript needed.

---

## Component Reference

| Category | Components |
|---|---|
| **Inputs** | Button, Input, Textarea, Select, Checkbox, Radio, Toggle |
| **Feedback** | Badge, Alert, Avatar, Progress bar, Step indicator |
| **Container** | Card, Stat card, Tabs, Accordion, Table + Pagination, Workflow tracker |
| **Layout** | 12-column Grid, Page header, Content wrapper |
| **Navigation** | App banner, Sidebar (collapsible, grouped), Breadcrumb, Dropdown |
| **Icons** | 70+ Lucide-compatible SVG icons with sizing helpers |

Full documentation and live examples: **[sjoe77.github.io/sitara/showcase](https://sjoe77.github.io/sitara/showcase/)** — or open `showcase/index.html` locally.

---

## File Structure

```
sitara/
├── src/
│   ├── sitara.css          ← main bundle (import this)
│   ├── tokens.css          ← design tokens (CSS custom properties)
│   ├── reset.css           ← CSS normalisation
│   ├── themes/
│   │   ├── banking.css
│   │   ├── fintech.css
│   │   └── insurance.css
│   └── components/
│       ├── buttons.css
│       ├── forms.css
│       ├── layout.css
│       ├── navigation.css
│       ├── interactive.css
│       ├── data.css
│       └── icons.css
└── showcase/
    ├── index.html          ← component showcase
    ├── icons.html          ← icon library & search
    ├── getting-started.html← installation guide
    └── showcase.css        ← showcase-only styles
```

---

## Design Tokens

All values are CSS custom properties prefixed with `--st-`. Override any token at the `:root` level or inside a scoped selector to customise the system without touching source files:

```css
:root {
  --st-color-accent: #0057B7;      /* your brand colour */
  --st-card-radius: 8px;           /* tighten card corners */
  --st-font-sans: 'Your Font', sans-serif;
}
```

Key token groups:

| Group | Example tokens |
|---|---|
| Colour | `--st-color-accent`, `--st-color-bg`, `--st-color-surface`, `--st-color-text` |
| Semantic colour | `--st-color-success`, `--st-color-warning`, `--st-color-danger`, `--st-color-info` |
| Spacing | `--st-space-1` … `--st-space-16` (4 px scale) |
| Typography | `--st-text-xs` … `--st-text-4xl`, `--st-font-sans`, `--st-font-mono` |
| Radius | `--st-radius-sm` … `--st-radius-full` |
| Shadow | `--st-shadow-xs` … `--st-shadow-xl` |
| Transition | `--st-transition-fast`, `--st-transition-base`, `--st-transition-slow` |

---

## Icons

Sitara ships 70+ Lucide-compatible SVG icons. Add `.st-icon` to any `<svg>` for automatic sizing and colour inheritance:

```html
<!-- Inline SVG (recommended) -->
<svg class="st-icon st-icon--lg" viewBox="0 0 24 24">
  <circle cx="11" cy="11" r="8"/>
  <path d="m21 21-4.35-4.35"/>
</svg>

<!-- Size modifiers: --xs --sm --md --lg --xl --2xl -->
<!-- Colour modifiers: --muted --accent --success --warning --danger --info -->
<!-- Animated: --spin (for loader icons) -->
```

Browse all icons with search at `showcase/icons.html`.

---

## Browser Support

| Browser | Minimum version |
|---|---|
| Chrome / Edge | 88+ |
| Firefox | 85+ |
| Safari | 14+ |
| iOS Safari | 14+ |

Relies on CSS custom properties, `color-mix()`, `:has()`, and `@layer` — all green in evergreen browsers.

---

## Accessibility

- All interactive components use correct ARIA roles and attributes
- Keyboard navigable (Tab, Enter, Space, Arrow keys)
- Sufficient colour contrast ratios in all three themes (WCAG AA)
- Focus rings styled to be visible and on-brand
- Screen-reader-friendly labels on icon-only buttons

---

## Contributing

1. Fork the repo
2. Create a feature branch: `git checkout -b feature/my-component`
3. Make your changes in `src/components/`
4. Test in the showcase: `npm start`
5. Open a pull request

---

## License

MIT © Sitara Design System
