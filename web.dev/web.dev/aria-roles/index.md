<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#lesscodegreaterrolelesscodegreater-values-are-not-valid" class="w-toc__header--link"><code>[role]</code> values are not valid</a>
-------------------------------------------------------------------------------------------------------------------------------------------

-   [How Lighthouse determines an ARIA role has an invalid value](#how-lighthouse-determines-an-aria-role-has-an-invalid-value)
-   [How to fix invalid ARIA role values](#how-to-fix-invalid-aria-role-values)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

`[role]` values are not valid
=============================

May 2, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Users of screen readers and other assistive technologies need information about the behavior and purpose of controls on your web page. Built-in HTML controls like buttons and radio groups come with that information [built in](/use-semantic-html). For custom controls you create, however, you must provide the information with [ARIA](https://www.w3.org/TR/wai-aria-1.1/#role_definitions) roles and attributes. (Learn more in the [Introduction to ARIA](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/).)

The ARIA specification includes a [defined set of roles](https://www.w3.org/TR/wai-aria-1.1/#role_definitions). When the value for an element's `role` attribute doesn't match a role from the set, assistive technologies can't announce the element correctly or interact with it as the developer intended.

How Lighthouse determines an ARIA role has an invalid value <a href="#how-lighthouse-determines-an-aria-role-has-an-invalid-value" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse) flags ARIA roles with invalid values:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8Qd5Rfq5WUWJa1ZF6z0A.png?auto=format&amp;w=1600 1600w" width="800" height="185" /></figure>Lighthouse uses the [role definitions from the WAI-ARIA specification](https://www.w3.org/TR/wai-aria-1.1/#role_definitions) to check that all `role` attributes have valid values. A page fails this audit when it contains an element with an invalid `role` value. In the example Lighthouse audit above, `button` has been misspelled as `buton`, which isn't a valid role value.

The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

How to fix invalid ARIA role values <a href="#how-to-fix-invalid-aria-role-values" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------

Refer to the [WAI-ARIA role definitions](https://www.w3.org/TR/wai-aria-1.1/#role_definitions) to see the full list of valid roles. Make sure all `role` attributes are set to a value in the definitions list.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **`[role]` values are not valid** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/aria-roles.js)
-   [ARIA roles used must conform to valid values (Deque University)](https://dequeuniversity.com/rules/axe/3.3/aria-roles)
-   [Role definitions from the WAI-ARIA specification](https://www.w3.org/TR/wai-aria-1.1/#role_definitions)

<span class="w-mr--sm">Last updated: May 2, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/aria-roles/index.md)

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
