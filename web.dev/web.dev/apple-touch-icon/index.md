## <a href="#does-not-provide-a-valid-apple-touch-icon" class="w-toc__header--link">Does not provide a valid apple-touch-icon</a>

- [How the Lighthouse Apple touch icon audit fails](#how-the-lighthouse-apple-touch-icon-audit-fails)
- [How to add an Apple touch icon](#how-to-add-an-apple-touch-icon)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Does not provide a valid apple-touch-icon

Aug 27, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

When iOS Safari users add [Progressive Web Apps (PWAs)](/discover-installable) to their home screens, the icon that appears is called the _Apple touch icon_. You can specify what icon your app should use by including a `<link rel="apple-touch-icon" href="/example.png">` tag in the `<head>` of your page. If your page doesn't have this link tag, iOS generates an icon by taking a screenshot of the page content. In other words, instructing iOS to download an icon results in a more polished user experience.

## How the Lighthouse Apple touch icon audit fails <a href="#how-the-lighthouse-apple-touch-icon-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages without a `<link rel="apple-touch-icon" href="/example.png">` tag in the `<head>`:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mXGs4XSr4DXMxLk536wo.png?auto=format&amp;w=1600 1600w" width="800" height="95" /></figure>A `rel="apple-touch-icon-precomposed"` link passes the audit, but it has been obsolete since iOS 7. Use `rel="apple-touch-icon"` instead.

Lighthouse doesn't check whether the icon actually exists or whether the icon is the correct size.

In the Lighthouse report UI the full PWA badge is given when you pass all of the audits in all of the PWA subcategories (**Fast and reliable**, **Installable**, and **PWA optimized**).

## How to add an Apple touch icon <a href="#how-to-add-an-apple-touch-icon" class="w-headline-link">#</a>

1.  Add `<link rel="apple-touch-icon" href="/example.png">` to the `<head>` of your page:

        <!DOCTYPE html>
        <html lang="en">
          <head>
            …
            <link rel="apple-touch-icon" href="/example.png">
            …
          </head>
          …

2.  Replace `/example.png` with the actual path to your icon.

**Try it**! Check out the [Add an Apple touch icon to your Progressive Web App](/codelab-apple-touch-icon) codelab to see how adding an Apple touch icon creates a more polished user experience.

To provide a good user experience, make sure that:

- The icon is 180x180 pixels or 192x192 pixels
- The specified path to the icon is valid
- The background of the icon is not transparent

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Does not provide a valid `apple-touch-icon`** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/apple-touch-icon.js)
- [Discover what it takes to be installable](/install-criteria)
- [Use Apple Touch Icon](https://webhint.io/docs/user-guide/hints/hint-apple-touch-icons/)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/apple-touch-icon/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-apple-touch-icon/" class="w-callout__link w-callout__link--codelab">Add an Apple touch icon to your Progressive Web App</a>

<a href="/lighthouse-pwa" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
