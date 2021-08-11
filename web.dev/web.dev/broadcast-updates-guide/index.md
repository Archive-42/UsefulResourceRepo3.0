<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#broadcast-updates-to-pages-with-service-workers" class="w-toc__header--link">Broadcast updates to pages with service workers</a>
------------------------------------------------------------------------------------------------------------------------------------------

-   [Production cases](#production-cases)
-   [Tinder](#tinder)
-   [Squoosh](#squoosh)
-   [Using Workbox](#using-workbox)
-   [Listen to service worker lifecycle events](#listen-to-service-worker-lifecycle-events)
-   [Inform the page of changes in cache data](#inform-the-page-of-changes-in-cache-data)
-   [Using browser APIs](#using-browser-apis)
-   [Broadcast Channel API](#broadcast-channel-api)
-   [Client API](#client-api)
-   [Message Channel](#message-channel)
-   [Next steps](#next-steps)
-   [Additional resources](#additional-resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Broadcast updates to pages with service workers
===============================================

Dec 8, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

-   <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
-   <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

[<img src="https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Andrew Guan" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/andrewguan/)

<a href="/authors/andrewguan/" class="w-author__name-link">Andrew Guan</a>

-   <a href="https://github.com/AndrewKGuan" class="w-author__link">GitHub</a>

In some scenarios the service worker might need to proactively communicate with any of the active tabs it controls to inform of a certain event. Examples include:

-   Informing the page when a new version of the service worker has been installed, so that the page can show an **"Update to refresh"** button to the user to access the new functionality immediately.
-   Letting the user know about a change on cached data that took place on the service worker side, by showing an indication, like: **"The app is now ready to work offline"**, or **"New version of the content available"**.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format" sizes="(min-width: 550px) 550px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/RpZYhHYGpPY9e3AjxuaQ.png?auto=format&amp;w=1100 1100w" width="550" height="318" /></figure>We'll call these types of use cases where the service worker doesn't need to receive a message from the page to start a communication **"broadcast updates"**. In this guide we'll review different ways of implementing this type of communication between pages and service workers, by using standard browser APIs and the [Workbox library](https://developers.google.com/web/tools/workbox).

Check out [Workers overview](/workers-overview/) for a high-level explanation of when to use web workers versus service workers and the rest of the [Communicate with workers](/reliable/#communicate-with-workers) series for guides on other common use cases.

Production cases <a href="#production-cases" class="w-headline-link">#</a>
--------------------------------------------------------------------------

### Tinder <a href="#tinder" class="w-headline-link">#</a>

Tinder PWA uses [`workbox-window`](https://developers.google.com/web/tools/workbox/modules/workbox-window) to listen to important service worker lifecycle moments from the page ("installed", "controlled" and "activated"). That way when a new service worker comes into play, it shows an **"Update Available"** banner, so that they can refresh the PWA and access the latest features:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format" alt="In the Tinder PWA, the service worker tells the page that a new version is ready, and the page shows users a &quot;Update Available&quot; banner." sizes="(min-width: 650px) 650px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/I8TQ9quakuxJc4l6aNvW.png?auto=format&amp;w=1300 1300w" width="650" height="366" /><figcaption>In the Tinder PWA, the service worker tells the page that a new version is ready, and the page shows users a "Update Available" banner.</figcaption></figure>### Squoosh <a href="#squoosh" class="w-headline-link">#</a>

In the [Squoosh PWA](https://squoosh.app/), when the service worker has cached all of the necessary assets to make it work offline, it sends a message to the page to show a "Ready to work offline" toast, letting the user know about the feature:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format" alt="In the Squoosh PWA the service worker broadcasts an update to the page when cache is ready, and the page displays &quot;Ready to work offline&quot; toast." sizes="(min-width: 550px) 550px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tRM8WvCI0aEdVGWGDpLS.png?auto=format&amp;w=1100 1100w" width="550" height="380" /><figcaption>In the Squoosh PWA the service worker broadcasts an update to the page when cache is ready, and the page displays "Ready to work offline" toast.</figcaption></figure>Using Workbox <a href="#using-workbox" class="w-headline-link">#</a>
--------------------------------------------------------------------

### Listen to service worker lifecycle events <a href="#listen-to-service-worker-lifecycle-events" class="w-headline-link">#</a>

`workbox-window` provides a straightforward interface to listen to [important service worker lifecycle events](https://developers.google.com/web/tools/workbox/modules/workbox-window#important_service_worker_lifecycle_moments). Under the hood, the library uses client-side APIs like [`updatefound`](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerRegistration/onupdatefound) and [statechange](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorker/onstatechange) and provides higher level event listeners in the `workbox-window` object, making it easier for the user to consume these events.

The following page code lets you detect every time a new version of the service worker is installed, so you can communicate it to the user:

    const wb = new Workbox('/sw.js');

    wb.addEventListener('installed', (event) => {
      if (event.isUpdate) {
        // Show "Update App" banner
      }
    });

    wb.register();

### Inform the page of changes in cache data <a href="#inform-the-page-of-changes-in-cache-data" class="w-headline-link">#</a>

The Workbox package [`workbox-broadcast-update`](https://developers.google.com/web/tools/workbox/modules/workbox-broadcast-update) provides a standard way of notifying window clients that a cached response has been updated. This is most commonly used along with the [StaleWhileRevalidate strategy](https://developers.google.com/web/tools/workbox/modules/workbox-strategies#stale-while-revalidate).

To broadcast updates add a `broadcastUpdate.BroadcastUpdatePlugin` to your strategy options in the service worker side:

    import {registerRoute} from 'workbox-routing';
    import {StaleWhileRevalidate} from 'workbox-strategies';
    import {BroadcastUpdatePlugin} from 'workbox-broadcast-update';

    registerRoute(
      ({url}) => url.pathname.startsWith('/api/'),
      new StaleWhileRevalidate({
        plugins: [
          new BroadcastUpdatePlugin(),
        ],
      })
    );

In your web app, you can listen for these events like so:

    navigator.serviceWorker.addEventListener('message', async (event) => {
      // Optional: ensure the message came from workbox-broadcast-update
      if (event.data.meta === 'workbox-broadcast-update') {
        const {cacheName, updatedUrl} = event.data.payload;

        // Do something with cacheName and updatedUrl.
        // For example, get the cached content and update
        // the content on the page.
        const cache = await caches.open(cacheName);
        const updatedResponse = await cache.match(updatedUrl);
        const updatedText = await updatedResponse.text();
      }
    });

Using browser APIs <a href="#using-browser-apis" class="w-headline-link">#</a>
------------------------------------------------------------------------------

If the functionality that Workbox provides is not enough for your needs, use the following browser APIs to implement **"broadcast updates"**:

### Broadcast Channel API <a href="#broadcast-channel-api" class="w-headline-link">#</a>

The service worker creates a [BroadcastChannel object](https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel) and starts sending messages to it. Any context (e.g. page) interested in receiving these messages can instantiate a `BroadcastChannel` object and implement a message handler to receive messages.

To inform the page when a new service worker is installed, use the following code:

    // Create Broadcast Channel to send messages to the page
    const broadcast = new BroadcastChannel('sw-update-channel');

    self.addEventListener('install', function (event) {
      // Inform the page every time a new service worker is installed
      broadcast.postMessage({type: 'CRITICAL_SW_UPDATE'});
    });

The page listens to these events by subscribing to the `sw-update-channel`:

    // Create Broadcast Channel and listen to messages sent to it
    const broadcast = new BroadcastChannel('sw-update-channel');

    broadcast.onmessage = (event) => {
      if (event.data && event.data.type === 'CRITICAL_SW_UPDATE') {
        // Show "update to refresh" banner to the user.
      }
    };

This is a simple technique, but its limitation is browser support: at the moment of this writing, [Safari doesn't support this API](https://caniuse.com/?search=Broadcastchannel).

### Client API <a href="#client-api" class="w-headline-link">#</a>

The [Client API](https://developer.mozilla.org/en-US/docs/Web/API/Client) provides a straightforward way of communicating with multiple clients from the service worker by iterating over an array of [`Client`](https://developer.mozilla.org/en-US/docs/Web/API/Client) objects.

Use the following service worker code to send a message to the last focused tab:

    // Obtain an array of Window client objects
    self.clients.matchAll(options).then(function (clients) {
      if (clients && clients.length) {
        // Respond to last focused tab
        clients[0].postMessage({type: 'MSG_ID'});
      }
    });

The page implements a message handler to intercept these messages:

    // Listen to messages
    navigator.serviceWorker.onmessage = (event) => {
         if (event.data && event.data.type === 'MSG_ID') {
             // Process response
       }
    };

Client API is a great option for cases like broadcasting information to multiple active tabs. The API is supported by all major browsers, but not all of its methods are. Check browser support before using it.

### Message Channel <a href="#message-channel" class="w-headline-link">#</a>

[Message Channel](https://developer.mozilla.org/en-US/docs/Web/API/Channel_Messaging_API) requires an initial configuration step, by passing a port from the page to the service worker, to establish a communication channel between them. The page instantiates a `MessageChannel` object and passes a port to the service worker, via the `postMessage()` interface:

    const messageChannel = new MessageChannel();

    // Init port
    navigator.serviceWorker.controller.postMessage({type: 'PORT_INITIALIZATION'}, [
      messageChannel.port2,
    ]);

The page listens to messages by implementing an "onmessage" handler on that port:

    // Listen to messages
    messageChannel.port1.onmessage = (event) => {
      // Process message
    };

The service worker receives the port and saves a reference to it:

    // Initialize
    let communicationPort;

    self.addEventListener('message', (event) => {
      if (event.data && event.data.type === 'PORT_INITIALIZATION') {
        communicationPort = event.ports[0];
      }
    });

From that point it can send messages to the page, by calling `postMessage()` in the reference to the port:

    // Communicate
    communicationPort.postMessage({type: 'MSG_ID' });

`MessageChannel` might be more complex to implement, due to the need of initializing ports, but it's supported by [all major browsers](https://caniuse.com/?search=channel%20messaging).

Next steps <a href="#next-steps" class="w-headline-link">#</a>
--------------------------------------------------------------

In this guide we explored one particular case of Window to service worker communication: **"broadcast updates"**. The examples explored include listening to important service worker lifecycle events, and communicating to the page about changes in content or cached data. You can think of more interesting use cases where the service worker proactively communicates with the page, without receiving any message previously.

For more patterns of Window and service worker communication check out:

-   [Imperative caching guide](/imperative-caching-guide): Calling a service worker from the page to cache resources in advance (e.g. in prefetching scenarios).
-   [Two-way communication](/two-way-communication-guide): Delegating a task to a service worker (e.g. a heavy download), and keeping the page informed on the progress.

Additional resources <a href="#additional-resources" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

-   [workbox-window](https://developers.google.com/web/tools/workbox/modules/workbox-window)
-   [workbox-broadcast-update](https://developers.google.com/web/tools/workbox/modules/workbox-broadcast-update)
-   [Workbox 4: Implementing refresh-to-update-version flow using the workbox-window module](https://medium.com/google-developer-experts/workbox-4-implementing-refresh-to-update-version-flow-using-the-workbox-window-module-41284967e79c)

<a href="/tags/service-worker/" class="w-chip">Service Worker</a> <a href="/tags/offline/" class="w-chip">Offline</a>

<span class="w-mr--sm">Last updated: Dec 8, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/broadcast-updates-guide/index.md)

<a href="/reliable" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
