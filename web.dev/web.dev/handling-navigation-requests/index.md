<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format" alt="Picture of a compass." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/YekhsmFaDpnxwhG14CQv.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#handling-navigation-requests" class="w-toc__header--link">Handling navigation requests</a>

- [Different approaches for architectures](#different-approaches-for-architectures)
- [Small static sites](#small-static-sites)
- [Single-page apps](#single-page-apps)
- [Multi-page apps](#multi-page-apps)
- [Everything else](#everything-else)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Handling navigation requests

Respond to navigation requests without waiting on the network by using  
a service worker.

Jul 13, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

- <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
- <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
- <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

Navigation requests are requests for HTML documents made by your browser whenever you enter a new URL in the navigation bar, or follow a link on a page taking you to a new URL. This is where service workers make their biggest impact on performance: if you use a service worker to respond to navigation requests without waiting for the network, you can ensure that navigations are reliably fast, in addition to being resilient when the network is unavailable. This is the single biggest performance win that comes from a service worker, versus what's possible with [HTTP caching](/http-cache/).

As detailed in the [Identify resources loaded from the network](/identify-resources-via-network-panel/) guide, a navigation request is the first of potentially many requests made in the ["waterfall"](https://developers.google.com/web/tools/chrome-devtools/network/reference#waterfall) of network traffic. The HTML that you load via a navigation request kicks off the flow of all other requests for subresources like images, scripts, and styles.

Inside of a service worker's `fetch` event handler, you can determine whether a request is a navigation by checking the `request.mode` property on the `FetchEvent`. If it's set to `'navigate'`, then it's a navigation request.

As a general rule, do not use long-lived `Cache-Control headers` to cache the HTML response for a navigation request. They should normally be satisfied via the network, with `Cache-Control: no-cache`, to ensure that the HTML, along with the chain of subsequent network requests, is (reasonably) fresh. Going against the network each time the user navigates to a new page unfortunately means that each navigation _might_ be slow. At the very least, it means that it won't be _reliably_ fast.

`Cache-Control: no-cache` means the browser must check (or "revalidate") with the server before using a previously cached resource. This requires a round-trip network communication to complete before the resource can be used.

## Different approaches for architectures <a href="#different-approaches-for-architectures" class="w-headline-link">#</a>

Figuring out _how_ to respond to navigation requests while avoiding the network can be tricky. The right approach depends very much on your web site's architecture and the number of unique URLs that users might navigate to.

While there's no one-size-fits all solution, the following general guidelines should help you decide which approach is the most viable.

### Small static sites <a href="#small-static-sites" class="w-headline-link">#</a>

If your web app consists of a relatively small number (think: a couple of dozen) unique URLs, and each of those URLs corresponds to a different static HTML file, then one viable approach is to just cache all of those HTML files, and respond to navigation requests with the appropriate cached HTML.

Using [precaching](/precache-with-workbox/), you can cache the HTML in advance, as soon as the service worker is installed, and update the cached HTML each time you rebuild your site and redeploy your service worker.

Alternatively, if you would rather avoid precaching all of your HTML—perhaps because users tend to navigate to only a subset of URLs on your site—you can use a [stale-while-revalidate](/runtime-caching-with-workbox/#stale-while-revalidate) runtime caching strategy. Be careful about this approach, though, as each individual HTML document is cached and updated separately. Using runtime caching for HTML is most appropriate if you have a small number of URLs that are revisited **frequently** by the same set of users, and if you feel comfortable about those URLs being revalidated independently of each other.

### Single-page apps <a href="#single-page-apps" class="w-headline-link">#</a>

A single-page architecture is frequently used by modern web applications. In it, client-side JavaScript modifies the HTML in response to user actions. This model uses the [History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API) to modify the current URL as the user interacts with the web app, leading to what's effectively a "simulated" navigation. While subsequent navigations might be "fake", the initial navigation is real, and it's still important to make sure that it isn't blocked on the network.

Fortunately, if you're using the single-page architecture, there's a straightforward pattern to follow for serving the initial navigation from the cache: the [application shell](https://developers.google.com/web/fundamentals/architecture/app-shell). In this model, your service worker responds to navigation requests by returning the same, single HTML file that has already been precached—regardless of the URL being requested. This HTML should be bare-bones, consisting of, perhaps, a generic loading indicator or [skeleton content](https://css-tricks.com/building-skeleton-screens-css-custom-properties/). Once the browser has loaded this HTML from the cache, your existing client-side JavaScript takes over, and renders the correct HTML content for the URL from the original navigation request.

Workbox provides the tools that you need to implement this approach; the `navigateFallback option` allows you to specify which HTML document to use as your app shell, along with an optional allow and deny list to limit this behavior to a subset of your URLs.

### Multi-page apps <a href="#multi-page-apps" class="w-headline-link">#</a>

If your web server generates your site's HTML dynamically, or if you have more than a few dozen unique pages, then it's much harder to avoid the network when handling navigation requests. The advice in [Everything else](#everything-else) will likely apply to you.

But for a certain subset of multi-page apps, you might be able to implement a service worker that fully replicates the logic used in your web server to generate HTML. This works best if you can share routing and templating information between the server and service worker environments, and in particular, if your web server uses JavaScript (without relying on [Node.js](https://nodejs.org)-specific features, like file system access).

If your web server falls into that category and you would like to explore one approach to moving HTML generation off the network and into your service worker, the guidance in [Beyond SPAs: alternative architectures for your PWA](https://developers.google.com/web/updates/2018/05/beyond-spa) can get you started.

### Everything else <a href="#everything-else" class="w-headline-link">#</a>

If you can't respond to navigation requests with cached HTML, you must take steps to ensure that adding a service worker to your site (to handle other, non-HTML requests) doesn't end up slowing down your navigations. Starting up the service worker without using it to respond to a navigation request will introduce a small amount of latency (as explained in [Building Faster, More Resilient Apps with Service Worker](https://youtu.be/25aCD5XL1Jk)). You can mitigate this overhead by enabling a feature called [navigation preload](https://developers.google.com/web/updates/2017/02/navigation-preload), and then [using the network response](https://developers.google.com/web/updates/2017/02/navigation-preload#using_the_preloaded_response) that's been preloaded inside of your `fetch` event handler.

Workbox [provides a helper library](https://developers.google.com/web/tools/workbox/modules/workbox-navigation-preload) that feature-detects whether navigation preload is supported, and if so, simplifies the process of telling your service worker to use the network response.

_Photo by [Aaron Burden](https://unsplash.com/@aaronburden?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText) on [Unsplash](https://unsplash.com/s/photos/navigate?utm_source=unsplash&utm_medium=referral&utm_content=creditCopyText),_

<a href="/tags/network/" class="w-chip">Network</a> <a href="/tags/service-worker/" class="w-chip">Service Worker</a> <a href="/tags/offline/" class="w-chip">Offline</a>

<span class="w-mr--sm">Last updated: Jul 13, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/handling-navigation-requests/index.md)

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
