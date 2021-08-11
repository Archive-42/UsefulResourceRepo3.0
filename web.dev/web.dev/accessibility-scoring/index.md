<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#lighthouse-accessibility-scoring" class="w-toc__header--link">Lighthouse accessibility scoring</a>
------------------------------------------------------------------------------------------------------------

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Lighthouse accessibility scoring
================================

Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

The Lighthouse Accessibility score is a weighted average of all [accessibility audits](/lighthouse-accessibility). Weighting is based on [axe user impact assessments](https://github.com/dequelabs/axe-core/blob/develop/doc/rule-descriptions.md).

Each accessibility audit is pass or fail. Unlike the [Performance audits](/lighthouse-performance), a page doesn't get points for partially passing an accessibility audit. For example, if some buttons on a page have accessible names, but others don't, the page gets a 0 for the [**Buttons do not have an accessible name** audit](/button-name).

The following table shows the weighting for each accessibility audit. More heavily weighted audits have a bigger effect on your score. [Manual audits](/lighthouse-accessibility/#additional-items-to-manually-check) aren't included in the table because they don't affect your score.

<table><thead><tr class="header"><th>Audit</th><th>Weight</th></tr></thead><tbody><tr class="odd"><td><a href="/accesskeys/"><code>[accesskey]</code> values are not unique</a></td><td>3</td></tr><tr class="even"><td><a href="/bypass/">The page does not contain a heading, skip link, or landmark region</a></td><td>3</td></tr><tr class="odd"><td><a href="/duplicate-id-active/"><code>[id]</code> attributes on active, focusable elements are not unique</a></td><td>10</td></tr><tr class="even"><td><a href="/heading-order">Headings skip levels</a></td><td>3</td></tr><tr class="odd"><td><a href="/tabindex/">Some elements have a <code>[tabindex]</code> value greater than <code>0</code></a></td><td>3</td></tr><tr class="even"><td><a href="/aria-allowed-attr/"><code>[aria-*]</code> attributes do not match their roles</a></td><td>10</td></tr><tr class="odd"><td><a href="/aria-hidden-body"><code>[aria-hidden="true"]</code> is present on the document <code>&lt;body&gt;</code></a></td><td>10</td></tr><tr class="even"><td><a href="/aria-hidden-focus"><code>[aria-hidden="true"]</code> elements contain focusable descendants</a></td><td>10</td></tr><tr class="odd"><td><a href="/aria-input-field-name">Not all ARIA input fields have accessible names</a></td><td>10</td></tr><tr class="even"><td><a href="/aria-required-attr/"><code>[role]</code>s do not have all required <code>[aria-*]</code> attributes</a></td><td>10</td></tr><tr class="odd"><td><a href="/aria-required-children/">Elements with an ARIA <code>[role]</code> that require children to contain a specific <code>[role]</code> are missing some or all of those required children</a></td><td>10</td></tr><tr class="even"><td><a href="/aria-required-parent/"><code>[role]</code>s are not contained by their required parent element</a></td><td>10</td></tr><tr class="odd"><td><a href="/aria-roles/"><code>[role]</code> values are not valid</a></td><td>10</td></tr><tr class="even"><td><a href="/aria-toggle-field-name/">Not all ARIA toggle fields have accessible names</a></td><td>10</td></tr><tr class="odd"><td><a href="/aria-valid-attr-value/"><code>[aria-*]</code> attributes do not have valid values</a></td><td>10</td></tr><tr class="even"><td><a href="/aria-valid-attr/"><code>[aria-*]</code> attributes are not valid or misspelled</a></td><td>10</td></tr><tr class="odd"><td><a href="/duplicate-id-aria/">ARIA IDs are not all unique</a></td><td>10</td></tr><tr class="even"><td><a href="/button-name/">Buttons do not have an accessible name</a></td><td>10</td></tr><tr class="odd"><td><a href="/document-title/">Document doesn't have a <code>&lt;title&gt;</code> element</a></td><td>3</td></tr><tr class="even"><td><a href="/form-field-multiple-labels">Form fields have multiple labels</a></td><td>3</td></tr><tr class="odd"><td><a href="/frame-title/"><code>&lt;frame&gt;</code> or <code>&lt;iframe&gt;</code> elements do not have a title</a></td><td>3</td></tr><tr class="even"><td><a href="/image-alt/">Image elements do not have <code>[alt]</code> attributes</a></td><td>10</td></tr><tr class="odd"><td><a href="/input-image-alt/"><code>&lt;input type="image"&gt;</code> elements do not have <code>[alt]</code> text</a></td><td>10</td></tr><tr class="even"><td><a href="/label/">Form elements do not have associated labels</a></td><td>10</td></tr><tr class="odd"><td><a href="/link-name/">Links do not have a discernible name</a></td><td>3</td></tr><tr class="even"><td><a href="/object-alt/"><code>&lt;object&gt;</code> elements do not have <code>[alt]</code> text</a></td><td>3</td></tr><tr class="odd"><td><a href="/color-contrast/">Background and foreground colors do not have a sufficient contrast ratio</a></td><td>3</td></tr><tr class="even"><td><a href="/definition-list/"><code>&lt;dl&gt;</code>s do not contain only properly ordered <code>&lt;dt&gt;</code> and <code>&lt;dd&gt;</code> groups, <code>&lt;script&gt;</code>, or <code>&lt;template&gt;</code> elements</a></td><td>3</td></tr><tr class="odd"><td><a href="/dlitem/">Definition list items are not wrapped in <code>&lt;dl&gt;</code> elements</a></td><td>3</td></tr><tr class="even"><td><a href="/list/">Lists do not contain only <code>&lt;li&gt;</code> elements and script supporting elements (<code>&lt;script&gt;</code> and <code>&lt;template&gt;</code>)</a></td><td>3</td></tr><tr class="odd"><td><a href="/listitem/">List items (<code>&lt;li&gt;</code>) are not contained within <code>&lt;ul&gt;</code> or <code>&lt;ol&gt;</code> parent elements</a></td><td>3</td></tr><tr class="even"><td><a href="/layout-table/">Presentational <code>&lt;table&gt;</code> elements do not avoid using <code>&lt;th&gt;</code>, <code>&lt;caption&gt;</code>, or the <code>[summary]</code> attribute</a></td><td>3</td></tr><tr class="odd"><td><a href="/td-headers-attr/">Cells in a <code>&lt;table&gt;</code> element that use the <code>[headers]</code> attribute refer to an element id not found within the same table</a></td><td>3</td></tr><tr class="even"><td><a href="/th-has-data-cells/"><code>&lt;th&gt;</code> elements and elements with <code>[role="columnheader"/"rowheader"]</code> do not have data cells they describe</a></td><td>3</td></tr><tr class="odd"><td><a href="/meta-refresh/">The document uses <code>&lt;meta http-equiv="refresh"&gt;</code></a></td><td>10</td></tr><tr class="even"><td><a href="/meta-viewport/"><code>[user-scalable="no"]</code> is used in the <code>&lt;meta name="viewport"&gt;</code> element or the <code>[maximum-scale]</code> attribute is less than 5</a></td><td>10</td></tr><tr class="odd"><td><a href="/audio-caption/"><code>&lt;audio&gt;</code> elements are missing a <code>&lt;track&gt;</code> element with <code>[kind="captions"]</code></a></td><td>10</td></tr><tr class="even"><td><a href="/video-caption/"><code>&lt;video&gt;</code> elements do not contain a <code>&lt;track&gt;</code> element with <code>[kind="captions"]</code></a></td><td>10</td></tr><tr class="odd"><td><a href="/video-description/"><code>&lt;video&gt;</code> elements do not contain a <code>&lt;track&gt;</code> element with <code>[kind="description"]</code></a></td><td>10</td></tr><tr class="even"><td><a href="/html-has-lang/"><code>&lt;html&gt;</code> element does not have a <code>[lang]</code> attribute</a></td><td>3</td></tr><tr class="odd"><td><a href="/html-lang-valid/"><code>&lt;html&gt;</code> element does not have a valid value for its <code>[lang]</code> attribute</a></td><td>3</td></tr><tr class="even"><td><a href="/valid-lang/"><code>[lang]</code> attributes do not have a valid value</a></td><td>3</td></tr></tbody></table>

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/accessibility-scoring/index.md)

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
