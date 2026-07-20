# minstrap

A minimal, zero-dependency CSS grid system built with custom elements
and CSS custom properties.

Inspired by Bootstrap.

## Features

- Custom elements: `ms-container`, `ms-row`, `ms-column`. No classes
  required layouts
- 12-column grid: `.span-1` to `.span-12`, plus `.span-auto` for
  content-sized columns
- Five responsive breakpoints: `sm` (576px), `md` (768px), `lg`
  (992px), `xl` (1200px), `xxl` (1400px)
- Responsive span classes: `.sm-*`, `.md-*`, `.lg-*`, `.xl-*`,
  `.xxl-*` override the base span at each breakpoint.
- Container max widths: container snaps to fixed widths at each
  breakpoint; `.fluid` for full‑width containers.
- Gutter modifiers: `.g-0` through `.g-5` on rows to adjust horizontal
  and vertical spacing.
- Nesting: rows can be placed inside columns for complex layouts.
- CSS custom properties: easily override gutter sizes, column count,
  and breakpoint widths.

## Quick Start

```html
<link rel="stylesheet" href="minstrap.css">

<ms-container>
  <ms-row>
    <ms-column class="span-12 sm-6 md-4">
      Responsive column
    </ms-column>
    <ms-column class="span-12 sm-6 md-4">
      Responsive column
    </ms-column>
    <ms-column class="span-12 sm-6 md-4">
      Responsive column
    </ms-column>
  </ms-row>
</ms-container>
```

Check out the accompanying [html](minstrap.html) for a more
comprehensive demonstration.
