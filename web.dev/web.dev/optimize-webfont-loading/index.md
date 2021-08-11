





<a href="#optimize-webfont-loading-and-rendering" class="w-toc__header--link">Optimize WebFont loading and rendering</a>
------------------------------------------------------------------------------------------------------------------------

-   [The default behavior](#the-default-behavior)
-   [WebFont loading checklist](#webfont-loading-checklist)
-   [Preload your WebFont resources](#preload-your-webfont-resources)
-   [Automated testing for WebFont loading behavior with Lighthouse](#automated-testing-for-webfont-loading-behavior-with-lighthouse)
-   [Customize the text rendering delay](#customize-the-text-rendering-delay)
-   [The Font Loading API](#the-font-loading-api)
-   [Proper caching is a must](#proper-caching-is-a-must)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Optimize WebFont loading and rendering
======================================

Aug 16, 2019 <span class="w-author__separator">•</span> Updated Jul 3, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Ilya Grigorik" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/ilyagrigorik/)

<a href="/authors/ilyagrigorik/" class="w-author__name-link">Ilya Grigorik</a>

-   <a href="https://twitter.com/igrigorik" class="w-author__link">Twitter</a>
-   <a href="https://github.com/igrigorik" class="w-author__link">GitHub</a>

A "full" WebFont that includes all stylistic variants, which you may not need, plus all the glyphs, which may go unused, can easily result in a multi-megabyte download. In this post you will find out how to optimize loading of WebFonts so visitors only download what they will use.

To address the problem of large files containing all variants, the `@font-face` CSS rule is specifically designed to allow you to split the font family into a collection of resources. For example unicode subsets, and distinct style variants.

Given these declarations, the browser figures out the required subsets and variants and downloads the minimal set required to render the text, which is very convenient. However, if you're not careful, it can also create a performance bottleneck in the critical rendering path and delay text rendering.

### The default behavior <a href="#the-default-behavior" class="w-headline-link">#</a>

Lazy loading of fonts carries an important hidden implication that may delay text rendering: the browser must [construct the render tree](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction), which is dependent on the DOM and CSSOM trees, before it knows which font resources it needs in order to render the text. As a result, font requests are delayed well after other critical resources, and the browser may be blocked from rendering text until the resource is fetched.

<img src="https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format" alt="Font critical rendering path" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/NgSTa9SirmikQAq1G5fN.png?auto=format&amp;w=1600 1600w" width="800" height="303" />

1.  The browser requests the HTML document.
2.  The browser begins parsing the HTML response and constructing the DOM.
3.  The browser discovers CSS, JS, and other resources and dispatches requests.
4.  The browser constructs the CSSOM after all of the CSS content is received and combines it with the DOM tree to construct the render tree.
    -   Font requests are dispatched after the render tree indicates which font variants are needed to render the specified text on the page.
5.  The browser performs layout and paints content to the screen.
    -   If the font is not yet available, the browser may not render any text pixels.
    -   After the font is available, the browser paints the text pixels.

The "race" between the first paint of page content, which can be done shortly after the render tree is built, and the request for the font resource is what creates the "blank text problem" where the browser might render page layout but omits any text.

By preloading WebFonts and using `font-display` to control how browsers behave with unavailable fonts, you can prevent blank pages and layout shifts due to font loading.

### Preload your WebFont resources <a href="#preload-your-webfont-resources" class="w-headline-link">#</a>

If there's a high probability that your page will need a specific WebFont hosted at a URL you know in advance, you can take advantage of [resource prioritization](https://developers.google.com/web/fundamentals/performance/resource-prioritization). Using `<link rel="preload">` will trigger a request for the WebFont early in the critical rendering path, without having to wait for the CSSOM to be created.

### Customize the text rendering delay <a href="#customize-the-text-rendering-delay" class="w-headline-link">#</a>

While preloading makes it more likely that a WebFont will be available when a page's content is rendered, it offers no guarantees. You still need to consider how browsers behave when rendering text that uses a `font-family` which is not yet available.

In the post [Avoid invisible text during font loading](/avoid-invisible-text/) you can see that default browser behavior is not consistent. However, you can tell modern browsers how you want them to behave by using [`font-display`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display).

Similar to the existing font timeout behaviors that some browsers implement, `font-display` segments the lifetime of a font download into three major periods:

1.  The first period is the **font block period**. During this period, if the font face is not loaded, any element attempting to use it must instead render with an invisible fallback font face. If the font face successfully loads during the block period, the font face is then used normally.
2.  The **font swap period** occurs immediately after the font block period. During this period, if the font face is not loaded, any element attempting to use it must instead render with a fallback font face. If the font face successfully loads during the swap period, the font face is then used normally.
3.  The **font failure period** occurs immediately after the font swap period. If the font face is not yet loaded when this period starts, it's marked as a failed load, causing normal font fallback. Otherwise, the font face is used normally.

Understanding these periods means you can use `font-display` to decide how your font should render depending on whether or when it was downloaded.

To work with the `font-display` property, add it to your `@font-face` rules:

    @font-face {
      font-family: 'Awesome Font';
      font-style: normal;
      font-weight: 400;
      font-display: auto; /* or block, swap, fallback, optional */
      src: local('Awesome Font'),
           url('/fonts/awesome-l.woff2') format('woff2'), /* will be preloaded */
           url('/fonts/awesome-l.woff') format('woff'),
           url('/fonts/awesome-l.ttf') format('truetype'),
           url('/fonts/awesome-l.eot') format('embedded-opentype');
      unicode-range: U+000-5FF; /* Latin glyphs */
    }

`font-display` currently supports the following range of values:

-   `auto`
-   `block`
-   `swap`
-   `fallback`
-   `optional`

For more information on preloading fonts, and the `font-display` property, see the following posts:

-   [Avoid invisible text during font loading](/avoid-invisible-text/)
-   [Controlling font performance using font-display](https://developers.google.com/web/updates/2016/02/font-display)
-   [Prevent layout shifting and flashes of invisibile text (FOIT) by preloading optional fonts](/preload-optional-fonts/)

### The Font Loading API <a href="#the-font-loading-api" class="w-headline-link">#</a>

Used together, `<link rel="preload">` and the CSS `font-display` give you a great deal of control over font loading and rendering, without adding in much overhead. But if you need additional customizations, and are willing to incur the overhead introduced by running JavaScript, there is another option.

The [Font Loading API](https://www.w3.org/TR/css-font-loading/) provides a scripting interface to define and manipulate CSS font faces, track their download progress, and override their default lazyload behavior. For example, if you're sure that a particular font variant is required, you can define it and tell the browser to initiate an immediate fetch of the font resource:

    var font = new FontFace("Awesome Font", "url(/fonts/awesome.woff2)", {
      style: 'normal', unicodeRange: 'U+000-5FF', weight: '400'
    });

    // don't wait for the render tree, initiate an immediate fetch!
    font.load().then(function() {
      // apply the font (which may re-render text and cause a page reflow)
      // after the font has finished downloading
      document.fonts.add(font);
      document.body.style.fontFamily = "Awesome Font, serif";

      // OR... by default the content is hidden,
      // and it's rendered after the font is available
      var content = document.getElementById("content");
      content.style.visibility = "visible";

      // OR... apply your own render strategy here...
    });

Further, because you can check the font status (via the [`check()`](https://www.w3.org/TR/css-font-loading/#font-face-set-check)) method and track its download progress, you can also define a custom strategy for rendering text on your pages:

-   You can hold all text rendering until the font is available.
-   You can implement a custom timeout for each font.
-   You can use the fallback font to unblock rendering and inject a new style that uses the desired font after the font is available.

Best of all, you can also mix and match the above strategies for different content on the page. For example, you can delay text rendering on some sections until the font is available, use a fallback font, and then re-render after the font download has finished.

The Font Loading API is [not available in older browsers](http://caniuse.com/#feat=font-loading). Consider using the [FontLoader polyfill](https://github.com/bramstein/fontloader) or the [WebFontloader library](https://github.com/typekit/webfontloader) to deliver similar functionality, albeit with even more overhead from an additional JavaScript dependency.

### Proper caching is a must <a href="#proper-caching-is-a-must" class="w-headline-link">#</a>

Font resources are, typically, static resources that don't see frequent updates. As a result, they are ideally suited for a long max-age expiry— ensure that you specify both a [conditional ETag header](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching#validating-cached-responses-with-etags), and an [optimal Cache-Control policy](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching#cache-control) for all font resources.

If your web application uses a [service worker](https://developers.google.com/web/fundamentals/primers/service-workers/), serving font resources with a [cache-first strategy](https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook/#cache-then-network) is appropriate for most use cases.

You should not store fonts using [`localStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/localStorage) or [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API); each of those has its own set of performance issues. The browser's HTTP cache provides the best and most robust mechanism to deliver font resources to the browser.

WebFont loading checklist <a href="#webfont-loading-checklist" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

-   **Customize font loading and rendering using `<link rel="preload">`, `font-display`, or the Font Loading API:** default lazyloading behavior may result in delayed text rendering. These web platform features allow you to override this behavior for particular fonts, and to specify custom rendering and timeout strategies for different content on the page.
-   **Specify revalidation and optimal caching policies:** fonts are static resources that are infrequently updated. Make sure that your servers provide a long-lived max-age timestamp and a revalidation token to allow for efficient font reuse between different pages. If using a service worker, a cache-first strategy is appropriate.

Automated testing for WebFont loading behavior with Lighthouse <a href="#automated-testing-for-webfont-loading-behavior-with-lighthouse" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse) can help automate the process of making sure that you're following web font optimization best practices.

The following audits can help you make sure that your pages are continuing to follow web font optimization best practices over time:

-   [Preload key requests](/uses-rel-preload/)
-   [Uses inefficient cache policy on static assets](/uses-long-cache-ttl/)
-   [All text remains visible during WebFont loads](/font-display/)

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/fonts/" class="w-chip">Fonts</a>

<span class="w-mr--sm">Last updated: Jul 3, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/optimize-webfont-loading/index.md)

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
