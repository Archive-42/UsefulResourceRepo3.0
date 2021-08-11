## <a href="#service-worker-caching-and-http-caching" class="w-toc__header--link">Service worker caching and HTTP caching</a>

- [Overview of caching flow](#overview-of-caching-flow)
- [Caching layers](#caching-layers)
- [Service worker caching](#service-worker-caching)
- [HTTP caching](#http-caching)
- [Designing your cache expiry logic](#designing-your-cache-expiry-logic)
- [Consistent expiry logic for all cache layers](#consistent-expiry-logic-for-all-cache-layers)
- [Different cache expiry logic at the service worker cache and HTTP layers](#different-cache-expiry-logic-at-the-service-worker-cache-and-http-layers)
- [Conclusion](#conclusion)
- [Learn more](#learn-more)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Service worker caching and HTTP caching

The pros and cons of using consistent or different expiry logic across the service worker cache and HTTP cache layers.

Jul 17, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/DSWao9z2Qq584d9kbjit.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jonathan Chen" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/DSWao9z2Qq584d9kbjit.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/DSWao9z2Qq584d9kbjit.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/DSWao9z2Qq584d9kbjit.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/DSWao9z2Qq584d9kbjit.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/DSWao9z2Qq584d9kbjit.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jonchen/)

<a href="/authors/jonchen/" class="w-author__name-link">Jonathan Chen</a>

- <a href="https://twitter.com/jonchenn" class="w-author__link">Twitter</a>
- <a href="https://github.com/jonchenn" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jonchenn" class="w-author__link">Glitch</a>

While service workers and PWAs are becoming standards of modern web applications, resource caching has become more complex than ever. This article covers the big picture of browser caching, including:

- The use cases of and differences between service worker caching and HTTP caching.
- The pros and cons of different service worker caching expiry strategies compared to regular HTTP caching strategies.

## Overview of caching flow <a href="#overview-of-caching-flow" class="w-headline-link">#</a>

At a high-level, a browser follows the caching order below when it requests a resource:

1.  **Service worker cache**: The service worker checks if the resource is in its cache and decides whether to return the resource itself based on its programmed caching strategies. Note that this does not happen automatically. You need to create a fetch event handler in your service worker and intercept network requests so that the requests are served from the service worker's cache rather than the network.
2.  **HTTP cache (also known as the browser cache)**: If the resource is found in the [HTTP Cache](/http-cache) and has not yet expired, the browser automatically uses the resource from the HTTP cache.
3.  **Server-side:** If nothing is found in the service worker cache or the HTTP cache, the browser goes to the network to request the resource. If the resource isn't cached in a CDN, the request must go all the way back to the origin server.

<img src="https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format" alt="Caching flow" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/vtKWC9Bg9dAMzoFKTeAM.png?auto=format&amp;w=1600 1600w" width="800" height="585" />

Note that some browsers like Chrome have a **memory cache** layer in front of the service worker cache. The details of the memory cache depend on each browser's implementation. Unfortunately, there is no clear specification for this part yet.

## Caching layers <a href="#caching-layers" class="w-headline-link">#</a>

### Service worker caching <a href="#service-worker-caching" class="w-headline-link">#</a>

A service worker intercepts network-type HTTP requests and uses a [caching strategy](https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook#serving-suggestions) to determine what resources should be returned to the browser. The service worker cache and the HTTP cache serve the same general purpose, but the service worker cache offers more caching capabilities, such as fine-grained control over exactly what is cached and how caching is done.

#### Controlling the service worker cache <a href="#controlling-the-service-worker-cache" class="w-headline-link">#</a>

A service worker intercepts HTTP requests with [event listeners](https://github.com/mdn/sw-test/blob/gh-pages/sw.js#L19) (usually the `fetch` event). This [code snippet](https://github.com/mdn/sw-test/blob/gh-pages/sw.js#L19) demonstrates the logic of a [Cache-First](https://developers.google.com/web/tools/workbox/modules/workbox-strategies#cache_first_cache_falling_back_to_network) caching strategy.

<img src="https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format" alt="A diagram showing how service workers intercept HTTP requests" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/INLfnhEpmL4KpMmFXnTL.png?auto=format&amp;w=1600 1600w" width="800" height="516" />

It's highly recommended to use [Workbox](https://developers.google.com/web/tools/workbox) to avoid reinventing the wheel. For example, you can [register resource URL paths with a single line of regex code](https://developers.google.com/web/tools/workbox/modules/workbox-routing#how_to_register_a_regular_expression_route).

    import {registerRoute} from 'workbox-routing';

    registerRoute(new RegExp('styles/.*\\.css'), callbackHandler);

#### Service worker caching strategies and use cases <a href="#service-worker-caching-strategies-and-use-cases" class="w-headline-link">#</a>

The next table outlines common service worker caching strategies and when each strategy is useful.

<table><colgroup><col style="width: 33%" /><col style="width: 33%" /><col style="width: 33%" /></colgroup><thead><tr class="header"><th><strong>Strategies</strong></th><th><strong>Freshness rationale</strong></th><th><strong>Use cases</strong></th></tr></thead><tbody><tr class="odd"><td><strong><a href="https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook#network-only">Network only</a></strong></td><td>The content has to be up-to-date at all times.</td><td><ul><li>Payments and checkouts</li><li>Balance statements</li></ul></td></tr><tr class="even"><td><strong><a href="https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook#network-falling-back-to-cache">Network falling back to cache</a></strong></td><td>It's preferable to serve the fresh content. However if the network fails or is unstable, it's acceptable to serve slightly old content.</td><td><ul><li>Timely data</li><li>Prices and rates (requires disclaimers)</li><li>Order statuses</li></ul></td></tr><tr class="odd"><td><strong><a href="/stale-while-revalidate/">Stale-while-revalidate</a></strong></td><td>It's okay to serve cached content right away, but updated cached content should be used in the future.</td><td><ul><li>News feeds</li><li>Product listing pages</li><li>Messages</li></ul></td></tr><tr class="even"><td><strong><a href="https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook#cache-then-network">Cache first, fall back to network</a></strong></td><td>The content is non-critical and can be served from the cache for performance gains, but the service worker should occasionally check for updates.</td><td><ul><li>App shells</li><li>Common resources</li></ul></td></tr><tr class="odd"><td><strong><a href="https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook#cache-only">Cache only</a></strong></td><td>The content rarely changes.</td><td><ul><li>Static content</li></ul></td></tr></tbody></table>

#### Additional benefits of service worker caching <a href="#additional-benefits-of-service-worker-caching" class="w-headline-link">#</a>

In addition to fine-grained control of caching logic, service worker caching also provides:

- **More memory and storage space for your origin:** The browser allocates HTTP cache resources on a per-[origin](/same-site-same-origin/#origin) basis. In other words, if you have multiple subdomains, they all share the same HTTP cache. There is no guarantee that the content of your origin/domain stays in the HTTP cache for a long time. For example, a user may purge the cache by manually cleaning up from a browser's settings UI, or triggering a hard-reload on a page. With a service worker cache you have a much higher likelihood that your cached content stays cached. See [Persistent storage](https://developers.google.com/web/updates/2016/06/persistent-storage) to learn more.
- **Higher flexibility with flaky networks or offline experiences:** With the HTTP cache you only have a binary choice: either the resource is cached, or not. With service worker caching you can mitigate little "hiccups" much easier (with the "stale-while-revalidate" strategy), offer a complete offline experience (with the "Cache only" strategy) or even something in between, like customized UIs with parts of the page coming from the service worker cache and some parts excluded (with the "Set catch handler" strategy) where appropriate.

### HTTP caching <a href="#http-caching" class="w-headline-link">#</a>

The first time a browser loads a web page and related resources, it stores these resources in its HTTP cache. The HTTP cache is usually enabled automatically by browsers, unless it has been explicitly disabled by the end user.

Using HTTP caching means relying on the server to determine when to cache a resource and for how long.

#### Control HTTP cache expiry with HTTP response headers <a href="#control-http-cache-expiry-with-http-response-headers" class="w-headline-link">#</a>

When a server responds to a browser request for a resource, the server uses HTTP response headers to tell a browser how long it should cache the resource. See [Response headers: configure your web server](/http-cache/#response-headers) to learn more.

#### HTTP caching strategies and use cases <a href="#http-caching-strategies-and-use-cases" class="w-headline-link">#</a>

HTTP caching is much simpler than service worker caching, because HTTP caching only deals with time-based (TTL) resource expiration logic. See [Which response header values should you use?](/http-cache/#response-header-strategies) and [Summary](/http-cache/#summary) to learn more about HTTP caching strategies.

## Designing your cache expiry logic <a href="#designing-your-cache-expiry-logic" class="w-headline-link">#</a>

This section explains the pros and cons of using consistent expiry logic across the service worker cache and HTTP cache layers, as well as the pros and cons of separate expiry logic across these layers.

The Glitch below demonstrates how service worker caching and HTTP caching work in action across different scenarios:

### Consistent expiry logic for all cache layers <a href="#consistent-expiry-logic-for-all-cache-layers" class="w-headline-link">#</a>

To demonstrate the pros and cons, we'll look at 3 scenarios: long-term, medium-term, and short-term.

<table><thead><tr class="header"><th>Scenarios</th><th>Long-term caching</th><th>Medium-term caching</th><th>Short-term caching</th></tr></thead><tbody><tr class="odd"><td>Service worker caching strategy</td><td>Cache, falling back to network</td><td>Stale-while-revalidate</td><td>Network falling back to cache</td></tr><tr class="even"><td>Service worker cache TTL</td><td><strong>30 days</strong></td><td><strong>1 day</strong></td><td><strong>10 mins</strong></td></tr><tr class="odd"><td>HTTP cache max-age</td><td><strong>30 days</strong></td><td><strong>1 day</strong></td><td><strong>10 mins</strong></td></tr></tbody></table>

#### Scenario: Long-term caching (Cache, falling back to network) <a href="#scenario:-long-term-caching-(cache-falling-back-to-network)" class="w-headline-link">#</a>

- When a cached resource is valid (&lt;= 30 days): The service worker returns the cached resource immediately without going to the network.
- When a cached resource is expired (&gt; 30 days): The service worker goes to the network to fetch the resource. The browser doesn't have a copy of the resource in its HTTP cache, so it goes server-side for the resource.

Con: In this scenario, HTTP caching provides less value because the browser will always pass the request to the server-side when the cache expires in the service worker.

#### Scenario: Medium-term caching (Stale-while-revalidate) <a href="#scenario:-medium-term-caching-(stale-while-revalidate)" class="w-headline-link">#</a>

- When a cached resource is valid (&lt;= 1 day): The service worker returns the cached resource immediately, and goes to the network to fetch the resource. The browser has a copy of the resource in its HTTP cache, so it returns that copy to the service worker.
- When a cached resource is expired (&gt; 1 day): The service worker returns the cached resource immediately, and goes to the network to fetch the resource. The browser doesn't have a copy of the resource in its HTTP cache, so it goes server-side to fetch the resource.

Con: The service worker requires additional cache-busting to override the HTTP cache in order to make the most of the "revalidate" step.

#### Scenario: Short-term caching (Network falling back to cache) <a href="#scenario:-short-term-caching-(network-falling-back-to-cache)" class="w-headline-link">#</a>

- When a cached resource is valid (&lt;= 10 mins): The service worker goes to the network to fetch the resource. The browser has a copy of the resource in its HTTP cache so it returns that to the service worker without going server-side.
- When a cached resource is expired (&gt; 10 mins): The service worker returns the cached resource immediately, and goes to the network to fetch the resource. The browser doesn't have a copy of the resource in its HTTP cache, so it goes server-side to fetch the resource.

Con: Similar to the medium-term caching scenario, the service worker requires additional cache-busting logic to override the HTTP cache in order to fetch the latest resource from the server-side.

#### Service worker in all scenarios <a href="#service-worker-in-all-scenarios" class="w-headline-link">#</a>

In all scenarios, the service worker cache can still return cached resources when the network is unstable. On the other hand, the HTTP cache is not reliable when the network is unstable or down.

### Different cache expiry logic at the service worker cache and HTTP layers <a href="#different-cache-expiry-logic-at-the-service-worker-cache-and-http-layers" class="w-headline-link">#</a>

To demonstrate the pros and cons, we'll again look at long-term, medium-term, and short-term scenarios.

<table><thead><tr class="header"><th>Scenarios</th><th>Long-term caching</th><th>Medium-term caching</th><th>Short-term caching</th></tr></thead><tbody><tr class="odd"><td>Service worker caching strategy</td><td>Cache, falling back to network</td><td>Stale-while-revalidate</td><td>Network falling back to cache</td></tr><tr class="even"><td>Service worker cache TTL</td><td><strong>90 days</strong></td><td><strong>30 days</strong></td><td><strong>1 day</strong></td></tr><tr class="odd"><td>HTTP cache max-age</td><td><strong>30 days</strong></td><td><strong>1 day</strong></td><td><strong>10 mins</strong></td></tr></tbody></table>

#### Scenario: Long-term caching (Cache, falling back to network) <a href="#scenario:-long-term-caching-(cache-falling-back-to-network)-2" class="w-headline-link">#</a>

- When a cached resource is valid in the service worker cache (&lt;= 90 days): The service worker returns the cached resource immediately.
- When a cached resource is expired in the service worker cache (&gt; 90 days): The service worker goes to the network to fetch the resource. The browser doesn't have a copy of the resource in its HTTP cache, so it goes server-side.

Pros and cons:

- Pro: Users experience instant response as the service worker returns cached resources immediately.
- Pro: The service worker has more fine-grained control of when to use its cache and when to request new versions of resources.
- Con: A well-defined service worker caching strategy is required.

#### Scenario: Mid-term caching (Stale-while-revalidate) <a href="#scenario:-mid-term-caching-(stale-while-revalidate)" class="w-headline-link">#</a>

- When a cached resource is valid in the service worker cache (&lt;= 30 days): The service worker returns the cached resource immediately.
- When a cached resource is expired in the service worker cache (&gt; 30 days): The service worker goes to the network for the resource. The browser doesn't have a copy of the resource in its HTTP cache, so it goes server-side.

Pros and cons:

- Pro: Users experience instant response as the service worker returns cached resources immediately.
- Pro: The service worker can ensure that the **next** request for a given URL uses a fresh response from the network, thanks to the revalidation that happens "in the background."
- Con: A well-defined service worker caching strategy is required.

#### Scenario: Short-term caching (Network falling back to cache) <a href="#scenario:-short-term-caching-(network-falling-back-to-cache)-2" class="w-headline-link">#</a>

- When a cached resource is valid in the service worker cache (&lt;= 1 day): The service worker goes to the network for the resource. The browser returns the resource from the HTTP cache if it's there. If the network is down, the service worker returns the resource from the service worker cache
- When a cached resource is expired in the service worker cache (&gt; 1 day): The service worker goes to the network to fetch the resource. The browser fetches the resources over the network as the cached version in its HTTP cache is expired.

Pros and cons:

- Pro: When the network is unstable or down, the service worker returns cached resources immediately.
- Con: The service worker requires additional cache-busting to override the HTTP Cache and make "Network first" requests.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

Given the complexity of the combination of caching scenarios, it's not possible to design one rule that covers all cases. However, based on the findings in the previous sections, there are a few suggestions to look at when designing your cache strategies:

- Service worker caching logic doesn't need to be consistent with HTTP caching expiry logic. If possible, use longer expiry logic in the service worker to grant the service worker more control.
- HTTP caching still plays an important role, but it's not reliable when the network is unstable or down.
- Revisit your caching strategies for each resource to make sure your service worker caching strategy provides its value, without conflicting with the HTTP cache.

## Learn more <a href="#learn-more" class="w-headline-link">#</a>

- [Network reliability](/reliable/)
- [Prevent unnecessary network requests with the HTTP Cache](/http-cache)
- [HTTP cache codelab](/codelab-http-cache/)
- [Measuring the real-world performance impact of service workers](https://developers.google.com/web/showcase/2016/service-worker-perf)
- [Cache-Control vs. Expires](https://stackoverflow.com/questions/5799906/what-s-the-difference-between-expires-and-cache-control-headers)

<a href="/tags/network/" class="w-chip">Network</a> <a href="/tags/service-worker/" class="w-chip">Service Worker</a> <a href="/tags/offline/" class="w-chip">Offline</a>

<span class="w-mr--sm">Last updated: Jul 17, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/service-worker-caching-and-http-caching/index.md)

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
