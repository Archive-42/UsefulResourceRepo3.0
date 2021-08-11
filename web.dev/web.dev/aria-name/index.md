<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#aria-items-do-not-have-accessible-names" class="w-toc__header--link">ARIA items do not have accessible names</a>

- [How Lighthouse identifies ARIA items without accessible names](#how-lighthouse-identifies-aria-items-without-accessible-names)
- [Example 1: How to add accessible names to your custom ARIA toggle fields](#example-1:-how-to-add-accessible-names-to-your-custom-aria-toggle-fields)
- [Option 1: Add inner text to the element](#option-1:-add-inner-text-to-the-element)
- [Option 2: Add an aria-label attribute to the element](#option-2:-add-an-aria-label-attribute-to-the-element)
- [Option 3: Refer to another element using aria-labelledby](#option-3:-refer-to-another-element-using-aria-labelledby)
- [Example 2: How to add accessible names to your custom ARIA input fields](#example-2:-how-to-add-accessible-names-to-your-custom-aria-input-fields)
- [Option 1: Add an aria-label attribute to the element](#option-1:-add-an-aria-label-attribute-to-the-element)
- [Option 2: Refer to another element using aria-labelledby](#option-2:-refer-to-another-element-using-aria-labelledby)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# ARIA items do not have accessible names

Dec 8, 2020

Users of screen readers and other assistive technologies need information about the behavior and purpose of controls on your web page. Built-in HTML controls like buttons and radio groups come with that information [built in](/use-semantic-html). For custom controls you create, however, you must provide the information with [ARIA](https://www.w3.org/TR/wai-aria-1.1/#role_definitions) roles and attributes. (Learn more in the [Introduction to ARIA](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/).)

To be announced properly by assistive technologies, both [built-in HTML controls](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#Forms) and [custom ARIA controls](https://www.w3.org/TR/wai-aria-practices-1.1/#aria_ex) must have [accessible names](/labels-and-text-alternatives) that convey their purpose.

## How Lighthouse identifies ARIA items without accessible names <a href="#how-lighthouse-identifies-aria-items-without-accessible-names" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags custom ARIA items whose names aren't accessible to assistive technologies:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Dnruhkr4IKtq0Pi9Pgny.png?auto=format&amp;w=1600 1600w" width="800" height="259" /></figure>There are 7 audits that check for accessible names, each one covers a different set of [ARIA roles](https://www.w3.org/TR/wai-aria-practices-1.1/#aria_ex). Elements that have any of the following ARIA roles but don't have accessible names will cause this audit to fail:

<table><thead><tr class="header"><th>Audit name</th><th>ARIA roles</th></tr></thead><tbody><tr class="odd"><td><code>aria-command-name</code></td><td><code>button</code>, <code>link</code>, <code>menuitem</code></td></tr><tr class="even"><td><code>aria-input-field-name</code></td><td><code>combobox</code>, <code>listbox</code>, <code>searchbox</code>, <code>slider</code>, <code>spinbutton</code>, <code>textbox</code></td></tr><tr class="odd"><td><code>aria-meter-name</code></td><td><code>meter</code></td></tr><tr class="even"><td><code>aria-progressbar-name</code></td><td><code>progressbar</code></td></tr><tr class="odd"><td><code>aria-toggle-field-name</code></td><td><code>checkbox</code>, <code>menu</code>, <code>menuitemcheckbox</code>, <code>menuitemradio</code>, <code>radio</code>, <code>radiogroup</code>, <code>switch</code></td></tr><tr class="even"><td><code>aria-tooltip-name</code></td><td><code>tooltip</code></td></tr><tr class="odd"><td><code>aria-treeitem-name</code></td><td><code>treeitem</code></td></tr></tbody></table>

**Caution**: Most common input types can be created with standardized HTML elements, which come with built-in behaviors and accessible semantics that can be time consuming to replicate. Consider [using built-in elements](/semantics-and-screen-readers/#use-semantic-html) instead of ARIA roles if possible.

The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## Example 1: How to add accessible names to your custom ARIA toggle fields <a href="#example-1:-how-to-add-accessible-names-to-your-custom-aria-toggle-fields" class="w-headline-link">#</a>

### Option 1: Add inner text to the element <a href="#option-1:-add-inner-text-to-the-element" class="w-headline-link">#</a>

The easiest way to provide an accessible name for most elements is to include text content inside the element.

For example, this custom checkbox will be announced as "Newspaper" to assistive technology users:

    <div id="checkbox1" role="checkbox">Newspaper</div>

Using the [clip pattern](https://www.a11yproject.com/posts/2013-01-11-how-to-hide-content/) you can hide the inner text on screen, but still have it announced by assistive technology. This can be especially handy if you translate your pages for localization.

    <a href="/accessible">Learn more <span class="visually-hidden">about accessibility on web.dev</span></a>

### Option 2: Add an `aria-label` attribute to the element <a href="#option-2:-add-an-aria-label-attribute-to-the-element" class="w-headline-link">#</a>

If you can't add inner text—for example, if you don't want the element's name to be visible—use the `aria-label` attribute.

This custom switch will be announced as "Toggle blue light" to assistive technology users:

    <div id="switch1"
        role="switch"
        aria-checked="true"
        aria-label="Toggle blue light">
        <span>off</span>
        <span>on</span>
    </div>

### Option 3: Refer to another element using `aria-labelledby` <a href="#option-3:-refer-to-another-element-using-aria-labelledby" class="w-headline-link">#</a>

Use the `aria-labelledby` attribute to identify another element, using its ID, to serve as the name for the current element.

For example, this custom menu radio button refers to the `menuitem1Label` paragraph as its label and will be announced as "Sans-serif":

    <p id="menuitem1Label">Sans-serif</p>
    <ul role="menu">
        <li id="menuitem1"
            role="menuitemradio"
            aria-labelledby="menuitem1Label"
            aria-checked="true"></li>
    </ul>

## Example 2: How to add accessible names to your custom ARIA input fields <a href="#example-2:-how-to-add-accessible-names-to-your-custom-aria-input-fields" class="w-headline-link">#</a>

The easiest way to provide an accessible name for most elements is to include text content in the element. However, custom input fields typically don't have inner text, so you can use one of the following strategies instead.

### Option 1: Add an `aria-label` attribute to the element <a href="#option-1:-add-an-aria-label-attribute-to-the-element" class="w-headline-link">#</a>

Use the `aria-label` attribute to define the name for the current element.

For example, this custom combobox will be announced as "country" to assistive technology users:

    <div id="combo1" aria-label="country" role="combobox"></div>

### Option 2: Refer to another element using `aria-labelledby` <a href="#option-2:-refer-to-another-element-using-aria-labelledby" class="w-headline-link">#</a>

Use the `aria-labelledby` attribute to identify another element, using its ID, to serve as the name for the current element.

For example, this custom searchbox refers to the `searchLabel` paragraph as its label and will be announced as "Search currency pairs":

    <p id="searchLabel">Search currency pairs:</p>
    <div id="search"
        role="searchbox"
        contenteditable="true"
        aria-labelledby="searchLabel"></div>

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Not all ARIA toggle fields have accessible names** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/aria-toggle-field-name.js)
- [ARIA button, link, and menuitem must have an accessible name (Deque University)](https://dequeuniversity.com/rules/axe/4.1/aria-command-name)
- [ARIA input fields must have an accessible name (Deque University)](https://dequeuniversity.com/rules/axe/4.1/aria-input-field-name)
- [ARIA meter must have an accessible name (Deque University)](https://dequeuniversity.com/rules/axe/4.1/aria-meter-name)
- [ARIA progressbar must have an accessible name (Deque University)](https://dequeuniversity.com/rules/axe/4.1/aria-progressbar-name)
- [ARIA toggle fields have an accessible name (Deque University)](https://dequeuniversity.com/rules/axe/4.1/aria-toggle-field-label)
- [ARIA tooltip must have an accessible name (Deque University)](https://dequeuniversity.com/rules/axe/4.1/aria-tooltip-name)
- [ARIA treeitem must have an accessible name (Deque University)](https://dequeuniversity.com/rules/axe/4.1/aria-treeitem-name)
- [Labels and text alternatives](/labels-and-text-alternatives)
- [Use semantic HTML for easy keyboard wins](/use-semantic-html)

<a href="/tags/accessibility/" class="w-chip">Accessibility</a>

<span class="w-mr--sm">Last updated: Dec 8, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/aria-name/index.md)

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
