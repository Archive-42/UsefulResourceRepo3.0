<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#imperative-caching-guide" class="w-toc__header--link">Imperative caching guide</a>
--------------------------------------------------------------------------------------------

-   [Production case](#production-case)
-   [Using Workbox](#using-workbox)
-   [Using browser APIs](#using-browser-apis)
-   [A simple prefetching example](#a-simple-prefetching-example)
-   [Prefetch product detail pages](#prefetch-product-detail-pages)
-   [Beyond JSON data](#beyond-json-data)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Imperative caching guide
========================

Dec 8, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

-   <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
-   <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

[<img src="https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Andrew Guan" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/andrewguan/)

<a href="/authors/andrewguan/" class="w-author__name-link">Andrew Guan</a>

-   <a href="https://github.com/AndrewKGuan" class="w-author__link">GitHub</a>

Some websites might need to communicate to the service worker without the need of being informed about the result. Here are some examples:

-   A page sends the service worker a list of URLs [to prefetch](/instant-navigation-experiences/), so that, when the user clicks on a link the document or page subresources are already available in the cache, making subsequent navigation much faster.
-   The page asks the service worker to retrieve and cache a set of top articles, to have them available for offline purposes.

Delegating these types of non-critical tasks to the service worker has the benefit of freeing up the main thread for better handling more pressing tasks such as responding to user interactions.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format" sizes="(min-width: 565px) 565px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gCpdKiIbSDZBMJEJE2tZ.png?auto=format&amp;w=1130 1130w" width="565" height="264" /></figure>In this guide we'll explore how to implement a **one-way** communication technique from the page to the service worker by using standard browser APIs and the Workbox library. We'll call these types of use cases **imperative caching**.

Check out [Workers overview](/workers-overview/) for a high-level explanation of when to use web workers versus service workers and the rest of the [Communicate with workers](/reliable/#communicate-with-workers) series for guides on other common use cases.

Production case <a href="#production-case" class="w-headline-link">#</a>
------------------------------------------------------------------------

1-800-Flowers.com implemented **imperative caching** (prefetching) with service workers via [`postMessage()`](https://developer.mozilla.org/en-US/docs/Web/API/Worker/postMessage) to prefetch the top items in category pages to speed up subsequent navigation to product detail pages.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format" sizes="(min-width: 400px) 400px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eNMKYuaKnlYu0N3IIhI5.png?auto=format&amp;w=800 800w" width="400" height="203" /></figure>They use a mixed approach to decide which items to prefetch:

-   At page load time they ask the servicer worker to retrieve the JSON data for the top 9 items, and add the resulting response objects to the cache.
-   For the remaining items, they listen to the [`mouseover`](https://developer.mozilla.org/en-US/docs/Web/API/Element/mouseover_event) event, so that, when a user moves the cursor on top of an item, they can trigger a fetch for the resource on "demand".

They use the [Cache API](https://developer.mozilla.org/en-US/docs/Web/API/Cache) to store JSON responses:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format" alt="Prefetching JSON product data from product listing pages in 1-800Flowers.com." sizes="(min-width: 728px) 728px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FH4clAbGShyIdhj4jWdL.png?auto=format&amp;w=1456 1456w" width="728" height="287" /><figcaption>Prefetching JSON product data from product listing pages in 1-800Flowers.com.</figcaption></figure>When the user clicks on an item, the JSON data associated with it can be picked up from the cache, without the need of going to the network, making the navigation faster.

Using Workbox <a href="#using-workbox" class="w-headline-link">#</a>
--------------------------------------------------------------------

[Workbox](https://developers.google.com/web/tools/workbox) provides an easy way to send messages to a service worker, via the [`workbox-window`](https://developers.google.com/web/tools/workbox/modules/workbox-window) package, a set of modules that are intended to run in the window context. They're a complement to the other Workbox packages that run in the service worker.

To communicate the page with the service worker, first obtain a Workbox object reference to the registered service worker:

    const wb = new Workbox('/sw.js');
    wb.register();

Then you can directly send the message declaratively, without the hassle of the getting the registration, checking for activation, or thinking about the underlying communication API:

    wb.messageSW({"type": "PREFETCH", "payload": {"urls": ["/data1.json", "data2.json"]}}); });

The service worker implements a [`message`](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerGlobalScope/message_event) handler to listen to these messages. It can optionally return a response, although, in cases like these, it's not necessary:

    self.addEventListener('message', (event) => {
      if (event.data && event.data.type === 'PREFETCH') {
        // do something
      }
    });

Using browser APIs <a href="#using-browser-apis" class="w-headline-link">#</a>
------------------------------------------------------------------------------

If the Workbox library is not enough for your needs, here is how you can implement window to service worker communication, using browser APIs.

The [postMessage API](https://html.spec.whatwg.org/multipage/workers.html#dom-worker-postmessage) can be used to establish a **one-way** communication mechanism from the page to the service worker.

The page calls [`postMessage()`](https://html.spec.whatwg.org/multipage/workers.html#dom-worker-postmessage) on the service worker interface:

    navigator.serviceWorker.controller.postMessage({
      type: 'MSG_ID',
      payload: 'some data to perform the task',
    });

The service worker implements a [`message`](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerGlobalScope/message_event) handler to listen to these messages.

    self.addEventListener('message', (event) => {
      if (event.data && event.data.type === MSG_ID) {
        // do something
      }
    });

The `{type : ‘MSG_ID'}` attribute is not absolutely required, but it is one way to allow the page to send different types of instructions to the service worker (i.e. 'to prefetch' vs. 'to clear storage'). The service worker can branch into different execution paths based on this flag.

If the operation was successful, the user will be able to get the benefits from it but, if not, it won't alter the main user flow. For example, when 1-800-Flowers.com attempts to precache, the page doesn't need to know whether the service worker succeeded. If it does, then the user will enjoy a faster navigation. If it doesn't the page still needs to navigate to the new page. It's just going to take a little longer.

### A simple prefetching example <a href="#a-simple-prefetching-example" class="w-headline-link">#</a>

One of the most common applications of **imperative caching** is **prefetching**, meaning fetching resources for a given URL, before the user moves to it, in order to speed up navigation.

There are different ways of implementing prefetching in sites:

-   Using [Link prefetch tags](/link-prefetch/) in pages: resources are kept in the browser cache for five minutes, after which the normal `Cache-Control` rules for the resource apply.
-   Complementing the previous technique with [a runtime caching strategy in the service worker](/instant-navigation-experiences/) to extend the lifetime of the prefetch resource beyond this limit.

For relatively simple prefetching scenarios, like prefetching documents, or specific assets (JS, CSS, etc.), those techniques are the best approach.

If additional logic is required, for example, parsing the prefetch resource (a JSON file or page) in order to fetch its internal URLs, it's more appropriate to delegate this task entirely to the service worker.

Delegating these types of operations to the service worker has the following advantages:

-   Offloading the heavy lifting of fetching and post-fetch processing (which will be introduced later) to a secondary thread. By doing this, it frees the main thread to handle more important tasks such as responding to user interactions.
-   Allowing multiple clients (e.g. tabs) to reuse a common functionality, and even calling the service simultaneously without blocking the main thread.

### Prefetch product detail pages <a href="#prefetch-product-detail-pages" class="w-headline-link">#</a>

First use [`postMessage()`](https://developer.mozilla.org/en-US/docs/Web/API/Worker/postMessage) on the service worker interface and pass an array of URLs to cache:

    navigator.serviceWorker.controller.postMessage({
      type: 'PREFETCH',
      payload: {
        urls: [
          'www.exmaple.com/apis/data_1.json',
          'www.exmaple.com/apis/data_2.json',
        ],
      },
    });

In the service worker, implement a [`message`](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerGlobalScope/message_event) handler to intercept and process messages sent by any active tab:

    addEventListener('message', (event) => {
      let data = event.data;
      if (data && data.type === 'PREFETCH') {
        let urls = data.payload.urls;
        for (let i in urls) {
          fetchAsync(urls[i]);
        }
      }
    });

In the previous code we introduced a small helper function called `fetchAsync()` to iterate on the array of URLs and issue a fetch request for each of them:

    async function fetchAsync(url) {
      // await response of fetch call
      let prefetched = await fetch(url);
      // (optionally) cache resources in the service worker storage
    }

When the response is obtained you can rely on the caching headers of the resource. In many cases though, like in product detail pages, resources are not cached (which means, they have a `Cache-control` header of `no-cache`). In cases like these you can override this behavior, by storing the fetched resource in the service worker cache. This has the added benefit of allowing the file to be served in offline scenarios.

### Beyond JSON data <a href="#beyond-json-data" class="w-headline-link">#</a>

Once the JSON data is fetched from a server endpoint, it often contains other URLs that are also worth prefetching, such as an image or other endpoint data that are associated with this first-level data.

Let's say that in our example, the JSON data returned is the information of a grocery shopping site:

    {
      "productName": "banana",
      "productPic": "https://cdn.example.com/product_images/banana.jpeg",
      "unitPrice": "1.99"
     }

Modify the `fetchAsync()` code to iterate over the list of products and cache the hero image for each of them:

    async function fetchAsync(url, postProcess) {
      // await response of fetch call
      let prefetched = await fetch(url);

      //(optionally) cache resource in the service worker cache

      // carry out the post fetch process if supplied
      if (postProcess) {
        await postProcess(prefetched);
      }
    }

    async function postProcess(prefetched) {
      let productJson = await prefetched.json();
      if (productJson && productJson.product_pic) {
        fetchAsync(productJson.product_pic);
      }
    }

You can add some exception handling around this code for situations like 404s. But the beauty of using a service worker to prefetch is that it can fail without much consequence to the page and the main thread. You may also have more elaborate logic in the post-processing of the prefetched content, making it more flexible and decoupled with the data it's handling. The sky's the limit.

**Caution**: Prefetching techniques consume extra bytes for resources that are not immediately needed, so it needs to be applied thoughtfully; only prefetch resources when you are confident that users will need them. Avoid prefetching when users are on slow connections. You can detect that with the [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API).

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

In this article, we covered a common use case of **one-way** communication between page and service worker: **imperative caching**. The examples discussed are only meant for demonstrating one way of using this pattern and the same approach can be applied to other use cases as well, for example, caching top articles on demand for offline consumption, bookmarking, and others.

For more patterns of page and service worker communication, check out:

-   [Broadcast updates](/broadcast-updates-guide): Calling the page from the service worker to inform about important updates (e.g. a new version of the webapp is available).
-   [Two-way communication](/two-way-communication-guide): Delegating a task to a service worker (e.g. a heavy download), and keeping the page informed on the progress.

<a href="/tags/service-worker/" class="w-chip">Service Worker</a> <a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/offline/" class="w-chip">Offline</a>

<span class="w-mr--sm">Last updated: Dec 8, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/imperative-caching-guide/index.md)

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
