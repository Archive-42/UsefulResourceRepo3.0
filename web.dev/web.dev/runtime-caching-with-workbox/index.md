





<a href="#runtime-caching-with-workbox" class="w-toc__header--link">Runtime caching with Workbox</a>
----------------------------------------------------------------------------------------------------

-   [Getting strategic](#getting-strategic)
-   [Network-first](#network-first)
-   [Cache-first](#cache-first)
-   [Stale-while-revalidate](#stale-while-revalidate)
-   [Why should you use Workbox?](#why-should-you-use-workbox)
-   [Which of your assets should be cached, with which strategies?](#which-of-your-assets-should-be-cached-with-which-strategies)
-   [Use stale-while-revalidate to prioritize reliability over freshness](#use-stale-while-revalidate-to-prioritize-reliability-over-freshness)
-   [Use network-first to prioritize freshness over reliability](#use-network-first-to-prioritize-freshness-over-reliability)
-   [Use cache-first for versioned URLs](#use-cache-first-for-versioned-urls)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Runtime caching with Workbox
============================

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

-   <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
-   <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
-   <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

Runtime caching refers to gradually adding responses to a cache "as you go". While runtime caching doesn't help with the reliability of the *current* request, it can help make *future* requests for the same URL more reliable.

The browser's HTTP cache is an example of runtime caching; it's only populated after a request for a given URL. But service workers allow you to implement runtime caching that goes beyond what the HTTP cache alone can offer.

Getting strategic <a href="#getting-strategic" class="w-headline-link">#</a>
----------------------------------------------------------------------------

As opposed to [precaching](/precache-with-workbox/) (which always tries to serve a set of predefined files from a cache), runtime caching can combine network and cache access in multiple ways. Each combination is generally referred to as a caching strategy. Key caching strategies include:

-   Network-first
-   Cache-first
-   Stale-while-revalidate

### Network-first <a href="#network-first" class="w-headline-link">#</a>

In this approach, your service worker first attempts to retrieve a response from the network. If the network request succeeds, great! The response is returned to your web app, and a copy of the response is stored using the Cache Storage API—either creating a new entry, or updating a previous entry for the same URL.

<img src="https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format" alt="Diagram showing the request going from the page to the service worker and from the service worker to the network. The network request fails so the request goes to the cache." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/AyTKqrG1aBH2JOkz3LzL.png?auto=format&amp;w=1600 1600w" width="800" height="388" />

If the network request fails entirely, or [takes too long](https://developers.google.com/web/tools/workbox/guides/common-recipes#force_a_timeout_on_network_requests) to return a response, then the most recent response from the cache is returned instead.

### Cache-first <a href="#cache-first" class="w-headline-link">#</a>

A cache-first strategy is effectively the opposite of network-first. In this approach, when your service worker intercepts a request, it first uses the Cache Storage API to see whether there's a cached response available. If there is, that response is returned to the web app.

If there's a cache miss, though, then the service worker will go to the network and attempt to retrieve a response there. Assuming that network request is successful, it's returned to your web app and a copy is saved in a cache. This cached copy will be used to bypass the network the next time a request for the same URLs is made.

<img src="https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format" alt="Diagram showing the request going from the page to the service worker and from the service worker to the cache. The cache request fails so the request goes to the network." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/HR4BhK1uWqjve9bC5h6u.png?auto=format&amp;w=1600 1600w" width="800" height="395" />

### Stale-while-revalidate <a href="#stale-while-revalidate" class="w-headline-link">#</a>

Stale-while-revalidate is something of a hybrid. When using it, your service worker will immediately check for a cached response and, if one is found, pass it back to your web app.

In the meantime, regardless of whether there was a cache match, your service worker also fires off a network request to get back a "fresh" response. This response is used to update any previously cached response. If the initial cache check was a miss, a copy of the network response is also passed back to your web app.

<img src="https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format" alt="Diagram showing the request going from the page to the service worker and from the service worker to the cache. The cache immediately returns a response while also fetching an update from the network for future requests." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/lPpEfVFxdd9qGqLIx1gy.png?auto=format&amp;w=1600 1600w" width="800" height="388" />

### Why should you use Workbox? <a href="#why-should-you-use-workbox" class="w-headline-link">#</a>

These caching strategies amount to recipes that you would normally have to rewrite in your own service worker, again and again. Instead of resorting to that, Workbox offers them packaged up as part of its [strategies library](https://developers.google.com/web/tools/workbox/modules/workbox-strategies), ready for you to drop in to your service worker.

Workbox also provides versioning support, allowing you to automatically [expire](https://developers.google.com/web/tools/workbox/modules/workbox-cache-expiration) cached entries, or notify your web app when [updates](https://developers.google.com/web/tools/workbox/modules/workbox-broadcast-cache-update) to a previously cached entry occur.

Which of your assets should be cached, with which strategies? <a href="#which-of-your-assets-should-be-cached-with-which-strategies" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------------------------------------------

Runtime caching can be viewed as a complement to precaching. If all of your assets are already being precached, then you're done—there's nothing that needs to be cached at runtime. Chances are, for any relatively complex web app, you're not going to be precaching *everything* though.

Larger media files, assets that are served from a third-party host like a CDN, or API responses, are just a few examples of the types of assets that can't be effectively precached. Use the Network panel in DevTools to identify requests that fall into this category, and for each of them, think about what tradeoff of freshness vs. reliability is appropriate.

### Use stale-while-revalidate to prioritize reliability over freshness <a href="#use-stale-while-revalidate-to-prioritize-reliability-over-freshness" class="w-headline-link">#</a>

Since a stale-while-revalidate strategy returns a cached response almost immediately—after the cache has been populated via the first request—you'll end up seeing reliably fast performance when using this strategy. This comes with the tradeoff of getting back response data that could be stale in comparison to what would have been retrieved from the network. Using this strategy works best for assets like user profile images or the initial API responses used to populate a view, when you know that showing something *immediately* is key, even if it's an older value.

### Use network-first to prioritize freshness over reliability <a href="#use-network-first-to-prioritize-freshness-over-reliability" class="w-headline-link">#</a>

In some sense, using a network-first strategy is admitting defeat in your battle against the network—it's given priority, but that brings with it uncertainty about reliability. For certain types of assets, seeing a fresh response is preferable to getting back stale information. You might prefer freshness when making an API request for the text of an article that is updated frequently, for instance.

By using a network-first strategy inside of a service worker, instead of just going against the network directly, you have the benefit of being able to fall back to *something*, even if it's a potentially stale response. You won't be reliably fast, but at least you'll be reliable while offline.

### Use cache-first for versioned URLs <a href="#use-cache-first-for-versioned-urls" class="w-headline-link">#</a>

In a cache-first strategy, once an entry is cached, it's never updated. For that reason, make sure that you only use it with assets that you know are unlikely to change. In particular, it works best for URLs that contain versioning information—the same sort of URLs that should also be served with a `Cache-Control: max-age=31536000` response header.

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/runtime-caching-with-workbox/index.md)

<a href="/reliable" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
