





<a href="#does-not-provide-fallback-content-when-javascript-is-not-available" class="w-toc__header--link">Does not provide fallback content when JavaScript is not available</a>
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [How the Lighthouse fallback content audit fails](#how-the-lighthouse-fallback-content-audit-fails)
-   [How to ensure your page has content without JavaScript](#how-to-ensure-your-page-has-content-without-javascript)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Does not provide fallback content when JavaScript is not available
==================================================================

May 4, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

[Progressive Enhancement](https://en.wikipedia.org/wiki/Progressive_enhancement) is a web development strategy that ensures that your site is accessible to the largest possible audience. The core principle is that basic content and page functionality should rely on only the most fundamental web technologies. Enhanced experiences, such as sophisticated styling using CSS or interactivity using JavaScript, can be layered on top for browsers that support those technologies. But basic content and page functionality should not rely on CSS or JavaScript.

How the Lighthouse fallback content audit fails <a href="#how-the-lighthouse-fallback-content-audit-fails" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages that don't contain *some* content when JavaScript is unavailable:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/durRW9Bh687rjFAIgF7P.png?auto=format&amp;w=1600 1600w" width="800" height="120" /></figure>Lighthouse disables JavaScript on the page and then inspects the page's HTML. If the HTML is empty, the audit fails.

In the Lighthouse report UI the full PWA badge is given when you pass all of the audits in all of the PWA subcategories (**Fast and reliable**, **Installable**, and **PWA optimized**).

How to ensure your page has content without JavaScript <a href="#how-to-ensure-your-page-has-content-without-javascript" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------------------------------

Progressive enhancement is a large and contentious topic. One camp says that, in order to adhere to the strategy of progressive enhancement, pages should be layered so that basic content and page functionality only require HTML. See Smashing Magazine's [Progressive Enhancement: What It Is, And How To Use It](https://www.smashingmagazine.com/2009/04/progressive-enhancement-what-it-is-and-how-to-use-it/) for an example of this approach.

Another camp believes that this strict approach is unfeasible or unnecessary for many modern, large-scale web applications and suggests using inline critical-path CSS in the document `<head>` for absolutely critical page styles.

Given these considerations, this Lighthouse audit performs a simple check to ensure that your page isn't blank when JavaScript is disabled. How strictly your app adheres to progressive enhancement is a topic of debate, but there's widespread agreement that all pages should display at least *some* information when JavaScript is disabled, even if the content is just an alert to the user that JavaScript is required to use the page.

For pages that absolutely must rely on JavaScript, one approach is to use a [`<noscript>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/noscript) element to alert the user that JavaScript is required for the page. This is better than a blank page because the blank page leaves users uncertain about whether there's a problem with the page, their browsers, or their computers.

To see how your site looks and performs when JavaScript is disabled, use Chrome DevTools' [Disable JavaScript](https://developers.google.com/web/tools/chrome-devtools/javascript/disable) feature.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **Does not provide fallback content when JavaScript is not available** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/without-javascript.js)
-   [Progressive Enhancement: What It Is, And How To Use It](https://www.smashingmagazine.com/2009/04/progressive-enhancement-what-it-is-and-how-to-use-it/)
-   [Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/)
-   [Disable JavaScript With Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/javascript/disable)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/without-javascript/index.md)

<a href="/lighthouse-pwa" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
