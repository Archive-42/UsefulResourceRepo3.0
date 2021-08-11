## <a href="#lesscodegreaterandltobjectandgtlesscodegreater-elements-do-not-have-lesscodegreateraltlesscodegreater-text" class="w-toc__header--link"><code>&lt;object&gt;</code> elements do not have <code>[alt]</code> text</a>

- [How this Lighthouse audit fails](#how-this-lighthouse-audit-fails)
- [How to add alternative text to &lt;object&gt; elements](#how-to-add-alternative-text-to-lessobjectgreater-elements)
- [Tips for writing effective alt text](#tips-for-writing-effective-alt-text)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# `<object>` elements do not have `[alt]` text

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Screen readers and other assistive technologies cannot translate non-text content. Adding alternative text to define `<object>` elements helps assistive technologies convey meaning to users.

## How this Lighthouse audit fails <a href="#how-this-lighthouse-audit-fails" class="w-headline-link">#</a>

Lighthouse flags `<object>` elements that don't have alternative text:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/JWSzKy951NpiznLGxqoQ.png?auto=format&amp;w=1600 1600w" width="800" height="206" /></figure>The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to add alternative text to `<object>` elements <a href="#how-to-add-alternative-text-to-lessobjectgreater-elements" class="w-headline-link">#</a>

Describe the object in the text content of the `<object>` element. In the example below `2019 Web Accessibility Report` is the description of the object.

    <object type="application/pdf"
        data="/report.pdf"
        width="600"
        height="400">
    2019 Web Accessibility Report
    </object>

Learn more in [Include text alternatives for images and objects](/labels-and-text-alternatives#include-text-alternatives-for-images-and-objects).

You can also use `alt` and ARIA labels to describe object elements, for example, `<object type="application/pdf" data="/report.pdf alt="2019 Web Accessibility Report">`. (See [&lt;object&gt; elements must have alternate text](https://dequeuniversity.com/rules/axe/3.3/object-alt).)

## Tips for writing effective `alt` text <a href="#tips-for-writing-effective-alt-text" class="w-headline-link">#</a>

- As previously mentioned, describe the information contained in the embedded object.
- Alternative text should give the intent, purpose, and meaning of the object.
- Blind users should get as much information from alternative text as a sighted user gets from the object.
- Avoid non-specific words like "chart", "image", or "diagram".

Learn more in [WebAIM's guide to Alternative Text](https://webaim.org/techniques/alttext/).

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **`<object>` elements do not have `[alt]` text** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/object-alt.js)
- [&lt;object&gt; elements must have alternate text (Deque University)](https://dequeuniversity.com/rules/axe/3.3/object-alt)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/object-alt/index.md)

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
