<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format" alt="Image of laptop with mouse pointing to checkout button on a web page" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/1bX6ydHTmi5UrEFx3PDc.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#how-to-report-metrics-and-build-a-performance-culture" class="w-toc__header--link">How to report metrics and build a performance culture</a>

- [Introduction](#introduction)
- [A word about metrics](#a-word-about-metrics)
- [Increasing bounce rate](#increasing-bounce-rate)
- [Problem](#problem)
- [Solution](#solution)
- [Decreasing relative conversions](#decreasing-relative-conversions)
- [Problem](#problem-2)
- [Solution](#solution-2)
- [Dropping engagement](#dropping-engagement)
- [Problem](#problem-3)
- [Solution](#solution-3)
- [Using averages or medians](#using-averages-or-medians)
- [Problem](#problem-4)
- [Solution](#solution-4)
- [Third party content](#third-party-content)
- [Performance Culture](#performance-culture)
- [Make metrics tangible](#make-metrics-tangible)
- [Recap](#recap)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# How to report metrics and build a performance culture

Understand why performance matters when it comes to conversion.

May 5, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Martin Schierle" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/martinschierle/)

<a href="/authors/martinschierle/" class="w-author__name-link">Martin Schierle</a>

- <a href="https://twitter.com/martinschierle" class="w-author__link">Twitter</a>
- <a href="https://github.com/martinschierle" class="w-author__link">GitHub</a>

## Introduction <a href="#introduction" class="w-headline-link">#</a>

Website performance is a key goal towards e-commerce conversions, so it must be a core priority for business stakeholders and leadership, not just development teams.

For that reason, it's crucial to make performance metrics visible and tangible for all stakeholders, and to build reporting and monitoring into your workflow.

This guide describes what to be aware of and what to avoid to achieve this successfully.

## A word about metrics <a href="#a-word-about-metrics" class="w-headline-link">#</a>

There are countless metrics to evaluate website performance, and while it may seem useful to collect all of them, too many metrics can be confusing and misleading. There are several ways to deal with this:

- Gather multiple metrics and try to narrow and filter afterwards on what might be relevant for the task at hand.
- Abstract metrics into an overall score, as for example [Lighthouse does](https://developers.google.com/web/tools/lighthouse/v3/scoring#perf). This can be especially useful for non-technical staff and other stakeholders, but is probably insufficient for deeper technical analysis.
- Try to find the one metric which is most relevant as a predictor for your conversions and then optimize towards this.

In reality, a pragmatic combination makes the most sense here. Gather more rather than less to begin with, report an abstract score to management, and optimize towards the one metric which best predicts your conversions.

Finding this metric can be done by using your analytics tool of choice to map performance metrics to user engagement, conversions and transaction values. For example, a custom report to do so looks like this in Google Analytics:

<figure><img src="https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format" alt="Fig 1: Custom report in Google Analytics to analyze the impact of speed on conversions and engagement." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/YI31t9fE82uEhrrYKTVg.png?auto=format&amp;w=1600 1600w" width="800" height="430" /><figcaption>Fig 1: Custom report in Google Analytics to analyze the impact of speed on conversions and engagement.</figcaption></figure>**Caution**: **Metrics can be deceiving.** Unfortunately metrics can sometimes be misleading with respect to performance. Keep reading for specifics.

## Increasing bounce rate <a href="#increasing-bounce-rate" class="w-headline-link">#</a>

### Problem <a href="#problem" class="w-headline-link">#</a>

Often it is assumed that bounce rate will drop when page load speed increases. While this normally does hold true, measurements sometimes show the opposite. This is because analytics can only measure a bounce after the analytics library is loaded. A faster page load means analytics code also loads faster, so analytics may see more bounces even if there aren't more happening.

### Solution <a href="#solution" class="w-headline-link">#</a>

This can be eased by measuring [real page abandonment](https://developers.google.com/web/fundamentals/performance/user-centric-performance-metrics#load_abandonment) instead.

## Decreasing relative conversions <a href="#decreasing-relative-conversions" class="w-headline-link">#</a>

### Problem <a href="#problem-2" class="w-headline-link">#</a>

Relative conversions may sometimes seem to drop for faster sites. This is because faster pages reach a bigger audience who might be less engaged or committed. While incremental traffic and conversions increase with faster pages, relative conversions (the ratio of conversions to page views or visitors) might still drop.

### Solution <a href="#solution-2" class="w-headline-link">#</a>

This effect can be eased by looking out for absolute conversions instead, and even calculate Cost Per Sales (conversions divided with investment level) or ROI.

## Dropping engagement <a href="#dropping-engagement" class="w-headline-link">#</a>

### Problem <a href="#problem-3" class="w-headline-link">#</a>

Page engagement may seem to drop for a faster page.

### Solution <a href="#solution-3" class="w-headline-link">#</a>

This can actually be a positive signal! If the page is faster users can reach their goal more quickly and might just have shorter sessions and less time on page.

## Using averages or medians <a href="#using-averages-or-medians" class="w-headline-link">#</a>

### Problem <a href="#problem-4" class="w-headline-link">#</a>

In general, it can be deceiving to look at averages and medians of performance metrics (see this nicely described in _[Everything You Know About Latency Is Wrong](https://bravenewgeek.com/everything-you-know-about-latency-is-wrong/))_. Similar to a chain being just as strong as the weakest link, the performance of a funnel is only as good as its slowest load. A single slow load may be enough to lose the user. Therefore averages and medians are more likely to hide the real performance issues, than to reveal them.

### Solution <a href="#solution-4" class="w-headline-link">#</a>

It's best to analyze complete distributions, but as this is not always easily possible we recommend using 90th percentiles—this is the value for which 90% of loads were faster. Even then a user hitting ten pages will still have one load slower than this, and might drop out there.

While performance measurement is highly important, make sure to keep an open mind and question unexpected results—and make sure to not report misleading numbers to stakeholders and management. If unsure on what to pick and report, we'd advise as a minimum for 90th percentile [First Contentful Paint](/first-contentful-paint), which is also what we use across our public tooling.

## Third party content <a href="#third-party-content" class="w-headline-link">#</a>

Website performance is especially prone to being dragged down by third party content (see [Eliminate render-blocking resources](/render-blocking-resources)). This is a particular problem for e-commerce, often due to trackers and widgets.

Some ways to handle third party content with respect to performance:

- Always keep third party content out of the [critical rendering path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/). If the third party has server problems and times out, it will impact your website heavily. You can test and simulate this via [WebPageTest Single-Point-of-Failure](https://css-tricks.com/use-webpagetest-api/#single-point-of-failure) tests.
- Continually measure and report the ratio of third party content, for example via WebPageTest [domain breakdown](https://www.webpagetest.org/domains.php). Make sure to use performance budgets for third party content.
- If you suspect that a particular third party component is having a detrimental effect on performance, do a performance comparison with it included and excluded. [Find out how](https://andydavies.me/blog/2018/02/19/using-webpagetest-to-measure-the-impact-of-3rd-party-tags/).
- Try to stay on one stack from one vendor if possible. For example, if you have a tag manager and analytics on one stack, you may only need a single script, and may be able to [take advantage of HTTP2 synergies](https://developers.google.com/web/fundamentals/performance/http2/) as there is only one host involved.
- Make sure not to use the same functionality from two different vendors. You shouldn't need two tag managers or two analytics platforms.
- Routinely audit and clean out redundant third party scripts, trackers and widgets. This can easily be done via [Ghostery Extension](https://chrome.google.com/webstore/detail/ghostery-%E2%80%93-privacy-ad-blo/mlomiejdfkolichcflejclcbmpeaniij?hl=en) or tools like [WhatRuns](https://chrome.google.com/webstore/detail/whatruns/cmkdbmfndkfgebldhnkbfhlneefdaaip?hl=en):

<figure><img src="https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format" alt="A Ghostery report showing all loaded trackers" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/w2xb4mUJ7kDpt254fq0k.png?auto=format&amp;w=1600 1600w" width="800" height="710" /><figcaption>A Ghostery report showing all loaded trackers</figcaption></figure>Learn more in [Loading Third-Party JavaScript](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/loading-third-party-javascript/).

## Performance Culture <a href="#performance-culture" class="w-headline-link">#</a>

Unfortunately performance is often seen as a one-off optimization task, and then regresses over time as stakeholders raise new feature requests or insist on adding new trackers and widgets.

Performance must be a continuous goal to improve acquisition, discovery, and conversion rates as well as safeguarding the reputation of your brand. This can be achieved with [performance budgets](/performance-budgets-101) like [Tinder did](https://medium.com/@addyosmani/a-tinder-progressive-web-app-performance-case-study-78919d98ece0), and by establishing and fostering a performance culture, where all employees and especially decision makers recognize speed as a core feature of the website.

## Make metrics tangible <a href="#make-metrics-tangible" class="w-headline-link">#</a>

Reports on metrics are often abstract and easy to challenge or dismiss. It's best to make your performance tangible and visible. There are several good ways to do this:

- [Facebook](https://www.theverge.com/2015/10/28/9625062/facebook-2g-tuesdays-slow-internet-developing-world) and Google do this by providing slow networks across the company for testing.
- Make average, low-spec devices with low [bandwidth or high latencies](https://developers.google.com/web/fundamentals/performance/poor-connectivity/) available to management and other stakeholders.
- Consider adding overlays showing performance metrics on your development or staging servers. Connections to these servers from mobile can potentially be throttled by default on corporate networks.
- Monitors can be placed strategically across the company showing videos or timestrips of your website's loading behavior, preferably in comparison to competitors. WebPageTest [can create these](https://www.webpagetest.org/video/) very easily and automatically.
- Performance can also be fun—maybe a [game based on an individual Lighthouse report](https://g.co/perfgame) can reach audiences which can't be reached by pure reports and metrics?

## Recap <a href="#recap" class="w-headline-link">#</a>

This guide explains why the selection of metrics, and how they are reported and handled, is as important as the measurement and optimization itself—or even more. Make sure to prefer percentiles or distributions over averages, be cautious of using just bounce rate or relative conversion rate as impact measures, and make sure that metrics are easy to understand and tangible for stakeholders across the company. Establishing a performance culture is also an important step towards a well performing e-commerce site.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: May 5, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/how-to-report-metrics/index.md)

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
