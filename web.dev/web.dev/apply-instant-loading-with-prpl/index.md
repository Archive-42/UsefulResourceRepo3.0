





## <a href="#apply-instant-loading-with-the-prpl-pattern" class="w-toc__header--link">Apply instant loading with the PRPL pattern</a>

- [Audit your page with Lighthouse](#audit-your-page-with-lighthouse)
- [Preload critical resources](#preload-critical-resources)
- [Render the initial route as soon as possible](#render-the-initial-route-as-soon-as-possible)
- [Pre-cache assets](#pre-cache-assets)
- [Lazy load](#lazy-load)
- [Next Steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Apply instant loading with the PRPL pattern

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

- <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
- <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
- <a href="https://houssein.me/" class="w-author__link">Blog</a>

PRPL is an acronym that describes a pattern used to make web pages load and become interactive, faster:

- **Push** (or **preload**) the most important resources.
- **Render** the initial route as soon as possible.
- **Pre-cache** remaining assets.
- **Lazy load** other routes and non-critical assets.

In this guide, learn how each of these techniques fit together but still can be used independently to achieve performance results.

## Audit your page with Lighthouse <a href="#audit-your-page-with-lighthouse" class="w-headline-link">#</a>

Run Lighthouse to identify opportunities for improvement aligned with the PRPL techniques:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Lighthouse** tab.
3.  Select the **Performance** and **Progressive Web App** checkboxes.
4.  Click **Run Audits** to generate a report.

For more information, see [Discover performance opportunities with Lighthouse](/discover-performance-opportunities-with-lighthouse).

## Preload critical resources <a href="#preload-critical-resources" class="w-headline-link">#</a>

Lighthouse shows the following failed audit if a certain resource is parsed and fetched late:

<img src="https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format" alt="Lighthouse: Preload key requests audit" class="w-screenshot" sizes="(min-width: 745px) 745px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/tgcMfl3HJLmdoERFn7Ji.png?auto=format&amp;w=1490 1490w" width="745" height="97" />

[**Preload**](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content) is a declarative fetch request that tells the browser to request a resource as soon as possible. Preload critical resources by adding a `<link>` tag with `rel="preload"` to the head of your HTML document:

    <link rel="preload" as="style" href="css/style.css">

The browser sets a more appropriate priority level for the resource in order to try to download it sooner while not delaying the `window.onload` event.

For more information about preloading critical resources, refer to the [Preload critical assets](/preload-critical-assets) guide.

## Render the initial route as soon as possible <a href="#render-the-initial-route-as-soon-as-possible" class="w-headline-link">#</a>

Lighthouse provides a warning if there are resources that delay [**First Paint**](https://developers.google.com/web/fundamentals/performance/user-centric-performance-metrics#first_paint_and_first_contentful_paint), the moment when your site renders pixels to the screen:

<img src="https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format" alt="Lighthouse: Eliminate render-blocking resources audit" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/gvj0jlCYbMdpLNtHu0Ji.png?auto=format&amp;w=1600 1600w" width="800" height="111" />

To improve First Paint, Lighthouse recommends inlining critical JavaScript and deferring the rest using [`async`](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/adding-interactivity-with-javascript), as well as inlining critical CSS used above-the-fold. This improves performance by eliminating round-trips to the server to fetch render-blocking assets. However, inline code is harder to maintain from a development perspective and cannot be cached separately by the browser.

Another approach to improve First Paint is to **server-side render** the initial HTML of your page. This displays content immediately to the user while scripts are still being fetched, parsed, and executed. However, this can increase the payload of the HTML file significantly, which can harm [**Time to Interactive**](/interactive), or the time it takes for your application to become interactive and can respond to user input.

There is no single correct solution to reduce the First Paint in your application, and you should only consider inlining styles and server-side rendering if the benefits outweigh the tradeoffs for your application. You can learn more about both of these concepts with the following resources.

- [Optimize CSS Delivery](https://developers.google.com/speed/docs/insights/OptimizeCSSDelivery)
- [What is Server-Side Rendering?](https://www.youtube.com/watch?v=GQzn7XRdzxY)

## <figure><img src="https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/xv1f7ZLKeBZD83Wcw6pd.png?auto=format&amp;w=1600 1600w" width="800" height="1224" /></figure>Pre-cache assets <a href="#pre-cache-assets" class="w-headline-link">#</a>

By acting as a proxy, **service workers** can fetch assets directly from the cache rather than the server on repeat visits. This not only allows users to use your application when they are offline, but also results in faster page load times on repeat visits.

Use a third-party library to simplify the process of generating a service worker unless you have more complex caching requirements than what a library can provide. For example, [Workbox](/workbox) provides a collection of tools that allow you to create and maintain a service worker to cache assets. For more information on service workers and offline reliability, refer to the [service worker guide](/service-workers-cache-storage) in the reliability learning path.

## Lazy load <a href="#lazy-load" class="w-headline-link">#</a>

Lighthouse displays a failed audit if you send too much data over the network.

<img src="https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format" alt="Lighthouse: Has enormous network payloads audit" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/Ml4hOCqfD4kGWfuKYVTN.png?auto=format&amp;w=1600 1600w" width="800" height="99" />

This includes all asset types, but large JavaScript payloads are especially costly due to the time it takes the browser to parse and compile them. Lighthouse also provides a warning for this when appropriate.

<img src="https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format" alt="Lighthouse: JavaScript boot-up time audit" class="w-screenshot" sizes="(min-width: 797px) 797px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/aKDCV8qv3nuTVFt0Txyj.png?auto=format&amp;w=1594 1594w" width="797" height="100" />

To send a smaller JavaScript payload that contains only the code needed when a user initially loads your application, split the entire bundle and [lazy load](/reduce-javascript-payloads-with-code-splitting) chunks on demand.

Once you've managed to split your bundle, preload the chunks that are more important (see the [Preload critical assets](/preload-critical-assets) guide). Preloading ensures more important resources are fetched and downloaded sooner by the browser.

Aside from splitting and loading different JavaScript chunks on demand, Lighthouse also provides an audit for lazy-loading non-critical images.

<img src="https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format" alt="Lighthouse: Defer offscreen images audit" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/sEgLhoYadRCtKFCYVM1d.png?auto=format&amp;w=1600 1600w" width="800" height="90" />

If you load many images on your web page, defer all that are below the fold, or outside the device viewport, when a page is loaded (see [Use lazysizes to lazyload images](/use-lazysizes-to-lazyload-images)).

## Next Steps <a href="#next-steps" class="w-headline-link">#</a>

Now that you understand some of the basic concepts behind the PRPL pattern, continue to the next guide in this section to learn more. It's important to remember that not all of the techniques need to be applied together. Any efforts made with any of the following will provide noticeable performance improvements.

- **Push** (or **preload**) critical resources.
- **Render** the initial route as soon as possible.
- **Pre-cache** remaining assets.
- **Lazy load** other routes and non-critical assets.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/apply-instant-loading-with-prpl/index.md)

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
