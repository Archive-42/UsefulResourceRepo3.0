<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

Accessibility audits
====================

Can all users access content and navigate your site effectively?

<img src="https://web-dev.imgix.net/image/jxu1OdD7LKOGIDU7jURMpSH2lyK2/84Wscf0ndzfe8Ri59fsW.svg" alt="Collection cover image" class="w-masthead-path__image" width="330" height="220" />

Overview
--------

These checks highlight opportunities to improve the accessibility of your web app. Only a subset of accessibility issues can be automatically detected so manual testing is also encouraged.

Table of Contents
-----------------

-   <a href="#audit-scoring" class="w-path-link">Audit scoring</a>
-   <a href="#navigation" class="w-path-link">Navigation</a>
-   <a href="#aria" class="w-path-link">ARIA</a>
-   <a href="#names-and-labels" class="w-path-link">Names and labels</a>
-   <a href="#contrast" class="w-path-link">Contrast</a>
-   <a href="#tables-and-lists" class="w-path-link">Tables and lists</a>
-   <a href="#best-practices" class="w-path-link">Best practices</a>
-   <a href="#audio-and-video" class="w-path-link">Audio and video</a>
-   <a href="#internationalization-and-localization" class="w-path-link">Internationalization and localization</a>
-   <a href="#additional-items-to-manually-check" class="w-path-link">Additional items to manually check</a>

------------------------------------------------------------------------

Audit scoring <a href="#audit-scoring" class="w-headline-link">#</a>
--------------------------------------------------------------------

-   <a href="/accessibility-scoring/" class="w-path-link">Lighthouse accessibility scoring</a>

Navigation <a href="#navigation" class="w-headline-link">#</a>
--------------------------------------------------------------

-   <a href="/accesskeys/" class="w-path-link"><code>[accesskey]</code> values are not unique</a>
-   <a href="/bypass/" class="w-path-link">The page does not contain a heading, skip link, or landmark region</a>
-   <a href="/duplicate-id-active/" class="w-path-link"><code>[id]</code> attributes on active, focusable elements are not unique</a>
-   <a href="/heading-order/" class="w-path-link">Heading elements are not in a sequentially-descending order</a>
-   <a href="/tabindex/" class="w-path-link">Some elements have a <code>[tabindex]</code> value greater than <code>0</code></a>

ARIA <a href="#aria" class="w-headline-link">#</a>
--------------------------------------------------

-   <a href="/aria-allowed-attr/" class="w-path-link"><code>[aria-*]</code> attributes do not match their roles</a>
-   <a href="/aria-hidden-body/" class="w-path-link"><code>[aria-hidden="true"]</code> is present on the document <code>&lt;body&gt;</code></a>
-   <a href="/aria-hidden-focus/" class="w-path-link"><code>[aria-hidden="true"]</code> elements contain focusable descendants</a>
-   <a href="/aria-required-attr/" class="w-path-link"><code>[role]</code>s do not have all required <code>[aria-*]</code> attributes</a>
-   <a href="/aria-required-children/" class="w-path-link">Elements with an ARIA <code>[role]</code> that require children to contain a specific <code>[role]</code> are missing some or all of those required children</a>
-   <a href="/aria-required-parent/" class="w-path-link"><code>[role]</code>s are not contained by their required parent element</a>
-   <a href="/aria-roles/" class="w-path-link"><code>[role]</code> values are not valid</a>
-   <a href="/aria-valid-attr-value/" class="w-path-link"><code>[aria-*]</code> attributes do not have valid values</a>
-   <a href="/aria-valid-attr/" class="w-path-link"><code>[aria-*]</code> attributes are not valid or misspelled</a>
-   <a href="/duplicate-id-aria/" class="w-path-link">ARIA IDs are not unique</a>

Names and labels <a href="#names-and-labels" class="w-headline-link">#</a>
--------------------------------------------------------------------------

-   <a href="/button-name/" class="w-path-link">Buttons do not have an accessible name</a>
-   <a href="/document-title/" class="w-path-link">Document doesn't have a <code>&lt;title&gt;</code> element</a>
-   <a href="/form-field-multiple-labels/" class="w-path-link">Form fields have multiple labels</a>
-   <a href="/frame-title/" class="w-path-link"><code>&lt;frame&gt;</code> or <code>&lt;iframe&gt;</code> elements do not have a title</a>
-   <a href="/image-alt/" class="w-path-link">Image elements do not have <code>[alt]</code> attributes</a>
-   <a href="/input-image-alt/" class="w-path-link"><code>&lt;input type="image"&gt;</code> elements do not have <code>[alt]</code> text</a>
-   <a href="/label/" class="w-path-link">Form elements do not have associated labels</a>
-   <a href="/link-name/" class="w-path-link">Links do not have a discernible name</a>
-   <a href="/object-alt/" class="w-path-link"><code>&lt;object&gt;</code> elements do not have <code>[alt]</code> text</a>

Contrast <a href="#contrast" class="w-headline-link">#</a>
----------------------------------------------------------

-   <a href="/color-contrast/" class="w-path-link">Background and foreground colors do not have a sufficient contrast ratio</a>

Tables and lists <a href="#tables-and-lists" class="w-headline-link">#</a>
--------------------------------------------------------------------------

-   <a href="/definition-list/" class="w-path-link"><code>&lt;dl&gt;</code>s do not contain only properly ordered <code>&lt;dt&gt;</code> and <code>&lt;dd&gt;</code> groups, <code>&lt;script&gt;</code>, or <code>&lt;template&gt;</code> elements</a>
-   <a href="/dlitem/" class="w-path-link">Definition list items are not wrapped in <code>&lt;dl&gt;</code> elements</a>
-   <a href="/list/" class="w-path-link">Lists do not contain only <code>&lt;li&gt;</code> elements and script supporting elements (<code>&lt;script&gt;</code> and <code>&lt;template&gt;</code>)</a>
-   <a href="/listitem/" class="w-path-link">List items (<code>&lt;li&gt;</code>) are not contained within <code>&lt;ul&gt;</code> or <code>&lt;ol&gt;</code> parent elements</a>
-   <a href="/layout-table/" class="w-path-link">Presentational <code>&lt;table&gt;</code> elements do not avoid using <code>&lt;th&gt;</code>, <code>&lt;caption&gt;</code>, or the <code>[summary]</code> attribute</a>
-   <a href="/td-headers-attr/" class="w-path-link">Cells in a <code>&lt;table&gt;</code> element that use the <code>[headers]</code> attribute refer to an element ID not found within the same table</a>
-   <a href="/th-has-data-cells/" class="w-path-link"><code>&lt;th&gt;</code> elements and elements with <code>[role="columnheader"/"rowheader"]</code> do not have data cells they describe</a>

Best practices <a href="#best-practices" class="w-headline-link">#</a>
----------------------------------------------------------------------

-   <a href="/meta-refresh/" class="w-path-link">The document uses <code>&lt;meta http-equiv="refresh"&gt;</code></a>
-   <a href="/meta-viewport/" class="w-path-link"><code>[user-scalable="no"]</code> is used in the <code>&lt;meta name="viewport"&gt;</code> element or the <code>[maximum-scale]</code> attribute is less than <code>5</code></a>

Audio and video <a href="#audio-and-video" class="w-headline-link">#</a>
------------------------------------------------------------------------

-   <a href="/audio-caption/" class="w-path-link"><code>&lt;audio&gt;</code> elements are missing a <code>&lt;track&gt;</code> element with <code>[kind="captions"]</code></a>
-   <a href="/video-caption/" class="w-path-link"><code>&lt;video&gt;</code> elements do not contain a <code>&lt;track&gt;</code> element with <code>[kind="captions"]</code></a>
-   <a href="/video-description/" class="w-path-link"><code>&lt;video&gt;</code> elements do not contain a <code>&lt;track&gt;</code> element with <code>[kind="description"]</code></a>

Internationalization and localization <a href="#internationalization-and-localization" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------

-   <a href="/html-has-lang/" class="w-path-link"><code>&lt;html&gt;</code> element does not have a <code>[lang]</code> attribute</a>
-   <a href="/html-lang-valid/" class="w-path-link"><code>&lt;html&gt;</code> element does not have a valid value for its <code>[lang]</code> attribute</a>
-   <a href="/valid-lang/" class="w-path-link"><code>[lang]</code> attributes do not have a valid value</a>

Additional items to manually check <a href="#additional-items-to-manually-check" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------

-   <a href="/logical-tab-order/" class="w-path-link">The page has a logical tab order</a>
-   <a href="/focusable-controls/" class="w-path-link">Interactive controls are keyboard focusable</a>
-   <a href="/interactive-element-affordance/" class="w-path-link">Interactive elements indicate their purpose and state</a>
-   <a href="/managed-focus/" class="w-path-link">The user's focus is directed to new content added to the page</a>
-   <a href="/focus-traps/" class="w-path-link">User focus is not accidentally trapped in a region</a>
-   <a href="/custom-controls-labels/" class="w-path-link">Custom controls have associated labels</a>
-   <a href="/custom-control-roles/" class="w-path-link">Custom controls have ARIA roles</a>
-   <a href="/visual-order-follows-dom/" class="w-path-link">Visual order on the page follows DOM order</a>
-   <a href="/offscreen-content-hidden/" class="w-path-link">Offscreen content is hidden from assistive technology</a>
-   <a href="/use-landmarks/" class="w-path-link">HTML5 landmark elements are used to improve navigation</a>

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
