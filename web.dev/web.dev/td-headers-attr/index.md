## <a href="#cells-in-a-lesscodegreaterandlttableandgtlesscodegreater-element-that-use-the-lesscodegreaterheaderslesscodegreater-attribute-refer-to-an-element-id-not-found-within-the-same-table" class="w-toc__header--link">Cells in a <code>&lt;table&gt;</code> element that use the <code>[headers]</code> attribute refer to an element ID not found within the same table</a>

- [How this Lighthouse audit fails](#how-this-lighthouse-audit-fails)
- [How to fix data cells that refer to nonexistent headers](#how-to-fix-data-cells-that-refer-to-nonexistent-headers)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Cells in a `<table>` element that use the `[headers]` attribute refer to an element ID not found within the same table

May 2, 2019 <span class="w-author__separator">•</span> Updated Mar 20, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Screen readers and other assistive technologies announce table headers when they come to each table data cell. If the headers and data cells don't match up, it's very confusing. Every table data cell must relate to the correct table header; therefore, there should only be one table header per column.

## How this Lighthouse audit fails <a href="#how-this-lighthouse-audit-fails" class="w-headline-link">#</a>

Lighthouse flags tables that have more than one table header per column:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RI3y7LU6YECI6AdOw5GC.png?auto=format&amp;w=1600 1600w" width="800" height="227" /></figure>The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to fix data cells that refer to nonexistent headers <a href="#how-to-fix-data-cells-that-refer-to-nonexistent-headers" class="w-headline-link">#</a>

Each table data cell must align with one table header cell.

The following table isn't structured correctly; one column has multiple table headers:

    <table>
      <caption><strong>My marathon training log</strong></caption>
      <thead>
        <tr>
          <th>Week</th>
          <th>Total miles</th>
          <th>Longest run</th>
          <th>Long run pace</th>
        </tr>
      </thead>

      <tbody>
        <tr>
          <th headers="Week">1</th>
          <td>14</td>
          <td>5</td>
          <td>12.30</td>
        </tr>

        <tr>
          <th>1</th>
          <td>16</td>
          <td>6</td>
          <td>12.15</td>
        </tr>

      </tbody>

    </table>

To fix this table, remove `headers="Week"` and apply the `scope` attribute to our header column and table rows.

The `scope` attribute tells the browser and assistive technologies that everything under the column is related to the header at the top, and everything to the right of the row header is related to that header.

Also add the missing `<td>` to the first row in the body, so that the table data aligns correctly with the table headers:

    <table>
      <caption>My marathon training log</caption>
      <thead>
        <tr>
          <th scope="col">Week</th>
          <th scope="col">Total miles</th>
          <th scope="col">Longest run</th>
          <th scope="col">Long run pace</th>
        </tr>
      </thead>

      <tbody>
        <tr>
          <th scope="row">1</th>
          <td>14</td>
          <td>5</td>
          <td>12.30</td>
        </tr>

        <tr>
          <th scope="row">1</th>
          <td>16</td>
          <td>6</td>
          <td>12.15</td>
        </tr>

      </tbody>

    </table>

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Cells in a `<table>` element that use the `[headers]` attribute refer to an element `id` not found within the same table** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/td-headers-attr.js)
- [All cells in a `<table>` element that use the headers attribute must only refer to other cells of that same `<table>` (Deque University)](https://dequeuniversity.com/rules/axe/3.3/td-headers-attr)

<span class="w-mr--sm">Last updated: Mar 20, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/td-headers-attr/index.md)

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
