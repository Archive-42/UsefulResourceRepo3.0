<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format" alt="A row of shopping carts." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/7DmRrgsxnlS4GNPCyW0Q.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#what-should-you-measure-to-improve-performance" class="w-toc__header--link">What should you measure to improve performance?</a>
-----------------------------------------------------------------------------------------------------------------------------------------

-   [Discovery](#discovery)
-   [Engagement And Conversion](#engagement-and-conversion)
-   [WebPageTest](#webpagetest)
-   [Puppeteer](#puppeteer)
-   [Re-Engagement](#re-engagement)
-   [Recap](#recap)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

-   <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
-   <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

What should you measure to improve performance?
===============================================

Strategies to measure performance at each stage in the purchase funnel.

May 31, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Martin Schierle" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/DheRfImH6FxRNajMslIk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/martinschierle/)

<a href="/authors/martinschierle/" class="w-author__name-link">Martin Schierle</a>

-   <a href="https://twitter.com/martinschierle" class="w-author__link">Twitter</a>
-   <a href="https://github.com/martinschierle" class="w-author__link">GitHub</a>

The different steps of a purchase funnel are prone to performance issues in different ways, and therefore need different measurement and optimizations:

<figure><img src="https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format" alt="A conversion funnel." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/87cAGdJAnPggf8Yt58ID.png?auto=format&amp;w=1600 1600w" width="800" height="399" /><figcaption>A conversion funnel.</figcaption></figure>In this guide we'll address how the different steps can be measured. For this we recommend you to look at lab as well as field data.

**Lab data** is gathered by running tests locally, for example by using [Lighthouse](/fast/discover-performance-opportunities-with-lighthouse) and other tools. This can make it possible to compare website performance over time and with competitors through a controlled, stable environment, but it might not be representative of the performance users experience in real life.

**Field data** is gathered via analytics from real users, and is therefore representative of their experience. However, it can't easily be compared over time or with competitors. Network connections and smartphone hardware evolve over time, and different target audiences might have different devices, thereby making comparisons with field data tough. See also *[Measure Performance In The Field](/fast#measure-performance-in-the-field)*.

To get a complete picture, both data sources are needed. The following sections show how to gather lab and field data for the different relevant performance marks across the funnel.

Discovery <a href="#discovery" class="w-headline-link">#</a>
------------------------------------------------------------

Optimizing for discovery means optimizing for the first load, which is what new users will get, but also search and social [crawlers](https://developers.google.com/search/docs/guides/rendering). Lab data for a first load can be easily acquired through [Lighthouse](/fast/discover-performance-opportunities-with-lighthouse), while field data (at least for Chrome) is readily available through [Chrome UX reports](/fast/chrome-ux-report). A convenient combination of both can be found in [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/). You should also track relevant metrics from the field yourself: [Measuring these metrics on real users' devices](https://developers.google.com/web/fundamentals/performance/user-centric-performance-metrics#measuring_these_metrics_on_real_users_devices) provides a good overview.

From a user perspective the most important metrics are:

-   **[First Contentful Paint (FCP)](/first-contentful-paint):** The time the user stares at a blank screen. This is when most users bounce, as they don't see progress.
-   **[First Meaningful Paint (FMP)](/first-meaningful-paint):** When the user begins to see the main content they came for. This is often the hero image, but for a landing page it may even be a call to action such as a **Buy** button, since the user may have arrived with a clear intent (for example, through a targeted ad campaign).
-   **[First Input Delay (FID)](https://developers.google.com/web/updates/2018/05/first-input-delay):** The time the website needs to react to the user's first input. Excessive JavaScript and other asset loading problems can block this, leading to failed taps or clicks, erroneous inputs and page abandonment.

There are more metrics you can look at, but these are a good baseline. Additionally also make sure to capture bounce rates, conversions and user engagement so that you can set these in relation.

Engagement And Conversion <a href="#engagement-and-conversion" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

After the first load of a landing page, a user will proceed through your site, hopefully towards a successful conversion.

In this phase it is important to have fast and responsive navigations and interactions. Unfortunately it is not trivial to measure the complete flow of navigation and interaction events in the field, as every user takes different paths through the page. We therefore recommend measuring the time needed towards conversion or conversion subgoals ("*Time-to-Action*") by scripting and measuring the flow in a lab test, to compare performance over time or with competitors.

There are two convenient ways of doing this:

### WebPageTest <a href="#webpagetest" class="w-headline-link">#</a>

[WebPageTest](https://www.webpagetest.org/) offers a very flexible [scripting solution](https://github.com/WPO-Foundation/webpagetest-docs/blob/master/user/Scripting.md). The basic idea is to:

-   Tell WebPageTest to navigate through the pages of the flow with the [`navigate`](https://github.com/WPO-Foundation/webpagetest-docs/blob/master/user/Scripting.md#navigate) command.
-   If needed script the clicking of buttons via [`clickAndWait`](https://github.com/WPO-Foundation/webpagetest-docs/blob/master/user/Scripting.md#clickandwait) commands and fill text fields via [`setValue`](https://github.com/WPO-Foundation/webpagetest-docs/blob/master/user/Scripting.md#selectvalue). For testing of Single Page Applications use `clickAndWait` rather than `navigate` commands for all steps after the first, as `navigate` will do a full load instead of the lightweight virtual page load.
-   Make sure to combine the different steps of the flow in the analysis via [`combineSteps`](https://github.com/WPO-Foundation/webpagetest-docs/blob/master/user/Scripting.md#combinesteps) to produce a single overall result report for the complete flow.

Such a script could look like this:

    combineSteps
    navigate    https://www.store.google.com/landingpage
    navigate    https://www.store.google.com/productpage
    clickAndWait    innerText=Buy Now
    navigate   https://www.store.google.com/basket
    navigate https://www.store.google.com/checkout

With a script like this in place you can easily measure and compare performance over time. This can even be automated through the [WebPageTest API](https://github.com/WPO-Foundation/webpagetest-docs/blob/5337749ae99d0529fc0ae690d402fd4f88766be9/dev/api.md).

### Puppeteer <a href="#puppeteer" class="w-headline-link">#</a>

Another great option to script testing is via headless Chrome, which can be controlled through the Node API [Puppeteer](https://github.com/GoogleChrome/puppeteer). The general idea is to start the browser through Puppeteer, navigate to the landing page through the [goto](https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md#pagegotourl-options) function, [inject JavaScript](https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md#pageevaluatepagefunction-args) to fill fields or [click](https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md#pageclickselector-options) buttons and proceed through the funnel through further [goto](https://github.com/GoogleChrome/puppeteer/blob/master/docs/api.md#pagegotourl-options) calls as needed.

As a metric the duration of the flow can be measured directly, but you could also sum up the FCP, FMP or TTI values of the individual loads of the flow. [Test website performance with Puppeteer](https://michaljanaszek.com/blog/test-website-performance-with-puppeteer) provides an overview of how to get performance metrics via Puppeteer. A very simplified example Node script could look like this:

    const puppeteer = require('puppeteer');
    (async () => {
      const browser = await puppeteer.launch();
      const page = await browser.newPage();
      const start = performance.now();
      await page.goto('https://www.store.google.com/landingpage');
      await page.goto('https://www.store.google.com/productpage');
      // click the buy button, which triggers overlay basket
      await page.click('#buy_btn');
      // wait until basket overlay is shown
      await page.waitFor('#close_btn');
      await page.goto('https://www.store.google.com/basket');
      await page.goto('https://www.store.google.com/checkout');
      console.log('Flow took ' + parseInt((performance.now() - start)/1000) + ' seconds');
      await browser.close();
    })();

This script can easily be automated, and even be made part of the build process or perf budgets, and be monitored regularly.

Re-Engagement <a href="#re-engagement" class="w-headline-link">#</a>
--------------------------------------------------------------------

Users will return to your site in different time intervals. Depending on time passed, the browser may have less of the website's resources cached, needing more network requests. This makes it difficult to estimate performance differences across repeat visits in lab tests. It is still recommended to keep an eye on this though, and a great lab test tool for repeat visits is [WebPageTest](https://www.webpagetest.org/), which has a dedicated option for a direct repeat visit:

<figure><img src="https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format" alt="Webpagetest offers options to test first load and repeat load as well" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/6eHzqWl6gaKjL39n8Dwh.png?auto=format&amp;w=1600 1600w" width="800" height="650" /><figcaption>Webpagetest offers options to test first load and repeat load as well</figcaption></figure>To get a better feeling for repeat visit performance in the field use your analytics package of choice to segment your performance metrics by user type. Here is an example of such a report in Google Analytics:

<figure><img src="https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format" alt="A Google Analytics custom report can be used to report speed metrics for new and returning users." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/pSxM9xuJKho7RjOn4aDK.png?auto=format&amp;w=1600 1600w" width="800" height="444" /><figcaption>A Google Analytics custom report can be used to report speed metrics for new and returning users.</figcaption></figure>A report like this will give you page load times for new and returning users as well.

Recap <a href="#recap" class="w-headline-link">#</a>
----------------------------------------------------

This guide showed you how to measure first load, flow and repeat load via field and lab tests. Make sure to optimize the different steps of the funnel accordingly to maximize discovery (first load), engagement (navigations and flow) and re-engagement (repeat load).

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: May 31, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/what-should-you-measure-to-improve-performance/index.md)

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
