## <a href="#service-workers-and-the-cache-storage-api" class="w-toc__header--link">Service workers and the Cache Storage API</a>

- [Service workers](#service-workers)
- [The Cache Storage API](#the-cache-storage-api)
- [Wait… there's another cache to think about now?](#wait...-there's-another-cache-to-think-about-now)
- [API nuts and bolts](#api-nuts-and-bolts)
- [A quick detour: promises and async/await](#a-quick-detour:-promises-and-asyncawait)
- [Don't deploy that code… yet](#don't-deploy-that-code...-yet)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Service workers and the Cache Storage API

Nov 5, 2018 <span class="w-author__separator">•</span> Updated Feb 27, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

- <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
- <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
- <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

You're locked in a struggle for network reliability. The browser's HTTP cache is your first line of defense, but as you've learned, it's only really effective when loading versioned URLs that you've previously visited. On its own, the HTTP cache is not enough.

Fortunately, two newer tools are available to help turn the tide in your favor: [service workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) and the [Cache Storage API](https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage). Since they're so often used together, it's worth learning about them both at the same time.

## Service workers <a href="#service-workers" class="w-headline-link">#</a>

A service worker is built into the browser and controlled by a bit of extra JavaScript code that you are responsible for creating. You deploy this alongside the other files that make up your actual web application.

A service worker has some special powers. Among other duties, it patiently waits for your web app to make an outgoing request, and then springs into action by intercepting it. What the service worker does with this intercepted request is up to you.

For some requests, the best course of action might be just to allow the request to continue on to the network, just like what would happen if there were no service worker at all.

For other requests, though, you can take advantage of something more flexible than the browser's HTTP cache, and return a reliably fast response without having to worry about the network. That entails using the other piece of the puzzle: the Cache Storage API.

## The Cache Storage API <a href="#the-cache-storage-api" class="w-headline-link">#</a>

The Cache Storage API opens up a whole new range of possibilities, by giving developers complete control over the contents of the cache. Instead of relying on a combination of HTTP headers and the browser's built-in [heuristics](https://httpwg.org/specs/rfc7234.html#heuristic.freshness), the Cache Storage API exposes a code-driven approach to caching. The Cache Storage API is particularly useful when called from your service worker's JavaScript.

### Wait… there's another cache to think about now? <a href="#wait...-there&#39;s-another-cache-to-think-about-now" class="w-headline-link">#</a>

You're probably asking yourself questions like "Do I still need to configure my HTTP headers?" and "What can I do with this new cache that wasn't possible with the HTTP cache?" Don't worry—those are natural reactions.

It's still recommended that you configure the `Cache-Control` headers on your web server, even when you know that you're using the Cache Storage API. You can usually get away with setting `Cache-Control: no-cache` for unversioned URLs, and/or `Cache-Control: max-age=31536000` for URLs that contain versioning information, like hashes.

When populating the Cache Storage API cache, the browser [defaults to checking for existing entries](https://jakearchibald.com/2016/caching-best-practices/#the-service-worker-the-http-cache-play-well-together-dont-make-them-fight) in the HTTP cache, and uses those if found. If you're adding versioned URLs to the Cache Storage API cache, the browser avoids an additional network request. The flip side of this is that if you're using misconfigured `Cache-Control` headers, like specifying a long-lived cache lifetime for an unversioned URL, you can end up [making things worse](https://jakearchibald.com/2016/caching-best-practices/#a-service-worker-can-extend-the-life-of-these-bugs) by adding that stale content to the Cache Storage API. Getting your HTTP cache behavior sorted is a prerequisite for effectively using the Cache Storage API.

As for what's now possible with this new API, the answer is: a lot. Some common uses that would be difficult or impossible with just the HTTP cache include:

- Use a "refresh in the background" approach to cached content, known as stale-while-revalidate.
- Impose a cap on the maximum number of assets to cache, and implement a custom expiration policy to remove items once that limit is reached.
- Compare previously cached and fresh network responses to see if anything's changed, and enable the user to update content (with a button, for example) when data has actually been updated.

Check out [The Cache API: A quick guide](/cache-api-quick-guide/) to learn more.

### API nuts and bolts <a href="#api-nuts-and-bolts" class="w-headline-link">#</a>

There are some things to keep in mind about the API's design:

- [`Request`](https://developer.mozilla.org/en-US/docs/Web/API/Request) objects are used as the unique keys when reading and writing to these caches. As a convenience, you can pass in a URL string like `'https://example.com/index.html'` as the key instead of an actual `Request` object, and the API will automatically handle that for you.
- [`Response`](https://developer.mozilla.org/en-US/docs/Web/API/Response) objects are used as the values in these caches.
- The `Cache-Control` header on a given `Response` is effectively ignored when caching data. There are no automatic, built-in expiration or freshness checks, and once you store an item in the cache, it will persist until your code explicitly removes it. (There are libraries to simplify cache maintenance on your behalf. They'll be covered later on in this series.)
- Unlike with older, synchronous APIs such as [`LocalStorage`](https://developer.mozilla.org/en-US/docs/Web/API/Storage/LocalStorage), all Cache Storage API operations are asynchronous.

## A quick detour: promises and async/await <a href="#a-quick-detour:-promises-and-asyncawait" class="w-headline-link">#</a>

Service workers and the Cache Storage API use [asynchronous programming concepts](<https://en.wikipedia.org/wiki/Asynchrony_(computer_programming)>). In particular, they rely heavily on promises to represent the future result of async operations. You should familiarize yourself with [promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise), and the related [`async`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)/[`await`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await) syntax, before diving in.

**Try it**! [Make an application reliable by registering a service worker](/codelab-service-workers).

## Don't deploy that code… yet <a href="#don&#39;t-deploy-that-code...-yet" class="w-headline-link">#</a>

While they provide an important foundation, and can be used as-is, both service workers and the Cache Storage API are effectively lower-level building blocks, with a number of edge cases and "gotchas". There are some higher-level tools that can help smooth the difficult bits of those APIs, and provide all you need to build a production-ready service worker. The next guide covers one such tool: [Workbox](https://developers.google.com/web/tools/workbox/).

**Success**: Learn while having fun. Check out the new [Service Workies game!](https://serviceworkies.com/).

<span class="w-mr--sm">Last updated: Feb 27, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/service-workers-cache-storage/index.md)

<a href="/reliable" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
