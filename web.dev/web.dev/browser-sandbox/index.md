<a href="/" class="header-default__logo-link gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="header-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="header-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="header-default__link gc-analytics-event">Blog</a> <a href="/about/" class="header-default__link gc-analytics-event">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="drawer-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="drawer-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="drawer-default__link gc-analytics-event">Blog</a> <a href="/about/" class="drawer-default__link gc-analytics-event">About</a>

## <a href="#browser-sandbox" class="w-toc__header--link">Browser sandbox</a>

- [The idea of a "sandbox"](#the-idea-of-a-)
- [Why is a sandbox necessary?](#why-is-a-sandbox-necessary)
- [Make it secure by design](#make-it-secure-by-design)
- [Wrap up](#wrap-up)

Share <a href="/newsletter/" class="w-actions__fab w-actions__fab--subscribe gc-analytics-event"><span>subscribe</span></a>

# Browser sandbox

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/secure" class="w-post-signpost__link">Safe and secure</a>

[<img src="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Mariko Kosaka" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75 1x,     https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x,     https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x,     https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x,     https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/kosamari/)

<a href="/authors/kosamari/" class="w-author__name-link">Mariko Kosaka</a>

- <a href="https://twitter.com/kosamari" class="w-author__link">Twitter</a>
- <a href="https://github.com/kosamari" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@kosamari" class="w-author__link">Glitch</a>
- <a href="https://kosamari.com/" class="w-author__link">Blog</a>

To defend against attacks, a developer needs to mitigate vulnerabilities and add security features to an application. Luckily, on the web, the browser provides many security features. Some are available for developers to opt-in, and some are turned on by default to protect users.

## The idea of a "sandbox" <a href="#the-idea-of-a-%22sandbox%22" class="w-headline-link">#</a>

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format" alt="Figure: Browser as a sandbox" sizes="(min-width: 719px) 719px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=200 200w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=228 228w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=260 260w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=296 296w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=338 338w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=385 385w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=439 439w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=500 500w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=571 571w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=650 650w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=741 741w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=845 845w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=964 964w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=1098 1098w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=1252 1252w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=1428 1428w,     https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kPXwa8wRoJ5DGw97Mx3D.png?auto=format&amp;w=1438 1438w" width="719" height="403" /><figcaption>Figure: Browser as a sandbox</figcaption></figure>Modern web browsers are built on the idea of a "sandbox". A sandbox is a security mechanism used to run an application in a restricted environment. Just like the physical sandbox at a playground where kids can create anything they want within the boundary without making a mess elsewhere, application code has the freedom to execute within a restricted environment. For example, JavaScript can add and modify elements on the page but might be restricted from accessing an external JSON file. This is because of a sandbox feature called same-origin

## Why is a sandbox necessary? <a href="#why-is-a-sandbox-necessary" class="w-headline-link">#</a>

Every day, users of the web download arbitrary code and execute it on their computer or phone multiple times. If someone told you "Hey! Download and run this application!", you might pause to think if that application comes from a trusted source, read up on the application vendor, or check reviews carefully. How about when someone sends you a URL saying "check out this blog post"? You would probably click on it without asking questions like "What kind of JavaScript will this site download?".

The browser sandbox is the key feature that makes browsing on the web frictionless by making it safer to run arbitrary code.

## Make it secure by design <a href="#make-it-secure-by-design" class="w-headline-link">#</a>

If the browser is sandboxing each web application, should we even care about security? Absolutely yes!

First of all, sandbox features are not the perfect shield. Even though browser engineers work hard, browsers could have vulnerabilities and attackers are always trying to bypass the sandbox (such as with [Spectre Attack](https://developers.google.com/web/updates/2018/02/meltdown-spectre)).

The sandbox could sometimes get in a way of creating a great web experience. For example, a browser may block a fetch request to an image hosted on a different domain. You can share resources on different domains by turning on Cross-Origin Resource Sharing (CORS for short), but if it is not done carefully you can expose a resource to everyone else on the web, essentially undoing the sandbox.

## Wrap up <a href="#wrap-up" class="w-headline-link">#</a>

A secure web experience can only be achieved if security is baked into the design of your application, and strong design starts with understanding existing features. The next two guides dive into CORS and same-origin policy in depth.

<span class="w-mr--sm"> Last updated: Nov 5, 2018 </span> [Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/secure/browser-sandbox/index.md)

<a href="/secure" class="w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single gc-analytics-event">Return to all articles</a>

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
