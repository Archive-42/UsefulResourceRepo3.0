<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#lesscodegreateraria-hiddenandquottrueandquotlesscodegreater-elements-contain-focusable-descendants" class="w-toc__header--link"><code>[aria-hidden="true"]</code> elements contain focusable descendants</a>

- [How Lighthouse identifies partially hidden focusable elements](#how-lighthouse-identifies-partially-hidden-focusable-elements)
- [How to fix partially hidden focusable elements](#how-to-fix-partially-hidden-focusable-elements)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# `[aria-hidden="true"]` elements contain focusable descendants

Oct 17, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Users of screen readers and other assistive technologies need information about the behavior and purpose of controls on your web page. Built-in HTML controls like buttons and radio groups come with that information [built in](/use-semantic-html). For custom controls you create, however, you must provide the information with [ARIA](https://www.w3.org/TR/wai-aria-1.1/#role_definitions) roles and attributes. (Learn more in the [Introduction to ARIA](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/).)

Using the `aria-hidden="true"` attribute on an element hides the element and all its children from screen readers and other assistive technologies. If the hidden element contains a **focusable** element, assistive technologies won't read the focusable element, but keyboard users will still be able to navigate to it, which can cause confusion.

## How Lighthouse identifies partially hidden focusable elements <a href="#how-lighthouse-identifies-partially-hidden-focusable-elements" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse) flags focusable elements that have parents with the `aria-hidden="true"` attribute:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqhdHogcBrLR4W0uiECZ.png?auto=format&amp;w=1600 1600w" width="800" height="206" /></figure>An element is *focusable* when keyboard users can navigate to it using the `Tab` key. Focusability differs somewhat across browsers, but in general, the following elements are focusable:

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

The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to fix partially hidden focusable elements <a href="#how-to-fix-partially-hidden-focusable-elements" class="w-headline-link">#</a>

If you're hiding a container element on your page using `aria-hidden`, you also need to prevent users from navigating to any focusable elements inside that container.

One way to do that is to use JavaScript to apply a `tabindex="-1"` attribute to all focusable elements in the container. However, as implied by the list above, a query that captures all focusable elements can get complicated quickly.

If you're hiding the container element from sighted users, consider using one of the following strategies instead:

- Add a `hidden` attribute to the container element.
- Apply the `display: none` or the `visibility: hidden` CSS property to the container element.

If you can't visually hide the container element—for example, if it's behind a modal dialog with a translucent background—consider using [the WICG's `inert` polyfill](https://github.com/WICG/inert). The polyfill emulates the behavior of a proposed `inert` attribute, which prevents elements from being read or selected.

**Caution**: The `inert` polyfill is experimental and may not work as expected in all cases. Test carefully before using in production.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **`[aria-hidden="true"]` elements contain focusable descendants** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/aria-hidden-focus.js)
- [aria-hidden elements do not contain focusable elements (Deque University)](https://dequeuniversity.com/rules/axe/3.3/aria-hidden-focus)
- [WICG `inert` polyfill](https://github.com/WICG/inert)

<span class="w-mr--sm">Last updated: Oct 17, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/aria-hidden-focus/index.md)

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
