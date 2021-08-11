## <a href="#current-page-does-not-respond-with-a-200-when-offline" class="w-toc__header--link">Current page does not respond with a 200 when offline</a>

- [How the Lighthouse offline audit fails](#how-the-lighthouse-offline-audit-fails)
- [How to make your PWA work offline](#how-to-make-your-pwa-work-offline)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Current page does not respond with a 200 when offline

May 4, 2019 <span class="w-author__separator">•</span> Updated Jun 4, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

The [Core Progressive Web App checklist](/pwa-checklist/#core) says that a PWA should provide a custom offline page. The [Optimial Progressive Web App checklist](/pwa-checklist/#optimal) says that a PWA should provide an offline experience where the PWA works the same offline as it does online (wherever network connectivity isn't strictly required).

Learn more in the [What is network reliability and how do you measure it?](/network-connections-unreliable/) post.

## How the Lighthouse offline audit fails <a href="#how-the-lighthouse-offline-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages that don't respond with an [HTTP 200 response](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#Successful_responses) when offline:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kpkiosw2MD8u8wfq4AJU.png?auto=format&amp;w=1600 1600w" width="800" height="95" /></figure>Lighthouse emulates an offline connection using the [Chrome Remote Debugging Protocol](https://github.com/ChromeDevTools/devtools-protocol) and then attempts to retrieve the page using [`XMLHttpRequest`](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest).

In the Lighthouse report UI the full PWA badge is given when you pass all of the audits in all of the PWA subcategories (**Fast and reliable**, **Installable**, and **PWA optimized**).

## How to make your PWA work offline <a href="#how-to-make-your-pwa-work-offline" class="w-headline-link">#</a>

**Success**: [Workbox](/workbox) is the recommended approach for adding service workers to websites because it automates a lot of boilerplate, makes it easier to follow best practices, and prevents subtle bugs that are common when using the low-level `ServiceWorker` API directly.

1.  Add a [service worker](https://developers.google.com/web/fundamentals/primers/service-workers) to your app.
2.  Use the service worker to cache files locally.
3.  When offline, use the service worker as a network proxy to return the locally cached version of the file.

**Try it**! Learn how to add a service worker to your app with the [Working with service workers](/codelab-service-workers) codelab.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [What is network reliability and how do you measure it?](/network-connections-unreliable/)
- [Service Workers: an Introduction](https://developers.google.com/web/fundamentals/primers/service-workers)

<span class="w-mr--sm">Last updated: Jun 4, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/works-offline/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-service-workers/" class="w-callout__link w-callout__link--codelab">Working with service workers</a>

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
