# 02 — CSS Typography, Text & Colors

Complete theory notes with a real-world restaurant landing page. Study this file, then experiment in `index.html` and `style.css`.

## Contents
1. Typography basics
2. Font families and fallback stacks
3. Font size and responsive units
4. Font weight, style, and variants
5. Line height
6. Text alignment and decoration
7. Letter spacing, word spacing, and text transform
8. Indentation, wrapping, overflow, and breaking
9. Text shadows and contrast
10. Web fonts and `@font-face`
11. CSS color formats
12. Alpha and opacity
13. Gradients
14. CSS custom properties
15. Advanced typography patterns
16. Project walkthrough
17. Accessibility and common mistakes
18. Practice tasks
19. Quick revision

---

## 1. Typography basics

**Typography** is the design and arrangement of text. It affects readability, hierarchy, tone, and the overall character of an interface.

A useful hierarchy typically includes:
- **Hero/display heading:** largest text, used sparingly.
- **Section heading:** announces a new part of the page.
- **Body text:** comfortable for longer reading.
- **Eyebrow/caption:** short supporting label.
- **Button/link text:** concise and easy to identify.

If every line is bold, uppercase, large, or colorful, nothing stands out. Use emphasis intentionally.

HTML provides structure and meaning. CSS controls the visual presentation:

```html
<h1 class="page-title">Seasonal cooking</h1>
<p class="intro">Good ingredients, treated well.</p>
```

```css
.page-title {
    font-family: Georgia, serif;
    font-size: 3rem;
    color: #3c261b;
}

.intro {
    font-family: system-ui, sans-serif;
    line-height: 1.7;
}
```

## 2. Font families and fallback stacks

Use `font-family` to choose the preferred font and fallbacks:

```css
body {
    font-family: Arial, Helvetica, sans-serif;
}

h1 {
    font-family: Georgia, "Times New Roman", serif;
}

code {
    font-family: "Courier New", monospace;
}
```

Common families:
- `serif`: letterforms with small finishing strokes; often editorial or traditional.
- `sans-serif`: no serifs; often clean and modern.
- `monospace`: characters use consistent horizontal spacing; useful for code.
- `system-ui`: uses the operating system's UI font.
- `cursive` and `fantasy`: appearance varies considerably by platform.

The browser tries the list from left to right. A fallback is important because a named font may not be installed. Writing a font name does **not** download that font.

If a name contains spaces, quote it: `"Times New Roman"`.

## 3. Font size and responsive units

```css
body { font-size: 1rem; }
h1 { font-size: 3rem; }
.caption { font-size: 0.875rem; }
```

- `px`: CSS pixels; useful for small precise values.
- `rem`: relative to the root element's font size; good for a consistent type scale.
- `em`: relative to the element's computed font size for `font-size`; context can matter for other properties.
- `%`: relative to the reference size for the property.
- `vw`: 1% of the viewport width.

If the browser root size is 16px, `1rem` is typically 16px, `1.5rem` 24px, and `0.875rem` 14px. Users can change their browser defaults, so do not assume it is always 16px.

### Responsive type with `clamp()`

```css
.hero-title {
    font-size: clamp(2.5rem, 6vw, 5rem);
}
```

`clamp(minimum, preferred, maximum)` lets a value scale within limits. Here the title grows with viewport width but remains within the minimum and maximum. Test at narrow screens and zoom levels; never shrink body text to an uncomfortable size.

## 4. Font weight, style, and variants

### `font-weight`

```css
.light { font-weight: 300; }
.normal { font-weight: 400; }
.medium { font-weight: 500; }
.semibold { font-weight: 600; }
.bold { font-weight: 700; }
.extra-bold { font-weight: 800; }
```

`normal` is 400 and `bold` is 700. Numeric weights from 1–1000 are supported, but the font must contain the requested weight to render it exactly. Browsers may synthesize weights that are not available.

### `font-style`

```css
.quote { font-style: italic; }
.slanted { font-style: oblique; }
```

Italic often uses a specifically designed italic face. Oblique generally slants the normal face.

### `font-variant`

```css
.label { font-variant: small-caps; }
```

Small caps use smaller capital letterforms where supported. For advanced OpenType control, prefer high-level properties such as `font-variant-ligatures` when they meet the need; low-level `font-feature-settings` is available for specialized cases.

## 5. Line height

`line-height` controls the height of each line box and strongly affects readability.

```css
body { line-height: 1.6; }
h1 { line-height: 1.05; }
```

A unitless value is a good default because it scales with font size. Body text often benefits from more line spacing than large headings. Values like `1.5` are starting points, not universal laws; test actual paragraphs and headings that wrap.

## 6. Text alignment and decoration

### `text-align`

```css
.left { text-align: left; }
.center { text-align: center; }
.right { text-align: right; }
.justified { text-align: justify; }
```

`text-align` aligns inline content inside line boxes; it does not center the block element itself. To center a constrained block, use `max-width` and `margin-inline: auto`. Left-aligned text is usually easier to read in left-to-right languages. Justified text can create uneven spaces, especially in narrow columns.

### `text-decoration`

```css
a {
    text-decoration: underline;
    text-decoration-color: currentColor;
    text-decoration-thickness: 0.08em;
    text-underline-offset: 0.2em;
}
```

Common decoration lines are `underline`, `overline`, `line-through`, and `none`. Links should remain recognizable and keyboard-accessible if you remove their underline.

## 7. Letter spacing, word spacing, and text transform

```css
.eyebrow {
    letter-spacing: 0.14em;
    text-transform: uppercase;
}

.copy {
    word-spacing: 0.08em;
}
```

- `letter-spacing`: adjusts space between characters.
- `word-spacing`: adjusts space between words.
- `text-transform: uppercase`: displays text in uppercase without changing the underlying HTML.
- `lowercase`: displays lowercase.
- `capitalize`: capitalizes word beginnings according to CSS text transformation rules.

Letter spacing is useful for short labels, but too much harms word recognition. Avoid long uppercase paragraphs.

## 8. Indentation, wrapping, overflow, and breaking

### Indentation

```css
.article-paragraph { text-indent: 2em; }
```

`text-indent` indents the first formatted line, not the entire element.

### Whitespace and wrapping

```css
.normal { white-space: normal; }
.preserve-breaks { white-space: pre-line; }
.code-like { white-space: pre-wrap; }
.no-wrap { white-space: nowrap; }
```

- `normal`: collapses ordinary whitespace and wraps normally.
- `pre`: preserves spaces and line breaks; normally does not wrap.
- `pre-wrap`: preserves whitespace and line breaks and allows wrapping.
- `pre-line`: preserves line breaks while collapsing runs of spaces.
- `nowrap`: prevents line wrapping.

### Overflow and long words

```css
.single-line {
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
}

.long-url {
    overflow-wrap: anywhere;
}
```

Ellipsis requires a constrained box and is normally used for a single line. `overflow-wrap: anywhere` helps long words or URLs avoid overflowing. `word-break: break-all` breaks more aggressively and is usually not the first choice for normal prose.

## 9. Text shadows and contrast

```css
.hero-title {
    text-shadow: 0 2px 12px rgb(0 0 0 / 25%);
}
```

The common order is horizontal offset, vertical offset, blur radius, and color. Multiple shadows can be comma-separated. Shadows should not replace sufficient contrast; text over photographs needs reliable contrast across all parts of the image.

## 10. Web fonts and `@font-face`

```css
@font-face {
    font-family: "Restaurant Display";
    src: url("fonts/restaurant-display.woff2") format("woff2");
    font-style: normal;
    font-weight: 400;
    font-display: swap;
}

h1 {
    font-family: "Restaurant Display", Georgia, serif;
}
```

The font URL is relative to the CSS file. Use properly licensed font files; WOFF2 is a common efficient web format. `font-display: swap` lets fallback text show while the font loads. For a variable font, a supported weight range can be declared. Static font files should declare their actual weight.

This project uses system fonts and therefore needs no external font download. Third-party font services can add network requests and should be considered for performance, privacy, availability, and licensing.

## 11. CSS color formats

### Named colors

```css
color: tomato;
background-color: ivory;
```

### Hexadecimal

```css
color: #ffffff; /* white */
color: #000000; /* black */
color: #c96b3b; /* warm orange-brown */
```

`#RRGGBB` specifies red, green, and blue channels. `#RGB` is shorthand when each channel digit repeats (`#f00` equals `#ff0000`). `#RRGGBBAA` adds alpha; `#RGBA` is the shorthand form.

### RGB

```css
color: rgb(201 107 59);
color: rgb(201 107 59 / 80%);
```

RGB defines red, green, and blue channel values. Modern syntax allows alpha after `/`.

### HSL

```css
color: hsl(20 55% 51%);
color: hsl(20 55% 51% / 80%);
```

HSL means hue (angle), saturation (percentage), and lightness (percentage), with optional alpha. It can be convenient for creating related shades by changing lightness or saturation while keeping hue similar.

### `currentColor`

```css
.card {
    color: #3d2b24;
    border: 1px solid currentColor;
}
```

`currentColor` uses the element's computed text color. It is handy for matching borders, outlines, and SVG details to text.

## 12. Alpha and opacity

### Alpha on one color

```css
.overlay {
    background-color: rgb(20 20 20 / 60%);
}
```

Only that color is transparent; text inside the element can remain fully opaque.

### `opacity`

```css
.faded-element { opacity: 0.5; }
```

`opacity` affects the entire rendered element and its descendants. It can create a stacking context when below `1`. If only the background should be translucent, use a color with alpha rather than reducing the parent's opacity.

## 13. Gradients

Gradients are CSS-generated images.

```css
.hero {
    background-image: linear-gradient(
        120deg,
        #24170f 0%,
        #7e4025 55%,
        #d28a50 100%
    );
}
```

Other types:

```css
.radial {
    background-image: radial-gradient(circle, #fff2d6, #c96b3b);
}

.conic {
    background-image: conic-gradient(#c96b3b, #f3d7a5, #c96b3b);
}
```

Gradients can be layered with background images. A gradient overlay can help text contrast over a photo, but test the actual image behind the text.

## 14. CSS custom properties

Custom properties (often called CSS variables) store reusable values:

```css
:root {
    --color-ink: #2c211b;
    --color-paper: #fffaf3;
    --color-accent: #b84e2b;
    --space-md: 1rem;
    --radius-card: 1rem;
}

body {
    color: var(--color-ink);
    background: var(--color-paper);
}

.button {
    padding: var(--space-md);
    border-radius: var(--radius-card);
    background: var(--color-accent);
}
```

They make site-wide changes easier and help keep colors, spacing, and radii consistent. Fallbacks are allowed: `color: var(--text-color, #222);`. Custom properties normally inherit and are resolved where used.

## 15. Advanced typography patterns

### Fluid type

```css
.section-title { font-size: clamp(1.75rem, 3vw, 3rem); }
```

### Font shorthand

```css
.card-copy { font: italic 600 1rem/1.7 Georgia, serif; }
```

Common shorthand order: style/weight, size, optional `/line-height`, then family. Shorthand resets other font-related subproperties, so separate declarations may be clearer while learning.

### Text selection

```css
::selection {
    color: white;
    background: #8b3d22;
}
```

Keep selected text readable. Supported properties may be limited.

### Text over an image

```css
.hero {
    color: white;
    background:
        linear-gradient(rgb(20 15 10 / 65%), rgb(20 15 10 / 35%)),
        url("images/restaurant.jpg") center / cover no-repeat;
}
```

The first background layer is painted on top. Ensure the image path exists and text remains readable if the image fails to load.

## 16. Real-world project: Saffron & Stone

The companion `index.html` builds a restaurant landing page with:
- Brand and navigation.
- Hero heading and call-to-action.
- Three menu cards and prices.
- Story section.
- Reservation details and footer.
- Responsive layout for smaller screens.

### Design tokens in `style.css`

| Token | Purpose |
|---|---|
| `--color-ink` | Main text |
| `--color-paper` | Warm page background |
| `--color-accent` | Main restaurant accent |
| `--font-body` | Body text stack |
| `--font-display` | Heading stack |
| `--radius-card` | Consistent card rounding |

Why the design works:
- Serif headings give an editorial restaurant mood.
- A system sans-serif body font supports comfortable reading without an external request.
- Repeated accent colors create consistency across buttons, prices, and labels.
- `clamp()` makes the hero title responsive.
- Line-height and constrained text width reduce dense, hard-to-read paragraphs.
- `:focus-visible` styling supports keyboard users.
- Reduced-motion preferences are respected.
- The dish illustrations are made with CSS, so the demo has no image assets to download.

The address and email are demonstration content; replace them before publishing a real restaurant site.

## 17. Accessibility and common mistakes

1. Do not use color alone to communicate meaning; include text, icons, or another cue.
2. Normal text generally needs a contrast ratio of at least **4.5:1** for WCAG AA; large text generally needs at least **3:1**. Check actual foreground/background pairs.
3. Avoid tiny body text and test browser zoom.
4. Avoid long uppercase passages.
5. Do not remove link underlines or focus outlines without accessible replacements.
6. Avoid lowering a whole parent element's opacity if its text must stay fully opaque.
7. Always provide font fallbacks.
8. Use text shadows sparingly.
9. Truncate content only when hiding the rest is intentional.
10. Avoid fixed heights on text-heavy cards unless overflow is handled.
11. Use semantic headings, not just large paragraphs.
12. Test on narrow screens and with zoom.

## 18. Practice tasks

### Beginner
- Change the body font stack and compare serif/sans-serif.
- Set all section headings to one consistent color.
- Compare paragraph line-height values `1.4`, `1.6`, and `1.8`.
- Add an uppercase eyebrow using `text-transform` and `letter-spacing`.
- Express the accent color in hex, RGB, and HSL.

### Intermediate
- Build a palette using custom properties.
- Use `clamp()` for hero and section headings.
- Add a subtle text shadow without reducing legibility.
- Make long dish descriptions wrap cleanly.
- Add keyboard-visible focus styles to interactive elements.
- Add a gradient over a photo and check contrast.

### Advanced
- Load a licensed local WOFF2 font with `@font-face`.
- Create light and dark theme tokens.
- Experiment with a variable font's weight range.
- Add ellipsis to a constrained single-line tag.
- Check contrast for every text/background pair.
- Test at 320px, 768px, and desktop widths.

## 19. Quick revision

```css
/* Typography */
body { font-family: system-ui, sans-serif; }
h1 { font-size: clamp(2rem, 5vw, 4rem); }
strong { font-weight: 700; }
p { line-height: 1.6; }

/* Text */
.eyebrow { letter-spacing: 0.12em; text-transform: uppercase; }
a { text-decoration: underline; }
.centered-text { text-align: center; }

/* Color formats */
.a { color: tomato; }
.b { color: #c96b3b; }
.c { color: rgb(201 107 59); }
.d { color: hsl(20 55% 51%); }

/* Transparency */
.overlay { background: rgb(0 0 0 / 50%); }
.faded { opacity: 0.5; }

/* Reusable tokens */
:root {
    --color-ink: #2c211b;
    --color-paper: #fffaf3;
    --color-accent: #b84e2b;
}
```

**Best learning method:** change one property, predict the result, refresh the browser, then explain why it happened. That builds understanding rather than memorizing declarations.
