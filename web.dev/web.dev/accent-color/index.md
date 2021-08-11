<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/huEpiCoJQ6dAo8rHGsZT.png?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#css-lesscodegreateraccent-colorlesscodegreater" class="w-toc__header--link">CSS <code>accent-color</code></a>

- [Browser support](#browser-support)
- [Supported elements](#supported-elements)
- [Checkbox](#checkbox)
- [Radio](#radio)
- [Range](#range)
- [Progress](#progress)
- [Guaranteeing contrast](#guaranteeing-contrast)
- [Extra: More tinting](#extra:-more-tinting)
- [Potential future](#potential-future)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# CSS `accent-color`

Bring your brand color to built-in HTML form inputs with one line of code.

Aug 11, 2021

[<img src="https://web-dev.imgix.net/image/admin/jdQIxAJrGuFOtwmuDfIn.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Adam Argyle" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/jdQIxAJrGuFOtwmuDfIn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/jdQIxAJrGuFOtwmuDfIn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/jdQIxAJrGuFOtwmuDfIn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/jdQIxAJrGuFOtwmuDfIn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/jdQIxAJrGuFOtwmuDfIn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/adamargyle/)

<a href="/authors/adamargyle/" class="w-author__name-link">Adam Argyle</a>

- <a href="https://twitter.com/argyleink" class="w-author__link">Twitter</a>
- <a href="https://github.com/argyleink" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@argyleink" class="w-author__link">Glitch</a>
- <a href="https://nerdy.dev" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/ahMMPwVRwAdp0gFdY0zZnncYdsm1/3i0rkOVNKJImIy1UWvyC.jpeg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Joey Arhar" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/ahMMPwVRwAdp0gFdY0zZnncYdsm1/3i0rkOVNKJImIy1UWvyC.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/ahMMPwVRwAdp0gFdY0zZnncYdsm1/3i0rkOVNKJImIy1UWvyC.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/ahMMPwVRwAdp0gFdY0zZnncYdsm1/3i0rkOVNKJImIy1UWvyC.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/ahMMPwVRwAdp0gFdY0zZnncYdsm1/3i0rkOVNKJImIy1UWvyC.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/ahMMPwVRwAdp0gFdY0zZnncYdsm1/3i0rkOVNKJImIy1UWvyC.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jarhar/)

<a href="/authors/jarhar/" class="w-author__name-link">Joey Arhar</a>

- <a href="https://twitter.com/josepharhar" class="w-author__link">Twitter</a>
- <a href="https://github.com/josepharhar" class="w-author__link">GitHub</a>

Today's HTML form elements are [difficult to customize](https://codepen.io/GeoffreyCrofte/pen/BiHzp). It feels as if it's a choice between few or no custom styles, or resetting input styles and build it up from scratch. Building it up from scratch ends up being much more work than anticipated. It can also lead to forgotten styles for element states ([indeterminate](https://developer.mozilla.org/en-US/docs/Web/CSS/:indeterminate), I'm looking at you), and the loss of built-in accessibility features. To fully recreate what the browser provides may be more work than you're looking to take on.

    accent-color: hotpink;

CSS `accent-color` from the [CSS UI specification](https://www.w3.org/TR/css-ui-4/#widget-accent) is here to tint elements with one line of CSS, saving you from customization efforts by providing a way to bring your brand into elements.

<figure><img src="https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format" alt="Demo" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/CfSS3F1XUsfCHIB86xeE.png?auto=format&amp;w=1600 1600w" width="800" height="548" /><figcaption><a href="https://codepen.io/web-dot-dev/pen/PomBZdy">Demo</a></figcaption></figure>The `accent-color` property also works with [`color-scheme`](/color-scheme/), allowing authors to tint both the light and dark elements. In the following example the user has a dark theme active, the page uses `color-scheme: light dark`, and uses the same `accent-color: hotpink` for dark themed hotpink tinted controls.

<figure><img src="https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format" alt="Demo" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/3gxeeZoSLY34tsMxkyt9.png?auto=format&amp;w=1600 1600w" width="800" height="548" /><figcaption><a href="https://codepen.io/web-dot-dev/pen/PomBZdy">Demo</a></figcaption></figure>### Browser support <a href="#browser-support" class="w-headline-link">#</a>

As of this writing, Chromium 93+ and Firefox 92+ support `accent-color`.

## Supported elements <a href="#supported-elements" class="w-headline-link">#</a>

Currently, only four elements will tint via the `accent-color` property: [checkbox](#checkbox), [radio](#radio), [range](#range) and [progress](#progress). Each can be previewed here <https://accent-color.glitch.me> in light and dark color schemes.

**Warning**: If the following demo elements are all the same color, then your browser doesn't support `accent-color` yet.

### Checkbox <a href="#checkbox" class="w-headline-link">#</a>

### Radio <a href="#radio" class="w-headline-link">#</a>

### Range <a href="#range" class="w-headline-link">#</a>

### Progress <a href="#progress" class="w-headline-link">#</a>

## Guaranteeing contrast <a href="#guaranteeing-contrast" class="w-headline-link">#</a>

To prevent inaccessible elements from existing, browsers with `accent-color` need to determine an [eligible contrast color](https://webaim.org/articles/contrast/) to be used alongside the custom accent. Below is a screenshot demonstrating how Chrome 94 (left) and Firefox 92 Nightly (right) differ in their algorithms:

<img src="https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format" alt="A screenshot of Firefox and Chromium side by side, rendering a full spectrum of checkboxes in various hues and darknesses." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/vS06HQ1YTsbMKSFTIPl2iogUQP73/DJhB56n10Eh8O29RsRdE.png?auto=format&amp;w=1600 1600w" width="800" height="832" />

The most important thing to take away from this, is to **trust the browser**. Provide a brand color, and trust that it will make smart decisions for you.

The browser will not change your color in a dark theme.

## Extra: More tinting <a href="#extra:-more-tinting" class="w-headline-link">#</a>

You may be wondering how to tint more than these four form elements? Here's a minimal sandbox which tints:

- the focus ring
- text selection highlights
- list [markers](/css-marker-pseudo-element/)
- arrow indicators (Webkit only)
- scrollbar thumb (Firefox only)

<!-- -->

    html {
      --brand: hotpink;
      scrollbar-color: hotpink Canvas;
    }

    :root { accent-color: var(--brand); }
    :focus-visible { outline-color: var(--brand); }
    ::selection { background-color: var(--brand); }
    ::marker { color: var(--brand); }

    :is(
      ::-webkit-calendar-picker-indicator,
      ::-webkit-clear-button,
      ::-webkit-inner-spin-button,
      ::-webkit-outer-spin-button
    ) {
      color: var(--brand);
    }

### Potential future <a href="#potential-future" class="w-headline-link">#</a>

The spec does not limit the application of `accent-color` to the four elements shown in this article, more support could be added later. Elements like the selected `<option>` in a `<select>` could be highlighted with the `accent-color`.

What else do you like to tint on the web? Tweet [@argyleink](https://twitter.com/argyleink) with your selector and it might get added to this article!

<a href="/tags/css/" class="w-chip">CSS</a>

<span class="w-mr--sm">Last updated: Aug 11, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/blog/accent-color/index.md)

<a href="/blog" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
