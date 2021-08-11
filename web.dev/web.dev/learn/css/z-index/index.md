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

- <a href="#z-index" class="toc__anchor">Z-index</a>
- <a href="#negative-z-index" class="toc__anchor">Negative z-index</a>
- <a href="#stacking-context" class="toc__anchor">Stacking context</a>
- <a href="#creating-a-stacking-context" class="toc__anchor">Creating a stacking context</a>
- <a href="#resources" class="toc__anchor">Resources</a>

018

# Z-index and stacking contexts

In this module find out how to control the order in which things layer on top of each other, by using z-index and the stacking context.

On this page

- <a href="#z-index" class="toc__anchor">Z-index</a>
- <a href="#negative-z-index" class="toc__anchor">Negative z-index</a>
- <a href="#stacking-context" class="toc__anchor">Stacking context</a>
- <a href="#creating-a-stacking-context" class="toc__anchor">Creating a stacking context</a>
- <a href="#resources" class="toc__anchor">Resources</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 019: z-index and stacking contexts

Say you've got a couple of elements that are absolutely positioned, and are supposed to be positioned on top of each other. You might write a bit of a HTML like this:

    <div class="stacked-items">
     <div class="item-1">Item 1</div>
      <div class="item-2">Item 2</div>
    </div>

But which one sits on top of the other, by default? To know which item would do that, you need to understand z-index and stacking contexts.

## Z-index <a href="#z-index" class="w-headline-link">#</a>

The [`z-index`](https://developer.mozilla.org/en-US/docs/Web/CSS/z-index) property explicitly sets a layer order for HTML based on the 3D space of the browser—the Z axis. This is the axis which shows which layers are closer to and further from you. The vertical axis on the web is the Y axis and the horizontal axis is the X axis.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/PDglCLEK0OJY5LIHwpkI.svg" alt="Each axis surrounding the element" width="760" height="467" />

The `z-index` property accepts a numerical value which can be a positive or negative number. Elements will appear above another element if they have a higher `z-index` value. If no `z-index` is set on your elements then the default behaviour is that document source order dictates the Z axis. This means that elements further down the document sit on top of elements that appear before them.

In normal flow, if you set a specific value for `z-index` and it isn't working, you need to set the element's `position` value to anything other than `static`. This is a common place where people struggle with `z-index`.

This isn't the case if you are in a flexbox or grid context, though, because you can modify the z-index of flex or grid items without adding `position: relative`.

## Negative z-index <a href="#negative-z-index" class="w-headline-link">#</a>

To set an element _behind_ another element, add a negative value for `z-index`.

    .my-element {
      background: rgb(232 240 254 / 0.4);
    }

    .my-element .child {
      position: relative;
       z-index: -1;
    }

As long as `.my-element` has the initial value for `z-index` of `auto`, the `.child` element will sit behind it.

Add the following CSS to `.my-element`, and the `.child` element will not sit behind it.

    .my-element {
      position: relative;
      z-index: 0;
      background: rgb(232 240 254 / 0.4);
    }

Because `.my-element` now has a `position` value that's not `static` and a `z-index` value that's not `auto`, it has created a new **stacking context**. This means that even if you set `.child` to have a `z-index` of `-999`, it would still not sit behind `.my-parent`.

## Stacking context <a href="#stacking-context" class="w-headline-link">#</a>

A stacking context is a group of elements that have a common parent and move up and down the z axis together.

In this example, the first parent element has a `z-index` of `1`, so creates a new stacking context. Its child element has a `z-index` of `999`. Next to this parent, there is another parent element with one child. The parent has a `z-index` of `2` and the child element also has a `z-index` of `2`. Because both parents create a stacking context, the `z-index` of all children is based on that of their parent.

The `z-index` of elements inside of a stacking context are always relative to the parent's current order in its own stacking context.

The `<html>` element is a stacking context itself and nothing can ever go behind it. You can put stuff behind the `<body>` until you create a stacking context with it.

## Creating a stacking context <a href="#creating-a-stacking-context" class="w-headline-link">#</a>

You don't need to apply `z-index` and `position` to create a new [stacking context](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context). You can create a new stacking context by adding a value for properties which create a new composite layer such as `opacity`, `will-change` and `transform`. You can [see a full list of properties here](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context).

To explain what a composite layer is, imagine a web page is a canvas. A browser takes your HTML and CSS and uses these to work out how big to make the canvas. It then paints the page on this canvas. If an element was to change—say, it changes position—the browser then has to go back and re-work out what to paint.

To help with performance, the browser creates new composite layers which are layered on top of the canvas. These are a bit like post-it notes: moving one around and changing it doesn't have a huge impact on the overall canvas. A new composite layer is created for elements with `opacity`, `transform` and `will-change` because these are very likely to change, so the browser makes sure that change is performant as possible by using the GPU to apply style adjustments.

You can also create a stacking context by adding a `filter` and setting `backface-visibility: hidden`.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Forcing layers](https://surma.dev/things/forcing-layers/)
- [Animations Guide: Force layer creation](https://web.dev/animations-guide/#force)
- [Understanding z-index](https://ishadeed.com/article/understanding-z-index/)

Test your knowledge of z-index

    <section>
      <article>1</article>
      <article>2</article>
      <article>3</article>
      <article>4</article>
    </section>

Which article is on top by default?

<span data-role="option">1</span> <span data-role="option">2</span> <span data-role="option">3</span> <span data-role="option">4</span>

It's in the very back.

Try again!

Try again!

Last in the document sits on top yep!

If z-index isn't working, what property should you inspect on your element?

<span data-role="option">`display`</span> <span data-role="option">`relative`</span> <span data-role="option">`position`</span> <span data-role="option">`animation`</span>

Not the likely property for why z-index isn't working.

This is a CSS value, not a property.

Make sure this is set to something other than `static`.

Not the likely property for why z-index isn't working.

Do flexbox and grid need `position: relative`?

<span data-role="option">Yes</span> <span data-role="option">No</span>

These display types do not need it.

Using z-index inside a flexbox or grid layout will work without `position: relative`.

<a href="/learn/css/focus/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">017</span>

Focus

<a href="/learn/css/functions/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">019</span>

Functions

CSS has a range of inbuilt functions. In this module you will find out about some of the key functions, and how to use them.

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
