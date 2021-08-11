<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#your-first-performance-budget" class="w-toc__header--link">Your first performance budget</a>
------------------------------------------------------------------------------------------------------

-   [Preliminary analysis](#preliminary-analysis)
-   [Competitive analysis](#competitive-analysis)
-   [Budget for timing milestones](#budget-for-timing-milestones)
-   [Combine different metrics](#combine-different-metrics)
-   [Budget for quantity-based metrics](#budget-for-quantity-based-metrics)
-   [Budget for rule-based metrics](#budget-for-rule-based-metrics)
-   [Prioritize](#prioritize)
-   [Next steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Your first performance budget
=============================

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

-   <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
-   <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

When you set a personal, business or family budget, you are setting a limit to your spending and making sure you stay within it. [Performance budgets](/performance-budgets-101) work in the same way, but for metrics that affect website performance.

With a performance budget established and enforced you can be sure that your site will render as quickly as possible. This will provide a better experience for your visitors and positively impact business metrics.

Here's how to define your first performance budget in a few simple steps.

Preliminary analysis <a href="#preliminary-analysis" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

If you are trying to improve the performance of an existing site, start by identifying the most important pages. For example, these could be pages that have the highest amount of user traffic or a product landing page.

After you identify your key pages, it's time to analyze them. First, we'll focus on the timing milestones that best measure the user experience.

Under the Audits panel in Chrome DevTools, you'll find [Lighthouse](https://developers.google.com/web/tools/lighthouse/). Run audits on each page in a [Guest window](https://support.google.com/chrome/answer/6130773?co=GENIE.Platform%3DDesktop&hl=en) to record these two times:

-   [First Contentful Paint (FCP)](/first-contentful-paint)
-   [Time to Interactive (TTI)](/interactive)

Using a Guest window gives you a clean testing environment without any Chrome extensions that could interfere with the audit.

<img src="https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format" alt="Lighthouse panel in Chrome DevTools" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/VUtkCadH9vjnKSzGzd0S.png?auto=format&amp;w=1600 1600w" width="800" height="637" />

Let's take a highly specialized search engine, doggos.io, as an example. Doggos.io aims to index all dog-related things on the internet, and its most important pages are the home and results pages. Here are the FCP and TTI numbers measured for the site on desktop and mobile.

Desktop

FCP

TTI

Homepage

1,680 ms

5,550 ms

Results page

2,060 ms

6,690 ms

Desktop analysis of doggos.io

Mobile

FCP

TTI

Homepage

1,800 ms

6,150 ms

Results page

1,100 ms

7,870 ms

Mobile analysis of doggos.io

Competitive analysis <a href="#competitive-analysis" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

Once you've analyzed your own site, it's time to analyze your competitors' sites. Comparing results from websites similar to yours is a great way to figure out a performance budget. Whether you are working on an established project or starting from scratch, this is an important step. You get competitive advantage when you are faster than your competitors.

If you are not sure which sites to look at, here are a few tools to try:

1.  Google search's "related:" keyword
2.  [Alexa's similar sites](https://www.alexa.com/find-similar-sites) feature
3.  [SimilarWeb](https://www.similarweb.com)

<img src="https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format" alt="Screenshot of Google search with the related keyword" class="w-screenshot" sizes="(min-width: 775px) 775px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/EzpGvSgVJYC2y3rsnHRk.png?auto=format&amp;w=1550 1550w" width="775" height="336" />

For a realistic picture, try to **find 10 or so competitors**.

### Budget for timing milestones <a href="#budget-for-timing-milestones" class="w-headline-link">#</a>

Our niche search engine in this example has a handful of competitors and we'll focus on optimizing the homepage for mobile devices. Over [half of the internet traffic](https://www.statista.com/statistics/277125/share-of-website-traffic-coming-from-mobile-devices/) today happens on mobile networks and using mobile numbers as default will benefit not only your mobile users, but your desktop users as well.

Create a chart with FCP and TTI times for all the similar websites and highlight the fastest in the bunch. A chart like this one gives you a clearer picture of how your website is doing compared to the competition.

Site/Homepage

FCP

TTI

goggles.com

**880 ms**

**3,150 ms**

doggos.io

1,800 ms

6,500 ms

quackquackgo.com

2,680 ms

4,740 ms

ding.xyz

2,420 ms

7,040 ms

Competitive analysis of doggos.io on 3G network

<figure><img src="https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format" alt="Doggos.io seems to be doing okay on the FCP metric but seriously lagging behind in TTI" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/Mfzr0dmMxHij9KrJraHD.jpg?auto=format&amp;w=1600 1600w" width="800" height="600" /><figcaption>Doggos.io seems to be doing okay on the FCP metric but seriously lagging behind in TTI</figcaption></figure>There's room for improvement and a good guideline for that is the [20% rule](https://www.smashingmagazine.com/2015/09/why-performance-matters-the-perception-of-time/#the-need-for-performance-optimization-the-20-rule). Research states that users recognize a difference in response times when it's greater than 20%. This means that if you want to be noticeably better than the best comparable site, you have to **be at least 20% faster**.

Measure

Current time

Budget (20% faster than competition)

FCP

1,800 ms

704 ms

TTI

6,500 ms

2,520 ms

Performance budget that would get doggos.com ahead of the competition

If you are trying to optimize an existing site that goal may seem impossible to reach. This is not a sign for you to give up. Start with small steps and set a budget at 20% faster than your current speed. Keep optimizing from there.

For doggos.io, a revised budget could look like this.

Measure

Current time

Initial budget (20% faster than the current time)

Long-term goal (20% faster than competition)

FCP

1,800 ms

1,440 ms

704 ms

TTI

6,500 ms

5,200 ms

2,520 ms

Revised doggos.io performance budget

Combine different metrics <a href="#combine-different-metrics" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

A solid performance budget combines different types of metrics. We've already defined the budget for milestone timings and now we'll add two more to the mix:

-   quantity-based metrics
-   rule-based metrics

### Budget for quantity-based metrics <a href="#budget-for-quantity-based-metrics" class="w-headline-link">#</a>

Whatever total page weight number you come up with, try to **deliver** under 170 KB of **[critical-path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/) resources** (compressed/minified). This guarantees your website will be fast even on [inexpensive devices and slow 3G](https://infrequently.org/2017/10/can-you-afford-it-real-world-web-performance-budgets/).

You can have a bigger budget for the desktop experience, but don't go wild. The median page weight on both desktop and mobile is over 1MB according to the [HTTP Archive](https://httparchive.org/reports/page-weight) data for the last year. To get a performant website you have to aim well below these median numbers.

Here are a few examples based on TTI budgets:

<table><thead><tr class="header"><th>Network</th><th>Device</th><th>JS</th><th>Images</th><th>CSS</th><th>HTML</th><th>Fonts</th><th>Total</th><th>Time to Interactive budget</th></tr></thead><tbody><tr class="odd"><td>Slow 3G</td><td>Moto G4</td><td>100</td><td>30</td><td>10</td><td>10</td><td>20</td><td>~170 KB</td><td>5s</td></tr><tr class="even"><td>Slow 4G</td><td>Moto G4</td><td>200</td><td>50</td><td>35</td><td>30</td><td>30</td><td>~345 KB</td><td>3s</td></tr><tr class="odd"><td>WiFi</td><td>Desktop</td><td>300</td><td>250</td><td>50</td><td>50</td><td>100</td><td>~750 KB</td><td>2s</td></tr></tbody></table>

The recommended sizes are for the critical-path resources.

Defining a budget based on quantity metrics is a tricky business. An e-commerce website with loads of product photos is very different from a news portal which is mostly text. If you have ads or analytics on your site, that increases the amount of JavaScript you're shipping.

Use the table above as a starting point and adjust based on the type of content you are working with. Define what your pages will include, review your research and take an educated guess for individual asset sizes. For example, if you are building a website with a lot of images, put stricter limits to JS size.

Once you have a working website, check how you are doing on user-centric performance metrics and adjust your budget.

### Budget for rule-based metrics <a href="#budget-for-rule-based-metrics" class="w-headline-link">#</a>

Very effective rule-based metrics are [Lighthouse](https://developers.google.com/web/tools/lighthouse/) scores. Lighthouse grades your app in 5 categories and one of those is performance. Performance scores are calculated based on [5 different metrics](https://developers.google.com/web/tools/lighthouse/scoring#perf-audits), including First Contentful Paint and Time to Interactive.

When you try to build a great site, **set Lighthouse performance score budget to at least 85 (out of 100)**. Use [Lighthouse CI](https://github.com/ebidel/lighthouse-ci) to enforce it on pull-requests.

Prioritize <a href="#prioritize" class="w-headline-link">#</a>
--------------------------------------------------------------

Ask yourself what level of interaction you expect on your site. If it's a news website, users' primary goal is to read content so you should focus on rendering quickly and keeping FCP low. Doggos.com visitors want to click on relevant links as soon as possible, so the top priority is low TTI.

Find out exactly what part of your audience browses on desktop vs. on mobile devices and prioritize accordingly. One way to figure this out is to check what your audience is doing on competitors' websites, through the [Chrome User Experience report](https://developers.google.com/web/updates/2018/08/chrome-ux-report-dashboard) dashboard.

<figure><img src="https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format" alt="Device distribution data from Chrome User Experience report" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/ycZwOrFNzjdjquriM9rJ.png?auto=format&amp;w=1600 1600w" width="800" height="530" /><figcaption>Device distribution data from Chrome User Experience report</figcaption></figure>Next steps <a href="#next-steps" class="w-headline-link">#</a>
--------------------------------------------------------------

Make sure your performance budget is enforced throughout the project and incorporate it into your build process.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/your-first-performance-budget/index.md)

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
