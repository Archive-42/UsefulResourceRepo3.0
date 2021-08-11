<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#interactive-controls-are-keyboard-focusable" class="w-toc__header--link">Interactive controls are keyboard focusable</a>
----------------------------------------------------------------------------------------------------------------------------------

-   [How to manually test](#how-to-manually-test)
-   [How to fix](#how-to-fix)
-   [Why this matters](#why-this-matters)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Interactive controls are keyboard focusable
===========================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Manually check that all custom controls are keyboard focusable and display a focus indicator. The order in which elements are focused should aim to follow the DOM order. If you're unsure which elements should receive focus, see [Introduction to Focus](https://developers.google.com/web/fundamentals/accessibility/focus/).

How to manually test <a href="#how-to-manually-test" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

To test that the custom control is focusable and displays a focus indicator, start by tabbing through your site. Use `TAB` (or `SHIFT + TAB`) to move between controls, and use the arrow keys and `ENTER` and `SPACE` to manipulate their values (see also [Keyboard access fundamentals](/keyboard-access)):

Are you able to reach all of the interactive controls on the page? Is there a focus indicator on each interactive control?

How to fix <a href="#how-to-fix" class="w-headline-link">#</a>
--------------------------------------------------------------

If you aren't able to tab through all elements on a page, you may need to use `tabindex` to improve the focusability of those controls.

To make a custom control focusable, insert the custom control element into the natural tab order using `tabindex="0"` (see also [Control focus with tabindex](/control-focus-with-tabindex)). For example:

    <div tabindex="0">Focus me with the TAB key</div>

You may also need to add the appropriate ARIA roles to the custom control elements. See [Custom controls have ARIA roles](/custom-control-roles).

If you're not seeing a focus indicator, consider using `:focus` to always show a focus indicator. Regardless of whether you use a mouse or a keyboard to tab to it, the button's focus indicator always looks the same (see also [Style focus](/style-focus)).

Why this matters <a href="#why-this-matters" class="w-headline-link">#</a>
--------------------------------------------------------------------------

For users who either cannot or choose not to use a mouse, keyboard navigation is the primary means of reaching everything on a screen. Good keyboarding experiences depend on a logical tab order and easily discernable focus styles. If a keyboard user can't see what's focused, they have no way of interacting with the page.

Learn more in [How to do an Accessibility Review](https://developers.google.com/web/fundamentals/accessibility/how-to-review#try_it_with_a_screen_reader).

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **Interactive controls are keyboard focusable** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/manual/focusable-controls.js)
-   [Some elements have a `[tabindex]` value greater than `0`](/tabindex)
-   [Use semantic HTML for easy keyboard wins](/use-semantic-html)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/focusable-controls/index.md)

<a href="/lighthouse-accessibility" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

-   ### Contribute

    -   <a href="https://github.com/GoogleChrome/web.dev/issues/new?assignees=&amp;labels=bug&amp;template=bug_report.md&amp;title=" class="w-footer__linkbox-link">File a bug</a>
    -   <a href="https://github.com/googlechrome/web.dev" class="w-footer__linkbox-link">View source</a>

-   ### Related content

    -   <a href="https://blog.chromium.org/" class="w-footer__linkbox-link">Chrome updates</a>
    -   <a href="https://developers.google.com/web/" class="w-footer__linkbox-link">Web Fundamentals</a>
    -   <a href="https://developers.google.com/web/showcase/" class="w-footer__linkbox-link">Case studies</a>
    -   <a href="https://devwebfeed.appspot.com/" class="w-footer__linkbox-link">DevWeb Content Firehose</a>
    -   <a href="/podcasts/" class="w-footer__linkbox-link">Podcasts</a>
    -   <a href="/shows/" class="w-footer__linkbox-link">Shows</a>

-   ### Connect

    -   <a href="https://www.twitter.com/ChromiumDev" class="w-footer__linkbox-link">Twitter</a>
    -   <a href="https://www.youtube.com/user/ChromeDevelopers" class="w-footer__linkbox-link">YouTube</a>

<a href="https://developers.google.com/" class="w-footer__utility-logo-link"><img src="/images/lockup-color.png" alt="Google Developers" class="w-footer__utility-logo" width="185" height="33" /></a>

-   <a href="https://developer.chrome.com/" class="w-footer__utility-link">Chrome</a>
-   <a href="https://firebase.google.com/" class="w-footer__utility-link">Firebase</a>
-   <a href="https://cloud.google.com/" class="w-footer__utility-link">Google Cloud Platform</a>
-   <a href="https://developers.google.com/products" class="w-footer__utility-link">All products</a>

<!-- -->

-   <a href="https://policies.google.com/" class="w-footer__utility-link">Terms &amp; Privacy</a>
-   <a href="/community-guidelines/" class="w-footer__utility-link">Community Guidelines</a>

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/terms/site-policies).
