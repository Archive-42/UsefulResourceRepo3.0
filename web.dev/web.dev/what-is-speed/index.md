<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#what-is-speed" class="w-toc__header--link">What is speed?</a>
-----------------------------------------------------------------------

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

What is speed?
==============

May 1, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Bojan Pavic" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/bojanpavic/)

<a href="/authors/bojanpavic/" class="w-author__name-link">Bojan Pavic</a>

-   <a href="https://github.com/bojanpavic" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Chris Anstey" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/ansteychris/)

<a href="/authors/ansteychris/" class="w-author__name-link">Chris Anstey</a>

-   <a href="https://github.com/ansteychris" class="w-author__link">GitHub</a>

So, speed matters, but what exactly do we mean by it? What does it mean to have a fast site?

It's common to hear people talk in terms of their website loading in x.xx seconds or similar, but a [load is not a single moment in time](https://developers.google.com/web/fundamentals/performance/user-centric-performance-metrics); it's an experience that no single metric can fully capture. There are multiple moments during the load experience that can affect whether a user perceives it as 'fast', and if you just focus solely on one, you might miss bad experiences that happen during the rest of the time.

Rather than measuring load with just one metric, you should time each moment during the experience that affects the user's perception of load speed. When a user navigates to a web page, they're typically looking for certain types of feedback:

<img src="https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format" alt="Image of feedback user is typically looking for" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/NGX9WC2BXTRY6FP5TTGl.png?auto=format&amp;w=1600 1600w" width="800" height="185" />

Traditional performance metrics like load time or DOMContentLoaded time are unreliable, since their occurrence may or may not correspond with these feedback milestones. So, [additional metrics](/lighthouse-performance/#metrics) have emerged that could be used to understand when a page delivers this feedback to its users:

<img src="https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format" alt="Image of speed metrics" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/tz1aubGGvefskjcPfjBQ.png?auto=format&amp;w=1600 1600w" width="800" height="654" />

It's important to understand the different insights offered by these metrics, then establish the ones that are important to your user experience. Some brands even define additional custom metrics specific to the expectations people have of their service. In the case of Pinterest, users want to see images, so they defined a custom metric, [Pinner Wait Time](https://www.youtube.com/watch?v=Xryhxi45Q5M), that combines Time to Interactive and Above the Fold Image load times.

Even though the load is more than one moment in time, it can still be useful to have a single metric for the purposes of simplified reporting or comparison: [Speed Index](/speed-index) and [Lighthouse score](https://developers.google.com/web/tools/lighthouse/v3/scoring) can both be used in this way.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: May 1, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/what-is-speed/index.md)

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
