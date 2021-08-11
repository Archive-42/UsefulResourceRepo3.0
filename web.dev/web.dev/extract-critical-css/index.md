<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format" alt="A flatlay photo of wrenches and screwdrivers." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/ZC6iWHhgnrSZtPJMfwMh.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#extract-critical-css" class="w-toc__header--link">Extract critical CSS</a>
------------------------------------------------------------------------------------

-   [Overview of tools](#overview-of-tools)
-   [Critical](#critical)
-   [criticalCSS](#criticalcss)
-   [Penthouse](#penthouse)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

-   <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
-   <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

Extract critical CSS
====================

Learn how to improve render times with critical CSS technique.

May 29, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

-   <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
-   <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

The browser must download and parse CSS files before it can show the page, which makes CSS a render-blocking resource. If CSS files are big, or network conditions are poor, requests for CSS files can significantly increase the time it takes for a web page to render.

**Key Term**: Critical CSS is a technique that extracts the CSS for above-the-fold content in order to render content to the user as fast as possible.

<figure><img src="https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/t3Kkvh265zi6naTBga41.png?auto=format&amp;w=1600 1600w" width="800" height="469" /></figure>Above-the-fold is all the content a viewer sees on page load, before scrolling. There is no universally defined pixel height of what is considered above the fold content since there is a myriad of devices and screen sizes.

Inlining extracted styles in the `<head>` of the HTML document eliminates the need to make an additional request to fetch these styles. The remainder of the CSS can be loaded asynchronously.

<figure><img src="https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format" alt="Inlined critical CSS" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/RVU3OphqtjlkrlAtKLEn.png?auto=format&amp;w=1600 1600w" width="800" height="325" /><figcaption>Inlined critical CSS</figcaption></figure>Improving render times can make a huge difference in [perceived performance](https://developers.google.com/web/fundamentals/performance/rail#ux), especially under poor network conditions. On mobile networks, high latency is an issue regardless of bandwidth.

<figure><img src="https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format" alt="Comparison of loading a page with render-blocking CSS (top) and the same page with inlined critical CSS (bottom) on a 3G connection" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/NdQz49RVgdHoh3Fff0yr.png?auto=format&amp;w=1600 1600w" width="800" height="363" /><figcaption>Comparison of loading a page with render-blocking CSS (top) and the same page with inlined critical CSS (bottom) on a 3G connection</figcaption></figure>If you have poor [First Contentful Paint (FCP)](/first-contentful-paint) and see "Eliminate render-blocking resource" opportunity in Lighthouse audits it's a good idea to give critical CSS a go.

<img src="https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format" alt="Lighthouse audit with &#39;Eliminate render-blocking resource&#39; or &#39;Defer unused CSS&#39; opportunities" class="w-screenshot" sizes="(min-width: 743px) 743px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/0xea7menL90lWHwbjZoP.png?auto=format&amp;w=1486 1486w" width="743" height="449" />

**Gotchas!**

Keep in mind that if you inline a large amount of CSS, it delays the transmission of the rest of the HTML document. If everything is prioritized then nothing is. Inlining also has some downsides in that it prevents the browser from caching the CSS for reuse on subsequent page loads, so it's best to use it sparingly.

To minimize the number of roundtrips to first render, aim to keep above-the-fold content under **14 KB** (compressed).

New [TCP](https://hpbn.co/building-blocks-of-tcp/) connections cannot immediately use the full available bandwidth between the client and the server, they all go through [slow-start](https://hpbn.co/building-blocks-of-tcp/#slow-start) to avoid overloading the connection with more data than it can carry. In this process, the server starts the transfer with a small amount of data and if it reaches the client in perfect condition, doubles the amount in the next roundtrip. For most servers, 10 packets or approximately 14 KB is the maximum that can be transferred in the first roundtrip.

The performance impact you can achieve with this technique depends on the type of your website. Generally speaking, the more CSS a site has, the greater the possible impact of inlined CSS.

Overview of tools <a href="#overview-of-tools" class="w-headline-link">#</a>
----------------------------------------------------------------------------

There are a number of great tools that can automatically determine the critical CSS for a page. This is good news because doing this manually would be a tedious process. It requires analysis of the entire DOM to determine the styles that are applied to each element in the viewport.

### Critical <a href="#critical" class="w-headline-link">#</a>

[Critical](https://github.com/addyosmani/critical) extracts, minifies and inlines above-the-fold CSS and is available as [npm module](https://www.npmjs.com/package/critical). It can be used with Gulp (directly) or with Grunt (as a [plugin](https://github.com/bezoerb/grunt-critical)) and there's a [webpack plugin](https://github.com/anthonygore/html-critical-webpack-plugin) too.

It's a simple tool that takes a lot of thinking out of the process. You don't even have to specify the stylesheets, Critical automatically detects them. It also supports extracting critical CSS for multiple screen resolutions.

### criticalCSS <a href="#criticalcss" class="w-headline-link">#</a>

[CriticalCSS](https://github.com/filamentgroup/criticalCSS) is another [npm module](https://www.npmjs.com/package/criticalcss) that extracts above-the-fold CSS. It is also available as a CLI.

It doesn't have options to inline and minify critical CSS, but it does let you force-include rules that don't actually belong in critical CSS and gives you more granular control over including `@font-face` declarations.

### Penthouse <a href="#penthouse" class="w-headline-link">#</a>

[Penthouse](https://github.com/pocketjoso/penthouse) is a good choice if your site or app has a large number of styles or styles which are being dynamically injected into the DOM (common in Angular apps). It uses [Puppeteer](https://github.com/GoogleChrome/puppeteer) under the hood and even features an [online hosted version](https://jonassebastianohlsson.com/criticalpathcssgenerator/) too.

Penthouse doesn't detect stylesheets automatically, you have to specify the HTML and CSS files that you want to generate critical CSS for. The upside is that it's good at running many jobs in parallel.

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/css/" class="w-chip">CSS</a>

<span class="w-mr--sm">Last updated: May 29, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/extract-critical-css/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-extract-and-inline-critical-css/" class="w-callout__link w-callout__link--codelab">Extract and inline critical CSS with Critical</a>

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
