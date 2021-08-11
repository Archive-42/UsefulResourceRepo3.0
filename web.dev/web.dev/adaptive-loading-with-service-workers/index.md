<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#adaptive-loading-with-service-workers" class="w-toc__header--link">Adaptive loading with service workers</a>

- [Production case](#production-case)
- [Implement adaptive loading with Workbox](#implement-adaptive-loading-with-workbox)
- [Cloudinary Workbox Plugin](#cloudinary-workbox-plugin)
- [Explore more adaptive loading strategies](#explore-more-adaptive-loading-strategies)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Adaptive loading with service workers

Modifying the assets that you serve to users based on their device and network conditions.

Jun 23, 2020 <span class="w-author__separator">•</span> Updated Aug 20, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

- <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
- <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

- <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
- <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
- <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

Users access websites through a wide variety of devices and network connections. Even in major cities, where mobile networks are fast and reliable, one can end up experiencing slower load times, for example, when commuting in the subway, in a car, or just when moving around. In regions like emerging markets, this phenomenon is even more common, not only due to unreliable networks, but also because devices tend to have less memory and CPU processing power.

[Adaptive loading](/adaptive-loading-cds-2019/) is a web performance pattern that lets you adapt your site based on the user's network and device conditions.

The adaptive loading pattern is made possible by [service workers](/service-workers-cache-storage/), the [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API), the [Hardware Concurrency API](https://developer.mozilla.org/en-US/docs/Web/API/NavigatorConcurrentHardware/hardwareConcurrency), and the [Device Memory API](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/deviceMemory). In this guide we explore how you can use service workers and the Network Information API to achieve an adaptive loading strategy.

## Production case <a href="#production-case" class="w-headline-link">#</a>

[Terra](https://www.terra.com.br/) is one of the biggest media companies in Brazil. It has a large user base, coming from a wide variety of devices and networks.

To provide a more reliable experience to all their users, Terra combines service workers and the [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API) to deliver lower quality images to users on 2G or 3G connections.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format" sizes="(min-width: 734px) 734px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/EQst12doZ2b8CLO0MtO5.png?auto=format&amp;w=1468 1468w" width="734" height="381" /></figure>The company also found that the scripts and assets (like banners) loaded by ad networks were especially detrimental to users navigating in 3G or slower connections.

As is the case with many publishers, Terra serves [AMP](https://amp.dev/) versions of their pages to users coming from search engines and other link sharing platforms. AMP pages are usually lightweight and help mitigate the impact of ads in performance by deprioritizing their load with respect to the main content of the page.

Taking that into consideration, Terra decided to start serving AMP versions of their pages not only to users coming from search engines, but also to those navigating their site in 3G connections or slower.

To achieve that, they use the [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API) in the service worker to detect if the request comes from 3G or slower. If that's the case, they change the URL of the page to request the AMP version of the page instead.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format" sizes="(min-width: 741px) 741px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/4kfDfkeIzxVXLoaTylug.png?auto=format&amp;w=1482 1482w" width="741" height="379" /></figure>Thanks to this technique, they send **70% less bytes** to users on slower connections. The **time spent** in AMP pages is higher for 3G users and ads in AMP pages have a better **CTR (click-through-rate)** for that group.

## Implement adaptive loading with Workbox <a href="#implement-adaptive-loading-with-workbox" class="w-headline-link">#</a>

In this section we'll explore how [Workbox](/workbox/) can be used to implement adaptive loading strategies.

Workbox provides several [runtime caching strategies](/runtime-caching-with-workbox/) out of the box. They are used to indicate how the service worker generates a response after receiving a `fetch` event.

For example, in a [Cache First](https://developers.google.com/web/tools/workbox/modules/workbox-strategies#cache_first_cache_falling_back_to_network) strategy the [`Request`](https://developer.mozilla.org/en-US/docs/Web/API/Request) will be fulfilled using the cached response (if available). If there isn't a cached response, the `Request` will be fulfilled by a network request and the response will be cached.

    import {registerRoute} from 'workbox-routing';
    import {CacheFirst} from 'workbox-strategies';

    registerRoute(
      new RegExp('/img/'),
      new CacheFirst()
    );

Caching strategies can be customized with [Workbox plugins](https://developers.google.com/web/tools/workbox/guides/using-plugins). These allow you to add additional behaviors by manipulating requests and responses during the lifecycle of a request. Workbox has several built-in plugins for common cases and APIs, but you can also define a [custom plugin](https://developers.google.com/web/tools/workbox/guides/using-plugins#custom_plugins), and introduce some custom logic of your choice.

To achieve adapting loading, define a custom plugin, called, for example, `adaptiveLoadingPlugin`:

    const adaptiveLoadingPlugin = {
      requestWillFetch: async ({request}) => {
        const urlParts = request.url.split('/');
        let imageQuality;

        switch (
          navigator && navigator.connection
            ? navigator.connection.effectiveType
            : ''
        ) {
          //...
          case '3g':
            imageQuality = 'q_30';
            break;
          //...
        }

        const newUrl = urlParts
          .splice(urlParts.length - 1, 0, imageQuality)
          .join('/')
          .replace('.jpg', '.png');
        const newRequest = new Request(newUrl.href, {headers: request.headers});

        return newRequest;
      },
    };

The previous code does the following:

- Implements a `requestWillFetch()` callback: This is called whenever a network request is about to be made, so you can alter the `Request`.
- Checks the connection type, by using the [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/NavigatorConcurrentHardware/hardwareConcurrency). Based on the status of the network, it creates a new URL part, indicating the quality of the image to fetch (e.g. `q_30` for 3G users).
- Creates a new URL based on the dynamic `newPart` value, and returns the new `Request` to be made, based on that URL.

Next, pass the plugin to a `cacheFirst` strategy containing a regular expression to match image URLs (e.g. `/img/`):

    workbox.routing.registerRoute(
      new RegExp('/img/'),
      workbox.strategies.cacheFirst({
        cacheName: 'images',
        plugins: [
          adaptiveLoadingPlugin,
          workbox.expiration.Plugin({
            maxEntries: 50,
            purgeOnQuotaError: true,
          }),
        ],
      }),
    );

As a result, when requests for images are intercepted, the runtime caching strategy will try to fulfill the request from the cache. If it's not available, it will run the logic in the plugin, to decide which image quality to fetch from the network.

Finally the response will be persisted in the cache, and sent back to the page.

## Cloudinary Workbox Plugin <a href="#cloudinary-workbox-plugin" class="w-headline-link">#</a>

Cloudinary, a video and image hosting service, has a [Workbox Plugin](https://www.npmjs.com/package/cloudinary-workbox-plugin) that encapsulates the functionality explained in the previous section, making it even easier to implement.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format" sizes="(min-width: 637px) 637px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iY2R0e4PvimaoVORo8Go.png?auto=format&amp;w=1274 1274w" width="637" height="269" /></figure>The plugin is designed to work with the [Workbox webpack plugin](https://developers.google.com/web/tools/workbox/modules/workbox-webpack-plugin). To implement it, use the [`GenerateSW()`](https://developers.google.com/web/tools/workbox/reference-docs/latest/module-workbox-webpack-plugin.GenerateSW) class:

    new workboxPlugin.GenerateSW({
      swDest: 'sw.js',
      importScripts: ['./cloudinaryPlugin.js'],
      runtimeCaching: [
        {
          urlPattern: new RegExp('^https://res.cloudinary.com/.*/image/upload/'),
          handler: 'CacheFirst',
          options: {
            cacheName: 'cloudinary-images',
            plugins: [
              {
                requestWillFetch: async ({request}) =>
                  cloudinaryPlugin.requestWillFetch(request),
              },
            ],
          },
        },
      ],
    });

The previous code does the following:

- Uses the `GenerateSW()` class to configure webpack to generate a service worker in the destination indicated in `swDest`.
- Imports the cloudinary plugin script.
- Defines a Cache First runtime caching strategy for requests for images to the Cloudinary CDN.
- Passes the [Cloudinary Workbox Plugin](https://www.npmjs.com/package/cloudinary-workbox-plugin) to adjust the image quality according to the network conditions.

## Explore more adaptive loading strategies <a href="#explore-more-adaptive-loading-strategies" class="w-headline-link">#</a>

You can go beyond this, by mapping device signals, like [hardware concurrency](https://developer.mozilla.org/en-US/docs/Web/API/NavigatorConcurrentHardware/hardwareConcurrency) and [device memory](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/deviceMemory) to device categories and then serving different assets depending on the device type (low-, mid- or high-end).

<a href="/tags/case-study/" class="w-chip">Case Study</a> <a href="/tags/network/" class="w-chip">Network</a> <a href="/tags/service-worker/" class="w-chip">Service Worker</a> <a href="/tags/memory/" class="w-chip">Memory</a> <a href="/tags/amp/" class="w-chip">AMP</a>

<span class="w-mr--sm">Last updated: Aug 20, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/adaptive-loading-with-service-workers/index.md)

<a href="/blog" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
