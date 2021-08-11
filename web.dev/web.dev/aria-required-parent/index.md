<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#lesscodegreaterrolelesscodegreaters-are-not-contained-by-their-required-parent-element" class="w-toc__header--link"><code>[role]</code>s are not contained by their required parent element</a>
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [How Lighthouse identifies missing parent roles](#how-lighthouse-identifies-missing-parent-roles)
-   [How to add missing parent roles](#how-to-add-missing-parent-roles)
-   [Option 1: Place the child elements within the parent in the DOM](#option-1:-place-the-child-elements-within-the-parent-in-the-dom)
-   [Option 2: Associate the child roles with the parent role using aria-owns](#option-2:-associate-the-child-roles-with-the-parent-role-using-aria-owns)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

`[role]`s are not contained by their required parent element
============================================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Users of screen readers and other assistive technologies need information about the behavior and purpose of controls on your web page. Built-in HTML controls like buttons and radio groups come with that information [built in](/use-semantic-html). For custom controls you create, however, you must provide the information with [ARIA](https://www.w3.org/TR/wai-aria-1.1/#role_definitions) roles and attributes. (Learn more in the [Introduction to ARIA](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/).)

Some ARIA roles must be owned by specific parent roles. For example, the `tab` role must have an element with the `tablist` role as a parent. If the required parent role isn't present, assistive technologies may announce the child roles as plain text content rather than the intended control.

How Lighthouse identifies missing parent roles <a href="#how-lighthouse-identifies-missing-parent-roles" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse) flags ARIA child roles that aren't contained by the required parent:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ENzj3jYUVvSR3n23aC6M.png?auto=format&amp;w=1600 1600w" width="800" height="206" /></figure>Lighthouse uses the [role definitions from the WAI-ARIA specification](https://www.w3.org/TR/wai-aria-1.1/#role_definitions) to check for [required context roles](https://www.w3.org/TR/wai-aria/#scope)—that is, required parent roles. A page fails this audit when it contains a child role that's missing its required parent role.

In the example Lighthouse audit above, the `listitem` role requires a parent `group` or `list`. Since there's no parent role defined, the audit fails. This makes sense, as it would be confusing to have a list item that isn't part of a list.

This issue is important to fix and may break the experience for users. In the example above, the element would be announced as plain text content, and its `listitem` role would be ignored.

The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

How to add missing parent roles <a href="#how-to-add-missing-parent-roles" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------

Refer to the [WAI-ARIA role definitions](https://www.w3.org/TR/wai-aria-1.1/#role_definitions) to see which parent roles are required for the elements that Lighthouse flagged. (The spec refers to required parents as [required context roles](https://www.w3.org/TR/wai-aria/#scope).)

There are two ways to set up the required relationships between ARIA parent and child roles.

### Option 1: Place the child elements within the parent in the DOM <a href="#option-1:-place-the-child-elements-within-the-parent-in-the-dom" class="w-headline-link">#</a>

Placing elements with child roles within the parent role element in your HTML is usually the easiest and most maintainable solution. For example:

    <div role="tablist">
     <button role="tab" aria-selected="true" aria-controls="tab-1-pane" active>
          Tab 1
       </button>
        <button role="tab" aria-selected="false" tabindex="-1" aria-controls="tab-2-pane">
           Tab 2
       </button>
        <button role="tab" aria-selected="false" tabindex="-1" aria-controls="tab-3-pane">
           Tab 3
       </button>
    </div>

### Option 2: Associate the child roles with the parent role using `aria-owns` <a href="#option-2:-associate-the-child-roles-with-the-parent-role-using-aria-owns" class="w-headline-link">#</a>

If you can't place child role elements inside the parent role element, you can use the `aria-owns` attribute to associate them:

    <div role="tablist" aria-owns="tab-1 tab-2 tab-3"></div>
    …
    <button id="tab-1" role="tab" aria-selected="true" aria-controls="tab-1-pane" active>
      Tab 1
    </button>
    <button id="tab-2" role="tab" aria-selected="false" tabindex="-1" aria-controls="tab-2-pane">
      Tab 2
    </button>
    <button id="tab-3" role="tab" aria-selected="false" tabindex="-1" aria-controls="tab-3-pane">
      Tab 3
    </button>

If an element with the `aria-owns` attribute contains DOM children, assistive technologies will announce the DOM children before the elements listed in `aria-owns`.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **`[role]`s are not contained by their required parent element** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/aria-required-parent.js)
-   [Certain ARIA roles must be contained by particular parent elements (Deque University)](https://dequeuniversity.com/rules/axe/3.3/aria-required-parent)
-   [Role definitions from the WAI-ARIA specification](https://www.w3.org/TR/wai-aria-1.1/#role_definitions)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/aria-required-parent/index.md)

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
