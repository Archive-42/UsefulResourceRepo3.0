





<a href="#use-lighthouse-for-performance-budgets" class="w-toc__header--link">Use Lighthouse for performance budgets</a>
------------------------------------------------------------------------------------------------------------------------

-   [Install Lighthouse](#install-lighthouse)
-   [Create a Budget](#create-a-budget)
-   [Run Lighthouse](#run-lighthouse)
-   [View the Results](#view-the-results)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

-   <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
-   <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

Use Lighthouse for performance budgets
======================================

Jun 14, 2019 <span class="w-author__separator">•</span> Updated Apr 3, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

-   <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
-   <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
-   <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

[Lighthouse](https://github.com/GoogleChrome/lighthouse) now supports performance budgets. This feature, [LightWallet](https://developers.google.com/web/tools/lighthouse/audits/budgets), can be set up in under five minutes and provides feedback on performance metrics and the size and quantity of page resources.

Install Lighthouse <a href="#install-lighthouse" class="w-headline-link">#</a>
------------------------------------------------------------------------------

LightWallet is available in the command line version of Lighthouse v5+.

To get started, install Lighthouse:

    npm install -g lighthouse

Create a Budget <a href="#create-a-budget" class="w-headline-link">#</a>
------------------------------------------------------------------------

Create a file named `budget.json`. In this file add the following JSON:

    [
      {
        "path": "/*",
        "timings": [
          {
            "metric": "interactive",
            "budget": 3000
          },
          {
            "metric": "first-meaningful-paint",
            "budget": 1000
          }
        ],
        "resourceSizes": [
          {
            "resourceType": "script",
            "budget": 125
          },
          {
            "resourceType": "total",
            "budget": 300
          }
        ],
        "resourceCounts": [
          {
            "resourceType": "third-party",
            "budget": 10
          }
        ]
      }
    ]

This example `budget.json` file sets five separate budgets:

-   A budget of 3000ms for Time to Interactive.
-   A budget of 1000ms for First Meaningful Paint
-   A budget of 125 KB for the total amount of JavaScript on the page.
-   A budget of 300 KB for the overall size of the page.
-   A budget of 10 requests for the number of requests made to third-party origins.

For a complete list of supported performance metrics and resource types, refer to the [Performance Budgets](https://github.com/GoogleChrome/lighthouse/blob/master/docs/performance-budgets.md) section of the Lighthouse docs.

Run Lighthouse <a href="#run-lighthouse" class="w-headline-link">#</a>
----------------------------------------------------------------------

Run Lighthouse using the `--budget-path` flag. This flag tells Lighthouse the location of your budget file.

    lighthouse https://example.com --budget-path=./budget.json

**Note**: A budget file does not have to be named `budget.json`.

View the Results <a href="#view-the-results" class="w-headline-link">#</a>
--------------------------------------------------------------------------

If LightWallet has been configured correctly, the Lighthouse report will contain a **Budgets** section within the **Performance** category.

<img src="https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format" alt="&#39;Budgets&#39; section of the Lighthouse report" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/FdUeI8rKZtJB3Ol624S3.png?auto=format&amp;w=1600 1600w" width="800" height="289" />

In the JSON version of the Lighthouse report, Lightwallet results can be found within the audit findings for the `performance-budget` audit.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Apr 3, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/use-lighthouse-for-performance-budgets/index.md)

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
