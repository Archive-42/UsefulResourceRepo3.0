





<a href="#total-blocking-time-(tbt)" class="w-toc__header--link">Total Blocking Time (TBT)</a>
----------------------------------------------------------------------------------------------

-   [What is TBT?](#what-is-tbt)
-   [How does TBT relate to TTI?](#how-does-tbt-relate-to-tti)
-   [How to measure TBT](#how-to-measure-tbt)
-   [Lab tools](#lab-tools)
-   [What is a good TBT score?](#what-is-a-good-tbt-score)
-   [How to improve TBT](#how-to-improve-tbt)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Total Blocking Time (TBT)
=========================

Nov 7, 2019 <span class="w-author__separator">•</span> Updated Jun 15, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/metrics" class="w-post-signpost__link">Metrics</a>

[<img src="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Philip Walton" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/philipwalton/)

<a href="/authors/philipwalton/" class="w-author__name-link">Philip Walton</a>

-   <a href="https://twitter.com/philwalton" class="w-author__link">Twitter</a>
-   <a href="https://github.com/philipwalton" class="w-author__link">GitHub</a>
-   <a href="https://philipwalton.com" class="w-author__link">Blog</a>

Total Blocking Time (TBT) is an important [lab metric](/user-centric-performance-metrics/#in-the-lab) for measuring [load responsiveness](/user-centric-performance-metrics/#types-of-metrics) because it helps quantify the severity of how non-interactive a page is prior to it becoming reliably interactive—a low TBT helps ensure that the page is [usable](/user-centric-performance-metrics/#questions).

What is TBT? <a href="#what-is-tbt" class="w-headline-link">#</a>
-----------------------------------------------------------------

The Total Blocking Time (TBT) metric measures the total amount of time between [First Contentful Paint (FCP)](/fcp/) and [Time to Interactive (TTI)](/tti/) where the main thread was blocked for long enough to prevent input responsiveness.

The main thread is considered "blocked" any time there's a [Long Task](/custom-metrics/#long-tasks-api)—a task that runs on the main thread for more than 50 milliseconds (ms). We say the main thread is "blocked" because the browser cannot interrupt a task that's in progress. So in the event that a user *does* interact with the page in the middle of a long task, the browser must wait for the task to finish before it can respond.

If the task is long enough (e.g. anything above 50 ms), it's likely that the user will notice the delay and perceive the page as sluggish or janky.

The *blocking time* of a given long task is its duration in excess of 50 ms. And the *total blocking time* for a page is the sum of the *blocking time* for each long task that occurs between FCP and TTI.

For example, consider the following diagram of the browser's main thread during page load:

[<img src="https://web-dev.imgix.net/image/admin/clHG8Yv239lXsGWD6Iu6.svg" alt="A tasks timeline on the main thread" width="800" height="156" />](https://web-dev.imgix.net/image/admin/clHG8Yv239lXsGWD6Iu6.svg)

The above timeline has five tasks, three of which are Long Tasks because their duration exceeds 50 ms. The next diagram shows the blocking time for each of the long tasks:

[<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xKxwKagiz8RliuOI2Xtc.svg" alt="A tasks timeline on the main thread showing blocking time" width="800" height="156" />](https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xKxwKagiz8RliuOI2Xtc.svg)

So while the total time spent running tasks on the main thread is 560 ms, only 345 ms of that time is considered blocking time.

Task duration

Task blocking time

Task one

250 ms

200 ms

Task two

90 ms

40 ms

Task three

35 ms

0 ms

Task four

30 ms

0 ms

Task five

155 ms

105 ms

**Total Blocking Time**

**345 ms**

### How does TBT relate to TTI? <a href="#how-does-tbt-relate-to-tti" class="w-headline-link">#</a>

TBT is a great companion metric for TTI because it helps quantify the severity of how non-interactive a page is prior it to becoming reliably interactive.

TTI considers a page "reliably interactive" if the main thread has been free of long tasks for at least five seconds. This means that three, 51 ms tasks spread out over 10 seconds can push back TTI just as far as a single 10-second long task—but those two scenarios would feel very different to a user trying to interact with the page.

In the first case, three, 51 ms tasks would have a TBT of **3 ms**. Whereas a single, 10-second long tasks would have a TBT of **9950 ms**. The larger TBT value in the second case quantifies the worse experience.

How to measure TBT <a href="#how-to-measure-tbt" class="w-headline-link">#</a>
------------------------------------------------------------------------------

TBT is a metric that should be measured [in the lab](/user-centric-performance-metrics/#in-the-lab). The best way to measure TBT is to run a Lighthouse performance audit on your site. See the [Lighthouse documentation on TBT](/lighthouse-total-blocking-time) for usage details.

### Lab tools <a href="#lab-tools" class="w-headline-link">#</a>

-   [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/)
-   [Lighthouse](https://developers.google.com/web/tools/lighthouse/)
-   [WebPageTest](https://www.webpagetest.org/)

While it is possible to measure TBT in the field, it's not recommended as user interaction can affect your page's TBT in ways that lead to lots of variance in your reports. To understand a page's interactivity in the field, you should measure [First Input Delay (FID)](/fid/).

What is a good TBT score? <a href="#what-is-a-good-tbt-score" class="w-headline-link">#</a>
-------------------------------------------------------------------------------------------

To provide a good user experience, sites should strive to have a Total Blocking Time of less than **300 milliseconds** when tested on **average mobile hardware**.

For details on how your page's TBT affects your Lighthouse performance score, see [How Lighthouse determines your TBT score](/lighthouse-total-blocking-time/#how-lighthouse-determines-your-tbt-score)

How to improve TBT <a href="#how-to-improve-tbt" class="w-headline-link">#</a>
------------------------------------------------------------------------------

To learn how to improve TBT for a specific site, you can run a Lighthouse performance audit and pay attention to any specific [opportunities](/lighthouse-performance/#opportunities) the audit suggests.

To learn how to improve TBT in general (for any site), refer to the following performance guides:

-   [Reduce the impact of third-party code](/third-party-summary/)
-   [Reduce JavaScript execution time](/bootup-time/)
-   [Minimize main thread work](/mainthread-work-breakdown/)
-   [Keep request counts low and transfer sizes small](/resource-summary/)

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/metrics/" class="w-chip">Metrics</a>

<span class="w-mr--sm">Last updated: Jun 15, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/metrics/tbt/index.md)

<a href="/metrics" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
