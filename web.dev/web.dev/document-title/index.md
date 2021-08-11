<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#document-doesn&#39;t-have-a-lesscodegreaterandlttitleandgtlesscodegreater-element" class="w-toc__header--link">Document doesn't have a <code>&lt;title&gt;</code> element</a>

- [How the Lighthouse title audit fails](#how-the-lighthouse-title-audit-fails)
- [How to add a title](#how-to-add-a-title)
- [Tips for creating great titles](#tips-for-creating-great-titles)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Document doesn't have a `<title>` element

May 2, 2019 <span class="w-author__separator">•</span> Updated Mar 20, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a><span class="w-post-signpost__divider">|</span><a href="/lighthouse-seo" class="w-post-signpost__link">SEO audits</a>

Having a `<title>` element on every page helps all your users:

- Search engine users rely on the title to determine whether a page is relevant to their search.
- The title also gives users of screen readers and other assistive technologies an overview of the page. The title is the first text that an assistive technology announces.

## How the Lighthouse title audit fails <a href="#how-the-lighthouse-title-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages without a `<title>` element in the page's `<head>`:

## <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format" class="w-screenshot w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/zHgXut3CQbi5wnev8ypt.png?auto=format&amp;w=1600 1600w" width="800" height="206" /></figure>How to add a title <a href="#how-to-add-a-title" class="w-headline-link">#</a>

Add a `<title>` element to the `<head>` of your page. Make sure the title clearly states what the page is about. For example:

    <!doctype html>
      <html lang="en">
        <head>
          …
          <title>20-week training schedule for your first marathon</title>
          …
        </head>
      <body>
        …
      </body>
    </html>

## Tips for creating great titles <a href="#tips-for-creating-great-titles" class="w-headline-link">#</a>

- Use a unique title for each page.
- Make titles descriptive and concise. Avoid vague titles like "Home."
- Avoid [keyword stuffing](https://support.google.com/webmasters/answer/66358). It doesn't help users, and search engines may mark the page as spam.
- It's OK to brand your titles, but do so concisely.

Here are examples of good and bad titles:

Don't

    <title>Donut recipe</title>

Too vague.

Do

    <title>Mary's quick maple bacon donut recipe</title>

Descriptive yet concise.

See Google's [Create good titles and snippets in Search Results](https://support.google.com/webmasters/answer/35624) page for more details about these tips.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Document has a `<title>` element** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/document-title.js)
- [Create good titles and snippets in Search Results](https://support.google.com/webmasters/answer/35624)
- [Documents must contain a title element to aid in navigation (Deque University)](https://dequeuniversity.com/rules/axe/3.2/document-title)
- [Irrelevant keywords](https://support.google.com/webmasters/answer/66358)
- [Label documents and frames](/labels-and-text-alternatives#label-documents-and-frames)

<span class="w-mr--sm">Last updated: Mar 20, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/document-title/index.md)

<a href="/lighthouse-accessibility" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
