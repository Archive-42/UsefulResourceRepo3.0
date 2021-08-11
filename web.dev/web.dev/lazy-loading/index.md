<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

- [Why lazy-load images or video instead of just loading them?](#why)
- [Implementing lazy-loading](#implementing)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Use lazy-loading to improve loading speed

Aug 16, 2019 <span class="w-author__separator">•</span> Updated Jun 9, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeremy Wagner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeremywagner/)

<a href="/authors/jeremywagner/" class="w-author__name-link">Jeremy Wagner</a>

- <a href="https://twitter.com/malchata" class="w-author__link">Twitter</a>
- <a href="https://github.com/malchata" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rachel Andrew" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rachelandrew/)

<a href="/authors/rachelandrew/" class="w-author__name-link">Rachel Andrew</a>

- <a href="https://twitter.com/rachelandrew" class="w-author__link">Twitter</a>
- <a href="https://github.com/rachelandrew" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@rachelandrew" class="w-author__link">Glitch</a>
- <a href="https://rachelandrew.co.uk/" class="w-author__link">Blog</a>

The portion of [images](http://beta.httparchive.org/reports/state-of-images?start=earliest&end=latest) and [video](http://beta.httparchive.org/reports/page-weight#bytesVideo) in the typical payload of a website can be significant. Unfortunately, project stakeholders may be unwilling to cut any media resources from their existing applications. Such impasses are frustrating, especially when all parties involved want to improve site performance, but can't agree on how to get there. Fortunately, lazy-loading is a solution that lowers initial page payload _and_ load time, but doesn't skimp on content.

## What is lazy-loading? <a href="#what" class="w-headline-link">#</a>

Lazy-loading is a technique that defers loading of non-critical resources at page load time. Instead, these non-critical resources are loaded at the moment of need. Where images are concerned, "non-critical" is often synonymous with "off-screen". If you've used Lighthouse and examined some opportunities for improvement, you may have seen some guidance in this realm in the form of the [Defer offscreen images audit](/offscreen-images/):

<figure><img src="https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format" alt="One of Lighthouse&#39;s performance audits is to identify off screen images, which are candidates for lazy-loading." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/63NnMISWUUWD3mvAliwe.png?auto=format&amp;w=1600 1600w" width="800" height="102" /><figcaption>One of Lighthouse's performance audits is to identify off screen images, which are candidates for lazy-loading.</figcaption></figure>You've probably already seen lazy-loading in action, and it goes something like this:

- You arrive at a page, and begin to scroll as you read content.
- At some point, you scroll a placeholder image into the viewport.
- The placeholder image is suddenly replaced by the final image.

An example of image lazy-loading can be found on the popular publishing platform [Medium](https://medium.com/), which loads lightweight placeholder images at page load, and replaces them with lazily-loaded images as they're scrolled into the viewport.

<figure><img src="https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format" alt="An example of image lazy-loading in action. A placeholder image is loaded at page load (left), and when scrolled into the viewport, the final image loads at the time of need." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/p5ahQ67QtZ20bgto7Kpy.jpg?auto=format&amp;w=1600 1600w" width="800" height="493" /><figcaption>An example of image lazy-loading in action. A placeholder image is loaded at page load (left), and when scrolled into the viewport, the final image loads at the time of need.</figcaption></figure>If you're unfamiliar with lazy-loading, you might be wondering just how useful the technique is, and what its benefits are. Read on to find out!

## Why lazy-load images or video instead of just _loading_ them? <a href="#why" class="w-headline-link">#</a>

Because it's possible you're loading stuff the user may never see. This is problematic for a couple reasons:

- It wastes data. On unmetered connections, this isn't the worst thing that could happen (although you could be using that precious bandwidth for downloading other resources that are indeed going to be seen by the user). On limited data plans, however, loading stuff the user never sees could effectively be a waste of their money.
- It wastes processing time, battery, and other system resources. After a media resource is downloaded, the browser must decode it and render its content in the viewport.

Lazy-loading images and video reduces initial page load time, initial page weight, and system resource usage, all of which have positive impacts on performance.

## Implementing lazy-loading <a href="#implementing" class="w-headline-link">#</a>

There are a number of ways to implement lazy-loading. Your choice of solution must take into account the browsers you support, and also what you are trying to lazy-load.

Modern browsers implement [browser-level lazy-loading](/browser-level-image-lazy-loading/), which can be enabled using the `loading` attribute on images and iframes. To provide compatibility with older browsers or to perform lazy-loading on elements without built-in lazy-loading you can implement a solution with your own JavaScript. There are also a number of existing libraries to help you to do this. See the posts on this site for full details of all of these approaches:

- [Lazy-loading images](/lazy-loading-images/)
- [Lazy-loading video](/lazy-loading-video/)

Also, we have compiled a list of [potential issues with lazy-loading](/lazy-loading-best-practices), and things to watch out for in your implementation.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

Used with care, lazy-loading images and video can seriously lower the initial load time and page payloads on your site. Users won't incur unnecessary network activity and processing costs of media resources they may never see, but they can still view those resources if they want.

As far as performance improvement techniques go, lazy-loading is reasonably uncontroversial. If you have a lot of inline imagery in your site, it's a perfectly fine way to cut down on unnecessary downloads. Your site's users and project stakeholders will appreciate it!

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/images/" class="w-chip">Images</a>

<span class="w-mr--sm">Last updated: Jun 9, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/lazy-loading/index.md)

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
