<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format" alt="A photo of letterpress type." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/T4kc8pjG9mvfZwynORjM.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#best-practices-for-fonts" class="w-toc__header--link">Best practices for fonts</a>

- [Font loading](#font-loading)
- [Best practices](#best-practices)
- [Font delivery](#font-delivery)
- [Best practices](#best-practices-2)
- [Font rendering](#font-rendering)
- [Best practices](#best-practices-3)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Best practices for fonts

Optimize web fonts for Core Web Vitals.

Jun 3, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/learn-web-vitals" class="w-post-signpost__link">Web Vitals</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

- <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
- <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
- <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

This article discusses performance best practices for fonts. There are a variety of ways in which web fonts impact performance:

- **Delayed text rendering:** If a web font has not loaded, browsers typically delay text rendering. In many situations, this delays [First Contentful Paint (FCP)](/fcp). In some situations, this delays [Largest Contentful Paint (LCP)](/lcp/).
- **Layout shifts:** The practice of font swapping has the potential to [cause layout shifts](/debug-layout-shifts/#identifying-the-cause-of-a-layout-shift). These layout shifts occur when a web font and its fallback font take up different amounts of space on the page.

This article is broken down into three sections: font loading, font delivery, and font rendering. Each section explains how that particular aspect of the font lifecycle works and provides corresponding best practices.

## Font loading <a href="#font-loading" class="w-headline-link">#</a>

Before diving into best practices for font loading it's important to understand how [`@font-face`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face) works and how this impacts font loading.

The [`@font-face`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face) declaration is an essential part of working with any web font. At a minimum, it declares the name that will be used to refer to the font and indicates the location of the corresponding font file.

    @font-face {
      font-family: "Open Sans";
      src: url("/fonts/OpenSans-Regular-webfont.woff2") format("woff2");
    }

A common misconception is that a font is requested when a `@font-face` declaration is encountered—this is not true. By itself, `@font-face` declaration does not trigger font download. Rather, a font is downloaded only if it is referenced by styling that is used on the page. For example, like this:

    @font-face {
      font-family: "Open Sans";
      src: url("/fonts/OpenSans-Regular-webfont.woff2") format("woff2");
    }

    h1 {
      font-family: "Open Sans"
    }

In other words, in the example above, `Open Sans` would only be downloaded if the page contained a `<h1>` element.

Other ways of loading a font are the [`preload`](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content) resource hint and the [Font Loading API](/optimize-webfont-loading/#the-font-loading-api).

Thus, when thinking about font optimization, it's important to give stylesheets just as much consideration as the font files themselves. Changing the contents or delivery of stylesheets can have a significant impact on when fonts arrive. Similarly, removing unused CSS and splitting stylesheets can reduce the number of fonts loaded by a page.

### Best practices <a href="#best-practices" class="w-headline-link">#</a>

Fonts are typically important resources, as without them the user might be unable to view page content. Thus, best practices for font loading generally focus on making sure that fonts get loaded as early as possible. Particular care should be given to fonts loaded from third-party sites as downloading these font files requires separate connection setups.

If you're unsure if your page's fonts are being requested in time, check the **Timing** tab within the **Network** panel in Chrome DevTools for more information.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format" alt="Screenshot of the Timing tab in DevTools" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/hFVGVzDQHymbC5aIAtD9.png?auto=format&amp;w=1600 1600w" width="800" height="472" />

#### Inline font declarations <a href="#inline-font-declarations" class="w-headline-link">#</a>

Most sites would strongly benefit from inlining font declarations and other critical styling in the `<head>` of the main document rather than including them in an external stylesheet. This allows the browser to discover the font declarations sooner as the browser doesn't need to wait for the external stylesheet to download.

    <head>
      <style>
        @font-face {
            font-family: "Open Sans";
            src: url("/fonts/OpenSans-Regular-webfont.woff2") format("woff2");
        }

        body {
            font-family: "Open Sans";

        }
      </style>
    </head>

Inlining the font files themselves is not recommended. Inlining large resources like fonts is likely to delay the delivery of the main document, and with it, the discovery of other resources.

#### Preconnect to critical third-party origins <a href="#preconnect-to-critical-third-party-origins" class="w-headline-link">#</a>

If your site loads fonts from a third-party site, it is highly recommended that you use the [`preconnect`](https://developer.mozilla.org/en-US/docs/Web/HTML/Link_types/preconnect) resource hint to establish early connection(s) with the third-party origin. Resource hints should be placed in the `<head>` of the document. The resource hint below sets up a connection for loading the font stylesheet.

    <head>
      <link rel="preconnect" href="https://fonts.com">
    </head>

To preconnect the connection that is used to download the font file, add a separate `preconnect` resource hint that uses the `crossorigin` attribute. Unlike stylesheets, font files must be sent over a [CORS connection](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#what_requests_use_cors).

    <head>
      <link rel="preconnect" href="https://fonts.com">
      <link rel="preconnect" href="https://fonts.com" crossorigin>
    </head>

When using the `preconnect` resource hint, keep in mind that a font provider may serve stylesheets and fonts from separate origins. For example, this is how the `preconnect` resource hint would be used for Google Fonts.

    <head>
      <link rel="preconnect" href="https://fonts.googleapis.com">
      <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    </head>

[Google Fonts](https://fonts.google.com/) provides the option to load fonts via `<link>` tags or an `@import` statement. The `<link>` code snippet includes a `preconnect` resource hint and therefore will likely result in faster stylesheet delivery than using `@import` version. These `<link>` tags should be placed as early in the document as possible.

#### Avoid using preload to load fonts <a href="#avoid-using-preload-to-load-fonts" class="w-headline-link">#</a>

Generally speaking, using the [`preload`](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content) resource hint to load fonts should be avoided. Although `preload` is highly effective at making fonts discoverable early in the page load process, this comes at the cost of taking away browser resources from the loading of other resources.

In most scenarios, inlining font declarations and adjusting stylesheets is a more effective approach. These adjustments come closer to addressing the root cause of late-discovered fonts - rather than just providing a workaround.

In addition, using `preload` as a font-loading strategy should also be used carefully as it bypasses some of the browser's built-in content negotiation strategies. For example, `preload` ignores `unicode-range` declarations, and if used prudently, should only be used to load a single font format.

## Font delivery <a href="#font-delivery" class="w-headline-link">#</a>

Faster font delivery yields faster text rendering. In addition, if a font is delivered early enough, this can help eliminate layout shifts resulting from font swapping.

### Best practices <a href="#best-practices-2" class="w-headline-link">#</a>

#### Using self-hosted fonts <a href="#using-self-hosted-fonts" class="w-headline-link">#</a>

On paper, using a self-hosted font should deliver better performance as it eliminates a third-party connection setup. However, in practice, the performance differences between these two options is less clear cut: for example, the [Web Almanac](https://almanac.httparchive.org/en/2020/fonts#fig-7) found that sites using third-party fonts had a faster render than fonts that used first-party fonts.

If you are considering using self-hosted fonts, confirm that your site is using a [Content Delivery Network (CDN)](/content-delivery-networks/) and [HTTP/2](/content-delivery-networks/#http2-and-http3). Without use of these technologies, it is much less likely that self-hosted fonts will deliver better performance. For more information, see [Content Delivery Networks](/content-delivery-networks/).

If you're unsure if using self-hosted fonts will deliver better performance, try serving a font file from your own servers and compare the transfer time (including connection setup) with that of a third-party font. If you have slow servers, don't use a CDN, or don't use HTTP/2 it becomes less likely that the self-hosted font will be more performant.

If you use a self-hosted font, it is recommended that you also apply some of the font file optimizations that third-party font providers typically provide automatically—for example, font subsetting and WOFF2 compression. The amount of effort required to apply these optimizations will depend somewhat on the languages that your site supports. In particular, be aware that optimizing fonts for [CJK languages](https://en.wikipedia.org/wiki/CJK_characters) can be particularly challenging.

**Unicode-range and font subsetting:** `@font-face` is often used in conjunction with the [`unicode-range`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/unicode-range) descriptor. `unicode-range` informs the browser which characters a font can be used for.

    @font-face {
        font-family: "Open Sans";
        src: url("/fonts/OpenSans-Regular-webfont.woff2") format("woff2");
        unicode-range: U+0025-00FF;
    }

A font file will be downloaded if the page contains one or more characters matching the unicode range. `unicode-range` is commonly used to serve different font files depending on the language used by page content.

`unicode-range` is often used in conjunction with the technique of subsetting. A subset font includes a smaller portion of the [glyphs](https://en.wikipedia.org/wiki/Glyph) (that is, characters) that were contained in the original font file. For example, rather than serve all characters to all users, a site might generate separate subset fonts for Latin and Cyrillic characters. The number of glyphs per font varies wildly: Latin fonts are usually on the magnitude of 100 to 1000 glyphs per font; [CJK](https://en.wikipedia.org/wiki/CJK_characters) fonts may have over 10,000 characters. Removing unused glyphs can significantly reduce the filesize of a font.

Tools for generating font subsets include [subfont](https://github.com/Munter/subfont) and [glyphanger](https://github.com/zachleat/glyphhanger).

For information on how Google Fonts implements font subsetting, see this [presentation](https://www.unicodeconference.org/presentations-42/S5T3-Sheeter.pdf). For the Google Fonts API subsets, see this [repo](https://github.com/googlefonts/gftools/tree/main/Lib/gftools/encodings).

**WOFF2:** Of the modern font fonts, [WOFF2](https://www.w3.org/TR/WOFF2/) is the newest, has the widest browser support, and offers the best compression. Because it uses Brotli, WOFF2 compresses 30% better than WOFF.

#### Use fewer web fonts <a href="#use-fewer-web-fonts" class="w-headline-link">#</a>

The fastest font to deliver is a font that isn't requested in the first place. System fonts and variable fonts are two ways to potentially reduce the number of web fonts used on your site.

A **system font** is the default font used by the user interface of a user's device. System fonts typically vary by operating system and version. Because the font is already installed, the font does not need to be downloaded. System fonts can work particularly well for body text.

To use the system font in your CSS, list `system-ui` as the font-family:

    font-family: system-ui

The idea behind **[variable fonts](/variable-fonts/)** is that a single variable font can be used as a replacement for multiple font files. Variable fonts work by defining a "default" font style and providing ["axes"](/variable-fonts/#axes-definitions) for manipulating the font. For example, a variable font with a `Weight` axis could be used to implement lettering that would previously require separate fonts for light, regular, bold, and extra bold.

We often refer to "Times New Roman" and "Helvetica" as fonts. However, technically speaking, these are font _families_. A family is composed of styles, which are particular variations of the typeface (for example, light, medium, or bold italic). A font file contains a single style unless it is a variable font. A typeface is the underlying design, which can be expressed as digital fonts - and in physical type, like carved woodblocks or metal.

Not everyone will benefit from switching to variable fonts. [Variable fonts](/variable-fonts/) contain many styles, so typically have larger file sizes than individual non-variable fonts that only contain one style. Sites that will see the largest improvement from using variable fonts are those that use (and need to use) a variety of font styles and weights.

## Font rendering <a href="#font-rendering" class="w-headline-link">#</a>

When faced with a web font that has not yet loaded, the browser is faced with a dilemma: should it hold off on rendering text until the web font has arrived? Or should it render the text in a fallback font until the web font arrives?

Different browsers handle this scenario differently. By default, Chromium-based and Firefox browsers will block text rendering for up to 3 seconds if the associated web font has not loaded; Safari will block text rendering indefinitely.

This behavior can be configured by using the `font-display` attribute. This choice can have significant implications: `font-display` has the potential to impact LCP, FCP, and layout stability.

### Best practices <a href="#best-practices-3" class="w-headline-link">#</a>

#### Choose an appropriate `font-display` strategy <a href="#choose-an-appropriate-font-display-strategy" class="w-headline-link">#</a>

[`font-display`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display) informs the browser how it should proceed with text rendering when the associated web font has not loaded. It is defined per font-face.

    @font-face {
      font-family: Roboto, Sans-Serif
      src: url(/fonts/roboto.woff) format('woff'),
      font-display: swap;
    }

There are five possible values for `font-display`:

<table><thead><tr class="header"><th><strong>Value</strong></th><th><strong>Block period</strong></th><th><strong>Swap period</strong></th></tr></thead><tbody><tr class="odd"><td>Auto</td><td>Varies by browser</td><td>Varies by browser</td></tr><tr class="even"><td>Block</td><td>3 seconds</td><td>Infinite</td></tr><tr class="odd"><td>Swap</td><td>0ms</td><td>Infinite</td></tr><tr class="even"><td>Fallback</td><td>100ms</td><td>3 seconds</td></tr><tr class="odd"><td>Optional</td><td>100ms</td><td>None</td></tr></tbody></table>

- **Block period**: The block period begins when the browser requests a web font. During the block period, if the web font is not available, the font is rendered in an _invisible_ fallback font and thus the text will not be visible to the user. If the font is not available at the end of the block period, it will be rendered in the fallback font.
- **Swap period**: The swap period comes after the block period. If the web font becomes available during the swap period, it will be "swapped" in.

##### Recommendation <a href="#recommendation" class="w-headline-link">#</a>

`font-display` strategies reflect different viewpoints about the tradeoff between performance and aesthetics. For most sites, these are the two strategies that will be most applicable:

- **If performance is a top priority:** Use `font-display: optional`. This is the most "performant" approach: text render is delayed for no longer than 100ms and there is assurance that there will be no font-swap related layout shifts.

- **If displaying text in a web font is a top priority:** Use `font-display: swap` but make sure to deliver the font early enough that it does not cause a layout shift.

`font-display: auto`, `font-display: block`, `font-display: swap`, and `font-display: fallback` all have the potential to cause layout shifts when the font is swapped. However, of these approaches, `font-display: swap` will delay text render the least. Thus, it is the preferred approach for situations where it is important that text ultimately gets rendered as a web font.

Also keep in mind that these two approaches can be combined: for example, use `font-display: swap` for branding and other visually distinctive page elements; use `font-display: optional` for fonts used in body text.

The `font-display` strategies that work well for traditional web fonts don't work nearly as well for icon fonts. The fallback font for an icon font typically looks significantly different than the icon font and its characters may convey a completely different meaning. As a result, icon fonts are more likely to cause significant layout shifts. In addition, using a fallback font may not be practical. If possible, it's best to replace icon fonts with SVG (this is also better for accessibility). Newer versions of popular icon fonts typically support SVG. For more information on switching to SVG, see [Font Awesome](https://fontawesome.com/v5.15/how-to-use/on-the-web/advanced/svg-sprites) and [Material Icons](https://google.github.io/material-design-icons/#svg).

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/web-vitals/" class="w-chip">Web Vitals</a>

<span class="w-mr--sm">Last updated: Jun 3, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/font-best-practices/index.md)

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
