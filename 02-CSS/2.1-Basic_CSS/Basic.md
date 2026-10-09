# 01 — Introduction to CSS

> Complete beginner-friendly notes for learning CSS after HTML. This chapter explains the concepts first, then lets you test them in a working HTML/CSS playground.

## Contents

1. [What is CSS?](#1-what-is-css)
2. [CSS syntax](#2-css-syntax)
3. [Three ways to apply CSS](#3-three-ways-to-apply-css)
4. [External stylesheet and file paths](#4-external-stylesheet-and-file-paths)
5. [CSS comments and readable organization](#5-css-comments-and-readable-organization)
6. [Selectors](#6-selectors)
7. [Combinators: relationships between elements](#7-combinators-relationships-between-elements)
8. [Attribute selectors](#8-attribute-selectors)
9. [Pseudo-classes and links](#9-pseudo-classes-and-links)
10. [Pseudo-elements](#10-pseudo-elements)
11. [Specificity, cascade, and inheritance](#11-specificity-cascade-and-inheritance)
12. [CSS values and units](#12-css-values-and-units)
13. [The box model](#13-the-box-model)
14. [Total width and total height](#14-total-width-and-total-height)
15. [Margin collapsing](#15-margin-collapsing)
16. [Display and basic layout behavior](#16-display-and-basic-layout-behavior)
17. [Common mistakes](#17-common-mistakes)
18. [Practice tasks](#18-practice-tasks)
19. [Quick revision](#19-quick-revision)

---

## 1. What is CSS?

**CSS (Cascading Style Sheets)** describes how HTML elements should look and how they should be laid out.

- **HTML** provides structure and meaning: headings, paragraphs, links, lists, forms, images.
- **CSS** controls presentation: colors, fonts, spacing, borders, sizes, and layout.
- **JavaScript** adds behavior: responding to clicks, validating forms, changing content, and more.

Example HTML:

```html
<p class="notice">Welcome to my website.</p>
```

CSS:

```css
.notice {
    color: navy;
    background-color: #eaf2ff;
    padding: 12px;
}
```

The HTML creates a paragraph. CSS selects it using its class and changes its appearance.

### How a browser applies CSS

1. The browser reads the HTML and builds a document tree.
2. It loads and parses available CSS.
3. It matches CSS selectors to HTML elements.
4. It resolves competing declarations using the cascade and specificity.
5. It calculates layout and paints the result on screen.

CSS is not a programming language in the same sense as JavaScript or C++; it is a stylesheet language with rules and values.

## 2. CSS syntax

A CSS rule has this shape:

```css
selector {
    property: value;
    another-property: another-value;
}
```

Example:

```css
h1 {
    color: darkblue;
    font-size: 32px;
}
```

- `h1` is the **selector**: which elements to target.
- `color` and `font-size` are **properties**: what aspect to change.
- `darkblue` and `32px` are **values**.
- Each `property: value` pair is a **declaration**.
- Curly braces `{ }` contain the declarations.
- A semicolon `;` ends a declaration. The final semicolon is good practice even when the parser could omit it.

CSS property names are generally written in lowercase. Spelling a property incorrectly usually means the browser ignores that declaration.

## 3. Three ways to apply CSS

### 3.1 Inline CSS

CSS is written in an element's `style` attribute.

```html
<p style="color: crimson; font-weight: bold;">
    This is inline-styled text.
</p>
```

**Use:** quick experiments or exceptional one-off styling.

**Limitations:** mixes presentation into HTML, is hard to reuse, and is difficult to maintain across a website. Inline declarations also have high precedence in the normal author cascade compared with ordinary selector rules.

### 3.2 Internal CSS

CSS is written in a `<style>` element, usually inside `<head>`.

```html
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
        }

        .notice {
            color: darkgreen;
        }
    </style>
</head>
```

**Use:** small standalone pages, demos, or a page-specific experiment.

**Limitations:** the rules are tied to that HTML file and cannot be reused automatically by other pages.

### 3.3 External CSS

CSS is written in a separate `.css` file and connected using `<link>`.

HTML:

```html
<head>
    <link rel="stylesheet" href="style.css">
</head>
```

`style.css`:

```css
body {
    font-family: Arial, sans-serif;
}

.notice {
    color: darkgreen;
}
```

**Usually best for projects:** it separates structure from presentation, supports reuse, and makes styles easier to maintain. Browsers can cache external stylesheets.

### Which method should you prefer?

| Method | Where CSS lives | Typical use |
|---|---|---|
| Inline | HTML `style` attribute | Rare one-off styles |
| Internal | HTML `<style>` element | Small demo or single-page example |
| External | Separate `.css` file | Normal websites and learning projects |

When multiple applicable declarations compete, the browser uses the cascade. Do not assume “external always wins” or “the last file always wins”; importance, origin, cascade layers, specificity, and source order can all matter.

## 4. External stylesheet and file paths

Given:

```text
project/
├── index.html
└── style.css
```

Use:

```html
<link rel="stylesheet" href="style.css">
```

If the CSS is in a folder:

```text
project/
├── index.html
└── css/
    └── style.css
```

Use:

```html
<link rel="stylesheet" href="css/style.css">
```

The `href` is a path to the stylesheet, relative to the HTML document's URL (or a URL). File and folder names must match. `Style.css` and `style.css` may be treated as different names depending on the system/server.

A `<link rel="stylesheet">` belongs in the document's `<head>` as a normal convention. The browser fetches the stylesheet and applies its rules.

## 5. CSS comments and readable organization

Comments explain the code and are ignored by the CSS parser.

```css
/* This is a CSS comment. */

/*
  A multi-line comment can describe
  a complete section.
*/

body {
    margin: 0; /* Remove the browser's default body margin */
}
```

CSS comments start with `/*` and end with `*/`. CSS does not use `//` for comments.

Use meaningful section headings, consistent indentation, and related rules grouped together. Avoid comments that merely repeat obvious code.

## 6. Selectors

A **selector** describes which HTML elements a rule targets.

### 6.1 Universal selector: `*`

Matches all elements:

```css
* {
    box-sizing: border-box;
}
```

This is often used for a predictable box model. It does not select pseudo-elements unless they are included explicitly (for example, `*, *::before, *::after`).

### 6.2 Element/type selector: `p`, `h1`, `div`

Matches all elements of that type:

```css
p {
    line-height: 1.6;
}

h1 {
    color: navy;
}
```

`div` selects every `<div>`. It does not mean “select a parent”; parent/child relationships are expressed with combinators.

### 6.3 Class selector: `.class-name`

HTML:

```html
<p class="highlight">First paragraph</p>
<p class="highlight">Second paragraph</p>
```

CSS:

```css
.highlight {
    background-color: #fff1a8;
}
```

A class can be reused on many elements. An element can have multiple classes:

```html
<p class="highlight important">Read this carefully.</p>
```

```css
.highlight { background-color: #fff1a8; }
.important { font-weight: bold; }
```

Class names are case-sensitive in HTML/CSS matching in modern standards contexts; choose simple lowercase names such as `card-title`.

### 6.4 ID selector: `#id-name`

HTML:

```html
<h1 id="page-title">CSS Notes</h1>
```

CSS:

```css
#page-title {
    color: darkblue;
}
```

An ID should be unique within the document. IDs are useful for unique elements, fragment links, and JavaScript hooks, but classes are generally more reusable for styling.

### 6.5 Grouping selectors: comma `,`

Applies the same declarations to several selectors:

```css
h1,
h2,
h3 {
    font-family: Georgia, serif;
}
```

The comma means “and also select this other group.” It does not mean descendants.

### 6.6 Compound selectors: no space

Selects an element that satisfies all listed selector parts:

```css
p.highlight {
    color: darkred;
}

.card.featured {
    border: 2px solid royalblue;
}

a#special-link {
    font-weight: bold;
}
```

`p.highlight` means a `<p>` element with class `highlight`. It does not mean a paragraph inside an element with class `highlight`.

### 6.7 Selector comparison

| Selector | Meaning |
|---|---|
| `p` | Every paragraph |
| `*` | Every element |
| `.note` | Every element with class `note` |
| `#header` | The element with ID `header` |
| `p.note` | Paragraphs that have class `note` |
| `.menu a` | Links anywhere inside `.menu` |
| `.menu > a` | Links that are direct children of `.menu` |
| `h2, p` | All `h2` elements and all paragraphs |
| `h2 + p` | A paragraph immediately after an `h2` |
| `h2 ~ p` | Paragraph siblings that follow an `h2` |

## 7. Combinators: relationships between elements

Combinators describe relationships in the HTML tree. For these examples:

```html
<div class="parent">
    <p>Direct child paragraph</p>

    <section>
        <p>Nested paragraph</p>
    </section>
</div>
```

### 7.1 Descendant combinator: a space

```css
.parent p {
    color: blue;
}
```

Matches **every `<p>` inside `.parent` at any depth**, including the nested paragraph. A space is meaningful: `.parent p` differs from `.parentp`.

### 7.2 Child combinator: `>`

```css
.parent > p {
    color: green;
}
```

Matches only `<p>` elements that are **direct children** of `.parent`. It does not match the paragraph inside `<section>`.

### 7.3 Adjacent sibling combinator: `+`

```html
<h2>Title</h2>
<p>This paragraph immediately follows the heading.</p>
<p>This one does not immediately follow the heading.</p>
```

```css
h2 + p {
    color: purple;
}
```

Matches the first paragraph because it is the next element sibling after the `h2`. Whitespace and comments between them do not create an element sibling.

### 7.4 General sibling combinator: `~`

```css
h2 ~ p {
    color: brown;
}
```

Matches paragraphs that come after the `h2` and share the same parent, even if other element siblings sit between them. It does not match paragraphs nested inside another element.

### Quick way to remember

- `A B`: B is somewhere inside A.
- `A > B`: B is a direct child of A.
- `A + B`: B is the next element sibling after A.
- `A ~ B`: B is a later element sibling after A.

## 8. Attribute selectors

Attribute selectors target elements based on HTML attributes.

```css
a[target] {
    border-bottom: 2px solid;
}

input[type="email"] {
    background-color: #eef5ff;
}

a[href^="https"] {
    color: seagreen;
}

a[href$=".pdf"] {
    font-weight: bold;
}

a[href*="github"] {
    text-decoration-style: dashed;
}
```

| Pattern | Meaning |
|---|---|
| `[attr]` | Attribute exists |
| `[attr="value"]` | Exact value |
| `[attr^="value"]` | Value starts with this text |
| `[attr$="value"]` | Value ends with this text |
| `[attr*="value"]` | Value contains this text |

These selectors are useful for forms, external links, file links, and other elements with meaningful attributes.

## 9. Pseudo-classes and links

A **pseudo-class** selects an element in a particular state or position. It starts with a single colon, such as `:hover`.

### 9.1 Link states

```css
a:link {
    color: #155eef;
}

a:visited {
    color: #6b3fa0;
}

a:hover {
    color: #d1242f;
    text-decoration: none;
}

a:active {
    color: #e67700;
}

a:focus-visible {
    outline: 3px solid orange;
    outline-offset: 3px;
}
```

- `:link`: an unvisited link.
- `:visited`: a visited link, with browser privacy restrictions on which properties can change visibly.
- `:hover`: the pointer is over the element.
- `:active`: the element is being activated, such as while a mouse button is held.
- `:focus-visible`: the element has keyboard-style focus where the browser decides a visible focus indicator is appropriate.

The familiar ordering is **LVHFA**: `:link`, `:visited`, `:hover`, `:active`. It helps prevent one link-state rule from unexpectedly overriding another. Focus styling is separate and should not be removed without a good accessible replacement.

`:hover` is not reliable as the only way to reveal important information because touch devices may not have hover.

### 9.2 Structural pseudo-classes

```css
li:first-child {
    font-weight: bold;
}

li:last-child {
    color: crimson;
}

li:nth-child(2) {
    background-color: #fff1a8;
}

li:nth-child(odd) {
    /* Targets odd-numbered matching siblings */
}

p:not(.intro) {
    /* Paragraphs without class intro */
}
```

- `:first-child`: first element child of its parent.
- `:last-child`: last element child of its parent.
- `:nth-child(n)`: selects according to sibling position.
- `:nth-child(odd)` / `:nth-child(even)`: odd/even positions.
- `:not(selector)`: excludes elements matching a selector.
- `:checked`: selected checkbox/radio option.
- `:disabled`: disabled form control.
- `:required`: form control marked required.

`:nth-child(2)` counts element siblings, not only siblings of the same tag. For the second paragraph specifically, use `p:nth-of-type(2)` when that is the intended rule.

## 10. Pseudo-elements

A **pseudo-element** styles a specific part of an element or creates a generated box. It generally uses two colons.

```css
p::first-letter {
    font-size: 2rem;
    font-weight: bold;
}

p::first-line {
    color: darkblue;
}

.note::before {
    content: "Note: ";
    font-weight: bold;
}

.note::after {
    content: " ✓";
}
```

- `::before` and `::after` create generated content inside an element's box; the `content` property is required for generated text.
- `::first-letter` targets the first typographic letter.
- `::first-line` targets the first formatted line, which can change when the layout changes.
- `::selection` styles selected text in supported ways.

Do not use generated content as a replacement for essential information that must be available to assistive technologies.

## 11. Specificity, cascade, and inheritance

When several rules set the same property on the same element, the browser needs a way to decide which value wins.

### 11.1 Specificity

A useful simplified comparison is:

1. ID selectors — `#title`
2. Class, attribute, and pseudo-class selectors — `.card`, `[disabled]`, `:hover`
3. Element and pseudo-element selectors — `p`, `::before`

Universal selector `*` and combinators such as `>` do not add specificity themselves. A compound selector's specificity comes from its selector parts.

Example:

```css
p { color: black; }             /* element */
.message { color: blue; }       /* class */
#status { color: red; }         /* ID */
```

```html
<p id="status" class="message">Which color?</p>
```

The text is red because `#status` has higher specificity than `.message` and `p`.

Specificity is not the only cascade factor. Origin, importance (`!important`), cascade layers, and scoping can affect the winner before specificity is compared. If otherwise equal, later source order wins.

### 11.2 Source order

```css
p { color: blue; }
p { color: orange; }
```

Both selectors have equal specificity and importance. The later declaration wins, so the paragraph is orange.

### 11.3 Inheritance

Some properties, such as `color` and `font-family`, are normally inherited by children:

```css
body {
    color: #222;
    font-family: Arial, sans-serif;
}
```

Descendant text usually inherits these values unless another rule sets them.

Properties such as `margin`, `padding`, `border`, and `width` are not normally inherited. A child does not automatically get its parent's margin.

### 11.4 The cascade is not simply “last rule wins”

“Last rule wins” only works when the declarations are otherwise tied in the relevant cascade comparisons. A later low-specificity rule may lose to an earlier high-specificity rule.

Avoid using `!important` as a routine fix:

```css
p {
    color: red !important;
}
```

It makes normal overrides harder and can create specificity battles. Understand the conflict and fix the selector or rule organization instead.

## 12. CSS values and units

### Common units

| Unit | Meaning | Typical use |
|---|---|---|
| `px` | CSS pixel | Borders, small precise spacing |
| `%` | Relative to a property's reference size | Fluid widths |
| `em` | Relative to the element's font size for font-size; otherwise often to the element's computed font size | Local scalable sizing |
| `rem` | Relative to the root element's font size | Consistent spacing and typography |
| `vw` | 1% of viewport width | Viewport-related sizing |
| `vh` | 1% of viewport height | Viewport-related sizing |

Examples:

```css
.box {
    width: 80%;
    padding: 1rem;
    border: 1px solid #aaa;
}

h1 {
    font-size: 2rem;
}
```

For most beginner projects, start with `px`, `%`, and `rem`. Learn other units as needed. Unit behavior can depend on the property; for example, percentages do not always refer to the same parent dimension.

### Colors

```css
color: red;
color: #ff0000;
color: rgb(255 0 0);
color: hsl(0 100% 50%);
```

CSS color syntax includes named colors, hexadecimal, RGB, HSL, and other modern formats.

### Common properties

```css
.example {
    color: #222;                    /* text color */
    background-color: white;        /* background */
    font-size: 16px;                /* text size */
    font-family: Arial, sans-serif; /* font stack */
    font-weight: 700;               /* text weight */
    text-align: center;             /* horizontal text alignment */
    line-height: 1.6;               /* line spacing */
    width: 300px;                   /* content width by default */
    max-width: 100%;                /* never exceed container width */
    padding: 16px;                  /* inner spacing */
    border: 1px solid #ccc;         /* border shorthand */
    border-radius: 8px;             /* rounded corners */
}
```

## 13. The box model

Every element that participates in layout has a box. The classic box model has four conceptual areas, from inside to outside:

1. **Content** — text, image, or child content.
2. **Padding** — space between content and border.
3. **Border** — edge around padding and content.
4. **Margin** — outside spacing around the border.

Visual idea:

```text
┌──────────────────────── MARGIN ────────────────────────┐
│  ┌───────────────────── BORDER ─────────────────────┐  │
│  │  ┌────────────────── PADDING ──────────────────┐  │  │
│  │  │                                             │  │  │
│  │  │                 CONTENT                    │  │  │
│  │  │                                             │  │  │
│  │  └─────────────────────────────────────────────┘  │  │
│  └───────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────┘
```

### Content

`width` and `height` describe the content box by default when `box-sizing: content-box`.

```css
.box {
    width: 200px;
    height: 100px;
}
```

### Padding

Padding increases the space inside the border and is included in the element's background painting.

```css
.box {
    padding: 20px;
}
```

Shorthand order:

```css
padding: 10px;                 /* all four sides */
padding: 10px 20px;            /* top/bottom, left/right */
padding: 10px 20px 30px;       /* top, left/right, bottom */
padding: 10px 20px 30px 40px;  /* top, right, bottom, left */
```

The four-value order is **top, right, bottom, left** (clockwise).

### Border

```css
.box {
    border: 2px solid #333;
    border-top: 4px dashed red;
    border-radius: 8px;
}
```

A border adds to the rendered dimensions under `content-box`.

### Margin

Margin creates outside spacing:

```css
.box {
    margin: 20px;
}
```

Margin shorthand follows the same one-, two-, three-, and four-value pattern as padding. Margins can be negative; negative margins can pull boxes closer or cause overlap. Padding cannot be negative.

`margin: 0 auto;` often centers a block with a definite or constrained width in its containing block when there is available horizontal space:

```css
.container {
    width: min(900px, 100%);
    margin: 0 auto;
}
```

Margins are transparent; they do not paint the element's background.

## 14. Total width and total height

This is one of the most important calculations in CSS.

### 14.1 With `box-sizing: content-box`

This is the default if no other rule changes it:

```css
.box {
    width: 200px;
    height: 100px;
    padding: 20px;
    border: 5px solid black;
    margin: 10px;
}
```

**Rendered border-box width:**

- Content width: `200px`
- Left + right padding: `20 + 20 = 40px`
- Left + right border: `5 + 5 = 10px`

`200 + 40 + 10 = 250px`

**Rendered border-box height:**

- Content height: `100px`
- Top + bottom padding: `20 + 20 = 40px`
- Top + bottom border: `5 + 5 = 10px`

`100 + 40 + 10 = 150px`

The box's outer dimensions including margins, when margins are not collapsing and the element is in an ordinary layout where those margins contribute, are `270px` wide and `170px` tall.

Formulas:

```text
border-box width =
    width + padding-left + padding-right
          + border-left + border-right

border-box height =
    height + padding-top + padding-bottom
           + border-top + border-bottom

outer horizontal space =
    border-box width + margin-left + margin-right

outer vertical space =
    border-box height + margin-top + margin-bottom
```

### 14.2 With `box-sizing: border-box`

```css
*,
*::before,
*::after {
    box-sizing: border-box;
}
```

Now `width: 200px` means the box from the outside of the left border to the outside of the right border is 200px, including padding and borders. The content area shrinks to make room for them.

With the same 20px padding and 5px borders:

- Border-box width: `200px`
- Content width: `200 - 40 - 10 = 150px`

If `height: 100px`, content height is `100 - 40 - 10 = 50px`.

Margins remain outside the border-box and are not included in the declared width or height.

**Recommended default for many projects:**

```css
*,
*::before,
*::after {
    box-sizing: border-box;
}
```

This makes width calculations easier and prevents padding/borders from unexpectedly increasing a specified width.

## 15. Margin collapsing

**Margin collapsing** is when certain vertical margins combine into one margin instead of adding together. It mainly occurs between normal-flow block boxes in the same block formatting context. Horizontal margins do not collapse.

### 15.1 Two adjacent vertical margins

```html
<div class="first">First box</div>
<div class="second">Second box</div>
```

```css
.first {
    margin-bottom: 30px;
}

.second {
    margin-top: 20px;
}
```

For ordinary adjacent block boxes in normal flow, the gap is generally **30px**, not `30 + 20 = 50px`. The larger positive margin wins.

When both margins are positive, the collapsed margin is the larger one. When both are negative, the more negative value wins. When positive and negative margins collapse, their values are added algebraically.

### 15.2 Parent and child margins

A first/last child's vertical margin can sometimes collapse through its parent. For example, a child's `margin-top` can appear outside the parent rather than creating the separation you expected inside it.

This can happen when there is no border, padding, inline content, or other layout feature separating the parent and child margins. The exact rules depend on the formatting context and layout.

Ways to prevent or change this behavior include:

```css
.parent {
    padding-top: 1px;
}
```

or:

```css
.parent {
    border-top: 1px solid transparent;
}
```

or establishing a new block formatting context:

```css
.parent {
    display: flow-root;
}
```

`display: flow-root` is often a clean choice when you want the parent to contain its contents and avoid certain margin-collapsing/float interactions without adding visible padding or borders.

### 15.3 When margins do not collapse

Vertical margins generally do not collapse in flex or grid containers between their items. Margins also do not collapse in many other situations, including absolutely positioned elements and floats.

Do not treat margin collapsing as a universal rule for every pair of elements. It applies only to specific block-layout situations.

### 15.4 Margin collapsing is not the same as overlap

- **Collapsing:** two vertical margins combine into one resulting gap.
- **Overlap:** boxes or content physically occupy the same area, often because of negative margins, transforms, positioning, or other layout rules.

Example of deliberate overlap:

```css
.card-two {
    margin-top: -20px;
}
```

A negative margin may pull the second card upward. This is different from ordinary positive-margin collapsing.

## 16. Display and basic layout behavior

### `display: block`

A block-level box normally starts on a new line and takes the available inline width by default. Width and height can be set.

Examples include `div`, `p`, and headings in their default styles.

### `display: inline`

An inline box flows with text. `width` and `height` generally do not apply to a non-replaced inline element in the same way they do to a block box. Vertical padding and borders can paint around the line without behaving like block height.

Examples include `span` and `a` in their default styles.

### `display: inline-block`

Flows inline with surrounding content, while allowing width and height like a block-level box.

### `display: none`

Removes the element's box from layout. It is different from `visibility: hidden`, which hides the element but preserves its layout space.

### `width`, `max-width`, and `height`

```css
.content {
    width: 800px;
    max-width: 100%;
    min-height: 200px;
}
```

- `width`: preferred used width, subject to layout constraints.
- `max-width`: prevents width from exceeding a limit.
- `min-width`: sets a lower width limit.
- `height`: preferred height; content can overflow if it cannot fit.
- `min-height`: minimum height while allowing growth.

For a responsive centered container:

```css
.container {
    width: min(100% - 2rem, 900px);
    margin-inline: auto;
}
```

`margin-inline` sets logical left/right margins in a typical left-to-right layout and adapts to writing direction.

## 17. Common mistakes

1. **Forgetting the dot for a class.** `.card` selects a class; `card` selects an HTML element named `<card>`.
2. **Forgetting `#` for an ID.** `#title` selects the ID `title`.
3. **Using the wrong file path.** Confirm the `href` in `<link>` matches the actual file location and spelling.
4. **Missing a brace or semicolon.** A malformed rule can cause declarations to be ignored or parsed incorrectly.
5. **Confusing descendant and child selectors.** `.parent p` includes nested paragraphs; `.parent > p` includes only direct children.
6. **Assuming the latest rule always wins.** Specificity and other cascade rules matter.
7. **Assuming `width` includes padding by default.** It does not under `content-box`.
8. **Adding vertical margins and expecting them always to add.** They can collapse in normal block flow.
9. **Using an ID for every styled element.** Prefer reusable classes for most styling.
10. **Removing focus outlines without replacement.** Keyboard users need to see which control is focused.
11. **Using hover as the only interaction cue.** Touch and keyboard users may not be able to trigger it the same way.
12. **Using `!important` to fix every conflict.** Inspect the selector and cascade first.

## 18. Practice tasks

Use `index.html` and `style.css` to complete these without immediately looking up a solution.

### Beginner

- Change the page background and base font.
- Apply one class to three different elements and style them together.
- Give one unique heading an ID and select it with `#`.
- Make every `h2` and `h3` use the same color using a grouped selector.
- Create a link with a visible hover state and keyboard focus state.

### Selectors

- Color every paragraph inside `.article`.
- Color only direct child paragraphs of `.article`.
- Style the paragraph immediately after each `h2`.
- Highlight every second list item.
- Select email inputs using `[type="email"]`.
- Explain why `.card p` and `.card > p` can select different paragraphs.

### Box model

- Create a box with `width: 200px`, `padding: 20px`, and `border: 5px solid`.
- Calculate its border-box width under `content-box`.
- Add `box-sizing: border-box` and explain why the content width changes.
- Give two adjacent blocks `margin-bottom: 30px` and `margin-top: 20px`. Inspect their vertical gap.
- Try `margin-top: -20px` and explain why this is overlap rather than normal margin collapsing.
- Center a container with `max-width` and auto horizontal margins.

### Explain it in your own words

1. What is the difference between a class and an ID?
2. What does the space in `.parent p` mean?
3. How does `>` differ from a space?
4. What are the four areas of the box model?
5. Why does `box-sizing: border-box` make sizing easier?
6. Why can `margin-top: 20px` and `margin-bottom: 30px` create a 30px gap rather than a 50px gap?
7. What is specificity, and why is “last rule always wins” incorrect?
8. Which properties commonly inherit from a parent, and which do not?

## 19. Quick revision

```css
/* Ways to add CSS */
<p style="color: red;">Inline</p>
<style>p { color: blue; }</style>
<link rel="stylesheet" href="style.css">

/* Basic selectors */
* { box-sizing: border-box; }
p { color: black; }
.note { color: blue; }
#title { color: green; }
p.note { font-weight: bold; }
h1, h2 { font-family: Arial, sans-serif; }

/* Relationships */
.parent p { }       /* descendant */
.parent > p { }     /* direct child */
h2 + p { }          /* next sibling */
h2 ~ p { }          /* later siblings */

/* States and generated parts */
a:hover { }
a:focus-visible { }
li:nth-child(2) { }
.note::before { content: "Note: "; }

/* Box model */
.box {
    width: 200px;
    padding: 20px;
    border: 5px solid;
    margin: 10px;
    box-sizing: border-box;
}
```

**Learning rule:** don't only memorize selector symbols. Write small HTML structures, predict which elements match, then test the prediction in the browser's developer tools.
