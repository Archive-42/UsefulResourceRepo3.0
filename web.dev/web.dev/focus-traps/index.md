## <a href="#user-focus-is-not-accidentally-trapped-in-a-region" class="w-toc__header--link">User focus is not accidentally trapped in a region</a>

- [How to manually test](#how-to-manually-test)
- [How to fix](#how-to-fix)
- [Why this matters](#why-this-matters)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# User focus is not accidentally trapped in a region

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Keyboard focus should never be locked or trapped at one particular page element. Users should be able to navigate to and from all page elements using only the keyboard.

## How to manually test <a href="#how-to-manually-test" class="w-headline-link">#</a>

To test users can't accidentally trap their focus, navigate to and from all page elements using only the keyboard. Use `TAB` to navigate "forward" and `SHIFT + TAB` to navigate "backward."

If you can't tab through all page elements successfully, then you've failed the test. When testing, watch out in particular for autocomplete widgets, where keyboard focus may get stuck.

## How to fix <a href="#how-to-fix" class="w-headline-link">#</a>

Pages that present content in multiple formats, such as modal dialogs, widgets, are at risk for focus traps. In the case of a displaying a modal, when you don't want the user interacting with the rest of the page, it makes sense to temporarily trap the user.

But you should aim to provide a keyboard-accessible method of escaping the modal as well. Check out [this example on how to create an accessible modal](https://github.com/gdkraus/accessible-modal-dialog). See also [Modals and Keyboard Traps](https://developers.google.com/web/fundamentals/accessibility/focus/using-tabindex#modals_and_keyboard_traps). In this example, you get the desired behaviors of a modal, without forcing the user to refresh the page to get out of the focus trap.

## Why this matters <a href="#why-this-matters" class="w-headline-link">#</a>

For users who either cannot or choose not to use a mouse, keyboard navigation is the primary means of reaching everything on a screen. Good keyboarding experiences depend on a logical tab order and easily discernible focus styles. If a keyboard user gets trapped in a particular page element, they have no way of interacting with the page.

Learn more in [How to do an Accessibility Review](https://developers.google.com/web/fundamentals/accessibility/how-to-review#try_it_with_a_screen_reader).

## Resources <a href="#resources" class="w-headline-link">#</a>

[Source code for **User focus is not accidentally trapped in a region** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/manual/focus-traps.js)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/focus-traps/index.md)

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
