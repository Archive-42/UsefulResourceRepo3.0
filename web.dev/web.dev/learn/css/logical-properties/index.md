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

- <a href="#terminology" class="toc__anchor">Terminology</a>
- <a href="#block-flow" class="toc__anchor">Block flow</a>
- <a href="#inline-flow" class="toc__anchor">Inline flow</a>
- <a href="#flow-relative" class="toc__anchor">Flow relative</a>
- <a href="#sizing" class="toc__anchor">Sizing</a>
- <a href="#start-and-end" class="toc__anchor">Start and end</a>
- <a href="#spacing-and-positioning" class="toc__anchor">Spacing and positioning</a>
- <a href="#borders" class="toc__anchor">Borders</a>
- <a href="#units" class="toc__anchor">Units</a>
- <a href="#using-logical-properties-pragmatically" class="toc__anchor">Using logical properties pragmatically</a>
- <a href="#solving-the-icon-issue" class="toc__anchor">Solving the icon issue</a>
- <a href="#browser-support" class="toc__anchor">Browser support</a>

011

# Logical Properties

Logical, flow relative properties and values are linked to the flow of text, rather than the physical shape of the screen. Learn how to take advantage of this newer approach to CSS.

On this page

- <a href="#terminology" class="toc__anchor">Terminology</a>
- <a href="#block-flow" class="toc__anchor">Block flow</a>
- <a href="#inline-flow" class="toc__anchor">Inline flow</a>
- <a href="#flow-relative" class="toc__anchor">Flow relative</a>
- <a href="#sizing" class="toc__anchor">Sizing</a>
- <a href="#start-and-end" class="toc__anchor">Start and end</a>
- <a href="#spacing-and-positioning" class="toc__anchor">Spacing and positioning</a>
- <a href="#borders" class="toc__anchor">Borders</a>
- <a href="#units" class="toc__anchor">Units</a>
- <a href="#using-logical-properties-pragmatically" class="toc__anchor">Using logical properties pragmatically</a>
- <a href="#solving-the-icon-issue" class="toc__anchor">Solving the icon issue</a>
- <a href="#browser-support" class="toc__anchor">Browser support</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 012: Logical Properties

A really common user interface pattern is a text label with a supporting inline icon.

The icon sits to the left of the text with a small gap between the two, provided by `margin-right` on the icon. There's a problem though, because this will only work when the text direction is left to right. If the text direction changed to right-to-left—which is how languages like Arabic read—the icon will sit up against the text.

How do you account for this in CSS? Logical properties allow you to resolve these situations. Among many other benefits, they provide free, automatic support for internationalization. They help you build a more resilient, inclusive front-end.

## Terminology <a href="#terminology" class="w-headline-link">#</a>

The physical properties of top, right, bottom, and left refer to the physical dimensions of the viewport. You can think of these like a compass rose on a map. Logical properties, on the other hand, refer to the edges of a box as they relate to the _flow of content_. Therefore, they can change if the text direction or writing mode changes. This is a big shift from directional styles, and it gives us a lot more flexibility when styling our interfaces.

## Block flow <a href="#block-flow" class="w-headline-link">#</a>

Block flow is the direction in which content blocks are placed. For example, if there are two paragraphs, the block flow is where the second paragraph will go. In an English document,the block flow is top-to-bottom. Think of this in the context of paragraphs of text following each other, top-to-bottom.

## <figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/JKfvuIFBBtmvylmFSV8K.svg" width="800" height="507" /></figure>Inline flow <a href="#inline-flow" class="w-headline-link">#</a>

The inline flow is how text flows in a sentence. In an English document the inline flow is left to right. If you were to change the document language of your webpage to Arabic (`<html lang="ar">`), then the inline flow would be right-to-left.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/DfyMS0jh0SjSxaeNioJt.svg" width="800" height="507" /></figure>Text flows in the direction determined by the document's writing mode. You can change the direction that text is laid out with the `writing-mode` property. This can be applied to the entire document, or to individual elements.

## Flow relative <a href="#flow-relative" class="w-headline-link">#</a>

Historically in CSS, we have only been able to apply properties like margin relative to the direction of their sides. For example, `margin-top` is applied to the physical top of the element. With logical properties, `margin-top` becomes `margin-block-start`. This means that regardless of language and text direction, the **block flow** has appropriate margin rules.

## <figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=1600 1600w" width="800" height="559" /></figure>Sizing <a href="#sizing" class="w-headline-link">#</a>

To prevent an element exceeding a certain width or height, write a rule like this:

    .my-element {
      max-width: 150px;
      max-height: 100px;
    }

The flow-relative equivalents are `max-inline-size` and `max-block-size`. You can also use `min-block-size` and `min-inline-size` instead of `min-height` and `min-width`.

With logical properties, that max width and height rule would look like this:

    .my-element {
      max-inline-size: 150px;
      max-block-size: 100px;
    }

## Start and end <a href="#start-and-end" class="w-headline-link">#</a>

Instead of using directions such as top, right, bottom and left, use start and end. This gives you block-start, inline-end, block-end, and inline-start. These allow you to apply CSS properties that respond to writing mode changes.

For example, to align text to the right, you could use this CSS:

    p {
      text-align: right;
    }

If your aim is not to align to the physical right, but rather to the start of the reading direction, this isn't helpful. With logical values, there are more helpful `start` and `end` values which map to the text direction. The text alignment rule now looks like this:

    p {
      text-align: end;
    }

## Spacing and positioning <a href="#spacing-and-positioning" class="w-headline-link">#</a>

Logical properties for `margin`, `padding` and `inset` make positioning elements, and determining how these elements interact with each other across writing modes easier and more efficient. The margin and padding related properties are still direct mappings to directions, but the key difference is that when a writing mode changes, they change with it.

    .my-element {
      padding-top: 2em;
      padding-bottom: 2em;
      margin-left: 2em;
      position: relative;
      top: 0.2em;
    }

This adds some vertical inside space with `padding` and pushes it out from the left with `margin`. The `top` property also shifts it downwards. With logical property equivalents, it would instead look like this:

    .my-element {
      padding-block-start: 2em;
      padding-block-end: 2em;
      margin-inline-start: 2em;
      position: relative;
      inset-block-start: 0.2em;
    }

This adds some inline inside space with `padding` and pushes it out from the inline-start with `margin`. The `inset-block` property moves it inwards from the block-start.

The `inset-block` property isn't the only shorthand option with logical properties. This rule can be further condensed, using shorthand versions of the margin and padding properties.

    .my-element {
      padding-block: 2em;
      margin-inline: 2em 0;
      position: relative;
      inset-block: 0.2em 0;
    }

## Borders <a href="#borders" class="w-headline-link">#</a>

Adding `border` and `border-radius` can also be done with logical properties. To add a border on the bottom and right, with a right-hand radius, you might write a rule like this:

    .my-element {
      border-bottom: 1px solid red;
      border-right: 1px solid red;
      border-bottom-right-radius: 1em;
    }

Or, you could use logical properties like this:

    .my-element {
      border-block-end: 1px solid red;
      border-inline-end: 1px solid red;
      border-end-end-radius: 1em;
    }

The "end-end" in `border-end-end-radius` is the block end _and_ inline end.

## Units <a href="#units" class="w-headline-link">#</a>

Logical properties bring two new units: `vi` and `vb`. A `vi` unit is 1% of the viewport size in the inline direction. The non-logical property equivalent is `vw`. The `vb` unit is 1% of the viewport in the block direction. The non-logical property equivalent is `vh`.

These units will always map to the reading direction. For example, if you want an element to take up 80% of the available inline space of a viewport, using the `vi` unit will automatically switch that size to be top to bottom if the writing mode is vertical.

## Using logical properties pragmatically <a href="#using-logical-properties-pragmatically" class="w-headline-link">#</a>

Logical properties and writing modes are not just for internationalization. You can use them to produce a more versatile user interface.

If you have a chart that has labels on the X axis and Y axis, you might want the text on the Y label to read vertically.

Because the Y axis label in the demo has a `writing-mode` of `vertical-rl`, you can use the same `margin` values on both labels. The `margin-block-start` value applies to both labels because the block start is on the right for the Y axis and on the top for the X axis. The block-start sides have a red border so you can see them.

## Solving the icon issue <a href="#solving-the-icon-issue" class="w-headline-link">#</a>

Now that we've covered logical properties, this knowledge can be applied to the design problem we started with.

    p {
      display: inline-flex;
      align-items: center;
    }

    p svg {
      width: 1.2em;
      height: 1.2em;
      margin-right: 0.5em;
      flex: none;
    }

The margin has been applied to the right of the icon element. In order for the spacing between the icon and the text to support all reading direction, the `margin-inline-end` property needs to be used instead.

    p {
      display: inline-flex;
      align-items: center;
    }

    p svg {
      width: 1.2em;
      height: 1.2em;
      margin-inline-end: 0.5em;
      flex: none;
    }

Now, regardless of reading direction, the icon will position itself and space itself appropriately.

Test your knowledge of logical properties

As you write with your hand, your wrist is moving along which logical axis?

<span data-role="option">`inline`</span> <span data-role="option">`block`</span>

Words flow inline and so must a your hand travel when writing.

Content flows as blocks and your wrist moves along this axis when end one content type and beginning another.

Check all that can benefit from logical properties

<span data-role="option">colors</span> <span data-role="option">alignment</span> <span data-role="option">shadows</span> <span data-role="option">box sides</span> <span data-role="option">sizes</span> <span data-role="option">box corners</span>

Color don't change when a document writing mode does.

Examples: `flex-start`, `block-end`, and `inline-start`

Shadows don't change when a document writing mode does.

Examples: `block-start` and `inline`.

Examples: `inline-size` and `max-block-size`.

Examples: `border-end-end-radius`.

Which logical side of a word is underlined?

<span data-role="option">inline start</span> <span data-role="option">inline end</span> <span data-role="option">block start</span> <span data-role="option">block end</span>

This would put an underline on the left of a word in English.

This would put an underline on the right of a word in English.

This would put an underline on the top of a word in English.

Very nice that CSS does this positioning for you.

## Browser support <a href="#browser-support" class="w-headline-link">#</a>

Browser support is extremely varied for logical properties and values, especially with shorthand properties, such as `margin-inline` and `padding-inline`. It's recommended that you assess the support for these properties before using them, and consider how your website will look and behave where no support is available. [A full breakdown can be found on caniuse.com](https://caniuse.com/css-logical-props).

<a href="/learn/css/grid/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">010</span>

Grid

<a href="/learn/css/spacing/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">012</span>

Spacing

Find out how to select the best method of spacing elements, taking into consideration the layout method you are using and component that you need to build.

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
