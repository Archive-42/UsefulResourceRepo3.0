<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#the-user&#39;s-focus-is-directed-to-new-content-added-to-the-page" class="w-toc__header--link">The user's focus is directed to new content added to the page</a>
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [How to manually test](#how-to-manually-test)
-   [How to fix](#how-to-fix)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

The user's focus is directed to new content added to the page
=============================================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Whenever new content is added to a page, try to ensure the user's focus gets directed to that content, so they can take action on it.

How to manually test <a href="#how-to-manually-test" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

Single-page apps are important to test, especially when it comes to managing a user's focus to new content.

Typically in a single-page app, clicking on a link won't do a hard refresh. Instead, a route change fetches new data for the `<main>` content area.

For sighted users, this works fine. But users navigating with a screen reader or other assistive technology may not know that the new content has been added to the page. There's no indication that they should navigate back to the `<main>` area.

When this happens, you'll want to manage the user's focus to keep the user's perceived context in sync with the site's visual content.

How to fix <a href="#how-to-fix" class="w-headline-link">#</a>
--------------------------------------------------------------

To manage a user's focus to fresh content on a page, find a good heading in the newly loaded content and direct focus to it. The easiest way to pull this off is to give the heading a `tabindex` of `-1` and call its `focus()` method:

    <main>
      <h2 tabindex="-1">Welcome to your shopping cart</h2>
    </main>
    <script>
      // Assuming this gets called every time new content loads...
      function onNewPage() {
        var heading = document.querySelector('h2');
        heading.focus();
        // You can also update the page title :)
        document.title = heading.textContent;
      }
    </script>

Assistive technologies announce the new heading and the main landmark area that it's contained in.

See also [Managing focus for accessibility](https://dev.to/robdodson/managing-focus-64l).

You probably don't want to do this focus management when a user first arrives at your site. Only implement this for subsequent navigation, like when they click a link.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

[Source code for **The user's focus is directed to new content added to the page** audit](https://github.com/GoogleChrome/lighthouse/blob/ecd10efc8230f6f772e672cd4b05e8fbc8a3112d/lighthouse-core/audits/accessibility/manual/managed-focus.js)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/managed-focus/index.md)

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
