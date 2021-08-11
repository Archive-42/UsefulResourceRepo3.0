<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#identify-resources-loaded-from-the-network" class="w-toc__header--link">Identify resources loaded from the network</a>
--------------------------------------------------------------------------------------------------------------------------------

-   [Know what you load](#know-what-you-load)
-   [Know when you load](#know-when-you-load)
-   [The Name and Type columns help with the what](#the-name-and-type-columns-help-with-the-what)
-   [The Waterfall column helps with the when](#the-waterfall-column-helps-with-the-when)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Identify resources loaded from the network
==========================================

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

-   <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
-   <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
-   <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

The Network panel in your browser's DevTools helps identify what resources are loaded and when they are loaded. Each row in the Network panel corresponds to a specific URL that your web app has loaded.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7TVH0ZV5TBIe5qwNDzAn.png?auto=format&amp;w=1600 1600w" width="800" height="602" /></figure>**Try it**! [Interpret network traffic using Chrome's DevTools](/codelab-explore-network-panel).

This guide uses screenshots and descriptions based on Chrome's DevTools interface. Other browsers support similar functionality, but the overall interface will be different if you're not using Chrome.

Know what you load <a href="#know-what-you-load" class="w-headline-link">#</a>
------------------------------------------------------------------------------

Coming up with the right caching strategies for your web application requires getting a handle on *what* exactly you're loading. When building a reliable web application, the network can be subject to all kinds of dark forces. You need to understand the network's vulnerabilities if you hope to cope with them in your app.

You might think that you already have a pretty good idea as to what your web application loads. If you're just using a small scattering of static HTML, JavaScript, CSS, and image files, that might be true. But as soon as you start mixing in third-party resources hosted on content delivery networks, using dynamic API requests and server-generated responses, the picture quickly becomes murkier.

A caching strategy that makes sense for a few small CSS files probably won't make sense for hundreds of large images, for instance.

Know when you load <a href="#know-when-you-load" class="w-headline-link">#</a>
------------------------------------------------------------------------------

Another part of the overall loading picture is *when* everything gets loaded.

Some requests to the network, such as the [navigation request](https://developer.mozilla.org/en-US/docs/Web/API/Request/mode#Value) for your initial HTML, are made unconditionally as soon as a user visits a given URL. That HTML might contain hardcoded references to critical CSS or JavaScript files that must also load in order to display your interactive page. These requests all sit in your critical loading path. You will need to aggressively cache these to be reliably fast.

Other resources, such as API requests or lazy-loaded assets, might not start to load until well after all of the initial loading is complete. If those requests only happen following a specific sequence of user interactions, then a completely different set of resources might end up being requested across multiple visits to the same page. A less aggressive caching strategy is often appropriate for content that you've identified as being outside the critical loading path.

Advanced techniques outside the scope of this guide, like [](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content), add a twist to this story by giving a head start to what would otherwise be a late-loaded request.

### The Name and Type columns help with the what <a href="#the-name-and-type-columns-help-with-the-what" class="w-headline-link">#</a>

The Name and Type columns help provide a meaningful picture of *what*'s being loaded. The answer to "*what*'s loading?" in the example above is a total of four URLs, each representing a unique type of content.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9wqFFPDtX9BPLvrVOQhc.png?auto=format&amp;w=1600 1600w" width="800" height="602" /></figure>The Name represents the URL that your browser requested—though you'll only see the last portion of the URL's path listed. For example, if `https://example.com/main.css` is loaded, you'd only end up seeing `main.css` listed under Name.

The last few characters of the URL's path, following the period (e.g. "css"), are known as the URL's extension. The URL's extension generally tells you what type of resource is being requested, and maps directly to the information shown in the Type column. For example, `v2.html` is a document, and `main.css` is a stylesheet.

### The Waterfall column helps with the when <a href="#the-waterfall-column-helps-with-the-when" class="w-headline-link">#</a>

Examine the Waterfall column, starting at the top and working your way down. The length of each bar represents the total amount of time that was spent loading each resource. How can you tell the difference between a request that's made as part of the critical loading path and a request that's fired off dynamically, long after the page's initial load is complete?

The first request in the waterfall is always going to be for the HTML document, for example, `v2.html`. All of the subsequent requests will flow (like a waterfall!) from this initial navigation request, based on what images, scripts, and styles the HTML document references.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format" alt="Chrome DevTools&#39; waterfall view." class="w-screenshot" sizes="(min-width: 774px) 774px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FuPs0Rk4nWlSP74FOJ5Q.png?auto=format&amp;w=1548 1548w" width="774" height="244" />

The waterfall shows that as soon as `v2.html` has finished loading, the requests for the assets it references (also referred to as *subresources*) start. The browser can request multiple subresources at the same time, and that's represented by the overlapping bars in the Waterfall column for `main.css` and `logo.svg`. Finally, you can see from the screenshot that `main.js` starts loading last, and it finishes loading after the other three URLs have completed as well.

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/identify-resources-via-network-panel/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-explore-network-panel/" class="w-callout__link w-callout__link--codelab">Explore DevTools Network panel</a>

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
