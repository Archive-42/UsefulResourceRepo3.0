





<a href="#site-works-cross-browser" class="w-toc__header--link">Site works cross-browser</a>
--------------------------------------------------------------------------------------------

-   [Recommendations](#recommendations)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Site works cross-browser
========================

May 4, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

To reach the most users, sites should work on every major browser.

Recommendations <a href="#recommendations" class="w-headline-link">#</a>
------------------------------------------------------------------------

Test your site in Chrome, Edge, Firefox, and Safari, and fix any issues that appear in each browser.

If your page is a [Progressive Web App](/discover-installable), consider using [Workbox](https://developers.google.com/web/tools/workbox), a high-level [service worker](/service-workers-cache-storage) toolkit. Workbox is developed against a cross-browser test suite, and when possible, automatically falls back to alternative implementations of features that are missing from certain browsers:

-   The [`workbox-broadcast-cache-update`](https://developers.google.com/web/tools/workbox/modules/workbox-broadcast-cache-update) module uses the [Broadcast Channel API](https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API) if possible and falls back to a [`postMessage()`](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) implementation.
-   The [`workbox-background-sync`](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) module uses the [Background Sync API](https://developers.google.com/web/tools/workbox/modules/workbox-background-sync) if possible and falls back to retrying queued events each time the service worker starts up.

Learn more in [Workbox: your high-level service worker toolkit](/workbox).

In the Lighthouse report UI the full PWA badge is given when you pass all of the audits in all of the PWA subcategories (**Fast and reliable**, **Installable**, and **PWA optimized**).

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

[Source code for **Site works cross-browser** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/manual/pwa-cross-browser.js)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/pwa-cross-browser/index.md)

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
