<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#custom-metrics" class="w-toc__header--link">Custom metrics</a>
------------------------------------------------------------------------

-   [APIs to measure custom metrics](#apis-to-measure-custom-metrics)
-   [Performance Observer](#performance-observer)
-   [User Timing API](#user-timing-api)
-   [Long Tasks API](#long-tasks-api)
-   [Element Timing API](#element-timing-api)
-   [Event Timing API](#event-timing-api)
-   [Resource Timing API](#resource-timing-api)
-   [Navigation Timing API](#navigation-timing-api)
-   [Server Timing API](#server-timing-api)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Custom metrics
==============

Nov 8, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/metrics" class="w-post-signpost__link">Metrics</a>

[<img src="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Philip Walton" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/philipwalton/)

<a href="/authors/philipwalton/" class="w-author__name-link">Philip Walton</a>

-   <a href="https://twitter.com/philwalton" class="w-author__link">Twitter</a>
-   <a href="https://github.com/philipwalton" class="w-author__link">GitHub</a>
-   <a href="https://philipwalton.com" class="w-author__link">Blog</a>

There's a lot of value in having [user-centric metrics](/user-centric-performance-metrics/) that you can measure, universally, on any given website. These metrics allow you to:

-   Understand how real users experience the web as a whole
-   Easily compare your site to a competitor's
-   Track useful and actionable data in your analytics tools without needing to write custom code

Universal metrics offer a good baseline, but in many cases you need to measure *more* than just these metrics in order to capture the full experience for your particular site.

Custom metrics allow you to measure aspects of your site's experience that may only apply to your site, such as:

-   How long it takes for a single page app (SPA) to transition from one "page" to another
-   How long it takes for a page to display data fetched from a database for logged-in users
-   How long it takes for a server-side-rendered (SSR) app to [hydrate](https://addyosmani.com/blog/rehydration/)
-   The cache hit rate for resources loaded by returning visitors
-   The event latency of click or keyboard events in a game

APIs to measure custom metrics <a href="#apis-to-measure-custom-metrics" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------

Historically web developers haven't had many low-level APIs to measure performance, and as a result they've had to resort to hacks in order to measure whether a site was performing well.

For example, it's possible to determine whether the main thread is blocked due to long-running JavaScript tasks by running a `requestAnimationFrame` loop and calculating the delta between each frame. If the delta is significantly longer than the display's framerate, you can report that as a long task. Such hacks are not recommended, though, because they actually affect performance themselves (by draining battery, for example).

The first rule of effective performance measurement is to make sure your performance measurement techniques aren't causing performance issues themselves. So for any custom metrics you measure on your site, it's best to use one of the following APIs if possible.

### Performance Observer <a href="#performance-observer" class="w-headline-link">#</a>

Understanding the PerformanceObserver API is critical to creating custom performance metrics because it's the mechanism by which you get data from all other performance APIs discussed in this article.

With `PerformanceObserver` you can subscribe passively to performance-related events, which means these APIs generally will not interfere with the performance of the page, as their callbacks are generally fired during [idle periods](https://w3c.github.io/requestidlecallback/#idle-periods).

You create a `PerformanceObserver` by passing it a callback to be run whenever new performance entries are dispatched. Then you tell the observer what types of entries to listen for via the [`observe()`](https://developer.mozilla.org/en-US/docs/Web/API/PerformanceObserver/observe) method:

    // Catch errors since some browsers throw when using the new `type` option.
    // https://bugs.webkit.org/show_bug.cgi?id=209216
    try {
      const po = new PerformanceObserver((list) => {
        for (const entry of list.getEntries()) {
          // Log the entry and all associated details.
          console.log(entry.toJSON());
        }
      });

      po.observe({type: 'some-entry-type'});
    } catch (e) {
      // Do nothing if the browser doesn't support this API.
    }

The sections below list all the various entry types available for observing, but in newer browsers you can inspect what entry types are available via the static [`PerformanceObserver.supportedEntryTypes`](https://w3c.github.io/performance-timeline/#supportedentrytypes-attribute) property.

The object passed to the `observe()` method can also specify an `entryTypes` array (in order to observe more than one entry type via the same observer). While specifying `entryTypes` is an older option with wider browser support, using `type` is now preferred, as it allows for specifying additional entry-specific observation configuration (such as the `buffered` flag, discussed next).

#### Observing entries that already happened <a href="#observing-entries-that-already-happened" class="w-headline-link">#</a>

By default, `PerformanceObserver` objects can only observe entries as they occur. This can be problematic if you want to load your performance analytics code lazily (to not block higher-priority resources).

To get historical entries (after they've occurred), set the `buffered` flag to `true` when you call `observe()`. The browser will include historical entries from its [performance entry buffer](https://w3c.github.io/performance-timeline/#dfn-performance-entry-buffer) the first time that your `PerformanceObserver` callback is called.

    po.observe({
      type: 'some-entry-type',
      buffered: true,
    });

To avoid memory issues, the performance entry buffer is not unlimited. For most typical page loads it's unlikely that the buffer will fill up and entries will be missed.

#### Legacy performance APIs to avoid <a href="#legacy-performance-apis-to-avoid" class="w-headline-link">#</a>

Prior to the Performance Observer API, developers could access performance entries using the following three methods defined on the [`performance`](https://w3c.github.io/performance-timeline/) object:

-   [`getEntries()`](https://developer.mozilla.org/en-US/docs/Web/API/Performance/getEntries)
-   [`getEntriesByName()`](https://developer.mozilla.org/en-US/docs/Web/API/Performance/getEntriesByName)
-   [`getEntriesByType()`](https://developer.mozilla.org/en-US/docs/Web/API/Performance/getEntriesByType)

While these APIs are still supported, their usage is not recommended because they don't allow you to listen for when new entries are emitted. In addition, many new APIs (such as Long Tasks) are not exposed via the `performance` object, they're only exposed via `PerformanceObserver`.

Unless you specifically need Internet Explorer compatibility, it's best to avoid these methods in your code and use `PerformanceObserver` going forward.

### User Timing API <a href="#user-timing-api" class="w-headline-link">#</a>

The [User Timing API](https://w3c.github.io/user-timing/) is your general purpose measurement API for time-based metrics. It allows you to arbitrarily mark points in time and then later measure the duration between those marks.

    // Record the time immediately before running a task.
    performance.mark('myTask:start');
    await doMyTask();
    // Record the time immediately after running a task.
    performance.mark('myTask:end');

    // Measure the delta between the start and end of the task
    performance.measure('myTask', 'myTask:start', 'myTask:end');

While APIs like `Date.now()` or `performance.now()` give you similar abilities, the benefit of using the User Timing API is it integrates well with performance tooling. For example, Chrome DevTools visualizes [User Timing measurements in the Performance panel](https://developers.google.com/web/updates/2018/04/devtools#tabs), and many analytics providers will also automatically track any measurements you make and send the duration data to their analytics back end.

To report User Timing measurements, you can use [PerformanceObserver](#performance-observer) and register to observe entries of type `measure`:

    // Catch errors since some browsers throw when using the new `type` option.
    // https://bugs.webkit.org/show_bug.cgi?id=209216
    try {
      // Create the performance observer.
      const po = new PerformanceObserver((list) => {
        for (const entry of list.getEntries()) {
          // Log the entry and all associated details.
          console.log(entry.toJSON());
        }
      });
      // Start listening for `measure` entries to be dispatched.
      po.observe({type: 'measure', buffered: true});
    } catch (e) {
      // Do nothing if the browser doesn't support this API.
    }

### Long Tasks API <a href="#long-tasks-api" class="w-headline-link">#</a>

The [Long Tasks API](https://w3c.github.io/longtasks/) is useful for knowing when the browser's main thread is blocked for long enough to affect frame rate or input latency. Currently the API will report any tasks that execute for longer than 50 milliseconds (ms).

Anytime you need to run expensive code (or load and execute large scripts) it's useful to track whether or not that code blocked the main thread. In fact, many higher-level metrics are built on top of the Long Tasks API themselves (such as [Time to Interactive (TTI)](/interactive/) and [Total Blocking Time (TBT)](/lighthouse-total-blocking-time/)).

To determine when long tasks happen, you can use [PerformanceObserver](https://developer.mozilla.org/en-US/docs/Web/API/PerformanceObserver) and register to observe entries of type `longtask`:

    // Catch errors since some browsers throw when using the new `type` option.
    // https://bugs.webkit.org/show_bug.cgi?id=209216
    try {
      // Create the performance observer.
      const po = new PerformanceObserver((list) => {
        for (const entry of list.getEntries()) {
          // Log the entry and all associated details.
          console.log(entry.toJSON());
        }
      });
      // Start listening for `longtask` entries to be dispatched.
      po.observe({type: 'longtask', buffered: true});
    } catch (e) {
      // Do nothing if the browser doesn't support this API.
    }

### Element Timing API <a href="#element-timing-api" class="w-headline-link">#</a>

The [Largest Contentful Paint (LCP)](/lcp/) metric is useful for knowing when the largest image or text block was painted to the screen, but in some cases you want to measure the render time of a different element.

For these cases, you can use the [Element Timing API](https://wicg.github.io/element-timing/). In fact, the Largest Contentful Paint API is actually built on top of the Element Timing API and adds automatic reporting of the largest contentful element, but you can report on additional elements by explicitly adding the `elementtiming` attribute to them, and registering a PerformanceObserver to observe the element entry type.

    <img elementtiming="hero-image" />
    <p elementtiming="important-paragraph">This is text I care about.</p>
    ...
    <script>
    // Catch errors since some browsers throw when using the new `type` option.
    // https://bugs.webkit.org/show_bug.cgi?id=209216
    try {
      // Create the performance observer.
      const po = new PerformanceObserver((entryList) => {
        for (const entry of entryList.getEntries()) {
          // Log the entry and all associated details.
          console.log(entry.toJSON());
        }
      });
      // Start listening for `element` entries to be dispatched.
      po.observe({type: 'element', buffered: true});
    } catch (e) {
      // Do nothing if the browser doesn't support this API.
    }
    </script>

**Gotchas!**

The types of elements considered for Largest Contentful Paint are the same as those observable via the Element Timing API. If you add the `elementtiming` attribute to an element that isn't one of those types, the attribute will be ignored.

### Event Timing API <a href="#event-timing-api" class="w-headline-link">#</a>

The [First Input Delay (FID)](/fid/) metric measures the time from when a user first interacts with a page to the time when the browser is actually able to begin processing event handlers in response to that interaction. However, in some cases it may also be useful to measure the event processing time itself as well as the time until the next frame can be rendered.

This is possible with the [Event Timing API](https://wicg.github.io/event-timing/) (which is used to measure FID) as it exposes a number of timestamps in the event lifecycle, including:

-   [`startTime`](https://w3c.github.io/performance-timeline/#dom-performanceentry-starttime): the time when the browser receives the event.
-   [`processingStart`](https://wicg.github.io/event-timing/#dom-performanceeventtiming-processingstart): the time when the browser is able to begin processing event handlers for the event.
-   [`processingEnd`](https://wicg.github.io/event-timing/#dom-performanceeventtiming-processingend): time when the browser finishes executing all synchronous code initiated from event handlers for this event.
-   [`duration`](https://wicg.github.io/event-timing/#dom-performanceeventtiming-processingstart): the time (rounded to 8ms for security reasons) between when the browser receives the event until it's able to paint the next frame after finishing executing all synchronous code initiated from the event handlers.

The following example shows how to use these these values to create custom measurements:

    // Catch errors since some browsers throw when using the new `type` option.
    // https://bugs.webkit.org/show_bug.cgi?id=209216
    try {
      const po = new PerformanceObserver((entryList) => {
        const firstInput = entryList.getEntries()[0];

        // Measure First Input Delay (FID).
        const firstInputDelay = firstInput.processingStart - firstInput.startTime;

        // Measure the time it takes to run all event handlers
        // Note: this does not include work scheduled asynchronously using
        // methods like `requestAnimationFrame()` or `setTimeout()`.
        const firstInputProcessingTime = firstInput.processingEnd - firstInput.processingStart;

        // Measure the entire duration of the event, from when input is received by
        // the browser until the next frame can be painted after processing all
        // event handlers.
        // Note: similar to above, this value does not include work scheduled
        // asynchronously using `requestAnimationFrame()` or `setTimeout()`.
        // And for security reasons, this value is rounded to the nearest 8ms.
        const firstInputDuration = firstInput.duration;

        // Log these values the console.
        console.log({
          firstInputDelay,
          firstInputProcessingTime,
          firstInputDuration,
        });
      });

      po.observe({type: 'first-input', buffered: true});
    } catch (error) {
      // Do nothing if the browser doesn't support this API.
    }

### Resource Timing API <a href="#resource-timing-api" class="w-headline-link">#</a>

The [Resource Timing API](https://w3c.github.io/resource-timing/) gives developers detailed insight into how resources for a particular page were loaded. Despite the name of the API, the information it provides is not just limited to timing data (though there's [plenty of that](https://w3c.github.io/resource-timing/#processing-model)). Other data you can access includes:

-   [initiatorType](https://w3c.github.io/resource-timing/#dom-performanceresourcetiming-initiatortype): how the resource was fetched: such as from a `<script>` or `<link>` tag, or from `fetch()`
-   [nextHopProtocol](https://w3c.github.io/resource-timing/#dom-performanceresourcetiming-nexthopprotocol): the protocol used to fetch the resource, such as `h2` or `quic`
-   [encodedBodySize](https://w3c.github.io/resource-timing/#dom-performanceresourcetiming-encodedbodysize)/[decodedBodySize](https://w3c.github.io/resource-timing/#dom-performanceresourcetiming-decodedbodysize)\]: the size of the resource in its encoded or decoded form (respectively)
-   [transferSize](https://w3c.github.io/resource-timing/#dom-performanceresourcetiming-transfersize): the size of the resource that was actually transferred over the network. When resources are fulfilled via the cache, this value can be much smaller than the `encodedBodySize`, and in some cases it can be zero (if no cache revalidation is required).

Note, you can use the `transferSize` property of resource timing entries to measure a *cache hit rate* metric or perhaps even a *total cached resource size* metric, which may be useful in understanding how your resource caching strategy affects performance for repeat visitors.

The following example logs all resources requested by the page and indicates whether or not each resource was fulfilled via the cache.

    // Catch errors since some browsers throw when using the new `type` option.
    // https://bugs.webkit.org/show_bug.cgi?id=209216
    try {
      // Create the performance observer.
      const po = new PerformanceObserver((list) => {
        for (const entry of list.getEntries()) {
          // If transferSize is 0, the resource was fulfilled via the cache.
          console.log(entry.name, entry.transferSize === 0);
        }
      });
      // Start listening for `resource` entries to be dispatched.
      po.observe({type: 'resource', buffered: true});
    } catch (e) {
      // Do nothing if the browser doesn't support this API.
    }

### Navigation Timing API <a href="#navigation-timing-api" class="w-headline-link">#</a>

The [Navigation Timing API](https://w3c.github.io/navigation-timing/) is similar to the Resource Timing API, but it reports only [navigation requests](https://developers.google.com/web/fundamentals/primers/service-workers/high-performance-loading#first_what_are_navigation_requests). The `navigation` entry type is also similar to the `resource` entry type, but it contains some [additional information](https://w3c.github.io/navigation-timing/#sec-PerformanceNavigationTiming) specific to only navigation requests (such as when the `DOMContentLoaded` and `load` events fire).

One metric many developers track to understand server response time ([Time to First Byte](https://en.wikipedia.org/wiki/Time_to_first_byte)) is available via the Navigation Timing API—specifically it's entry's `responseStart` timestamp.

    // Catch errors since some browsers throw when using the new `type` option.
    // https://bugs.webkit.org/show_bug.cgi?id=209216
    try {
      // Create the performance observer.
      const po = new PerformanceObserver((list) => {
        for (const entry of list.getEntries()) {
          // If transferSize is 0, the resource was fulfilled via the cache.
          console.log('Time to first byte', entry.responseStart);
        }
      });
      // Start listening for `navigation` entries to be dispatched.
      po.observe({type: 'navigation', buffered: true});
    } catch (e) {
      // Do nothing if the browser doesn't support this API.
    }

Another metric developers who use service worker may care about is the service worker startup time for navigation requests. This is the amount of time it takes the browser to start the service worker thread before it can start intercepting fetch events.

The service worker startup time for a particular navigation request can be determined from the delta between `entry.responseStart` and `entry.workerStart`.

    // Catch errors since some browsers throw when using the new `type` option.
    // https://bugs.webkit.org/show_bug.cgi?id=209216
    try {
      // Create the performance observer.
      const po = new PerformanceObserver((list) => {
        for (const entry of list.getEntries()) {
          console.log('Service Worker startup time:',
              entry.responseStart - entry.workerStart);
        }
      });
      // Start listening for `navigation` entries to be dispatched.
      po.observe({type: 'navigation', buffered: true});
    } catch (e) {
      // Do nothing if the browser doesn't support this API.
    }

### Server Timing API <a href="#server-timing-api" class="w-headline-link">#</a>

The [Server Timing API](https://w3c.github.io/server-timing/) allows you to pass request-specific timing data from your server to the browser via response headers. For example, you can indicate how long it took to lookup data in a database for a particular request—which can be useful in debugging performance issues caused by slowness on the server.

For developers who use third-party analytics providers, the Server Timing API is the only way to correlate server performance data with other business metrics that these analytics tools may be measuring.

To specify server timing data in your responses, you can use the `Server-Timing` response header. Here's an example.

    HTTP/1.1 200 OK

    Server-Timing: miss, db;dur=53, app;dur=47.2

Then, from your pages, you can read this data on both `resource` or `navigation` entries from the Resource Timing and Navigation Timing APIs.

    // Catch errors since some browsers throw when using the new `type` option.
    // https://bugs.webkit.org/show_bug.cgi?id=209216
    try {
      // Create the performance observer.
      const po = new PerformanceObserver((list) => {
        for (const entry of list.getEntries()) {
          // Logs all server timing data for this response
          console.log('Server Timing', entry.serverTiming);
        }
      });
      // Start listening for `navigation` entries to be dispatched.
      po.observe({type: 'navigation', buffered: true});
    } catch (e) {
      // Do nothing if the browser doesn't support this API.
    }

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/metrics/" class="w-chip">Metrics</a>

<span class="w-mr--sm">Last updated: Nov 8, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/metrics/custom-metrics/index.md)

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
