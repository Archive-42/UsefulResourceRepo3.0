## <a href="#the-page-has-a-logical-tab-order" class="w-toc__header--link">The page has a logical tab order</a>

- [How to manually test](#how-to-manually-test)
- [How to fix](#how-to-fix)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# The page has a logical tab order

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Many different users rely on the keyboard to navigate applications, from users with temporary and permanent motor impairments to users who use keyboard shortcuts to be more efficient and productive. A logical tab order is an important part of providing a smooth keyboard navigation experience.

## How to manually test <a href="#how-to-manually-test" class="w-headline-link">#</a>

To check if your application's tab order is logical, try tabbing through your page. The order in which elements are focused should aim to follow the DOM order. In general, focus should follow reading order, moving from left to right, from the top to the bottom of your page.

Learn more in [Keyboard access fundamentals](/keyboard-access).

Are you able to reach all of the interactive controls on the page? If not, you may need to use `tabindex` to improve the focusability of those controls. The general rule of thumb is that any control a user can interact with or provide input to should aim to be focusable and display a focus indicator. If a keyboard user can't see what's focused, they have no way of interacting with the page.

## How to fix <a href="#how-to-fix" class="w-headline-link">#</a>

If the focus order seems wrong, you should rearrange the elements in the DOM to make the tab order more natural.

If you aren't able to reach all of the interactive controls on the page, the first go-to fix is to replace custom controls with standardized HTML alternatives. For example, replace a `<div>` acting like a button with `<button>`. Using built-in HTML elements can greatly improve the accessibility of your site, and significantly cut down on your workload.

If you're building custom interactive components with no standardized HTML equivalent, use the `tabindex` attribute to ensure that they're keyboard accessible. For example:

    <div tabindex="0">Focus me with the TAB key</div>

Learn more in [Control focus with tabindex](/control-focus-with-tabindex).

## Resources <a href="#resources" class="w-headline-link">#</a>

[Source code for **The page has a logical tab order** audit](https://github.com/GoogleChrome/lighthouse/blob/ecd10efc8230f6f772e672cd4b05e8fbc8a3112d/lighthouse-core/audits/accessibility/manual/logical-tab-order.js)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/logical-tab-order/index.md)

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
