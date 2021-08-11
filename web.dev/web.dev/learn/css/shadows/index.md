<a href="#main" class="skip-link w-button">Skip to main</a>

<span class="w-tooltip w-tooltip--left">Open menu</span>

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

-   -   [Learn](/learn/)
-   [Learn CSS!](/learn/css/)

Share

On this page

-   <a href="#box-shadow" class="toc__anchor">Box shadow</a>
    -   <a href="#multiple-shadows" class="toc__anchor">Multiple shadows</a>
    -   <a href="#properties-affecting-box-shadow" class="toc__anchor">Properties affecting box-shadow</a>
-   <a href="#text-shadow" class="toc__anchor">Text shadow</a>
    -   <a href="#multiple-shadows-2" class="toc__anchor">Multiple shadows</a>
-   <a href="#drop-shadow" class="toc__anchor">Drop shadow</a>

016

Shadows
=======

There are a number of ways to add shadows to text and elements in CSS. In this module you'll learn how to use each option, and the tasks they were designed for.

On this page

-   <a href="#box-shadow" class="toc__anchor">Box shadow</a>
    -   <a href="#multiple-shadows" class="toc__anchor">Multiple shadows</a>
    -   <a href="#properties-affecting-box-shadow" class="toc__anchor">Properties affecting box-shadow</a>
-   <a href="#text-shadow" class="toc__anchor">Text shadow</a>
    -   <a href="#multiple-shadows-2" class="toc__anchor">Multiple shadows</a>
-   <a href="#drop-shadow" class="toc__anchor">Drop shadow</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 017: Shadows

Say you've been sent a design to build and in that design there's a picture of a t-shirt, cut out, with a drop shadow. The designer tells you that the product image is dynamic and can be updated via the content management system, so the drop shadow needs to be dynamic too. Instead of a t-shirt, the image could be a visor or shorts, or any other item. How do you do that with CSS?

CSS has the [`box-shadow`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow) and [`text-shadow`](https://developer.mozilla.org/en-US/docs/Web/CSS/text-shadow) properties, but the picture isn't text, so you can't use `text-shadow`. If you use `box-shadow`, the shadow is on the surrounding box, *not* around the t-shirt.

Luckily, there is another option: the [`drop-shadow()`](https://developer.mozilla.org/en-US/docs/Web/CSS/filter-function/drop-shadow()) filter. This enables you to do exactly what the designer asked for. There are plenty of options when it comes to shadows in CSS, each designed for a different use case.

Box shadow <a href="#box-shadow" class="w-headline-link">#</a>
--------------------------------------------------------------

The `box-shadow` property is for adding shadows to the box of an HTML element. It works on block elements and inline elements.

    .my-element {
     box-shadow: 5px 5px 20px 5px #000;
    }

The order of values for `box-shadow` are as follows:

1.  **Horizontal offset**: a positive number pushes it out from the left and a negative number will push it out from the right.
2.  **Vertical offset**: a positive number pushes it down from the top, and a negative number will push it up from the bottom.
3.  **Blur radius**: a larger number produces a more blurred shadow, whereas a small number produces a sharper shadow.
4.  **Spread radius** (optional): a larger number increases the size of the shadow and a smaller number decreases it, making it the same size as the **blur radius** if it's set to 0.
5.  **Color**: [Any valid color value](/learn/css/color). If this isn't defined, the computed text color will be used.

To make a box shadow an inner shadow, rather than the default outer shadow, add an `inset` keyword **before** the other properties.

    /* Outer shadow */
    .my-element {
      box-shadow: 5px 5px 20px 5px #000;
    }

    /* Inner shadow */
    .my-element {
       box-shadow: inset 5px 5px 20px 5px #000;
    }

### Multiple shadows <a href="#multiple-shadows" class="w-headline-link">#</a>

You can add as many shadows as you like with `box-shadow`. Add a comma separated collection of value sets to achieve this:

    .my-element {
      box-shadow: 5px 5px 20px 5px darkslateblue, -5px -5px 20px 5px dodgerblue,
        inset 0px 0px 10px 2px darkslategray, inset 0px 0px 20px 10px steelblue;
    }

### Properties affecting box-shadow <a href="#properties-affecting-box-shadow" class="w-headline-link">#</a>

Adding a `border-radius` to your box will also affect the shape of the box shadow. This is because CSS is creating a shadow based on the shape of the box as if light is pointing at it.

    .my-element {
      box-shadow: 0px 0px 20px 5px darkslateblue;
      border-radius: 25px;
    }

If your box with `box-shadow` is in a container that has `overflow: hidden`, the shadow **won't** break out of that overflow either.

    <div class="my-parent">
      <div class="my-shadow">My shadow is hidden by my parent.</div>
    </div>

    .my-parent,
    .my-shadow {
      width: 250px;
      height: 250px;
    }

    .my-shadow {
      box-shadow: 0px 0px 20px 5px darkslateblue;
    }

    .my-parent {
      overflow: hidden;
    }

Text shadow <a href="#text-shadow" class="w-headline-link">#</a>
----------------------------------------------------------------

The `text-shadow` property is very similar to the `box-shadow` property. It only works on text nodes.

    .my-element {
      text-shadow: 3px 3px 3px hotpink;
    }

The values for `text-shadow` are the same as `box-shadow` and in the same order. The only difference is that `text-shadow` has no `spread` value and no `inset` keyword.

When you add a `box-shadow` it is clipped to the shape of your box, but `text-shadow` has no clipping. This means that if your text is fully or semi transparent, the shadow is visible through it.

    .my-element {
      text-shadow: 3px 3px 3px gold;
      color: rgb(0 0 0 / 70%);
    }

### Multiple shadows <a href="#multiple-shadows-2" class="w-headline-link">#</a>

You can add as many shadows as you like with `text-shadow`, just as with `box-shadow`. Add a comma separated collection of value sets, and you can create some really cool text effects, such as 3D text.

    .my-element {
      text-shadow: 1px 1px 0px white,
        2px 2px 0px firebrick;
      color: darkslategray;
    }

Drop shadow <a href="#drop-shadow" class="w-headline-link">#</a>
----------------------------------------------------------------

To achieve a drop shadow that follows any potential curves of an image, use the CSS `drop-shadow` filter. This shadow is applied to an alpha mask which makes it very useful for adding a shadow to a cutout image, as in the case in the intro of this module.

    .my-image {
      filter: drop-shadow(0px 0px 10px rgba(0 0 0 / 30%))
    }

**Key Term**: We cover CSS [filters](/learn/css/filters) in another module, but in short, filters allow you to apply multiple graphical effects to the pixels of an element.

The `drop-shadow` filter has the same values as `box-shadow` **but** the `inset` keyword and `spread` value are not allowed. You can add as many shadows as you like, by adding multiple instances of `drop-shadow` values to the `filter` property. Each shadow will use the last shadow as a positioning reference point.

Test your knowledge of shadows

Which shadow value below is unique to `box-shadow`?

<span data-role="option">Horizontal offset</span> <span data-role="option">Vertical offset</span> <span data-role="option">Blur radius</span> <span data-role="option">Spread radius</span> <span data-role="option">Color</span> <span data-role="option">`inset`</span>

Try again!

Try again!

Try again!

🎉

Try again!

Try again! `inset` is a **keyword** which is also unique to `box-shadow`.

Only 13 box shadows allowed on an element at once.

<span data-role="option">True</span> <span data-role="option">False</span>

There's no official limit.

Add as many multiple box shadows as you need.

<a href="/learn/css/borders/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">015</span>

Borders

<a href="/learn/css/focus/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">017</span>

Focus

Understand the importance of focus in your web applications. You'll find out how to manage focus, and how to make sure the path through your page works for people using a mouse, and those using the keyboard to navigate.

-   ### Contribute

    -   <a href="https://github.com/GoogleChrome/web.dev/issues/new?assignees=&amp;labels=bug&amp;template=bug_report.md&amp;title=" class="w-footer__linkbox-link">File a bug</a>
    -   <a href="https://github.com/googlechrome/web.dev" class="w-footer__linkbox-link">View source</a>

-   ### Related content

    -   <a href="https://blog.chromium.org/" class="w-footer__linkbox-link">Chrome updates</a>
    -   <a href="https://developers.google.com/web/" class="w-footer__linkbox-link">Web Fundamentals</a>
    -   <a href="https://developers.google.com/web/showcase/" class="w-footer__linkbox-link">Case studies</a>
    -   <a href="https://devwebfeed.appspot.com/" class="w-footer__linkbox-link">DevWeb Content Firehose</a>
    -   <a href="/podcasts/" class="w-footer__linkbox-link">Podcasts</a>
    -   <a href="/shows/" class="w-footer__linkbox-link">Shows</a>

-   ### Connect

    -   <a href="https://www.twitter.com/ChromiumDev" class="w-footer__linkbox-link">Twitter</a>
    -   <a href="https://www.youtube.com/user/ChromeDevelopers" class="w-footer__linkbox-link">YouTube</a>

<a href="https://developers.google.com/" class="w-footer__utility-logo-link"><img src="/images/lockup-color.png" alt="Google Developers" class="w-footer__utility-logo" width="185" height="33" /></a>

-   <a href="https://developer.chrome.com/" class="w-footer__utility-link">Chrome</a>
-   <a href="https://firebase.google.com/" class="w-footer__utility-link">Firebase</a>
-   <a href="https://cloud.google.com/" class="w-footer__utility-link">Google Cloud Platform</a>
-   <a href="https://developers.google.com/products" class="w-footer__utility-link">All products</a>

<!-- -->

-   <a href="https://policies.google.com/" class="w-footer__utility-link">Terms &amp; Privacy</a>
-   <a href="/community-guidelines/" class="w-footer__utility-link">Community Guidelines</a>

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/terms/site-policies).
