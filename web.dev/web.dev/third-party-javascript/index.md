





<a href="#third-party-javascript-performance" class="w-toc__header--link">Third-party JavaScript performance</a>
----------------------------------------------------------------------------------------------------------------

-   [Performance](#performance)
-   [Network](#network)
-   [Rendering](#rendering)
-   [What to do about it](#what-to-do-about-it)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

-   <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
-   <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

Third-party JavaScript performance
==================================

Find out how third-party JavaScript can affect performance and what you can do to keep it from slowing down your sites.

Aug 13, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

-   <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
-   <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

Third-party JavaScript generally refers to scripts embedded in your website that are:

-   Not authored by you
-   Served from third-party servers

Sites use these scripts for various purposes, including:

-   Social sharing buttons
-   Video player embeds
-   Chat services
-   Advertising iframes
-   Analytics and metrics scripts
-   A/B testing scripts for experiments
-   Helper libraries (like date formatting, animation, and functional libraries)

Third-party scripts can provide powerful functionality, but that's not the whole story. They also affect privacy, security, and page behavior⁠—and they can be particularly problematic for performance.

Performance <a href="#performance" class="w-headline-link">#</a>
----------------------------------------------------------------

Any significant amount of [JavaScript can slow down performance](/bootup-time). But because third-party JavaScript is usually outside your control, it can bring additional issues.

### Network <a href="#network" class="w-headline-link">#</a>

Setting up connections takes time, and sending too many requests to multiple servers causes slowdowns. That time is even longer for secure connections, which may involve DNS lookups, redirects, and several round trips to the final server that handles the user's request.

Third-party scripts often add to network overhead with things such as:

-   Firing additional network requests
-   Pulling in unoptimized images and videos
-   Insufficient [HTTP caching](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/http-caching), which forces frequent fetching of network resources
-   Insufficient [server compression](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/optimize-encoding-and-transfer) of resources
-   Multiple instances of frameworks and libraries pulled in by different third-party embeds

### Rendering <a href="#rendering" class="w-headline-link">#</a>

The way third-party JavaScript is loaded matters a lot. If it's done synchronously in the critical rendering path it delays parsing of the rest of the document.

**Key Term**: The **critical rendering path** includes all resources that the browser needs to display the first screen's worth of content.

If a third party has server issues and fails to deliver a resource, rendering is blocked until the request times out, which can be anywhere from 10 to 80 seconds. You can test and simulate this problem with [WebPageTest Single-Point-of-Failure tests](https://css-tricks.com/use-webpagetest-api/#single-point-of-failure).

[A/B testing scripts](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/loading-third-party-javascript/#ab_test_smaller_samples_of_users) can also often delay rendering. Most of them block content display until they complete processing—which can be true even for asynchronous A/B testing scripts.

What to do about it <a href="#what-to-do-about-it" class="w-headline-link">#</a>
--------------------------------------------------------------------------------

Using third-party JavaScript is often unavoidable, but there are things you can do to minimize adverse effects:

-   When choosing third-party resources, favor those that send the least amount of code while still giving you the functionality you need.
-   Use [performance budgets](/use-lighthouse-for-performance-budgets/) for third-party content to keep their cost in check.
-   Don't use the same functionality from two different vendors. You probably don't need two tag managers or two analytics platforms.
-   Routinely audit and clean out redundant third-party scripts.

To learn how to audit third-party content and load it efficiently for better performance and user experience, check out the other posts in the [Optimize your third-party resources](/fast/#optimize-your-third-party-resources) section.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Aug 13, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/third-party-javascript/index.md)

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
