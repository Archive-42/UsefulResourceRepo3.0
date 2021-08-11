# Same Origin Policy & iframe

Nov 5, 2018

[<img src="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Mariko Kosaka" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/kosamari/)

<a href="/authors/kosamari/" class="w-author__name-link">Mariko Kosaka</a>

- <a href="https://twitter.com/kosamari" class="w-author__link">Twitter</a>
- <a href="https://github.com/kosamari" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@kosamari" class="w-author__link">Glitch</a>
- <a href="https://kosamari.com/" class="w-author__link">Blog</a>

In this codelab, see how the same-origin policy works when accessing data inside an iframe.

## Set up: Page with a same-origin iframe <a href="#set-up:-page-with-a-same-origin-iframe" class="w-headline-link">#</a>

This page embeds an `iframe`, called `iframe.html`, in the same origin. Since the host and the iframe share the same origin, the host site is able to access data inside of the iframe and expose the secret message like blow.

    const iframe = document.getElementById('iframe');
    const message = iframe.contentDocument.getElementById('message').innerText;

## Change to cross-origin iframe <a href="#change-to-cross-origin-iframe" class="w-headline-link">#</a>

Try changing the `src` of the `iframe` to `https://other-iframe.glitch.me/`. Can the host page still access the secret message?

Since the host and embedded `iframe` do not have the same origin, access to the data is restricted.

<a href="/same-origin-policy" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to article</a>

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
