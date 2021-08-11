<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#interactive-elements-indicate-their-purpose-and-state" class="w-toc__header--link">Interactive elements indicate their purpose and state</a>
------------------------------------------------------------------------------------------------------------------------------------------------------

-   [How to manually test visual focus](#how-to-manually-test-visual-focus)
-   [How to manually test with a screen reader](#how-to-manually-test-with-a-screen-reader)
-   [Why this matters](#why-this-matters)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Interactive elements indicate their purpose and state
=====================================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Interactive elements, such as links and buttons, should indicate their state and be distinguishable from non-interactive elements. To check that interactive elements indicate their purpose and state, use both a visual and a screen reader test.

How to manually test visual focus <a href="#how-to-manually-test-visual-focus" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

To manually test visual focus, `TAB` through your page.

-   Are you able to tab to each interactive element?
-   When you get to an interactive element, is there a visual clue that users can interact with it?
-   Does each interactive element change in appearance when you select it?

There are many ways to style the focus indicators for each interactive element. One sure way is to use `:focus`. The `:focus` pseudo-class lets you apply a uniform style to an element. That style is applied any time the element is focused, regardless of the input device or method used to focus it.

Learn more in [Style focus](/style-focus).

How to manually test with a screen reader <a href="#how-to-manually-test-with-a-screen-reader" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------

Using a screen reader, navigate your page and check that the screen reader is able to announce the name of each interactive control, the role of that control, and the current interactive state. If the role of an element is unclear, and the state of the element is unclear, you may need to add the appropriate ARIA roles. Learn more in [Custom controls have ARIA roles](/custom-control-roles).

It is also important to pay close attention to how interactive elements are labeled. Users of screen readers and other assistive technologies rely on labels to understand the context of that element. Vague labels are common, and they are non-helpful for navigating content. Learn how to improve [Labels and text alternatives](/labels-and-text-alternatives).

Why this matters <a href="#why-this-matters" class="w-headline-link">#</a>
--------------------------------------------------------------------------

Providing visual hints about what a control will do helps people operate and navigate your site. These hints are called affordances. Providing affordances makes it possible for people to use your site on a wide variety of devices.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

[Source code for **Interactive elements indicate their purpose and state** audit](https://github.com/GoogleChrome/lighthouse/blob/ecd10efc8230f6f772e672cd4b05e8fbc8a3112d/lighthouse-core/audits/accessibility/manual/interactive-element-affordance.js)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/interactive-element-affordance/index.md)

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
