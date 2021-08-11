





## <a href="#custom-controls-have-aria-roles" class="w-toc__header--link">Custom controls have ARIA roles</a>

- [How to manually test](#how-to-manually-test)
- [How to fix](#how-to-fix)
- [Why this matters](#why-this-matters)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Custom controls have ARIA roles

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Check that all custom controls have an appropriate `role` and any required ARIA attributes that confer their properties and state. For example, a custom checkbox needs a `role="checkbox"` and `aria-checked="true|false"` to properly convey its state. See the [Introduction to ARIA](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/) for a general overview of how ARIA can provide missing semantics for custom controls.

## How to manually test <a href="#how-to-manually-test" class="w-headline-link">#</a>

To check that all custom interactive controls have appropriate ARIA roles, test the page using either the [Chrome DevTools accessibility pane](https://developers.google.com/web/tools/chrome-devtools/accessibility/reference#pane) or a screen reader. [JAWS](https://www.freedomscientific.com/products/software/jaws/) and [NVDA](https://www.nvaccess.org/) are two of the more popular screen readers for Windows. [VoiceOver](https://www.apple.com/accessibility/mac/vision/) is the screen reader built into MacOS.

Using CSS, it's possible to style the `<div>` and `<button>` elements so they convey the same visual affordances, but the two experiences are very different when using a screen reader. A `<div>` is just a generic grouping element, so a screen reader only announces the text content of the `<div>`. The `<button>` is announced as a "button," a much stronger signal to the user that it's something they can interact with. See also [Semantics and screen readers](/semantics-and-screen-readers).

## How to fix <a href="#how-to-fix" class="w-headline-link">#</a>

The simplest and often best solution to this problem is to avoid custom interactive controls altogether. For example, replace a `<div>` that's acting like a button with an actual `<button>`.

If you must keep the `<div>`, then add `role="button"` and `aria-pressed="false"` to the `<div>`:

Now screen readers will announces the role and interactive state for the `<div>`.

## Why this matters <a href="#why-this-matters" class="w-headline-link">#</a>

The only way to truly understand how assistive technology users experience your content is to check that content yourself using a screen reader. Using a screen reader first hand will give you a clear understanding of how your content is labeled, and if there are any obstructions to assistive technology navigation. If you're unfamiliar with how semantic markup gets interpreted by assistive technology, see the [Introduction to Semantics](https://developers.google.com/web/fundamentals/accessibility/semantics-builtin/) for a refresher.

See also [How to Do an Accessibility Review](https://developers.google.com/web/fundamentals/accessibility/how-to-review#try_it_with_a_screen_reader).

## Resources <a href="#resources" class="w-headline-link">#</a>

[Source code for **Custom controls have ARIA roles** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/manual/custom-controls-roles.js)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/custom-control-roles/index.md)

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
