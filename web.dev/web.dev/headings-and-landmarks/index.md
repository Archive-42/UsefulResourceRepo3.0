<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#headings-and-landmarks" class="w-toc__header--link">Headings and landmarks</a>
----------------------------------------------------------------------------------------

-   [Use headings to outline the page](#use-headings-to-outline-the-page)
-   [Don't skip heading levels](#don't-skip-heading-levels)
-   [Use landmarks to aid navigation](#use-landmarks-to-aid-navigation)
-   [Bypass repetitive content with skip links](#bypass-repetitive-content-with-skip-links)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Headings and landmarks
======================

Nov 18, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/accessible" class="w-post-signpost__link">Accessible to all</a>

[<img src="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rob Dodson" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/robdodson/)

<a href="/authors/robdodson/" class="w-author__name-link">Rob Dodson</a>

-   <a href="https://twitter.com/rob_dodson" class="w-author__link">Twitter</a>
-   <a href="https://github.com/robdodson" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@robdodson" class="w-author__link">Glitch</a>
-   <a href="https://robdodson.me" class="w-author__link">Blog</a>

Screen readers have commands to quickly jump between headings or to specific landmark regions. In fact, [a survey of screen reader users](http://www.heydonworks.com/article/responses-to-the-screen-reader-strategy-survey) found that they most often navigate an unfamiliar page by exploring the headings.

By using correct heading and landmark elements, you can dramatically improve the navigation experience on your site for users of assistive technologies.

Use headings to outline the page <a href="#use-headings-to-outline-the-page" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------

Use `h1`-`h6` elements to create a *structural* outline for your page. The goal is to create a skeleton or scaffold of the page such that anyone navigating by headings can form a mental picture.

A common practice is to use a single `h1` for the primary headline or logo on a page, `h2`s to designate major sections, and `h3`'s in supporting subsections:

    <h1>Company name</h1>
    <section>
      <h2>Section Heading</h2>
      …
      <h3>Sub-section Heading</h3>
    </section>

Don't skip heading levels <a href="#don&#39;t-skip-heading-levels" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------

Developers often skip heading levels to use the browser's default styles that closely match their design. This is considered an anti-pattern because it breaks the outline model.

Instead of relying on the browser's default font-sizing for headings, use your own CSS, and don't skip levels.

For example, this site has a section called "IN THE NEWS", followed by two headlines:

<img src="https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format" alt="A news site with a headline, hero image, and subsections." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/CdBjBuUo2yVVHWVFnQzx.png?auto=format&amp;w=1600 1600w" width="800" height="414" />

The section heading, "IN THE NEWS", could be an `h2`, and the supporting headlines could both be `h3`'s.

Because the `font-size` for "IN THE NEWS" is *smaller* than the headline, it may be tempting to make the headline for the first story an `h2` and to make "IN THE NEWS" an `h3`. While that may match the browser's default styling, it would break the outline conveyed to a screen reader user!

Though it may seem counterintuitive, it does not matter if *visually* `h3`'s and `h4`'s are larger than their `h2` or `h1` counterparts. What matters is the outline conveyed by the elements and elements' ordering.

You can use Lighthouse to check if your page skips any heading levels. Run the Accessibility audit (**Lighthouse &gt; Options &gt; Accessibility**) and look for the results of the **Headings don't skip levels** audit.

Use landmarks to aid navigation <a href="#use-landmarks-to-aid-navigation" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------

HTML5 elements such as `main`, `nav`, and `aside` act as **landmarks**, or special regions on the page to which a screen reader can jump.

Use landmark tags to define major sections of your page, instead of relying on `div`s. Be careful not to go overboard because having *too many* landmarks can be overwhelming. For example, stick to just one `main` element instead of 3 or 4.

Lighthouse recommends manually auditing your site to check that "HTML5 landmark elements are used to improve navigation." You can use this [list of landmark elements](https://www.w3.org/TR/2017/NOTE-wai-aria-practices-1.1-20171214/examples/landmarks/HTML5.html) to check your page.

Bypass repetitive content with skip links <a href="#bypass-repetitive-content-with-skip-links" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------

Many sites contain repetitive navigation in their headers, which can be annoying to navigate with assistive technology. Use a **skip link** to let users bypass this content.

A skip link is an offscreen anchor that is always the first focusable item in the DOM. Typically, it contains an in-page link to the main content of the page. Because it is the first element in the DOM, it only takes a single action from assistive technology to focus it and bypass repetitive navigation.

    <!-- index.html -->
    <a class="skip-link" href="#main">Skip to main</a>
    …
    <main id="main">
      [Main content]
    </main>

    /* style.css */
    .skip-link {
      position: absolute;
      top: -40px;
      left: 0;
      background: #000000;
      color: white;
      padding: 8px;
      z-index: 100;
    }

    .skip-link:focus {
      top: 0;
    }

**Try it**! [Live skip link example.](https://skip-link.glitch.me/)

Many popular sites such as [GitHub](https://github.com/), [The NY Times](https://www.nytimes.com/), and [Wikipedia](https://wikipedia.org/) all contain skip links. Try visiting them and pressing the `TAB` key on your keyboard a few times.

Lighthouse can help you check if your page contains a skip link. Run the Accessibility audit again and look for the results of the **The page contains a heading, skip link, or landmark region** audit.

Technically, this test will also pass if your site contains any `h1`-`h6` elements or any of the HTML5 landmark elements. But although the test is vague in its requirements, it's still nice to pass it if you can!

<span class="w-mr--sm">Last updated: Nov 18, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/accessible/headings-and-landmarks/index.md)

<a href="/accessible" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
