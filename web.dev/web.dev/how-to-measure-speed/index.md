<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#how-to-measure-speed" class="w-toc__header--link">How to measure speed?</a>

- [Lab data vs Field data](#lab-data-vs-field-data)
- [Tools](#tools)
- [Lab data](#lab-data)
- [Field data](#field-data)
- [Other tools](#other-tools)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# How to measure speed?

May 1, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Bojan Pavic" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/vxFF9sBge4qdpMqaKC0Z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/bojanpavic/)

<a href="/authors/bojanpavic/" class="w-author__name-link">Bojan Pavic</a>

- <a href="https://github.com/bojanpavic" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Chris Anstey" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/n9o3c8Qxz0uUprZnlsRk.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/ansteychris/)

<a href="/authors/ansteychris/" class="w-author__name-link">Chris Anstey</a>

- <a href="https://github.com/ansteychris" class="w-author__link">GitHub</a>

Real-world performance is highly variable due to differences in users' devices, network connections, and other factors. For example, if you load your website using a cable network connection in your office and compare it against the load using WiFi in a coffee shop, the experiences are likely to be very different. There are many tools on the market that can help you collect lab or field data to assess page performance.

## Lab data vs Field data <a href="#lab-data-vs-field-data" class="w-headline-link">#</a>

<img src="https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format" alt="Speed tools graphics" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/6OMEfvIKRuDWWSiVDto4.png?auto=format&amp;w=1600 1600w" width="800" height="232" />

**Lab data** is performance data collected within a controlled environment with predefined device and network settings, while **Field data** is performance data collected from real page loads experienced by your users in the wild. Each type has its own strengths and limitations.

**Lab data** offers reproducible results and a debugging environment, but might not capture real-world bottlenecks and cannot correlate against real-world page KPIs. With lab data, you need to understand your users' typical devices and networks and appropriately mirror those conditions when you test performance. Have in mind that even in areas with 4G, users may still experience slower or intermittent connections when in elevators, while commuting, or in comparable environments.

**Field data** (also called Real User Monitoring or RUM) captures true real-world user experience and enables correlation to business KPIs, but has a restricted set of metrics and limited debugging capabilities.

## Tools <a href="#tools" class="w-headline-link">#</a>

### Lab data <a href="#lab-data" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) takes a URL and runs a series of audits against the page, generating a report on how well the page did. There are multiple ways to run Lighthouse, including an option to easily audit a page from within Chrome DevTools.

### Field data <a href="#field-data" class="w-headline-link">#</a>

[Chrome User Experience Report (CrUX)](https://developers.google.com/web/tools/chrome-user-experience-report/) provides metrics showing how real-world Chrome users experience popular destinations on the web.

### Other tools <a href="#other-tools" class="w-headline-link">#</a>

[PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/) provides both lab and field data about a page. It uses Lighthouse to collect and analyze lab data about the page, while real-world field data is based on the Chrome User Experience Report dataset.

[Chrome Developer Tools](https://developers.google.com/web/tools/chrome-devtools/) is a set of web developer tools built directly into the Google Chrome browser. It allows you to profile the runtime of a page, as well as identify and debug performance bottlenecks.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: May 1, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/how-to-measure-speed/index.md)

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
