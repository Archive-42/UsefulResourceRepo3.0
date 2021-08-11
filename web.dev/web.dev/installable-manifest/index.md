<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#web-app-manifest-does-not-meet-the-installability-requirements" class="w-toc__header--link">Web app manifest does not meet the installability requirements</a>
------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [How the Lighthouse web app manifest audit fails](#how-the-lighthouse-web-app-manifest-audit-fails)
-   [How to make your PWA installable](#how-to-make-your-pwa-installable)
-   [How to check that your PWA is installable](#how-to-check-that-your-pwa-is-installable)
-   [In Chrome](#in-chrome)
-   [In other browsers](#in-other-browsers)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Web app manifest does not meet the installability requirements
==============================================================

May 4, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

Installability is a core requirement of [Progressive Web Apps (PWAs)](/discover-installable). By prompting users to install your PWA, you allow them to add it to their home screens. Users who add apps to home screens engage with those apps more frequently.

A [web app manifest](/add-manifest/) includes key pieces of information required to make your app installable.

How the Lighthouse web app manifest audit fails <a href="#how-the-lighthouse-web-app-manifest-audit-fails" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages that don't have a [web app manifest](/add-manifest/) that meets minimum requirements for installability:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/039DlaixA4drrswBzSra.png?auto=format&amp;w=1600 1600w" width="800" height="98" /></figure>If a page's manifest doesn't include the following properties, it will fail the audit:

-   A [`short_name`](https://developer.mozilla.org/en-US/docs/Web/Manifest/short_name) or [`name`](https://developer.mozilla.org/en-US/docs/Web/Manifest/name) property
-   An [`icons`](https://developer.mozilla.org/en-US/docs/Web/Manifest/icons) property that includes a 192x192 px and a 512x512 px icon
-   A [`start_url`](https://developer.mozilla.org/en-US/docs/Web/Manifest/start_url) property
-   A [`display`](https://developer.mozilla.org/en-US/docs/Web/Manifest/display) property set to `fullscreen`, `standalone`, or `minimal-ui`
-   A [`prefer_related_applications`](https://developers.google.com/web/fundamentals/app-install-banners/native) property set to a value other than `true`.

**Caution**: A web app manifest is *necessary* for your app to be installable, but it isn't *sufficient*. To learn how to meet all the requirements for installability, see the [Discover what it takes to be installable](/discover-installable) post.

In the Lighthouse report UI the full PWA badge is given when you pass all of the audits in all of the PWA subcategories (**Fast and reliable**, **Installable**, and **PWA optimized**).

How to make your PWA installable <a href="#how-to-make-your-pwa-installable" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------

Make sure your app has a manifest that meets the criteria above. See the [Installable](/installable/) collection for more information about creating a PWA.

How to check that your PWA is installable <a href="#how-to-check-that-your-pwa-is-installable" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------

### In Chrome <a href="#in-chrome" class="w-headline-link">#</a>

When your app meets the minimum requirements for installability, Chrome fires a `beforeinstallprompt` event that you can use to prompt the user to install your PWA.

**Try it**! Learn how to make your app installable in Chrome with the [Make it installable](/codelab-make-installable) codelab.

### In other browsers <a href="#in-other-browsers" class="w-headline-link">#</a>

Other browsers have different criteria for installation and for triggering the `beforeinstallprompt` event. Check their respective sites for full details:

-   [Edge](https://docs.microsoft.com/en-us/microsoft-edge/progressive-web-apps#requirements)
-   [Firefox](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Add_to_home_screen#How_do_you_make_an_app_A2HS-ready)
-   [Opera](https://dev.opera.com/articles/installable-web-apps/)
-   [Samsung Internet](https://hub.samsunginter.net/docs/ambient-badging/)
-   [UC Browser](https://plus.ucweb.com/docs/pwa/docs-en/zvrh56)

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **Web app manifest does not meet the installability requirements** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/installable-manifest.js)
-   [Add a web app manifest](/add-manifest/)
-   [Discover what it takes to be installable](/discover-installable)
-   [Web App Manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest)
-   [Does not use HTTPS](/is-on-https/)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/installable-manifest/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-make-installable/" class="w-callout__link w-callout__link--codelab">Make it installable</a>

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
