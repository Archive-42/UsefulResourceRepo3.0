## <a href="#form-elements-do-not-have-associated-labels" class="w-toc__header--link">Form elements do not have associated labels</a>

- [How this Lighthouse audit fails](#how-this-lighthouse-audit-fails)
- [How to add labels to form elements](#how-to-add-labels-to-form-elements)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Form elements do not have associated labels

May 2, 2019 <span class="w-author__separator">•</span> Updated Mar 20, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Labels ensure that form controls are announced properly by assistive technologies like screen readers. Assistive technology users rely on these labels to navigate forms. Mouse and touchscreen users also benefit from labels because the label text makes a larger click target.

## How this Lighthouse audit fails <a href="#how-this-lighthouse-audit-fails" class="w-headline-link">#</a>

Lighthouse flags form elements that don't have associated labels:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMWt5UyiUUskhKHUcYoN.png?auto=format&amp;w=1600 1600w" width="800" height="185" /></figure>The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to add labels to form elements <a href="#how-to-add-labels-to-form-elements" class="w-headline-link">#</a>

There are two ways to associate a label with a form element. Either place the input element inside a label element:

    <label>
      Receive promotional offers?
      <input type="checkbox">
    </label>

Or use the label's `for` attribute and refer to the element's ID:

    <input id="promo" type="checkbox">
    <label for="promo">Receive promotional offers?</label>

When the checkbox has been labeled correctly, assistive technologies report that the element has a role of checkbox, is in a checked state, and is named "Receive promotional offers?" See also [Label form elements](/labels-and-text-alternatives#label-form-elements).

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Form elements do not have associated labels** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/label.js)
- [Form `<input>` elements must have labels (Deque University)](https://dequeuniversity.com/rules/axe/3.3/label)

<span class="w-mr--sm">Last updated: Mar 20, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/label/index.md)

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
