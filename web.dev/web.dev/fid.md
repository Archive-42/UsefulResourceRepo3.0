<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#first-input-delay-(fid)" class="w-toc__header--link">First Input Delay (FID)</a>
------------------------------------------------------------------------------------------

-   [What is FID?](#what-is-fid)
-   [What is a good FID score?](#what-is-a-good-fid-score)
-   [FID in detail](#fid-in-detail)
-   [What if an interaction doesn't have an event listener?](#what-if-an-interaction-doesn't-have-an-event-listener)
-   [Why only consider the first input?](#why-only-consider-the-first-input)
-   [What counts as a first input?](#what-counts-as-a-first-input)
-   [What if a user never interacts with your site?](#what-if-a-user-never-interacts-with-your-site)
-   [Why only consider the input delay?](#why-only-consider-the-input-delay)
-   [How to measure FID](#how-to-measure-fid)
-   [Field tools](#field-tools)
-   [Measure FID in JavaScript](#measure-fid-in-javascript)
-   [Analyzing and reporting on FID data](#analyzing-and-reporting-on-fid-data)
-   [How to improve FID](#how-to-improve-fid)
-   [CHANGELOG](#changelog)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

First Input Delay (FID)
=======================

Nov 7, 2019 <span class="w-author__separator">•</span> Updated Jun 19, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/learn-web-vitals" class="w-post-signpost__link">Web Vitals</a><span class="w-post-signpost__divider">|</span><a href="/metrics" class="w-post-signpost__link">Metrics</a>

[<img src="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Philip Walton" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/philipwalton/)

<a href="/authors/philipwalton/" class="w-author__name-link">Philip Walton</a>

-   <a href="https://twitter.com/philwalton" class="w-author__link">Twitter</a>
-   <a href="https://github.com/philipwalton" class="w-author__link">GitHub</a>
-   <a href="https://philipwalton.com" class="w-author__link">Blog</a>

First Input Delay (FID) is an important, user-centric metric for measuring [load responsiveness](/user-centric-performance-metrics/#types-of-metrics) because it quantifies the experience users feel when trying to interact with unresponsive pages—a low FID helps ensure that the page is [usable](/user-centric-performance-metrics/#questions).

We all know how important it is to make a good first impression. It's important when meeting new people, and it's also important when building experiences on the web.

On the web, a good first impression can make the difference between someone becoming a loyal user or them leaving and never coming back. The question is, what makes for a good impression, and how do you measure what kind of impression you're likely making on your users?

On the web, first impressions can take a lot of different forms—we have first impressions of a site's design and visual appeal as well as first impressions of its speed and responsiveness.

While it is hard to measure how much users like a site's design with web APIs, measuring its speed and responsiveness is not!

The first impression users have of how fast your site loads can be measured with [First Contentful Paint (FCP)](/fcp/). But how fast your site can paint pixels to the screen is just part of the story. Equally important is how responsive your site is when users try to interact with those pixels!

The First Input Delay (FID) metric helps measure your user's first impression of your site's interactivity and responsiveness.

What is FID? <a href="#what-is-fid" class="w-headline-link">#</a>
-----------------------------------------------------------------

FID measures the time from when a user first interacts with a page (i.e. when they click a link, tap on a button, or use a custom, JavaScript-powered control) to the time when the browser is actually able to begin processing event handlers in response to that interaction.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Se4TiXIdp8jtLJVScWed.svg" alt="Good fid values are 2.5 seconds, poor values are greater than 4.0 seconds and anything in between needs improvement" class="w-screenshot w-screenshot--filled width-full" width="400" height="300" />

### What is a good FID score? <a href="#what-is-a-good-fid-score" class="w-headline-link">#</a>

To provide a good user experience, sites should strive to have a First Input Delay of **100 milliseconds** or less. To ensure you're hitting this target for most of your users, a good threshold to measure is the **75th percentile** of page loads, segmented across mobile and desktop devices.

To learn more about the research and methodology behind this recommendation, see: [Defining the Core Web Vitals metrics thresholds](/defining-core-web-vitals-thresholds/)

FID in detail <a href="#fid-in-detail" class="w-headline-link">#</a>
--------------------------------------------------------------------

As developers who write code that responds to events, we often assume our code is going to be run immediately—as soon as the event happens. But as users, we've all frequently experienced the opposite—we've loaded a web page on our phone, tried to interact with it, and then been frustrated when nothing happened.

In general, input delay (a.k.a. input latency) happens because the browser's main thread is busy doing something else, so it can't (yet) respond to the user. One common reason this might happen is the browser is busy parsing and executing a large JavaScript file loaded by your app. While it's doing that, it can't run any event listeners because the JavaScript it's loading might tell it to do something else.

**Gotchas!**

FID only measures the "delay" in event processing. It does not measure the event processing time itself nor the time it takes the browser to update the UI after running event handlers. While this time does affect the user experience, including it as part of FID would incentivize developers to respond to events asynchronously—which would improve the metric but likely make the experience worse. See [why only consider the input delay](#why-only-consider-the-input-delay) below for more details.

Consider the following timeline of a typical web page load:

[<img src="https://web-dev.imgix.net/image/admin/9tm3f6pwlHMqNKuFvaP0.svg" alt="Example page load trace" width="800" height="260" />](https://web-dev.imgix.net/image/admin/9tm3f6pwlHMqNKuFvaP0.svg)

The above visualization shows a page that's making a couple of network requests for resources (most likely CSS and JS files), and—after those resources are finished downloading—they're processed on the main thread.

This results in periods where the main thread is momentarily busy, which is indicated by the beige-colored [task](https://html.spec.whatwg.org/multipage/webappapis.html#concept-task) blocks.

Long first input delays typically occur between [First Contentful Paint (FCP)](/fcp/) and [Time to Interactive (TTI)](/tti/) because the page has rendered some of its content but isn't yet reliably interactive. To illustrate how this can happen, FCP and TTI have been added to the timeline:

[<img src="https://web-dev.imgix.net/image/admin/24Y3T5sWNuZD9fKhkuER.svg" alt="Example page load trace with FCP and TTI" width="800" height="340" />](https://web-dev.imgix.net/image/admin/24Y3T5sWNuZD9fKhkuER.svg)

You may have noticed that there's a fair amount of time (including three [long tasks](/custom-metrics/#long-tasks-api)) between FCP and TTI, if a user tries to interact with the page during that time (e.g. click on a link), there will be a delay between when the click is received and when the main thread is able to respond.

Consider what would happen if a user tried to interact with the page near the beginning of the longest task:

[<img src="https://web-dev.imgix.net/image/admin/krOoeuQ4TWCbt9t6v5Wf.svg" alt="Example page load trace with FCP, TTI, and FID" width="800" height="380" />](https://web-dev.imgix.net/image/admin/krOoeuQ4TWCbt9t6v5Wf.svg)

Because the input occurs while the browser is in the middle of running a task, it has to wait until the task completes before it can respond to the input. The time it must wait is the FID value for this user on this page.

In this example the user just happened to interact with the page at the beginning of the main thread's most busy period. If the user had interacted with the page just a moment earlier (during the idle period) the browser could have responded right away. This variance in input delay underscores the importance of looking at the distribution of FID values when reporting on the metric. You can read more about this in the section below on analyzing and reporting on FID data.

### What if an interaction doesn't have an event listener? <a href="#what-if-an-interaction-doesn&#39;t-have-an-event-listener" class="w-headline-link">#</a>

FID measures the delta between when an input event is received and when the main thread is next idle. This means FID is measured **even in cases where an event listener has not been registered.** The reason is because many user interactions do not require an event listener but *do* require the main thread to be idle in order to run.

For example, all of the following HTML elements need to wait for in-progress tasks on the main thread to complete prior to responding to user interactions:

-   Text fields, checkboxes, and radio buttons (`<input>`, `<textarea>`)
-   Select dropdowns (`<select>`)
-   links (`<a>`)

### Why only consider the first input? <a href="#why-only-consider-the-first-input" class="w-headline-link">#</a>

While a delay from any input can lead to a bad user experience, we primarily recommend measuring the first input delay for a few reasons:

-   The first input delay will be the user's first impression of your site's responsiveness, and first impressions are critical in shaping our overall impression of a site's quality and reliability.
-   The biggest interactivity issues we see on the web today occur during page load. Therefore, we believe initially focusing on improving site's first user interaction will have the greatest impact on improving the overall interactivity of the web.
-   The recommended solutions for how sites should fix high first input delays (code splitting, loading less JavaScript upfront, etc.) are not necessarily the same solutions for fixing slow input delays after page load. By separating out these metrics we'll be able to provide more specific performance guidelines to web developers.

### What counts as a first input? <a href="#what-counts-as-a-first-input" class="w-headline-link">#</a>

FID is a metric that measures a page's responsiveness during load. As such, it only focuses on input events from discrete actions like clicks, taps, and key presses.

Other interactions, like scrolling and zooming, are continuous actions and have completely different performance constraints (also, browsers are often able to hide their latency by running them on a separate thread).

To put this another way, FID focuses on the R (responsiveness) in the [RAIL performance model](https://developers.google.com/web/fundamentals/performance/rail), whereas scrolling and zooming are more related to A (animation), and their performance qualities should be evaluated separately.

### What if a user never interacts with your site? <a href="#what-if-a-user-never-interacts-with-your-site" class="w-headline-link">#</a>

Not all users will interact with your site every time they visit. And not all interactions are relevant to FID (as mentioned in the previous section). In addition, some user's first interactions will be at bad times (when the main thread is busy for an extended period of time), and some user's first interactions will be at good times (when the main thread is completely idle).

This means some users will have no FID values, some users will have low FID values, and some users will probably have high FID values.

How you track, report on, and analyze FID will probably be quite a bit different from other metrics you may be used to. The next section explains how best to do this.

### Why only consider the input delay? <a href="#why-only-consider-the-input-delay" class="w-headline-link">#</a>

As mentioned above, FID only measures the "delay" in event processing. It does not measure the event processing time itself nor the time it takes the browser to update the UI after running event handlers.

Even though this time is important to the user and *does* affect the experience, it's not included in this metric because doing so could incentivize developers to add workarounds that actually make the experience worse—that is, they could wrap their event handler logic in an asynchronous callback (via `setTimeout()` or `requestAnimationFrame()`) in order to separate it from the task associated with the event. The result would be an improvement in the metric score but a slower response as perceived by the user.

However, while FID only measure the "delay" portion of event latency, developers who want to track more of the event lifecycle can do so using the [Event Timing API](https://wicg.github.io/event-timing/). See the guide on [custom metrics](/custom-metrics/#event-timing-api) for more details.

How to measure FID <a href="#how-to-measure-fid" class="w-headline-link">#</a>
------------------------------------------------------------------------------

FID is a metric that can only be measured [in the field](/user-centric-performance-metrics/#in-the-field), as it requires a real user to interact with your page. You can measure FID with the following tools.

FID requires a real user and thus cannot be measured in the lab. However, the [Total Blocking Time (TBT)](/tbt/) metric is lab-measurable, correlates well with FID in the field, and also captures issues that affect interactivity. Optimizations that improve TBT in the lab should also improve FID for your users.

### Field tools <a href="#field-tools" class="w-headline-link">#</a>

-   [Chrome User Experience Report](https://developers.google.com/web/tools/chrome-user-experience-report)
-   [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
-   [Search Console (Core Web Vitals report)](https://support.google.com/webmasters/answer/9205520)
-   [`web-vitals` JavaScript library](https://github.com/GoogleChrome/web-vitals)

### Measure FID in JavaScript <a href="#measure-fid-in-javascript" class="w-headline-link">#</a>

To measure FID in JavaScript, you can use the [Event Timing API](https://wicg.github.io/event-timing). The following example shows how to create a [`PerformanceObserver`](https://developer.mozilla.org/en-US/docs/Web/API/PerformanceObserver) that listens for [`first-input`](https://wicg.github.io/event-timing/#sec-performance-event-timing) entries and logs them to the console:

    new PerformanceObserver((entryList) => {
      for (const entry of entryList.getEntries()) {
        const delay = entry.processingStart - entry.startTime;
        console.log('FID candidate:', delay, entry);
      }
    }).observe({type: 'first-input', buffered: true});

**Warning**: This code shows how to log `first-input` entries to the console and calculate their delay. However, measuring FID in JavaScript is more complicated. See below for details:

In the above example, the `first-input` entry's delay value is measured by taking the delta between the entry's `startTime` and `processingStart` timestamps. In most cases this will be the FID value; however, not all `first-input` entries are valid for measuring FID.

The following section lists the differences between what the API reports and how the metric is calculated.

#### Differences between the metric and the API <a href="#differences-between-the-metric-and-the-api" class="w-headline-link">#</a>

-   The API will dispatch `first-input` entries for pages loaded in a background tab but those pages should be ignored when calculating FID.
-   The API will also dispatch `first-input` entries if the page was backgrounded prior to the first input occurring, but those pages should also be ignored when calculating FID (inputs are only considered if the page was in the foreground the entire time).
-   The API does not report `first-input` entries when the page is restored from the [back/forward cache](/bfcache/#impact-on-core-web-vitals), but FID should be measured in these cases since users experience them as distinct page visits.
-   The API does not report inputs that occur within iframes, but to properly measure FID you should consider them. Sub-frames can use the API to report their `first-input` entries to the parent frame for aggregation.

Rather than memorizing all these subtle differences, developers can use the [`web-vitals` JavaScript library](https://github.com/GoogleChrome/web-vitals) to measure FID, which handles these differences for you (where possible):

    import {getFID} from 'web-vitals';

    // Measure and log FID as soon as it's available.
    getFID(console.log);

You can refer to [the source code for `getFID)`](https://github.com/GoogleChrome/web-vitals/blob/master/src/getFID.ts) for a complete example of how to measure FID in JavaScript.

In some cases (such as cross-origin iframes) it's not possible to measure FID in JavaScript. See the [limitations](https://github.com/GoogleChrome/web-vitals#limitations) section of the `web-vitals` library for details.

### Analyzing and reporting on FID data <a href="#analyzing-and-reporting-on-fid-data" class="w-headline-link">#</a>

Due to the expected variance in FID values, it's critical that when reporting on FID you look at the distribution of values and focus on the higher percentiles.

While [choice of percentile](/defining-core-web-vitals-thresholds/#choice-of-percentile) for all Core Web Vitals thresholds is the 75th, for FID in particular we still strongly recommend looking at the 95th–99th percentiles, as those will correspond to the particularly bad first experiences users are having with your site. And it will show you the areas that need the most improvement.

This is true even if you segment your reports by device category or type. For example, if you run separate reports for desktop and mobile, the FID value you care most about on desktop should be the 95th–99th percentile of desktop users, and the FID value you care about most on mobile should be the 95th–99th percentile of mobile users.

How to improve FID <a href="#how-to-improve-fid" class="w-headline-link">#</a>
------------------------------------------------------------------------------

To learn how to improve FID for a specific site, you can run a Lighthouse performance audit and pay attention to any specific [opportunities](/lighthouse-performance/#opportunities) the audit suggests.

While FID is a field metric (and Lighthouse is a lab metric tool), the guidance for improving FID is the same as that for improving the lab metric [Total Blocking Time (TBT)](/tbt/).

For a deep dive on how to improve FID, see [Optimize FID](/optimize-fid/). For additional guidance on individual performance techniques that can also improve FID, see:

-   [Reduce the impact of third-party code](/third-party-summary/)
-   [Reduce JavaScript execution time](/bootup-time/)
-   [Minimize main thread work](/mainthread-work-breakdown/)
-   [Keep request counts low and transfer sizes small](/resource-summary/)

CHANGELOG <a href="#changelog" class="w-headline-link">#</a>
------------------------------------------------------------

Occasionally, bugs are discovered in the APIs used to measure metrics, and sometimes in the definitions of the metrics themselves. As a result, changes must sometimes be made, and these changes can show up as improvements or regressions in your internal reports and dashboards.

To help you manage this, all changes to either the implementation or definition of these metrics will be surfaced in this [CHANGELOG](http://bit.ly/chrome-speed-metrics-changelog).

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/metrics/" class="w-chip">Metrics</a>

<span class="w-mr--sm">Last updated: Jun 19, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/metrics/fid/index.md)

<a href="/learn-web-vitals" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
