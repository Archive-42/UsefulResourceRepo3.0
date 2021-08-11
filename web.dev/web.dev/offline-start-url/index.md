## <a href="#lesscodegreaterstart_urllesscodegreater-does-not-respond-with-a-200-when-offline" class="w-toc__header--link"><code>start_url</code> does not respond with a 200 when offline</a>

- [How the Lighthouse start_url audit fails](#how-the-lighthouse-start_url-audit-fails)
- [How to ensure your page is available offline](#how-to-ensure-your-page-is-available-offline)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# `start_url` does not respond with a 200 when offline

May 4, 2019 <span class="w-author__separator">•</span> Updated Apr 29, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

The [manifest](/add-manifest) for a [Progressive Web App](/what-are-pwas/) (PWA) should include a `start_url`, which indicates the URL to be loaded when the user launches the app.

If the browser doesn't receive an [HTTP 200 response](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#Successful_responses) when accessing an app from the `start_url`, either the `start_url` isn't correct, or the page isn't accessible offline. This causes problems for users who have installed the app to their devices.

## How the Lighthouse `start_url` audit fails <a href="#how-the-lighthouse-start_url-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags web apps whose start URL doesn't respond with a 200 when offline:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZR8gYzKNpBkrXEgQQnbl.png?auto=format&amp;w=1600 1600w" width="800" height="76" /></figure>In the Lighthouse report UI the full PWA badge is given when you pass all of the audits in all of the PWA subcategories (**Fast and reliable**, **Installable**, and **PWA optimized**).

## How to ensure your page is available offline <a href="#how-to-ensure-your-page-is-available-offline" class="w-headline-link">#</a>

**Success**: [Workbox](/workbox) is the recommended approach for adding service workers to websites because it automates a lot of boilerplate, makes it easier to follow best practices, and prevents subtle bugs that are common when using the low-level `ServiceWorker` API directly.

1.  If you don't already have one, [add a web app manifest](/add-manifest/).
2.  Check that the `start_url` in your manifest is correct.
3.  Add a service worker to your app.
4.  Use the service worker to cache files locally.
5.  When offline, use the service worker as a network proxy to return the locally cached version of the file.

See the [Current page does not respond with a 200 when offline](/works-offline) guide for more information.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [What is network reliability and how do you measure it?](/network-connections-unreliable/)
- [Add a web app manifest](/add-manifest/)
- [Workbox: Your high-level service worker toolkit](/workbox/)

<span class="w-mr--sm">Last updated: Apr 29, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/offline-start-url/index.md)

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
