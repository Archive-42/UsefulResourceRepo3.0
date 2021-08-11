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

- <a href="#numeric-colors" class="toc__anchor">Numeric colors</a>
  - <a href="#hex-colors" class="toc__anchor">Hex colors</a>
  - <a href="#rgb-(red-green-blue)" class="toc__anchor">RGB (Red, Green, Blue)</a>
  - <a href="#hsl-(hue-saturation-lightness)" class="toc__anchor">HSL (Hue, Saturation, Lightness)</a>
- <a href="#color-keywords" class="toc__anchor">Color Keywords</a>
- <a href="#where-to-use-color-in-css-rules" class="toc__anchor">Where to use color in CSS rules</a>
- <a href="#resources" class="toc__anchor">Resources</a>

006

# Color

There are several different ways to specify color in CSS. In this module we take a look at the most commonly used color values.

On this page

- <a href="#numeric-colors" class="toc__anchor">Numeric colors</a>
  - <a href="#hex-colors" class="toc__anchor">Hex colors</a>
  - <a href="#rgb-(red-green-blue)" class="toc__anchor">RGB (Red, Green, Blue)</a>
  - <a href="#hsl-(hue-saturation-lightness)" class="toc__anchor">HSL (Hue, Saturation, Lightness)</a>
- <a href="#color-keywords" class="toc__anchor">Color Keywords</a>
- <a href="#where-to-use-color-in-css-rules" class="toc__anchor">Where to use color in CSS rules</a>
- <a href="#resources" class="toc__anchor">Resources</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 006: Color Part One

Color is an important part of any website and in CSS there are many options for color types, functions and treatments.

How do you decide which color type to use? How do you make your colors semi-transparent? In this lesson, you're going to learn which options you have to help you make the right decisions for your project and team.

CSS has [various different data types](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Types), such as strings and numbers. Color is one of these types and uses other types, such as numbers for its own definitions.

## Numeric colors <a href="#numeric-colors" class="w-headline-link">#</a>

It is very likely that your first exposure to colors in CSS is via numeric colors. We can work with numerical color values in a few different forms.

### Hex colors <a href="#hex-colors" class="w-headline-link">#</a>

    h1 {
      color: #b71540;
    }

Hexadecimal notation (often shortened to hex) is a shorthand syntax for RGB, which assigns a numeric value to red green and blue, which are the three **primary colors**.

According to the Web Almanac, [hex is the most popular color syntax type](https://almanac.httparchive.org/en/2019/css#color-types).

The hexadecimal ranges are **0-9** and **A-F**. When used in a six digit sequence, they are translated to the RGB numerical ranges which are 0-255 which correspond to the red, green, and blue color channels respectively.

You can also define an alpha value with any numerical colors. An alpha value is a percentage of transparency. In hex code, you add another two digits to the six digit sequence, making an eight digit sequence. For example, to set black in hex code, write `#000000`. To add a 50% transparency, change it to `#00000080`.

Because the hex scale is **0-9** and **A-F**, the transparency values are probably not quite what you'd expect them to be. Here are some key, common values added to the black hex code, `#000000`:

- 0% alpha—which is fully transparent—is **00**: `#00000000`
- 50% alpha is **80**: `#00000080`
- 75% alpha is **BF**: `#000000BF`

To convert a two digit hex to a decimal, take the first digit and multiply it by 16 (because hex is base 16), then add the second digit. Using **BF** as an example for 75% alpha:

1.  B is equal to 11, which when multiplied by 16 equals 176
2.  F is equal to 15
3.  176 + 15 = 191
4.  The alpha value is 191—75% of 255

You can also write hex codes in a three digit shorthand. A three digit hex code is a shortcut to an equivalent six digit sequence. For example, `#a4e` is identical to `#aa44ee`. To add alpha, then `#a4e8` would expand to `#aa44ee88`.

### RGB (Red, Green, Blue) <a href="#rgb-(red-green-blue)" class="w-headline-link">#</a>

    h1 {
      color: rgb(183, 21, 64);
    }

RGB colors are defined with the [`rgb()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/rgb()>) color function, using either numbers or percentages as parameters. The numbers need to be within the **0-255** range and the percentages are between **0% and 100%‌**. RGB works on the 0-255 scale, so 255 would be equivalent to 100%, and 0 to 0%.

To set black in RGB, define it as `rgb(0 0 0)`, which is zero red, zero green and zero blue. Black can also be defined as `rgb(0%, 0%, 0%)`. White is the exact opposite: `rgb(255, 255, 255)` or `rgb(100%, 100%, 100%)`.

An alpha is set in `rgb()` in one of two ways. Either add a `/` **after** the red, green and blue parameters, or use the [`rgba()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/rgba()>) function. The alpha can be defined with a percentage or a decimal between 0 and 1. For example, to set a 50% alpha black in modern browsers, write: `rgb(0 0 0 / 50%)` or `rgb(0 0 0 / 0.5)`. For wider support, using the `rgba()` function, write: `rgba(0, 0, 0, 50%)` or `rgba(0, 0, 0, 0.5)`.

Commas were removed from the `rgb()` and `hsl()` notation because newer color functions, such as `lab()` and `lch()` use spaces instead of commas as a delimiter. This change provides more consistency not just with newer color functions, but with CSS in general. For better backwards compatibility, you can still use commas to define `rgb()` and `hsl()`.

### HSL (Hue, Saturation, Lightness) <a href="#hsl-(hue-saturation-lightness)" class="w-headline-link">#</a>

    h1 {
      color: hsl(344, 79%, 40%);
    }

HSL stands for hue, saturation and lightness. Hue describes the value on the color wheel, from 0 to 360 degrees, starting with red (being both 0 and 360). A hue of 180, or 50% would be in the blue range. It's the origin of the color that we see.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ob7MTste1Obu9AoLvbKq.svg" alt="A color wheel with labels for degree values in 60 degree increments to help visuals what each angle value represents" width="800" height="507" />

Saturation is how vibrant the selected hue is. A fully desaturated color (with a saturation of `0%`) will appear grayscale. And finally, lightness is the parameter which describes the scale from white to black of added light. A lightness of `100%` will always give you white.

Using the [`hsl()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/hsl()>) color function, you define a true black by writing `hsl(0 0% 0%)`, or even `hsl(0deg 0% 0%)`. This is because the hue parameter defines the degree on the color wheel, which if you use the number type, is **0-360**. You can also use the angle type, which is (`0deg`) or `(0turn)`. Both saturation and lightness are defined with percentages.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/RhVxWSZ6bH35eBdN6Prj.svg" alt="The HSL color function broken down visually. The hue uses the color wheel. The saturation shows grey blending into teal. The lightness shows black into white." width="800" height="478" />

[The angle type](https://developer.mozilla.org/en-US/docs/Web/CSS/angle) in CSS is great for defining hue because it represents the angle of the color wheel really well. This type accepts degrees, turns, radians and gradians.

Alpha is defined in `hsl()`, in the same way as `rgb()` by adding a `/` after the hue, saturation and lightness parameters _or_ by using the [`hsla()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/hsla()>) function. The alpha can be defined with a percentage or a decimal between 0 and 1. For example, to set a 50% alpha black, use: `hsl(0 0% 0% / 50%)` or `hsl(0 0% 0% / 0.5)`. Using the `hsla()` function, write: `hsla(0, 0%, 0%, 50%)` or `hsla(0, 0%, 0%, 0.5)`.

There are some newer color types coming to CSS. These include [lab()](<https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/lab()>) and [lch()](<https://developer.mozilla.org/en-US/docs/Web/CSS/color_value/lch()>), which allow a far wider range of color to be specified than is possible in RGB.

## Color Keywords <a href="#color-keywords" class="w-headline-link">#</a>

There are [148 named colors in CSS](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value#color_keywords). These are plain English names such as purple, tomato and goldenrod. Some of the most popular names, according to the [Web Almanac](https://almanac.httparchive.org/en/2019/css), are black, white, red, blue and gray. Our favorites include goldenrod, aliceblue, and hotpink.

Aside from standard colors, there are also special keywords available:

- `transparent` is a fully transparent color. It is also the initial value of `background-color`
- `currentColor` is the contextual computed dynamic value of the `color` property. If you have a text color of `red` and then set the `border-color` to be `currentColor`, it will also be red. If the element that you define `currentColor` on doesn't have a value for `color` defined, `currentColor` will be computed by the cascade instead

System keywords are colors that are defined by your operating system theme. Some examples of these colors are `Background`, which is the desktop background color or `Highlight`, which is the highlight color of selected items. These are just two of [many options](https://www.w3.org/wiki/CSS/Properties/color/keywords#System_Colors).

All color keywords are case-insensitive, however you will often see system colors with capitalization in order to differentiate them from standard color keywords.

## Where to use color in CSS rules <a href="#where-to-use-color-in-css-rules" class="w-headline-link">#</a>

If a CSS property accepts the [`<color>`](https://developer.mozilla.org/en-US/docs/Web/CSS/color_value) data type as a value, it will accept any of the above methods of expressing color. For styling text, use the `color`, `text-shadow` and `text-decoration-color` properties which all accept color as the value or color as part of the value.

For backgrounds, you can set a color as the value for `background` or `background-color`. Colors can also be used in gradients, such as `linear-gradient`. Gradients are a type of image that can be programmatically defined in CSS. Gradients accept two or more colors in any combination of color format, such as hex, rgb or hsl.

There's lots to learn with gradients so we wrote [a whole lesson](/learn/css/gradients) on how to use them.

Finally, `border-color`, and `outline-color` set the color for borders and outlines on your boxes. The `box-shadow` property also accepts color as one of the values.

Test your knowledge of color

Which of the following are valid colors?

<span data-role="option">`rbga(400 0 1)`</span> <span data-role="option">`#0f08`</span> <span data-role="option">`#OOFZ2`</span> <span data-role="option">`rgb(255, 0, 0)`</span> <span data-role="option">`hsl(180deg 50% 50%)`</span> <span data-role="option">`hotpink`</span>

rbga is a typo of rgba and 400 is larger than it would accept anyway, making it invalid.

🎉

This is not a hex value, it's only 5 numbers and includes an Z, making it invalid.

🎉

🎉

🎉

Spot the invalid hsl color.

<span data-role="option">`hsl(5, 0%, 90%)`</span> <span data-role="option">`hsl(.5turn 40% 60%)`</span> <span data-role="option">`hsl(0, 0, 0)`</span> <span data-role="option">`hsl(2rad 50% 50%)`</span> <span data-role="option">`hsl(0 0% 0% / 20%)`</span>

This is a valid hsl value.

This is a valid hsl value.

🎉 You found it, the 2nd and 3rd values should be percentages.

This is a valid hsl value.

This is a valid hsl value.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [A handy demo showing how you can use angles with HSL](https://codepen.io/argyleink/pen/ExjReJa)
- [A comprehensive guide on color](https://css-tricks.com/nerds-guide-color-web/)
- [\[video\] An explainer on how to read hex codes](https://www.youtube.com/watch?v=eqZqx6lRPe0)
- [How hexadecimal codes work](https://medium.com/basecs/hexs-and-other-magical-numbers-9785bc26b7ee)

<a href="/learn/css/inheritance/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">005</span>

Inheritance

<a href="/learn/css/sizing/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">007</span>

Sizing Units

In this module find out how to size elements using CSS, working with the flexible medium of the web.

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
