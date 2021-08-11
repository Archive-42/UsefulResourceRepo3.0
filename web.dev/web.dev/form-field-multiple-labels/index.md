



## <a href="#form-fields-have-multiple-labels" class="w-toc__header--link">Form fields have multiple labels</a>

- [How the Lighthouse multiple label audit fails](#how-the-lighthouse-multiple-label-audit-fails)
- [How to remove duplicate form labels](#how-to-remove-duplicate-form-labels)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Form fields have multiple labels

Oct 17, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

To be announced properly by assistive technologies, both [built-in HTML controls](https://developer.mozilla.org/en-US/docs/Web/HTML/Element#Forms) and [custom ARIA controls](https://www.w3.org/TR/wai-aria-practices-1.1/#aria_ex) must have [accessible names](/labels-and-text-alternatives) that convey their purpose.

`<label>` elements are a common way to assign names to controls. If you unintentionally associate multiple labels with a single control, you'll create inconsistent behavior across browsers and assistive technologies: some will read the first label, some will read the last label, and others will read both labels.

## How the Lighthouse multiple label audit fails <a href="#how-the-lighthouse-multiple-label-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags form elements that have more than one label:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XO2Y33NoSzSis8zNH8kv.png?auto=format&amp;w=1600 1600w" width="800" height="259" /></figure>There are several common scenarios that cause this audit to fail:

- Explicitly associating more than one `<label>` element with a form element using the `for` attribute. For example:

      <label for="checkbox1">Label one</label>
      <label for="checkbox1">Label two</label>
      <input type="checkbox" id="checkbox1" />

- Implicitly associating one `<label>` element with a form element and explicitly associating another using the `for` attribute. For example:

      <label for="checkbox1">Label one</label>
      <label>Label two
        <input type="checkbox" id="checkbox1" />
      </label>

- Associating one `<label>` element with a form element and associating another element using the `aria-labelledby` attribute. For example:

      <label for="checkbox1">Label one</label>
      <p id="checkbox1_label">Label two</p>
      <input type="checkbox" id="checkbox1" aria-labelledby="checkbox1_label" />

- Having nested `<label>` elements. For example:

      <label>Label one
        <label>Label two
          <input type="checkbox" id="checkbox1" />
        </label>
      </label>

The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to remove duplicate form labels <a href="#how-to-remove-duplicate-form-labels" class="w-headline-link">#</a>

Make sure that each form element on your page has no more than one label. Labels can be assigned in three ways:

- Implicitly, by making the `<label>` element a parent of the form element:

      <label>Label for checkbox
        <input type="checkbox" id="checkbox1" />
      </label>

- Explicitly, by associating a `<label>` element with the form element using the `for` attribute:

      <label for="checkbox1">Label for checkbox</label>
      <input type="checkbox" id="checkbox1" />

- Using the `aria-labelledby` attribute to associate the form element with a separate element using its ID:

      <p id="checkbox1_label">Label for checkbox</p>
      <input type="checkbox" id="checkbox1" aria-labelledby="checkbox1_label" />

Verify that you're using only one of these techniques for each form element.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Form fields have multiple labels** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/form-field-multiple-labels.js)
- [Form fields do not have duplicate labels (Deque University)](https://dequeuniversity.com/rules/axe/3.3/form-field-multiple-labels)

<span class="w-mr--sm">Last updated: Oct 17, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/form-field-multiple-labels/index.md)

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
