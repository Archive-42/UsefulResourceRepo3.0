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

- <a href="#linear-gradient" class="toc__anchor">Linear gradient</a>
- <a href="#radial-gradient" class="toc__anchor">Radial gradient</a>
- <a href="#conic-gradient" class="toc__anchor">Conic gradient</a>
- <a href="#repeating-and-mixing" class="toc__anchor">Repeating and mixing</a>
- <a href="#resources" class="toc__anchor">Resources</a>

020

# Gradients

In this module you will find out how to use the various types of gradients available in CSS. Gradients can be used to create a whole host of useful effects, without needing to create an image using a graphics application.

On this page

- <a href="#linear-gradient" class="toc__anchor">Linear gradient</a>
- <a href="#radial-gradient" class="toc__anchor">Radial gradient</a>
- <a href="#conic-gradient" class="toc__anchor">Conic gradient</a>
- <a href="#repeating-and-mixing" class="toc__anchor">Repeating and mixing</a>
- <a href="#resources" class="toc__anchor">Resources</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 021: Gradients

Imagine you've got a site to build and at the top, there's an intro with a heading, summary and a button. The designer has handed over a design which has a purple background for this intro. The only problem is the background features two shades of purple as a gradient. How do you do this?

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/0T5kGhQWJTLUclxSWipH.svg" alt="A dark to light purple gradient background with heading, paragraph and link" width="800" height="411" />

You might initially think that you're going to need to export an image from your design tool for this, but you can use a [`linear-gradient`](<https://developer.mozilla.org/en-US/docs/Web/CSS/linear-gradient()>) instead.

A gradient is an image and can be used anywhere images can be used, but it's created with CSS and is made up with colors, numbers and angles. CSS gradients allow you to create anything from a smooth gradient between two colors, right up to impressive artwork by mixing and repeating multiple gradients.

## Linear gradient <a href="#linear-gradient" class="w-headline-link">#</a>

The [`linear-gradient()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/linear-gradient()>) function generates an image of two or more colors, progressively. It takes multiple arguments, but in its simplest configuration, you can pass some colors like this and it will automatically split them evenly, while blending them.

    .my-element {
       background: linear-gradient(black, white);
    }

You can also pass an angle or keywords that represent an angle. If you choose to use keywords, specify a direction after the `to` keyword. This means if you want a gradient that is black and white, that runs from left (black) to right (white), you would specify the angle as `to right` as the first argument.

    .my-element {
        background: linear-gradient(to right, black, white);
    }

A color stop value defined where a color stops and mixes with its neighbors. For a gradient starting with a dark shade of red running at a 45deg angle, at 30% of the size of the gradient changing to a lighter red: it looks like this.

    .my-element {
        background: linear-gradient(45deg, darkred 30%, crimson);
    }

You can add as many colors and color stops as you like in a `linear-gradient()`, and you can layer gradients on top of each other by separating each gradient with a comma.

## Radial gradient <a href="#radial-gradient" class="w-headline-link">#</a>

To create a gradient that radiates in a circular fashion, the [`radial-gradient()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/radial-gradient()>) function steps in to help. It's similar to `linear-gradient()`, but instead of specifying an angle, you optionally specify a position and ending shape. If you just specify colors, the `radial-gradient()` will auto-select the position as `center` and select either a circle or ellipse, depending on the size of the box.

    .my-element {
      background: radial-gradient(white, black);
    }

The gradient's position is similar to `background-position` using keywords and/or number values. The size of the radial gradient determines the size of the gradient's ending shape (circle or ellipse) and by default will be `farthest-corner`, which means it exactly meets the farthest corner of the box from the center. You can also use the following keywords:

- `closest-corner` will meet the closest corner to the center of the gradient.
- `closest-side` will meet the side of the box closest to the center of the gradient.
- `farthest-side` will do the opposite to `closest-side`.

You can add as many color stops as you like, just like with the `linear-gradient`. Likewise, you can add as many `radial-gradients` as you like too.

## Conic gradient <a href="#conic-gradient" class="w-headline-link">#</a>

A conic gradient has a center point in your box and starts from the top (by default), and goes around in a 360 degree circle.

    .my-element {
        background: conic-gradient(white, black);
    }

The [`conic-gradient()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/conic-gradient()>) function accepts position and angle arguments.

By default, the angle is 0 degrees which starts at the top, in the center. If you were to set the angle to be `45deg`, it would be the top right corner. The angle argument accepts any type of angle value, like the linear and radial gradients.

The position is center by default. As with radial and linear gradients, positioning can be keyword-based, or it can be defined with numeric values.

You can add as many color stops as you want, like with other gradient types. A good use case for this capability, with conic gradients is rendering pie charts with CSS.

## Repeating and mixing <a href="#repeating-and-mixing" class="w-headline-link">#</a>

Each type of gradient has a repeating type, too. These are [`repeating-linear-gradient()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/repeating-linear-gradient()>), [`repeating-radial-gradient()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/repeating-radial-gradient()>) and [`repeating-conic-gradient()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/repeating-conic-gradient()>). They are similar to the non-repeating functions and take the same arguments. The difference is that if the defined gradient can be repeated to fill the box, based on both of their sizes, it will.

If your gradient doesn't appear to be repeating, you probably haven't set a length for one of the color stops. For example, you can create a striped background with a `repeating-linear-gradient` by setting color stop lengths.

    .my-element {
      background: repeating-linear-gradient(
        45deg,
        red,
        red 30px,
        white 30px,
        white 60px
      );
    }

You can also mix gradient functions on `background` properties, as well as defining as many gradients as you like, just like you would with a background image. For example, you can mix multiple linear-gradients together, or two linear-gradients with a radial gradient.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Conic.css](https://www.conic.style/) - a useful collection of conic gradients
- [MDN guide to gradients](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Images/Using_CSS_gradients)
- [Gradient generator](https://www.colorzilla.com/gradient-editor/)

Test your knowledge of gradients

What is the _minimum_ number of colors required to create a gradient?

<span data-role="option">1</span> <span data-role="option">2</span> <span data-role="option">3</span> <span data-role="option">4</span>

Try again!

They could be the same color and appear solid, but yes, at least 2 colors are required.

Try again!

Try again!

Elements can have multiple gradients as a background?

<span data-role="option">True</span> <span data-role="option">False</span>

The `background-image` property allows many gradients, just separate them with a comma.

Oh, but they can!

<a href="/learn/css/functions/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">019</span>

Functions

<a href="/learn/css/animations/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">021</span>

Animations

Animation is a great way to highlight interactive elements, and add interest and fun to your designs. In this module find out how to add and control animation effects with CSS.

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
