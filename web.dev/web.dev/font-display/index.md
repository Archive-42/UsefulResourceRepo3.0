## <a href="#ensure-text-remains-visible-during-webfont-load" class="w-toc__header--link">Ensure text remains visible during webfont load</a>

- [How the Lighthouse font-display audit fails](#how-the-lighthouse-font-display-audit-fails)
- [How to avoid showing invisible text](#how-to-avoid-showing-invisible-text)
- [Preload web fonts](#preload-web-fonts)
- [Google Fonts](#google-fonts)
- [Browser support](#browser-support)
- [Stack-specific guidance](#stack-specific-guidance)
- [Drupal](#drupal)
- [Magento](#magento)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Ensure text remains visible during webfont load

May 2, 2019 <span class="w-author__separator">•</span> Updated Apr 29, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-performance" class="w-post-signpost__link">Performance audits</a>

Fonts are often large files that take awhile to load. Some browsers hide text until the font loads, causing a [flash of invisible text (FOIT)](/avoid-invisible-text).

## How the Lighthouse font-display audit fails <a href="#how-the-lighthouse-font-display-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags any font URLs that may flash invisible text:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/251Gbh9tn89GDJY289zZ.png?auto=format&amp;w=1600 1600w" width="800" height="430" /></figure>See the [Lighthouse performance scoring](/performance-scoring) post to learn how your page's overall performance score is calculated.

## How to avoid showing invisible text <a href="#how-to-avoid-showing-invisible-text" class="w-headline-link">#</a>

The easiest way to avoid showing invisible text while custom fonts load is to temporarily show a system font. By including `font-display: swap` in your `@font-face` style, you can avoid FOIT in most modern browsers:

    @font-face {
      font-family: 'Pacifico';
      font-style: normal;
      font-weight: 400;
      src: local('Pacifico Regular'), local('Pacifico-Regular'), url(https://fonts.gstatic.com/s/pacifico/v12/FwZY7-Qmy14u9lezJ-6H6MmBp0u-.woff2) format('woff2');
      font-display: swap;
    }

The [font-display API](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display) specifies how a font is displayed. `swap` tells the browser that text using the font should be displayed immediately using a system font. Once the custom font is ready, it replaces the system font. (See the [Avoid invisible text during loading](/avoid-invisible-text) post for more information.)

### Preload web fonts <a href="#preload-web-fonts" class="w-headline-link">#</a>

Use `<link rel="preload" as="font">` to fetch your font files earlier. Learn more:

- [Preload web fonts to improve loading speed (codelab)](/codelab-preload-web-fonts/)
- [Prevent layout shifting and flashes of invisibile text (FOIT) by preloading optional fonts](/preload-optional-fonts/)

### Google Fonts <a href="#google-fonts" class="w-headline-link">#</a>

Add the `&display=swap` [parameter](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL#Basics_anatomy_of_a_URL) to the end of your Google Fonts URL:

    <link href="https://fonts.googleapis.com/css?family=Roboto:400,700&display=swap" rel="stylesheet">

## Browser support <a href="#browser-support" class="w-headline-link">#</a>

It's worth mentioning that not all major browsers support `font-display: swap`, so you may need to do a bit more work to fix the invisible text problem.

**Try it**! Check out the [Avoid flash of invisible text codelab](/codelab-avoid-invisible-text) to learn how to avoid FOIT across all browsers.

## Stack-specific guidance <a href="#stack-specific-guidance" class="w-headline-link">#</a>

### Drupal <a href="#drupal" class="w-headline-link">#</a>

Specify `@font-display` when defining custom fonts in your theme.

### Magento <a href="#magento" class="w-headline-link">#</a>

Specify `@font-display` when [defining custom fonts](https://devdocs.magento.com/guides/v2.3/frontend-dev-guide/css-topics/using-fonts.html).

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Ensure text remains visible during webfont load** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/font-display.js)
- [Avoid invisible text during loading](/avoid-invisible-text)
- [Controlling font performance with font displays](https://developers.google.com/web/updates/2016/02/font-display)
- [Preload web fonts to improve loading speed (codelab)](/codelab-preload-web-fonts/)
- [Prevent layout shifting and flashes of invisibile text (FOIT) by preloading optional fonts](/preload-optional-fonts/)

<span class="w-mr--sm">Last updated: Apr 29, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-performance/font-display/index.md)

<a href="/lighthouse-performance" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
