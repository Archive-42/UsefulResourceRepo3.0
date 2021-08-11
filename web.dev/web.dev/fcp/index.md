<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#first-contentful-paint-(fcp)" class="w-toc__header--link">First Contentful Paint (FCP)</a>
----------------------------------------------------------------------------------------------------

-   [What is FCP?](#what-is-fcp)
-   [What is a good FCP score?](#what-is-a-good-fcp-score)
-   [How to measure FCP](#how-to-measure-fcp)
-   [Field tools](#field-tools)
-   [Lab tools](#lab-tools)
-   [Measure FCP in JavaScript](#measure-fcp-in-javascript)
-   [How to improve FCP](#how-to-improve-fcp)
-   [CHANGELOG](#changelog)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

First Contentful Paint (FCP)
============================

Nov 7, 2019 <span class="w-author__separator">•</span> Updated Jan 18, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/metrics" class="w-post-signpost__link">Metrics</a>

[<img src="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Philip Walton" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/philipwalton/)

<a href="/authors/philipwalton/" class="w-author__name-link">Philip Walton</a>

-   <a href="https://twitter.com/philwalton" class="w-author__link">Twitter</a>
-   <a href="https://github.com/philipwalton" class="w-author__link">GitHub</a>
-   <a href="https://philipwalton.com" class="w-author__link">Blog</a>

First Contentful Paint (FCP) is an important, user-centric metric for measuring [perceived load speed](/user-centric-performance-metrics/#types-of-metrics) because it marks the first point in the page load timeline where the user can see anything on the screen—a fast FCP helps reassure the user that something is [happening](/user-centric-performance-metrics/#questions).

What is FCP? <a href="#what-is-fcp" class="w-headline-link">#</a>
-----------------------------------------------------------------

The First Contentful Paint (FCP) metric measures the time from when the page starts loading to when any part of the page's content is rendered on the screen. For this metric, "content" refers to text, images (including background images), `<svg>` elements, or non-white `<canvas>` elements.

[<img src="https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format" alt="FCP timeline from google.com" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format&amp;w=1600 1600w" width="800" height="311" />](https://web-dev.imgix.net/image/admin/3UhlOxRc0j8Vc4DGd4dt.png?auto=format)

In the above load timeline, FCP happens in the second frame, as that's when the first text and image elements are rendered to the screen.

You'll notice that though some of the content has rendered, not all of it has rendered. This is an important distinction to make between *First* Contentful Paint (FCP) and *[Largest Contentful Paint (LCP)](/lcp/)* —which aims to measure when the page's main contents have finished loading.

<img src="https://web-dev.imgix.net/image/eqprBhZUGfb8WYnumQ9ljAxRrA72/vQKpz0S2SGnnoXHMDidj.svg" alt="Good FCP values are 1.8 seconds or less, poor values are greater than 3.0 seconds and anything in between needs improvement" class="w-screenshot w-screenshot--filled width-full" width="400" height="300" />

### What is a good FCP score? <a href="#what-is-a-good-fcp-score" class="w-headline-link">#</a>

To provide a good user experience, sites should strive to have a First Contentful Paint of **1.8 seconds** or less. To ensure you're hitting this target for most of your users, a good threshold to measure is the **75th percentile** of page loads, segmented across mobile and desktop devices.

How to measure FCP <a href="#how-to-measure-fcp" class="w-headline-link">#</a>
------------------------------------------------------------------------------

FCP can be measured [in the lab](/user-centric-performance-metrics/#in-the-lab) or [in the field](/user-centric-performance-metrics/#in-the-field), and it's available in the following tools:

### Field tools <a href="#field-tools" class="w-headline-link">#</a>

-   [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
-   [Chrome User Experience Report](https://developers.google.com/web/tools/chrome-user-experience-report)
-   [Search Console (Speed Report)](https://webmasters.googleblog.com/2019/11/search-console-speed-report.html)
-   [`web-vitals` JavaScript library](https://github.com/GoogleChrome/web-vitals)

### Lab tools <a href="#lab-tools" class="w-headline-link">#</a>

-   [Lighthouse](https://developers.google.com/web/tools/lighthouse/)
-   [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/)
-   [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)

### Measure FCP in JavaScript <a href="#measure-fcp-in-javascript" class="w-headline-link">#</a>

To measure FCP in JavaScript, you can use the [Paint Timing API](https://w3c.github.io/paint-timing/). The following example shows how to create a [`PerformanceObserver`](https://developer.mozilla.org/en-US/docs/Web/API/PerformanceObserver) that listens for a `paint` entry with the name `first-contentful-paint` and logs it to the console.

    new PerformanceObserver((entryList) => {
      for (const entry of entryList.getEntriesByName('first-contentful-paint')) {
        console.log('FCP candidate:', entry.startTime, entry);
      }
    }).observe({type: 'paint', buffered: true});

**Warning**:

This code shows how to log the `first-contentful-paint` entry to the console, but measuring FCP in JavaScript is more complicated. See below for details:

In the above example, the logged `first-contentful-paint` entry will tell you when the first contentful element was painted. However, in some cases this entry is not valid for measuring FCP.

The following section lists the differences between what the API reports and how the metric is calculated.

#### Differences between the metric and the API <a href="#differences-between-the-metric-and-the-api" class="w-headline-link">#</a>

-   The API will dispatch a `first-contentful-paint` entry for pages loaded in a background tab, but those pages should be ignored when calculating FCP (first paint timings should only be considered if the page was in the foreground the entire time).
-   The API does not report `first-contentful-paint` entries when the page is restored from the [back/forward cache](/bfcache/#impact-on-core-web-vitals), but FCP should be measured in these cases since users experience them as distinct page visits.
-   The API [may not report paint timings from cross-origin iframes](https://w3c.github.io/paint-timing/#:~:text=cross-origin%20iframes), but to properly measure FCP you should consider all frames. Sub-frames can use the API to report their paint timings to the parent frame for aggregation.

Rather than memorizing all these subtle differences, developers can use the [`web-vitals` JavaScript library](https://github.com/GoogleChrome/web-vitals) to measure FCP, which handles these differences for you (where possible):

    import {getFCP} from 'web-vitals';

    // Measure and log FCP as soon as it's available.
    getFCP(console.log);

You can refer to [the source code for `getFCP()`](https://github.com/GoogleChrome/web-vitals/blob/master/src/getFCP.ts) for a complete example of how to measure FCP in JavaScript.

In some cases (such as cross-origin iframes) it's not possible to measure FCP in JavaScript. See the [limitations](https://github.com/GoogleChrome/web-vitals#limitations) section of the `web-vitals` library for details.

How to improve FCP <a href="#how-to-improve-fcp" class="w-headline-link">#</a>
------------------------------------------------------------------------------

To learn how to improve FCP for a specific site, you can run a Lighthouse performance audit and pay attention to any specific [opportunities](/lighthouse-performance/#opportunities) or [diagnostics](/lighthouse-performance/#diagnostics) the audit suggests.

To learn how to improve FCP in general (for any site), refer to the following performance guides:

-   [Eliminate render-blocking resources](/render-blocking-resources/)
-   [Minify CSS](/unminified-css/)
-   [Remove unused CSS](/unused-css-rules/)
-   [Preconnect to required origins](/uses-rel-preconnect/)
-   [Reduce server response times (TTFB)](/time-to-first-byte/)
-   [Avoid multiple page redirects](/redirects/)
-   [Preload key requests](/uses-rel-preload/)
-   [Avoid enormous network payloads](/total-byte-weight/)
-   [Serve static assets with an efficient cache policy](/uses-long-cache-ttl/)
-   [Avoid an excessive DOM size](/dom-size/)
-   [Minimize critical request depth](/critical-request-chains/)
-   [Ensure text remains visible during webfont load](/font-display/)
-   [Keep request counts low and transfer sizes small](/resource-summary/)

CHANGELOG <a href="#changelog" class="w-headline-link">#</a>
------------------------------------------------------------

Occasionally, bugs are discovered in the APIs used to measure metrics, and sometimes in the definitions of the metrics themselves. As a result, changes must sometimes be made, and these changes can show up as improvements or regressions in your internal reports and dashboards.

To help you manage this, all changes to either the implementation or definition of these metrics will be surfaced in this [CHANGELOG](http://bit.ly/chrome-speed-metrics-changelog).

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/metrics/" class="w-chip">Metrics</a>

<span class="w-mr--sm">Last updated: Jan 18, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/metrics/fcp/index.md)

<a href="/metrics" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
