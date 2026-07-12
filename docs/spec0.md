## SPECIFICATION: `minstrap`

### 1. Custom Elements
- `<ms-container>` – Grid container  
- `<ms-row>` – Flex row wrapper for columns  
- `<ms-column>` – Column (child of a row)

No polyfills or JavaScript required; style via element selectors.

### 2. Breakpoints
| Breakpoint | Min-width  |
|------------|------------|
| xs         | none (< 576px) |
| sm         | 576px      |
| md         | 768px      |
| lg         | 992px      |
| xl         | 1200px     |
| xxl        | 1400px     |

Base styles (no media query) apply to xs and up.

### 3. Container
- Default `<ms-container>` has `width: 100%` and `padding-left/right:
  calc(var(--ms-gutter-x) / 2)` (inherits gutter).
- Max-widths set in `:root` via custom properties and applied inside
  media queries:

  | Breakpoint | Max-width custom property  | Value |
  |------------|----------------------------|-------|
  | sm         | `--ms-container-max-width-sm` | 540px |
  | md         | `--ms-container-max-width-md` | 720px |
  | lg         | `--ms-container-max-width-lg` | 960px |
  | xl         | `--ms-container-max-width-xl` | 1140px |
  | xxl        | `--ms-container-max-width-xxl`| 1320px |

- Fluid container: `<ms-container class="fluid">` →
  `width: 100%; max-width: 100%` at all breakpoints.

### 4. Row
- `display: flex; flex-wrap: wrap`
- Negative margins using `var(--ms-gutter-x)` and `var(--ms-gutter-y)`:
  ```css
  margin-left: calc(var(--ms-gutter-x) / -2);
  margin-right: calc(var(--ms-gutter-x) / -2);
  margin-top: calc(var(--ms-gutter-y) / -2);
  margin-bottom: calc(var(--ms-gutter-y) / -2);
  ```
- Default gutter: `--ms-gutter-x: 1.5rem; --ms-gutter-y: 0` (set in `:root`).

### 5. Column
- Default bare `<ms-column>`: `flex: 1 0 0%` (equal‑width).
- Padding: `padding-left: calc(var(--ms-gutter-x) / 2); padding-right:
  calc(var(--ms-gutter-x) / 2);` (and same for Y if `--ms-gutter-y` >
  0).
- Spanned columns get `flex: 0 0 <width>`.

### 6. Span Classes
- **Base** (apply at all viewports): `.span-1` through `.span-12`,
  plus `.span-auto`.
- **Responsive** (apply at breakpoint and wider): `.sm-1` … `.sm-12`,
  `.md-1` … `.md-12`, `.lg-1` … `.lg-12`, `.xl-1` … `.xl-12`, `.xxl-1`
  … `.xxl-12`, plus `.sm-auto`, `.md-auto`, etc.
- No `xs-*` prefix; base `.span-*` covers the smallest viewport.

Widths calculated using `--ms-columns: 12`:
```css
/* example */
.span-6 { flex: 0 0 calc(6 / var(--ms-columns) * 100%); }
@media (min-width: 576px) {
  .sm-6 { flex: 0 0 calc(6 / var(--ms-columns) * 100%); }
}
```
`.auto` variants: `width: auto; flex: 0 0 auto;`.

### 7. Gutter Modifiers
Classes `.g-0` through `.g-5` (applied to `<ms-row>`) override the gutter custom properties:

| Class | `--ms-gutter-x` / `--ms-gutter-y` |
|-------|-----------------------------------|
| `.g-0` | 0 |
| `.g-1` | 0.25rem |
| `.g-2` | 0.5rem |
| `.g-3` | 1rem |
| `.g-4` | 1.5rem |
| `.g-5` | 3rem |

All classes set both `--ms-gutter-x` and `--ms-gutter-y` to the same value.

### 8. Nesting
- Place an `<ms-row>` inside an `<ms-column>`.
- Nested rows use the same negative margins and gutter mechanics,
  canceling the parent column’s padding.

### 9. Excluded Features
- Offset classes
- Order classes
- Alignment classes (horizontal/vertical on row or column)
- Any JavaScript or CSS preprocessor

### 10. Implementation Notes
- All base element styles use tag selectors (`ms-container`, `ms-row`,
  `ms-column`).
- CSS custom properties defined inside `:root`.
- Gutter modifiers and responsive span classes written manually.
- No `col-` prefix; span classes are simply `span-{size}` and
  `{breakpoint}-{size}`.
- `--ms-columns: 12` used in `calc()` for all width definitions.
- Container max‑widths stored as individual custom properties and
  applied in media queries.
