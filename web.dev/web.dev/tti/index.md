## <a href="#time-to-interactive-(tti)" class="w-toc__header--link">Time to Interactive (TTI)</a>

- [What is TTI?](#what-is-tti)
- [How to measure TTI](#how-to-measure-tti)
- [Lab tools](#lab-tools)
- [What is a good TTI score?](#what-is-a-good-tti-score)
- [How to improve TTI](#how-to-improve-tti)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Time to Interactive (TTI)

Nov 7, 2019 <span class="w-author__separator">•</span> Updated Jun 15, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/metrics" class="w-post-signpost__link">Metrics</a>

[<img src="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Philip Walton" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/philipwalton/)

<a href="/authors/philipwalton/" class="w-author__name-link">Philip Walton</a>

- <a href="https://twitter.com/philwalton" class="w-author__link">Twitter</a>
- <a href="https://github.com/philipwalton" class="w-author__link">GitHub</a>
- <a href="https://philipwalton.com" class="w-author__link">Blog</a>

Time to Interactive (TTI) is an important [lab metric](/user-centric-performance-metrics/#in-the-lab) for measuring [load responsiveness](/user-centric-performance-metrics/#types-of-metrics). It helps identify cases where a page _looks_ interactive but actually isn't. A fast TTI helps ensure that the page is [usable](/user-centric-performance-metrics/#questions).

## What is TTI? <a href="#what-is-tti" class="w-headline-link">#</a>

The TTI metric measures the time from when the page starts loading to when its main sub-resources have loaded and it is capable of reliably responding to user input quickly.

To calculate TTI based on a [performance trace](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference) of a web page, follow these steps:

1.  Start at [First Contentful Paint (FCP)](/fcp/).
2.  Search forward in time for a quiet window of at least five seconds, where _quiet window_ is defined as: no [long tasks](/custom-metrics/#long-tasks-api) and no more than two in-flight network GET requests.
3.  Search backwards for the last long task before the quiet window, stopping at FCP if no long tasks are found.
4.  TTI is the end time of the last long task before the quiet window (or the same value as FCP if no long tasks are found).

The following diagram should help visualize the steps above:

[<img src="https://web-dev.imgix.net/image/admin/WZM0n4aXah67lEyZugOT.svg" alt="A page load timeline showing how to compute TTI" width="800" height="473" />](https://web-dev.imgix.net/image/admin/WZM0n4aXah67lEyZugOT.svg)

Historically, developers have optimized pages for fast render times, sometimes at the expense of TTI.

Techniques like server-side rendering (SSR) can lead to scenarios where a page _looks_ interactive (that is, links and buttons are visible on the screen), but it's not _actually_ interactive because the main thread is blocked or because the JavaScript code controlling those elements hasn't loaded.

When users try to interact with a page that looks interactive but actually isn't, they'll likely respond in one of two ways:

- In the best-case scenario, they'll be annoyed that the page is slow to respond.
- In the worst-case scenario, they'll assume the page is broken and likely leave. They may even lose confidence or trust in the value of your brand.

To avoid this problem, make every effort to minimize the difference between FCP and TTI. And in cases were a noticeable difference does exist, make it clear through visual indicators that the components on your page are not yet interactive.

## How to measure TTI <a href="#how-to-measure-tti" class="w-headline-link">#</a>

TTI is a metric that's best measured [in the lab](/user-centric-performance-metrics/#in-the-lab). The best way to measure TTI is to run a Lighthouse performance audit on your site. See the [Lighthouse documentation on TTI](/interactive/) for usage details.

### Lab tools <a href="#lab-tools" class="w-headline-link">#</a>

- [Lighthouse](https://developers.google.com/web/tools/lighthouse/)
- [WebPageTest](https://www.webpagetest.org/)

While it's possible to measure TTI in the field, it's not recommended, as user interaction can affect your page's TTI in ways that lead to lots of variance in your reports. To understand a page's interactivity in the field, you should measure [First Input Delay (FID)](/fid/).

## What is a good TTI score? <a href="#what-is-a-good-tti-score" class="w-headline-link">#</a>

To provide a good user experience, sites should strive to have a Time to Interactive of less than **5 seconds** when tested on **average mobile hardware**.

For details on how your page's TTI affects your Lighthouse performance score, see [How Lighthouse determines your TTI score](/interactive/#how-lighthouse-determines-your-tti-score).

## How to improve TTI <a href="#how-to-improve-tti" class="w-headline-link">#</a>

To learn how to improve TTI for a specific site, you can run a Lighthouse performance audit and pay attention to any specific [opportunities](/lighthouse-performance/#opportunities) the audit suggests.

To learn how to improve TTI in general (for any site), refer to the following performance guides:

- [Minify JavaScript](/unminified-javascript/)
- [Preconnect to required origins](/uses-rel-preconnect/)
- [Preload key requests](/uses-rel-preload/)
- [Reduce the impact of third-party code](/third-party-summary/)
- [Minimize critical request depth](/critical-request-chains/)
- [Reduce JavaScript execution time](/bootup-time/)
- [Minimize main thread work](/mainthread-work-breakdown/)
- [Keep request counts low and transfer sizes small](/resource-summary/)

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/metrics/" class="w-chip">Metrics</a>

<span class="w-mr--sm">Last updated: Jun 15, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/metrics/tti/index.md)

<a href="/metrics" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
