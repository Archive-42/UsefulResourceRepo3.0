<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#lesscodegreaterandltthandgtlesscodegreater-elements-and-elements-with-lesscodegreaterroleandquotcolumnheaderandquotandquotrowheaderandquotlesscodegreater-do-not-have-data-cells-they-describe" class="w-toc__header--link"><code>&lt;th&gt;</code> elements and elements with <code>[role="columnheader"/"rowheader"]</code> do not have data cells they describe</a>
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [How this Lighthouse audit fails](#how-this-lighthouse-audit-fails)
-   [How to fix table headers that have no associated data cells](#how-to-fix-table-headers-that-have-no-associated-data-cells)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

`<th>` elements and elements with `[role="columnheader"/"rowheader"]` do not have data cells they describe
==========================================================================================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Screen readers and other assistive technologies have features to make navigating tables easier. Table headers must refer to some set of cells so that assistive technologies can help users navigate tables easily.

How this Lighthouse audit fails <a href="#how-this-lighthouse-audit-fails" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------

Lighthouse flags `<th>` elements and elements with `[role="columnheader"/"rowheader"]` that don't have the data cells they describe:

The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

How to fix table headers that have no associated data cells <a href="#how-to-fix-table-headers-that-have-no-associated-data-cells" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------------------

The following table isn't structured correctly; there's a table header column, "Marathon pace", without table data cells:

    <table>
      <caption>My marathon training log</caption>
      <thead>
        <tr>
          <th scope="col">Week</th>
          <th scope="col">Total miles</th>
          <th scope="col">Longest run</th>
          <th scope="col">Marathon pace</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">1</th>
          <td>14</td>
          <td>5</td>
        </tr>
        <tr>
          <th scope="row">2</th>
          <td>16</td>
          <td>6</td>
        </tr>
      </tbody>
    </table>

To fix this table, add the missing table data cells for the table header column, "Marathon pace":

    <table>
      <caption>My marathon training log</caption>
      <thead>
        <tr>
          <th scope="col">Week</th>
          <th scope="col">Total miles</th>
          <th scope="col">Longest run</th>
          <th scope="col">Marathon pace</th>
        </tr>
      </thead>
      <tbody>
        <tr>
          <th scope="row">1</th>
          <td>14</td>
          <td>5</td>
          <td>4:45:00</td>
        </tr>
        <tr>
          <th scope="row">2</th>
          <td>16</td>
          <td>6</td>
          <td>4:33:00</td>
        </tr>
      </tbody>
    </table>

Assistive technologies announce the table headers when they come to each table data cell. If the headers and data cells don't match up, it's very confusing.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Source code for **`<th>` elements and elements with `[role="columnheader"/"rowheader"]` do not have data cells they describe** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/th-has-data-cells.js)
-   [All `<th>` elements and elements with `role="columnheader"` or `role="rowheader"` must have data cells they describe (Deque University)](https://dequeuniversity.com/rules/axe/3.3/th-has-data-cells)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/th-has-data-cells/index.md)

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
