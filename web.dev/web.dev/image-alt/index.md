## <a href="#image-elements-do-not-have-lesscodegreateraltlesscodegreater-attributes" class="w-toc__header--link">Image elements do not have <code>[alt]</code> attributes</a>

- [How the Lighthouse image alternative text audit fails](#how-the-lighthouse-image-alternative-text-audit-fails)
- [How to add alternative text to images](#how-to-add-alternative-text-to-images)
- [Tips for writing effective alt text](#tips-for-writing-effective-alt-text)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Image elements do not have `[alt]` attributes

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Informative elements should aim for short, descriptive alternate text. Decorative elements can be ignored with an empty alt attribute.

## How the Lighthouse image alternative text audit fails <a href="#how-the-lighthouse-image-alternative-text-audit-fails" class="w-headline-link">#</a>

Lighthouse flags `<img>` elements that don't have `alt` attributes:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hb8ypHK5xwmtUZwdxyQG.png?auto=format&amp;w=1600 1600w" width="800" height="206" /></figure>The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to add alternative text to images <a href="#how-to-add-alternative-text-to-images" class="w-headline-link">#</a>

Provide an `alt` attribute for every `<img>` element. If the image fails to load, the `alt` text is used as a placeholder so users have a sense of what the image was trying to convey. (See also [Include text alternatives for images and objects](/labels-and-text-alternatives#include-text-alternatives-for-images-and-objects).)

Most images should have short, descriptive text:

    <img alt="Audits set-up in Chrome DevTools" src="...">

If the image acts as decoration and does not provide any useful content, give it an empty `alt=""` attribute to remove it from the accessibility tree:

    <img src="background.png" alt="">

You can also use ARIA labels to describe your images, for example, `<img aria-label="Audits set-up in Chrome DevTools" src="...">` See also [Using the aria-label attribute](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-label_attribute) and [Using the aria-labelledby attribute](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-labelledby_attribute).

## Tips for writing effective `alt` text <a href="#tips-for-writing-effective-alt-text" class="w-headline-link">#</a>

- `alt` text should give the intent, purpose, and meaning of the image.
- Blind users should get as much information from alt text as a sighted user gets from the image.
- Avoid non-specific words like "chart", "image", or "diagram".

Learn more in [WebAIM's guide to Alternative Text](https://webaim.org/techniques/alttext/).

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Image elements do not have `[alt]` attributes** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/image-alt.js)
- [Images must have alternate text (Deque University)](https://dequeuniversity.com/rules/axe/3.3/image-alt)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/image-alt/index.md)

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
