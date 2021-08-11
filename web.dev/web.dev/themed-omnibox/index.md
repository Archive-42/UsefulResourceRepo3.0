





<a href="#does-not-set-a-theme-color-for-the-address-bar" class="w-toc__header--link">Does not set a theme color for the address bar</a>
----------------------------------------------------------------------------------------------------------------------------------------

-   [Browser compatibility](#browser-compatibility)
-   [How the Lighthouse theme color audit fails](#how-the-lighthouse-theme-color-audit-fails)
-   [How to set a theme color for the address bar](#how-to-set-a-theme-color-for-the-address-bar)
-   [Step 1: Add a theme-color meta tag to every page you want to brand](#step-1:-add-a-theme-color-meta-tag-to-every-page-you-want-to-brand)
-   [Step 2: Add the theme\_color property to your web app manifest](#step-2:-add-the-theme_color-property-to-your-web-app-manifest)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Does not set a theme color for the address bar
==============================================

May 4, 2019 <span class="w-author__separator">•</span> Updated Jun 17, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

Theming the browser's address bar to match the brand colors of your [Progressive Web App (PWA)](/discover-installable) provides a more immersive user experience.

Browser compatibility <a href="#browser-compatibility" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

At the time of writing, theming the browser address bar is supported on Android-based browsers. See [Browser compatibility](https://developer.mozilla.org/docs/Web/Manifest/theme_color#Browser_compatibility) for updates.

How the Lighthouse theme color audit fails <a href="#how-the-lighthouse-theme-color-audit-fails" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages that don't apply a theme to the address bar:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/YadFSuw8denjl1hhnvFs.png?auto=format&amp;w=1600 1600w" width="800" height="98" /></figure>The audit fails if Lighthouse doesn't find a `theme-color` meta tag in the page's HTML and a `theme_color` property in the [web app manifest](/add-manifest).

Note that Lighthouse doesn't test whether the values are valid CSS color values.

In the Lighthouse report UI the full PWA badge is given when you pass all of the audits in all of the PWA subcategories (**Fast and reliable**, **Installable**, and **PWA optimized**).

How to set a theme color for the address bar <a href="#how-to-set-a-theme-color-for-the-address-bar" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------

### Step 1: Add a `theme-color` meta tag to every page you want to brand <a href="#step-1:-add-a-theme-color-meta-tag-to-every-page-you-want-to-brand" class="w-headline-link">#</a>

The `theme-color` meta tag ensures that the address bar is branded when a user visits your site as a normal webpage. Set the tag's `content` attribute to any valid CSS color value:

    <!DOCTYPE html>
    <html lang="en">
    <head>
      …
      <meta name="theme-color" content="#317EFB"/>
      …
    </head>
    …

Learn more about the `theme-color` meta tag in Google's [Support for `theme-color` in Chrome 39 for Android](https://developers.google.com/web/updates/2014/11/Support-for-theme-color-in-Chrome-39-for-Android).

### Step 2: Add the `theme_color` property to your web app manifest <a href="#step-2:-add-the-theme_color-property-to-your-web-app-manifest" class="w-headline-link">#</a>

The `theme_color` property in your web app manifest ensures that the address bar is branded when a user launches your PWA from the home screen. Unlike the `theme-color` meta tag, you only need to define this once, in the [manifest](/add-manifest). Set the property to any valid CSS color value:

    {
      "theme_color": "#317EFB"
      …
    }

The browser will set the address bar color of every page of your app according to the manifest's `theme_color`.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **Does not set a theme color for the address bar** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/themed-omnibox.js)
-   [Add a web app manifest](/add-manifest)
-   [Support for `theme-color` in Chrome 39 for Android](https://developers.google.com/web/updates/2014/11/Support-for-theme-color-in-Chrome-39-for-Android)

<span class="w-mr--sm">Last updated: Jun 17, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/themed-omnibox/index.md)

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
