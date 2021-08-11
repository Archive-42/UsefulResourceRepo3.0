<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format" alt="Phone outline with loading image and assets" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/F6VE4QkpCsomiJilTFNG.png?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#browser-level-image-lazy-loading-for-the-web" class="w-toc__header--link">Browser-level image lazy-loading for the web</a>
------------------------------------------------------------------------------------------------------------------------------------

-   [Browser compatibility](#browser-compatibility)
-   [Why browser-level lazy-loading?](#why-browser-level-lazy-loading)
-   [The loading attribute](#the-loading-attribute)
-   [Distance-from-viewport thresholds](#distance-from-viewport-thresholds)
-   [Improved data-savings and distance-from-viewport thresholds](#improved-data-savings-and-distance-from-viewport-thresholds)
-   [Images should include dimension attributes](#images-should-include-dimension-attributes)
-   [Avoid lazy-loading images that are in the first visible viewport](#avoid-lazy-loading-images-that-are-in-the-first-visible-viewport)
-   [Graceful degradation](#graceful-degradation)
-   [FAQ](#faq)
-   [Are there plans to automatically lazy-load images in Chrome?](#are-there-plans-to-automatically-lazy-load-images-in-chrome)
-   [Can I change how close an image needs to be before a load is triggered?](#can-i-change-how-close-an-image-needs-to-be-before-a-load-is-triggered)
-   [Can CSS background images take advantage of the loading attribute?](#can-css-background-images-take-advantage-of-the-loading-attribute)
-   [Is there a downside to lazy-loading images that are within the device viewport?](#is-there-a-downside-to-lazy-loading-images-that-are-within-the-device-viewport)
-   [How does the loading attribute work with images that are in the viewport but not immediately visible (for example: behind a carousel, or hidden by CSS for certain screen sizes)?](#how-does-the-loading-attribute-work-with-images-that-are-in-the-viewport-but-not-immediately-visible-(for-example:-behind-a-carousel-or-hidden-by-css-for-certain-screen-sizes))
-   [What if I'm already using a third-party library or a script to lazy-load images?](#what-if-i'm-already-using-a-third-party-library-or-a-script-to-lazy-load-images)
-   [How do I handle browsers that don't yet support lazy-loading?](#how-do-i-handle-browsers-that-don't-yet-support-lazy-loading)
-   [Is lazy-loading for iframes also supported in Chrome?](#is-lazy-loading-for-iframes-also-supported-in-chrome)
-   [How does browser-level lazy-loading affect advertisements on a web page?](#how-does-browser-level-lazy-loading-affect-advertisements-on-a-web-page)
-   [How are images handled when a web page is printed?](#how-are-images-handled-when-a-web-page-is-printed)
-   [Does Lighthouse recognize browser-level lazy-loading?](#does-lighthouse-recognize-browser-level-lazy-loading)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

-   <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
-   <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

Browser-level image lazy-loading for the web
============================================

Built-in lazy-loading is finally here!

Aug 6, 2019 <span class="w-author__separator">•</span> Updated Jul 16, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Addy Osmani" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/addyosmani/)

<a href="/authors/addyosmani/" class="w-author__name-link">Addy Osmani</a>

-   <a href="https://twitter.com/addyosmani" class="w-author__link">Twitter</a>
-   <a href="https://github.com/addyosmani" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/BTQ1idSEo72TlNRJKmLf.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Mathias Bynens" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BTQ1idSEo72TlNRJKmLf.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BTQ1idSEo72TlNRJKmLf.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BTQ1idSEo72TlNRJKmLf.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BTQ1idSEo72TlNRJKmLf.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BTQ1idSEo72TlNRJKmLf.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mathiasbynens/)

<a href="/authors/mathiasbynens/" class="w-author__name-link">Mathias Bynens</a>

-   <a href="https://twitter.com/mathias" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mathiasbynens" class="w-author__link">GitHub</a>
-   <a href="https://mathiasbynens.be/" class="w-author__link">Blog</a>

Browser-level support for lazy-loading images is now supported on the web! This video shows a [demo](https://mathiasbynens.be/demo/img-loading-lazy) of the feature:

In Chrome 76 onwards, you can use the `loading` attribute to lazy-load images without the need to write custom lazy-loading code or use a separate JavaScript library. Let's dive into the details.

Browser compatibility <a href="#browser-compatibility" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

`<img loading=lazy>` is supported by most popular Chromium-powered browsers (Chrome, Edge, Opera) and [Firefox](https://developer.mozilla.org/en-US/docs/Mozilla/Firefox/Releases/75#HTML). The implementation for WebKit (Safari) [is in progress](https://bugs.webkit.org/show_bug.cgi?id=200764). [caniuse.com](https://caniuse.com/#feat=loading-lazy-attr) has detailed information on cross-browser support. Browsers that do not support the `loading` attribute simply ignore it without side-effects.

Why browser-level lazy-loading? <a href="#why-browser-level-lazy-loading" class="w-headline-link">#</a>
-------------------------------------------------------------------------------------------------------

According to [HTTPArchive](https://httparchive.org/reports/page-weight), images are the most requested asset type for most websites and usually take up more bandwidth than any other resource. At the 90th percentile, sites send about 4.7 MB of images on desktop and mobile. That's a lot of [cat pictures](https://en.wikipedia.org/wiki/Cats_and_the_Internet).

Currently, there are two ways to defer the loading of off-screen images:

-   Using the [Intersection Observer API](https://developers.google.com/web/updates/2016/04/intersectionobserver)
-   Using `scroll`, `resize`, or `orientationchange` [event handlers](https://developers.google.com/web/fundamentals/performance/lazy-loading-guidance/images-and-video/#using_event_handlers_the_most_compatible_way)

Either option can let developers include lazy-loading functionality, and many developers have built third-party libraries to provide abstractions that are even easier to use. With lazy-loading supported directly by the browser, however, there's no need for an external library. Browser-level lazy loading also ensures that deferred loading of images still works even if JavaScript is disabled on the client.

The `loading` attribute <a href="#the-loading-attribute" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------

Today, Chrome already loads images at different priorities depending on where they're located with respect to the device viewport. Images below the viewport are loaded with a lower priority, but they're still fetched as soon as possible.

In Chrome 76+, you can use the `loading` attribute to completely defer the loading of offscreen images that can be reached by scrolling:

    <img src="image.png" loading="lazy" alt="…" width="200" height="200">

Here are the supported values for the `loading` attribute:

-   `auto`: Default lazy-loading behavior of the browser, which is the same as not including the attribute.
-   `lazy`: Defer loading of the resource until it reaches a [calculated distance](#distance-from-viewport-thresholds) from the viewport.
-   `eager`: Load the resource immediately, regardless of where it's located on the page.

**Caution**: Although available in Chromium, the `auto` value is not mentioned in the [specification](https://html.spec.whatwg.org/multipage/urls-and-fetching.html#lazy-loading-attributes). Since it may be subject to change, we recommend not to use it until it gets included.

### Distance-from-viewport thresholds <a href="#distance-from-viewport-thresholds" class="w-headline-link">#</a>

All images that are above the fold—that is, immediately viewable without scrolling—load normally. Those that are far below the device viewport are only fetched when the user scrolls near them.

Chromium's implementation of lazy-loading tries to ensure that offscreen images are loaded early enough so that they have finished loading once the user scrolls near to them. By fetching nearby images before they become visible in the viewport, we maximize the chance they are already loaded by the time they become visible.

Compared to JavaScript lazy-loading libraries, the thresholds for fetching images that scroll into view may be considered conservative. Chromium is looking at better aligning these thresholds with developer expectations.

Experiments conducted using Chrome on Android suggest that on 4G, 97.5% of below-the-fold images that are lazy-loaded were fully loaded within 10ms of becoming visible. Even on slow 2G networks, 92.6% of below-the-fold images were fully loaded within 10ms. This means browser-level lazy-loading offers a stable experience regarding the visibility of elements that are scrolled into view.

The distance threshold is not fixed and varies depending on several factors:

-   The type of image resource being fetched
-   Whether [Lite mode](https://blog.chromium.org/2019/04/data-saver-is-now-lite-mode.html) is enabled on Chrome for Android
-   The [effective connection type](https://googlechrome.github.io/samples/network-information/)

You can find the default values for the different effective connection types in the [Chromium source](https://cs.chromium.org/chromium/src/third_party/blink/renderer/core/frame/settings.json5?l=971-1003&rcl=e8f3cf0bbe085fee0d1b468e84395aad3ebb2cad). These numbers, and even the approach of fetching only when a certain distance from the viewport is reached, may change in the near future as the Chrome team improves heuristics to determine when to begin loading.

In Chrome 77+, you can experiment with these different thresholds by [throttling the network](https://developers.google.com/web/tools/chrome-devtools/network/#throttle) in DevTools. In the meantime, you will need to override the effective connection type of the browser using the `about://flags/#force-effective-connection-type` flag.

Improved data-savings and distance-from-viewport thresholds <a href="#improved-data-savings-and-distance-from-viewport-thresholds" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------------------

As of July 2020, Chrome has made significant improvements to align the image lazy-loading distance-from-viewport thresholds to better meet developer expectations.

On fast connections (e.g 4G), we reduced Chrome's distance-from-viewport thresholds from `3000px` to `1250px` and on slower connections (e.g 3G), changed the threshold from `4000px` to `2500px`. This change achieves two things:

-   `<img loading=lazy>` behaves closer to the experience offered by JavaScript lazy-loading libraries.
-   The new distance-from-viewport thresholds still allow us to guarantee images have probably loaded by the time a user has scrolled to them.

You can find a comparison between the old vs. new distance-from-viewport thresholds for one of our demos on a fast connection (4G) below:

Old thresholds. vs new thresholds:

<figure><img src="https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/xSZMqpbioBRwRTnenK8f.png?auto=format&amp;w=1600 1600w" width="800" height="460" /></figure>and the new thresholds vs. LazySizes (a popular JS lazy-loading library):

<figure><img src="https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/oHMFvflk9aesT7r0iJbx.png?auto=format&amp;w=1600 1600w" width="800" height="355" /></figure>To ensure Chrome users on recent versions also benefit from the new thresholds, we have backported these changes so that Chrome 79 - 85 inclusive also uses them. Please keep this in mind if attempting to compare data-savings from older versions of Chrome to newer ones.

We are committed to working with the web standards community to explore better alignment in how distance-from-viewport thresholds are approached across different browsers.

### Images should include dimension attributes <a href="#images-should-include-dimension-attributes" class="w-headline-link">#</a>

While the browser loads an image, it does not immediately know the image's dimensions, unless these are explicitly specified. To enable the browser to reserve sufficient space on a page for images, it is recommended that all `<img>` tags include both `width` and `height` attributes. Without dimensions specified, [layout shifts](/cls) can occur, which are more noticeable on pages that take some time to load.

    <img src="image.png" loading="lazy" alt="…" width="200" height="200">

Alternatively, specify their values directly in an inline style:

    <img src="image.png" loading="lazy" alt="…" style="height:200px; width:200px;">

The best practice of setting dimensions applies to `<img>` tags regardless of whether or not they are being loaded lazily. With lazy-loading, this can become more relevant. Setting `width` and `height` on images in modern browsers also allows browsers to infer their intrinsic size.

In most scenarios images still lazy-load if dimensions are not included, but there are a few edge cases you should be aware of. Without `width` and `height` specified, image dimensions are 0×0 pixels at first. If you have a gallery of such images, the browser may conclude that all of them fit inside the viewport at the start, as each takes up practically no space and no image is pushed offscreen. In this case the browser determines that all of them are visible to the user and decides to load everything.

Also, [specifying image dimensions decreases the chances of layout shifts happening](https://www.youtube.com/watch?v=4-d_SoCHeWE). If you are unable to include dimensions for your images, lazy-loading them can be a trade-off between saving network resources and potentially being more at risk of layout shift.

While lazy-loading in Chromium is implemented in a way such that images are likely to be loaded once they are visible, there is still a small chance that they might not be loaded yet. In this case, missing `width` and `height` attributes on such images increase their impact on Cumulative Layout Shift.

Take a look at this [demo](https://mathiasbynens.be/demo/img-loading-lazy) to see how the `loading` attribute works with 100 pictures.

Images that are defined using the `<picture>` element can also be lazy-loaded:

    <picture>
      <source media="(min-width: 800px)" srcset="large.jpg 1x, larger.jpg 2x">
      <img src="photo.jpg" loading="lazy">
    </picture>

Although a browser will decide which image to load from any of the `<source>` elements, the `loading` attribute only needs to be included to the fallback `<img>` element.

Avoid lazy-loading images that are in the first visible viewport <a href="#avoid-lazy-loading-images-that-are-in-the-first-visible-viewport" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

You should avoid setting `loading=lazy` for any images that are in the first visible viewport.

It is recommended to only add `loading=lazy` to images which are positioned below the fold, if possible. Images that are eagerly loaded can be fetched right away, while images which are loaded lazily the browser currently needs to wait until it knows where the image is positioned on the page, which relies on the IntersectionObserver to be available.

In Chromium, the impact of images in the initial viewport being marked with `loading=lazy` on Largest Contentful Paint is fairly small, with a regression of &lt;1% at the 75th and 99th percentiles compared to eagerly loaded images.

Generally, any images within the viewport should be loaded eagerly using the browser's defaults. You do not need to specify `loading=eager` for this to be the case for in-viewport images.

    <!-- visible in the viewport -->
    <img src="product-1.jpg" alt="..." width="200" height="200">
    <img src="product-2.jpg" alt="..." width="200" height="200">
    <img src="product-3.jpg" alt="..." width="200" height="200">

    <!-- offscreen images -->
    <img src="product-4.jpg" loading="lazy" alt="..." width="200" height="200">
    <img src="product-5.jpg" loading="lazy" alt="..." width="200" height="200">
    <img src="product-6.jpg" loading="lazy" alt="..." width="200" height="200">

Graceful degradation <a href="#graceful-degradation" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

Browsers that do not yet support the `loading` attribute will ignore its presence. While these browsers will of course not get the benefits of lazy-loading, including the attribute has no negative impact on them.

FAQ <a href="#faq" class="w-headline-link">#</a>
------------------------------------------------

### Are there plans to automatically lazy-load images in Chrome? <a href="#are-there-plans-to-automatically-lazy-load-images-in-chrome" class="w-headline-link">#</a>

Chromium already automatically lazy-loads any images that are well suited to being deferred if [Lite mode](https://blog.chromium.org/2019/04/data-saver-is-now-lite-mode.html) is enabled on Chrome for Android. This is primarily aimed at users who are conscious about data-savings.

### Can I change how close an image needs to be before a load is triggered? <a href="#can-i-change-how-close-an-image-needs-to-be-before-a-load-is-triggered" class="w-headline-link">#</a>

These values are hardcoded and can't be changed through the API. However, they may change in the future as browsers experiment with different threshold distances and variables.

### Can CSS background images take advantage of the `loading` attribute? <a href="#can-css-background-images-take-advantage-of-the-loading-attribute" class="w-headline-link">#</a>

No, it can currently only be used with `<img>` tags.

### Is there a downside to lazy-loading images that are within the device viewport? <a href="#is-there-a-downside-to-lazy-loading-images-that-are-within-the-device-viewport" class="w-headline-link">#</a>

It is safer to avoid putting `loading=lazy` on above-the-fold images, as Chrome won't preload `loading=lazy` images in the preload scanner.

### How does the `loading` attribute work with images that are in the viewport but not immediately visible (for example: behind a carousel, or hidden by CSS for certain screen sizes)? <a href="#how-does-the-loading-attribute-work-with-images-that-are-in-the-viewport-but-not-immediately-visible-(for-example:-behind-a-carousel-or-hidden-by-css-for-certain-screen-sizes)" class="w-headline-link">#</a>

Only images that are below the device viewport by the [calculated distance](#distance-from-viewport-thresholds) load lazily. All images above the viewport, regardless of whether they're immediately visible, load normally.

### What if I'm already using a third-party library or a script to lazy-load images? <a href="#what-if-i&#39;m-already-using-a-third-party-library-or-a-script-to-lazy-load-images" class="w-headline-link">#</a>

The `loading` attribute should not affect code that currently lazy-loads your assets in any way, but there are a few important things to consider:

1.  If your custom lazy-loader attempts to load images or frames sooner than when Chrome loads them normally—that is, at a distance greater than the [distance-from-viewport thresholds](#distance-from-viewport-thresholds)— they are still deferred and load based on normal browser behavior.
2.  If your custom lazy-loader uses a shorter distance to determine when to load a particular image than the browser, then the behavior would conform to your custom settings.

One of the important reasons to continue to use a third-party library along with `loading="lazy"` is to provide a polyfill for browsers that do not yet support the attribute.

### How do I handle browsers that don't yet support lazy-loading? <a href="#how-do-i-handle-browsers-that-don&#39;t-yet-support-lazy-loading" class="w-headline-link">#</a>

Create a polyfill or use a third-party library to lazy-load images on your site. The `loading` property can be used to detect if the feature is supported in the browser:

    if ('loading' in HTMLImageElement.prototype) {
      // supported in browser
    } else {
      // fetch polyfill/third-party library
    }

For example, [lazysizes](https://github.com/aFarkas/lazysizes) is a popular JavaScript lazy-loading library. You can detect support for the `loading` attribute to load lazysizes as a fallback library only when `loading` isn't supported. This works as follows:

-   Replace `<img src>` with `<img data-src>` to avoid an eager load in unsupported browsers. If the `loading` attribute is supported, swap `data-src` for `src`.
-   If `loading` is not supported, load a fallback (lazysizes) and initiate it. As per lazysizes docs, you use the `lazyload` class as a way to indicate to lazysizes which images to lazy-load.

<!-- -->

    <!-- Let's load this in-viewport image normally -->
    <img src="hero.jpg" alt="…">

    <!-- Let's lazy-load the rest of these images -->
    <img data-src="unicorn.jpg" alt="…" loading="lazy" class="lazyload">
    <img data-src="cats.jpg" alt="…" loading="lazy" class="lazyload">
    <img data-src="dogs.jpg" alt="…" loading="lazy" class="lazyload">

    <script>
      if ('loading' in HTMLImageElement.prototype) {
        const images = document.querySelectorAll('img[loading="lazy"]');
        images.forEach(img => {
          img.src = img.dataset.src;
        });
      } else {
        // Dynamically import the LazySizes library
        const script = document.createElement('script');
        script.src =
          'https://cdnjs.cloudflare.com/ajax/libs/lazysizes/5.1.2/lazysizes.min.js';
        document.body.appendChild(script);
      }
    </script>

Here's a [demo](https://lazy-loading.firebaseapp.com/lazy_loading_lib.html) of this pattern. Try it out in a browser like Firefox or Safari to see the fallback in action.

The lazysizes library also provides a [loading plugin](https://github.com/aFarkas/lazysizes/tree/gh-pages/plugins/native-loading) that uses browser-level lazy-loading when available but falls back to the library's custom functionality when needed.

### Is lazy-loading for iframes also supported in Chrome? <a href="#is-lazy-loading-for-iframes-also-supported-in-chrome" class="w-headline-link">#</a>

`<iframe loading=lazy>` was recently standardized and is already implemented in Chromium. This allows you to lazy-load iframes using the `loading` attribute. A dedicated article about iframe lazy-loading will be published on web.dev shortly.

The `loading` attribute affects iframes differently than images, depending on whether the iframe is hidden. (Hidden iframes are often used for analytics or communication purposes.) Chrome uses the following criteria to determine whether an iframe is hidden:

-   The iframe's width and height are 4 px or smaller.
-   `display: none` or `visibility: hidden` is applied.
-   The iframe is placed off-screen using negative X or Y positioning.

If an iframe meets any of these conditions, Chrome considers it hidden and won't lazy-load it in most cases. Iframes that *aren't* hidden will only load when they're within the [distance-from-viewport thresholds](#distance-from-viewport-thresholds). A placeholder shows for lazy-loaded iframes that are still being fetched.

### How does browser-level lazy-loading affect advertisements on a web page? <a href="#how-does-browser-level-lazy-loading-affect-advertisements-on-a-web-page" class="w-headline-link">#</a>

All ads displayed to the user in the form of an image or iframe lazy-load just like any other image or iframe.

### How are images handled when a web page is printed? <a href="#how-are-images-handled-when-a-web-page-is-printed" class="w-headline-link">#</a>

Although the functionality isn't in Chrome currently, there's an [open issue](https://bugs.chromium.org/p/chromium/issues/detail?id=875403) to ensure that all images and iframes are immediately loaded if a page is printed.

### Does Lighthouse recognize browser-level lazy-loading? <a href="#does-lighthouse-recognize-browser-level-lazy-loading" class="w-headline-link">#</a>

Earlier versions of Lighthouse would still highlight that pages using `loading=lazy` on images required a strategy for loading offscreen images. [Lighthouse 6.0](/lighthouse-whats-new-6.0/) and above better factor in approaches for offscreen image lazy-loading that may use different thresholds, allowing them to pass the [Defer offscreen images](/offscreen-images/) audit.

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

Baking in support for lazy-loading images can make it significantly easier for you to improve the performance of your web pages.

Are you noticing any unusual behavior with this feature enabled in Chrome? [File a bug](https://bugs.chromium.org/p/chromium/issues/entry?summary=%5BLazyLoad%5D:&comment=Application%20Version%20%28from%20%22Chrome%20Settings%20%3E%20About%20Chrome%22%29:%20%0DAndroid%20Build%20Number%20%28from%20%22Android%20Settings%20%3E%20About%20Phone/Tablet%22%29:%20%0DDevice:%20%0D%0DSteps%20to%20reproduce:%20%0D%0DObserved%20behavior:%20%0D%0DExpected%20behavior:%20%0D%0DFrequency:%20%0D%3Cnumber%20of%20times%20you%20were%20able%20to%20reproduce%3E%20%0D%0DAdditional%20comments:%20%0D&labels=Pri-2&components=Blink%3ELoader%3ELazyLoad%2C)!

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jul 16, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/browser-level-image-lazy-loading/index.md)

<a href="/blog" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
