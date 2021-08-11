<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#document-doesn&#39;t-have-a-valid-lesscodegreaterhreflanglesscodegreater" class="w-toc__header--link">Document doesn't have a valid <code>hreflang</code></a>

- [How the Lighthouse hreflang audit fails](#how-the-lighthouse-hreflang-audit-fails)
- [How to define an hreflang link for each version of a page](#how-to-define-an-hreflang-link-for-each-version-of-a-page)
- [Guidelines for hreflang values](#guidelines-for-hreflang-values)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Document doesn't have a valid `hreflang`

May 2, 2019 <span class="w-author__separator">•</span> Updated Aug 21, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-seo" class="w-post-signpost__link">SEO audits</a>

Many sites provide different versions of a page based on a user's language or region. `hreflang` links tell search engines the URLs for all the versions of a page so that they can display the correct version for each language or region.

## How the Lighthouse `hreflang` audit fails <a href="#how-the-lighthouse-hreflang-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags incorrect `hreflang` links:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format" class="w-screenshot w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9SqStqAKEC9FyHAC2TRQ.png?auto=format&amp;w=1600 1600w" width="800" height="185" /></figure>Lighthouse checks for `hreflang` links in the page's `head` and in its [response headers](https://developer.mozilla.org/en-US/docs/Glossary/Response_header).

Lighthouse then checks for valid language codes within the `hreflang`links. Lighthouse reports any `hreflang` links with invalid language codes.

Lighthouse does not check region codes or your [sitemap](https://support.google.com/webmasters/answer/156184).

Each SEO audit is weighted equally in the Lighthouse SEO Score, except for the manual **[Structured data is valid](/structured-data)** audit. Learn more in the [Lighthouse Scoring Guide](https://developers.google.com/web/tools/lighthouse/v3/scoring).

## How to define an `hreflang` link for each version of a page <a href="#how-to-define-an-hreflang-link-for-each-version-of-a-page" class="w-headline-link">#</a>

Suppose that you have three versions of a page:

- An English version at `https://example.com`
- A Spanish version at `https://es.example.com`
- A German version at `https://de.example.com`

There are three ways to tell search engines that these pages are equivalent. Choose whichever method is easiest for your situation.

**Option 1:** Add `hreflang` links to the `<head>` of each page:

    <link rel="alternate" hreflang="en" href="https://example.com" />
    <link rel="alternate" hreflang="es" href="https://es.example.com" />
    <link rel="alternate" hreflang="de" href="https://de.example.com" />

Each version of a page must link to all other versions, **including itself**. Otherwise, search engines may ignore the `hreflang` links or interpret them incorrectly.

For pages that allow users to select their language, use the `x-default` keyword:

    <link rel="alternate" href="https://example.com" hreflang="x-default" />

**Option 2:** Add `Link` headers to your HTTP response:

    Link: <https://example.com>; rel="alternate"; hreflang="en", <https://es.example.com>;
    rel="alternate"; hreflang="es", <https://de.example.com>; rel="alternate"; hreflang="de"

**Option 3:** Add language version information to your [sitemap](https://support.google.com/webmasters/answer/156184).

    <url>
    <loc>https://example.com</loc>

    <xhtml:link rel="alternate" hreflang="es"
    href="https://es.example.com"/>

    <xhtml:link rel="alternate" hreflang="de"
    href="https://es.example.com"/>

    </url>

For more information, see Google's [Tell Google about localized versions of your page](https://support.google.com/webmasters/answer/189077).

## Guidelines for `hreflang` values <a href="#guidelines-for-hreflang-values" class="w-headline-link">#</a>

- The `hreflang` value must always specify a language code.
- The language code must follow [ISO 639-1 format](https://wikipedia.org/wiki/List_of_ISO_639-1_codes).
- The `hreflang` value can also include an optional regional code. For example, `es-mx` is for Spanish speakers in Mexico, while `es-cl` is for Spanish speakers in Chile.
- The region code must follow the [ISO 3166-1 alpha-2 format](https://wikipedia.org/wiki/ISO_3166-1_alpha-2).

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Document does not have a valid `hreflang`** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/seo/hreflang.js)
- [Tell Google about localized versions of your page](https://support.google.com/webmasters/answer/189077)
- [ISO 639-1 format](https://wikipedia.org/wiki/List_of_ISO_639-1_codes)
- [ISO 3166-1 alpha-2 format](https://wikipedia.org/wiki/ISO_3166-1_alpha-2)

<span class="w-mr--sm">Last updated: Aug 21, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-seo/hreflang/index.md)

<a href="/lighthouse-seo" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
