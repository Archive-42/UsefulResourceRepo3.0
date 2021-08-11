<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#what-is-network-reliability-and-how-do-you-measure-it" class="w-toc__header--link">What is network reliability and how do you measure it?</a>
-------------------------------------------------------------------------------------------------------------------------------------------------------

-   [Reliable while offline](#reliable-while-offline)
-   [Reliably fast](#reliably-fast)
-   [Reliable is achievable](#reliable-is-achievable)
-   [Your guiding light: Responds with a 200 OK while offline](#your-guiding-light:-responds-with-a-200-ok-while-offline)
-   [It's a journey](#it's-a-journey)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

What is network reliability and how do you measure it?
======================================================

Nov 5, 2018 <span class="w-author__separator">•</span> Updated Oct 8, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

-   <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
-   <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
-   <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

The modern web is enjoyed by a wide swath of people, using a range of different devices and types of network connections. Your creations can reach users all across the world, but delivering a *reliable* experience on the web for all of your users can be challenging. It can be a challenge just to understand what reliability means.

Reliable while offline <a href="#reliable-while-offline" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------

One way of thinking about reliability is whether your web app will work without a network connection. This is a type of reliability that users take for granted with platform-specific apps installed on a mobile device from an app store. When you see an icon for one of these apps, you expect to be able to tap on it and open up some sort of experience, regardless of whether you're currently connected to the Internet.

Until recently, it's been a challenge to build web applications that are reliable without a network connection.

Reliably fast <a href="#reliably-fast" class="w-headline-link">#</a>
--------------------------------------------------------------------

Another way of thinking about reliability is whether your users can rely on your web app loading at a fast enough speed when they have a network connection that might be less than ideal. Will returning users have the same experience interacting with your web app when they're on a cellular connection as they do when they're on wi-fi? And what about users who have a high-latency, or "[lie-fi](https://developers.google.com/web/fundamentals/performance/poor-connectivity/#lie-fi)" connection. Will your web app be reliably fast even in those scenarios?

It's not enough to be fast under the best circumstances. Your users will view your web app's performance through the lens of how it behaves in all network conditions.

Reliable is achievable <a href="#reliable-is-achievable" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------

The good news is that the modern web platform provides technologies—such as [service workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) and the [Cache Storage API](https://developer.mozilla.org/en-US/docs/Web/API/CacheStorage)—that can serve as the building blocks for creating reliable web applications. They allow you to write code which sits between your web app and the network. In many cases, you can bypass the network entirely, and instead use previously cached content to fulfill your web app's requests.

Your guiding light: Responds with a 200 OK while offline <a href="#your-guiding-light:-responds-with-a-200-ok-while-offline" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------------

Once you start building out a service worker and serving content from caches, it's hard to know if you're doing it effectively. How do you know that the service worker you implement really does help your web app avoid the network? How do you prevent a small change to your caching strategy from breaking your carefully crafted offline experience?

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) provides one specific test that is of particular interest when building a reliable web app: **Responds with a 200 OK while offline**:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5bc5TNicZiBgDdWkgAXg.png?auto=format&amp;w=1600 1600w" width="800" height="253" /></figure>The actual interface may differ depending on which version of Lighthouse you're running.

What's actually being tested here? It boils down to simulating a loss of network connectivity within your browser, followed by an attempt to load whichever URL on your site is being audited. This tests one aspect of building a reliable site—being *reliable while offline*—using a controlled, repeatable sequence of actions.

It's a journey <a href="#it&#39;s-a-journey" class="w-headline-link">#</a>
--------------------------------------------------------------------------

If you're just starting out, then there's a very good chance that you'll get back a negative result for the Responds with a 200 while offline check. That's okay! Unless you're using a customized starter project, web applications don't have that type of reliability by default. The next few guides will introduce the techniques you need to identify what your web app is loading, and teach you how to use Lighthouse to make that loading experience reliable.

Throughout this process, you're encouraged to keep re-running the Lighthouse audits. They serve as a guiding light throughout your journey, starting with a new web application and ending with a reliable progressive web app.

<span class="w-mr--sm">Last updated: Oct 8, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/network-connections-unreliable/index.md)

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
