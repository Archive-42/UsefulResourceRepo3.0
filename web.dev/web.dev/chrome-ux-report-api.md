<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/TQ4U8BZanGFSfJI973xn.png?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#using-the-chrome-ux-report-api" class="w-toc__header--link">Using the Chrome UX Report API</a>
--------------------------------------------------------------------------------------------------------

-   [Querying origin data](#querying-origin-data)
-   [Errors](#errors)
-   [Querying URL data](#querying-url-data)
-   [URL normalization](#url-normalization)
-   [Querying by form factor](#querying-by-form-factor)
-   [Assessing Core Web Vitals performance](#assessing-core-web-vitals-performance)
-   [What's next?](#what's-next)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

-   <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
-   <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

Using the Chrome UX Report API
==============================

Learn how to use the Chrome UX Report API to get easy, RESTful access to real-user experience data across millions of websites.

Jun 25, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rick Viscomi" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rviscomi/)

<a href="/authors/rviscomi/" class="w-author__name-link">Rick Viscomi</a>

-   <a href="https://twitter.com/rick_viscomi" class="w-author__link">Twitter</a>
-   <a href="https://github.com/rviscomi" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/yPytekIqH5VnoqMx3jj2.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Shane Exterkamp" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/yPytekIqH5VnoqMx3jj2.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/yPytekIqH5VnoqMx3jj2.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/yPytekIqH5VnoqMx3jj2.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/yPytekIqH5VnoqMx3jj2.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/yPytekIqH5VnoqMx3jj2.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/exterkamp/)

<a href="/authors/exterkamp/" class="w-author__name-link">Shane Exterkamp</a>

-   <a href="https://twitter.com/shane_exterkamp" class="w-author__link">Twitter</a>
-   <a href="https://github.com/exterkamp" class="w-author__link">GitHub</a>

The [Chrome UX Report](https://developers.google.com/web/tools/chrome-user-experience-report) (CrUX) dataset represents how real-world Chrome users experience popular destinations on the web. Since 2017, when the queryable dataset was first released on [BigQuery](/chrome-ux-report-bigquery/), field data from CrUX has been integrated into developer tools like [PageSpeed Insights](/chrome-ux-report-pagespeed-insights/), the [CrUX Dashboard](/chrome-ux-report-data-studio-dashboard/), and Search Console's [Core Web Vitals report](https://support.google.com/webmasters/answer/9205520), enabling developers to easily measure and monitor real-user experiences. The piece that has been missing all this time has been a tool that provides free and RESTful access to CrUX data programmatically. To help bridge that gap, we're excited to announce the release of the all new [Chrome UX Report API](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference)!

This API has been built with the goal of providing developers with simple, fast, and comprehensive access to CrUX data. The CrUX API only reports [*field*](/how-to-measure-speed/#lab-data-vs-field-data) user experience data, unlike the existing [PageSpeed Insights API](https://developers.google.com/speed/docs/insights/v5/get-started), which also reports *lab* data from the Lighthouse performance audits. The CrUX API is streamlined and can quickly serve user experience data, making it ideally suited for real-time auditing applications.

To ensure that developers have access to all of the metrics that matter the most—the [Core Web Vitals](/vitals/#core-web-vitals)—the CrUX API audits and monitors [Largest Contentful Paint](/lcp/) (LCP), [First Input Delay](/fid/) (FID), and [Cumulative Layout Shift](/cls/) (CLS) at both the origin and URL level.

So let's dive in and see how to use it!

Querying origin data <a href="#querying-origin-data" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

Origins in the CrUX dataset encompass all underlying page-level experiences. The example below demonstrates how to query the CrUX API for an origin's user experience data using cURL on the command line.

    API_KEY="[YOUR_API_KEY]"
    curl "https://chromeuxreport.googleapis.com/v1/records:queryRecord?key=$API_KEY" \
      --header 'Content-Type: application/json' \
      --data '{"origin": "https://web.dev"}'

Run this query interactively in the [CrUX API explorer](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference/rest/v1/records/queryRecord?apix=true&apix_params=%7B%22resource%22%3A%7B%22origin%22%3A%22https%3A%2F%2Fwww.google.com%22%7D%7D).

All API requests must provide a value for the `key` parameter—`[YOUR_API_KEY]` in the example above is left as a placeholder. Get your own private CrUX API key at the click of a button in the official [CrUX API documentation](https://goo.gle/crux-api-key). For convenience, the interactive [CrUX API explorer](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference/rest/v1/records/queryRecord?apix=true) does not require an API key.

The `curl` command is made up of three parts:

1.  The URL endpoint of the API, including the caller's private API key.
2.  The `Content-Type: application/json` header, indicating that the request body contains JSON.
3.  The JSON-encoded [request body](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference/rest/v1/records/queryRecord#request-body), specifying the `https://web.dev` origin.

To do the same thing in JavaScript, use the <span id="crux-api-util">`CrUXApiUtil`</span> utility, which makes the API call and returns the decoded response.

    const CrUXApiUtil = {};
    // Get your CrUX API key at https://goo.gle/crux-api-key.
    CrUXApiUtil.API_KEY = '[YOUR_API_KEY]';
    CrUXApiUtil.API_ENDPOINT = `https://chromeuxreport.googleapis.com/v1/records:queryRecord?key=${CrUXApiUtil.API_KEY}`;
    CrUXApiUtil.query = function (requestBody) {
      if (CrUXApiUtil.API_KEY == '[YOUR_API_KEY]') {
        throw 'Replace "YOUR_API_KEY" with your private CrUX API key. Get a key at https://goo.gle/crux-api-key.';
      }
      return fetch(CrUXApiUtil.API_ENDPOINT, {
        method: 'POST',
        body: JSON.stringify(requestBody)
      }).then(response => response.json()).then(response => {
        if (response.error) {
          return Promise.reject(response);
        }
        return response;
      });
    };

Replace `[YOUR_API_KEY]` with your [key](https://goo.gle/crux-api-key). Next, call the `CrUXApiUtil.query` function and pass in the [request body](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference/rest/v1/records/queryRecord#request-body) object.

    CrUXApiUtil.query({
      origin: 'https://web.dev'
    }).then(response => {
      console.log(response);
    }).catch(response => {
      console.error(response);
    });

If data exists for this origin, the API response is a JSON-encoded object containing [metrics](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference/rest/v1/Metric) representing the distribution of user experiences. The distribution metrics are histogram bins and percentiles.

    {
      "record": {
        "key": {
          "origin": "https://web.dev"
        },
        "metrics": {
          "largest_contentful_paint": {
            "histogram": [
              {
                "start": 0,
                "end": 2500,
                "density": 0.7925068547983514
              },
              {
                "start": 2500,
                "end": 4000,
                "density": 0.1317422195536863
              },
              {
                "start": 4000,
                "density": 0.07575092564795324
              }
            ],
            "percentiles": {
              "p75": 2216
            }
          },
          // ...
        }
      }
    }

The `start` and `end` properties of the `histogram` object represent the range of values users experience for the given metric. The `density` property represents the proportion of user experiences within that range. In this example, 79% of LCP user experiences across all web.dev pages are under 2,500 milliseconds, which is the "[good](/lcp/#what-is-lcp)" LCP threshold. The `percentiles.p75` value means that 75% of user experiences in this distribution are less than 2,216 milliseconds. Learn more about the response structure in the [response body](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference/rest/v1/records/queryRecord#response-body) documentation.

### Errors <a href="#errors" class="w-headline-link">#</a>

When the CrUX API doesn't have any data for a given origin, it responds with a JSON-encoded error message:

    {
      "error": {
        "code": 404,
        "message": "chrome ux report data not found",
        "status": "NOT_FOUND"
      }
    }

To debug this error, first check that the requested origin is publicly navigable. You can test this by entering the origin into your browser's URL bar and comparing it against the final URL after any redirects. Common problems include unnecessarily adding or omitting the subdomain and using the wrong HTTP protocol.

Error

    {"origin": "http://www.web.dev"}

This origin incorrectly includes the `http://` protocol and `www.` subdomain.

Success

    {"origin": "https://web.dev"}

This origin is publicly navigable.

If the requested origin *is* the navigable version, this error may also occur if the origin has an insufficient number of samples. All origins and URLs included in the dataset must have a sufficient number of samples to anonymize individual users. Additionally, origins and URLs must be [publicly crawlable](https://developers.google.com/search/reference/robots_txt). Refer to the [CrUX methodology](https://developers.google.com/web/tools/chrome-user-experience-report#methodology) to learn more about how websites are included in the dataset.

Querying URL data <a href="#querying-url-data" class="w-headline-link">#</a>
----------------------------------------------------------------------------

You've seen how to query the CrUX API for the overall user experience on an origin. To restrict the results to a particular page, use the `url` request parameter.

    API_KEY="[YOUR_API_KEY]"
    curl "https://chromeuxreport.googleapis.com/v1/records:queryRecord?key=$API_KEY" \
      --header 'Content-Type: application/json' \
      --data '{"url": "https://web.dev/fast/"}'

This cURL command is similar to the origin example, except that the request body uses the `url` parameter to specify the page to look up.

To query URL data from the CrUX API in JavaScript, call the [`CrUXApiUtil.query`](#crux-api-util) function using the `url` parameter in the request body.

    CrUXApiUtil.query({
      url: 'https://web.dev/fast/'
    }).then(response => {
      console.log(response);
    }).catch(response => {
      console.error(response);
    });

If data for this URL exists in the CrUX dataset, the API will return a JSON-encoded response like the one below.

    {
      "record": {
        "key": {
          "url": "https://web.dev/fast/"
        },
        "metrics": {
          "largest_contentful_paint": {
            "histogram": [
              {
                "start": 0,
                "end": 2500,
                "density": 0.8477304539092148
              },
              {
                "start": 2500,
                "end": 4000,
                "density": 0.08988202359528057
              },
              {
                "start": 4000,
                "density": 0.062387522495501155
              }
            ],
            "percentiles": {
              "p75": 1947
            }
          },
          // ...
        }
      }
    }

True to form, the results show that `https://web.dev/fast/` has 85% "good" LCP experiences and a 75th percentile of 1,947 milliseconds, which is slightly better than the origin-wide distribution.

### URL normalization <a href="#url-normalization" class="w-headline-link">#</a>

The CrUX API may normalize requested URLs to better match the list of known URLs. For example, querying for the URL `https://web.dev/fast/#measure-performance-in-the-field` will result in data for `https://web.dev/fast/` due to normalization. When this happens, a `urlNormalizationDetails` object will be included in the response.

    {
      "record": {
        "key": {
          "url": "https://web.dev/fast/"
        },
        "metrics": { ... }
      },
      "urlNormalizationDetails": {
        "normalizedUrl": "https://web.dev/fast/",
        "originalUrl": "https://web.dev/fast/#measure-performance-in-the-field"
      }
    }

Learn more about [URL normalization](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference/rest/v1/records/queryRecord#urlnormalization) in the CrUX documentation.

Querying by form factor <a href="#querying-by-form-factor" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

**Key Term**: A form factor is the type of device on which a user visits a website. Common device types include desktop, phone, and tablet.

User experiences can vary significantly depending on website optimizations, network conditions, and users' devices. To better understand these differences, drill down into origin and URL performance using the [`formFactor`](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference/rest/v1/records/queryRecord#formfactor) dimension of the CrUX API.

The API supports three explicit form factor values: `DESKTOP`, `PHONE`, and `TABLET`. In addition to the origin or URL, specify one of these values in the [request body](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference/rest/v1/records/queryRecord#request-body) to restrict results to only those user experiences. The example below demonstrates how to query the API by form factor using cURL.

    API_KEY="[YOUR_API_KEY]"
    curl "https://chromeuxreport.googleapis.com/v1/records:queryRecord?key=$API_KEY" \
      --header 'Content-Type: application/json' \
      --data '{"url": "https://web.dev/fast/", "formFactor": "PHONE"}'

To query the CrUX API for form factor-specific data using JavaScript, call the [`CrUXApiUtil.query`](#crux-api-util) function using the `url` and `formFactor` parameters in the request body.

    CrUXApiUtil.query({
      url: 'https://web.dev/fast/',
      formFactor: 'PHONE'
    }).then(response => {
      console.log(response);
    }).catch(response => {
      console.error(response);
    });

Omitting the `formFactor` parameter is equivalent to requesting data for all form factors combined.

    {
      "record": {
        "key": {
          "url": "https://web.dev/fast/",
          "formFactor": "PHONE"
        },
        "metrics": {
          "largest_contentful_paint": {
            "histogram": [
              {
                "start": 0,
                "end": 2500,
                "density": 0.778631284916204
              },
              {
                "start": 2500,
                "end": 4000,
                "density": 0.13943202979515887
              },
              {
                "start": 4000,
                "density": 0.08193668528864119
              }
            ],
            "percentiles": {
              "p75": 2366
            }
          },
        // ...
        }
      }
    }

The `key` field of the response will echo back the `formFactor` request configuration to confirm that only phone experiences are included.

**Caution**: The more fine-grained the request is, for example a specific combination of URL and form factor, the fewer user experiences it will include. This may lead to more frequent "not found" errors, especially when querying less popular URLs or the less popular tablet device type.

Recall from the previous section that 85% of user experiences on this page had "good" LCP. Compare that to phone-specific experiences, of which only 78% are considered "good". The 75th percentile is also slower among phone experiences, up from 1,947 milliseconds to 2,366 milliseconds. Segmenting by form factor has the potential to highlight more extreme disparities in user experiences.

Assessing Core Web Vitals performance <a href="#assessing-core-web-vitals-performance" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------

The [Core Web Vitals](/vitals/#core-web-vitals) program defines targets that help determine whether a user experience or a distribution of experiences can be considered "good". In the following example, we use the CrUX API and the [`CrUXApiUtil.query`](#crux-api-util) function to assess whether a web page's distribution of Core Web Vitals metrics (LCP, FID, CLS) are "good".

    CrUXApiUtil.query({
      url: 'https://web.dev/fast/'
    }).then(response => {
      assessCoreWebVitals(response);
    }).catch(response => {
      console.error(response);
    });

    function assessCoreWebVitals(response) {
      // See https://web.dev/vitals/#core-web-vitals.
      const CORE_WEB_VITALS = [
        'largest_contentful_paint',
        'first_input_delay',
        'cumulative_layout_shift'
      ];
      CORE_WEB_VITALS.forEach(metric => {
        const data = response.record.metrics[metric];
        if (!data) {
          console.log('No data for', metric);
          return;
        }
        const p75 = data.percentiles.p75;
        const threshold = data.histogram[0].end;
        // A Core Web Vitals metric passes the assessment if
        // its 75th percentile is under the "good" threshold.
        const passes = p75 < threshold;
        console.log(`The 75th percentile (${p75}) of ${metric} ` +
            `${passes ? 'passes' : 'does not pass'} ` +
            `the Core Web Vitals "good" threshold (${threshold}).`)
      });
    }

**Gotchas!**

The API may only be called with one origin or URL at a time. To assess multiple websites or pages, make separate calls to the API.

The results show that this page passes the Core Web Vitals assessments for all three metrics.

    The 75th percentile (1973) of largest_contentful_paint passes the Core Web Vitals "good" threshold (2500).
    The 75th percentile (20) of first_input_delay passes the Core Web Vitals "good" threshold (100).
    The 75th percentile (0.05) of cumulative_layout_shift passes the Core Web Vitals "good" threshold (0.10).

Combined with an automated way to monitor API results, data from CrUX can be used to ensure that real-user experiences **get fast** and **stay fast**. For more information about Core Web Vitals and how to measure them, check out [Web Vitals](/vitals) and [Tools to measure Core Web Vitals](/vitals-tools).

What's next? <a href="#what&#39;s-next" class="w-headline-link">#</a>
---------------------------------------------------------------------

The features included in the initial version of the CrUX API only scratch the surface of the kinds of insights that are possible with CrUX. Users of the [CrUX dataset on BigQuery](/chrome-ux-report-bigquery/) may be familiar with some of the more advanced features including:

-   Additional metrics
    -   `first_paint`
    -   `dom_content_loaded`
    -   `onload`
    -   `time_to_first_byte`
    -   `notification_permissions`
-   Additional dimensions
    -   month
    -   country
    -   effective connection type (ECT)
-   Additional granularity
    -   detailed histograms
    -   more percentiles

Over time, we hope to integrate more of these features with the CrUX API's ease of use and free pricing to enable new ways of exploring the data and discovering insights about the state of user experiences on the web.

Check out the official [CrUX API docs](https://developers.google.com/web/tools/chrome-user-experience-report/api/reference) to [acquire your API key](https://goo.gle/crux-api-key) and explore more example applications. We hope you'll give it a try and we'd love to hear any questions or feedback you may have, so please reach out to us on the [CrUX discussion forum](https://groups.google.com/a/chromium.org/forum/#!forum/chrome-ux-report). And to stay up to date on everything we have planned for the CrUX API, subscribe to the [CrUX announcement forum](https://groups.google.com/a/chromium.org/forum/#!forum/chrome-ux-report-announce) or follow us on Twitter at [@ChromeUXReport](https://twitter.com/ChromeUXReport).

<a href="/tags/chrome-ux-report/" class="w-chip">Chrome UX Report</a> <a href="/tags/web-vitals/" class="w-chip">Web Vitals</a> <a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/metrics/" class="w-chip">Metrics</a>

<span class="w-mr--sm">Last updated: Jun 25, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/chrome-ux-report-api/index.md)

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