## <a href="#using-the-chrome-ux-report-on-bigquery" class="w-toc__header--link">Using the Chrome UX Report on BigQuery</a>

- [Data organization](#data-organization)
- [Evaluating performance](#evaluating-performance)
- [Tracking performance](#tracking-performance)
- [FAQ](#faq)
- [When would I use BigQuery as opposed to other tools?](#when-would-i-use-bigquery-as-opposed-to-other-tools)
- [Are there any limitations to using BigQuery?](#are-there-any-limitations-to-using-bigquery)
- [Where can I learn more about BigQuery?](#where-can-i-learn-more-about-bigquery)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Using the Chrome UX Report on BigQuery

Jun 12, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rick Viscomi" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rviscomi/)

<a href="/authors/rviscomi/" class="w-author__name-link">Rick Viscomi</a>

- <a href="https://twitter.com/rick_viscomi" class="w-author__link">Twitter</a>
- <a href="https://github.com/rviscomi" class="w-author__link">GitHub</a>

The raw data of the Chrome UX Report ([CrUX](https://developers.google.com/web/tools/chrome-user-experience-report/)) is available on [BigQuery](https://console.cloud.google.com/bigquery?p=chrome-ux-report), a database on the Google Cloud Platform (GCP). Using BigQuery requires a [GCP project](https://developers.google.com/web/tools/chrome-user-experience-report/getting-started#getting-started) and basic knowledge of SQL.

In this guide, learn how to use BigQuery to write queries against the CrUX dataset to extract insightful results about the state of user experiences on the web:

- Understand how the data is organized
- Write a basic query to evaluate an origin's performance
- Write an advanced query to track performance over time

## Data organization <a href="#data-organization" class="w-headline-link">#</a>

Start by looking at a basic query:

    SELECT COUNT(DISTINCT origin) FROM `chrome-ux-report.all.201809`

To run the query, enter it into the query editor and press the "Run query" button:

<img src="https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format" alt="Enter a simple query into editor and press Run." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/aZp9WdPcgiTa7j7R1cAP.png?auto=format&amp;w=1600 1600w" width="800" height="430" />

There are two parts to this query:

- `SELECT COUNT(DISTINCT origin)` means querying for the number of origins in the table. Roughly speaking, two URLs are part of the same origin if they have the same scheme, host, and port.

- `FROM`chrome-ux-report.all.201809\`\` specifies the address of the source table, which has three parts:

  - The Cloud project name `chrome-ux-report` within which all CrUX data is organized
  - The dataset `all`, representing data across all countries
  - The table `201809`, the year and month of the data in YYYYMM format

There are also datasets for every country. For example, `chrome-ux-report.country_ca.201809` represents only the user experience data originating from Canada.

Within each dataset there are tables for every month since 201710. New tables for the previous calendar month are published regularly.

The structure of the data tables (also known as the _schema_) contains:

- The origin, e.g., `origin = 'https://www.example.com'`, which represents the aggregate user experience distribution for all pages on that website
- The connection speed at the time of page load, e.g., `effective_connection_type.name = '4G'`
- The device type, e.g., `form_factor.name = 'desktop'`
- The UX metrics themselves
  - first_paint (FP)
  - first_contentful_paint (FCP)
  - dom_content_loaded (DCL)
  - onload (OL)
  - experimental.first_input_delay (FID)

The data for each metric is organized as an array of objects. In JSON notation, `first_contentful_paint.histogram.bin` would look similar to this:

    [
      {"start": 0, "end": 100, "density": 0.1234},
       {"start": 100, "end": 200, "density": 0.0123},
     ...
    ]

Each bin contains a start and an end time in milliseconds and a density representing the percent of user experiences within that time range. In other words, 12.34% of FCP experiences for this hypothetical origin, connection speed, and device type are less than 100ms. The sum of all bin densities is 100%.

[Browse the structure of the tables in BigQuery.](https://bigquery.cloud.google.com/table/chrome-ux-report:all.201809?tab=preview)

## Evaluating performance <a href="#evaluating-performance" class="w-headline-link">#</a>

Let's use our knowledge of the table schema to write a query that extracts this performance data.

    SELECT
      fcp
    FROM
      `chrome-ux-report.all.201809`,
      UNNEST(first_contentful_paint.histogram.bin) AS fcp
    WHERE
      origin = 'https://developers.google.com' AND
      effective_connection_type.name = '4G' AND
      form_factor.name = 'phone' AND
      fcp.start = 0

<img src="https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format" alt="Querying CrUX FCP on BigQuery" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/ReMoTLXeKjiMqC95PJoV.png?auto=format&amp;w=1600 1600w" width="800" height="670" />

The result is `0.0013`, meaning that 0.13% of user experiences on this origin are between 0 and 100ms on 4G and on a phone. If we want to generalize our query to any connection and any device type, we can omit them from the `WHERE` clause and simply use the `SUM` aggregator function to add up all of their respective bin densities:

    SELECT
      SUM(fcp.density)
    FROM
      `chrome-ux-report.all.201809`,
      UNNEST(first_contentful_paint.histogram.bin) AS fcp
    WHERE
      origin = 'https://developers.google.com' AND
      fcp.start = 0

<img src="https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format" alt="Summing CrUX FCP on BigQuery" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/SaNxd4ZfYHaBGgz8yUJM.png?auto=format&amp;w=1600 1600w" width="800" height="676" />

The result is `0.0399`, or 3.99% across all devices and connection types. Let's modify the query slightly and add up the densities for all bins that are in the "fast" FCP range of 0–1000ms:

    SELECT
      SUM(fcp.density) AS fast_fcp
    FROM
      `chrome-ux-report.all.201809`,
      UNNEST(first_contentful_paint.histogram.bin) AS fcp
    WHERE
      origin = 'https://developers.google.com' AND
      fcp.start < 1000

<img src="https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format" alt="Querying fast FCP on BigQuery" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/jkK04PN5sGQxaYnLwmh3.png?auto=format&amp;w=1600 1600w" width="800" height="672" />

This gives us `0.3913`. In other words, 39.13% of the FCP user experiences on developers.google.com are considered "fast" according to the FCP range definition.

## Tracking performance <a href="#tracking-performance" class="w-headline-link">#</a>

Now that we've extracted performance data about an origin, let's compare it to the historical data available in older tables. To do that, we could rewrite the table address to an earlier month, or we could use the wildcard syntax to query all months:

    SELECT
      _TABLE_SUFFIX AS yyyymm,
      SUM(fcp.density) AS fast_fcp
    FROM
      `chrome-ux-report.all.*`,
      UNNEST(first_contentful_paint.histogram.bin) AS fcp
    WHERE
      origin = 'https://developers.google.com' AND
      fcp.start < 1000
    GROUP BY
      yyyymm
    ORDER BY
      yyyymm

<img src="https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format" alt="Querying a timeseries of CrUX FCP on BigQuery" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/yynnLgYHstp0307DmkBv.png?auto=format&amp;w=1600 1600w" width="800" height="1219" />

Here, we see that the percent of fast FCP experiences varies by a few percentage points each month.

<table><thead><tr class="header"><th>yyyymm</th><th>fast_fcp</th></tr></thead><tbody><tr class="odd"><td>201711</td><td>40.17%</td></tr><tr class="even"><td>201712</td><td>38.27%</td></tr><tr class="odd"><td>201801</td><td>39.89%</td></tr><tr class="even"><td>201802</td><td>39.76%</td></tr><tr class="odd"><td>201803</td><td>41.17%</td></tr><tr class="even"><td>201804</td><td>41.31%</td></tr><tr class="odd"><td>201805</td><td>41.55%</td></tr><tr class="even"><td>201806</td><td>40.73%</td></tr><tr class="odd"><td>201807</td><td>40.63%</td></tr><tr class="even"><td>201808</td><td>37.75%</td></tr><tr class="odd"><td>201809</td><td>39.13%</td></tr></tbody></table>

With these techniques, you're able to look up the performance for an origin, calculate the percent of fast experiences, and track it over time. As a next step, try querying for two or more origins and comparing their performance.

## FAQ <a href="#faq" class="w-headline-link">#</a>

### When would I use BigQuery as opposed to other tools? <a href="#when-would-i-use-bigquery-as-opposed-to-other-tools" class="w-headline-link">#</a>

BigQuery is only needed when you can't get the same information from other tools like the CrUX Dashboard and PageSpeed Insights. For example, BigQuery allows you to slice the data in meaningful ways and even join it with other public datasets like the [HTTP Archive](https://httparchive.org/) to do some advanced data mining.

### Are there any limitations to using BigQuery? <a href="#are-there-any-limitations-to-using-bigquery" class="w-headline-link">#</a>

Yes, the most important limitation is that by default users can only query 1TB worth of data per month. Beyond that, the standard rate of $5/TB applies.

### Where can I learn more about BigQuery? <a href="#where-can-i-learn-more-about-bigquery" class="w-headline-link">#</a>

Check out the [BigQuery documentation](https://cloud.google.com/bigquery/) for more info.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jun 12, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/chrome-ux-report-bigquery/index.md)

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
