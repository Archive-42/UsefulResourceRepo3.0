<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#links-do-not-have-descriptive-text" class="w-toc__header--link">Links do not have descriptive text</a>
----------------------------------------------------------------------------------------------------------------

-   [How the Lighthouse link text audit fails](#how-the-lighthouse-link-text-audit-fails)
-   [How to add descriptive link text](#how-to-add-descriptive-link-text)
-   [Link text best practices](#link-text-best-practices)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Links do not have descriptive text
==================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Aug 21, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-seo" class="w-post-signpost__link">SEO audits</a>

Link text is the clickable word or phrase in a hyperlink. When link text clearly conveys a hyperlink's target, both users and search engines can more easily understand your content and how it relates to other pages.

How the Lighthouse link text audit fails <a href="#how-the-lighthouse-link-text-audit-fails" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags links without descriptive text:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format" class="w-screenshot w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hiv184j4TFNCsmqTCTNY.png?auto=format&amp;w=1600 1600w" width="800" height="191" /></figure>Lighthouse flags the following generic link text:

-   `click here`
-   `click this`
-   `go`
-   `here`
-   `this`
-   `start`
-   `right here`
-   `more`
-   `learn more`

Each SEO audit is weighted equally in the Lighthouse SEO Score, except for the manual **[Structured data is valid](/structured-data)** audit. Learn more in the [Lighthouse Scoring Guide](https://developers.google.com/web/tools/lighthouse/v3/scoring).

How to add descriptive link text <a href="#how-to-add-descriptive-link-text" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------

Replace generic phrases like "click here" and "learn more" with specific descriptions. In general, write link text that clearly indicates what type of content users will get if they follow the hyperlink.

    <p>To see all of our basketball videos, <a href="videos.html">click here</a>.</p>

Don't

"Click here" doesn't convey where the hyperlink will take users.

    <p>Check out all of our <a href="videos.html">basketball videos</a>.</p>

Do

"Basketball videos" clearly conveys that the hyperlink will take users to a page of videos.

You'll often need to revise the surrounding sentence to make link text descriptive.

Link text best practices <a href="#link-text-best-practices" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------

-   Stay on topic. Don't use link text that has no relation to the page's content.
-   Don't use the page's URL as the link description unless you have a good reason to do so, such as referencing a site's new address.
-   Keep descriptions concise. Aim for a few words or a short phrase.
-   Pay attention to your internal links too. Improving the quality of internal links can help both users and search engines navigate your site more easily.

See the [Use links wisely](https://support.google.com/webmasters/answer/7451184#uselinkswisely) section of Google's [Search Engine Optimization (SEO) Starter Guide](https://support.google.com/webmasters/answer/7451184) for more tips.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **Links do not have descriptive text** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/seo/link-text.js)
-   [Search Engine Optimization (SEO) Starter Guide](https://support.google.com/webmasters/answer/7451184)

<span class="w-mr--sm">Last updated: Aug 21, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-seo/link-text/index.md)

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
