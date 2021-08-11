





## <a href="#lesscodegreateraria-hiddenandquottrueandquotlesscodegreater-is-present-on-the-document-lesscodegreaterandltbodyandgtlesscodegreater" class="w-toc__header--link"><code>[aria-hidden="true"]</code> is present on the document <code>&lt;body&gt;</code></a>

- [How Lighthouse identifies hidden body elements](#how-lighthouse-identifies-hidden-body-elements)
- [How to make your page accessible to assistive technology users](#how-to-make-your-page-accessible-to-assistive-technology-users)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# `[aria-hidden="true"]` is present on the document `<body>`

Oct 17, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Users of screen readers and other assistive technologies need information about the behavior and purpose of controls on your web page. Built-in HTML controls like buttons and radio groups come with that information [built in](/use-semantic-html). For custom controls you create, however, you must provide the information with [ARIA](https://www.w3.org/TR/wai-aria-1.1/#role_definitions) roles and attributes. (Learn more in the [Introduction to ARIA](https://developers.google.com/web/fundamentals/accessibility/semantics-aria/).)

Screen readers and other assistive technologies don't announce content that's marked as hidden. Applying the `aria-hidden="true"` attribute to your `<body>` element hides your entire web page from assistive technology users.

## How Lighthouse identifies hidden body elements <a href="#how-lighthouse-identifies-hidden-body-elements" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse) flags pages whose `<body>` element has an `aria-hidden="true"` attribute:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/enyVVcLr73lIw7qMyndR.png?auto=format&amp;w=1600 1600w" width="800" height="206" /></figure>The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to make your page accessible to assistive technology users <a href="#how-to-make-your-page-accessible-to-assistive-technology-users" class="w-headline-link">#</a>

Remove the `aria-hidden="true"` attribute from the `<body>` element of your page.

One reason developers mistakenly hide the body element is to prevent assistive technologies from announcing the main content of a page while a [modal dialog](https://www.w3.org/TR/wai-aria-practices-1.1/#dialog_modal) is open. However, hiding the body hides _all_ page content from assistive technology users, including the dialog.

A better solution is to apply the `aria-hidden` attribute to a lower-level container element while the dialog is open. For example, this sample hides the `<main>` element, which precedes the dialog in the HTML:

    <!DOCTYPE html>
    <html lang="en">
      <head>
        …
      </head>
      <body>
        <main aria-hidden="true">
          <h1>Page title</h1>
          <p>Main page content</p>
        </main>
        <div class="dialog" role="dialog" aria-modal="true" aria-label="Sample dialog">
          <p>Sample dialog content</p>
          <button>Close dialog</button>
        </div>
      </body>
    </html>

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **`[aria-hidden="true"]` is present on the document `<body>`** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/aria-hidden-body.js)
- [aria-hidden="true" must not be present on the document &lt;body&gt; (Deque University)](https://dequeuniversity.com/rules/axe/3.3/aria-hidden-body)

<span class="w-mr--sm">Last updated: Oct 17, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/aria-hidden-body/index.md)

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
