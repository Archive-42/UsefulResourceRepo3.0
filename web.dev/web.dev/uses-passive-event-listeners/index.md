<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#use-passive-listeners-to-improve-scrolling-performance" class="w-toc__header--link">Use passive listeners to improve scrolling performance</a>
--------------------------------------------------------------------------------------------------------------------------------------------------------

-   [Browser compatibility](#browser-compatibility)
-   [How the Lighthouse passive event listener audit fails](#how-the-lighthouse-passive-event-listener-audit-fails)
-   [How to make event listeners passive to improve scrolling performance](#how-to-make-event-listeners-passive-to-improve-scrolling-performance)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Use passive listeners to improve scrolling performance
======================================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Aug 28, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-best-practices" class="w-post-signpost__link">Best Practices audits</a>

Touch and wheel event listeners are useful for tracking user interactions and creating custom scrolling experiences, but they can also delay page scrolling. Currently, browsers can't know if an event listener will prevent scrolling, so they always wait for the listener to finish executing before scrolling the page. Passive event listeners solve this problem by letting you indicate that an event listener will never prevent scrolling.

Browser compatibility <a href="#browser-compatibility" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

Most browsers support passive event listeners. See [Browser compatibility](https://developer.mozilla.org/docs/Web/API/EventTarget/addEventListener#Browser_compatibility)

How the Lighthouse passive event listener audit fails <a href="#how-the-lighthouse-passive-event-listener-audit-fails" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags event listeners that may delay page scrolling:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/a59Rk7aCUDvyKNqqoYRJ.png?auto=format&amp;w=1600 1600w" width="800" height="213" /></figure>Lighthouse uses the following process to identify event listeners that may affect scrolling performance:

1.  Collect all event listeners on the page.
2.  Filter out non-touch and non-wheel listeners.
3.  Filter out listeners that call `preventDefault()`.
4.  Filter out listeners that are from a different host than the page.

Lighthouse filters out listeners from different hosts because you probably don't have control over these scripts. There may be third-party scripts that are harming your page's scrolling performance, but these aren't listed in your Lighthouse report.

Each Best Practices audit is weighted equally in the Lighthouse Best Practices Score. Learn more in [The Best Practices score](https://developers.google.com/web/tools/lighthouse/v3/scoring#best-practices).

How to make event listeners passive to improve scrolling performance <a href="#how-to-make-event-listeners-passive-to-improve-scrolling-performance" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Add a `passive` flag to every event listener that Lighthouse identified.

If you're only supporting browsers that have passive event listener support, just add the flag. For example:

    document.addEventListener('touchstart', onTouchStart, {passive: true});

If you're supporting [older browsers that don't support passive event listeners](https://developer.mozilla.org/en-US/docs/Web/API/EventTarget/addEventListener#Browser_compatibility), you'll need to use feature detection or a polyfill. See the [Feature Detection](https://github.com/WICG/EventListenerOptions/blob/gh-pages/explainer.md#feature-detection) section of the WICG [Passive event listeners](https://github.com/WICG/EventListenerOptions/blob/gh-pages/explainer.md) explainer document for more information.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **Does not use passive listeners to improve scrolling performance** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/dobetterweb/uses-passive-event-listeners.js)
-   [Improving Scrolling Performance with Passive Event Listeners](https://developers.google.com/web/updates/2016/06/passive-event-listeners)
-   [Passive event listeners explainer](https://github.com/WICG/EventListenerOptions/blob/gh-pages/explainer.md)
-   [EventTarget.addEventListener()](https://developer.mozilla.org/docs/Web/API/EventTarget/addEventListener)

<span class="w-mr--sm">Last updated: Aug 28, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-best-practices/uses-passive-event-listeners/index.md)

<a href="/lighthouse-best-practices" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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