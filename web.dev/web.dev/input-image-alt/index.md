<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#lesscodegreaterandltinput-typeandquotimageandquotandgtlesscodegreater-elements-do-not-have-lesscodegreateraltlesscodegreater-text" class="w-toc__header--link"><code>&lt;input type="image"&gt;</code> elements do not have <code>[alt]</code> text</a>
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [How this Lighthouse audit fails](#how-this-lighthouse-audit-fails)
-   [How to add alternative text to image inputs](#how-to-add-alternative-text-to-image-inputs)
-   [Tips for writing effective alt text](#tips-for-writing-effective-alt-text)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

`<input type="image">` elements do not have `[alt]` text
========================================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

When an image is being used as an `<input>` button, providing alternative text helps users of screen readers and other assistive technologies understand the purpose of the button.

How this Lighthouse audit fails <a href="#how-this-lighthouse-audit-fails" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------

Lighthouse flags `<input type="image">` elements that don't have `alt` text:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3uac0DpUpqJCobLSo2Cy.png?auto=format&amp;w=1600 1600w" width="800" height="206" /></figure>The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

How to add alternative text to image inputs <a href="#how-to-add-alternative-text-to-image-inputs" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------

Provide an `alt` attribute for every `<input type="image">` element. Describe the action that occurs when the user clicks on the button in the `alt` text:

    <form>
      <label>
        Username:
        <input type="text">
      </label>
      <input type="image" alt="Sign in" src="./sign-in-button.png">
    </form>

See the [Include text alternatives for images and objects](/labels-and-text-alternatives#include-text-alternatives-for-images-and-objects) post for more information.

You can also use ARIA labels to describe your image buttons.

For example: `<input type="image" aria-label="Sign in">`

See also [Using the aria-label attribute](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-label_attribute) and [Using the aria-labelledby attribute](https://developer.mozilla.org/en-US/docs/Web/Accessibility/ARIA/ARIA_Techniques/Using_the_aria-labelledby_attribute).

Tips for writing effective `alt` text <a href="#tips-for-writing-effective-alt-text" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------

-   As previously mentioned, describe the action that occurs when the user clicks on the button.
-   `alt` text should give the intent, purpose, and meaning of the image.
-   Blind users should get as much information from alt text as a sighted user gets from the image.
-   Avoid non-specific words like "chart", "image", or "diagram".

Learn more in [WebAIM's guide to Alternative Text](https://webaim.org/techniques/alttext/).

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **`<input type="image">` elements do not have `[alt]` text** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/input-image-alt.js)
-   [Image buttons must have alternate text (Deque University)](https://dequeuniversity.com/rules/axe/3.3/input-image-alt)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/input-image-alt/index.md)

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