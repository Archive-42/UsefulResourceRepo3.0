## <a href="#does-not-redirect-http-traffic-to-https" class="w-toc__header--link">Does not redirect HTTP traffic to HTTPS</a>

- [How the Lighthouse HTTP redirection audit fails](#how-the-lighthouse-http-redirection-audit-fails)
- [How to redirect HTTP traffic to HTTPS](#how-to-redirect-http-traffic-to-https)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Does not redirect HTTP traffic to HTTPS

May 4, 2019 <span class="w-author__separator">•</span> Updated Jun 10, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

All sites should be protected with HTTPS. See the [Does not use HTTPS](/is-on-https) post to learn why and how to set up HTTPS on your server.

## How the Lighthouse HTTP redirection audit fails <a href="#how-the-lighthouse-http-redirection-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages that aren't redirected to HTTPS:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BcRkqleQD9k31nfWZy2z.png?auto=format&amp;w=1600 1600w" width="800" height="95" /></figure>Lighthouse changes the page's URL to HTTP, loads the page, and then waits for the event from the [Chrome Remote Debugging Protocol](https://github.com/ChromeDevTools/devtools-protocol) that indicates that the page is secure. If Lighthouse doesn't receive the event within 10 seconds, the audit fails.

## How to redirect HTTP traffic to HTTPS <a href="#how-to-redirect-http-traffic-to-https" class="w-headline-link">#</a>

Once you've set up HTTPS, make sure that all unsecure HTTP traffic to your site is redirected to HTTPS:

- Use [canonical links](/canonical) in the head of your HTML page to help search engines figure out the best way to get to the page.
- Configure your server to redirect HTTP traffic to HTTPS:
  - [nginx](https://serverfault.com/questions/67316)
  - [Apache](https://stackoverflow.com/questions/16200501)
  - [Cloudflare](https://www.cloudflare.com/website-optimization/automatic-https-rewrite/)
  - [Microsoft IIS](https://serverfault.com/q/893315)

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Does not redirect HTTP traffic to HTTPS** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/redirects-http.js)
- [Does not use HTTPS](/is-on-https)
- [Document does not have a valid `rel=canonical`](/canonical)

<span class="w-mr--sm">Last updated: Jun 10, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/redirects-http/index.md)

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
