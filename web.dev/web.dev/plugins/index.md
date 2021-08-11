## <a href="#document-uses-plugins" class="w-toc__header--link">Document uses plugins</a>

- [How the Lighthouse plugins audit fails](#how-the-lighthouse-plugins-audit-fails)
- [Don't use plugins to display your content](#don't-use-plugins-to-display-your-content)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Document uses plugins

May 2, 2019 <span class="w-author__separator">•</span> Updated Aug 21, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-seo" class="w-post-signpost__link">SEO audits</a>

Search engines often can't index content that relies on browser plugins, such as Java or Flash. That means plugin-based content doesn't show up in search results.

Also, most mobile devices don't support plugins, which [creates frustrating experiences for mobile users](https://developers.google.com/search/mobile-sites/mobile-seo/common-mistakes#unplayable-content).

## How the Lighthouse plugins audit fails <a href="#how-the-lighthouse-plugins-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages that use plugins:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format" class="w-screenshot w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lL85pZVbdytWgeGIL8wB.png?auto=format&amp;w=1600 1600w" width="800" height="163" /></figure>Lighthouse checks the page for elements that commonly represent plugins:

- `embed`
- `object`
- `applet`

Lighthouse then flags an element as a plugin if its MIME type matches any of the following:

- `application/x-java-applet`
- `application/x-java-bean`
- `application/x-shockwave-flash`
- `application/x-silverlight`
- `application/x-silverlight-2`

Lighthouse also flags elements that point to a URL with a file format that is known to represent plugin content:

- `swf`
- `flv`
- `class`
- `xap`

## Don't use plugins to display your content <a href="#don&#39;t-use-plugins-to-display-your-content" class="w-headline-link">#</a>

To convert plugin-based content to HTML, refer to guidance for that plugin. For example, MDN explains [how to convert Flash video to HTML5 video](https://developer.mozilla.org/en-US/docs/Plugins/Flash_to_HTML5/Video).

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Document uses plugins** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/seo/plugins.js)
- [Unplayable content on mobile devices](https://developers.google.com/search/mobile-sites/mobile-seo/common-mistakes#unplayable-content)
- [Flash video to HTML5 video](https://developer.mozilla.org/en-US/docs/Plugins/Flash_to_HTML5/Video)

Each SEO audit is weighted equally in the Lighthouse SEO Score, except for the manual **[Structured data is valid](/structured-data)** audit. Learn more in the [Lighthouse Scoring Guide](https://developers.google.com/web/tools/lighthouse/v3/scoring).

<span class="w-mr--sm">Last updated: Aug 21, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-seo/plugins/index.md)

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
