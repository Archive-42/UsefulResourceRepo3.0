# Building resilient search experiences with Workbox

Jun 23, 2020

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

This codelab shows you how to implement a resilient search experience with Workbox. The demo app it uses contains a search box that calls a server endpoint, and redirects the user to a basic HTML page.

This codelab uses [Chrome DevTools](https://www.google.com/chrome/). Download Chrome if you don't already have it.

## Measure <a href="#measure" class="w-headline-link">#</a>

Before adding optimizations, it's always a good idea to first analyze the current state of the application.

- Click **Remix to Edit** to make the project editable.
- To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

In the new tab that just opened, check how the website behaves when going offline:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Network** tab.
3.  Open Chrome DevTools and select the Network panel.
4.  In the [Throttling drop-down list](https://developers.google.com/web/tools/chrome-devtools/network/reference#throttling), select **Offline**.
5.  In the demo app enter a search query, then click the **Search** button.

The standard browser error page is shown:

<img src="https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format" alt="A screenshot of the default offline UX in the browser." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/g4Naxj1RnipuqxqzC62x.png?auto=format&amp;w=1600 1600w" width="800" height="465" />

## Provide a fallback response <a href="#provide-a-fallback-response" class="w-headline-link">#</a>

The service worker contains the code to add the offline page to the [precache list](https://developers.google.com/web/tools/workbox/modules/workbox-precaching#explanation_of_the_precache_list), so it can always be cached at the service worker `install` event.

Usually you would need to instruct Workbox to add this file to the precache list at build time, by integrating the library with your build tool of choice (e.g. [webpack](https://webpack.js.org/) or [gulp](https://gulpjs.com/)).

For simplicity, we've already done it for you. The following code at `public/sw.js` does that:

    const FALLBACK_HTML_URL = ‘/index_offline.html’;
    …
    workbox.precaching.precacheAndRoute([FALLBACK_HTML_URL]);

To learn more about how to integrate Workbox with build tools, check out the [webpack Workbox plugin](https://developers.google.com/web/tools/workbox/modules/workbox-webpack-plugin) and the [Gulp Workbox plugin](https://developers.google.com/web/tools/workbox/guides/codelabs/gulp).

Next, add code to use the offline page as a fallback response:

1.  To view the source, press **View Source**.
2.  Add the following code to the bottom of `public/sw.js`:

<!-- -->

    workbox.routing.setDefaultHandler(new workbox.strategies.NetworkOnly());

    workbox.routing.setCatchHandler(({event}) => {
      switch (event.request.destination) {
        case 'document':
          return caches.match(FALLBACK_HTML_URL);
          break;
        default:
          return Response.error();
      }
    });

The Glitch UI says `workbox is not defined` because it doesn't realize that the `importScripts()` call on line 1 is importing the library.

The code does the following:

- Defines a default [Network Only strategy](https://developers.google.com/web/tools/workbox/modules/workbox-strategies#network_only) that will apply to all requests.
- Declares a global error handler, by calling `workbox.routing.setCatchHandler()` to manage failed requests. When requests are for documents, a fallback offline HTML page will be returned.

To test this functionality:

1.  Go back to the other tab that is running your app.
2.  Set the **Throttling** drop-down list back to **Online**.
3.  Press Chrome's **Back** button to navigate back to the search page.
4.  Make sure that the **Disable cache** checkbox in DevTools is disabled.
5.  Long-press Chrome's **Reload** button and select [**Empty cache and hard reload**](https://stackoverflow.com/q/14969315/1669860) to ensure that your service worker is updated.
6.  Set the **Throttling** drop-down list back to **Offline** again.
7.  Enter a search query, and click the **Search** button again.

The fallback HTML page is shown:

<img src="https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format" alt="A screenshot of the custom offline UX in the browser." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/2o0feM6Ib4GnLdKQqV9G.png?auto=format&amp;w=1600 1600w" width="800" height="456" />

## Request notification permission <a href="#request-notification-permission" class="w-headline-link">#</a>

For simplicity, the offline page at `views/index_offline.html` already contains the code to request notification permissions in a script block at the bottom:

    function requestNotificationPermission(event) {
      event.preventDefault();

      Notification.requestPermission().then(function (result) {
        showOfflineText(result);
      });
    }

The code does the following:

- When the user clicks **subscribe to notifications** the `requestNotificationPermission()` function is called, which calls `Notification.requestPermission()`, to show the default browser permission prompt. The promise resolves with the permission picked by the user, which can be either `granted`, `denied`, or `default`.
- Passes the resolved permission to `showOfflineText()` to show the appropriate text to the user.

## Persist offline queries and retry when back online <a href="#persist-offline-queries-and-retry-when-back-online" class="w-headline-link">#</a>

Next, implement [Workbox Background Sync](https://developers.google.com/web/tools/workbox/modules/workbox-background-sync) to persist offline queries, so they can be retried when the browser detects that connectivity has returned.

1.  Open `public/sw.js` for edit.
2.  Add the following code at the end of the file:

<!-- -->

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

The code does the following:

- `workbox.backgroundSync.Plugin` contains the logic to add failed requests to a queue so they can be retried later. These requests will be persisted in [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API).
- `maxRetentionTime` indicates the amount of time a request may be retried. In this case we have chosen 60 minutes (after which it will be discarded).
- `onSync` is the most important part of this code. This callback will be called when connection is back so that queued requests are retrieved and then fetched from the network.
- The network response is added to the `offline-search-responses` cache, appending the `&ampnotification=true` query param, so that this cache entry can be picked up when a user clicks on the notification.

To integrate background sync with your service, define a [NetworkOnly](https://developers.google.com/web/tools/workbox/modules/workbox-strategies#network_only) strategy for requests to the search URL (`/search_action`) and pass the previously defined `bgSyncPlugin`. Add the following code to the bottom of `public/sw.js`:

    const matchSearchUrl = ({url}) => {
      const notificationParam = url.searchParams.get('notification');
      return url.pathname === '/search_action' && !(notificationParam === 'true');
    };

    workbox.routing.registerRoute(
      matchSearchUrl,
      new workbox.strategies.NetworkOnly({
        plugins: [bgSyncPlugin],
      }),
    );

This tells Workbox to always go to the network, and, when requests fail, use the background sync logic.

Next, add the following code to the bottom of `public/sw.js` to define a caching strategy for requests coming from notifications. Use a [CacheFirst](https://developers.google.com/web/tools/workbox/modules/workbox-strategies#cache_first_cache_falling_back_to_network) strategy, so they can be served from the cache.

    const matchNotificationUrl = ({url}) => {
      const notificationParam = url.searchParams.get('notification');
      return (url.pathname === '/search_action' && (notificationParam === 'true'));
    };

    workbox.routing.registerRoute(matchNotificationUrl,
      new workbox.strategies.CacheFirst({
         cacheName: 'offline-search-responses',
      })
    );

Finally, add the code to show notifications:

    function showNotification(notificationUrl) {
      if (Notification.permission) {
         self.registration.showNotification('Your search is ready!', {
            body: 'Click to see you search result',
            icon: '/img/workbox.jpg',
            data: {
               url: notificationUrl
            }
         });
      }
    }

    self.addEventListener('notificationclick', function(event) {
      event.notification.close();
      event.waitUntil(
         clients.openWindow(event.notification.data.url)
      );
    });

## Test the feature <a href="#test-the-feature" class="w-headline-link">#</a>

1.  Go back to the other tab that is running your app.
2.  Set the **Throttling** drop-down list back to **Online**.
3.  Press Chrome's **Back** button to navigate back to the search page.
4.  Long-press Chrome's **Reload** button and select [**Empty cache and hard reload**](https://stackoverflow.com/q/14969315/1669860) to ensure that your service worker is updated.
5.  Set the **Throttling** drop-down list back to **Offline** again.
6.  Enter a search query, and click the **Search** button again.
7.  Click **subscribe to notifications**.
8.  When Chrome asks you if you want to grant the app permission to send notifications, click **Allow**.
9.  Enter another search query and click the **Search** button again.
10. Set the **Throttling** drop-down list back to **Online** again.

Once the connection is back a notification will be shown:

<img src="https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format" alt="A screenshot of the full offline flow." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/kvnl2PlazBdppGF4eMi0.png?auto=format&amp;w=1600 1600w" width="800" height="315" />

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

Workbox provides many built-in features to make your PWAs more resilient and engaging. In this codelab you have explored how to implement the Background Sync API by way of the Workbox abstraction, to ensure that offline user queries are not lost, and can be retried once connection is back. The demo is a simple search app, but you can use a similar implementation for more complex scenarios and use cases, including chat apps, posting messages on a social network, etc.

<a href="/resilient-search-experiences" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to article</a>

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
