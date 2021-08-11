<a href="#main" class="skip-link w-button">Skip to main</a>

<span class="w-tooltip">Close</span>

<span class="font-mono drawer-course__link-counter">000</span> <span class="drawer-course__link-title gap-left-400">Learn CSS</span>

<span class="font-mono drawer-course__link-counter">001</span> <span class="drawer-course__link-title gap-left-400">Box Model</span>

<span class="font-mono drawer-course__link-counter">002</span> <span class="drawer-course__link-title gap-left-400">Selectors</span>

<span class="font-mono drawer-course__link-counter">003</span> <span class="drawer-course__link-title gap-left-400">The cascade</span>

<span class="font-mono drawer-course__link-counter">004</span> <span class="drawer-course__link-title gap-left-400">Specificity</span>

<span class="font-mono drawer-course__link-counter">005</span> <span class="drawer-course__link-title gap-left-400">Inheritance</span>

<span class="font-mono drawer-course__link-counter">006</span> <span class="drawer-course__link-title gap-left-400">Color</span>

<span class="font-mono drawer-course__link-counter">007</span> <span class="drawer-course__link-title gap-left-400">Sizing Units</span>

<span class="font-mono drawer-course__link-counter">008</span> <span class="drawer-course__link-title gap-left-400">Layout</span>

<span class="font-mono drawer-course__link-counter">009</span> <span class="drawer-course__link-title gap-left-400">Flexbox</span>

<span class="font-mono drawer-course__link-counter">010</span> <span class="drawer-course__link-title gap-left-400">Grid</span>

<span class="font-mono drawer-course__link-counter">011</span> <span class="drawer-course__link-title gap-left-400">Logical Properties</span>

<span class="font-mono drawer-course__link-counter">012</span> <span class="drawer-course__link-title gap-left-400">Spacing</span>

<span class="font-mono drawer-course__link-counter">013</span> <span class="drawer-course__link-title gap-left-400">Pseudo-elements</span>

<span class="font-mono drawer-course__link-counter">014</span> <span class="drawer-course__link-title gap-left-400">Pseudo-classes</span>

<span class="font-mono drawer-course__link-counter">015</span> <span class="drawer-course__link-title gap-left-400">Borders</span>

<span class="font-mono drawer-course__link-counter">016</span> <span class="drawer-course__link-title gap-left-400">Shadows</span>

<span class="font-mono drawer-course__link-counter">017</span> <span class="drawer-course__link-title gap-left-400">Focus</span>

<span class="font-mono drawer-course__link-counter">018</span> <span class="drawer-course__link-title gap-left-400">Z-index and stacking contexts</span>

<span class="font-mono drawer-course__link-counter">019</span> <span class="drawer-course__link-title gap-left-400">Functions</span>

<span class="font-mono drawer-course__link-counter">020</span> <span class="drawer-course__link-title gap-left-400">Gradients</span>

<span class="font-mono drawer-course__link-counter">021</span> <span class="drawer-course__link-title gap-left-400">Animations</span>

<span class="font-mono drawer-course__link-counter">022</span> <span class="drawer-course__link-title gap-left-400">Filters</span>

<span class="font-mono drawer-course__link-counter">023</span> <span class="drawer-course__link-title gap-left-400">Blend Modes</span>

<span class="font-mono drawer-course__link-counter">024</span> <span class="drawer-course__link-title gap-left-400">Conclusion and next steps</span>

- - [Learn](/learn/)
- [Learn CSS!](/learn/css/)

Share

On this page

- <a href="#::before-and-::after" class="toc__anchor">::before and ::after</a>
- <a href="#::first-letter" class="toc__anchor">::first-letter</a>
- <a href="#::first-line" class="toc__anchor">::first-line</a>
- <a href="#::backdrop" class="toc__anchor">::backdrop</a>
- <a href="#::marker" class="toc__anchor">::marker</a>
- <a href="#::selection" class="toc__anchor">::selection</a>
- <a href="#::placeholder" class="toc__anchor">::placeholder</a>
- <a href="#::cue" class="toc__anchor">::cue</a>

013

# Pseudo-elements

A pseudo-element is like adding or targeting an extra element without having to add more HTML. They have a variety of roles and you can learn about them in this module.

On this page

- <a href="#::before-and-::after" class="toc__anchor">::before and ::after</a>
- <a href="#::first-letter" class="toc__anchor">::first-letter</a>
- <a href="#::first-line" class="toc__anchor">::first-line</a>
- <a href="#::backdrop" class="toc__anchor">::backdrop</a>
- <a href="#::marker" class="toc__anchor">::marker</a>
- <a href="#::selection" class="toc__anchor">::selection</a>
- <a href="#::placeholder" class="toc__anchor">::placeholder</a>
- <a href="#::cue" class="toc__anchor">::cue</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 014: Pseudo-elements

If you've got an article of content and you want the first letter to be a much bigger drop cap— how do you achieve that?

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Qpo2f3eRInt5iM6qW2p2.svg" alt="A couple of paragraphs of text with a blue drop cap" width="800" height="318" />

In CSS, you can use the `::first-letter` pseudo-element to achieve this sort of design detail.

    p::first-letter {
      color: blue;
      float: left;
      font-size: 2.6em;
      font-weight: bold;
      line-height: 1;
      margin-inline-end: 0.2rem;
    }

A pseudo-element is like adding or targeting an extra element without having to add more HTML. This example solution, using `::first-letter`, is one of many pseudo-elements. They have a range of roles, and in this lesson you're going to learn which pseudo-elements are available and how you can use them.

## `::before` and `::after` <a href="#::before-and-::after" class="w-headline-link">#</a>

Both the [`::before`](https://developer.mozilla.org/en-US/docs/Web/CSS/::before) and [`::after`](https://developer.mozilla.org/en-US/docs/Web/CSS/::after) pseudo-elements create a child element inside an element **only** if you define a `content` property.

    .my-element::before {
       content: "";
    }

    .my-element::after {
     content: "";
    }

The `content` can be any string —even an empty one— but be mindful that anything other than an empty string will likely be announced by a screen reader. You can add an image `url`, which will insert an image at its original dimensions, so you won't be able to resize it. You can also insert a [`counter`](<https://developer.mozilla.org/en-US/docs/Web/CSS/counter()>).

**Key Term**: You can create a named counter and then increment it, based on it's position in the document flow. There's all sorts of contexts where they can be really useful, such as automatically numbering an outline.

Once a `::before` or `::after` element has been created, you can style it however you want with no limits. You can only insert a `::before` or `::after` element to an element that will accept child elements ([elements with a document tree](https://www.w3.org/TR/CSS21/generate.html)), so elements such as `<img />`, `<video>`, `<button>` and `<input>` won't work.

## `::first-letter` <a href="#::first-letter" class="w-headline-link">#</a>

We met this pseudo-element at the start of the lesson. It is worth being aware that not all CSS properties can be used when targeting [`::first-letter`](https://developer.mozilla.org/en-US/docs/Web/CSS/::first-letter). The available properties are:

- `color`
- `background` properties (such as `background-image`)
- `border` properties (such as `border-color`)
- `float`
- `font` properties (such as `font-size` and `font-weight`)
- text properties (such as `text-decoration` and `word-spacing`)

<!-- -->

    p::first-letter {
      color: goldenrod;
      font-weight: bold;
    }

You can only use `:first-letter` on block containers. Therefore, it won't work if you try to add it to an element that has `display: inline`.

## `::first-line` <a href="#::first-line" class="w-headline-link">#</a>

The [`::first-line`](https://developer.mozilla.org/en-US/docs/Web/CSS/::first-line) pseudo-element will let you style the first line of text only if the element with `::first-line` applied has a `display` value of `block`, `inline-block`, `list-item`, `table-caption` or `table-cell`.

    p::first-line {
      color: goldenrod;
      font-weight: bold;
    }

Like the `::first-letter` pseudo-element, there's only a subset of CSS properties you can use:

- `color`
- `background` properties
- `font` properties
- `text` properties

## `::backdrop` <a href="#::backdrop" class="w-headline-link">#</a>

If you have an element that is presented in full screen mode, such as a `<dialog>` or a `<video>`, you can style the backdrop—the space between the element and the rest of the page—with the [`::backdrop`](https://developer.mozilla.org/en-US/docs/Web/CSS/::backdrop) pseudo-element:

    video::backdrop {
      background-color: goldenrod;
    }

The `::backdrop` pseudo-element is supported in all major browsers apart from Safari.

## `::marker` <a href="#::marker" class="w-headline-link">#</a>

The [`::marker`](https://developer.mozilla.org/en-US/docs/Web/CSS/::marker) pseudo-element lets you style the bullet or number for a list item or the arrow of a `<summary>` element.

    ::marker {
      color: hotpink;
    }

    ul ::marker {
      font-size: 1.5em;
    }

    ol ::marker {
      font-size: 1.1em;
    }

    summary::marker {
      content: '\002B'' '; /* Plus symbol with space */
    }

    details[open] summary::marker {
      content: '\2212'' '; /* Minus symbol with space */
    }

Only a small subset of CSS properties are supported for `::marker`:

- `color`
- `content`
- `white-space`
- `font` properties
- `animation` and `transition` properties

You can change the marker symbol, using the `content` property. You can use this to set a plus and minus symbol for the closed and empty states of a `<summary>` element, for example.

## `::selection` <a href="#::selection" class="w-headline-link">#</a>

The [`::selection`](https://developer.mozilla.org/en-US/docs/Web/CSS/::selection) pseudo-element allows you to style how selected text looks.

    ::selection {
      background: green;
      color: white;
    }

This pseudo-element can be used to style all selected text as in the above demo. It can also be used in combination with other selectors for a more specific selection style.

    p:nth-of-type(2)::selection {
      background: darkblue;
      color: yellow;
    }

As with other pseudo-elements, only a subset of CSS properties are allowed:

- `color`
- `background-color` but **not** `background-image`
- `text` properties

## `::placeholder` <a href="#::placeholder" class="w-headline-link">#</a>

You can add a helper hint to form elements, such as `<input>` with a `placeholder` attribute. The [`::placeholder`](https://developer.mozilla.org/en-US/docs/Web/CSS/::placeholder) pseudo-element allows you to style that text.

    input::placeholder {
      color: darkcyan;
    }

The `::placeholder` only supports a subset of CSS rules:

- `color`
- `background` properties
- `font` properties
- `text` properties

A `placeholder` is not `<label>` and should not be used in place of a `<label>`. Form elements must be labelled or they will be inaccessible.

## `::cue` <a href="#::cue" class="w-headline-link">#</a>

Last in this tour of pseudo-elements is the [`::cue`](https://developer.mozilla.org/en-US/docs/Web/CSS/::cue) pseudo-element. This allows you to style the WebVTT cues, which are the captions of a `<video>` element.

You can also pass a selector into a `::cue`, which allows you to style specific elements _inside_ a caption.

    video::cue {
      color: yellow;
    }

    video::cue(b) {
      color: red;
    }

    video::cue(i) {
      color: lightpink;
    }

Test your knowledge of pseudo-elements

Which of the following are not pseudo-elements?

<span data-role="option">`::before`</span> <span data-role="option">`::first-paragraph`</span> <span data-role="option">`::after`</span> <span data-role="option">`::marker`</span> <span data-role="option">`::pencil`</span> <span data-role="option">`:active`</span>

Don't forget to add `content: '';`.

This doesn't exist in CSS.

Don't forget to add `content: '';`.

This is the bullet element when you use a list element or display type.

This doesn't exist in CSS.

This is a pseudo-class not a pseudo-element.

Pseudo-elements can be found in an HTML file.

<span data-role="option">True</span> <span data-role="option">False</span>

While DevTools may show pseudo-elements in the Elements panel, pseudo-elements won't be found in the HTML, they're owned by the browser.

They can be targeted by CSS but won't be found in the HTML.

<a href="/learn/css/spacing/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">012</span>

Spacing

<a href="/learn/css/pseudo-classes/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">014</span>

Pseudo-classes

Pseudo-classes let you apply CSS based on state changes. This means that your design can react to user input such as an invalid email address.

- ### Contribute

  - <a href="https://github.com/GoogleChrome/web.dev/issues/new?assignees=&amp;labels=bug&amp;template=bug_report.md&amp;title=" class="w-footer__linkbox-link">File a bug</a>
  - <a href="https://github.com/googlechrome/web.dev" class="w-footer__linkbox-link">View source</a>

- ### Related content

  - <a href="https://blog.chromium.org/" class="w-footer__linkbox-link">Chrome updates</a>
  - <a href="https://developers.google.com/web/" class="w-footer__linkbox-link">Web Fundamentals</a>
  - <a href="https://developers.google.com/web/showcase/" class="w-footer__linkbox-link">Case studies</a>
  - <a href="https://devwebfeed.appspot.com/" class="w-footer__linkbox-link">DevWeb Content Firehose</a>
  - <a href="/podcasts/" class="w-footer__linkbox-link">Podcasts</a>
  - <a href="/shows/" class="w-footer__linkbox-link">Shows</a>

- ### Connect

  - <a href="https://www.twitter.com/ChromiumDev" class="w-footer__linkbox-link">Twitter</a>
  - <a href="https://www.youtube.com/user/ChromeDevelopers" class="w-footer__linkbox-link">YouTube</a>

<a href="https://developers.google.com/" class="w-footer__utility-logo-link"><img src="/images/lockup-color.png" alt="Google Developers" class="w-footer__utility-logo" width="185" height="33" /></a>

- <a href="https://developer.chrome.com/" class="w-footer__utility-link">Chrome</a>
- <a href="https://firebase.google.com/" class="w-footer__utility-link">Firebase</a>
- <a href="https://cloud.google.com/" class="w-footer__utility-link">Google Cloud Platform</a>
- <a href="https://developers.google.com/products" class="w-footer__utility-link">All products</a>

<!-- -->

- <a href="https://policies.google.com/" class="w-footer__utility-link">Terms &amp; Privacy</a>
- <a href="/community-guidelines/" class="w-footer__utility-link">Community Guidelines</a>

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/terms/site-policies).
