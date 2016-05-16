# Sections

> Sections allows authors to define the desired outline and document structure.

## Table of Contents

1. [Body](#body)
2. [Main](#main)
3. [Header](#header)
4. [Section](#section)
5. [Article](#article)
6. [Footer](#footer)
7. [Nav](#nav)
8. [Aside](#aside)
9. [Address](#address)
10. [Headings](#headings)

## Body

### Always include a heading for the `<body>` (sectioning root)

> **[?]** By including a heading for the body you define the first section of your document, making it more accessible to people using screen-readers. You can also define the body's heading inside a `<header>` element without hurting semantics, since [it's not a sectioning content](#use-the-header-element-to-represent-the-introductory-content of-a-section).

Bad:

```html
<body>
  ...
  <article>
    ...
  </article>
</body>
```

Good:

```html
<body>
  <h1>Burn of the Midnight Lamp's Website</h1>
  <article>
    ...
  </article>
</body>
```

## Main

> Note: Please notice that the `<main>` content is actually a `Text content` element and not a sectioning one. However, for convenience reasons (while the `Text content` section is not ready) it will stay here, given that people looking for a better division of their applications would first look for it here.

### Use the `<main>` element to identify the main content of the document.

> **[?]** The `<main>` element represents the main content of a document. It indicates content that is directly related to the central topic of a document, or the central functionality of an application. **There can be only one `<main>` element in a document.**

Bad:

```html
<body>
  <header>
    ...
  </header>
  <article>
    <!-- supposed to be the main content -->
    ...
  </article>
</body>
```

Good:

```html
<body>
  <header>
    ...
  </header>
  <main>
    <article>
      <!-- supposed to be the main content -->
      ...
    </article>
  </main>
</body>
```

### Don't use the `<main>` element as a descendent of any other sectioning element

> **[?]** Other sectioning elements such as `<article>`, `<aside>`, `<footer>`, `<header>`, or `<nav>` could not be the parent of a `<main>` element. Think about `<main>` as a semantic wrapper to define what is the meaning of the content inside the document, or the functionality inside an application.

Bad:

```html
<section>
  <article>
    <main>
      ...
    </main>
  </article>
</section>
```

Good:

```html
<main>
  <section>
    <article>
      ...
    </article>
  </section>
</main>
```

## Header

### Use the `<header>` element to represent the introductory content of a section

> **[?]** The `<header>` element is just a container. It doesn't introduce a new section. By defining a header element with a heading (`<h1>`, `<h2>`...`<h6>`) inside of it, the heading automatically becomes associated with the higher level element (in this case, the `<section>` element).

Bad:

```html
<section>
  <div class="intro">
    <h2>Introduction</h2>
  </div>
  <section>
    ...
  </section>
</section>
```

Good:

```html
<section>
  <header class="intro">
    <h2>Introduction</h2>
  </header>
  <section>
    ...
  </section>
</section>
```

## Section

### Prefer explicit `section`ing over implicit `section`ing

> **[?]** By explicitly sectioning different parts of your document, not only you define a better structure but it becomes easier to style by having beginning and ending elements. Headings alone can only show where a piece of content starts, not where it ends, which makes it difficult to tell what belongs to what.

Bad:

```html
<body>
  <h1>Guidelines for playing guitar like Jimi Hendrix</h1>
  ...
  <h2>Who is Jimi Hendrix?</h2>
  ...
  <h2>How to play like him?</h2>
  ...
  <h2>Need help? Talk with Us!!</h2>
</body>
```

Good:

```html
<body>
  ...
  <section>
    <h1>Guidelines for playing guitar like Jimi Hendrix</h1>
  </section>
  <section>
    <h2>Who is Jimi Hendrix?</h2>
  </section>
  <section>
    <h2>How to play like him?</h2>
  </section>
  <section>
    <h2>Need help? Talk with Us!!</h2>
  </section>
  ...
</body>
```

### Group related contents with the `<section>` element

> **[?]** Generally speaking, `<section>`s are used to group parts of a document that have related content. Defining its content explicitly in the document's outline.

Bad:

```html
<footer>
  ...
    <div class="about">
      <h2>About Us</h2>
      ...
    </div>
    <div class="contact">
      <h2>Contact Us</h2>
      ...
    </div>
    <div class="newsletter">
      <h2>Newsletter</h2>
      ...
    </div>
  ...
</footer>
```

Good:

```html
<footer>
  ...
  <section class="about">
    <h2>About Us</h2>
    ...
  </section>
  <section class="contact">
    <h2>Contact Us</h2>
    ...
  </section>
  <section class="newsletter">
    <h2>Newsletter</h2>
    ...
  </section>
  ...
</footer>
```

### Don't use `<section>` as a new `<div>` element

> **[?]** Unlike `<section>`, the `<div>` element don't have any semantic meaning, and should be used for styling purposes. By changing your `<div>`s to `<section>`s, you create a new outline for each part of your document, that not necessarily includes a meaningful separated section, which is definitely a bad idea.

Bad:

```html
<section class="overlay">
  <img src="..." alt="...">
  <section class="visible-on-hover">
    ...
  </section>
</section>
```

Good:

```html
<div class="overlay">
  <img src="..." alt="...">
  <div class="visible-on-hover">
    ...
  </div>
</div>
```

## Article

### Use the `<article>` element instead of `<section>` if the content makes sense outside the page's context

> **[?]** You could think about the `<article>` element as an independent section, that could be distributed elsewhere without losing its meaning. Despite being useful outside the page content, `<article>`s are used to group elements that fit together as the same way as a `<section>` .

Bad:

```html
<section>
  <header>
    <h1>Clastes Made of Sand</h1>
  </header>
  A little Indian brave who before he was ten, played war game sin.
  The woods with his Indian friends, and he built a dream that when he
  Grew up, he would be a fearless warrior Indian Chief
  ...
</section>
```

Good:

```html
<article>
  <header>
    <h1>Clastes Made of Sand</h1>
  </header>
  A little Indian brave who before he was ten, played war game sin.
  The woods with his Indian friends, and he built a dream that when he
  Grew up, he would be a fearless warrior Indian Chief
  ...
</article>
```

## Aside

### Use `<aside>` to include additional information about a topic that it's related

> **[?]** The aside element should be used to display information that is related to their wrapper (in this case, the `<article>` element), but not crucial for its understanding (the `<aside>` was used for an additional information about a curious fact).

Bad:

```html
<article>
  <header>
    <h1>Purple Haze by Jimi Hendrix</h1>
    <p>...</p>
  </header>
  Purple haze all in my brain
  Lately things don't seem the same
  Acting funny, but I don't know why
  Excuse me while I kiss the sky
  ...
  <div class="curious-fact">
    <h2>Curious Fact</h2>
    <p>Hendrix’s hit “Purple Haze” was partly influenced by a science fiction story, not drugs.
    Phillip Jose Farmer’s "Night of Light" described a purple haze that caused the inhabitants
    of planet Dante's Joy to become disoriented.</p>
  </div>
</article>
```

Good:

```html
<article>
  <header>
    <h1>Purple Haze by Jimi Hendrix</h1>
    <p></p>
  </header>
  Purple haze all in my brain
  Lately things don't seem the same
  Acting funny, but I don't know why
  Excuse me while I kiss the sky
  ...
  <aside class="curious-fact">
    <h2>Curious Fact</h2>
    <p>Hendrix’s hit “Purple Haze” was partly influenced by a science fiction story, not drugs.
    Phillip Jose Farmer’s "Night of Light" described a purple haze that caused the inhabitants
    of planet Dante's Joy to become disoriented.</p>
  </aside>
</article>
```

## Footer

### Use the `<footer>` element to semantically display authoring information about its parent section

> **[?]** The `<footer>` element is not necessarily used as a direct child of the `<body>` element (despite being the most used place). It could also be used to display information about who wrote the content (usually as a parent of an `<address>` element), link related documents, copyright information and related stuff.

Bad:

```html
<article>
  <h1>Are You Experienced Album</h1>
  <ul>
    <li>1. "Foxy Lady" - 3:19</li>
    <li>2. "Manic Depression" - 3:42</li>
    <li>3. "Red House" - 3:42</li>
    ...
  </ul>
  <div>
    Are You Experienced © 1966 - Jimi Hendrix Experience
  </div>
  ...
</article>
```

Good:

```html
<article>
  <h1>Are You Experienced Album</h1>
  <ul>
    <li>1. "Foxy Lady" - 3:19</li>
    <li>2. "Manic Depression" - 3:42</li>
    <li>3. "Red House" - 3:42</li>
    ...
  </ul>
  <footer>
    Are You Experienced © 1966 - Jimi Hendrix Experience
  </footer>
  ...
</article>
```

## Nav

### For major navigation blocks, use the `<nav>` element to define a new section with navigation links

> **[?]** The `<nav>` element is, by itself, a sectioning element. Not necessarily for internal navigation, `<nav>` could also be used to mark up a collection of external links. Use cases could be an website's navigation menu, a table of contents and a group of related links inside an article.

Bad:

```html
<ul>
  <li><a href="about.html">About</a><li>
  <li><a href="contact.html">Contact</a><li>
</ul>
```

Good:

```html
<nav>
  <ul>
    <li><a href="about.html">About</a><li>
    <li><a href="contact.html">Contact</a><li>
  </ul>
</nav>
```

## Address

### Use `<address>` to display any contextual contact information

> **[?]** The `<address>` element represents the contact information for its nearest parent, not necessarily `<address>`es. If the `<address>` is included inside an `<article>`, then the contact information is related to the `<article>` author. On this context, it is usually used inside a `<footer>` element. If applied directly inside the `<body>`, the contact information applies to the document as a whole.

Bad:

```html
<article>
  ...
  <footer>
    <p>Written by <a href="http://jimihendrix.com">Jimi Hendrix</a></p>
  </footer>
</article>
```

Good:

```html
<article>
  ...
  <footer>
    <address>
      <p>Written by <a href="http://jimihendrix.com">Jimi Hendrix</a></p>
    </address>
  </footer>
</article>
```

## Headings

### Always add a Heading to an explicit sectioning content

> **[?]** With standalone headings, screen-readers vocalizes the page saying "Entering section", but without explicit including sections around it, there is no way to determine if the section has ended. This way, for accessibility reasons, include a heading (a `<h1>`, `<h2>`...`<h6>`) in each sectioning element (`<section>`, `<article>`, `<nav>`, `<aside>`).

Bad:

```html
<section>
   <header>
      <p class="post-title">The Day I met Jimi Hendrix</p>
      ...
   </header>
   ...
</section>
```

Good:

```html
<section>
   <header>
      <h1 class="post-title">The Day I met Jimi Hendrix</h1>
      ...
   </header>
   ...
</section>
```

### Use the appropriate ranking for heading elements

> **[?]** At the current moment (04/2016), browsers still do not correctly implemented the "outline algorithm", meaning that multiple `<h1>` elements inside diferent sections will still be treated as duplicated top headings, which will issue a warning on the W3C conformance checker.

> A warning message is also displayed on the [W3C HTML Spec](http://www.w3.org/TR/html5/sections.html#outlines) alerting for this issue.

Bad:

```html
<section>
  <h1>First Section</h1>
  ...
  <section>
    <h1>Subsection</h1>
    ...
    <section>
      <h1>Another Subsection</h1>
      ...
    </section>
  </section>
</section>
```

Good:

```html
<section>
  <h1>First Section</h1>
  ...
  <section>
    <h2>Subsection</h2>
    ...
    <section>
      <h3>Another Subsection</h3>
      ...
    </section>
  </section>
</section>
```

### Don't use `display: none` CSS attribute to hide unwanted visible outline headings

> **[?]** Sometimes, by creating outlines, some headings are included for semantic purposes only and are not intended to be visible for the general public (a good example would be the heading of a `<nav>` section). By using `display: none`, you hide it from all users, including screen readers. By relying on the above technique, created by [Steve Faulkner](https://www.paciellogroup.com/blog/2012/05/html5-accessibility-chops-hidden-and-aria-hidden/), you can still keep the information for screen reader users while keep it hidden from other audiences.

Bad:

```css
.offscreen {
  display: none;
}
```

Good:

```css
.offscreen {
  position: absolute;
  clip: rect(1px 1px 1px 1px); /* for Internet Explorer */
  clip: rect(1px, 1px, 1px, 1px);
  padding: 0;
  border: 0;
  height: 1px;
  width: 1px;
  overflow: hidden;
}
```
