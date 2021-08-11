## <a href="#document-does-not-have-a-meta-description" class="w-toc__header--link">Document does not have a meta description</a>

- [How the Lighthouse meta description audit fails](#how-the-lighthouse-meta-description-audit-fails)
- [How to add a meta description](#how-to-add-a-meta-description)
- [Meta description best practices](#meta-description-best-practices)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Document does not have a meta description

May 2, 2019 <span class="w-author__separator">•</span> Updated Apr 8, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-seo" class="w-post-signpost__link">SEO audits</a>

The `<meta name="description">` element provides a summary of a page's content that search engines include in search results. A high-quality, unique meta description makes your page appear more relevant and can increase your search traffic.

## How the Lighthouse meta description audit fails <a href="#how-the-lighthouse-meta-description-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages without a meta description:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format" class="w-screenshot w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dtMQ12xujHMJGuEwZ413.png?auto=format&amp;w=1600 1600w" width="800" height="74" /></figure>The audit fails if:

- Your page doesn't have a `<meta name=description>` element.
- The `content` attribute of the `<meta name=description>` element is empty.

Lighthouse doesn't evaluate the quality of your description.

Each SEO audit is weighted equally in the Lighthouse SEO Score, except for the manual **[Structured data is valid](/structured-data)** audit. Learn more in the [Lighthouse Scoring Guide](https://developers.google.com/web/tools/lighthouse/v3/scoring).

## How to add a meta description <a href="#how-to-add-a-meta-description" class="w-headline-link">#</a>

Add a `<meta name=description>` element to the `<head>` of each of your pages:

    <meta name="description" content="Put your description here.">

If appropriate, include clearly tagged facts in the descriptions. For example:

    <meta name="description" content="Author: A.N. Author,
        Illustrator: P. Picture, Category: Books, Price: $17.99,
        Length: 784 pages">

## Meta description best practices <a href="#meta-description-best-practices" class="w-headline-link">#</a>

- Use a unique description for each page.
- Make descriptions clear and concise. Avoid vague descriptions like "Home."
- Avoid [keyword stuffing](https://support.google.com/webmasters/answer/66358). It doesn't help users, and search engines may mark the page as spam.
- Descriptions don't have to be complete sentences; they can contain structured data.

Here are examples of good and bad descriptions:

Don't

    <meta name="description" content="A donut recipe.">

Too vague.

Do

    <meta
      name="description"
      content="Mary's simple recipe for maple bacon donuts
               makes a sticky, sweet treat with just a hint
               of salt that you'll keep coming back for.">

Descriptive yet concise.

See Google's [Create good titles and snippets in Search Results](https://support.google.com/webmasters/answer/35624#1) page for more tips.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Document does not have a meta description** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/seo/meta-description.js)
- [Create good titles and snippets in Search Results](https://support.google.com/webmasters/answer/35624#1)
- [Irrelevant keywords](https://support.google.com/webmasters/answer/66358)

<span class="w-mr--sm">Last updated: Apr 8, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-seo/meta-description/index.md)

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
