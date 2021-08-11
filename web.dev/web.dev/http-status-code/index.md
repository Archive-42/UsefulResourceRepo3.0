

## <a href="#page-has-unsuccessful-http-status-code" class="w-toc__header--link">Page has unsuccessful HTTP status code</a>

- [How the Lighthouse HTTP status code audit fails](#how-the-lighthouse-http-status-code-audit-fails)
- [How to fix an unsuccessful HTTP status code](#how-to-fix-an-unsuccessful-http-status-code)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Page has unsuccessful HTTP status code

May 2, 2019 <span class="w-author__separator">•</span> Updated Aug 21, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-seo" class="w-post-signpost__link">SEO audits</a>

Servers provide a three-digit [HTTP status code](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status) for each resource request they receive. Status codes in the 400s and 500s [indicate that there's an error](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status#Client_error_responses) with the requested resource. If a search engine encounters a status code error when it's **crawling** a web page, it may not index that page properly.

**Key Term**: _Crawling_ is how a search engine updates its index of content on the web.

## How the Lighthouse HTTP status code audit fails <a href="#how-the-lighthouse-http-status-code-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages that return an unsuccessful HTTP status code (in the 400s or 500s):

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/omMzgdKyzeYBQjPjQFKa.png?auto=format&amp;w=1600 1600w" width="800" height="74" /></figure>Each SEO audit is weighted equally in the Lighthouse SEO Score, except for the manual **[Structured data is valid](/structured-data)** audit. Learn more in the [Lighthouse Scoring Guide](https://developers.google.com/web/tools/lighthouse/v3/scoring).

## How to fix an unsuccessful HTTP status code <a href="#how-to-fix-an-unsuccessful-http-status-code" class="w-headline-link">#</a>

First make sure you actually want search engines to crawl the page. Some pages, like your 404 page or any other page that shows an error, shouldn't be included in search results.

To fix an HTTP status code error, refer to the documentation for your server or hosting provider. The server should return a status code in the 200s for all valid URLs or a status code in the 300s for a resource that has moved to another URL.

If you're [using Github Pages to host a single-page app](https://www.smashingmagazine.com/2016/08/sghpa-single-page-app-hack-github-pages/), you'll likely need to serve valid content with a 404 status code.

**Try it**! Single-page applications can make fixing HTTP status code errors a bit more complicated. Learn how to [fix sneaky 404s in an Express application](/codelab-fix-sneaky-404).

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Page has unsuccessful HTTP status code** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/seo/http-status-code.js)
- [HTTP response status codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-fix-sneaky-404/" class="w-callout__link w-callout__link--codelab">Fix sneaky 404s</a>

<span class="w-mr--sm">Last updated: Aug 21, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-seo/http-status-code/index.md)

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
