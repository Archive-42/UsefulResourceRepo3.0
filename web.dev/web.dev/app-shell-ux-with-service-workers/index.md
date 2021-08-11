<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#app-shell-ux-with-service-workers-and-streams" class="w-toc__header--link">App shell UX with service workers and streams</a>
--------------------------------------------------------------------------------------------------------------------------------------

-   [Production case](#production-case)
-   [Implement an app shell UX architecture in MPAs with Workbox](#implement-an-app-shell-ux-architecture-in-mpas-with-workbox)
-   [The server](#the-server)
-   [The service worker](#the-service-worker)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

-   <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
-   <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

App shell UX with service workers and streams
=============================================

Achieving a SPA-like architecture in multi-page apps by combining partials, service workers, and streams.

Jun 23, 2020 <span class="w-author__separator">•</span> Updated Aug 20, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

-   <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
-   <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

-   <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
-   <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
-   <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

[Single-page app (SPA)](https://en.wikipedia.org/wiki/Single-page_application) is an architectural pattern in which the browser runs JavaScript code to update the existing page when the user visits a different section of the site, as opposed to loading an entire new page.

This means that the web app doesn't perform an actual page reload. The [History API](https://developer.mozilla.org/en-US/docs/Web/API/History_API) is used instead to navigate back and forth through the user's history and manipulate the contents of the history stack.

Using this type of architecture can provide an [app shell UX](https://developers.google.com/web/fundamentals/architecture/app-shell) that's fast, reliable, and usually consumes less data when navigating.

In multi-page apps (MPAs) each time a user navigates to a new URL, the browser progressively renders HTML specific to that page. This means a full page refresh every time you visit a new page.

While both are equally valid models to use, you might want to bring some of the benefits of the app shell UX of SPAs to your existing MPA site. In this article we'll analyze how you can achieve an SPA-like architecture in multi-page apps by combining partials, service workers, and streams.

Production case <a href="#production-case" class="w-headline-link">#</a>
------------------------------------------------------------------------

[DEV](https://dev.to/) is a community where software developers write articles, take part in discussions, and build their professional profiles.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Vk2qqXg5PmLV7oCR7xVh.jpg?auto=format&amp;w=1600 1600w" width="800" height="482" /></figure>Their architecture is a multi-page app based on traditional backend templating through Ruby on Rails. Their team was interested in some of the benefits of an app shell model, but didn't want to undertake a major architectural change or move away from their original tech stack.

Here's how their solution works:

1.  First, they create partials of their home page for the header and the footer (`shell_top.html` and `shell_bottom.html`) and deliver them as standalone HTML snippets with an endpoint. These assets are added to the cache at the service worker `install` event (what's commonly referred to as [precaching](/precache-with-workbox/)).
2.  When a navigation request is intercepted by the service worker, they create a [streamed response](https://developer.mozilla.org/en-US/docs/Web/API/ReadableStream) by combining the cached header and footer with the main page content that just came from the server. The body is the only actual part of the page that requires fetching data from the network.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QkGCrnzggZmrp1PXrbHb.png?auto=format&amp;w=1600 1600w" width="800" height="363" /></figure>The key element of this solution is the usage of [streams](https://developers.google.com/web/updates/2016/06/sw-readablestreams), which enables [incremental creations and updates](https://streams.spec.whatwg.org/#intro) of data sources. The Streams API also provides an interface for reading or writing asynchronous chunks of data, only a subset of which might be available in memory at any given time. This way, the header of the page can be rendered as soon as it's picked from the cache, while the rest of the content is being fetched from the network. As a result, the navigation experience is so fast that users don't perceive an actual page refresh, only the new content (the body) being updated.

The resulting UX is similar to the app shell UX pattern of SPAs, implemented on a MPA site.

The previous section contains a quick summary of DEV's solution. For a more detailed explanation check out their [blog post](https://dev.to/devteam/instant-webpages-and-terabytes-of-data-savings-through-the-magic-of-service-workers-1mkc) on this topic.

Implement an app shell UX architecture in MPAs with Workbox <a href="#implement-an-app-shell-ux-architecture-in-mpas-with-workbox" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------------------

In this section we'll cover a summary of the different parts involved in implementing an app shell UX architecture in MPAs. For a more detailed post on how to implement this on a real site, check out [Beyond SPAs: alternative architectures for your PWA](https://developers.google.com/web/updates/2018/05/beyond-spa).

### The server <a href="#the-server" class="w-headline-link">#</a>

#### Partials <a href="#partials" class="w-headline-link">#</a>

The first step is to adopt a site structure based on HTML partials. These are just modular pieces of your pages that can be reused across your site and also delivered as standalone HTML snippets.

The **head partial** can contain all the logic needed to style and render the header of the page. The **navbar partial** can contain the logic for the navigation bar, the **footer partial** the code that needs to execute there, and so forth.

The first time the user visits the site, your server generates a response by assembling the different parts of the page:

    app.get(routes.get('index'), async (req, res) => {
      res.write(headPartial + navbarPartial);
      const tag = req.query.tag || DEFAULT_TAG;
      const data = await requestData(…);
      res.write(templates.index(tag, data.items));
      res.write(footPartial);
      res.end();
    });

By using the `res` (response) object's [write() method](https://nodejs.org/api/http.html#http_response_write_chunk_encoding_callback), and referencing locally stored partial templates, the response can be [streamed](https://github.com/substack/stream-handbook) immediately, without getting blocked by any external data source. The browser takes this initial HTML and renders a meaningful interface and loading message right away.

The next portion of the page uses API data, which involves a network request. The web app can't render anything else until it gets a response back and processes it, but at least users aren't staring at a blank screen while they wait.

### The service worker <a href="#the-service-worker" class="w-headline-link">#</a>

The first time a user visits a site, the header of the page will be rendered faster, without having to wait for the body of the page. The browser still needs to go to the network to fetch the rest of the page.

After the first page load, the service worker is registered, allowing you to fetch the partials for the different static parts of the page (header, navbar, footer, etc.) from the cache.

#### Precaching static assets <a href="#precaching-static-assets" class="w-headline-link">#</a>

The first step is to cache the partial HTML templates, so they are immediately available. With [Workbox precaching](https://developers.google.com/web/tools/workbox/modules/workbox-precaching) you can store these files at the `install` event of the service worker and keep them up to date when changes are deployed to the web app.

Depending on the build process, Workbox has different solutions to generate a service worker and indicate the list of files to precache, including [webpack](https://developers.google.com/web/tools/workbox/modules/workbox-webpack-plugin) and [gulp](https://developers.google.com/web/tools/workbox/guides/codelabs/gulp) plugins, a [generic node module](https://developers.google.com/web/tools/workbox/modules/workbox-build) and a [command line interface](https://developers.google.com/web/tools/workbox/modules/workbox-cli).

For a partials configuration like the one described earlier, the resulting service worker file should contain something similar to the following:

    workbox.precaching.precacheAndRoute([
      {
        url: 'partials/about.html',
        revision: '518747aad9d7e',
      },
      {
        url: 'partials/foot.html',
        revision: '69bf746a9ecc6',
      },
      // etc.
    ]);

#### Streaming <a href="#streaming" class="w-headline-link">#</a>

Next, add the service worker logic so that the precached partial HTML can be sent back to the web app immediately. This is a crucial part of being reliably fast. Using the [Streams API](https://developer.mozilla.org/en-US/docs/Web/API/Streams_API) within our service worker makes that possible. [Workbox Streams](https://developers.google.com/web/tools/workbox/reference-docs/latest/module-workbox-streams) abstracts the details of how streaming works. The package lets you pass to the library a mix of streaming sources, both from caches and runtime data that might come from the network. Workbox takes care of coordinating the individual sources and stitching them together into a single, streaming response.

First, set up the strategies in Workbox to handle the different sources that will make up the streaming response.

    const cacheStrategy = workbox.strategies.cacheFirst({
      cacheName: workbox.core.cacheNames.precache,
    });

    const apiStrategy = workbox.strategies.staleWhileRevalidate({
      cacheName: API_CACHE_NAME,
      plugins: [
        new workbox.expiration.Plugin({maxEntries: 50}),
      ],
    });

-   The first strategy reads data that's been precached, like the partial HTML templates.
-   The second strategy implements the [stale-while-revalidate](https://developers.google.com/web/tools/workbox/modules/workbox-strategies#stale-while-revalidate) caching logic, along with [least-recently-used cache expiration](https://developers.google.com/web/tools/workbox/modules/workbox-expiration#restrict_the_number_of_cache_entries) logic once we reach 50 entries.

Next, tell Workbox how to use the strategies to construct a complete, streaming response, by passing in an array of sources as functions to execute immediately:

    workbox.streams.strategy([
      () => cacheStrategy.handle({
          request: new Request(getCacheKeyForURL("/head.html")),
        }),
      () => cacheStrategy.handle({
          request: new Request(getCacheKeyForURL("/navbar.html")),
        }),
      async ({event, url}) => {
        const tag = url.searchParams.get('tag') || DEFAULT_TAG;
        const listResponse = await apiStrategy.handle(…);
        const data = await listResponse.json();
        return templates.index(tag, data.items);
      },
      () => cacheStrategy.handle({
          request: new Request(getCacheKeyForURL("/foot.html")),
        }),
    ]);

-   The first two sources are precached partial templates read directly from the service worker's cache, so they'll always be available immediately.
-   The next source function fetches data from the network, and processes the response into the HTML that the web app expects.
-   Finally, a cached copy of the footer and closing HTML tags is streamed to complete the response.

Workbox takes the result from each source and streams it to the web app, in sequence, only delaying if the next function in the array hasn't completed yet. As a result, the user immediately sees the page being painted. The experience is so fast that when navigating the header stays in its position without making the user perceive the full page refresh. This is very similar to the UX that the app shell SPA model provides.

<a href="/tags/case-study/" class="w-chip">Case Study</a> <a href="/tags/network/" class="w-chip">Network</a> <a href="/tags/service-worker/" class="w-chip">Service Worker</a>

<span class="w-mr--sm">Last updated: Aug 20, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/app-shell-ux-with-service-workers/index.md)

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
