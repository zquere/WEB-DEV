# HTML --- From Zero to Writing Real Web Pages

> HTML is the structure of the web.
>
> CSS will make that structure look good. JavaScript will make it
> behave. But HTML comes first because a browser needs something
> meaningful to work with.

------------------------------------------------------------------------

## How to Use This Chapter

Don't try to memorize every HTML tag.

The useful question is:

> **What does this content mean?**

HTML is much easier when you choose elements by meaning rather than by
appearance.

This chapter goes from the first HTML document all the way through
semantic HTML, forms, tables, accessibility, debugging, and a complete
mini-project.

------------------------------------------------------------------------

# Table of Contents

1.  What HTML Actually Is
2.  Document Structure
3.  Elements, Tags, and Attributes
4.  Nesting
5.  Comments
6.  The Head
7.  The Body
8.  Text
9.  Headings
10. Paragraphs
11. Emphasis and Importance
12. Quotes
13. Code
14. Lists
15. Links
16. Absolute URLs
17. Relative URLs
18. Anchor Links
19. Download Links
20. Images
21. `alt`
22. Audio
23. Video
24. iframe
25. Semantic HTML
26. header
27. nav
28. main
29. section
30. article
31. aside
32. footer
33. Forms
34. Form Structure
35. Inputs
36. Labels
37. Buttons
38. select
39. textarea
40. Checkboxes
41. Radio Buttons
42. Validation
43. Tables
44. Rows and Columns
45. Table Headers
46. Captions
47. Accessibility
48. Keyboard Navigation
49. ARIA Basics
50. Complete Example
51. Common Mistakes
52. DOM and Browser Thinking
53. Debugging
54. Practical Exercises
55. Final Checklist

------------------------------------------------------------------------

# 1. What HTML Actually Is

HTML stands for **HyperText Markup Language**.

HTML is not a programming language.

It is a markup language used to describe the **structure and meaning of
content** in a web document.

For example:

``` html
<h1>My Portfolio</h1>
<p>I am learning web development.</p>
```

You are telling the browser:

-   this is a main heading
-   this is a paragraph

You are not telling it to perform a calculation or make a decision.

That is where programming languages such as JavaScript come in.

A useful mental model is:

``` text
HTML
  ↓
Structure and meaning

CSS
  ↓
Appearance and layout

JavaScript
  ↓
Behavior and interaction
```

Imagine a house:

``` text
HTML       → rooms, walls, doors
CSS        → paint, furniture, decoration
JavaScript → switches, automation, behavior
```

It is not a perfect analogy, but it is useful.

------------------------------------------------------------------------

# 2. HTML Document Structure

A basic HTML document looks like this:

``` html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title>My First Page</title>
</head>

<body>
    <h1>Hello World</h1>
    <p>This is my first webpage.</p>
</body>

</html>
```

Think of the document as:

``` text
HTML document
│
├── DOCTYPE
│
└── html
    │
    ├── head
    │   ├── metadata
    │   ├── title
    │   └── resource links
    │
    └── body
        ├── headings
        ├── paragraphs
        ├── links
        ├── images
        ├── forms
        └── other content
```

## `<!DOCTYPE html>`

This tells the browser that the document should be interpreted as modern
HTML.

It is not an HTML element.

------------------------------------------------------------------------

# 3. Elements, Tags, and Attributes

These terms sound similar, but they mean different things.

## Tags

A tag is markup surrounded by angle brackets:

``` html
<p>
```

and:

``` html
</p>
```

The first is an opening tag.

The second is a closing tag.

## Element

The whole thing is an element:

``` html
<p>Hello</p>
```

Break it down:

``` text
<p>       opening tag
Hello     content
</p>      closing tag
```

## Attribute

An attribute gives additional information about an element.

``` html
<a href="https://example.com">Visit Example</a>
```

Here:

``` html
href="https://example.com"
```

is an attribute.

Another example:

``` html
<img src="cat.jpg" alt="A sleeping cat">
```

`src` tells the browser where the image is.

`alt` provides a text alternative.

A useful mental model:

``` text
ELEMENT
│
├── TAGS
├── CONTENT
└── ATTRIBUTES
```

Not every element has visible content, and some elements are void
elements that do not have closing tags.

For example:

``` html
<img src="cat.jpg" alt="Cat">
```

------------------------------------------------------------------------

# 4. Nesting

HTML elements can contain other elements.

This is called nesting.

``` html
<p>
    I am learning
    <strong>HTML</strong>
    today.
</p>
```

Here `<strong>` is inside `<p>`.

Think of it as boxes:

``` text
paragraph
┌───────────────────────────┐
│ I am learning             │
│     ┌──────────┐          │
│     │ HTML     │          │
│     └──────────┘          │
│ today.                    │
└───────────────────────────┘
```

Correct nesting:

``` html
<div>
    <p>
        <strong>Hello</strong>
    </p>
</div>
```

Incorrect nesting:

``` html
<div>
    <p>
        <strong>Hello
    </div>
    </strong>
</p>
```

A useful rule is:

> Close the innermost element first.

Opening:

``` text
div
  p
    strong
```

Closing:

``` text
strong
  p
    div
```

This is similar to a stack.

------------------------------------------------------------------------

# 5. Comments

HTML comments look like this:

``` html
<!-- This is a comment -->
```

The browser does not display them as normal page content.

Useful:

``` html
<!-- Main navigation -->
<nav>
    ...
</nav>
```

Not very useful:

``` html
<!-- Open paragraph -->
<p>
    <!-- Text -->
    Hello
    <!-- Close paragraph -->
</p>
```

Don't use comments for secrets.

This is not secure:

``` html
<!-- password = myPassword123 -->
```

Comments are sent as part of the HTML source.

------------------------------------------------------------------------

# 6. The Head

The `<head>` contains information about the document.

Example:

``` html
<head>
    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <title>My Website</title>

    <meta
        name="description"
        content="A website for learning HTML."
    >

    <link rel="stylesheet" href="style.css">
</head>
```

## `title`

``` html
<title>My Website</title>
```

This normally appears in the browser tab.

It also matters for bookmarks and search engines.

## Character encoding

``` html
<meta charset="UTF-8">
```

UTF-8 supports a huge range of characters:

``` text
Hello
नमस्ते
こんにちは
你好
```

## Viewport

``` html
<meta
    name="viewport"
    content="width=device-width, initial-scale=1.0"
>
```

This helps the page behave correctly on mobile devices.

## CSS

``` html
<link rel="stylesheet" href="style.css">
```

This tells the browser to load a stylesheet.

------------------------------------------------------------------------

# 7. The Body

The `<body>` contains the document's visible and interactive content.

``` html
<body>

    <h1>My Website</h1>

    <p>Welcome.</p>

</body>
```

The body can contain:

-   headings
-   paragraphs
-   links
-   images
-   lists
-   forms
-   tables
-   audio
-   video
-   semantic sections

Visible content does not belong in `<head>`.

Wrong:

``` html
<head>
    <h1>My Website</h1>
</head>
```

Correct:

``` html
<body>
    <h1>My Website</h1>
</body>
```

------------------------------------------------------------------------

# 8. Text

HTML has different elements for different kinds of text.

``` html
<h1>Main heading</h1>

<p>Paragraph text.</p>

<strong>Important text</strong>

<em>Emphasized text</em>

<blockquote>A quotation.</blockquote>

<code>const x = 10;</code>
```

The important point is that HTML describes meaning.

Don't choose elements only because their default browser appearance
looks convenient.

CSS is responsible for visual styling.

------------------------------------------------------------------------

# 9. Headings

HTML provides six heading levels:

``` html
<h1>Heading 1</h1>
<h2>Heading 2</h2>
<h3>Heading 3</h3>
<h4>Heading 4</h4>
<h5>Heading 5</h5>
<h6>Heading 6</h6>
```

Think about headings as a document hierarchy.

``` html
<h1>Web Development</h1>

<h2>HTML</h2>
<h3>Elements</h3>
<h3>Attributes</h3>

<h2>CSS</h2>
<h3>Selectors</h3>
<h3>Box Model</h3>
```

This creates:

``` text
Web Development
│
├── HTML
│   ├── Elements
│   └── Attributes
│
└── CSS
    ├── Selectors
    └── Box Model
```

Don't use `<h5>` simply because you want small text.

Choose the heading level according to the document hierarchy.

Use CSS later if you want to change its size.

------------------------------------------------------------------------

# 10. Paragraphs

Use `<p>` for paragraphs.

``` html
<p>
    HTML gives a webpage structure and meaning.
</p>
```

Separate paragraphs should normally be separate elements:

``` html
<p>HTML describes structure.</p>

<p>CSS controls presentation.</p>

<p>JavaScript adds behavior.</p>
```

Don't use many `<br>` elements to create paragraph spacing.

Bad:

``` html
HTML is structure.<br>
<br>
CSS is presentation.<br>
<br>
JavaScript is behavior.
```

Better:

``` html
<p>HTML is structure.</p>
<p>CSS is presentation.</p>
<p>JavaScript is behavior.</p>
```

------------------------------------------------------------------------

# 11. Emphasis and Importance

Two important elements are:

``` html
<strong>Important</strong>
```

and:

``` html
<em>Emphasized</em>
```

They communicate meaning.

Example:

``` html
<p>
    You <strong>must</strong> save your work.
</p>
```

``` html
<p>
    I meant <em>this</em> file.
</p>
```

Browsers usually render these as bold and italic, but their semantic
meaning is more important than their default appearance.

------------------------------------------------------------------------

# 12. Quotes

## Inline quotation

Use `<q>`:

``` html
<p>
    My teacher said, <q>Understand the basics first.</q>
</p>
```

## Long quotation

Use `<blockquote>`:

``` html
<blockquote>
    A longer quotation can be represented here.
</blockquote>
```

You can identify the source URL with `cite`:

``` html
<blockquote cite="https://example.com/article">
    A quoted passage.
</blockquote>
```

For the title of a work:

``` html
<p>
    I am reading <cite>The Pragmatic Programmer</cite>.
</p>
```

------------------------------------------------------------------------

# 13. Code

HTML provides useful elements for technical content.

## Inline code

``` html
<p>
    Use <code>console.log()</code> in JavaScript.
</p>
```

## Code block

Use `<pre>` with `<code>`:

``` html
<pre><code>int main() {
    cout << "Hello";
    return 0;
}</code></pre>
```

`<pre>` preserves whitespace and line breaks.

## Keyboard input

``` html
<p>
    Press <kbd>Ctrl</kbd> + <kbd>S</kbd> to save.
</p>
```

## Program output

``` html
<p>
    The program returned:
    <samp>Hello World</samp>
</p>
```

These are especially useful when writing programming documentation.

------------------------------------------------------------------------

# 14. Lists

HTML has three common list types:

-   unordered lists
-   ordered lists
-   description lists

## Unordered list

``` html
<ul>
    <li>HTML</li>
    <li>CSS</li>
    <li>JavaScript</li>
</ul>
```

Use this when the order doesn't matter.

## Ordered list

``` html
<ol>
    <li>Open the editor.</li>
    <li>Create an HTML file.</li>
    <li>Open it in a browser.</li>
</ol>
```

Use this when the order matters.

## Description list

``` html
<dl>
    <dt>HTML</dt>
    <dd>The structure of a webpage.</dd>

    <dt>CSS</dt>
    <dd>The presentation of a webpage.</dd>
</dl>
```

Think:

``` text
TERM
 ↓
DESCRIPTION
```

------------------------------------------------------------------------

# 15. Links

The main link element is `<a>`.

``` html
<a href="https://example.com">Visit Example</a>
```

`href` tells the browser where the link goes.

A link can point to:

-   another website
-   another page in the same project
-   a section on the current page
-   a file
-   an email address
-   other supported URL schemes

------------------------------------------------------------------------

# 16. Absolute URLs

An absolute URL contains the complete address.

``` html
<a href="https://example.com/about.html">
    About Example
</a>
```

Another example:

``` html
<a href="https://developer.mozilla.org/">
    MDN
</a>
```

Absolute URLs are common when linking to another website.

------------------------------------------------------------------------

# 17. Relative URLs

A relative URL is interpreted relative to the current document.

Suppose:

``` text
website/
├── index.html
├── about.html
└── pages/
    └── contact.html
```

From `index.html`:

``` html
<a href="about.html">About</a>
```

points to:

``` text
website/about.html
```

From `pages/contact.html`:

``` html
<a href="../index.html">Home</a>
```

`..` means:

> parent directory

From `index.html`:

``` html
<a href="pages/contact.html">Contact</a>
```

A good debugging question is:

> Relative to which HTML file is this path being resolved?

------------------------------------------------------------------------

# 18. Anchor Links

You can link to an element using its `id`.

``` html
<h2 id="contact">Contact</h2>
```

Then:

``` html
<a href="#contact">Go to Contact</a>
```

The `#contact` refers to the element whose ID is `contact`.

You can also target an ID on another page:

``` html
<a href="about.html#team">
    Meet the team
</a>
```

------------------------------------------------------------------------

# 19. Download Links

The `download` attribute can indicate that a linked resource is intended
to be downloaded.

``` html
<a href="files/resume.pdf" download>
    Download my resume
</a>
```

You can suggest a filename:

``` html
<a
    href="files/resume.pdf"
    download="my-resume.pdf"
>
    Download Resume
</a>
```

The browser and server can influence the final behavior, so `download`
is a hint rather than an absolute guarantee for every URL.

------------------------------------------------------------------------

# 20. Images

Use `<img>` to embed an image.

``` html
<img src="cat.jpg" alt="A sleeping cat">
```

Important attributes:

``` text
src → image location
alt → text alternative
```

You can also provide dimensions:

``` html
<img
    src="cat.jpg"
    alt="A sleeping cat"
    width="800"
    height="600"
>
```

Providing dimensions can help the browser reserve space before the image
finishes loading.

------------------------------------------------------------------------

# 21. The `alt` Attribute

`alt` is a text alternative for an image.

Example:

``` html
<img
    src="mountain.jpg"
    alt="Snow-covered mountain above a lake at sunrise"
>
```

A screen reader can communicate the alternative text.

If an image is purely decorative:

``` html
<img src="decorative-line.svg" alt="">
```

Don't write:

``` html
alt="image"
```

That gives almost no useful information.

Also don't stuff keywords into `alt`.

Bad:

``` html
alt="mountain travel nature hiking best mountain"
```

Better:

``` html
alt="Snow-covered mountain beside a lake"
```

A good question is:

> If the image disappeared, what information would the user need
> instead?

------------------------------------------------------------------------

# 22. Audio

Use `<audio>` for audio content.

``` html
<audio controls>
    <source src="song.mp3" type="audio/mpeg">
    Your browser does not support the audio element.
</audio>
```

Multiple formats can be provided:

``` html
<audio controls>
    <source src="song.mp3" type="audio/mpeg">
    <source src="song.ogg" type="audio/ogg">

    Your browser does not support this audio.
</audio>
```

`controls` asks the browser to provide playback controls.

------------------------------------------------------------------------

# 23. Video

Use `<video>` for video.

``` html
<video controls width="800">
    <source src="movie.mp4" type="video/mp4">
    Your browser does not support the video element.
</video>
```

Common attributes include:

``` text
controls
autoplay
muted
loop
poster
width
height
```

Example:

``` html
<video
    controls
    muted
    loop
    poster="thumbnail.jpg"
>
    <source src="intro.mp4" type="video/mp4">
</video>
```

Be careful with autoplay.

Unexpected audio is disruptive, and browsers commonly restrict autoplay
with sound.

------------------------------------------------------------------------

# 24. iframe

An `<iframe>` embeds another browsing context.

``` html
<iframe
    src="https://example.com"
    title="Example website"
    width="800"
    height="500"
></iframe>
```

Common uses include:

-   maps
-   videos
-   documentation
-   external tools
-   embedded applications

An iframe is not simply copied HTML.

It creates a separate browsing context inside your page.

For untrusted content, iframe security features such as `sandbox` can be
important.

------------------------------------------------------------------------

# 25. Semantic HTML

Semantic HTML means choosing elements according to their meaning.

Compare:

``` html
<div class="top">...</div>
<div class="links">...</div>
<div class="content">...</div>
<div class="bottom">...</div>
```

with:

``` html
<header>...</header>
<nav>...</nav>
<main>...</main>
<footer>...</footer>
```

The second version communicates much more.

HTML is consumed by more than the visual browser window.

It is also used by:

-   screen readers
-   search engines
-   accessibility tools
-   browser APIs
-   developers
-   automated systems

Semantic HTML gives those systems more useful information.

------------------------------------------------------------------------

# 26. `header`

`<header>` represents introductory content for a page or section.

``` html
<header>
    <h1>My Blog</h1>
    <p>Notes about programming.</p>
</header>
```

A header can also belong to an article:

``` html
<article>

    <header>
        <h2>Learning HTML</h2>
        <p>Published October 4, 2026</p>
    </header>

    <p>Article content...</p>

</article>
```

`header` does not necessarily mean "the very top of the entire webpage."

------------------------------------------------------------------------

# 27. `nav`

`<nav>` represents a major navigation section.

``` html
<nav>
    <a href="/">Home</a>
    <a href="/about.html">About</a>
    <a href="/projects.html">Projects</a>
    <a href="/contact.html">Contact</a>
</nav>
```

Not every group of links needs to be a `<nav>`.

Use it for important navigation.

------------------------------------------------------------------------

# 28. `main`

`<main>` contains the primary content of the page.

``` html
<body>

    <header>
        <h1>My Website</h1>
    </header>

    <nav>
        ...
    </nav>

    <main>
        <h2>Welcome</h2>
        <p>This is the main content.</p>
    </main>

    <footer>
        ...
    </footer>

</body>
```

Repeated site-wide content such as navigation normally doesn't belong
inside `<main>`.

------------------------------------------------------------------------

# 29. `section`

A `<section>` represents a thematic grouping.

``` html
<section>
    <h2>My Skills</h2>

    <p>I am currently learning HTML and CSS.</p>
</section>
```

A common pattern:

``` html
<main>

    <section>
        <h2>About Me</h2>
        <p>...</p>
    </section>

    <section>
        <h2>Projects</h2>
        <p>...</p>
    </section>

</main>
```

Don't replace every `<div>` with `<section>`.

If a container has no meaningful semantic purpose, a `<div>` can be
exactly right.

------------------------------------------------------------------------

# 30. `article`

`<article>` represents a self-contained piece of content.

Examples:

-   blog post
-   news story
-   forum post
-   product review
-   independent comment

Example:

``` html
<article>

    <header>
        <h2>Why I Started Learning Web Development</h2>
        <p>Published October 4, 2026</p>
    </header>

    <p>
        I wanted to understand how websites actually work.
    </p>

</article>
```

A useful test:

> Could this content make sense if it were separated from the
> surrounding page?

If yes, `<article>` may be appropriate.

------------------------------------------------------------------------

# 31. `aside`

`<aside>` represents related or secondary content.

Examples:

-   related articles
-   author information
-   tips
-   sidebars
-   related resources

``` html
<aside>
    <h2>Related Topics</h2>

    <ul>
        <li><a href="/css.html">CSS</a></li>
        <li><a href="/javascript.html">JavaScript</a></li>
    </ul>
</aside>
```

------------------------------------------------------------------------

# 32. `footer`

`<footer>` represents footer information for a page or section.

``` html
<footer>
    <p>&copy; 2026 My Website</p>
    <a href="/privacy.html">Privacy</a>
</footer>
```

A footer can belong to the entire page or to an individual article.

------------------------------------------------------------------------

# 33. Forms

Forms collect user input.

Common examples:

-   login
-   registration
-   search
-   contact
-   checkout
-   surveys
-   settings

A basic form:

``` html
<form>
    <label for="name">Name</label>

    <input
        id="name"
        name="name"
        type="text"
    >

    <button type="submit">Submit</button>
</form>
```

Think:

``` text
form
│
├── label
├── input
└── button
```

------------------------------------------------------------------------

# 34. Form Structure

A realistic form:

``` html
<form action="/register" method="post">

    <div>
        <label for="username">Username</label>

        <input
            id="username"
            name="username"
            type="text"
        >
    </div>

    <div>
        <label for="email">Email</label>

        <input
            id="email"
            name="email"
            type="email"
        >
    </div>

    <button type="submit">
        Create Account
    </button>

</form>
```

Important attributes:

``` text
action → destination for the submission
method → HTTP method used by the form
name   → name of submitted field
id     → identifies the element in the document
```

The `name` attribute is especially important for form submission.

------------------------------------------------------------------------

# 35. Inputs

`<input>` supports many types.

``` html
<input type="text">
<input type="email">
<input type="password">
<input type="number">
<input type="date">
<input type="file">
<input type="search">
<input type="url">
<input type="tel">
```

There are many others.

## Hidden input

``` html
<input
    type="hidden"
    name="userId"
    value="123"
>
```

Hidden does not mean secure.

The user can inspect and modify client-side data.

Never put secrets in hidden inputs.

------------------------------------------------------------------------

# 36. Labels

A label tells the user what a form control represents.

Good:

``` html
<label for="email">Email address</label>

<input
    id="email"
    name="email"
    type="email"
>
```

The connection is:

``` text
label for="email"
          ↓
input id="email"
```

You can also wrap the input:

``` html
<label>
    Email address

    <input
        type="email"
        name="email"
    >
</label>
```

Labels improve usability and accessibility.

------------------------------------------------------------------------

# 37. Buttons

Use `<button>` for buttons.

``` html
<button type="submit">
    Create Account
</button>
```

Types include:

``` html
<button type="submit">Submit</button>
<button type="reset">Reset</button>
<button type="button">Normal button</button>
```

Inside a form, a button without an explicit `type` can act as a submit
button.

So if it should not submit the form:

``` html
<button type="button">
    Open Menu
</button>
```

A real button already has useful keyboard and accessibility behavior.

Don't turn a `<div>` into a button unless you have a very specific
reason.

------------------------------------------------------------------------

# 38. `select`

A dropdown:

``` html
<label for="country">Country</label>

<select id="country" name="country">
    <option value="in">India</option>
    <option value="jp">Japan</option>
    <option value="ca">Canada</option>
</select>
```

The user sees:

``` text
India
```

but the submitted value can be:

``` text
in
```

You can select a default:

``` html
<option value="in" selected>India</option>
```

You can group options:

``` html
<select name="language">

    <optgroup label="Programming">
        <option value="cpp">C++</option>
        <option value="js">JavaScript</option>
    </optgroup>

    <optgroup label="Markup">
        <option value="html">HTML</option>
    </optgroup>

</select>
```

------------------------------------------------------------------------

# 39. `textarea`

Use `<textarea>` for multi-line input.

``` html
<label for="message">Message</label>

<textarea
    id="message"
    name="message"
    rows="6"
    cols="40"
></textarea>
```

Initial text goes between the tags:

``` html
<textarea name="message">Hello</textarea>
```

Not:

``` html
<textarea value="Hello"></textarea>
```

CSS will later give you better control over visual sizing.

------------------------------------------------------------------------

# 40. Checkboxes

Checkboxes represent independent choices.

``` html
<label>
    <input
        type="checkbox"
        name="terms"
        value="accepted"
    >
    I agree to the terms.
</label>
```

Multiple checkboxes can be selected:

``` html
<fieldset>

    <legend>Interests</legend>

    <label>
        <input
            type="checkbox"
            name="interest"
            value="coding"
        >
        Coding
    </label>

    <label>
        <input
            type="checkbox"
            name="interest"
            value="music"
        >
        Music
    </label>

    <label>
        <input
            type="checkbox"
            name="interest"
            value="sports"
        >
        Sports
    </label>

</fieldset>
```

------------------------------------------------------------------------

# 41. Radio Buttons

Radio buttons are for choosing one option from a group.

``` html
<fieldset>

    <legend>Choose a plan</legend>

    <label>
        <input
            type="radio"
            name="plan"
            value="basic"
        >
        Basic
    </label>

    <label>
        <input
            type="radio"
            name="plan"
            value="pro"
        >
        Pro
    </label>

</fieldset>
```

The important part is that they share:

``` text
name="plan"
```

If radio buttons have different names, the browser treats them as
separate groups.

------------------------------------------------------------------------

# 42. Form Validation

HTML can provide basic client-side validation without JavaScript.

## Required

``` html
<input
    type="text"
    name="username"
    required
>
```

## Minimum length

``` html
<input
    type="text"
    name="username"
    minlength="3"
>
```

## Maximum length

``` html
<input
    type="text"
    name="username"
    maxlength="20"
>
```

## Number range

``` html
<input
    type="number"
    name="age"
    min="18"
    max="100"
>
```

## Pattern

``` html
<input
    type="text"
    name="code"
    pattern="[A-Z]{3}[0-9]{3}"
>
```

This accepts a pattern such as:

``` text
ABC123
```

## Email

``` html
<input
    type="email"
    name="email"
    required
>
```

## Placeholder

``` html
<input
    type="email"
    placeholder="you@example.com"
>
```

Remember:

**A placeholder is not a label.**

Use both when appropriate:

``` html
<label for="email">Email address</label>

<input
    id="email"
    name="email"
    type="email"
    placeholder="you@example.com"
>
```

### Client-side validation is not security

A user controls their browser.

Important data must be validated on the server too.

Think:

``` text
HTML validation
      ↓
Better user experience

Server validation
      ↓
Application security and correctness
```

------------------------------------------------------------------------

# 43. Tables

Tables are for **tabular data**.

Good examples:

-   marks
-   prices
-   schedules
-   statistics
-   comparison data

Bad use:

-   building the entire website layout

Basic table:

``` html
<table>

    <tr>
        <th>Name</th>
        <th>Score</th>
    </tr>

    <tr>
        <td>Aman</td>
        <td>92</td>
    </tr>

    <tr>
        <td>Riya</td>
        <td>88</td>
    </tr>

</table>
```

------------------------------------------------------------------------

# 44. Rows and Columns

The basic table structure is:

``` text
table
└── tr
    ├── th
    └── td
```

`tr` = table row

`th` = table header cell

`td` = table data cell

For a better structured table:

``` html
<table>

    <thead>
        <tr>
            <th>Technology</th>
            <th>Purpose</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>HTML</td>
            <td>Structure</td>
        </tr>

        <tr>
            <td>CSS</td>
            <td>Presentation</td>
        </tr>
    </tbody>

</table>
```

------------------------------------------------------------------------

# 45. Table Headers

Use `<th>` for headers.

For column headers:

``` html
<th scope="col">Student</th>
<th scope="col">Math</th>
<th scope="col">Physics</th>
```

For row headers:

``` html
<tr>
    <th scope="row">Aman</th>
    <td>95</td>
    <td>91</td>
</tr>
```

`scope` helps assistive technologies understand table relationships.

For complicated tables, additional techniques may be necessary.

------------------------------------------------------------------------

# 46. Captions

Use `<caption>` to describe what the table represents.

``` html
<table>

    <caption>Class 12 Exam Results</caption>

    <thead>
        <tr>
            <th scope="col">Student</th>
            <th scope="col">Score</th>
        </tr>
    </thead>

    <tbody>
        <tr>
            <td>Aman</td>
            <td>95</td>
        </tr>
    </tbody>

</table>
```

A caption is particularly useful when the table would otherwise be
difficult to understand out of context.

------------------------------------------------------------------------

# 47. Accessibility

Accessibility means making a website usable by people with different
abilities and ways of interacting with computers.

Some users may:

-   use screen readers
-   use only a keyboard
-   have low vision
-   have motor difficulties
-   have hearing difficulties
-   need clearer structure

Accessibility is not something you should bolt onto a website at the
very end.

Good HTML gives you a strong foundation.

------------------------------------------------------------------------

# 48. Semantic HTML and Accessibility

Compare:

``` html
<div onclick="saveData()">Save</div>
```

with:

``` html
<button type="button">Save</button>
```

The button is much better.

A real button already has:

-   semantic meaning
-   focus behavior
-   keyboard behavior
-   browser behavior
-   accessibility information

Likewise:

``` html
<div class="navigation">
```

communicates less than:

``` html
<nav>
```

Semantic HTML reduces unnecessary work.

------------------------------------------------------------------------

# 49. Keyboard Navigation

Try using your webpage without a mouse.

Common keys:

``` text
Tab        → move forward
Shift+Tab  → move backward
Enter      → activate many controls
Space      → activate appropriate controls
Arrow keys → interact with certain controls
Esc        → commonly closes dialogs/menus
```

Native controls already support many of these behaviors.

This is another reason to prefer:

``` html
<button>
```

over:

``` html
<div>
```

Be careful with `tabindex`.

Avoid creating strange manual focus orders with large positive values
such as:

``` html
tabindex="10"
```

In most cases, native focus order is better.

------------------------------------------------------------------------

# 50. ARIA Basics

ARIA stands for:

**Accessible Rich Internet Applications**

ARIA provides additional accessibility information through attributes
such as:

``` text
aria-label
aria-labelledby
aria-describedby
aria-expanded
aria-hidden
aria-live
role
```

Example:

``` html
<button
    type="button"
    aria-expanded="false"
>
    Menu
</button>
```

This can communicate the state of an associated expandable interface.

## The most useful ARIA rule

> Prefer native HTML when native HTML already does the job.

Don't build this:

``` html
<div role="button" tabindex="0">
    Save
</div>
```

when you can write:

``` html
<button type="button">
    Save
</button>
```

ARIA is useful, but incorrect ARIA can make accessibility worse.

------------------------------------------------------------------------

# 51. `aria-label`

Sometimes a control needs an accessible name that is not obvious from
its visible content.

``` html
<button
    type="button"
    aria-label="Close dialog"
>
    X
</button>
```

The visible symbol is `X`.

The accessible name explains what the control does.

Don't add `aria-label` everywhere.

If a visible label already gives the control a clear name, that is
usually preferable.

------------------------------------------------------------------------

# 52. `aria-labelledby`

This connects an element to another element that provides its accessible
name.

``` html
<h2 id="dialog-title">Delete account</h2>

<div
    role="dialog"
    aria-labelledby="dialog-title"
>
    ...
</div>
```

The dialog is associated with the heading.

------------------------------------------------------------------------

# 53. `aria-describedby`

This connects an element to additional descriptive text.

``` html
<label for="password">Password</label>

<input
    id="password"
    name="password"
    type="password"
    aria-describedby="password-help"
>

<p id="password-help">
    Your password must contain at least 8 characters.
</p>
```

The help text is now associated with the input.

------------------------------------------------------------------------

# 54. `aria-hidden`

This can remove content from the accessibility tree.

For example, a decorative icon:

``` html
<span aria-hidden="true">★</span>
```

Be careful.

Do not hide meaningful information from assistive technologies.

------------------------------------------------------------------------

# 55. Complete Example

Here is a small but realistic HTML page combining many concepts:

``` html
<!DOCTYPE html>
<html lang="en">

<head>

    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <meta
        name="description"
        content="A beginner-friendly HTML learning page."
    >

    <title>My HTML Learning Page</title>

</head>

<body>

    <header>

        <h1>My HTML Learning Journey</h1>

        <p>
            Learning the fundamentals of web development one step at a time.
        </p>

    </header>

    <nav aria-label="Main navigation">

        <a href="#about">About</a>
        <a href="#skills">Skills</a>
        <a href="#contact">Contact</a>

    </nav>

    <main>

        <section id="about">

            <h2>About Me</h2>

            <p>
                I am learning how websites work, starting with HTML.
            </p>

            <p>
                My goal is to understand the fundamentals instead of
                memorizing random tags.
            </p>

        </section>

        <section id="skills">

            <h2>What I Am Learning</h2>

            <ul>
                <li>HTML</li>
                <li>CSS</li>
                <li>JavaScript</li>
            </ul>

        </section>

        <article>

            <header>
                <h2>Why HTML Matters</h2>
            </header>

            <p>
                HTML gives a webpage structure and meaning.
            </p>

            <blockquote>
                Good HTML is more than making text appear on a screen.
            </blockquote>

        </article>

        <section id="contact">

            <h2>Contact</h2>

            <form action="/contact" method="post">

                <div>
                    <label for="name">Name</label>

                    <input
                        id="name"
                        name="name"
                        type="text"
                        required
                    >
                </div>

                <div>
                    <label for="email">Email</label>

                    <input
                        id="email"
                        name="email"
                        type="email"
                        required
                    >
                </div>

                <div>
                    <label for="message">Message</label>

                    <textarea
                        id="message"
                        name="message"
                        rows="6"
                        required
                    ></textarea>
                </div>

                <button type="submit">
                    Send Message
                </button>

            </form>

        </section>

    </main>

    <footer>

        <p>&copy; 2026 My Website</p>

    </footer>

</body>
</html>
```

Don't just copy this.

Try explaining why each element exists.

If you can't explain a tag, that is exactly the part you need to
revisit.

------------------------------------------------------------------------

# 56. Common HTML Mistakes

## 1. Forgetting to close elements

``` html
<p>Hello
```

Browsers are forgiving, but don't rely on that.

Write:

``` html
<p>Hello</p>
```

## 2. Incorrect nesting

Bad:

``` html
<p>
    <strong>Hello
</p>
</strong>
```

Good:

``` html
<p>
    <strong>Hello</strong>
</p>
```

## 3. Choosing headings by size

Don't think:

> I want small text, so I'll use h5.

Choose the correct document level and style it later with CSS.

## 4. Using `<br>` for spacing

Bad:

``` html
<p>Hello</p>
<br>
<br>
<br>
<p>World</p>
```

CSS should control layout and spacing.

## 5. Missing `alt`

Bad:

``` html
<img src="profile.jpg">
```

Better:

``` html
<img src="profile.jpg" alt="Portrait of the author">
```

For decorative images:

``` html
<img src="decoration.svg" alt="">
```

## 6. Placeholder instead of label

Bad:

``` html
<input type="email" placeholder="Email">
```

Better:

``` html
<label for="email">Email address</label>

<input
    id="email"
    name="email"
    type="email"
    placeholder="you@example.com"
>
```

## 7. Divs everywhere

Don't make everything:

``` html
<div>
```

Use semantic elements when their meaning fits.

## 8. Tables for layout

Tables are for tabular data, not page layout.

## 9. Assuming hidden means secure

``` html
<input type="hidden" value="secret">
```

is not a security mechanism.

## 10. Assuming browser validation is security

Client-side validation can be bypassed.

Important data must be validated on the server.

------------------------------------------------------------------------

# 57. The Browser and the DOM

The browser doesn't simply display the HTML file line by line.

It parses the document and builds a structure called the **DOM**.

DOM means:

**Document Object Model**

Given:

``` html
<body>

    <h1>Hello</h1>

    <p>
        Welcome to my page.
    </p>

</body>
```

the browser creates a tree-like structure:

``` text
Document
└── html
    └── body
        ├── h1
        │   └── "Hello"
        │
        └── p
            └── "Welcome to my page."
```

JavaScript can interact with that structure:

``` javascript
document.querySelector("h1");
```

This is why HTML structure matters.

You are building a document tree, not just writing text.

------------------------------------------------------------------------

# 58. `div` and `span`

These are generic containers.

## `div`

``` html
<div>
    <p>Hello</p>
</div>
```

Use `<div>` when you need a generic container and no semantic element
fits.

## `span`

``` html
<p>
    This is
    <span>some text</span>.
</p>
```

`span` is useful for small inline pieces of content.

Later, CSS and JavaScript will often interact with these containers.

But don't use them to replace semantic elements.

------------------------------------------------------------------------

# 59. Global Attributes

Some attributes can be used on many HTML elements.

## `id`

``` html
<h2 id="about">About</h2>
```

Useful for:

-   anchor links
-   CSS
-   JavaScript
-   accessibility relationships

IDs should be unique within a document.

Bad:

``` html
<p id="text">One</p>
<p id="text">Two</p>
```

## `class`

``` html
<p class="highlight">Important text.</p>
```

A class can be reused:

``` html
<p class="highlight">One</p>
<p class="highlight">Two</p>
```

## `title`

``` html
<button title="Save your work">
    Save
</button>
```

This can provide advisory information, but it should not replace proper
visible labels or accessibility.

## `lang`

``` html
<html lang="en">
```

You can indicate a language change:

``` html
<p>
    Hello.
    <span lang="fr">Bonjour</span>.
</p>
```

------------------------------------------------------------------------

# 60. Special Characters

Some characters have special meaning in HTML.

For example:

``` html
&lt;
```

represents:

``` text
<
```

``` html
&gt;
```

represents:

``` text
>
```

``` html
&amp;
```

represents:

``` text
&
```

You may also see:

``` html
&nbsp;
```

for a non-breaking space.

Don't use `&nbsp;` as your main layout tool.

CSS is the right tool for layout.

------------------------------------------------------------------------

# 61. Boolean Attributes

Some HTML attributes are boolean.

Examples:

``` text
required
disabled
checked
selected
multiple
autofocus
controls
muted
loop
```

Example:

``` html
<input type="checkbox" checked>
```

The presence of the attribute is what matters.

Don't assume:

``` html
checked="false"
```

means unchecked.

For boolean attributes, presence generally means enabled.

------------------------------------------------------------------------

# 62. Forms and HTTP

This is where your previous Web Fundamentals knowledge connects directly
to HTML.

Suppose you have:

``` html
<form action="/login" method="post">

    <input
        name="username"
        type="text"
    >

    <input
        name="password"
        type="password"
    >

    <button type="submit">
        Login
    </button>

</form>
```

Conceptually:

``` text
HTML form
    ↓
User enters data
    ↓
Browser creates an HTTP request
    ↓
Server receives request
    ↓
Server processes data
    ↓
Server sends response
```

The `name` attributes identify the form fields.

This is why your Web Fundamentals chapter and HTML chapter are connected
rather than separate topics.

------------------------------------------------------------------------

# 63. GET and POST in Forms

Example:

``` html
<form action="/search" method="get">
```

A search form commonly uses GET.

Conceptually, the query might become:

``` text
/search?q=html
```

POST is commonly used when sending data in the request body:

``` html
<form action="/register" method="post">
```

Don't confuse HTTP methods with security.

This is wrong thinking:

``` text
GET = insecure
POST = secure
```

The encryption of an HTTP connection comes from HTTPS/TLS.

------------------------------------------------------------------------

# 64. Semantic Links and Accessibility

Avoid vague link text when possible.

Less useful:

``` html
<a href="/report.pdf">Click here</a>
```

Better:

``` html
<a href="/report.pdf">
    Download the 2026 annual report
</a>
```

A screen-reader user may navigate through links without reading all
surrounding text.

The link text should therefore make sense on its own.

------------------------------------------------------------------------

# 65. `figure` and `figcaption`

Use `<figure>` when content is self-contained and has an optional
caption.

``` html
<figure>

    <img
        src="mountain.jpg"
        alt="Mountain above a lake"
    >

    <figcaption>
        Sunrise over the lake.
    </figcaption>

</figure>
```

This is useful for images, diagrams, code examples, and other content
that has a caption.

------------------------------------------------------------------------

# 66. `details` and `summary`

HTML can create an expandable section without JavaScript:

``` html
<details>

    <summary>What is HTML?</summary>

    <p>
        HTML is the markup language used to structure web documents.
    </p>

</details>
```

Useful for:

-   FAQs
-   additional explanations
-   optional details

This is a good example of why you should learn native HTML before
solving every interaction with JavaScript.

------------------------------------------------------------------------

# 67. `data-*` Attributes

HTML allows custom data attributes beginning with `data-`.

Example:

``` html
<button
    type="button"
    data-product-id="42"
>
    Add to cart
</button>
```

JavaScript can later read this value.

These attributes are useful for application-specific information.

But they do not replace semantic HTML.

This:

``` html
<button data-action="save">
    Save
</button>
```

is good.

This:

``` html
<div data-action="button">
    Save
</div>
```

is still a div pretending to be a button.

------------------------------------------------------------------------

# 68. HTML Is Forgiving

Browsers are surprisingly forgiving.

You can write broken HTML and still see something on screen.

That does not mean the HTML is correct.

Browsers often attempt to repair invalid markup.

Your goal is not:

> "The browser showed something."

Your goal is:

> "I wrote a clear document that the browser can correctly understand."

------------------------------------------------------------------------

# 69. Debugging HTML

When something isn't working, don't randomly change tags.

Use a process.

## Step 1 --- Check the file

Make sure you're editing the HTML file you're actually opening.

## Step 2 --- Check paths

If this doesn't load:

``` html
<img src="images/photo.jpg" alt="Photo">
```

check:

``` text
Current HTML file
       ↓
images folder
       ↓
photo.jpg
```

Case can matter depending on the server/environment.

## Step 3 --- Inspect the element

Open browser DevTools and inspect the element.

Look at the DOM the browser actually created.

## Step 4 --- Check Network

If an image, CSS file, video, or other resource fails, check the Network
tab.

For example:

``` text
404 Not Found
```

usually means the requested resource wasn't found at that URL.

Now you can investigate the path instead of guessing.

------------------------------------------------------------------------

# 70. A Good Learning Loop

Don't write hundreds of lines before opening the browser.

Use this:

``` text
Write a small piece
       ↓
Open/refresh browser
       ↓
Look at result
       ↓
Inspect if something is wrong
       ↓
Fix it
       ↓
Repeat
```

You'll learn faster because every mistake becomes visible immediately.

------------------------------------------------------------------------

# 71. Practical Exercise 1 --- Personal Profile

Create:

``` text
profile.html
```

Include:

-   page title
-   one `<h1>`
-   introduction
-   profile image
-   skills list
-   two external links
-   footer

No CSS.

Focus only on structure.

------------------------------------------------------------------------

# 72. Practical Exercise 2 --- HTML Documentation Page

Create:

``` text
html-notes.html
```

Structure:

``` text
HTML
├── What is HTML?
├── Elements
├── Attributes
├── Links
├── Images
├── Forms
└── Accessibility
```

Use:

``` text
h1
h2
p
ul
a
code
section
main
```

Add a navigation menu using internal anchor links.

------------------------------------------------------------------------

# 73. Practical Exercise 3 --- Registration Form

Create a registration form containing:

``` text
Name
Email
Password
Age
Plan
Country
Interests
About yourself
Terms checkbox
Submit
```

Requirements:

-   every control has a label
-   correct input types
-   required fields
-   useful validation
-   radio buttons share the same `name`
-   checkboxes can be selected independently
-   use `fieldset` and `legend` where appropriate

Try doing it entirely with HTML first.

------------------------------------------------------------------------

# 74. Practical Exercise 4 --- Student Result Table

Create a table:

``` text
Student
Math
Physics
Chemistry
Total
```

Requirements:

-   caption
-   table head
-   table body
-   column headers
-   row headers where appropriate
-   at least five students

Try to make the table understandable even without CSS.

------------------------------------------------------------------------

# 75. Practical Exercise 5 --- Semantic Blog

Build:

``` text
header
nav
main
    article
        article header
        paragraphs
        image
        figure
        blockquote
    aside
footer
```

Make it represent a real blog article.

The goal is semantic structure, not visual design.

------------------------------------------------------------------------

# 76. Practical Exercise 6 --- Build From Memory

Close your notes.

Create a page containing:

``` text
DOCTYPE
html
head
title
body
header
nav
main
section
article
aside
footer
```

Then add:

-   headings
-   paragraphs
-   links
-   image
-   list
-   form
-   table

Afterward, compare your result with this chapter.

This is much better for learning than simply rereading examples.

------------------------------------------------------------------------

# 77. Mini Project --- Portfolio Skeleton

Build the HTML structure of a personal portfolio.

Suggested structure:

``` text
Portfolio
│
├── Header
│   ├── Name
│   └── Navigation
│
├── Main
│   ├── About
│   ├── Skills
│   ├── Projects
│   │   ├── Project article
│   │   ├── Project article
│   │   └── Project article
│   └── Contact
│       └── Form
│
└── Footer
```

Start with:

``` html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">

    <meta
        name="viewport"
        content="width=device-width, initial-scale=1.0"
    >

    <title>Your Name — Portfolio</title>
</head>

<body>

    <header>
        ...
    </header>

    <nav>
        ...
    </nav>

    <main>

        <section id="about">
            ...
        </section>

        <section id="skills">
            ...
        </section>

        <section id="projects">
            ...
        </section>

        <section id="contact">
            ...
        </section>

    </main>

    <footer>
        ...
    </footer>

</body>

</html>
```

Don't worry about colors, animations, or fancy design.

For now, make the document make sense.

------------------------------------------------------------------------

# 78. Questions You Should Be Able to Answer

## Fundamentals

1.  What is HTML?
2.  Why isn't HTML a programming language?
3.  What is an element?
4.  What is a tag?
5.  What is an attribute?
6.  What is nesting?
7.  What does `<!DOCTYPE html>` do?
8.  What belongs in `<head>`?
9.  What belongs in `<body>`?

## Text

10. What is the difference between `<h1>` and `<h2>`?
11. Why shouldn't headings be chosen only because of size?
12. What is the difference between `<strong>` and `<em>`?
13. When would you use `<blockquote>`?
14. What does `<pre>` do?
15. What is the difference between `<ul>` and `<ol>`?

## Links

16. What is an absolute URL?
17. What is a relative URL?
18. What does `../` mean?
19. How do you link to a section on the same page?
20. What does `download` do?

## Media

21. Why is `alt` important?
22. What should decorative images use for `alt`?
23. What does `<audio>` do?
24. What does `<video>` do?
25. What is an iframe?

## Semantic HTML

26. Why use semantic HTML?
27. What is `<main>` for?
28. What is the difference between `<section>` and `<article>`?
29. What is `<aside>`?
30. Why use `<nav>`?

## Forms

31. Why is `<label>` important?
32. Why do form controls need `name`?
33. What is the difference between a checkbox and radio button?
34. Why do radio buttons share the same `name`?
35. What does `required` do?
36. Is browser validation enough for security?

## Tables

37. What is `<tr>`?
38. What is `<th>`?
39. What is `<td>`?
40. What is `<caption>`?
41. When should you use a table?

## Accessibility

42. Why is semantic HTML useful for accessibility?
43. Why is a real `<button>` better than a clickable `<div>`?
44. What does keyboard navigation mean?
45. What is ARIA?
46. Why shouldn't ARIA unnecessarily replace native HTML?

------------------------------------------------------------------------

# 79. Final Checklist

## Fundamentals

-   [ ] HTML document structure
-   [ ] Elements
-   [ ] Tags
-   [ ] Attributes
-   [ ] Nesting
-   [ ] Comments
-   [ ] Head
-   [ ] Body

## Text

-   [ ] Headings
-   [ ] Paragraphs
-   [ ] Emphasis
-   [ ] Quotes
-   [ ] Code
-   [ ] Lists

## Links

-   [ ] Absolute URLs
-   [ ] Relative URLs
-   [ ] Anchor links
-   [ ] Download links
-   [ ] File paths

## Images and Media

-   [ ] Images
-   [ ] `alt`
-   [ ] Audio
-   [ ] Video
-   [ ] iframe
-   [ ] figure
-   [ ] figcaption

## Semantic HTML

-   [ ] `header`
-   [ ] `nav`
-   [ ] `main`
-   [ ] `section`
-   [ ] `article`
-   [ ] `aside`
-   [ ] `footer`
-   [ ] `div`
-   [ ] `span`

## Forms

-   [ ] Form structure
-   [ ] Inputs
-   [ ] Labels
-   [ ] Buttons
-   [ ] Select
-   [ ] Textarea
-   [ ] Checkboxes
-   [ ] Radio buttons
-   [ ] Validation
-   [ ] `name`
-   [ ] `id`
-   [ ] `required`

## Tables

-   [ ] Rows
-   [ ] Columns
-   [ ] Headers
-   [ ] Captions
-   [ ] `thead`
-   [ ] `tbody`
-   [ ] `scope`

## Accessibility

-   [ ] Semantic HTML
-   [ ] Accessible forms
-   [ ] Keyboard navigation
-   [ ] Meaningful `alt`
-   [ ] Native controls
-   [ ] ARIA basics

------------------------------------------------------------------------

# 80. Where HTML Fits in the Roadmap

Your web-development path now looks like:

``` text
Web Fundamentals
       ↓
HTML
       ↓
CSS
       ↓
JavaScript
       ↓
DOM & Browser APIs
       ↓
Async JavaScript / Fetch
       ↓
Frontend Projects
       ↓
React
       ↓
Node.js
       ↓
Express
       ↓
REST APIs
       ↓
Databases
       ↓
Authentication
       ↓
Deployment
       ↓
Full-Stack Projects
```

Don't rush toward frameworks.

If HTML is weak, React won't magically fix that.

If HTML + CSS are weak, frontend frameworks will mostly hide the gaps.

The fundamentals are what make the later tools easier.

------------------------------------------------------------------------

# Final Mental Model

When you see a webpage, try to think about its structure:

``` text
DOCUMENT
│
├── HEAD
│   ├── title
│   ├── metadata
│   └── resource references
│
└── BODY
    │
    ├── HEADER
    │   └── introductory content
    │
    ├── NAV
    │   └── navigation
    │
    ├── MAIN
    │   │
    │   ├── SECTION
    │   │   └── content
    │   │
    │   ├── ARTICLE
    │   │   └── independent content
    │   │
    │   └── ASIDE
    │       └── related content
    │
    └── FOOTER
        └── footer information
```

Inside those structures you place:

``` text
Text
Links
Images
Lists
Forms
Tables
Audio
Video
```

The browser parses all of this and creates the DOM.

That is the real foundation.

You don't need to memorize every HTML tag.

You need to understand the structure well enough that, when you have a
piece of content in front of you, you can decide what it **is** and
choose the appropriate HTML element.

**The tags are the vocabulary.\
The structure is the language.**
