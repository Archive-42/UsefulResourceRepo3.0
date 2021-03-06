## <a href="#page-load-is-not-fast-enough-on-mobile-networks" class="w-toc__header--link">Page load is not fast enough on mobile networks</a>

- [How the Lighthouse page load speed audit fails](#how-the-lighthouse-page-load-speed-audit-fails)
- [How to improve your page's load time](#how-to-improve-your-page's-load-time)
- [How to improve your overall Performance score](#how-to-improve-your-overall-performance-score)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Page load is not fast enough on mobile networks

May 4, 2019 <span class="w-author__separator">•</span> Updated Jun 10, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

Many users of your page visit on a slow cellular network connection. Making your page load quickly on a mobile network helps to ensure a positive experience for your mobile users.

A fast page load on a mobile network is a baseline requirement for a site to be considered a Progressive Web App. See the [Core Progressive Web App checklist](/pwa-checklist/#core).

## How the Lighthouse page load speed audit fails <a href="#how-the-lighthouse-page-load-speed-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages that don't load fast enough on mobile:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Cg0UJ1Lykj672ygYYeXo.png?auto=format&amp;w=1600 1600w" width="800" height="98" /></figure>Two main metrics affect how users perceive load time:

- [First Meaningful Paint (FMP)](/first-meaningful-paint), which measures when the primary content of the page appears visually complete
- [Time to Interactive (TTI)](/interactive), which measures when the page is fully interactive

For example, if a page appears visually complete after 1 second, but the user can't interact with it for 10 seconds, users will likely perceive the page load time as 10 seconds.

Lighthouse computes what the TTI would be on a slow 4G network connection. If the time to interactive is more than 10 seconds, the audit fails.

In the Lighthouse report UI the full PWA badge is given when you pass all of the audits in all of the PWA subcategories (**Fast and reliable**, **Installable**, and **PWA optimized**).

## How to improve your page's load time <a href="#how-to-improve-your-page&#39;s-load-time" class="w-headline-link">#</a>

## How to improve your overall Performance score <a href="#how-to-improve-your-overall-performance-score" class="w-headline-link">#</a>

Unless you have a specific reason for focusing on a particular metric, it's usually better to focus on improving your overall Performance score.

Use the **Opportunities** section of your Lighthouse report to determine which improvements will have the most value for your page. The more significant the opportunity, the greater the effect it will have on your Performance score. For example, the Lighthouse screenshot below shows that [eliminating render-blocking resources](/render-blocking-resources) will yield the biggest improvement:

<figure><img src="/images/shared/opportunities.png" class="w-screenshot w-screenshot--filled" /></figure>See the [Performance audits landing page](/lighthouse-performance) to learn how to address the opportunities identified in your Lighthouse report.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Page load is not fast enough on mobile networks** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/load-fast-enough-for-pwa.js)
- [Baseline Progressive Web App Checklist](https://developers.google.com/web/progressive-web-apps/checklist#baseline)
- [Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/)
- [Get Started With Analyzing Runtime Performance](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/)
- [Record load performance](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#record-load)
- [Optimizing Content Efficiency](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/)
- [Rendering Performance](https://developers.google.com/web/fundamentals/performance/rendering/)

<span class="w-mr--sm">Last updated: Jun 10, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/load-fast-enough-for-pwa/index.md)

<a href="/lighthouse-pwa" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
