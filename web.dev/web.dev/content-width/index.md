## <a href="#content-is-not-sized-correctly-for-the-viewport" class="w-toc__header--link">Content is not sized correctly for the viewport</a>

- [How the Lighthouse content width audit fails](#how-the-lighthouse-content-width-audit-fails)
- [How to make your page fit on mobile screens](#how-to-make-your-page-fit-on-mobile-screens)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Content is not sized correctly for the viewport

May 4, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

The viewport is the part of the browser window in which your page's content is visible. When your page's content width is smaller or larger than the viewport width, it may not render correctly on mobile screens. For example, if the content width is too large, content may be scaled down to fit, making text difficult to read.

## How the Lighthouse content width audit fails <a href="#how-the-lighthouse-content-width-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages whose width isn't equal to the width of the viewport:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y8JKlbJTu7ERetHUGuaA.png?auto=format&amp;w=1600 1600w" width="800" height="98" /></figure>The audit fails if `window.innerWidth` does not equal `window.outerWidth`.

In the Lighthouse report UI the full PWA badge is given when you pass all of the audits in all of the PWA subcategories (**Fast and reliable**, **Installable**, and **PWA optimized**).

## How to make your page fit on mobile screens <a href="#how-to-make-your-page-fit-on-mobile-screens" class="w-headline-link">#</a>

This audit is a roundabout way of determining if your page is optimized for mobile devices. See Google's [Responsive Web Design Basics](https://developers.google.com/web/fundamentals/design-and-ux/responsive/) for an overview of how to create a mobile-friendly page.

You can ignore this audit if:

- Your site does not need to be optimized for mobile screens.
- The content width of your page is intentionally smaller or larger than the viewport width.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Content is not sized correctly for the viewport** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/content-width.js)
- [Responsive Web Design Basics](https://developers.google.com/web/fundamentals/design-and-ux/responsive/)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/content-width/index.md)

<a href="/lighthouse-pwa" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
