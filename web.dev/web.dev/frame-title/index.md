



## <a href="#lesscodegreaterandltframeandgtlesscodegreater-or-lesscodegreaterandltiframeandgtlesscodegreater-elements-do-not-have-a-title" class="w-toc__header--link"><code>&lt;frame&gt;</code> or <code>&lt;iframe&gt;</code> elements do not have a title</a>

- [How the Lighthouse frame title audit fails](#how-the-lighthouse-frame-title-audit-fails)
- [How to add titles to frames and iframes](#how-to-add-titles-to-frames-and-iframes)
- [Tips for creating descriptive frame titles](#tips-for-creating-descriptive-frame-titles)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# `<frame>` or `<iframe>` elements do not have a title

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Users of screen readers and other assistive technologies rely on frame titles to describe the contents of frames. Navigating through frames and inline frames can quickly become difficult and confusing for assistive technology users if the frames are not marked with a title attribute.

## How the Lighthouse frame title audit fails <a href="#how-the-lighthouse-frame-title-audit-fails" class="w-headline-link">#</a>

Lighthouse flags `<frame>` and `<iframe>` elements that don't have titles:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vlHxWKrB3ESjPfmLbuwL.png?auto=format&amp;w=1600 1600w" width="800" height="185" /></figure>The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to add titles to frames and iframes <a href="#how-to-add-titles-to-frames-and-iframes" class="w-headline-link">#</a>

Provide unique and descriptive `title` attributes for all `frame` and `iframe` elements.

Additionally, best practice is to give the enclosed document a title element with content identical to the title attribute. For example:

    <iframe title="My Daily Marathon Tracker" src="https://www.mydailymarathontracker.com/"></iframe>

## Tips for creating descriptive frame titles <a href="#tips-for-creating-descriptive-frame-titles" class="w-headline-link">#</a>

- As previously mentioned, give the enclosed document a title element with content identical to title attribute.
- Replace placeholder titles such as "untitled frame" with a more appropriate phrase.
- Make each title unique. Don't duplicate titles, even if they are similar.

Learn more in [Write descriptive titles, descriptions, and link text for every page](/write-descriptive-text).

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **`<frame>` or `<iframe>` elements do not have a title** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/frame-title.js)
- [Label documents and frames](/labels-and-text-alternatives#label-documents-and-frames)
- [Frames must have title attribute (Deque University)](https://dequeuniversity.com/rules/axe/3.3/frame-title)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/frame-title/index.md)

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
