





<a href="#prioritize-resources" class="w-toc__header--link">Prioritize resources</a>
------------------------------------------------------------------------------------

-   [Default priorities in the browser](#default-priorities-in-the-browser)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Prioritize resources
====================

Aug 17, 2018 <span class="w-author__separator">•</span> Updated Aug 5, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/qexUlvBmj0edRQSlsdGL.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Sérgio Gomes" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/qexUlvBmj0edRQSlsdGL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/qexUlvBmj0edRQSlsdGL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/qexUlvBmj0edRQSlsdGL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/qexUlvBmj0edRQSlsdGL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/qexUlvBmj0edRQSlsdGL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/sgomes/)

<a href="/authors/sgomes/" class="w-author__name-link">Sérgio Gomes</a>

-   <a href="https://twitter.com/sergiomdgomes" class="w-author__link">Twitter</a>

Not every byte that is sent down the wire to the browser has the same degree of importance, and the browser knows this. Browsers have heuristics that attempt to make a best-guess at the most important resources to load first—such as CSS before scripts and images.

That said, as with any heuristic, it doesn't always work out; the browser might make the wrong decision, usually because it doesn't have enough information at that time. There are ways that you can influence this decision-making using `<link rel="preload">`, `<link rel="preconnect">`, and `<link rel="prefetch">`.

Default priorities in the browser <a href="#default-priorities-in-the-browser" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

The browser assigns different relative priorities to different types of resources based on how critical they might be. So, for example, a `<script>` tag in your page's `<head>` would be loaded in Chrome at a **High** priority (below CSS, at **Highest**), but that priority would change to **Low** if it has the `async` attribute (meaning it can be loaded and run asynchronously).

Priorities become important when investigating loading performance in your site. Beyond the usual techniques of [measuring](https://developers.google.com//web/fundamentals/performance/critical-rendering-path/measure-crp) and [analyzing the critical rendering path](https://developers.google.com//web/fundamentals/performance/critical-rendering-path/analyzing-crp), it's useful to know Chrome's priority for each resource. You can find that in the **Network** panel in Chrome DevTools. Here's what it looks like:

<figure><img src="https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format" alt="The Priority column, which is hidden by default (see Add or remove columns ." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/oqcdfVAVj2RajVWfs6ap.png?auto=format&amp;w=1600 1600w" width="800" height="249" /><figcaption>The <strong>Priority</strong> column, which is hidden by default (see <a href="https://developers.google.com/web/tools/chrome-devtools/network/reference#columns">Add or remove columns</a> .</figcaption></figure>These priorities give you an idea of how much relative importance the browser attributes to each resource. And remember that subtle differences are enough for the browser to assign a different priority; for example, an image that is part of the initial render is prioritized higher than an image that starts offscreen. If you're curious about priorities, [Preload, Prefetch And Priorities in Chrome](https://medium.com/reloading/preload-prefetch-and-priorities-in-chrome-776165961bbf) digs a lot deeper into the current state of priorities in Chrome.

So what can you do if you find any resources that are marked with a different priority than the one you'd want?

There are three different declarative solutions, which are all relatively new `<link>` types.

-   [`<link rel="preload">`](/preload-critical-assets/) informs the browser that a resource is needed as part of the current navigation, and that it should start getting fetched as soon as possible.
-   [`<link rel="preconnect">`](/preconnect-and-dns-prefetch/) informs the browser that your page intends to establish a connection to another origin, and that you'd like the process to start as soon as possible.
-   [`<link rel="prefetch">`](/link-prefetch/) is somewhat different from `<link rel="preload">` and `<link rel="preconnect">`, in that it doesn't try to make something critical happen faster; instead, it tries to make something non-critical happen earlier, if there's a chance.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Aug 5, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/prioritize-resources/index.md)

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
