# minstrap – Implementation Checklist

## Phase 1: Foundation (Container + Row + Basic Column)

- [x] Define CSS custom properties in `:root`:
  - `--ms-gutter-x: 1.5rem`
  - `--ms-gutter-y: 0`
  - `--ms-columns: 12`
  - All `--ms-container-max-width-*` properties (sm through xxl)
- [x] Style `<ms-container>` (width: 100%, padding using gutter)
- [x] Style `<ms-row>` (flex, wrap, negative margins)
- [x] Style bare `<ms-column>` (flex: 1 0 0%, padding)
- [x] **Visual test:** 3 equal-width columns in a row inside a container

## Phase 2: Base Span Classes

- [x] Add `.span-1` through `.span-12` (using `calc(N / var(--ms-columns) * 100%)`)
- [x] Add `.span-auto` (width: auto; flex: 0 0 auto)
- [x] **Visual test:** Row with `.span-4`, `.span-6`, `.span-2` (sum to 12) and `.span-auto`

## Phase 3: Container Max-Widths

- [x] Add media queries for container max-widths (sm, md, lg, xl, xxl)
- [x] Add `.fluid` class (max-width: 100% at all breakpoints)
- [x] **Visual test:** Container snaps to max-widths; fluid stays 100%

## Phase 4: Gutter Modifiers

- [x] Add `.g-0` through `.g-5` classes on `<ms-row>` (set both gutter vars)
- [x] **Visual test:** Rows with different gutter classes (g-0, g-2, g-5)

## Phase 5: Responsive Span Classes

- [x] Add `.sm-1` through `.sm-12` and `.sm-auto` (media query 576px)
- [x] Add `.md-*` (768px)
- [x] Add `.lg-*` (992px)
- [x] Add `.xl-*` (1200px)
- [x] Add `.xxl-*` (1400px)
- [x] **Visual test:** Columns that change layout at breakpoints (e.g., `.span-12 .md-6 .lg-4`)

## Phase 6: Nesting

- [x] Verify nested rows inside columns work (negative margins cancel padding)
- [x] **Visual test:** Nested grid with inner row of 2 columns

## Phase 7: Edge Cases & Polish

- [x] Test all breakpoints together for conflicts
- [x] Test `.span-auto` and responsive auto variants
- [x] **Final visual test:** Complex layout exercising all features, resize browser
