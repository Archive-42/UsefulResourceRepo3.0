<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#lesscodegreateridlesscodegreater-attributes-on-active-focusable-elements-are-not-unique" class="w-toc__header--link"><code>[id]</code> attributes on active, focusable elements are not unique</a>

- [How Lighthouse identifies focusable elements with duplicate IDs](#how-lighthouse-identifies-focusable-elements-with-duplicate-ids)
- [How to fix duplicate IDs](#how-to-fix-duplicate-ids)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# `[id]` attributes on active, focusable elements are not unique

Oct 17, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Each ID in your HTML document must be unique. Using the same ID on more than one element may cause screen readers and other assistive technologies to only announce the first element with the shared ID, preventing users from accessing the later elements.

Avoiding duplicate IDs for focusable controls like buttons and checkboxes is particularly important to ensure that users can access all of your page's functionality.

## How Lighthouse identifies focusable elements with duplicate IDs <a href="#how-lighthouse-identifies-focusable-elements-with-duplicate-ids" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags focusable elements that have duplicate IDs:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/hAevzwng1erk5DYZjLyq.png?auto=format&amp;w=1600 1600w" width="800" height="185" /></figure>An element is *focusable* when keyboard users can navigate to it using the `Tab` key. Focusability differs somewhat across browsers, but in general, the following elements are focusable:

- `<a>`
- `<area>`
- `<audio controls>`
- `<button>`
- `<iframe>`
- `<input>`
- `<select>`
- `<summary>`
- `<textarea>`
- `<video controls>`
- Any element with the `contentEditable` attribute
- Any element with a `tabindex` set to a numeric value other than `-1`

For a complete breakdown of cross-browser focus behavior, see ally.js's [Focusable Elements - Browser Compatibility Table](https://allyjs.io/data-tables/focusable.html).

This audit is similar to the [**ARIA IDs are not all unique**](/duplicate-id-aria) audit but checks for duplicate IDs in a different set of elements.

The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to fix duplicate IDs <a href="#how-to-fix-duplicate-ids" class="w-headline-link">#</a>

Change an ID value if it is used more than once.

For example, the following code sample includes two elements with the same ID. One ID should be changed:

    <input type="radio" id="huey" name="newphews" value="Huey" checked>
    <input type="radio" id="huey" name="newphews" value="Dewey" checked>
    <input type="radio" id="louie" name="newphews" value="Louie" checked>

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **`[id]` attributes on active, focusable elements are not unique** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/duplicate-id-active.js)
- [ID attribute value must be unique (Deque University)](https://dequeuniversity.com/rules/axe/3.3/duplicate-id-active)

<span class="w-mr--sm">Last updated: Oct 17, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/duplicate-id-active/index.md)

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
