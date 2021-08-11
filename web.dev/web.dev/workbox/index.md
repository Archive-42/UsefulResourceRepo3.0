## <a href="#workbox:-your-high-level-service-worker-toolkit" class="w-toc__header--link">Workbox: your high-level service worker toolkit</a>

- [Runtime code](#runtime-code)
- [Why should you use Workbox?](#why-should-you-use-workbox)
- [Cache management](#cache-management)
- [Extensive logging and error reporting](#extensive-logging-and-error-reporting)
- [A tested, cross-browser codebase](#a-tested-cross-browser-codebase)
- [Build integration](#build-integration)
- [How should you use Workbox?](#how-should-you-use-workbox)
- [Framework integration](#framework-integration)
- [Add Workbox to your existing build process](#add-workbox-to-your-existing-build-process)
- [Use Workbox at runtime in an existing service worker](#use-workbox-at-runtime-in-an-existing-service-worker)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Workbox: your high-level service worker toolkit

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

- <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
- <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
- <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

Two APIs play a crucial role in building reliable web apps: [Service Worker](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) and [Cache Storage](https://developer.mozilla.org/en-US/docs/Web/API/Cache). But using them effectively—without introducing subtle bugs or bumping into edge cases—can be a challenge. For example, errors in your service worker code can cause caching problems; users might be shown out-of-date content or broken links.

[Workbox](https://developers.google.com/web/tools/workbox/) is a high-level service worker toolkit built on top of the Service Worker and Cache Storage APIs. It provides a production-ready set of libraries for adding offline support to web apps. The toolkit is structured into two collections: tools that help manage code that runs inside of your service worker, and tools that integrate with your build process.

### Runtime code <a href="#runtime-code" class="w-headline-link">#</a>

This is the code that runs inside of your service worker script and controls how it intercepts outgoing requests and interacts with the Cache Storage API. Workbox has a [dozen or so library modules in total](https://developers.google.com/web/tools/workbox/modules/), that each handle a variety of specialized use cases. The most important modules determine _whether_ the service worker will respond (known as [routing](https://developers.google.com/web/tools/workbox/modules/workbox-routing)), and _how_ it will respond (known as the [caching strategy](https://developers.google.com/web/tools/workbox/modules/workbox-strategies)).

### Build integration <a href="#build-integration" class="w-headline-link">#</a>

Workbox offers [command line](https://developers.google.com/web/tools/workbox/modules/workbox-cli), [Node.js module](https://developers.google.com/web/tools/workbox/modules/workbox-build), and [webpack plugin](https://developers.google.com/web/tools/workbox/modules/workbox-webpack-plugin) tools that provide alternative ways to accomplish two things:

- Create a service worker script based on a set of configuration options. The generated service worker uses Workbox's runtime libraries "under the hood" to put into action the caching strategies you configure.
- Generate a list of URLs that should be "[precached](https://developers.google.com/web/tools/workbox/modules/workbox-precaching)", based on configurable patterns to include and exclude files generated during your build process.

## Why should you use Workbox? <a href="#why-should-you-use-workbox" class="w-headline-link">#</a>

Using Workbox when building your service worker is optional—there are a number of guides out there that walk through [common caching strategies](https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook/) from a "vanilla" service worker perspective. If you do decide to use Workbox, here are some of its benefits.

### Cache management <a href="#cache-management" class="w-headline-link">#</a>

Workbox handles cache updates for you, either tied in to your build process when using precaching, or via configurable size/age policies when using runtime caching. The underlying Cache Storage API is powerful, but it does not have any built-in support for cache expiration. Tools like Workbox fill that gap.

### Extensive logging and error reporting <a href="#extensive-logging-and-error-reporting" class="w-headline-link">#</a>

When you're getting started with service workers, figuring out _why_ something is being cached (or, equally frustrating, why it _isn't_ cached) is a challenge. Workbox automatically detects when you're running a development version of your website on `localhost`, and turns on debug logging in your browser's JavaScript console.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format" alt="Workbox logging to the DevTools console" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gvsGSU3urfjl52jRcj3j.png?auto=format&amp;w=1600 1600w" width="800" height="438" />

By following along with the log messages, you can get to the root of any configuration or invalidation problems much more quickly than if you were going it alone.

### A tested, cross-browser codebase <a href="#a-tested-cross-browser-codebase" class="w-headline-link">#</a>

Workbox is developed against a cross-browser test suite, and when possible, automatically falls back to alternative implementations of features that are missing from certain browsers.

- The [`workbox-broadcast-cache-update module`](https://developers.google.com/web/tools/workbox/modules/workbox-broadcast-cache-update) uses the [Broadcast Channel API](https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API) when available, and falls back to a [`postMessage()`](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage)-based implementation on browsers that lack support.
- The [workbox-background-sync module](https://developers.google.com/web/tools/workbox/modules/workbox-background-sync) uses the [Background Sync API](https://developers.google.com/web/updates/2015/12/background-sync) if possible, and if not, falls back to retrying queued events each time the service worker starts up.

## How should you use Workbox? <a href="#how-should-you-use-workbox" class="w-headline-link">#</a>

### Framework integration <a href="#framework-integration" class="w-headline-link">#</a>

If you're starting a new project from scratch, you can take advantage of the Workbox integration found in many popular starter kits and add-on plugins:

- [create-react-app](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app)
- [vue-cli](https://github.com/vuejs/vue-cli/blob/dev/packages/%40vue/cli-plugin-pwa/README.md)
- [preact-cli](https://github.com/prateekbh/preact-cli-workbox-plugin/blob/master/README.md)
- [Gatsby](https://www.gatsbyjs.org/packages/gatsby-plugin-offline/)
- [Next.js](https://github.com/hanford/next-offline/blob/master/readme.md)

### Add Workbox to your existing build process <a href="#add-workbox-to-your-existing-build-process" class="w-headline-link">#</a>

If you already have a build process for your site in place, dropping in the appropriate [command line](https://developers.google.com/web/tools/workbox/modules/workbox-cli), [Node.js module](https://developers.google.com/web/tools/workbox/modules/workbox-build), or [webpack plugin](https://developers.google.com/web/tools/workbox/modules/workbox-webpack-plugin) tool may be all you need to start using Workbox.

In particular, the Workbox command line interface makes it easy to get up and running, featuring a `wizard` mode that will check your local development environment and suggest a reasonable default configuration that you could use moving forward:

    workbox wizard
    ? What is the root of your web app (i.e. which directory do you deploy)? src/
    ? Which file types would you like to precache? css, js, html
    ? Where would you like your service worker file to be saved? build/sw.js
    ? Where would you like to save these configuration options? workbox-config.js

To build your service worker, run `workbox generateSW workbox-config.js` as part of a build process. See the [`generateSW` documentation](https://goo.gl/fdTQBf) for details. You can further customize your service worker by making changes to `workbox-config.js`. See the [documentation of the options](https://goo.gl/gVo87N) for details.

### Use Workbox at runtime in an existing service worker <a href="#use-workbox-at-runtime-in-an-existing-service-worker" class="w-headline-link">#</a>

If you have an existing service worker and want to try out Workbox's runtime libraries, [import Workbox from its official CDN](https://developers.google.com/web/tools/workbox/modules/workbox-sw#using_workbox_sw_via_cdn) and start using it for runtime caching right away. Please note that this use case means that you won't be able to take advantage of precaching (which requires build-time integration), but it's great for prototyping and trying out different caching strategies on the fly.

    // Replace 3.6.3 with the current version number of Workbox.
    importScripts('https://storage.googleapis.com/workbox-cdn/releases/3.6.3/workbox-sw.js');

    workbox.routing.registerRoute(
      new RegExp('\.png$'),
      workbox.strategies.cacheFirst({
        cacheName: 'images-cache',
      })
    );

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/workbox/index.md)

<a href="/reliable" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
