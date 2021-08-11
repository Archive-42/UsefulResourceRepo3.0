<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#html5-landmark-elements-are-used-to-improve-navigation" class="w-toc__header--link">HTML5 landmark elements are used to improve navigation</a>
--------------------------------------------------------------------------------------------------------------------------------------------------------

-   [How to manually check landmarks](#how-to-manually-check-landmarks)
-   [How to use landmarks effectively](#how-to-use-landmarks-effectively)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

HTML5 landmark elements are used to improve navigation
======================================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

HTML5 elements such as `main`, `nav`, and `aside` act as landmarks, or special regions on the page to which screen readers and other assistive technologies can jump. By using landmark elements, you can dramatically improve the navigation experience on your site for users of assistive technology. Learn more in Deque University's [HTML 5 and ARIA Landmarks](https://dequeuniversity.com/assets/html/jquery-summit/html5/slides/landmarks.html).

How to manually check landmarks <a href="#how-to-manually-check-landmarks" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------

Use [the W3C's list of landmark elements](https://www.w3.org/TR/2017/NOTE-wai-aria-practices-1.1-20171214/examples/landmarks/HTML5.html) to check that each major section of your page is contained by a landmark element. For example:

    <header>
      <p>Put product name and logo here</p>
    </header>
    <nav>
      <ul>
        <li>Put navigation here</li>
      </ul>
    </nav>
    <main>
      <p>Put main content here</p>
    </main>
    <footer>
      <p>Put copyright info, supplemental links, etc. here</p>
    </footer>

You can also use tools like Microsoft's [Accessibility Insights extension](https://accessibilityinsights.io/) to visualize your page structure and catch sections that aren't contained in landmarks:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EUH3Yz64EbuAI0GKQoWa.png?auto=format&amp;w=1600 1600w" width="800" height="534" /></figure>How to use landmarks effectively <a href="#how-to-use-landmarks-effectively" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------

-   Use landmark elements to define major sections of your page instead of relying on generic elements like `<div>` or `<span>`.
-   Use landmarks to convey the structure of your page. For example, the `<main>` element should include all content directly related to the page's main idea, so there should only be one per page. See [MDN's summary of content sectioning elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#Content_sectioning) to learn how to use each landmark.
-   Use landmarks judiciously. Having too many landmarks can actually make navigation *more* difficult for assistive technology users because it prevents them from easily skipping to a desired piece of content.

If you find that your page has, for example, four `<nav>` elements or ten `<aside>` elements, that may suggest a need to simplify your user interface or content structure, which will likely benefit *all* users.

See the [Headings and landmarks](/headings-and-landmarks) post for more information.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **HTML5 landmark elements are used to improve navigation** audit](https://github.com/GoogleChrome/lighthouse/blob/ecd10efc8230f6f772e672cd4b05e8fbc8a3112d/lighthouse-core/audits/accessibility/manual/use-landmarks.js)
-   [HTML5 Sectioning Elements (W3C)](https://www.w3.org/TR/2017/NOTE-wai-aria-practices-1.1-20171214/examples/landmarks/HTML5.html)
-   [HTML 5 and ARIA Landmarks (Deque University)](https://dequeuniversity.com/assets/html/jquery-summit/html5/slides/landmarks.html)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/use-landmarks/index.md)

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
