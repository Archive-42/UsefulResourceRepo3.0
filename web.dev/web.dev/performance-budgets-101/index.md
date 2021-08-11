<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#performance-budgets-101" class="w-toc__header--link">Performance budgets 101</a>
------------------------------------------------------------------------------------------

-   [Definition](#definition)
-   [Choose metrics](#choose-metrics)
-   [Quantity-based metrics ⚖️](#quantity-based-metrics)
-   [Milestone timings ⏱️](#milestone-timings)
-   [Rule-based metrics 💯](#rule-based-metrics)
-   [Establish a baseline](#establish-a-baseline)
-   [Examples of budgets](#examples-of-budgets)
-   [Add performance budgets to your build process](#add-performance-budgets-to-your-build-process)
-   [Track performance](#track-performance)
-   [Wrap up](#wrap-up)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Performance budgets 101
=======================

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

-   <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
-   <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

Performance is an important part of the user experience and it [affects business metrics](https://wpostats.com/). It's tempting to think that if you are a good developer you'll end up with a performant site, but the truth is that good performance is rarely a side effect. As with most other things—to reach a goal you have to define it clearly. Start the journey by setting a **performance budget**.

Definition <a href="#definition" class="w-headline-link">#</a>
--------------------------------------------------------------

A performance budget is a set of limits imposed on metrics that affect site performance. This could be the total size of a page, the time it takes to load on a mobile network, or even the number of HTTP requests that are sent. Defining a budget helps get the web performance conversation started. It serves as a point of reference for making decisions about design, technology, and adding features.

Having a budget enables designers to think about the effects of high-resolution images and the number of web fonts they pick. It also helps developers compare different approaches to a problem and evaluate frameworks and libraries based on their size and [parsing cost](https://medium.com/@addyosmani/the-cost-of-javascript-in-2018-7d8950fbb5d4).

Choose metrics <a href="#choose-metrics" class="w-headline-link">#</a>
----------------------------------------------------------------------

### Quantity-based metrics ⚖️ <a href="#quantity-based-metrics" class="w-headline-link">#</a>

These metrics are useful in the early stages of development because they highlight the impact of including heavy images and scripts. They are also easy to communicate to both designers and developers.

We've already mentioned a few things you can include in a performance budget such as page weight and the number of HTTP requests, but you can split these up into more granular limits like:

-   Maximum size of images
-   Maximum number of web fonts
-   Maximum size of scripts, including frameworks
-   Total number of external resources, such as third-party scripts

However, these numbers don't tell you much about the user experience. Two pages with the same number of requests or same weight can render differently depending on the order in which resources get requested. If a [critical resource](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/) like a hero image or a stylesheet on one of the pages is loaded late in the process, the users will wait longer to see something useful and perceive the page as slower. If on the other page the most important parts load quickly, they may not even notice if the rest of the page doesn't.

<figure><img src="https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format" sizes="(min-width: 611px) 611px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/U0QhA82KFyED4r1y3tAq.png?auto=format&amp;w=1222 1222w" width="611" height="300" /></figure>This is why it's important to keep track of another type of metric.

### Milestone timings ⏱️ <a href="#milestone-timings" class="w-headline-link">#</a>

Milestone timings mark events that happen during page load, such as [DOMContentLoaded](https://developer.mozilla.org/en-US/docs/Web/Events/DOMContentLoaded) or [load](https://developer.mozilla.org/en-US/docs/Web/Events/load) event. The most useful timings are [user-centric performance metrics](https://developers.google.com/web/fundamentals/performance/user-centric-performance-metrics) that tell you something about the experience of loading a page. These metrics are available through [browser APIs](https://developers.google.com/web/fundamentals/performance/user-centric-performance-metrics#measuring_these_metrics_on_real_users_devices) and as part of [Lighthouse](https://developers.google.com/web/tools/lighthouse/) reports.

[First Contentful Paint (FCP)](/first-contentful-paint) measures when the browser displays the first bit of content from the DOM, like text or images.

[Time to Interactive (TTI)](/interactive) measures how long it takes for a page to become fully interactive and reliably respond to user input. It's a very important metric to track if you expect any kind of user interaction on the page like clicking links, buttons, typing or using form elements.

### Rule-based metrics 💯 <a href="#rule-based-metrics" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) and [WebPageTest](https://www.webpagetest.org/) calculate [performance scores](https://developers.google.com/web/tools/lighthouse/scoring#perf-scoring) based on general best practice rules, that you can use as guidelines. As a bonus, Lighthouse also offers you hints for simple optimizations.

You'll get the best results if you keep track of a combination of quantity-based and user-centric performance metrics. Focus on asset sizes in the early phases of a project and start tracking FCP and TTI as soon as possible.

Establish a baseline <a href="#establish-a-baseline" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

The only way to really know what works best for your site is to try it—research and then test your findings. Analyze the competition to see how you stack up. 🕵️

If you don't have time for that, here are good default numbers to get you started:

-   Under **5 s** Time to Interactive
-   Under **170 KB** of [critical-path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/) resources (compressed/minified)

These [numbers](https://infrequently.org/2017/10/can-you-afford-it-real-world-web-performance-budgets/) are calculated based on real-world baseline devices and **3G network speed**. [Over half of the internet traffic](https://www.statista.com/statistics/277125/share-of-website-traffic-coming-from-mobile-devices/) today happens on mobile networks, so you should use 3G network speed as a starting point.

### Examples of budgets <a href="#examples-of-budgets" class="w-headline-link">#</a>

You should have a budget in place for different types of pages on your site since the content will vary. For example:

-   Our product page must ship less than 170 KB of JavaScript on mobile
-   Our search page must include less than 2 MB of images on desktop
-   Our home page must load and get interactive in &lt; 5 s on slow 3G on a Moto G4 phone
-   Our blog must score &gt; 80 on Lighthouse performance audits

Add performance budgets to your build process <a href="#add-performance-budgets-to-your-build-process" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------------

<img src="https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format" alt="Webpack, bundlesize and Lighthouse logos" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/YKJcgI9Yd8qEZM0nzPuv.png?auto=format&amp;w=1600 1600w" width="800" height="267" />

Choosing a tool for this will depend a lot on the scale of your project and resources that you can dedicate to the task. There are a few open-source tools that can help you add budgeting to your build process:

-   [Webpack performance features](https://webpack.js.org/configuration/performance/)
-   [bundlesize](https://github.com/siddharthkp/bundlesize)
-   [Lighthouse CI](https://github.com/GoogleChrome/lighthouse-ci)

If something goes over a defined threshold, you can either:

-   Optimize an existing feature or asset 🛠️
-   Remove an existing feature or asset 🗑️
-   Not add the new feature or asset ✋⛔

Track performance <a href="#track-performance" class="w-headline-link">#</a>
----------------------------------------------------------------------------

Making sure your site is fast enough means you have to keep measuring after the initial launch. Monitoring these metrics over time and [getting data from real users](https://developers.google.com/web/fundamentals/performance/navigation-and-resource-timing/) will show you how changes in performance impact key business metrics.

Wrap up <a href="#wrap-up" class="w-headline-link">#</a>
--------------------------------------------------------

The purpose of a performance budget is to make sure you focus on performance throughout a project and setting it early will help prevent backtracking later. It should be the point of reference for helping you figure out what to include on your website. The main idea is to set goals so that you can better balance performance without harming functionality or user experience.🎯

The next guide will walk you through defining your first performance budget in a few simple steps.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/performance-budgets-101/index.md)

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