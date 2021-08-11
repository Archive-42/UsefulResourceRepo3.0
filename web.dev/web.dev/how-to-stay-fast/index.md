<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#how-to-stay-fast" class="w-toc__header--link">How to stay fast?</a>

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# How to stay fast?

May 1, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Bojan Pavic" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/bojanpavic/)

<a href="/authors/bojanpavic/" class="w-author__name-link">Bojan Pavic</a>

- <a href="https://github.com/bojanpavic" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Chris Anstey" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/ansteychris/)

<a href="/authors/ansteychris/" class="w-author__name-link">Chris Anstey</a>

- <a href="https://github.com/ansteychris" class="w-author__link">GitHub</a>

Brands that optimize speed will often find they regress quickly. This is because website performance is a lot like getting fit: it's not enough to make a one time effort; you have to change your lifestyle.

[Internal Google study](https://www.youtube.com/watch?v=YJGCZCaIZkQ) has found that 40% of brands regress on web performance after 6 months.

Performance budgets are one way to address this. A performance budget is a set of limits on metrics that affect site performance. The concept is similar to a financial budget: you set a limit and make sure you stay within it. In general, a good performance budget combines different types of metrics; so, for example, the performance budget for a product page might look as follows:

Time To Interactive on slow 3G

Less than

5 seconds

First Contentful Paint on slow 3G

Less than

2 seconds

Lighthouse performance score

Greater than

80

Total JavaScript size

Less than

170 kb

Example performance budget.

Once set, a performance budget has to be enforced, which means for example incorporating the budget into your build process and reporting. Tools like Lighthouse can be included in your continuous integration, and you can write tests that fail a build if key metrics drop below a set threshold. Additionally, regular reporting through dashboards or summary reports can help with visibility and accountability. [Pinterest](https://www.youtube.com/watch?v=Xryhxi45Q5M) are one example of a business that have implemented performance budgets to make sure their fast experience stays fast, while brands like [Experian](https://www.thinkwithgoogle.com/intl/en-gb/success-stories/uk-success-stories/how-mobile-first-mindset-helped-experian-slash-page-load-times/) are now using site speed as a key metric in their monthly executive KPI reports.

You can find more details on performance budgets [here](/performance-budgets-101). A guide that describes how to further instill performance culture and make speed metrics visible and tangible for all stakeholders can be found [here](/how-to-report-metrics/).

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: May 1, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/how-to-stay-fast/index.md)

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
