<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#using-the-chrome-ux-report-on-pagespeed-insights" class="w-toc__header--link">Using the Chrome UX Report on PageSpeed Insights</a>
--------------------------------------------------------------------------------------------------------------------------------------------

-   [Reading the data](#reading-the-data)
-   [Summary of origin performance](#summary-of-origin-performance)
-   [Null response when URL not available](#null-response-when-url-not-available)
-   [FAQ](#faq)
-   [When would I use PageSpeed Insights as opposed to other tools?](#when-would-i-use-pagespeed-insights-as-opposed-to-other-tools)
-   [Are there any limitations to using PageSpeed Insights?](#are-there-any-limitations-to-using-pagespeed-insights)
-   [Where can I learn more about PageSpeed Insights?](#where-can-i-learn-more-about-pagespeed-insights)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Using the Chrome UX Report on PageSpeed Insights
================================================

May 28, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rick Viscomi" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rviscomi/)

<a href="/authors/rviscomi/" class="w-author__name-link">Rick Viscomi</a>

-   <a href="https://twitter.com/rick_viscomi" class="w-author__link">Twitter</a>
-   <a href="https://github.com/rviscomi" class="w-author__link">GitHub</a>

[PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) (PSI) is a tool for web developers to understand what a page's performance is and how to improve it. It uses [Lighthouse](https://developers.google.com/web/tools/lighthouse/) to audit the page and identify opportunities to improve performance. It also integrates with the [Chrome UX Report](https://developers.google.com/web/tools/chrome-user-experience-report/) (CrUX) to show how real users experience the page and the origin in aggregate. In this guide, learn how to use PSI to extract insights from CrUX and better understand the user experience.

<img src="https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format" alt="Field data from CrUX in PageSpeed Insights" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/8ORarOdBzgJ5FAMkws7p.png?auto=format&amp;w=1600 1600w" width="800" height="703" />

Reading the data <a href="#reading-the-data" class="w-headline-link">#</a>
--------------------------------------------------------------------------

To get started, go to <https://developers.google.com/speed/pagespeed/insights/> and enter the URL of the page you want to test.

<img src="https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format" alt="Enter a URL to get started on PageSpeed Insights" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/5bnx9Xt0LT2XWk8Gpy3s.png?auto=format&amp;w=1600 1600w" width="800" height="203" />

After a few seconds, Lighthouse audits will be performed and you will see sections for Field and Lab data. CrUX is a collection of real user experiences from the field, while Lighthouse is a controlled test in the lab.

<img src="https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format" alt="Field data from CrUX in PageSpeed Insights" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/bKoL7v3vnO6Ttl70FkZe.png?auto=format&amp;w=1600 1600w" width="800" height="296" />

In the **Field Data** section, you'll see four metrics: [First Contentful Paint](/fcp/) (FCP), [First Input Delay](/fid/) (FID), [Largest Contentful Paint](/lcp/) (LCP), and [Cumulative Layout Shift](/cls/) (CLS). FID, LCP, and CLS are considered the [Core Web Vitals](/vitals/#core-web-vitals) metrics. These metrics are representative of the user experience in different ways:

-   **FCP** measures the time until the page displays something in the foreground, like some text or a logo.
-   **FID** measures the interactivity of the page, from the user's first interaction to the time the page responds to it.
-   **LCP** measures the time until the page displays what is likely its main content, like a hero image or heading.
-   **CLS** measures the degree of layout instability on the page, due to shifts like asynchronously loaded content being injected.

<table><thead><tr class="header"><th>Metric</th><th>"Good"</th><th>"Needs Improvement"</th><th>"Poor"</th></tr></thead><tbody><tr class="odd"><td>FCP</td><td>0–1000ms</td><td>1000ms–3000ms</td><td>3000ms+</td></tr><tr class="even"><td>FID</td><td>0–100ms</td><td>100–300ms</td><td>300ms+</td></tr><tr class="odd"><td>LCP</td><td>0–2500ms</td><td>2500–4000ms</td><td>4000ms+</td></tr><tr class="even"><td>CLS</td><td>0.00-0.10</td><td>0.10–0.25</td><td>0.25+</td></tr></tbody></table>

This table describes how values for these metrics are categorized as either "good", "needing improvement", or "poor".

There are three ways that the user experience is displayed in PSI:

-   a label summarizing the page as passing or not passing the Core Web Vitals assessment
-   percentiles measured in seconds or milliseconds (CLS is unitless)
-   a distribution representing the percent of "good", "needing improvement", and "poor" experiences

In the screenshot above, the page is labelled as "passing" the Core Web Vitals assessment. To pass, the percentile must be categorized as "good". Otherwise, the page is labelled as "not passing".

The percentiles shown for all metrics correspond to the 75th percentile. In statistics, a percentile is a measure that indicates the value below which a given percentage of samples fall. For example, the screenshot above shows that FID's 75th percentile is 15ms, meaning that 75% of FID experiences are faster than 15ms. These values are color-coded according to the threshold table above where "good" values are green, values "needing improvement" are orange, and "poor" values are red.

Finally, the distributions for each metric are illustrated using the "good", "needs improvement", and "poor" grouping. For example, FCP experiences on this page are "good" (less than 1 second) 44% of the time. FID is "poor" (at least 300 milliseconds) 1% of the time. These distributions represent all user experiences on the page and their shapes indicate the tendency to be either "good" or "poor".

Summary of origin performance <a href="#summary-of-origin-performance" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------

PSI also includes a summary of origin performance. This is an aggregation of user experiences across all pages of an origin. You can get the same stats for an entire origin that are available for individual pages. This data is closely aligned with what is available on [BigQuery](/chrome-ux-report-bigquery/), while the page-level performance is not made available to query.

<img src="https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format" alt="Origin CrUX performance in PageSpeed Insights" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/7Xr7VVdZMbRlEMlgq3cj.png?auto=format&amp;w=1600 1600w" width="800" height="371" />

There is one major difference between the origin-level data on PSI versus BigQuery. The datasets on BigQuery are released once a month and encompass the data from the previous calendar month. For example, the 202005 dataset includes all user experiences that occurred in May 2020. On the other hand, PSI aggregates new data every day encompassing the previous 28 days. So the results you see today may be different tomorrow and they would not necessarily be the same as what you'd see in the monthly aggregations on BigQuery.

Null response when URL not available <a href="#null-response-when-url-not-available" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------

If the URL you entered is not available in CrUX, you will see a null response like the one below, indicating that there is not enough field data. Lab data from Lighthouse is still available to give you an approximation of the page's performance.

<img src="https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format" alt="No CrUX data on PageSpeed Insights" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/TQSwqryJR9phVV5vjDs4.png?auto=format&amp;w=1600 1600w" width="800" height="202" />

FAQ <a href="#faq" class="w-headline-link">#</a>
------------------------------------------------

### When would I use PageSpeed Insights as opposed to other tools? <a href="#when-would-i-use-pagespeed-insights-as-opposed-to-other-tools" class="w-headline-link">#</a>

PSI combines the real-world user experience data of CrUX with the lab-based performance diagnostics of Lighthouse. This makes it easy to see how fast a page is experienced and how to make it faster all in one place. The daily aggregation of field data in PSI makes it a great place to more closely monitor origin or URL performance than tools with less frequent aggregations.

### Are there any limitations to using PageSpeed Insights? <a href="#are-there-any-limitations-to-using-pagespeed-insights" class="w-headline-link">#</a>

PSI only provides the most recent daily aggregation, so you wouldn't necessarily be able to see how a site's performance is trending. There are also some non-vital metrics included in the CrUX dataset that are not exposed in PSI.

### Where can I learn more about PageSpeed Insights? <a href="#where-can-i-learn-more-about-pagespeed-insights" class="w-headline-link">#</a>

Check out the [PSI documentation](https://developers.google.com/speed/docs/insights/v5/about) for more info.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: May 28, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/chrome-ux-report-pagespeed-insights/index.md)

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
