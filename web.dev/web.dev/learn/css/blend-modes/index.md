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

- <a href="#what-is-a-blend-mode" class="toc__anchor">What is a blend mode?</a>
- <a href="#separable-blend-modes" class="toc__anchor">Separable blend modes</a>
  - <a href="#normal" class="toc__anchor">Normal</a>
  - <a href="#multiply" class="toc__anchor">Multiply</a>
  - <a href="#screen" class="toc__anchor">Screen</a>
  - <a href="#overlay" class="toc__anchor">Overlay</a>
  - <a href="#darken" class="toc__anchor">Darken</a>
  - <a href="#lighten" class="toc__anchor">Lighten</a>
  - <a href="#color-dodge" class="toc__anchor">Color dodge</a>
  - <a href="#color-burn" class="toc__anchor">Color burn</a>
  - <a href="#hard-light" class="toc__anchor">Hard light</a>
  - <a href="#soft-light" class="toc__anchor">Soft light</a>
  - <a href="#difference" class="toc__anchor">Difference</a>
  - <a href="#exclusion" class="toc__anchor">Exclusion</a>
- <a href="#non-separable-blend-modes" class="toc__anchor">Non-separable blend modes</a>
  - <a href="#hue" class="toc__anchor">Hue</a>
  - <a href="#saturation" class="toc__anchor">Saturation</a>
  - <a href="#color" class="toc__anchor">Color</a>
  - <a href="#luminosity" class="toc__anchor">Luminosity</a>
- <a href="#the-isolation-property" class="toc__anchor">The isolation property</a>

023

# Blend Modes

Create compositional effects by mixing two or more layers, and learn how to isolate an image with a white background in this module on blend modes.

On this page

- <a href="#what-is-a-blend-mode" class="toc__anchor">What is a blend mode?</a>
- <a href="#separable-blend-modes" class="toc__anchor">Separable blend modes</a>
  - <a href="#normal" class="toc__anchor">Normal</a>
  - <a href="#multiply" class="toc__anchor">Multiply</a>
  - <a href="#screen" class="toc__anchor">Screen</a>
  - <a href="#overlay" class="toc__anchor">Overlay</a>
  - <a href="#darken" class="toc__anchor">Darken</a>
  - <a href="#lighten" class="toc__anchor">Lighten</a>
  - <a href="#color-dodge" class="toc__anchor">Color dodge</a>
  - <a href="#color-burn" class="toc__anchor">Color burn</a>
  - <a href="#hard-light" class="toc__anchor">Hard light</a>
  - <a href="#soft-light" class="toc__anchor">Soft light</a>
  - <a href="#difference" class="toc__anchor">Difference</a>
  - <a href="#exclusion" class="toc__anchor">Exclusion</a>
- <a href="#non-separable-blend-modes" class="toc__anchor">Non-separable blend modes</a>
  - <a href="#hue" class="toc__anchor">Hue</a>
  - <a href="#saturation" class="toc__anchor">Saturation</a>
  - <a href="#color" class="toc__anchor">Color</a>
  - <a href="#luminosity" class="toc__anchor">Luminosity</a>
- <a href="#the-isolation-property" class="toc__anchor">The isolation property</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 024: Blend Modes

[Duotone](https://en.wikipedia.org/wiki/Duotone) is a popular color treatment for photography which makes an image look like it is only made up of two contrasting colors: one for highlights and the other for lowlights. How do you do this with CSS though?

Using blend modes—and other techniques you have learned about, such as [filters](/learn/css/filters) and [pseudo-elements](/learn/css/pseudo-elements)—you can apply this effect to any image.

## What is a blend mode? <a href="#what-is-a-blend-mode" class="w-headline-link">#</a>

Blend modes are commonly used in design tools such as Photoshop to create a compositional effect by mixing colors from two or more layers. By changing how colors mix, you can achieve really interesting visual effects. You can also use blend modes as a utility, such as isolating an image that has a white background, so it appears to have a transparent background.

You can use most of the blend modes available in a design tool with CSS, using the [`mix-blend-mode`](https://developer.mozilla.org/en-US/docs/Web/CSS/mix-blend-mode) or the [`background-blend-mode`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-blend-mode) properties. The `mix-blend-mode` applies blending to a whole element and the `background-blend-mode` applies blending to the background of an element.

You use `background-blend-mode` when you have multiple backgrounds on an element and want them all to blend into each other.

The `mix-blend-mode` affects the entire element, including its pseudo elements. One use-case is in the initial example of a duotone image, which has color layers applied to the element through its pseudo elements.

Blend modes fall into two categories: separable and non-separable. A separable blend mode considers each color component, such as RGB, individually. A non-separable blend mode considers all color components equally.

## Separable blend modes <a href="#separable-blend-modes" class="w-headline-link">#</a>

### Normal <a href="#normal" class="w-headline-link">#</a>

This is the default blend mode and changes nothing about how an element blends with others.

### Multiply <a href="#multiply" class="w-headline-link">#</a>

The `multiply` blend mode is like stacking multiple transparencies on top of each other. White pixels will appear transparent, and black pixels will appear black. Anything in between will multiply its luminosity (light) values. This means lights get much lighter and darks, darker—most often producing a darker result.

    .my-element {
      mix-blend-mode: multiply;
    }

### Screen <a href="#screen" class="w-headline-link">#</a>

Using `screen` multiplies the _light_ values—an inverse effect to `multiply`, and will most often produce a brighter result.

    .my-element {
      mix-blend-mode: screen;
    }

### Overlay <a href="#overlay" class="w-headline-link">#</a>

This blend mode—`overlay`—combines `multiply` and `screen`. Base dark colors become darker and base light colors become lighter. Mid-range colors, such as a 50% gray, are unaffected.

    .my-element {
      mix-blend-mode: overlay;
    }

### Darken <a href="#darken" class="w-headline-link">#</a>

The `darken` blend mode compares the source image and backdrop image's dark color luminosity and selects the darkest of the two. It does this by comparing rgb values instead of luminosity (like `multiply` and `screen` would do), for each color channel. With `darken` and `lighten`, new color values are often created from this comparison process.

    .my-element {
      mix-blend-mode: darken;
    }

### Lighten <a href="#lighten" class="w-headline-link">#</a>

Using `lighten` does the exact opposite of `darken`.

    .my-element {
      mix-blend-mode: lighten;
    }

### Color dodge <a href="#color-dodge" class="w-headline-link">#</a>

If you use `color-dodge`, it lightens the background color to reflect the source color. Pure black colors see no effect from this mode.

    .my-element {
      mix-blend-mode: color-dodge;
    }

### Color burn <a href="#color-burn" class="w-headline-link">#</a>

The `color-burn` blend mode is very similar to the `multiply` blend mode, but increases contrast, resulting in more saturated mid-tones and reduced highlights.

    .my-element {
      mix-blend-mode: color-burn;
    }

### Hard light <a href="#hard-light" class="w-headline-link">#</a>

Using `hard-light` creates a vivid contrast. This blend mode either screens or multiplies luminosity values. If the pixel value is lighter than 50% gray, the image is lightened, as if it were screened. If it is darker, it's multiplied.

    .my-element {
      mix-blend-mode: hard-light;
    }

### Soft light <a href="#soft-light" class="w-headline-link">#</a>

The `soft-light` blend mode is a less-harsh version of `overlay`. It works in very much the same way with less contrast.

    .my-element {
      mix-blend-mode: soft-light;
    }

### Difference <a href="#difference" class="w-headline-link">#</a>

A good way to picture how `difference` works is a bit like how a photo negative works. The `difference` blend mode takes the difference value of each pixel, inverting light colors. If the color values are identical, they become black. Differences in the values will invert.

    .my-element {
      mix-blend-mode: difference;
    }

### Exclusion <a href="#exclusion" class="w-headline-link">#</a>

Using `exclusion` is very similar to `difference`, but instead of returning black for identical pixels, it will return 50% gray, resulting in a softer output with less contrast.

    .my-element {
      mix-blend-mode: exclusion;
    }

## Non-separable blend modes <a href="#non-separable-blend-modes" class="w-headline-link">#</a>

You can think of these blend modes like HSL [color](/learn/css/color) components. Each takes a specific component value from the active layer and mixes it with other component values.

### Hue <a href="#hue" class="w-headline-link">#</a>

The `hue` blend mode takes the hue of the source color and applies it to the saturation and luminosity of the backdrop color.

    .my-element {
      mix-blend-mode: hue;
    }

### Saturation <a href="#saturation" class="w-headline-link">#</a>

This works like `hue`, but using `saturation` as the blend mode applies the saturation of the source color to the hue and luminosity of the backdrop color.

    .my-element {
      mix-blend-mode: saturation;
    }

### Color <a href="#color" class="w-headline-link">#</a>

The `color` blend mode will create a color from the hue and saturation of the source color and the luminosity of the backdrop color.

    .my-element {
      mix-blend-mode: color;
    }

### Luminosity <a href="#luminosity" class="w-headline-link">#</a>

Lastly, `luminosity`is the inverse of `color`. It creates a color with the luminosity of the source color and the hue and saturation of the backdrop color.

    .my-element {
      mix-blend-mode: luminosity;
    }

## The `isolation` property <a href="#the-isolation-property" class="w-headline-link">#</a>

If you set the [`isolation`](https://developer.mozilla.org/en-US/docs/Web/CSS/isolation) property to have a value of `isolate`, it will create a new stacking context, which will prevent it from blending with a backdrop layer. As you learned in the [z-index module](/learn/css/z-index), when you create a new stacking context, that layer becomes the base layer. This means that parent-level blend modes will no longer apply, but elements inside of an element with `isolation: isolate` set can _still_ blend.

Note that this doesn't work with `background-blend-mode` because the background property is already isolated.

Test your knowledge of blend-modes

Which of following are CSS blend modes?

<span data-role="option">Difference</span> <span data-role="option">Lighten</span> <span data-role="option">Brighten</span> <span data-role="option">Dullen</span> <span data-role="option">Multiply</span> <span data-role="option">Overlay</span>

🎉

🎉

Try again!

Try again!

🎉

🎉

If you want to blend different colors in different ways, which style of blend mode would you need?

<span data-role="option">Separable</span> <span data-role="option">Non-separable</span>

These blend modes feature color channel targeted effects

Try again, non-separable are not color channel aware

<a href="/learn/css/filters/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">022</span>

Filters

<a href="/learn/css/conclusion/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">024</span>

Conclusion and next steps

Further resources to help you take your next steps.

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
