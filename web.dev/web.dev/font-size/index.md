<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#document-doesn&#39;t-use-legible-font-sizes" class="w-toc__header--link">Document doesn't use legible font sizes</a>
------------------------------------------------------------------------------------------------------------------------------

-   [How the Lighthouse font size audit fails](#how-the-lighthouse-font-size-audit-fails)
-   [How to fix illegible fonts](#how-to-fix-illegible-fonts)
-   [How to fix a missing viewport config](#how-to-fix-a-missing-viewport-config)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Document doesn't use legible font sizes
=======================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Aug 20, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-seo" class="w-post-signpost__link">SEO audits</a>

Many search engines rank pages based on how mobile-friendly they are. Font sizes smaller than 12 px are often difficult to read on mobile devices and may require users to zoom in to display text at a comfortable reading size.

How the Lighthouse font size audit fails <a href="#how-the-lighthouse-font-size-audit-fails" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages with font sizes that are too small to read easily on mobile:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ky2VDt8ZtedleWFLn1Gt.png?auto=format&amp;w=1600 1600w" width="800" height="225" /></figure>Lighthouse flags pages on which 60% or more of the text has a font size smaller than 12 px. When a page fails the audit, Lighthouse lists the results in a table with four columns:

<table><tbody><tr class="odd"><td><strong>Source</strong></td><td>The source location of the CSS ruleset that is causing the illegible text.</td></tr><tr class="even"><td><strong>Selector</strong></td><td>The selector of the ruleset.</td></tr><tr class="odd"><td><strong>% of Page Text</strong></td><td>The percentage of text on the page that is affected by the ruleset.</td></tr><tr class="even"><td><strong>Font Size</strong></td><td>The computed size of the text.</td></tr></tbody></table>

Each SEO audit is weighted equally in the Lighthouse SEO Score, except for the manual **[Structured data is valid](/structured-data)** audit. Learn more in the [Lighthouse Scoring Guide](https://developers.google.com/web/tools/lighthouse/v3/scoring).

How to fix illegible fonts <a href="#how-to-fix-illegible-fonts" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------

Check font sizes in your CSS. Aim to have a font size of at least 12 px on at least 60% of the text on your page.

How to fix a missing viewport config <a href="#how-to-fix-a-missing-viewport-config" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------

If Lighthouse reports `Text is illegible because of a missing viewport config`, add a `<meta name="viewport" content="width=device-width, initial-scale=1">` tag to the `<head>` of your document.

See the [Does not have a `<meta name="viewport">` tag with `width` or `initial-scale`](/viewport) post for more information.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

[Source code for **Document does not use legible font sizes** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/seo/font-size.js)

<span class="w-mr--sm">Last updated: Aug 20, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-seo/font-size/index.md)

<a href="/lighthouse-seo" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
