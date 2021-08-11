<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#how-amp-can-guarantee-fastness-in-your-next.js-app" class="w-toc__header--link">How AMP can guarantee fastness in your Next.js app</a>

- [What will you learn?](#what-will-you-learn)
- [How AMP guarantees fast page loads](#overview)
- [How you can use AMP in Next.js](#strategies)
- [How to decide whether to use the Hybrid AMP or AMP-only approach](#guidance)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# How AMP can guarantee fastness in your Next.js app

Learn about the benefits and tradeoffs of supporting AMP in your Next.js app

Nov 8, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

- <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
- <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
- <a href="https://houssein.me/" class="w-author__link">Blog</a>

[AMP](https://amp.dev) is a web component framework that guarantees fast page loads. [Next.js](/performance-as-a-default-with-nextjs) has built-in support for AMP.

## What will you learn? <a href="#what-will-you-learn" class="w-headline-link">#</a>

This guide first briefly describes [how AMP guarantees fast page loads](#overview), then explains [the different ways you can support AMP in a Next.js app](#strategies), then helps you [decide which approach is best for you](#guidance).

The intended audience for this guide is a web developer who has decided to use Next.js but is unsure of whether to support AMP.

This guide was not written for web developers who have decided to use AMP but are unsure of what framework to use. We will note briefly however that Next.js could be a good choice because it supports [AMP server-side rendering](https://amp.dev/documentation/guides-and-tutorials/optimize-and-measure/server-side-rendering/) and makes it easy to serve AMP content without introducing a lot of complexity into your codebase.

## How AMP guarantees fast page loads <a href="#overview" class="w-headline-link">#</a>

AMP has two main strategies for guaranteeing fastness:

- **AMP HTML**: A restricted form of HTML that makes certain optimizations mandatory and prohibits architectural patterns that lead to slowness. See [How AMP works](https://amp.dev/about/how-amp-works/) for a high-level overview of the optimizations and restrictions.
- **AMP Cache**: A content cache used by some search engines, such as Google and Bing, that uses [prerendering](https://developers.googleblog.com/2019/08/the-speed-benefit-of-amp-prerendering.html) to speed up page loads. See [Why AMP Caches exist](https://blog.amp.dev/2017/01/13/why-amp-caches-exist/) to learn more about the benefits and tradeoffs of the caches and [How does my AMP page get cached?](https://amp.dev/documentation/guides-and-tutorials/learn/amp-caches-and-cors/how_amp_pages_are_cached/#how-does-my-amp-page-get-cached?) to understand how your AMP pages get into the caches.

## How you can use AMP in Next.js <a href="#strategies" class="w-headline-link">#</a>

There are two ways to use AMP in Next.js:

- The **Hybrid AMP** approach lets you create an accompanying AMP version of any Next.js page.
- The **AMP-only** approach lets you make AMP the only option for a page.

Although Next.js is usually thought of as a React framework, it's important to understand that when you use Next.js to serve AMP pages, you can no longer run React components client-side because React components are not valid AMP components. In other words, Next.js is no longer a React framework but rather a server-side templating engine for generating AMP pages.

**Try it**! Check out [How to use AMP in Next.js](/how-to-use-amp-in-nextjs) to try out the two approaches yourself.

## How to decide whether to use the Hybrid AMP or AMP-only approach <a href="#guidance" class="w-headline-link">#</a>

If you're serious about load performance, an AMP-only page could be a good way to make sure that your page gets fast and stays fast. But here's the catch: in order to guarantee fastness, AMP prohibits certain architectural patterns and HTML elements that often lead to slow pages. For example, AMP doesn't allow custom synchronous JavaScript because [render-blocking resources](/render-blocking-resources) are a common cause of slow page loads.

In order to understand whether an AMP-only approach is right for you, you need to figure out whether all of your frontend code can be represented in AMP HTML:

- Read [How AMP works](https://amp.dev/about/how-amp-works/) to understand AMP's high-level architectural restrictions and mandatory optimizations.
- Read [HTML Tags](https://amp.dev/documentation/guides-and-tutorials/learn/spec/amphtml/#html-tags) to see what HTML tags AMP allows and prohibits, browse the [AMP component catalogue](https://amp.dev/documentation/components/) to see the custom components that the AMP community has built to solve common use cases, and check out [amp-script](https://amp.dev/documentation/components/amp-script/) to learn how to use custom JavaScript to implement features that AMP doesn't currently support.

Even if an AMP-only approach won't work for your page, it might still be a good idea to use AMP whenever possible, because of the guaranteed fastness of AMP HTML and the AMP Caches. The Hybrid AMP approach in Next.js provides a way to conditionally serve AMP pages. However, it also creates a higher maintenance cost because it requires you to maintain two versions of each page.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

AMP guarantees that your site gets fast and stays fast by enforcing patterns that lead to fastness and prohibiting patterns that lead to slowness. AMP HTML and AMP Caches are the two main ways that AMP guarantees fastness. But before adopting AMP you should make sure that it can support all of your site's requirements.

<span class="w-mr--sm">Last updated: Nov 8, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/how-amp-can-guarantee-fastness-in-your-nextjs-app/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/how-to-use-amp-in-nextjs/" class="w-callout__link w-callout__link--codelab">How to use AMP in Next.js</a>

<a href="/react" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
