<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/SgXCZjcjvhXuNIskeeBN.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#precaching-in-create-react-app-with-workbox" class="w-toc__header--link">Precaching in Create React App with Workbox</a>
----------------------------------------------------------------------------------------------------------------------------------

-   [Why is this useful?](#why-is-this-useful)
-   [Workbox in CRA](#workbox-in-cra)
-   [Modifying caching strategies](#modifying-caching-strategies)
-   [Handling a cache-first strategy](#handling-a-cache-first-strategy)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Precaching in Create React App with Workbox
===========================================

Caching assets with a service worker can speed up repeat visits and provide offline support. Workbox makes this easy and is included in Create React App by default.

Apr 29, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

If you don't yet understand the basic idea behind service workers and precaching, read the [Precaching with Workbox](/precache-with-workbox) guide first.

[`Workbox`](https://developers.google.com/web/tools/workbox/) is built into Create React App (CRA) with a default configuration that precaches all the static assets in your application with every build.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/3s4l29dJ6ch6QBmTvVg3.png?auto=format&amp;w=1600 1600w" width="800" height="1224" /></figure>Why is this useful? <a href="#why-is-this-useful" class="w-headline-link">#</a>
-------------------------------------------------------------------------------

Service workers enable you to store important resources in its cache (*precaching*) so that when a user loads the web page for a second time, the browser can retrieve them from the service worker instead of making requests to the network. This results in faster page loads on repeat visits as well as in the ability to surface content when the user is offline.

Workbox in CRA <a href="#workbox-in-cra" class="w-headline-link">#</a>
----------------------------------------------------------------------

**Workbox** is a collection of tools that allow you create and maintain service workers. In CRA, the [`workbox-webpack-plugin`](https://developers.google.com/web/tools/workbox/modules/workbox-webpack-plugin) is already included into the production build and only needs to be enabled in the `src/index.js` file in order to register a new service worker with every build:

    import React from 'react';
    import ReactDOM from 'react-dom';
    import './index.css';
    import App from './App';
    import * as serviceWorker from './serviceWorker';
    ReactDOM.render(<App />, document.getElementById('root'));

    serviceWorker.unregister();
    serviceWorker.register();

Here is an example of a React app built with CRA that has a service worker enabled through this file:

To see which assets are being cached:

-   To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).
-   Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
-   Click the **Network** tab.
-   Reload the app.

You'll notice that instead of showing the payload size, the `Size` column shows a `(from ServiceWorker)` message to indicate that these resources were retrieved from the service worker.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format" alt="Network requests with a service worker" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/N7YbiAIT88s8wPUriwo0.png?auto=format&amp;w=1600 1600w" width="800" height="450" />

Since the service worker caches all static assets, try to use the application while offline:

1.  In the **Network** tab in DevTools, enable the **Offline** checkbox to simulate an offline experience.

-   Reload the app.

The application works in exactly the same way, even without a network connection!

Modifying caching strategies <a href="#modifying-caching-strategies" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------

The default precaching strategy used by Workbox in CRA is **cache-first**, where all static assets are fetched from the service worker cache and if that fails (if the resource is not cached for example), the network request is made. This is how content can still be served to users even when they are in a complete offline state.

Although Workbox provides support to define different strategies and approaches to caching static and dynamic resources, the default configuration in CRA cannot be modified or overwritten unless you eject entirely. However, there is an [open proposal](https://github.com/facebook/create-react-app/issues/5359) to explore adding support for an external `workbox.config.js` file. This would allow developers to override the default settings by just creating a single `workbox.config.js` file.

For more details on all the caching strategies that a service worker can use, take a look at the [Offline Cookbook](https://developers.google.com/web/fundamentals/instant-and-offline/offline-cookbook/).

Handling a cache-first strategy <a href="#handling-a-cache-first-strategy" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------

Relying on the service worker cache first and then falling back to the network is an excellent way to build sites that load faster on subsequent visits and work offline to some extent. However, there are a few things that need to be taken into consideration:

-   How can caching behaviors by a service worker be tested?
-   Should there be a message for users to let them know they are looking at cached content?

[The CRA documentation](https://facebook.github.io/create-react-app/docs/making-a-progressive-web-app#offline-first-considerations) explains these points, and more, in detail.

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

Use a service worker to precache important resources in your application to provide a faster experience for your users as well as offline support.

1.  If you are using CRA, enable the pre-configured service worker in `src/index.js`.
2.  If you are not using CRA to build a React application, include one of the many libraries Workbox provides, such as `workbox-webpack-plugin`, into your build process.
3.  Keep an eye out for when CRA will support a `workbox.config.js` override file in this [GitHub issue](https://github.com/facebook/create-react-app/issues/5359).

<span class="w-mr--sm">Last updated: Apr 29, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/precache-with-workbox-react/index.md)

<a href="/react" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

-   ### Contribute

    -   <a href="https://github.com/GoogleChrome/web.dev/issues/new?assignees=&amp;labels=bug&amp;template=bug_report.md&amp;title=" class="w-footer__linkbox-link">File a bug</a>
    -   <a href="https://github.com/googlechrome/web.dev" class="w-footer__linkbox-link">View source</a>

-   ### Related content

    -   <a href="https://blog.chromium.org/" class="w-footer__linkbox-link">Chrome updates</a>
    -   <a href="https://developers.google.com/web/" class="w-footer__linkbox-link">Web Fundamentals</a>
    -   <a href="https://developers.google.com/web/showcase/" class="w-footer__linkbox-link">Case studies</a>
    -   <a href="https://devwebfeed.appspot.com/" class="w-footer__linkbox-link">DevWeb Content Firehose</a>
    -   <a href="/podcasts/" class="w-footer__linkbox-link">Podcasts</a>
    -   <a href="/shows/" class="w-footer__linkbox-link">Shows</a>

-   ### Connect

    -   <a href="https://www.twitter.com/ChromiumDev" class="w-footer__linkbox-link">Twitter</a>
    -   <a href="https://www.youtube.com/user/ChromeDevelopers" class="w-footer__linkbox-link">YouTube</a>

<a href="https://developers.google.com/" class="w-footer__utility-logo-link"><img src="/images/lockup-color.png" alt="Google Developers" class="w-footer__utility-logo" width="185" height="33" /></a>

-   <a href="https://developer.chrome.com/" class="w-footer__utility-link">Chrome</a>
-   <a href="https://firebase.google.com/" class="w-footer__utility-link">Firebase</a>
-   <a href="https://cloud.google.com/" class="w-footer__utility-link">Google Cloud Platform</a>
-   <a href="https://developers.google.com/products" class="w-footer__utility-link">All products</a>

<!-- -->

-   <a href="https://policies.google.com/" class="w-footer__utility-link">Terms &amp; Privacy</a>
-   <a href="/community-guidelines/" class="w-footer__utility-link">Community Guidelines</a>

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/terms/site-policies).
