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

- <a href="#the-filter-property" class="toc__anchor">The filter property</a>
  - <a href="#blur" class="toc__anchor">blur</a>
  - <a href="#brightness" class="toc__anchor">brightness</a>
  - <a href="#contrast" class="toc__anchor">contrast</a>
  - <a href="#grayscale" class="toc__anchor">grayscale</a>
  - <a href="#invert" class="toc__anchor">invert</a>
  - <a href="#opacity" class="toc__anchor">opacity</a>
  - <a href="#saturate" class="toc__anchor">saturate</a>
  - <a href="#sepia" class="toc__anchor">sepia</a>
  - <a href="#hue-rotate" class="toc__anchor">hue-rotate</a>
  - <a href="#drop-shadow" class="toc__anchor">drop-shadow</a>
  - <a href="#url" class="toc__anchor">url</a>
- <a href="#backdrop-filter" class="toc__anchor">Backdrop filter</a>

022

# Filters

Filters in CSS mean that you can apply effects you might only think possible in a graphics application. In this module, you can discover what is available.

On this page

- <a href="#the-filter-property" class="toc__anchor">The filter property</a>
  - <a href="#blur" class="toc__anchor">blur</a>
  - <a href="#brightness" class="toc__anchor">brightness</a>
  - <a href="#contrast" class="toc__anchor">contrast</a>
  - <a href="#grayscale" class="toc__anchor">grayscale</a>
  - <a href="#invert" class="toc__anchor">invert</a>
  - <a href="#opacity" class="toc__anchor">opacity</a>
  - <a href="#saturate" class="toc__anchor">saturate</a>
  - <a href="#sepia" class="toc__anchor">sepia</a>
  - <a href="#hue-rotate" class="toc__anchor">hue-rotate</a>
  - <a href="#drop-shadow" class="toc__anchor">drop-shadow</a>
  - <a href="#url" class="toc__anchor">url</a>
- <a href="#backdrop-filter" class="toc__anchor">Backdrop filter</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 023: Filters

Say you need to build an element that's got a slightly opaque, frosted glass effect that sits over the top of an image. The text needs to be live text and not an image. How do you do that?

A combination of CSS filters and the `backdrop-filter` allow us to apply effects and blur what's needed in real time. Blur and opacity are two of many available filters, so let's have a quick run through what they all do and how to use them.

Take care when placing text over images, that the text is still readable should the filter effect not be supported in a user's browser. For example, at the moment [`backdrop-filter`](https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter) is not supported in Firefox, and so you should check that Firefox users aren't left with text they cannot easily read.

## The `filter` property <a href="#the-filter-property" class="w-headline-link">#</a>

You can apply one or many of the following filters as a value for [`filter`](https://developer.mozilla.org/en-US/docs/Web/CSS/filter). If you incorrectly apply a filter, the rest of the filters defined for `filter` will not work.

### `blur` <a href="#blur" class="w-headline-link">#</a>

This applies a gaussian blur and the only argument you can pass is a `radius`, which is [how much blur is applied](https://dbaron.org/log/20110225-blur-radius). This needs to be a length unit, like `10px`. Percentages are not accepted.

    .my-element {
     filter: blur(0.2em);
    }

### `brightness` <a href="#brightness" class="w-headline-link">#</a>

To increase or decrease the brightness of an element, use the brightness function. The brightness value is expressed as a percentage with the unchanged image being expressed as a value of 100%. A value of 0% turns the image completely black, therefore values between 0% and 100% make the image less bright. Use values over 100% to increase the brightness.

    .my-element {
        filter: brightness(80%);
    }

You can also use decimal values, instead of percentage values in filters like `brightness`. To set 80% brightness with a decimal, write `0.8`.

### `contrast` <a href="#contrast" class="w-headline-link">#</a>

Set a value between 0% and 100% to decrease or increase the contrast, respectively.

    .my-element {
      filter: contrast(160%);
    }

### `grayscale` <a href="#grayscale" class="w-headline-link">#</a>

You can apply a completely grayscale effect by using `1` as a value for `grayscale()`, or `0` to have a completely saturated element. You can also use percentage or decimal values to only apply a partial grayscale effect. If you pass no arguments, the element will be completely grayscale. If you pass a value greater than 100%, it will be capped at 100%.

    .my-element {
       filter: grayscale(80%);
    }

### `invert` <a href="#invert" class="w-headline-link">#</a>

Just like `grayscale`, you can pass `1` or `0` to the `invert()` function to turn it on or off. When it is on, the element's colors are completely inverted. You can also use percentage or decimal values to only apply a partial inversion of colors. If you don't pass any arguments into the `invert()` function, the element will be completely inverted.

    .my-element {
       filter: invert(1);
    }

### `opacity` <a href="#opacity" class="w-headline-link">#</a>

The `opacity()` filter works just like the `opacity` property, where you can pass a number or percentage to increase or reduce opacity. If you pass no arguments, the element is fully visible.

    .my-element {
     filter: opacity(0.3);
    }

### `saturate` <a href="#saturate" class="w-headline-link">#</a>

The saturate filter is very similar to the `brightness` filter and accepts the same argument: number or percentage. Instead of increasing or decreasing the brightness effect, `saturate` increases or decreases color saturation.

    .my-element {
       filter: saturate(155%);
    }

### `sepia` <a href="#sepia" class="w-headline-link">#</a>

You can add a sepia tone effect with this filter that works like `grayscale()`. The sepia tone is a photographic printing technique that converts black tones to brown tones to warm them up. You can pass a number or percentage as the argument for `sepia()` which increases or decreases the effect. Passing no arguments adds a full sepia effect (equivalent to `sepia(100%)`).

    .my-element {
      filter: sepia(70%);
    }

### `hue-rotate` <a href="#hue-rotate" class="w-headline-link">#</a>

You learned about how the hue in `hsl` references a rotation of the color wheel in the [colors lesson](/learn/css/color) and this filter works in a similar way. If you pass an angle, such as degrees or turns, it shifts the hue of all the element's colors, changing the part of the color wheel it references. If you pass no argument, it does nothing.

    .my-element {
       filter: hue-rotate(120deg);
    }

### `drop-shadow` <a href="#drop-shadow" class="w-headline-link">#</a>

You can apply a curve-hugging drop shadow like you would in a design tool, such as Photoshop with [`drop-shadow`](https://developer.mozilla.org/en-US/docs/Web/CSS/drop-shadow). This shadow is applied to an alpha mask which makes it very useful for adding a shadow to a cutout image. The `drop-shadow` filter takes a shadow parameter which contains space separated offset-x, offset-y, blur and color values. It is almost identical to `box-shadow`, but the `inset` keyword and spread value are not supported.

    .my-element {
     filter: drop-shadow(5px 5px 10px orange);
    }

Learn more about the different types of shadows in the [shadows](/learn/css/shadows) module.

### `url` <a href="#url" class="w-headline-link">#</a>

The `url` filter allows you to apply an SVG filter from a linked SVG element or file. You can [read more about SVG filters here](https://developer.mozilla.org/en-US/docs/Web/SVG/Element/filter)

## Backdrop filter <a href="#backdrop-filter" class="w-headline-link">#</a>

The [backdrop-filter](https://developer.mozilla.org/en-US/docs/Web/CSS/backdrop-filter) property accepts all of the same filter function values as `filter`. The difference between `backdrop-filter` and `filter` is that the `backdrop-filter` property only applies the filters to the background, where the `filter` property applies it to the whole element.

The example right at the start of this lesson is the perfect example, because you don't want the text to be blurred and ideally you don't want to have to add extra HTML elements. Being able to apply filters only to the backdrop enables that.

Test your knowledge of filters

Which of following are CSS filter functions?

<span data-role="option">`grayscale()`</span> <span data-role="option">`invert()`</span> <span data-role="option">`flip()`</span> <span data-role="option">`multiply()`</span> <span data-role="option">`blur()`</span> <span data-role="option">`brightness()`</span>

🎉

🎉

Try again!

Try again!

🎉

🎉

Can CSS use SVG filters?

<span data-role="option">Yes</span> <span data-role="option">No</span>

The `url()` filter function enables this

Try again!

<a href="/learn/css/animations/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">021</span>

Animations

<a href="/learn/css/blend-modes/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">023</span>

Blend Modes

Create compositional effects by mixing two or more layers, and learn how to isolate an image with a white background in this module on blend modes.

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
