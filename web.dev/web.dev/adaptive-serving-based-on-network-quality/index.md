





## <a href="#adaptive-serving-based-on-network-quality" class="w-toc__header--link">Adaptive serving based on network quality</a>

- [Usage](#usage)
- [How it works](#how-it-works)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Adaptive serving based on network quality

May 6, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

- <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
- <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
- <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

Loading a website can be a very different experience depending on the network conditions. Everything is usually smooth when you are on a fast network, but when you're on the go with a limited data plan and spotty connection, or stuck with a laptop on slow coffee-shop Wi-Fi, it's a different story.

One way to deal with this is by adapting which assets you're serving to users based on the quality of their connection. This is now possible with the [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API) which enables web applications to access information about the user's network.

You can see which browsers support [the Network Information API on caniuse.com](https://caniuse.com/#feat=netinfo).

## Usage <a href="#usage" class="w-headline-link">#</a>

There are many ways you can use this network information to improve the user experience:

- Switch between serving high-definition and low-definition content based on the user's network.
- Decide whether to preload resources.
- Defer uploads and downloads when users are on a slow connection.
- Enable offline mode if the network quality is not good enough to load the app and use the features.
- Warn users that doing something (for example, watching video) over cellular could cost them money.
- Use it in your analytics to gather data on your users' network quality.

Many applications are already doing something similar. For example, YouTube, Netflix and most other video (or video calling) services automatically adjust the resolution during streaming. When Gmail is loading, it provides users with a link to "load basic HTML (for slow connections)".

## <figure><img src="https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format" class="w-screenshot" sizes="(min-width: 528px) 528px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/zSTd1IMrb3UJfefdeRAt.png?auto=format&amp;w=1056 1056w" width="528" height="236" /></figure>How it works <a href="#how-it-works" class="w-headline-link">#</a>

The `navigator.connection` object contains information about a client's connection. Its properties are explained in the table bellow.

<table><thead><tr class="header"><th>Property</th><th>Explanation</th></tr></thead><tbody><tr class="odd"><td><code>downlink</code></td><td>The bandwidth estimate in megabits per second.</td></tr><tr class="even"><td><code>effectiveType</code></td><td>The effective type of the connection, with possible values <code>'slow-2g'</code>, <code>'2g'</code>, <code>'3g'</code>, or <code>'4g'</code> (covers 4g and higher). Determined based on the combination of <a href="https://wicg.github.io/netinfo/#effective-connection-types">round-trip time and downlink speed</a>. For example, fast downlink combined with high latency will have lower effectiveType due to latency.</td></tr><tr class="odd"><td><code>onchange</code></td><td>An event handler that fires when connection information changes.</td></tr><tr class="even"><td><code>rtt</code></td><td>The estimated round-trip latency of the connection in milliseconds.</td></tr><tr class="odd"><td><code>saveData</code></td><td>A boolean that defines whether the user has requested a reduced data usage mode.</td></tr></tbody></table>

Here's what this looks like when you run it in the browser's console:

<img src="https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format" alt="Chrome DevTools console displaying the values of navigator.connection object&#39;s properties" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/ayW8uxhh3S6I4MTipr0m.jpg?auto=format&amp;w=1600 1600w" width="800" height="523" />

The `effectiveType` values are also available via [Client Hints](https://www.chromestatus.com/feature/5407907378102272) and allow you to communicate the browser's connection type to servers.

You can access Network Information API inside [Service Workers](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorker) to adapt to situations when users are offline.

The `onchange` event listener enables you to dynamically adapt to changes in network quality. If you deferred uploads or downloads because of poor network conditions, you can rely on the event listener to restart the transfer when it detects better network conditions. You can also use it to notify users when the network quality changes. For example, if they lost their Wi-Fi signal and were dropped to a cellular network this can prevent accidental data transfers (and charges 💸).

Use the `onchange` event listener as you would any other event listener:

    navigator.connection.addEventListener('change', doSomethingOnChange);

Network information API is [supported in Chromium-based browsers](https://caniuse.com/#feat=netinfo) since version 62.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

The potential benefits of the Network Information API are big, especially for users on slow networks and applications that require a lot of bandwidth. Best of all, it can be used as a progressive enhancement technique.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: May 6, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/adaptive-serving-based-on-network-quality/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-adapt-video-to-image-serving-based-on-network-quality/" class="w-callout__link w-callout__link--codelab">Adapt video to image serving based on network quality</a>

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
