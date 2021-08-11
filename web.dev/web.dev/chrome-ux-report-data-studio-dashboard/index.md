<img src="https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/k3hWnnwqTvg7w7URsbIK.png?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#using-the-crux-dashboard-on-data-studio" class="w-toc__header--link">Using the CrUX Dashboard on Data Studio</a>

- [Creating a dashboard](#creating-a-dashboard)
- [Using the dashboard](#using-the-dashboard)
- [Core Web Vitals overview](#core-web-vitals-overview)
- [Metric performance](#metric-performance)
- [User demographics](#user-demographics)
- [FAQ](#faq)
- [When would I use the CrUX Dashboard as opposed to other tools?](#when-would-i-use-the-crux-dashboard-as-opposed-to-other-tools)
- [Are there any limitations to using the CrUX Dashboard?](#are-there-any-limitations-to-using-the-crux-dashboard)
- [Where can I learn more about Data Studio?](#where-can-i-learn-more-about-data-studio)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Using the CrUX Dashboard on Data Studio

Jun 22, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rick Viscomi" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/oWRqaR6XXwIdNXPLpUMn.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rviscomi/)

<a href="/authors/rviscomi/" class="w-author__name-link">Rick Viscomi</a>

- <a href="https://twitter.com/rick_viscomi" class="w-author__link">Twitter</a>
- <a href="https://github.com/rviscomi" class="w-author__link">GitHub</a>

[Data Studio](https://marketingplatform.google.com/about/data-studio/) is a powerful data visualization tool that enables you to build dashboards on top of big data sources, like the [Chrome UX Report](https://developers.google.com/web/tools/chrome-user-experience-report/) (CrUX). In this guide, learn how to create your own custom CrUX Dashboard to track an origin's user experience trends.

<img src="https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format" alt="CrUX Dashboard" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=1600 1600w" width="800" height="598" />

The CrUX Dashboard is built with a Data Studio feature called [Community Connectors](https://developers.google.com/datastudio/connector/). This connector is a pre-established link between the raw CrUX data on [BigQuery](https://console.cloud.google.com/bigquery?p=chrome-ux-report) and the visualizations of Data Studio. It eliminates the need for users of the dashboard to write any queries or generate any charts. Everything is built for you; all you need is to provide an origin and a custom dashboard will be generated for you.

## Creating a dashboard <a href="#creating-a-dashboard" class="w-headline-link">#</a>

To get started, go to [g.co/chromeuxdash](https://g.co/chromeuxdash). This will take you to the CrUX community connector page where you can provide the origin for which the dashboard will be generated. Note that first-time users may need to complete permission or marketing preference prompts.

<img src="https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format" alt="CrUX Dashboard connector" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/SSUqCau3HiN5qBbewX6h.png?auto=format&amp;w=1600 1600w" width="800" height="484" />

The text input field only accepts origins, not full URLs. For example:

Origin (Supported)

    https://developers.google.com

URL (Not supported)

    https://developers.google.com/web/tools/chrome-user-experience-report/

If you omit the protocol, HTTPS is assumed. Subdomains matter, for example `https://developers.google.com` and `https://www.google.com` are considered to be different origins.

Some common issues with origins are providing the wrong protocol, for example `http://` instead of `https://`, and omitting the subdomain when needed. Some websites include redirects, so if `http://example.com` redirects to `https://www.example.com`, then you should use the latter, which is the canonical version of the origin. As a rule of thumb, use whichever origin users see in the URL bar.

If your origin is not included in the CrUX dataset, you may get an error message like the one below. There are over 4 million origins in the dataset, but the one you want may not have sufficient data to be included.

<img src="https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format" alt="CrUX Dashboard error message" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/qt0jWTgtdS93hDKW2SCm.png?auto=format&amp;w=1600 1600w" width="800" height="409" />

If the origin exists, you'll be taken to the schema page for the dashboard. This shows you all of the fields that are included: each effective connection type, each form factor, the month of the dataset release, the distribution of performance for each metric, and of course the name of the origin. There's nothing you need to do or change on this page, just click **Create Report** to continue.

<img src="https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format" alt="CrUX Dashboard schema" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/DTNigYO4gUwovCuCgyhH.png?auto=format&amp;w=1600 1600w" width="800" height="403" />

## Using the dashboard <a href="#using-the-dashboard" class="w-headline-link">#</a>

Each dashboard comes with three types of pages:

1.  Core Web Vitals overview
2.  Metric performance
3.  User demographics

Each page includes a chart showing distributions over time for each available monthly release. As new datasets are released, you can simply refresh the dashboard to get the latest data.

The monthly datasets are released on the second Tuesday of every month. For example, the dataset consisting of user experience data from the month of May is released on the second Tuesday of June.

### Core Web Vitals overview <a href="#core-web-vitals-overview" class="w-headline-link">#</a>

The first page is an overview of the origin's monthly [Core Web Vitals](/vitals/) performance. These are the most important UX metrics that Google recommends you focus on.

<img src="https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format" alt="CrUX Dashboard Core Web Vitals overview" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/h8iCTgvmG4DS2zScvatc.png?auto=format&amp;w=1600 1600w" width="800" height="906" />

Use the Core Web Vitals page to understand how the origin is experienced by desktop and phone users. By default, the most recent month at the time you created the dashboard is selected. To change between older or newer monthly releases, use the **Month** filter at the top of the page.

Note that tablet is omitted from these charts by default, but if needed you could remove the **No Tablet** filter in the bar chart configuration, shown below.

<img src="https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format" alt="Editing the CrUX Dashboard to show tablets on the Core Web Vitals page" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/lD3eZ3LipJmBGmmkrUvG.png?auto=format&amp;w=1600 1600w" width="800" height="288" />

### Metric performance <a href="#metric-performance" class="w-headline-link">#</a>

After the Core Web Vitals page, you'll find standalone pages for all [metrics](https://developers.google.com/web/tools/chrome-user-experience-report/#metrics) in the CrUX dataset.

<img src="https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format" alt="CrUX Dashboard LCP page" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/AG2jdUtgsQzrxIUlLFyf.png?auto=format&amp;w=1600 1600w" width="800" height="598" />

Atop each page is the **Device** filter, which you can use to restrict the form factors included in the experience data. For example, you can drill down specifically into phone experiences. This setting persists across pages.

The primary visualizations on these pages are the monthly distributions of experiences categorized as "Good", "Needs Improvement", and "Poor". The color-coded legend below the chart indicates the range of experiences included in the category. For example, in the screenshot above, you can see the percent of "good" [Largest Contentful Paint](/lcp/#what-is-a-good-lcp-score) (LCP) experiences fluctuating and getting slightly worse in recent months.

The most recent month's percentages of "good" and "poor" experiences are shown above the chart along with an indicator of the percent difference from the previous month. For this origin, "good" LCP experiences fell by 3.2% to 56.04% month-over-month.

**Caution**: Due to a quirk with Data Studio, you may sometimes see `No Data` here. This is normal and due to the previous month's release not being available until the second Tuesday.

Additionally, for metrics like LCP and other Core Web Vitals that provide explicit percentile recommendations, you'll find the "P75" metric between the "good" and "poor" percentages. This value corresponds to the origin's 75th percentile of user experiences. In other words, 75% of experiences are better than this value. One thing to note is that this applies to the overall distribution across _all devices_ on the origin. Toggling specific devices with the **Device** filter will not recalculate the percentile.

## Boring technical caveats about percentiles

Be aware that the percentile metrics are based on the histogram data from [BigQuery](/chrome-ux-report-bigquery/), so the granularity will be coarse: 1000ms for LCP, 100ms for FID, and 0.05 for CLS. In other words, a P75 LCP of 3800ms indicates that the true 75th percentile is somewhere between 3800ms and 3900ms.

Additionally, the BigQuery dataset uses a technique called "bin spreading" in which densities of user experiences are intrinsically grouped into very coarse bins of decreasing granularity. This allows us to include minute densities in the tail of the distribution without having to exceed four digits of precision. For example, LCP values less than 3 seconds are grouped into bins 200ms wide. Between 3 and 10 seconds, bins are 500ms wide. Beyond 10 seconds, bins are 5000ms wide, etc. Rather than having bins of varying widths, bin spreading ensures that all bins are a constant 100ms wide (the greatest common divisor), and the distribution is linearly interpolated across each bin.

Corresponding P75 values in tools like PageSpeed Insights are not based on the public BigQuery dataset and are able to provide millisecond-precision values.

### User demographics <a href="#user-demographics" class="w-headline-link">#</a>

There are two [dimensions](https://developers.google.com/web/tools/chrome-user-experience-report/#dimensions) included on the user demographic pages: devices and effective connection types (ECTs). These pages illustrate the distribution of page views across the entire origin for users in each demographic.

The device distribution page shows you the breakdown of phone, desktop, and tablet users over time. Many origins tend to have little to no tablet data so you'll often see "0%" hanging off the edge of the chart.

<img src="https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format" alt="CrUX Dashboard device page" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/6PXh8MoQTWHnHXf8o1ZU.png?auto=format&amp;w=1600 1600w" width="800" height="603" />

Similarly, the ECT distribution page shows you the breakdown of 4G, 3G, 2G, slow 2G, and offline experiences.

**Key Term**: Effective connection types are considered _effective_ because they're based on bandwidth measurements on users' devices, and don't imply any particular technology used. For example, a desktop user on fast Wi-Fi may be labelled as 4G while a slower mobile connection might be labelled as 2G.

The distributions for these dimensions are calculated using segments of the [First Contentful Paint](/fcp/) (FCP) histogram data.

## FAQ <a href="#faq" class="w-headline-link">#</a>

### When would I use the CrUX Dashboard as opposed to other tools? <a href="#when-would-i-use-the-crux-dashboard-as-opposed-to-other-tools" class="w-headline-link">#</a>

The CrUX Dashboard is based on the same underlying data available on BigQuery, but you don't need to write a single line of SQL to extract the data and you don't ever have to worry about exceeding any free quotas. Setting up a dashboard is quick and easy, all of the visualizations are generated for you, and you have the control to share it with anyone you want.

### Are there any limitations to using the CrUX Dashboard? <a href="#are-there-any-limitations-to-using-the-crux-dashboard" class="w-headline-link">#</a>

Being based on BigQuery means that the CrUX Dashboard inherits all of its limitations as well. It is restricted to origin-level data at monthly granularity.

The CrUX Dashboard also trades away some of the versatility of the raw data on BigQuery for simplicity and convenience. For example, metric distributions are only given as "good", "needs improvement", and "poor", as opposed to the full histograms. The CrUX Dashboard also provides data at a global level, while the BigQuery dataset allows you to zoom in on particular countries.

### Where can I learn more about Data Studio? <a href="#where-can-i-learn-more-about-data-studio" class="w-headline-link">#</a>

Check out the [Data Studio features page](https://marketingplatform.google.com/about/data-studio/features/) for more info.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jun 22, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/chrome-ux-report-data-studio-dashboard/index.md)

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
