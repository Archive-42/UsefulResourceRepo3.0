





<a href="#preload-critical-assets-to-improve-loading-speed" class="w-toc__header--link">Preload critical assets to improve loading speed</a>
--------------------------------------------------------------------------------------------------------------------------------------------

-   [How preloading works](#how-preloading-works)
-   [Use cases](#use-cases)
-   [Preloading resources defined in CSS](#preloading-resources-defined-in-css)
-   [Preloading CSS files](#preloading-css-files)
-   [Preloading JavaScript files](#preloading-javascript-files)
-   [How to implement rel=preload](#how-to-implement-relpreload)
-   [Preloading JavaScript modules with webpack](#preloading-javascript-modules-with-webpack)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Preload critical assets to improve loading speed
================================================

Nov 5, 2018 <span class="w-author__separator">•</span> Updated May 27, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

-   <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
-   <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

When you open a web page, the browser requests the HTML document from a server, parses its contents, and submits separate requests for any referenced resources. As a developer, you already know about all the resources your page needs and which of them are the most important. You can use that knowledge to request the critical resources ahead of time and speed up the loading process. This post explains how to achieve that with `<link rel="preload">`.

How preloading works <a href="#how-preloading-works" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

Preloading is best suited for resources typically discovered late by the browser.

<figure><img src="https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format" alt="In this example, Pacifico font is defined in the stylesheet with a @font-face rule. The browser loads the font file only after it has finished downloading and parsing the stylesheet." sizes="(min-width: 701px) 701px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/Ad9PLq3DcQt9Ycp63z6O.png?auto=format&amp;w=1402 1402w" width="701" height="509" /><figcaption>In this example, Pacifico font is defined in the stylesheet with a <a href="/reduce-webfont-size/#defining-a-font-family-with-@font-face)"><code>@font-face</code></a> rule. The browser loads the font file only after it has finished downloading and parsing the stylesheet.</figcaption></figure>By preloading a certain resource, you are telling the browser that you would like to fetch it sooner than the browser would otherwise discover it because you are certain that it is important for the current page.

<figure><img src="https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format" alt="In this example, Pacifico font is preloaded, so the download happens in parallel with the stylesheet." sizes="(min-width: 701px) 701px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/PgRbERrxLGfF439yBMeY.png?auto=format&amp;w=1402 1402w" width="701" height="509" /><figcaption>In this example, Pacifico font is preloaded, so the download happens in parallel with the stylesheet.</figcaption></figure>The critical request chain represents the order of resources that are prioritized and fetched by the browser. Lighthouse identifies assets that are on the third level of this chain as late-discovered. You can use the [**Preload key requests**](/uses-rel-preload) audit to identify which resources to preload.

<img src="https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format" alt="Lighthouse&#39;s preload key requests audit." class="w-screenshot" sizes="(min-width: 745px) 745px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/BPUTHBNZFbeXqb0dVx2f.png?auto=format&amp;w=1490 1490w" width="745" height="97" />

You can preload resources by adding a `<link>` tag with `rel="preload"` to the head of your HTML document:

    <link rel="preload" as="script" href="critical.js">

The browser caches preloaded resources so they are available immediately when needed. (It doesn't execute the scripts or apply the stylesheets.)

After implementing preloading, many sites, including [Shopify, Financial Times and Treebo, saw 1-second improvements](https://medium.com/reloading/preload-prefetch-and-priorities-in-chrome-776165961bbf) in user-centric metrics such as [Time to Interactive](/interactive) and [First Contentful Paint](/first-contentful-paint).

Resource hints, for example, [`preconnect`](/preconnect-and-dns-prefetch)and [`prefetch`](/link-prefetch), are executed as the browser sees fit. The `preload`, on the other hand, is mandatory for the browser. Modern browsers are already pretty good at prioritizing resources, that's why it's important to use `preload` sparingly and only preload the most critical resources.

Unused preloads trigger a Console warning in Chrome, approximately 3 seconds after the `load` event.

<img src="https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format" alt="Chrome DevTools Console warning about unused preloaded resources." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/z4FbCezjXHxaIhq188TU.png?auto=format&amp;w=1600 1600w" width="800" height="228" />

[`preload` is supported](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content#Browser_compatibility) in all modern browsers.

Use cases <a href="#use-cases" class="w-headline-link">#</a>
------------------------------------------------------------

**Caution**: At the time of writing, Chrome has an open [bug](https://bugs.chromium.org/p/chromium/issues/detail?id=788757) for preloaded requests that are fetched sooner than other higher priority resources. Until this is resolved, be wary of how preloaded resources can "jump the queue" and be requested sooner than they should.

### Preloading resources defined in CSS <a href="#preloading-resources-defined-in-css" class="w-headline-link">#</a>

Fonts defined with [`@font-face`](/reduce-webfont-size/#defining-a-font-family-with-@font-face) rules or background images defined in CSS files aren't discovered until the browser downloads and parses those CSS files. Preloading these resources ensures they are fetched before the CSS files have downloaded.

### Preloading CSS files <a href="#preloading-css-files" class="w-headline-link">#</a>

If you are using the [critical CSS approach](/extract-critical-css), you split your CSS into two parts. The critical CSS required for rendering the above-the-fold content is inlined in the `<head>` of the document and non-critical CSS is usually lazy-loaded with JavaScript. Waiting for JavaScript to execute before loading non-critical CSS can cause delays in rendering when users scroll, so it's a good idea to use `<link rel="preload">` to initiate the download sooner.

### Preloading JavaScript files <a href="#preloading-javascript-files" class="w-headline-link">#</a>

Because browsers don't execute preloaded files, preloading is useful to separate fetching from [execution](/bootup-time) which can improve metrics such as Time to Interactive. Preloading works best if you [split](/reduce-javascript-payloads-with-code-splitting) your JavaScript bundles and only preload critical chunks.

How to implement rel=preload <a href="#how-to-implement-relpreload" class="w-headline-link">#</a>
-------------------------------------------------------------------------------------------------

The simplest way to implement `preload` is to add a `<link>` tag to the `<head>` of the document:

    <head>
      <link rel="preload" as="script" href="critical.js">
    </head>

Supplying the `as` attribute helps the browser set the priority of the prefetched resource according to its type, set the right headers, and determine whether the resource already exists in the cache. Accepted values for this attribute include: `script`, `style`, `font`, `image`, and [others](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link#Attributes).

Take a look at the [Chrome Resource Priorities and Scheduling](https://docs.google.com/document/d/1bCDuq9H1ih9iNjgzyAL0gpwNFiEP4TZS-YLRp_RuMlc/edit) document to learn more about how the browser prioritizes different types of resources.

**Caution**: Omitting the `as` attribute, or having an invalid value is equivalent to an [XHR request,](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) where the browser doesn't know what it is fetching so it can't determine the correct priority. It can also cause some resources, such as scripts, to be fetched twice.

Some types of resources, such as fonts, are loaded in [anonymous mode](https://www.w3.org/TR/css-fonts-3/#font-fetching-requirements). For those you must set the `crossorigin` attribute with `preload`:

    <link rel="preload" href="ComicSans.woff2" as="font" type="font/woff2" crossorigin>

**Caution**: Fonts preloaded without the `crossorigin` attribute will be fetched twice!

`<link>` elements also accept a [`type` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/link#attr-type), which contains the [MIME type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types) of the linked resource. The browsers use the value of the `type` attribute to make sure that resources get preloaded only if their file type is supported. If a browser doesn't support the specified resource type, it will ignore the `<link rel="preload">`.

**Try it**! [Improve the performance of a page by preloading web fonts](/codelab-preload-web-fonts).

You can also preload any type of resource via the [`Link` HTTP header](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Link):

`Link: </css/style.css>; rel="preload"; as="style"`

A benefit of specifying `preload` in the HTTP Header is that the browser doesn't need to parse the document to discover it, which can offer small improvements in some cases.

### Preloading JavaScript modules with webpack <a href="#preloading-javascript-modules-with-webpack" class="w-headline-link">#</a>

If you are using a module bundler that creates build files of your application, you need to check if it supports the injection of preload tags. With [webpack](https://webpack.js.org/) version 4.6.0 or later, preloading is supported through the use of [magic comments](https://webpack.js.org/api/module-methods/#magic-comments) inside `import()`:

    import(_/* webpackPreload: true */_ "CriticalChunk")

If you are using an older version of webpack, use a third-party plugin such as [preload-webpack-plugin](https://github.com/GoogleChromeLabs/preload-webpack-plugin).

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

To improve page speed, preload important resources that are discovered late by the browser. Preloading everything would be counterproductive so use `preload` sparingly and [measure the impact in the real-world](/fast#measure-performance-in-the-field).

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: May 27, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/preload-critical-assets/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-preload-critical-assets/" class="w-callout__link w-callout__link--codelab">Codelab: Preload critical assets to improve loading speed</a>
-   <a href="/codelab-preload-web-fonts/" class="w-callout__link w-callout__link--codelab">Preload web fonts to improve loading speed</a>

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
