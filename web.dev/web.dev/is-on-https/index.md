

## <a href="#does-not-use-https" class="w-toc__header--link">Does not use HTTPS</a>

- [How the Lighthouse HTTPS audit fails](#how-the-lighthouse-https-audit-fails)
- [How to migrate your site to HTTPS](#how-to-migrate-your-site-to-https)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Does not use HTTPS

May 4, 2019 <span class="w-author__separator">•</span> Updated Apr 29, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-best-practices" class="w-post-signpost__link">Best Practices audits</a><span class="w-post-signpost__divider">|</span><a href="/lighthouse-pwa" class="w-post-signpost__link">PWA audits</a>

All websites should be protected with HTTPS, even ones that don't handle sensitive data. HTTPS prevents intruders from tampering with or passively listening in on the communications between your site and your users.

A page can't qualify as a [Progressive Web App (PWA)](/discover-installable) if it doesn't run on HTTPS; many core PWA technologies, such as service workers, require HTTPS.

For more information about why all sites should be protected with HTTPS, see [Why HTTPS Matters](/why-https-matters/).

## How the Lighthouse HTTPS audit fails <a href="#how-the-lighthouse-https-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags pages that aren't on HTTPS:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FD2HDFl8SQCgRdhV4tzZ.png?auto=format&amp;w=1600 1600w" width="800" height="139" /></figure>Lighthouse waits for an event from the [Chrome Remote Debugging Protocol](https://github.com/ChromeDevTools/devtools-protocol) indicating that the page is running on a secure connection. If the event isn't heard within 10 seconds, the audit fails.

In the Lighthouse report UI the full PWA badge is given when you pass all of the audits in all of the PWA subcategories (**Fast and reliable**, **Installable**, and **PWA optimized**).

## How to migrate your site to HTTPS <a href="#how-to-migrate-your-site-to-https" class="w-headline-link">#</a>

Consider hosting your site on a CDN. Most CDNs are secure by default.

To learn how to enable HTTPS on your servers, see Google's [Enabling HTTPS on Your Servers](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/enable-https). If you're running your own server and need a cheap and easy way to generate certificates, [Let's Encrypt](https://letsencrypt.org/) is a good option.

If your page is already running on HTTPS but you're failing this audit, you may have problems with [mixed content](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/what-is-mixed-content). A page has mixed content when the page itself is loaded over HTTPS, but it requests an unprotected (HTTP) resource. Check out the following doc on the Chrome DevTools Security panel to learn how to debug these situations: [Understand Security Issues With Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/debug/security).

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Does not use HTTPS** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/is-on-https.js)
- [Why You Should Always Use HTTPS](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/why-https)
- [Enabling HTTPS on Your Servers](https://developers.google.com/web/fundamentals/security/encrypt-in-transit/enable-https)
- [Understand Security Issues With Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/debug/security)
- [What Is Mixed Content?](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/what-is-mixed-content)
- [Let's Encrypt](https://letsencrypt.org/)

<span class="w-mr--sm">Last updated: Apr 29, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-pwa/is-on-https/index.md)

<a href="/lighthouse-best-practices" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
