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

-   <a href="#numbers" class="toc__anchor">Numbers</a>
-   <a href="#percentages" class="toc__anchor">Percentages</a>
-   <a href="#dimensions-and-lengths" class="toc__anchor">Dimensions and lengths</a>
    -   <a href="#absolute-lengths" class="toc__anchor">Absolute lengths</a>
    -   <a href="#relative-lengths" class="toc__anchor">Relative lengths</a>
-   <a href="#miscellaneous-units" class="toc__anchor">Miscellaneous units</a>
    -   <a href="#angle-units" class="toc__anchor">Angle units</a>
-   <a href="#resources" class="toc__anchor">Resources</a>

007

Sizing Units
============

In this module find out how to size elements using CSS, working with the flexible medium of the web.

On this page

-   <a href="#numbers" class="toc__anchor">Numbers</a>
-   <a href="#percentages" class="toc__anchor">Percentages</a>
-   <a href="#dimensions-and-lengths" class="toc__anchor">Dimensions and lengths</a>
    -   <a href="#absolute-lengths" class="toc__anchor">Absolute lengths</a>
    -   <a href="#relative-lengths" class="toc__anchor">Relative lengths</a>
-   <a href="#miscellaneous-units" class="toc__anchor">Miscellaneous units</a>
    -   <a href="#angle-units" class="toc__anchor">Angle units</a>
-   <a href="#resources" class="toc__anchor">Resources</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 008: Sizing Units

The web is a responsive medium, but sometimes you want to control its dimensions to improve the overall interface quality. A good example of this is limiting line lengths to improve readability. How would you do that in a flexible medium like the web?

For this case, you can use a `ch` unit, which is equal to the width of a "0" character in the rendered font at its computed size. This unit allows you to limit the width of text with a unit that's designed to size text, which in turn, allows predictable control regardless of the size of that text. The `ch` unit is one of a handful of units that are helpful for specific contexts like this example.

Numbers <a href="#numbers" class="w-headline-link">#</a>
--------------------------------------------------------

Numbers are used to define `opacity`, `line-height` and even for color channel values in `rgb`. Numbers are unitless integers (1, 2, 3, 100) and decimals (.1, .2, .3).

Numbers have meaning depending on their context. For example, when defining `line-height`, a number is representative of a ratio if you define it without a supporting unit:

    p {
      font-size: 24px;
      line-height: 1.5;
    }

In this example, `1.5` is equal to **150%** of the `p` element's **computed pixel font size**. This means that if the `p` has a `font-size` of `24px`, the line height will be computed as `36px`.

It's a good idea to use a unitless value for `line-height`, rather than specifying a unit. As you learned in the [inheritance module](/learn/css/inheritance), `font-size` can be inherited. Defining a unitless `line-height` keeps the line-height relative to the font size. This provides a better experience than, say, `line-height: 15px`, which will not change and might look strange with certain font sizes.

Numbers can also be used in the following places:

-   When setting values for filters: `filter: sepia(0.5)` applies a `50%` sepia filter to the element.
-   When setting opacity: `opacity: 0.5` applies a `50%` opacity.
-   In color channels: `rgb(50, 50, 50)`, where the values 0-255 are acceptable to set a color value. [See color lesson](/learn/css/color).
-   To transform an element: `transform: scale(1.2)` scales the element by 120% of its initial size.

Percentages <a href="#percentages" class="w-headline-link">#</a>
----------------------------------------------------------------

When using a percentage in CSS you need to know how the percentage is calculated. For example,`width` is calculated as a percentage of the width of the parent element.

    div {
      width: 300px;
      height: 100px;
    }

    div p {
      width: 50%; /* calculated: 150px */
    }

In the above example, the width of `div p` is `150px`.

If you set `margin` or `padding` as a percentage, they will be a portion of the **parent element's width**, regardless of direction.

    div {
      width: 300px;
      height: 100px;
    }

    div p {
      margin-top: 50%; /* calculated: 150px */
      padding-left: 50%; /* calculated: 150px */
    }

In the above snippet, both the `margin-top` and `padding-left` will compute to `150px`.

    div {
      width: 300px;
      height: 100px;
    }

    div p {
      width: 50%; /* calculated: 150px */
      transform: translateX(10%); /* calculated: 15px */
    }

If you set a `transform` value as a percentage, it is based on the element with the transform set. In this example, the `p` has a `translateX` value of `10%` and a `width` of `50%`. First, calculate what the width will be: `150px` because it is **50% of its parent's width**. Then, take `10%` of `150px`, which is `15px`.

**Key Term**: The transform property allows you alter an element's appearance and position by rotating, skewing, scaling and translating it. This can be done in a 2D and 3D space.

Dimensions and lengths <a href="#dimensions-and-lengths" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------

If you attach a unit to a number, it becomes a dimension. For example, `1rem` is a dimension. In this context, the unit that is attached to a number is referred to in specifications as a dimension token. Lengths are **dimensions that refer to distance** and they can either be absolute or relative.

### Absolute lengths <a href="#absolute-lengths" class="w-headline-link">#</a>

All absolute lengths resolve against the same base, making them predictable wherever they're used in your CSS. For example, if you use `cm` to size your element and then print, it should be accurate if you compared it to a ruler.

    div {
      width: 10cm;
      height: 5cm;
      background: black;
    }

If you printed this page, the `div` would print as a 10x5cm black rectangle. Keep in mind, CSS is used not only for digital content, but also to style print content. Absolute lengths can really come in handy when designing for print.

<table><thead><tr class="header"><th>Unit</th><th>Name</th><th>Equivalent to</th></tr></thead><tbody><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#cm">cm</a></td><td>Centimeters</td><td>1cm = 96px/2.54</td></tr><tr class="even"><td><a href="https://www.w3.org/TR/css-values-4/#mm">mm</a></td><td>Millimeters</td><td>1mm = 1/10th of 1cm</td></tr><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#q">Q</a></td><td>Quarter-millimeters</td><td>1Q = 1/40th of 1cm</td></tr><tr class="even"><td><a href="https://www.w3.org/TR/css-values-4/#in">in</a></td><td>Inches</td><td>1in = 2.54cm = 96px</td></tr><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#pc">pc</a></td><td>Picas</td><td>1pc = 1/6th of 1in</td></tr><tr class="even"><td><a href="https://www.w3.org/TR/css-values-4/#pt">pt</a></td><td>Points</td><td>1pt = 1/72th of 1in</td></tr><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#px">px</a></td><td>Pixels</td><td>1px = 1/96th of 1in</td></tr></tbody></table>

### Relative lengths <a href="#relative-lengths" class="w-headline-link">#</a>

A relative length is calculated against a base value, much like a percentage. The difference between these and percentages is that you can contextually size elements. This means that CSS has units such as `ch` that use the text size as a basis, and `vw` which is based on the width of the viewport (your browser window). Relative lengths are particularly useful on the web due to its responsive nature.

#### Font-size-relative units <a href="#font-size-relative-units" class="w-headline-link">#</a>

CSS provides helpful units that are relative to the size of elements of rendered typography, such as the size of the text itself (`em` units) or width of the typefaces characters (`ch` units).

<table><thead><tr class="header"><th>unit</th><th>relative to:</th></tr></thead><tbody><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#em">em</a></td><td>Relative to the font size, i.e. 1.5em will be 50% larger than the base computed font size of its parent. (Historically, the height of the capital letter "M").</td></tr><tr class="even"><td><a href="https://www.w3.org/TR/css-values-4/#ex">ex</a></td><td>Heuristic to determine whether to use the x-height, a letter "x", or `.5em` in the current computed font size of the element.</td></tr><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#cap">cap</a></td><td>Height of the capital letters in the current computed font size of the element.</td></tr><tr class="even"><td><a href="https://www.w3.org/TR/css-values-4/#ch">ch</a></td><td>Average <a href="https://www.w3.org/TR/css-values-4/#length-advance-measure">character advance</a> of a narrow glyph in the element's font (represented by the "0" glyph).</td></tr><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#ic">ic</a></td><td>Average <a href="https://www.w3.org/TR/css-values-4/#length-advance-measure">character advance</a> of a full width glyph in the element's font, as represented by the "水" (CJK water ideograph, U+6C34) glyph.</td></tr><tr class="even"><td><a href="https://www.w3.org/TR/css-values-4/#rem">rem</a></td><td>Font size of the root element (default is 16px).</td></tr><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#lh">lh</a></td><td>Line height of the element.</td></tr><tr class="even"><td><a href="https://www.w3.org/TR/css-values-4/#rlh">rlh</a></td><td>Line height of the root element.</td></tr></tbody></table>

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ttaikDgwEC572lrGgWlG.svg" width="800" height="203" /></figure>#### Viewport-relative units <a href="#viewport-relative-units" class="w-headline-link">#</a>

You can use the dimensions of the viewport (browser window) as a relative basis. These units portion up the available viewport space.

<table><thead><tr class="header"><th>unit</th><th>relative to</th></tr></thead><tbody><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#vw">vw</a></td><td>1% of viewport's width. People use this unit to do cool font tricks, like resizing a header font based on the width of the page so as the user resizes, the font will also resize.</td></tr><tr class="even"><td><a href="https://www.w3.org/TR/css-values-4/#vh">vh</a></td><td>1% of viewport's height. You can use this to arrange items in a UI, if you have a footer toolbar for example.</td></tr><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#vi">vi</a></td><td>1% of viewport's size in the root element's <a href="https://www.w3.org/TR/css-writing-modes-4/#inline-axis">inline axis</a>. Axis refers to writing modes. In horizontal writing modes like English, the inline axis is horizontal. In vertical writing modes like some Japanese typefaces, the inline axis runs top to bottom.</td></tr><tr class="even"><td><a href="https://www.w3.org/TR/css-values-4/#vb">vb</a></td><td>1% of viewport's size in the root element's <a href="https://www.w3.org/TR/css-writing-modes-4/#block-axis">block axis</a>. For the block axis, this would be the directionality of the language. LTR languages like English would have a vertical block axis, since English language readers parse the page from top to bottom. A vertical writing mode has a horizontal block axis.</td></tr><tr class="odd"><td><a href="https://www.w3.org/TR/css-values-4/#vmin">vmin</a></td><td>1% of the viewport's smaller dimension.</td></tr><tr class="even"><td><a href="https://www.w3.org/TR/css-values-4/#vmax">vmax</a></td><td>1% of the viewport's larger dimension.</td></tr></tbody></table>

    div {
      width: 10vw;
    }

    p {
      max-width: 60ch;
    }

In this example, the `div` will be 10% of the viewport's width because `1vw` is **1% of the viewport width**. The `p` element has a `max-width` of `60ch` which means it can't exceed the width of 60 "0" characters in the calculated font and size.

**Objective**:

By sizing text with relative units like `em` or `rem`, rather than an absolute unit, like `px`, the size of your text can respond to user preferences. This can include the system font size or parent element's font size, such as the `<body>`. The base size of the `em` is the element's parent and the base size of the `rem` is the base font size of the document.

If you don't define a `font-size` on your `html` element, this user-preferred system font size will be honoured if you use relative lengths, such as `em` and `rem`. If you use `px` units for sizing text, this preference will be ignored.

Miscellaneous units <a href="#miscellaneous-units" class="w-headline-link">#</a>
--------------------------------------------------------------------------------

There are some other units which have been specified to deal with particular types of values.

### Angle units <a href="#angle-units" class="w-headline-link">#</a>

In the [color module](/learn/css/color/), we looked at **angle units**, which are helpful for defining degree values, such as the hue in `hsl`. They are also useful for rotating elements within transform functions.

    div {
      width: 150px;
      height: 150px;
      transform: rotate(60deg);
    }

Using the `deg` angle unit, you can rotate a `div` 90° on its center axis.

    div {
      background-image: url('a-low-resolution-image.jpg');
    }

    @media (-webkit-min-device-pixel-ratio: 2), (min-resolution: 192dpi) {
      div {
        background-image: url('a-high-resolution-image.jpg');
      }
    }

Other angle units include `rad` (radians), `grad` (gradians), and `turn` units, which represent a part of an angle, where `1turn` = `360deg`, and `0.5turn` = `180deg`.

#### Resolution units <a href="#resolution-units" class="w-headline-link">#</a>

In the previous example the value of `min-resolution` is `192dpi`. The `dpi` unit stands for **dots per inch**. A useful context for this is detecting very high resolution screens, such as Retina displays in a media query and serving up a higher resolution image.

Test your knowledge of sizing

Which of the following are valid dimensions?

<span data-role="option">cm</span> <span data-role="option">ui</span> <span data-role="option">in</span> <span data-role="option">8th</span> <span data-role="option">px</span> <span data-role="option">ch</span> <span data-role="option">ux</span> <span data-role="option">em</span> <span data-role="option">ex</span>

Centimeters, a valid absolute dimension.

User interface is not a dimension in CSS.

Inches, a valid absolute dimension.

Not a CSS dimension

Pixels, a valid absolute dimension.

Character units, a valid relative dimension.

User experience is not a dimension in CSS.

Letter 'M' units, a valid relative dimension.

Letter 'x' units, a valid relative dimension.

How are absolute and relative units different?

<span data-role="option">Absolute values can't change but relative units can</span> <span data-role="option">An absolute length is calculated against a single shared base value, where a relative unit is compared against a base value that can change.</span>

Absolute values can change, but the base they calculate against can't.

Relative units are more adaptive and fluid because of their contextual awareness, but there's a power and predictability to absolute units that can be foundational for certain designs.

Viewport units are absolute.

<span data-role="option">True</span> <span data-role="option">False</span>

They may feel absolute, but they're relative to a viewport, which could be an iframe or webview, and isn't always representative of a device screen size.

They are relative to the document window they were created in, which may or may not be the same as a device screen.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [CSS Spec Values and Units Level 4](https://www.w3.org/TR/css-values-4)
-   [Sizing and Units on MDN](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Values_and_units)
-   [All About Ems](https://learn.scannerlicker.net/2014/07/31/so-how-much-is-an-em/)
-   [A percentages explainer](https://wattenberger.com/blog/css-percents)

<a href="/learn/css/color/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">006</span>

Color

<a href="/learn/css/layout/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">008</span>

Layout

An overview of the various layout methods you have to choose from when building a component or page layout.

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
