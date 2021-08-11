<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#user-centric-performance-metrics" class="w-toc__header--link">User-centric performance metrics</a>
------------------------------------------------------------------------------------------------------------

-   [Defining metrics](#defining-metrics)
-   [How metrics are measured](#how-metrics-are-measured)
-   [In the lab](#in-the-lab)
-   [In the field](#in-the-field)
-   [Types of metrics](#types-of-metrics)
-   [Important metrics to measure](#important-metrics-to-measure)
-   [Custom metrics](#custom-metrics)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

User-centric performance metrics
================================

Nov 8, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/metrics" class="w-post-signpost__link">Metrics</a>

[<img src="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Philip Walton" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/philipwalton/)

<a href="/authors/philipwalton/" class="w-author__name-link">Philip Walton</a>

-   <a href="https://twitter.com/philwalton" class="w-author__link">Twitter</a>
-   <a href="https://github.com/philipwalton" class="w-author__link">GitHub</a>
-   <a href="https://philipwalton.com" class="w-author__link">Blog</a>

We've all heard how important performance is. But when we talk about performance—and about making websites "fast"—what specifically do we mean?

The truth is performance is relative:

-   A site might be fast for one user (on a fast network with a powerful device) but slow for another user (on a slow network with a low-end device).
-   Two sites may finish loading in the exact same amount of time, yet one may *seem* to load faster (if it loads content progressively rather than waiting until the end to display anything).
-   A site might *appear* to load quickly but then respond slowly (or not at all) to user interaction.

So when talking about performance, it's important to be precise and to refer to performance in terms of objective criteria that can be quantitatively measured. These criteria are known as *metrics*.

But just because a metric is based on objective criteria and can be quantitatively measured, it doesn't necessarily mean those measurements are useful.

Defining metrics <a href="#defining-metrics" class="w-headline-link">#</a>
--------------------------------------------------------------------------

Historically, web performance has been measured with the `load` event. However, even though `load` is a well-defined moment in a page's lifecycle, that moment doesn't necessarily correspond with anything the user cares about.

For example, a server could respond with a minimal page that "loads" immediately but then defers fetching content and displaying anything on the page until several seconds after the `load` event fires. While such a page might technically have a fast load time, that time would not correspond to how a user actually experiences the page loading.

Over the past few years, members of the Chrome team—in collaboration with the [W3C Web Performance Working Group](https://www.w3.org/webperf/)—have been working to standardize a set of new APIs and metrics that more accurately measure how users experience the performance of a web page.

To help ensure the metrics are relevant to users, we frame them around a few key questions:

<table><tbody><tr class="odd"><td><strong>Is it happening?</strong></td><td>Did the navigation start successfully? Has the server responded?</td></tr><tr class="even"><td><strong>Is it useful?</strong></td><td>Has enough content rendered that users can engage with it?</td></tr><tr class="odd"><td><strong>Is it usable?</strong></td><td>Can users interact with the page, or is it busy?</td></tr><tr class="even"><td><strong>Is it delightful?</strong></td><td>Are the interactions smooth and natural, free of lag and jank?</td></tr></tbody></table>

How metrics are measured <a href="#how-metrics-are-measured" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------

Performance metrics are generally measured in one of two ways:

-   **In the lab:** using tools to simulate a page load in a consistent, controlled environment
-   **In the field**: on real users actually loading and interacting with the page

Neither of these options is necessarily better or worse than the other—in fact you generally want to use both to ensure good performance.

### In the lab <a href="#in-the-lab" class="w-headline-link">#</a>

Testing performance in the lab is essential when developing new features. Before features are released in production, it's impossible to measure their performance characteristics on real users, so testing them in the lab before the feature is released is the best way to prevent performance regressions.

### In the field <a href="#in-the-field" class="w-headline-link">#</a>

On the other hand, while testing in the lab is a reasonable proxy for performance, it isn't necessarily reflective of how all users experience your site in the wild.

The performance of a site can vary dramatically based on a user's device capabilities and their network conditions. It can also vary based on whether (or how) a user is interacting with the page.

Moreover, page loads may not be deterministic. For example, sites that load personalized content or ads may experience vastly different performance characteristics from user to user. A lab test will not capture those differences.

The only way to truly know how your site performs for your users is to actually measure its performance as those users are loading and interacting with it. This type of measurement is commonly referred to as [Real User Monitoring](https://en.wikipedia.org/wiki/Real_user_monitoring)—or RUM for short.

Types of metrics <a href="#types-of-metrics" class="w-headline-link">#</a>
--------------------------------------------------------------------------

There are several other types of metrics that are relevant to how users perceive performance.

-   **Perceived load speed:** how quickly a page can load and render all of its visual elements to the screen.
-   **Load responsiveness:** how quickly a page can load and execute any required JavaScript code in order for components to respond quickly to user interaction
-   **Runtime responsiveness:** after page load, how quickly can the page respond to user interaction.
-   **Visual stability:** do elements on the page shift in ways that users don't expect and potentially interfere with their interactions?
-   **Smoothness:** do transitions and animations render at a consistent frame rate and flow fluidly from one state to the next?

Given all the above types of performance metrics, it's hopefully clear that no single metric is sufficient to capture all the performance characteristics of a page.

Important metrics to measure <a href="#important-metrics-to-measure" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------

-   **[First contentful paint (FCP)](/fcp/):** measures the time from when the page starts loading to when any part of the page's content is rendered on the screen. *([lab](#in-the-lab), [field](#in-the-field))*
-   **[Largest contentful paint (LCP)](/lcp/):** measures the time from when the page starts loading to when the largest text block or image element is rendered on the screen. *([lab](#in-the-lab), [field](#in-the-field))*
-   **[First input delay (FID)](/fid/):** measures the time from when a user first interacts with your site (i.e. when they click a link, tap a button, or use a custom, JavaScript-powered control) to the time when the browser is actually able to respond to that interaction. *([field](#in-the-field))*
-   **[Time to Interactive (TTI)](/tti/):** measures the time from when the page starts loading to when it's visually rendered, its initial scripts (if any) have loaded, and it's capable of reliably responding to user input quickly. *([lab](#in-the-lab))*
-   **[Total blocking time (TBT)](/tbt/):** measures the total amount of time between FCP and TTI where the main thread was blocked for long enough to prevent input responsiveness. *([lab](#in-the-lab))*
-   **[Cumulative layout shift (CLS)](/cls/):** measures the cumulative score of all unexpected layout shifts that occur between when the page starts loading and when its [lifecycle state](https://developers.google.com/web/updates/2018/07/page-lifecycle-api) changes to hidden. *([lab](#in-the-lab), [field](#in-the-field))*

While this list includes metrics measuring many of the various aspects of performance relevant to users, it does not include everything (e.g. runtime responsiveness and smoothness are not currently covered).

In some cases, new metrics will be introduced to cover missing areas, but in other cases the best metrics are ones specifically tailored to your site.

Custom metrics <a href="#custom-metrics" class="w-headline-link">#</a>
----------------------------------------------------------------------

The performance metrics listed above are good for getting a general understanding of the performance characteristics of most sites on the web. They're also good for having a common set of metrics for sites to compare their performance against their competitors.

However, there may be times when a specific site is unique in some way that requires additional metrics to capture the full performance picture. For example, the LCP metric is intended to measure when a page's main content has finished loading, but there could be cases where the largest element is not part of the page's main content and thus LCP may not be relevant.

To address such cases, the Web Performance Working Group has also standardized lower-level APIs that can be useful for implementing your own custom metrics:

-   [User Timing API](https://w3c.github.io/user-timing/)
-   [Long Tasks API](https://w3c.github.io/longtasks/)
-   [Element Timing API](https://wicg.github.io/element-timing/)
-   [Navigation Timing API](https://w3c.github.io/navigation-timing/)
-   [Resource Timing API](https://w3c.github.io/resource-timing/)
-   [Server timing](https://w3c.github.io/server-timing/)

Refer to the guide on [Custom Metrics](/custom-metrics/) to learn how to use these APIs to measure performance characteristics specific to your site.

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/metrics/" class="w-chip">Metrics</a>

<span class="w-mr--sm">Last updated: Nov 8, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/metrics/user-centric-performance-metrics/index.md)

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
