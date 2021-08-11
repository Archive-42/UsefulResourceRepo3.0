





## <a href="#using-the-chrome-ux-report-to-look-at-performance-in-the-field" class="w-toc__header--link">Using the Chrome UX Report to look at performance in the field</a>

- [How to use it](#how-to-use-it)
- [CrUX Dashboard](#crux-dashboard)
- [PageSpeed Insights](#pagespeed-insights)
- [CrUX on BigQuery](#crux-on-bigquery)
- [CrUX API](#crux-api)
- [How to get help](#how-to-get-help)
- [See it in action](#see-it-in-action)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Using the Chrome UX Report to look at performance in the field

Jul 13, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rick Viscomi" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rviscomi/)

<a href="/authors/rviscomi/" class="w-author__name-link">Rick Viscomi</a>

- <a href="https://twitter.com/rick_viscomi" class="w-author__link">Twitter</a>
- <a href="https://github.com/rviscomi" class="w-author__link">GitHub</a>

The [Chrome UX Report](https://developers.google.com/web/tools/chrome-user-experience-report/) (informally known as CrUX) is a public dataset of real user experience data on millions of websites. Unlike lab data, CrUX data actually comes from [opted-in users](https://developers.google.com/web/tools/chrome-user-experience-report/#methodology) in the field. It measures the [Core Web Vitals](/vitals/) metrics, including Largest Contentful Paint (LCP), First Input Delay (FID), and Cumulative Layout Shift (CLS), as well as diagnostic metrics like Time to First Byte (TTFB) and First Contentful Paint (FCP).

The dataset also contains qualitative dimensions about the user experience, for example, the device and connection types, which enables drilling down into user experiences grouped by similar technologies. See the [CrUX documentation](https://developers.google.com/web/tools/chrome-user-experience-report/#metrics) for the full list of metrics.

Using this data, developers are able to understand the wide distribution of real world user experiences between websites, segments of the web, or the web as a whole. This is a big deal! The Chrome UX Report dataset is the first of its kind to enable web developers to compare their real user performance against the competition and industry.

## How to use it <a href="#how-to-use-it" class="w-headline-link">#</a>

There are four primary ways to extract insights from the Chrome UX Report, ranging in complexity. For quick and easy analysis of website performance, the [CrUX Dashboard](http://g.co/chromeuxdash) and [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) are the recommended tools. [BigQuery](https://console.cloud.google.com/bigquery?p=chrome-ux-report) trades some of the simplicity of the analysis for the power of customization and more granular insights. And the [API](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference) enables the integration of high-level data with other applications.

### CrUX Dashboard <a href="#crux-dashboard" class="w-headline-link">#</a>

The [CrUX Dashboard](http://g.co/chromeuxdash) is a customizable data visualization tool of websites' historical performance built on [Data Studio](https://marketingplatform.google.com/about/data-studio/). The data is sourced from the BigQuery dataset and all of the SQL queries are handled for you under the hood. The dashboard shows the distribution of user experiences, as captured by key performance metrics, and how it changes over time. It also shows how the distributions of qualitative metrics like device type and effective connection type change over time. Try the [Data Studio Dashboard guide](/chrome-ux-report-data-studio-dashboard).

### PageSpeed Insights <a href="#pagespeed-insights" class="w-headline-link">#</a>

[PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) (PSI) shows the most recent performance distributions broken down by desktop and mobile users. Performance data is available for individual web pages (in addition to entire origins) and is aggregated for the most recent 28 days of data (as opposed to the previous calendar month on BigQuery). Using this tool is as easy as entering a URL or origin in the search box on the web interface, and the field performance data is displayed alongside prescriptive suggestions to optimize the page. Try the [PageSpeed Insights guide](/chrome-ux-report-pagespeed-insights).

### CrUX on BigQuery <a href="#crux-on-bigquery" class="w-headline-link">#</a>

The CrUX database on [BigQuery](https://console.cloud.google.com/bigquery?p=chrome-ux-report), part of the Google Cloud Platform (GCP) with a web and command line interface, hosts the raw data that aggregates key UX performance metrics for top origins on the web. New tables are periodically added to the database covering the previous calendar month. Developers can handcraft queries to mine the dataset for specific insights. BigQuery requires knowledge of SQL and a GCP project with billing enabled to run the queries. This is an especially useful tool for power users who require low-level access to the data to create custom reports, benchmarks, and reports about the state of the web. Try the [BigQuery guide](/chrome-ux-report-bigquery).

### CrUX API <a href="#crux-api" class="w-headline-link">#</a>

The CrUX API is a free and RESTful interface for looking up origin or URL-level user experience data. The data is updated daily and aggregates the previous 28 days of data, similar to PageSpeed Insights. You can use this API to build your own applications on top of the real-user experience data in CrUX. Try the [CrUX API](/chrome-ux-report-api) guide.

## How to get help <a href="#how-to-get-help" class="w-headline-link">#</a>

If you need any kind of support, there are a few channels to reach someone who can help. The [CrUX Google Group](https://groups.google.com/a/chromium.org/forum/#!forum/chrome-ux-report) is a public forum for users of the dataset to ask questions and share analyses. There is also a [CrUX tag for Stack Overflow](https://stackoverflow.com/questions/tagged/chrome-ux-report) if you need programming help with SQL or API access. And finally, [@ChromeUXReport](https://twitter.com/ChromeUXReport) is the Twitter account you can follow to ask questions and listen for product announcements.

## See it in action <a href="#see-it-in-action" class="w-headline-link">#</a>

In order to get more acquainted with the available data, walk through step-by-step guides for using BigQuery, Data Studio Dashboard, and PageSpeed Insights:

- [CrUX: Data Studio Dashboard](/chrome-ux-report-data-studio-dashboard)
- [CrUX: PageSpeed Insights](/chrome-ux-report-pagespeed-insights)
- [CrUX: BigQuery](/chrome-ux-report-bigquery)
- [CrUX: API](/chrome-ux-report-api)

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jul 13, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/chrome-ux-report/index.md)

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
