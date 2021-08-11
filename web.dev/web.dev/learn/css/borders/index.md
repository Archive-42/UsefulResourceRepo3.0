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

-   <a href="#border-properties" class="toc__anchor">Border properties</a>
    -   <a href="#style" class="toc__anchor">Style</a>
    -   <a href="#shorthand" class="toc__anchor">Shorthand</a>
    -   <a href="#color" class="toc__anchor">Color</a>
    -   <a href="#width" class="toc__anchor">Width</a>
-   <a href="#logical-properties" class="toc__anchor">Logical properties</a>
-   <a href="#border-radius" class="toc__anchor">Border radius</a>
-   <a href="#border-images" class="toc__anchor">Border images</a>
    -   <a href="#border-image-source" class="toc__anchor">border-image-source</a>
    -   <a href="#border-image-slice" class="toc__anchor">border-image-slice</a>
    -   <a href="#border-image-repeat" class="toc__anchor">border-image-repeat</a>

015

Borders
=======

A border provides a frame for your boxes. In this module find out how to change the size, style and color of borders using CSS.

On this page

-   <a href="#border-properties" class="toc__anchor">Border properties</a>
    -   <a href="#style" class="toc__anchor">Style</a>
    -   <a href="#shorthand" class="toc__anchor">Shorthand</a>
    -   <a href="#color" class="toc__anchor">Color</a>
    -   <a href="#width" class="toc__anchor">Width</a>
-   <a href="#logical-properties" class="toc__anchor">Logical properties</a>
-   <a href="#border-radius" class="toc__anchor">Border radius</a>
-   <a href="#border-images" class="toc__anchor">Border images</a>
    -   <a href="#border-image-source" class="toc__anchor">border-image-source</a>
    -   <a href="#border-image-slice" class="toc__anchor">border-image-slice</a>
    -   <a href="#border-image-repeat" class="toc__anchor">border-image-repeat</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 016: Borders

In the [box model](/learn/css/box-model) module, we considered a frame analogy to describe each section of the box model.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format" alt="Three picture frames next to each other. The middle frame has the sections of the box model over the top of it" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=1600 1600w" width="800" height="562" />

The border box is the frame of your boxes, and the `border` properties give you a huge array of options to create that frame in nearly any style that you can think of.

Border properties <a href="#border-properties" class="w-headline-link">#</a>
----------------------------------------------------------------------------

The individual `border` properties provide a way to style the various parts of a border.

### Style <a href="#style" class="w-headline-link">#</a>

For a border to appear, you have to define the [`border-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-style). There's a few options to choose from:

When using the `ridge`, `inset`, `outset` and `groove` styles, the browser will darken the border color for the second shown color to provide contrast and depth. This behaviour can vary between browsers, especially for dark colors such as `black`. In Chrome, these border styles will appear to be solid and in Firefox, they will be lightened to then provide a darker second color.

Browser behaviour can vary for other border styles too, so it's important to test your site in different browsers. A common example of this difference is how each browser renders the `dotted` and `dashed` styles.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format" alt="Borders displayed in Chrome, Firefox, and Safari." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ybLca9jmTgUtltTwfIpt.jpg?auto=format&amp;w=1600 1600w" width="800" height="489" /><figcaption>Borders displayed in Chrome, Firefox, and Safari.</figcaption></figure>To set border style on each side of your box, you can use [`border-top-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-top-style), [`border-right-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-right-style), [`border-left-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-left-style), and [`border-bottom-style`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-bottom-style).

### Shorthand <a href="#shorthand" class="w-headline-link">#</a>

As with `margin` and `padding`, you can use the [`border`](https://developer.mozilla.org/en-US/docs/Web/CSS/border) shorthand property to define all the parts of your border in one declaration.

    .my-element {
     border: 1px solid red;
    }

The order of values in the `border` shorthand are `border-width`, `border-style` and then, `border-color`.

### Color <a href="#color" class="w-headline-link">#</a>

You can set color on all sides of your box or on each individual side with [`border-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-color). By default, it uses the box's current text color: `currentColor`. This means that if you only declare border properties, like width, the color will be that computed value unless you explicitly set it.

    .my-element {
     color: blue;
      border: solid; /* Will be a blue border */
    }

    .my-element {
     color: blue;
      border: solid yellow;
    }

To set a border color on each side of your box, use [`border-top-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-top-color), [`border-right-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-right-color), [`border-left-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-left-color) and [`border-bottom-color`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-bottom-color).

### Width <a href="#width" class="w-headline-link">#</a>

The width of a border is how thick the line is, and is controlled by [`border-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-width). The default border width is `medium`. This won't be visible unless you define a style, though. You can use other named widths such as `thin` and `thick`.

The `border-width` properties also accept a length unit such as `px`, `em`, `rem` or `%`. To set border width on each side of your box, use [`border-top-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-top-width), [`border-right-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-right-width), [`border-left-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-left-width) and [`border-bottom-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-bottom-width).

Logical properties <a href="#logical-properties" class="w-headline-link">#</a>
------------------------------------------------------------------------------

In the [Logical Properties](/learn/css/logical-properties) module you discovered how to refer to block flow and inline flow, rather than explicit top, right, bottom or left sides.

You have this capability with borders, too:

    .my-element {
      border: 2px dotted;
       border-inline-end: 2px solid red;
    }

In this example, `.my-element` has all sides defined as having a `2px`, dotted border that is the current text color. The `inline-end` border is then defined as `2px`, solid and red. This means that in left-to-right languages—like English— the red border will be on the right side of the box. In right-to-left languages—like Arabic— the red border will be on the left side of the box.

Browser support is varied for logical properties in borders, so make sure you check support before using.

Border radius <a href="#border-radius" class="w-headline-link">#</a>
--------------------------------------------------------------------

To give a box rounded corners use the [`border-radius`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-radius) property.

    .my-element {
       border-radius: 1em;
    }

This shorthand adds a consistent border to each corner of your box. As with the other border properties, you can define the border radius for each side with [`border-top-left-radius`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-top-left-radius), [`border-top-right-radius`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-top-right-radius), [`border-bottom-right-radius`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-bottom-right-radius) and [`border-bottom-left-radius`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-bottom-left-radius).

You can also specify each corner's radius in the shorthand, which follows the order: top left, top right, bottom right then bottom left.

    .my-element {
      border-radius: 1em 2em 3em 4em;
    }

By defining a single value for a corner, you are using another shorthand because a border radius is split into two parts: the vertical and horizontal sides. This means that when you set `border-top-left-radius: 1em`, you are setting the top-left-**top** radius and the top-left-**left** radius.

You can define both properties, per corner like this:

    .my-element {
     border-top-left-radius: 1em 2em;
    }

This adds a `border-top-left-top` value of `1em`, and a border top-left-left value of `2em`. This converts the top left border radius into an elliptical radius, rather than the default circular radius.

You can define these values in the `border-radius` shorthand, using a `/` to define the elliptical values, after the standard values. This enables you to get creative and make some complex shapes.

    .my-element {
        border: 2px solid;
      border-radius: 95px 155px 148px 103px / 48px 95px 130px 203px;
    }

Border images <a href="#border-images" class="w-headline-link">#</a>
--------------------------------------------------------------------

You don't just have to use a stroke-based border in CSS. You can also use any type of image, using [`border-image`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-image). This shorthand property allows you to set the source image, how that image is sliced, the image width, how far the border is outset from the edge and how it should repeat.

    .my-element {
      border-image-source: url(https://assets.codepen.io/174183/border-image-frame.jpg);
      border-image-slice: 61 58 51 48;
      border-image-width: 20px 20px 20px 20px;
      border-image-outset: 0px 0px 0px 0px;
      border-image-repeat: stretch stretch;
    }

The [`border-image-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-image-width) property is like `border-width`: it is how you set the width of your border image. The [`border-image-outset`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-image-outset) property lets you set the distance between your border image and the box that it wraps around.

### `border-image-source` <a href="#border-image-source" class="w-headline-link">#</a>

The [`border-image-source`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-image-source) (source of the border image) can be a `url` for any valid image, which includes CSS gradients.

    .my-element {
     border-image-source: url('path/to/image.png');
    }

    .my-element {
     border-image-source: linear-gradient(to bottom, #000, #fff);
    }

### `border-image-slice` <a href="#border-image-slice" class="w-headline-link">#</a>

The [`border-image-slice`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-image-slice) property is a useful property that allows you to slice an image into 9 parts, made up of 4 split lines. It works like the `margin` shorthand where you define the top, right, bottom and left **offset value**.

    .my-element {
        border-image: url('image.jpg');
        border-image-slice: 61 58 51 48;
    }

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format" alt="The image used in the demo with the four slices shown with blue lines" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/WETsTwhFSfl30VfyfMTA.png?auto=format&amp;w=1600 1600w" width="800" height="380" />

With the offset values defined, you now have 9 sections of the image: 4 corners, 4 edges and a middle section. The corners are applied to the corners of the element with the border image. The edges are applied to the edges of that element. The [`border-image-repeat`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-image-repeat) property defines how those edges fill their space and the [`border-image-width`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-image-width) property controls the size of the slices.

Lastly, the `fill` keyword determines whether the middle section, left by the slicing, is used as the element's background image or not.

### `border-image-repeat` <a href="#border-image-repeat" class="w-headline-link">#</a>

[`border-image-repeat`](https://developer.mozilla.org/en-US/docs/Web/CSS/border-image-repeat) is how you instruct CSS how you would like your border image to repeat. It works the same as `background-repeat`.

-   The initial value is `stretch`, which stretches the source image to fill available space where possible.
-   The `repeat` value tiles the source image's edges as many times as possible, and may clip the edge regions to achieve this.
-   The `round` value is the same as repeat, but instead of clipping the image edge regions to fit as many as possible, it stretches the image as well as repeating it to achieve a seamless repeat
-   The `space` value is again, the same as repeat, but this value adds space between each edge region to create a seamless pattern.

Test your knowledge of borders

Which is the default border color?

<span data-role="option">`black`</span> <span data-role="option">`white`</span> <span data-role="option">`currentColor`</span> <span data-role="option">`historicColor`</span>

Try again!

Try again!

This special CSS value will represent the computed `text-color` value, and is the default border color.

This is made up. Try again!

    .my-element {
      border: solid hotpink;
    }

What is the default width of a border?

<span data-role="option">`1px`</span> <span data-role="option">`medium`</span> <span data-role="option">`solid`</span>

Try again!

🎉

This is a `border-style` value, not a `border-width` value.

`border-inline: 1px solid` would...

<span data-role="option">put borders on the left and right (in Latin layouts).</span> <span data-role="option">put borders on the top and bottom (in Latin layouts).</span> <span data-role="option">put borders on the inside.</span> <span data-role="option">put borders on the first line.</span>

🎉

In a Latin layout like English, `border-block` would be the top and bottom.

Try again!

Try again!

<a href="/learn/css/pseudo-classes/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">014</span>

Pseudo-classes

<a href="/learn/css/shadows/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">016</span>

Shadows

There are a number of ways to add shadows to text and elements in CSS. In this module you'll learn how to use each option, and the tasks they were designed for.

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
