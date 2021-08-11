

## <a href="#instant-navigation-experiences" class="w-toc__header--link">Instant navigation experiences</a>

- [Production cases](#production-cases)
- [Implement precaching with Workbox](#implement-precaching-with-workbox)
- [1. Precache static pages and page subresources](#1.-precache-static-pages-and-page-subresources)
- [2. Extend the lifetime of prefetch resources](#2.-extend-the-lifetime-of-prefetch-resources)
- [3. Delegate prefetching to the service worker](#3.-delegate-prefetching-to-the-service-worker)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Instant navigation experiences

Complementing traditional prefetching techniques with service workers.

Jun 23, 2020 <span class="w-author__separator">•</span> Updated Aug 20, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

- <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
- <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

- <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
- <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
- <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/4CxwBoPk1E2KKHDkdY1s.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Gilberto Cocchi" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/4CxwBoPk1E2KKHDkdY1s.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/4CxwBoPk1E2KKHDkdY1s.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/4CxwBoPk1E2KKHDkdY1s.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/4CxwBoPk1E2KKHDkdY1s.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/4CxwBoPk1E2KKHDkdY1s.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/gilbertococchi/)

<a href="/authors/gilbertococchi/" class="w-author__name-link">Gilberto Cocchi</a>

- <a href="https://twitter.com/gilberto_cocchi" class="w-author__link">Twitter</a>
- <a href="https://github.com/gilbertococchi" class="w-author__link">GitHub</a>

Performing a task on a site commonly involves several steps. For example, purchasing a product in an e-commerce website might involve searching for a product, picking an item from the list of results, adding the item to the cart, and completing the operation by checking out.

In technical terms, moving through different pages means making a **navigation request**. As a general rule, you **don't** want to use long-lived `Cache-Control` headers to cache the HTML response for a navigation request. They should normally be satisfied via the network, with `Cache-Control: no-cache`, to ensure that the HTML, along with the chain of subsequent network requests, is (reasonably) fresh. Having to go against the network each time the user navigates to a new page unfortunately means that each navigation might be slow—at the very least, it means that it won't be _reliably_ fast.

To speed up these requests, if you can anticipate the user's action, you can request these pages and assets beforehand and keep them in the cache for a short period of time until the user clicks on these links. This technique is called [prefetching](/link-prefetch/) and it's commonly implemented by adding `<link rel="prefetch">` tags to pages, indicating the resource to prefetch.

In this guide we'll explore different ways in which [service workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) can be used as a complement of traditional prefetching techniques.

## Production cases <a href="#production-cases" class="w-headline-link">#</a>

[MercadoLibre](https://www.mercadolibre.com.ar/) is the biggest e-commerce site in Latin America. To speed up navigations, they dynamically inject `<link rel="prefetch">` tags in some parts of the flow. For example, in listing pages, they fetch the next result page as soon as the user scrolls to the bottom of the listing:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format" sizes="(min-width: 682px) 682px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/80D6QavdktSNb6xnhXE0.png?auto=format&amp;w=1364 1364w" width="682" height="397" /></figure>Prefetched files are requested at the "Lowest" priority and stored in the [HTTP cache](/http-cache/) or the [memory cache](https://calendar.perfplanet.com/2016/a-tale-of-four-caches/) (depending on whether the resource is cacheable or not), for an amount of time that varies by browsers. For example, as of Chrome 85, this value is 5 minutes. Resources are kept around for five minutes, after which the normal `Cache-Control` rules for the resource apply.

Using service worker caching can help you extend the lifetime of prefetch resources beyond the five-minute window.

For example, Italian sports portal [Virgilio Sport](https://sport.virgilio.it/) uses service workers to prefetch the most popular posts in their home page. They also use the [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API) to avoid prefetching for users that are on a 2G connection.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format" sizes="(min-width: 340px) 340px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bqiSoliDKZ9SR1NX2Ek3.png?auto=format&amp;w=680 680w" width="340" height="100" /></figure>As a result of this, over 3 weeks of observation Virgilio Sport witnessed load times for navigation to articles improve **78%**, and the number of article impressions increase **45%**.

## <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format" sizes="(min-width: 536px) 536px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wn7OR4CA21QJUYhs8OUu.png?auto=format&amp;w=1072 1072w" width="536" height="442" /></figure>Implement precaching with Workbox <a href="#implement-precaching-with-workbox" class="w-headline-link">#</a>

In the following section we'll use [Workbox](/workbox/) to show how to implement different caching techniques in the service worker that can be used as a complement to `<link rel="prefetch">`, or even a replacement for it, by delegating this task completely to the service worker.

**Caution**: You must take steps to ensure that adding a service worker to your site doesn't end up actually slowing down your navigations. Starting up the service worker without using it to respond to a navigation request will introduce a small amount of latency (as explained in [Building Faster, More Resilient Apps with Service Workers](https://www.youtube.com/watch?v=25aCD5XL1Jk)). You can mitigate this overhead by enabling a feature called [navigation preload](https://developers.google.com/web/updates/2017/02/navigation-preload), and then using the [network response](https://developers.google.com/web/updates/2017/02/navigation-preload#using_the_preloaded_response) that's been preloaded inside of your fetch event handler.

### 1. Precache static pages and page subresources <a href="#1.-precache-static-pages-and-page-subresources" class="w-headline-link">#</a>

[Precaching](/precache-with-workbox/) is the ability of the service worker to save files to the cache while it's installing.

Precaching sounds similar to prefetching, but it's a different technique. In the first one, the service worker fetches and stores resources (typically static files) while it's installing and keeps them in the cache until a new version of the file is available. In the second, resources are requested ahead of time to have it in the cache for brief periods of time in order to speed up subsequent navigations.

In the following cases precaching is used to achieve a similar goal as prefetching: making navigations faster.

#### Precaching static pages <a href="#precaching-static-pages" class="w-headline-link">#</a>

For pages that are generated at build time (e.g. `about.html`, `contact.html`), or in completely static sites, one can just add the site's documents to the precache list, so they are already available in the cache every time the user accesses them:

    workbox.precaching.precacheAndRoute([
      {url: '/about.html', revision: 'abcd1234'},
      // ... other entries ...
    ]);

#### Precaching page subresources <a href="#precaching-page-subresources" class="w-headline-link">#</a>

Precaching static assets that the different sections of the site might use (e.g. JavaScript, CSS, etc.), is a general best practice and can give an extra boost in prefetching scenarios.

To speed up navigations in an e-commerce site, you can use `<link rel="prefetch">` tags in listing pages to prefetch product detail pages for the first few products of a listing page. If you have already precached the product page subresources, this can make the navigation even faster.

To implement this:

- Add a `<link rel="prefetch">` tag to the page:

<!-- -->

     <link rel="prefetch" href="/phones/smartphone-5x.html" as="document">

- Add the page subresources to the precache list in the service worker:

<!-- -->

    workbox.precaching.precacheAndRoute([
      '/styles/product-page.ac29.css',
      // ... other entries ...
    ]);

### 2. Extend the lifetime of prefetch resources <a href="#2.-extend-the-lifetime-of-prefetch-resources" class="w-headline-link">#</a>

As mentioned earlier, `<link rel="prefetch">` fetches and keeps resources in the HTTP cache for a limited amount of time, after which point the `Cache-Control` rules for a resource apply. As of Chrome 85, this value is 5 minutes.

Service workers allow you to extend the lifetime of the prefetch pages, while providing the added benefit of making those resources available for offline usage.

In the previous example, one could complement the `<link rel="prefetch">` used to prefetch a product page with a [Workbox runtime caching strategy](/runtime-caching-with-workbox/).

To implement that:

- Add a `<link rel="prefetch">` tag to the page:

<!-- -->

     <link rel="prefetch" href="/phones/smartphone-5x.html" as="document">

- Implement a runtime caching strategy in the service worker for these types of requests:

<!-- -->

    new workbox.strategies.StaleWhileRevalidate({
      cacheName: 'document-cache',
      plugins: [
        new workbox.expiration.Plugin({
          maxAgeSeconds: 30 * 24 * 60 * 60, // 30 Days
        }),
      ],
    });

In this case, we have opted to use a [stale-while-revalidate strategy](https://developers.google.com/web/tools/workbox/modules/workbox-strategies#stale-while-revalidate). In this strategy, pages can be requested from both the cache and the network, in parallel. The response comes from the cache if available, otherwise from the network. The cache is always kept up to date with the network response with each successful request.

### 3. Delegate prefetching to the service worker <a href="#3.-delegate-prefetching-to-the-service-worker" class="w-headline-link">#</a>

In most cases the best approach is to use `<link rel="prefetch">`. The tag is a [resource hint](https://www.w3.org/TR/resource-hints/) designed to make prefetching as efficient as possible.

In some cases, though, it might be better to delegate this task completely to the service worker. For example: to prefetch the first few products in a client-side rendered product listing page, one might need to inject several `<link rel="prefetch">` tags dynamically in the page, based on an API response. This can momentarily consume time on the page's main thread and make the implementation more difficult.

In cases like this, use a "page to service worker communication strategy", to delegate the task of prefetching completely to the service worker. This type of communication can be achieved by using [worker.postMessage()](https://html.spec.whatwg.org/multipage/workers.html#dom-worker-postmessage):

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format" sizes="(min-width: 626px) 626px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vokHySREOo6Y3PpxzxRC.png?auto=format&amp;w=1252 1252w" width="626" height="205" /></figure>The [Workbox Window package](https://developers.google.com/web/tools/workbox/modules/workbox-window) simplifies this type of communication, abstracting many details of the underlying call being done.

Prefetching with Workbox Window can be implemented in the following way:

- In the page: call the service worker passing it the type of message, and the list of URLs to prefetch:

<!-- -->

    const wb = new Workbox('/sw.js');
    wb.register();

    const prefetchResponse = await wb.messageSW({type: 'PREFETCH_URLS', urls: […]});

- In the service worker: implement a message handler to issue a `fetch()` request for each URL to prefetch:

<!-- -->

    addEventListener('message', (event) => {
      if (event.data.type === 'PREFETCH_URLS') {
        // Fetch URLs and store them in the cache
      }
    });

<a href="/tags/case-study/" class="w-chip">Case Study</a> <a href="/tags/network/" class="w-chip">Network</a> <a href="/tags/service-worker/" class="w-chip">Service Worker</a>

<span class="w-mr--sm">Last updated: Aug 20, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/instant-navigation-experiences/index.md)

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
