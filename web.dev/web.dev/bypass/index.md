





## <a href="#the-page-does-not-contain-a-heading-skip-link-or-landmark-region" class="w-toc__header--link">The page does not contain a heading, skip link, or landmark region</a>

- [How this Lighthouse audit fails](#how-this-lighthouse-audit-fails)
- [How to improve keyboard navigation](#how-to-improve-keyboard-navigation)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# The page does not contain a heading, skip link, or landmark region

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

For users who cannot use a mouse, content that's repeated on pages across your site can make navigation difficult. For example, screen reader users may have to move through many links in a navigation menu to get to the main content of the page.

Providing a way to bypass repetitive content makes non-mouse navigation easier.

## How this Lighthouse audit fails <a href="#how-this-lighthouse-audit-fails" class="w-headline-link">#</a>

Lighthouse flags pages that don't provide a way to skip repetitive content:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/fJBo4Nbmlks8cj5i2UMJ.png?auto=format&amp;w=1600 1600w" width="800" height="185" /></figure>Lighthouse checks that the page contains at least one of the following:

- A `<header>` element
- A [skip link](/headings-and-landmarks#bypass-repetitive-content-with-skip-links)
- A [landmark](/headings-and-landmarks/#use-landmarks-to-aid-navigation)

The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to improve keyboard navigation <a href="#how-to-improve-keyboard-navigation" class="w-headline-link">#</a>

Passing the Lighthouse audit is straightforward: add a heading, a [skip link](/headings-and-landmarks#bypass-repetitive-content-with-skip-links), or a [landmark](/headings-and-landmarks/#use-landmarks-to-aid-navigation) to your page.

However, to meaningfully improve the navigational experience for assistive technology users,

- Place all page content inside a landmark element.
- Make sure each landmark accurately reflects the kind of content it contains.
- Provide a skip link.

While most screen readers allow users to navigate by landmarks, other assistive technologies, like [switch devices](https://en.wikipedia.org/wiki/Switch_access), only allow users to move through each element in the tab order one at a time. So, it's important to provide both landmarks and skip links whenever possible.

In this example, all content is inside a landmark, the headings create an outline of the page's content, no headings are skipped, and a skip link is provided to skip the navigation menu:

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <title>Document title</title>
        <meta charset="utf-8">
        <meta http-equiv="X-UA-Compatible" content="IE=edge">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="/style.css">
      </head>
      <body>
        <a class="skip-link" href="#maincontent">Skip to main</a>
        <h1>Page title</h1>
        <nav>
          <ul>
            <li>
              <a href="https://google.com">Nav link</a>
              <a href="https://google.com">Nav link</a>
              <a href="https://google.com">Nav link</a>
            </li>
          </ul>
        </nav>
        <main id="maincontent">
          <section>
            <h2>Section heading</h2>
            <p>
                Bacon ipsum dolor amet brisket meatball chicken, cow hamburger pork belly
               alcatra pig chuck pork loin jerky beef tri-tip porchetta shank. Kevin porchetta
             landjaeger, ribeye bacon strip steak pork chop tenderloin andouille.
              </p>
            <h3>Sub-section heading</h3>
              <p>
                Prosciutto pork chicken chuck turkey tongue landjaeger shoulder picanha capicola
                ball tip meatball strip steak venison salami. Shoulder frankfurter short ribs
                ham hock, ball tip pork chop tenderloin beef ribs pastrami filet mignon.
              </p>
          </section>
        </main>
      </body>
    </html>

You usually don't want to show the skip link to mouse users, so it's conventional to use CSS to hide it offscreen until it receives [focus](/keyboard-access/#focus-and-the-tab-order):

    /* style.css */
    .skip-link {
      position: absolute;
      top: -40px;
      left: 0;
      background: #000000;
      color: white;
      padding: 8px;
      z-index: 100;
    }

    .skip-link:focus {
      top: 0;
    }

See the [Headings and landmarks](/headings-and-landmarks) post for more information.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **The page does not contain a heading, skip link, or landmark region** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/bypass.js)
- [Page must have means to bypass repeated blocks (Deque University)](https://dequeuniversity.com/rules/axe/3.3/bypass)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/bypass/index.md)

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
