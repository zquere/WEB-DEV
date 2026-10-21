# CSS Units and Sizing

A practical learning module for understanding CSS units, element sizing, the box model, and responsive layouts.

## Folder structure

```text
CSS/
└── 2.3-units-and-sizing/
    ├── README.md
    ├── index.html
    └── style.css
```

## Learning goals

By the end of this module, you should be able to:

- Explain absolute and relative CSS units.
- Choose between `px`, `%`, `em`, `rem`, `vw`, and `vh`.
- Control element dimensions with `width`, `height`, `min-width`, `max-width`, `min-height`, and `max-height`.
- Explain `content-box` and `border-box`.
- Calculate an element's rendered width.
- Use `calc()`, `min()`, `max()`, and `clamp()`.
- Build a layout that adapts to different screen sizes.

---

## 1. What are CSS units?

CSS units specify the size of things such as text, spacing, borders, and element dimensions.

```css
.card {
  width: 300px;
  padding: 1rem;
  margin-bottom: 2rem;
  font-size: 1rem;
}
```

The number tells CSS the amount; the unit tells CSS how to interpret that amount. Most non-zero length values need a unit.

## 2. Absolute units

Absolute units have fixed conversion relationships. On screens, `px` is the most commonly used CSS absolute unit.

| Unit | Meaning | Example |
|---|---|---|
| `px` | CSS pixel | `width: 320px;` |
| `cm` | centimetre | `width: 5cm;` |
| `mm` | millimetre | `width: 20mm;` |
| `in` | inch | `width: 2in;` |
| `pt` | point (1/72 inch) | `font-size: 12pt;` |
| `pc` | pica (12 points) | `width: 2pc;` |

Use `px` when a dimension should be precise, such as a thin border or a small icon detail. For layouts and text, relative units often adapt more comfortably to user settings and different viewports.

> A CSS pixel is not necessarily one physical screen pixel. Browsers map CSS pixels to device pixels.

## 3. Relative units

Relative units depend on another value, such as a parent element's size, the root font size, or the viewport.

| Unit | Relative to | Example |
|---|---|---|
| `%` | Usually the relevant containing block's size | `width: 80%;` |
| `em` | The element's font size for `font-size`; otherwise generally the element's computed font size | `padding: 1.5em;` |
| `rem` | Root (`html`) font size | `font-size: 1.25rem;` |
| `vw` | 1% of viewport width | `width: 50vw;` |
| `vh` | 1% of viewport height | `min-height: 100vh;` |
| `vmin` | 1% of the smaller viewport dimension | `padding: 2vmin;` |
| `vmax` | 1% of the larger viewport dimension | `padding: 2vmax;` |
| `ch` | Width of the `0` glyph in the current font | `max-width: 65ch;` |
| `ex` | x-height of the current font | `margin-top: 2ex;` |
| `lh` | Element's line height | `margin-bottom: 1lh;` |
| `rlh` | Root element's line height | `padding: 1rlh;` |

### `%` versus `vw`

```css
.panel {
  width: 80%;
}

.hero {
  width: 80vw;
}
```

- `80%` is calculated against the relevant containing block.
- `80vw` is 80% of the viewport width, regardless of the panel's parent width.

For most normal page layouts, `%` is useful for flexible widths inside containers. Use viewport units when sizing should be tied directly to the browser viewport.

### `em` versus `rem`

```css
html {
  font-size: 16px;
}

.parent {
  font-size: 20px;
}

.child {
  font-size: 1.5em;   /* 30px in this example */
  padding: 1rem;      /* 16px when the root font size is 16px */
}
```

- `em` can depend on the element's font size and can compound in nested typography.
- `rem` depends on the root element's font size, so it is more predictable for consistent site-wide spacing and typography.

Do not assume `1rem` is always 16px: users or stylesheets can change the root font size.

## 4. Width and height

```css
.box {
  width: 20rem;
  height: 12rem;
}
```

- `width` sets the preferred inline size in the usual horizontal writing mode.
- `height` sets the preferred block dimension in the usual horizontal writing mode.
- A fixed `height` can cause content to overflow if the content grows.
- For text-heavy content, `min-height` is often safer than a rigid `height`.

### `auto`

```css
img {
  max-width: 100%;
  height: auto;
}
```

`auto` lets the browser calculate a value based on layout rules. For images, `height: auto` preserves the image's intrinsic aspect ratio when its width changes.

### Minimum and maximum sizing

```css
.container {
  width: 90%;
  max-width: 1100px;
  min-width: 0;
  margin-inline: auto;
}
```

- `min-width` / `min-height` set lower limits.
- `max-width` / `max-height` set upper limits.
- `width: 90%; max-width: 1100px` makes a container flexible while preventing it from becoming excessively wide.

In flexbox and grid layouts, `min-width: 0` can let a child shrink below its automatic min-content size, helping prevent overflow.

## 5. The CSS box model

Every element is laid out as a box made up of:

1. **Content** — text, images, or child content.
2. **Padding** — space between content and border.
3. **Border** — line around padding and content.
4. **Margin** — space outside the border.

### `content-box` (the default)

With `box-sizing: content-box`, the declared width applies to the content only.

```css
.box {
  width: 300px;
  padding: 20px;
  border: 5px solid;
}
```

Total outer width, excluding margins:

`300 + 20 + 20 + 5 + 5 = 350px`

### `border-box`

```css
*,
*::before,
*::after {
  box-sizing: border-box;
}
```

With `border-box`, the declared width includes the content, padding, and border. The content area becomes smaller to make room for padding and border.

For most modern layouts, using `border-box` makes sizing easier to reason about.

### Total width and height

For `content-box`:

```text
Outer width = width + left/right padding + left/right border + left/right margin
Outer height = height + top/bottom padding + top/bottom border + top/bottom margin
```

For `border-box`, the declared width and height already include padding and border, but margins remain outside the box.

## 6. Margin collapsing

In normal block layout, adjacent vertical margins can sometimes collapse into a single margin rather than add together.

Example:

```css
.first {
  margin-bottom: 30px;
}

.second {
  margin-top: 20px;
}
```

When these vertical margins collapse, the gap is generally `30px`, not `50px`. This is a special rule for certain block-flow situations; margins do not collapse in every layout mode or in every relationship.

To create predictable internal spacing, padding or `gap` in flexbox/grid layouts is often easier to manage.

## 7. Modern sizing functions

### `calc()`

Combines values in a calculation. Operators need spaces around `+` and `-`.

```css
.sidebar {
  width: calc(100% - 2rem);
}
```

### `min()` and `max()`

```css
.wide-panel {
  width: min(90%, 70rem);
}

.readable-panel {
  width: max(80%, 20rem);
}
```

`min()` chooses the smallest supplied value; `max()` chooses the largest. Make sure the values and units make sense for the property.

### `clamp()`

`clamp(minimum, preferred, maximum)` sets a value that can grow or shrink within limits.

```css
h1 {
  font-size: clamp(2rem, 5vw, 4rem);
}
```

The font size responds to viewport width but will not go below `2rem` or above `4rem`.

## 8. Responsive sizing

Responsive design means a page adjusts to different screen sizes and available space. A flexible layout should not depend on one fixed desktop width.

### Use a fluid container

```css
.container {
  width: min(92%, 1100px);
  margin-inline: auto;
}
```

The container uses most of the available width on a small screen but stops growing beyond `1100px`.

### Use a responsive grid

```css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 220px), 1fr));
  gap: 1rem;
}
```

Cards fit into as many columns as available space allows, then wrap to fewer columns on narrower screens.

### Make images flexible

```css
img {
  display: block;
  max-width: 100%;
  height: auto;
}
```

This prevents an image from exceeding its container while keeping its aspect ratio.

### Use media queries when the layout needs a change

```css
.layout {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 2rem;
}

@media (max-width: 700px) {
  .layout {
    grid-template-columns: 1fr;
  }
}
```

A media query changes styles when the viewport meets the condition. Choose breakpoints based on where your content stops fitting well, not only on named devices.

### Responsive checklist

- Avoid fixed widths that are wider than a phone screen.
- Prefer `max-width` for readable page containers.
- Use flexible grids, flexbox, and `gap`.
- Let text wrap naturally; use `clamp()` only when a fluid size is useful.
- Use `max-width: 100%; height: auto` for responsive images.
- Test by resizing the browser and using its device emulation tools.
- Watch for horizontal scrolling and clipped content.

## 9. Try the practice page

Open `index.html` in your browser. Then edit `style.css` and observe what changes when you:

1. Change the root font size and compare `em` with `rem`.
2. Change `.demo-box` from `content-box` to `border-box`.
3. Change the container's `max-width`.
4. Resize the browser to see the card grid reflow.
5. Adjust the `clamp()` values for the heading.
6. Temporarily add a fixed width to a card and observe whether it causes overflow.

## 10. Practice tasks

- [ ] Create a container with `width: 90%` and `max-width: 1000px`.
- [ ] Create two boxes using `em` and `rem` spacing and compare them.
- [ ] Calculate the outer width of a `250px` content box with `12px` padding and `3px` borders.
- [ ] Make an image responsive.
- [ ] Build a three-card grid that becomes one column on a narrow viewport.
- [ ] Use `clamp()` to make a heading scale smoothly.
- [ ] Inspect the page at narrow, medium, and wide viewport widths.

## Quick reference

| Goal | Good starting point |
|---|---|
| Consistent site-wide spacing | `rem` |
| Spacing tied to local typography | `em` |
| Flexible child width | `%` |
| Viewport-based sizing | `vw`, `vh` |
| Readable text measure | `ch` |
| Flexible but capped container | `width: min(92%, 1100px)` |
| Fluid font size with limits | `clamp()` |
| Predictable box dimensions | `box-sizing: border-box` |
| Responsive images | `max-width: 100%; height: auto` |
