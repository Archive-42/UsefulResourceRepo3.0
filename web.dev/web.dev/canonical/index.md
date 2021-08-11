<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#document-does-not-have-a-valid-lesscodegreaterrelcanonicallesscodegreater" class="w-toc__header--link">Document does not have a valid <code>rel=canonical</code></a>
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [How the Lighthouse canonical links audit fails](#how-the-lighthouse-canonical-links-audit-fails)
-   [How to add canonical links to your pages](#how-to-add-canonical-links-to-your-pages)
-   [General guidelines](#general-guidelines)
-   [Google-specific guidelines](#google-specific-guidelines)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Document does not have a valid `rel=canonical`
==============================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Aug 20, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-seo" class="w-post-signpost__link">SEO audits</a>

When multiple pages have similar content, search engines consider them duplicate versions of the same page. For example, desktop and mobile versions of a product page are often considered duplicates.

Search engines select one of the pages as the *canonical*, or primary, version and **crawl** that one more. Valid canonical links let you tell search engines which version of a page to crawl and display to users in search results.

**Key Term**: *Crawling* is how a search engine updates its index of content on the web.

Using canonical links has many advantages:

-   It helps search engines consolidate multiple URLs into a single, preferred URL. For example, if other sites put query parameters on the ends of links to your page, search engines consolidate those URLs to your preferred version.
-   It simplifies tracking methods. Tracking one URL is easier than tracking many.
-   It improves the page ranking of syndicated content by consolidating the syndicated links to your original content back to your preferred URL.

How the Lighthouse canonical links audit fails <a href="#how-the-lighthouse-canonical-links-audit-fails" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags any page with an invalid canonical link:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format" class="w-screenshot w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TLhOThFgDllifsEEeOH3.png?auto=format&amp;w=1600 1600w" width="800" height="76" /></figure>A page fails this audit if any of the following conditions are met:

-   There is more than one canonical link.
-   The canonical link is not a valid URL.
-   The canonical link points to a page for a different region or language.
-   The canonical link points to a different domain.
-   The canonical link points to the site root. Note that this scenario may be valid in some scenarios, such as for AMP or mobile page variations, but Lighthouse nonetheless treats it as a failure.

Each SEO audit is weighted equally in the Lighthouse SEO Score, except for the manual **[Structured data is valid](/structured-data)** audit. Learn more in the [Lighthouse Scoring Guide](https://developers.google.com/web/tools/lighthouse/v3/scoring).

How to add canonical links to your pages <a href="#how-to-add-canonical-links-to-your-pages" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------

There are two options for specifying a canonical link.

**Option 1:** Add a `<link rel=canonical>` element to the `<head>` of the page:

    <!doctype html>
    <html lang="en">
      <head>
        …
        <link rel="canonical" href="https://example.com"/>
        …
      </head>
      <body>
        …
      </body>
    </html>

**Option 2:** Add a `Link` header to the HTTP response:

    Link: https://example.com; rel=canonical

For a list of the pros and cons of each approach, see Google's [Consolidate duplicate URLs](https://support.google.com/webmasters/answer/139066) page.

### General guidelines <a href="#general-guidelines" class="w-headline-link">#</a>

-   Make sure that the canonical URL is valid.
-   Use secure [HTTPS](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/why-https) canonical URLs rather than HTTP whenever possible.
-   If you use [`hreflang` links](/hreflang) to serve different versions of a page depending on a user's language or country, make sure that the canonical URL points to the proper page for that respective language or country.
-   Don't point the canonical URL to a different domain. Yahoo and Bing don't allow this.
-   Don't point lower-level pages to the site's root page unless their content is the same.

### Google-specific guidelines <a href="#google-specific-guidelines" class="w-headline-link">#</a>

-   Use the [Google Search Console](https://search.google.com/search-console/index) to see which URLs Google considers canonical or duplicative across your entire site.
-   Don't use Google's URL removal tool for canonization. It removes *all* versions of a URL from search.

Recommendations for other search engines are welcome. [Edit this page](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-seo/canonical/index.md).

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **Document does not have a valid `rel=canonical`** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/seo/canonical.js)
-   [5 common mistakes with rel=canonical](https://webmasters.googleblog.com/2013/04/5-common-mistakes-with-relcanonical.html)
-   [Consolidate duplicate URLs](https://support.google.com/webmasters/answer/139066)
-   [Block crawling of parameterized duplicate content](https://support.google.com/webmasters/answer/6080548)
-   [Google Search Console](https://search.google.com/search-console/index)

<span class="w-mr--sm">Last updated: Aug 20, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-seo/canonical/index.md)

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
