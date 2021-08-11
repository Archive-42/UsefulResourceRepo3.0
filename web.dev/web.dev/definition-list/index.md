<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#lesscodegreaterandltdlandgtlesscodegreaters-do-not-contain-only-properly-ordered-lesscodegreaterandltdtandgtlesscodegreater-and-lesscodegreaterandltddandgtlesscodegreater-groups-lesscodegreaterandltscriptandgtlesscodegreater-or-lesscodegreaterandlttemplateandgtlesscodegreater-elements" class="w-toc__header--link"><code>&lt;dl&gt;</code>s do not contain only properly ordered <code>&lt;dt&gt;</code> and <code>&lt;dd&gt;</code> groups, <code>&lt;script&gt;</code>, or <code>&lt;template&gt;</code> elements</a>

- [How this Lighthouse audit fails](#how-this-lighthouse-audit-fails)
- [How to structure definition lists correctly](#how-to-structure-definition-lists-correctly)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# `<dl>`s do not contain only properly ordered `<dt>` and `<dd>` groups, `<script>`, or `<template>` elements

May 2, 2019 <span class="w-author__separator">•</span> Updated Mar 20, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Screen readers and other assistive technologies have a specific way of announcing definition lists. When definition lists are not properly marked up, assistive technologies may produce confusing or inaccurate output.

## How this Lighthouse audit fails <a href="#how-this-lighthouse-audit-fails" class="w-headline-link">#</a>

Lighthouse flags `<dl>` elements that don't contain properly ordered `<dt>` and `<dd>` groups, `<script>`, or `<template>` elements:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7PIfPwOqBuptPXkECl2J.png?auto=format&amp;w=1600 1600w" width="800" height="223" /></figure>The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to structure definition lists correctly <a href="#how-to-structure-definition-lists-correctly" class="w-headline-link">#</a>

Definition list items require `dl` elements around the list, `dt` elements for each term, and `dd` elements for each definition. Each set of `dt` elements must be followed by one or more `dd` elements. For example:

    <dl>
      <dt>Trail shoe</dt>
        <dd>Extra grip for uneven, natural survaces, such as forest trails.</dd>
      <dt>Road shoe</dt>
        <dd>Extra cushioning for hard surfaces, such as sidewalks and roads.</dd>
    </dl>

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **`<dl>`s do not contain only properly ordered `<dt>` and `<dd>` groups, `<script>`, or `<template>` elements** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/definition-list.js)
- [`<dl>` elements must only directly contain properly-ordered `<dt>` and `<dd>` groups, `<script>`, or `<template>` elements (Deque University)](https://dequeuniversity.com/rules/axe/3.3/definition-list)

<span class="w-mr--sm">Last updated: Mar 20, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/definition-list/index.md)

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
