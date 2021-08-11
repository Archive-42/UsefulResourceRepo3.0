<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#two-way-communication-with-service-workers" class="w-toc__header--link">Two-way communication with service workers</a>
--------------------------------------------------------------------------------------------------------------------------------

-   [Using Workbox](#using-workbox)
-   [Using Browser APIs](#using-browser-apis)
-   [Broadcast Channel API](#broadcast-channel-api)
-   [Client API](#channel-api)
-   [Message Channel](#message-channel)
-   [Advanced APIs: Background Sync and Background Fetch](#advanced-apis:-background-sync-and-background-fetch)
-   [Next steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Two-way communication with service workers
==========================================

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

In some cases, a web app might need to establish a **two-way** communication channel between the page and the service worker.

For example: in a podcast PWA one could build a feature to let the user [download episodes for offline consumption](/app-like-pwas/#proactive-background-downloading) and allow the service worker to keep the page regularly informed about the progress, so the [main thread](https://developer.mozilla.org/en-US/docs/Glossary/Main_thread) can update the UI.

In this guide we'll explore the different ways of implementing a **two-way** communication between the [Window](https://developer.mozilla.org/en-US/docs/Web/API/Window) and [service worker](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API) context, by exploring different APIs, the [Workbox library](https://developers.google.com/web/tools/workbox), as well as some advanced cases.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HIbZyXbQNijm1S4eQlEv.png?auto=format&amp;w=1600 1600w" width="800" height="310" /></figure>Check out [Workers overview](/workers-overview/) for a high-level explanation of when to use web workers versus service workers and the rest of the [Communicate with workers](/reliable/#communicate-with-workers) series for guides on other common use cases.

Using Workbox <a href="#using-workbox" class="w-headline-link">#</a>
--------------------------------------------------------------------

[`workbox-window`](https://developers.google.com/web/tools/workbox/modules/workbox-window) is a set of modules of the [Workbox library](https://developers.google.com/web/tools/workbox) that are intended to run in the window context. The [`Workbox`](https://developers.google.com/web/tools/workbox/reference-docs/latest/module-workbox-window.Workbox) class provides a `messageSW()` method to send a message to the instance's registered service worker and await a response.

The following page code creates a new `Workbox` instance and sends a message to the service worker to obtain its version:

    const wb = new Workbox('/sw.js');
    wb.register();

    const swVersion = await wb.messageSW({type: 'GET_VERSION'});
    console.log('Service Worker version:', swVersion);

The service worker implements a message listener on the other end, and responds to the registered service worker:

    const SW_VERSION = '1.0.0';

    addEventListener('message', (event) => {
      if (event.data.type === 'GET_VERSION') {
        event.ports[0].postMessage(SW_VERSION);
      }
    });

Under the hood the library uses a browser API that we'll review in the next section: [Message Channel](https://developer.mozilla.org/en-US/docs/Web/API/Channel_Messaging_API), but abstracts many implementation details, making it easier to use, while leveraging the [wide browser support](https://caniuse.com/mdn-api_messagechannel_port1) this API has.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format" sizes="(min-width: 700px) 700px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DxyWzq96JQCU3hADZiN8.png?auto=format&amp;w=1400 1400w" width="700" height="410" /></figure>Using Browser APIs <a href="#using-browser-apis" class="w-headline-link">#</a>
------------------------------------------------------------------------------

If the Workbox library is not enough for your needs, there are several lower-level APIs available to implement **"two-way"** communication between pages and service workers. They have some similarities and differences:

Similarities:

-   In all cases the communication starts on one end via the `postMessage()` interface and is received on the other end by implementing a `message` handler.
-   In practice, all the available APIs allow us to implement the same use cases, but some of them might simplify development in some scenarios.

Differences:

-   They have different ways of identifying the other side of the communication: some of them use an explicit reference to the other context, while others can communicate implicitly via a proxy object instantiated on each side.
-   Browser support varies among them.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format" sizes="(min-width: 600px) 600px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nPYcdQbxAezigMiuoLJg.png?auto=format&amp;w=1200 1200w" width="600" height="273" /></figure>### Broadcast Channel API <a href="#broadcast-channel-api" class="w-headline-link">#</a>

The [Broadcast Channel API](https://developer.mozilla.org/en-US/docs/Web/API/Broadcast_Channel_API) allows basic communication between browsing contexts via [BroadcastChannel objects](https://developer.mozilla.org/en-US/docs/Web/API/BroadcastChannel).

To implement it, first, each context has to instantiate a `BroadcastChannel` object with the same ID and send and receive messages from it:

    const broadcast = new BroadcastChannel('channel-123');

The BroadcastChannel object exposes a `postMessage()` interface to send a message to any listening context:

    //send message
    broadcast.postMessage({ type: 'MSG_ID', });

Any browser context can listen to messages via the `onmessage` method of the `BroadcastChannel` object:

    //listen to messages
    broadcast.onmessage = (event) => {
      if (event.data && event.data.type === 'MSG_ID') {
        //process message...
      }
    };

As seen, there's no explicit reference to a particular context, so there's no need of obtaining a reference first to the service worker or any particular client.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format" sizes="(min-width: 700px) 700px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uWl3NVD3rxbSoA0JxvuN.png?auto=format&amp;w=1400 1400w" width="700" height="355" /></figure>The disadvantage is that, at the moment of this writing, the API has support from Chrome, Firefox and Edge, but other browsers, like Safari, [don't support it yet](https://caniuse.com/?search=broadcastchannel).

### Client API <a href="#channel-api" class="w-headline-link">#</a>

The [Client API](https://developer.mozilla.org/en-US/docs/Web/API/Client) allows you to obtain a reference to all the [`WindowClient`](https://developer.mozilla.org/en-US/docs/Web/API/WindowClient) objects representing the active tabs that the service worker is controlling.

Since the page is controlled by a single service worker, it listens to and sends messages to the active service worker directly via the `serviceWorker` interface:

    //send message
    navigator.serviceWorker.controller.postMessage({
      type: 'MSG_ID',
    });

    //listen to messages
    navigator.serviceWorker.onmessage = (event) => {
      if (event.data && event.data.type === 'MSG_ID') {
        //process response
      }
    };

Similarly, the service worker listens to messages by implementing an `onmessage` listener:

    //listen to messages
    self.addEventListener('message', (event) => {
      if (event.data && event.data.type === 'MSG_ID') {
        //Process message
      }
    });

To communicate back with any of its clients, the service worker obtains an array of [`WindowClient`](https://developer.mozilla.org/en-US/docs/Web/API/WindowClient) objects by executing methods such as [`Clients.matchAll()`](https://developer.mozilla.org/en-US/docs/Web/API/Clients/matchAll) and [`Clients.get()`](https://developer.mozilla.org/en-US/docs/Web/API/Clients/get). Then it can `postMessage()` any of them:

    //Obtain an array of Window client objects
    self.clients.matchAll(options).then(function (clients) {
      if (clients && clients.length) {
        //Respond to last focused tab
        clients[0].postMessage({type: 'MSG_ID'});
      }
    });

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format" sizes="(min-width: 500px) 500px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oApyHsmljr1KkBW85Wv9.png?auto=format&amp;w=1000 1000w" width="500" height="348" /></figure>`Client API` is a good option to communicate easily with all the active tabs from a service worker in a relatively straightforward way. The API is supported by [all major browsers](https://wpt.fyi/results/service-workers/service-worker/client-id.https.html?label=experimental&label=master&aligned), but not all its methods might be available, so make sure to check browser support before implementing it in your site.

In this guide we focus mostly on reliability use cases. Another interesting usage of this API is synchronizing data across documents via a service worker. Check out [this episode of HTTP 203](https://www.youtube.com/watch?v=9UNwHmagedE&feature=youtu.be&t=697) to know more about it.

### Message Channel <a href="#message-channel" class="w-headline-link">#</a>

[Message Channel](https://developer.mozilla.org/en-US/docs/Web/API/Channel_Messaging_API) requires defining and passing a port from one context to another to establish a **two-way** communication channel.

To initialize the channel, the page instantiates a [`MessageChannel`](https://developer.mozilla.org/en-US/docs/Web/API/MessageChannel/MessageChannel) object and uses it to send a port to the registered service worker. The page also implements an `onmessage` listener on it to receive messages from the other context:

    const messageChannel = new MessageChannel();

    //Init port
    navigator.serviceWorker.controller.postMessage({type: 'PORT_INITIALIZATION'}, [
      messageChannel.port2,
    ]);

    //Listen to messages
    messageChannel.port1.onmessage = (event) => {
      // Process message
    };

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format" sizes="(min-width: 600px) 600px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/THMp68FKAah5qYIsiFOk.png?auto=format&amp;w=1200 1200w" width="600" height="344" /></figure>The service worker receives the port, saves a reference to it and uses it to send a message to the other side:

    let communicationPort;

    //Save reference to port
    self.addEventListener('message', (event) => {
      if (event.data && event.data.type === 'PORT_INITIALIZATION') {
        communicationPort = event.ports[0];
      }
    });

    //Send messages
    communicationPort.postMessage({type: 'MSG_ID'});

`MessageChannel` is currently supported by [all major browsers](https://caniuse.com/?search=channel).

### Advanced APIs: Background Sync and Background Fetch <a href="#advanced-apis:-background-sync-and-background-fetch" class="w-headline-link">#</a>

In this guide we explored ways of implementing **two-way** communication techniques, for relatively simple cases, like passing a string message describing the operation to perform, or a list of URLs to cache from one context to the other. In this section we'll explore two APIs to handle specific scenarios: lack of connectivity and long downloads.

#### Background Sync <a href="#background-sync" class="w-headline-link">#</a>

A chat app might want to make sure that messages are never lost due to bad connectivity. The [Background Sync API](https://developers.google.com/web/updates/2015/12/background-sync) lets you defer actions to be retried when the user has stable connectivity. This is useful for ensuring that whatever the user wants to send, is actually sent.

Instead of the `postMessage()` interface, the page registers a `sync`:

    navigator.serviceWorker.ready.then(function (swRegistration) {
      return swRegistration.sync.register('myFirstSync');
    });

The service worker then listens for the `sync` event to process the message:

    self.addEventListener('sync', function (event) {
      if (event.tag == 'myFirstSync') {
        event.waitUntil(doSomeStuff());
      }
    });

The function `doSomeStuff()` should return a promise indicating the success/failure of whatever it's trying to do. If it fulfills, the sync is complete. If it fails, another sync will be scheduled to retry. Retry syncs also wait for connectivity, and employ an exponential back-off.

Once the operation has been performed, the service worker can then communicate back with the page to update the UI, by using any of the communication APIs explored earlier.

Google search uses Background Sync to persist failed queries due to bad connectivity, and retry them later when the user is online. Once the operation is performed, they communicate the result to the user via a web push notification:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format" sizes="(min-width: 700px) 700px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eMbvk9IRoaAggs8t5CbF.png?auto=format&amp;w=1400 1400w" width="700" height="381" /></figure>Check out [Resilient search experiences](/resilient-search-experiences/) to learn how to implement this feature using [Workbox Background Sync](https://developers.google.com/web/tools/workbox/modules/workbox-background-sync).

#### Background Fetch <a href="#background-fetch" class="w-headline-link">#</a>

For relatively short bits of work like sending a message, or a list of URLs to cache, the options explored so far are a good choice. If the task takes too long the browser will kill the service worker, otherwise it's a risk to the user's privacy and battery.

The [Background Fetch API](https://developers.google.com/web/updates/2018/12/background-fetch) allows you to offload a long task to a service worker, like downloading movies, podcasts, or levels of a game.

To communicate to the service worker from the page, use `backgroundFetch.fetch`, instead of `postMessage()`:

    navigator.serviceWorker.ready.then(async (swReg) => {
      const bgFetch = await swReg.backgroundFetch.fetch(
        'my-fetch',
        ['/ep-5.mp3', 'ep-5-artwork.jpg'],
        {
          title: 'Episode 5: Interesting things.',
          icons: [
            {
              sizes: '300x300',
              src: '/ep-5-icon.png',
              type: 'image/png',
            },
          ],
          downloadTotal: 60 * 1024 * 1024,
        },
      );
    });

The `BackgroundFetchRegistration` object allows the page listen to the `progress` event to follow the progress of the download:

    bgFetch.addEventListener('progress', () => {
      // If we didn't provide a total, we can't provide a %.
      if (!bgFetch.downloadTotal) return;

      const percent = Math.round(
        (bgFetch.downloaded / bgFetch.downloadTotal) * 100,
      );
      console.log(`Download progress: ${percent}%`);
    });

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format" alt="The UI is updated to indicate the progress of a download (left). Thanks to service workers, the operation can continue running when all tabs have been closed (right)." sizes="(min-width: 700px) 700px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Ii1koJyCl0drJyewTIxV.png?auto=format&amp;w=1400 1400w" width="700" height="434" /><figcaption>The UI is updated to indicate the progress of a download (left). Thanks to service workers, the operation can continue running when all tabs have been closed (right).</figcaption></figure>Check out the [Background Fetch guide](https://developers.google.com/web/updates/2018/12/background-fetch), which includes an [example podcast app](https://bgfetch-http203.glitch.me/) along with its [Glitch code](https://glitch.com/edit/#!/bgfetch-http203).

Next steps <a href="#next-steps" class="w-headline-link">#</a>
--------------------------------------------------------------

In this guide we explored the most general case of communication between page and service workers (bidirectional communication).

Many times, one might need only one context to communicate with the other, without receiving a response. Check out the following guides for guidance how to implement unidirectional techniques in your pages from and to the service worker, along with use cases and production examples:

-   [Imperative caching guide](/imperative-caching-guide): Calling a service worker from the page to cache resources in advance (e.g. in prefetching scenarios).
-   [Broadcast updates](/broadcast-updates-guide): Calling the page from the service worker to inform about important updates (e.g. a new version of the webapp is available).

<a href="/tags/service-worker/" class="w-chip">Service Worker</a> <a href="/tags/offline/" class="w-chip">Offline</a>

<span class="w-mr--sm">Last updated: Dec 8, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/two-way-communication-guide/index.md)

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
