## <a href="#resilient-search-experiences" class="w-toc__header--link">Resilient search experiences</a>

- [Production case](#production-case)
- [Implement resilient search experiences with Workbox](#implement-resilient-search-experiences-with-workbox)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Resilient search experiences

Using a service worker to save a search query when a user goes offline and then automatically retry the query once a connection is re-established.

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

Even in locations with fast networks a user might lose connection or connect to a flaky network, at some moments of the day. For example: a user is on the subway searching on the phone for a product on an e-commerce website. They type the product name, click the "search" button, and while waiting for the results, the connection is lost, leading to the standard browser offline page.

As a result, unless the user decides to come back to the site later, and repeat the same task, the site might lose a potential transaction and customer.

To provide a more resilient search experience in these cases you can use the [Background Sync API](https://developers.google.com/web/updates/2015/12/background-sync), which persists failed queries so they can be retried once the connection is recovered. This technique, in combination with [Web Push Notifications](https://developers.google.com/web/fundamentals/push-notifications) lets you inform the user of the search results, allowing you to keep them engaged with your service.

**Try it**! Try the [Building resilient search experiences with Workbox](/codelab-building-resilient-search-experiences) for a hands-on demonstration of the ideas explained in this guide.

## Production case <a href="#production-case" class="w-headline-link">#</a>

For concrete application of this technique let's take a look at Google Search for Chrome in Android. When visiting the Google Search web app and going offline, instead of showing the standard network error page, the site serves a custom offline response, but allows users to enter their search query immediately. The page also prompts the user to opt-in for notifications, to receive a link to the search results page once the connection is recovered.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TqDtqgbKOsxRFnr2lNSy.png?auto=format" sizes="(min-width: 257px) 257px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TqDtqgbKOsxRFnr2lNSy.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TqDtqgbKOsxRFnr2lNSy.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TqDtqgbKOsxRFnr2lNSy.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TqDtqgbKOsxRFnr2lNSy.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TqDtqgbKOsxRFnr2lNSy.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TqDtqgbKOsxRFnr2lNSy.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TqDtqgbKOsxRFnr2lNSy.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TqDtqgbKOsxRFnr2lNSy.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TqDtqgbKOsxRFnr2lNSy.png?auto=format&amp;w=514 514w" width="257" height="475" /></figure>When the user performs a search, the service worker allows the query to be deferred and sent to Google's servers as soon as the device goes back online by using the [Background Sync API](https://developers.google.com/web/updates/2015/12/background-sync), and to inform the user of the result by using the [Push API](https://developer.mozilla.org/en-US/docs/Web/API/Push_API).

<img src="https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format" alt="A screenshot of the offline flow in Google Search." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/ZZItVQMLUPmVbwJlfDck.png?auto=format&amp;w=1600 1600w" width="800" height="436" />

Service workers allow Google Search to provide a [meaningful offline experience](/google-search-sw/#meaningful-offline-experience) and keep the user engaged, letting them complete their task.

## Implement resilient search experiences with Workbox <a href="#implement-resilient-search-experiences-with-workbox" class="w-headline-link">#</a>

While Google Search implements this functionality without using Workbox, the [Workbox library](https://developers.google.com/web/tools/workbox) makes it easier by providing a [Background Sync module](https://developers.google.com/web/tools/workbox/modules/workbox-background-sync), which takes care of many implementation details for us.

<img src="https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format" alt="A service worker and a cache object communicating with each other." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/X06meG8U60SABUabxwHb.png?auto=format&amp;w=1600 1600w" width="800" height="383" />

To implement a resilient search experience in Workbox, first, import the following modules in your service worker:

    import {BackgroundSyncPlugin} from 'workbox-background-sync';
    import {registerRoute} from 'workbox-routing';
    import {NetworkOnly} from 'workbox-strategies';

Next, create an instance of the [workbox.backgroundSync plugin](https://developers.google.com/web/tools/workbox/reference-docs/v4/workbox.backgroundSync.Plugin), to automatically add failed requests to a queue, so they can be retried later:

    const bgSyncPlugin = new workbox.backgroundSync.Plugin('offlineQueryQueue', {
      maxRetentionTime: 60,
      onSync: async ({queue}) => {
        let entry;
        while ((entry = await queue.shiftRequest())) {
          try {
            const response = await fetch(entry.request);
            const cache = await caches.open('offline-search-responses');
            const offlineUrl = `${entry.request.url}&ampnotification=true`;
            cache.put(offlineUrl, response);
            showNotification(offlineUrl);
          } catch (error) {
            await this.unshiftRequest(entry);
            throw error;
          }
        }
      },
    });

The plugin receives the following parameters:

- `offlineQueryQueue`: The name of the queue that will be used to persist the failed requests in [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API).
- `maxRetentionTime`: The amount of time in minutes a request may be retried, after which point they will be discarded.
- `onSync`: The callback that will be triggered when the connection is recovered. At that point, each failed request can be dequeued and processed, by calling `queue.shiftRequest()`.

Finally, define a [networkOnly](https://developers.google.com/web/tools/workbox/modules/workbox-strategies#network_only) runtime caching strategy for requests to the search URL (e.g. `/search_action`) and pass it the `bgSyncPlugin` defined previously:

    workbox.routing.registerRoute(
      matchSearchUrl,
      new workbox.strategies.NetworkOnly({
            plugins: [bgSyncPlugin]
      })
    );

This tells Workbox to always go to the network when the service worker intercepts a request for the search endpoint, and to delegate to the Background Sync plugin the task of managing offline scenarios.

As a result, when the user goes offline while searching, the query is automatically saved. When the connection is recovered the offline logic is triggered to process the request and inform the user of the result.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

In this article you learned how to implement a search experience capable of responding gracefully to offline scenarios, by combining the [Background Sync API](https://developers.google.com/web/updates/2015/12/background-sync) and the [Push API](https://developer.mozilla.org/en-US/docs/Web/API/Push_API). We used Workbox to show how to implement this feature, as it simplifies the process, but the same can be achieved by writing vanilla service worker code.

In the code samples we focused on the core part of the feature: how requests are intercepted and managed by the service worker. For a step-by-step guide on how to implement this functionality, including the offline page and the notification logic, check out the codelab at the end of this article.

<a href="/tags/case-study/" class="w-chip">Case Study</a> <a href="/tags/network/" class="w-chip">Network</a> <a href="/tags/service-worker/" class="w-chip">Service Worker</a> <a href="/tags/offline/" class="w-chip">Offline</a>

<span class="w-mr--sm">Last updated: Aug 20, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/resilient-search-experiences/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-building-resilient-search-experiences/" class="w-callout__link w-callout__link--codelab">Building resilient search experiences with Workbox</a>

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
