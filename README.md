# @thanh-libs/typography

A theme-aware Typography component built on [Emotion](https://emotion.sh) with automatic semantic HTML tags, WCAG 2.2 accessibility, and text utilities.

## Requirements

| Peer Dependency | Version |
|-----------------|---------|
| `react` | `>=18.0.0` |
| `react-dom` | `>=18.0.0` |
| `@emotion/react` | `>=11.0.0` |
| `@emotion/styled` | `>=11.0.0` |
| `@thanh-libs/theme` | `>=0.0.3` |
| `@thanh-libs/utils` | `>=0.0.4` |

## Installation

```bash
npm install @thanh-libs/typography @thanh-libs/theme @thanh-libs/utils @emotion/react @emotion/styled
```

> Requires `ThemeProvider` from `@thanh-libs/theme` wrapping your app.

## Quick Start

```tsx
import { Typography } from '@thanh-libs/typography';

<Typography variant="h1">Heading 1</Typography>
<Typography variant="body">Body text</Typography>
<Typography variant="h3" color="primary">Colored heading</Typography>
```

## Props

| Prop | Type | Default | Description |
|------|------|---------|-------------|
| `variant` | `'h1' \| 'h2' \| 'h3' \| 'h4' \| 'h5' \| 'body'` | `'body'` | Typography variant — maps to theme typography scale |
| `component` | `ElementType` | auto | Override rendered HTML tag |
| `color` | `string` | `'inherit'` | Palette key (`'primary'`, `'error'`, `'success'`, `'warning'`, `'info'`), `'inherit'`, or CSS color |
| `align` | `'left' \| 'center' \| 'right' \| 'justify' \| 'inherit'` | `'inherit'` | Text alignment |
| `weight` | `number` | from theme | Override font weight |
| `gutterBottom` | `boolean` | `false` | Add `margin-bottom: 0.35em` |
| `noWrap` | `boolean` | `false` | Truncate with ellipsis (single line) |
| `children` | `ReactNode` | — | Content |

## Variant → HTML Tag Mapping

| Variant | Default Tag | Font Size | Weight | Line Height |
|---------|-------------|-----------|--------|-------------|
| `h1` | `<h1>` | 38px | 700 | 1.2 |
| `h2` | `<h2>` | 30px | 700 | 1.3 |
| `h3` | `<h3>` | 24px | 600 | 1.4 |
| `h4` | `<h4>` | 20px | 600 | 1.5 |
| `h5` | `<h5>` | 16px | 600 | 1.5 |
| `body` | `<p>` | 14px | 400 | 1.6 |

## Features

### Theme-aware
Reads `typography` scale from `ThemeSchema`. Falls back to built-in defaults.

### Color resolution
```tsx
<Typography color="primary">Uses theme.palette.primary.main</Typography>
<Typography color="error">Uses theme.palette.error.dark</Typography>
<Typography color="#FF5722">Direct CSS color</Typography>
```

### WCAG 2.2 Accessibility
When using a heading variant with a non-heading tag, `role="heading"` and `aria-level` are auto-added:
```tsx
<Typography variant="h1" component="span">
  {/* Renders: <span role="heading" aria-level="1">...</span> */}
</Typography>
```

### Text utilities
```tsx
<Typography noWrap>This very long text will be truncated...</Typography>
<Typography gutterBottom>Adds bottom margin for spacing</Typography>
<Typography weight={700}>Bold override</Typography>
```

## License

MIT
