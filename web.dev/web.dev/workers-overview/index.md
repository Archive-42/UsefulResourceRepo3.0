<img src="https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/Gfdeo856rHPAXJbXvPDi.jpeg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#workers-overview" class="w-toc__header--link">Workers overview</a>

- [How workers can improve your website](#how-workers-can-improve-your-website)
- [Web workers and service workers](#web-workers-and-service-workers)
- [Similarities](#similarities)
- [Differences](#differences)
- [Use cases](#use-cases)
- [Tools and libraries](#tools-and-libraries)
- [Comlink](#comlink)
- [Workbox](#workbox)
- [Next steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Workers overview

How web workers and service workers can improve the performance of your site, and when to use a web worker versus a service worker.

Dec 8, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

- <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
- <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

[<img src="https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Andrew Guan" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/HFWAhol3apcfNfuFxGZfjtLt2Yq2/oXpI60ZHNBOBos8bGJRn.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/andrewguan/)

<a href="/authors/andrewguan/" class="w-author__name-link">Andrew Guan</a>

- <a href="https://github.com/AndrewKGuan" class="w-author__link">GitHub</a>

This overview explains how web workers and service workers can improve the performance of your website, and when to use a web worker versus a service worker. Check out the rest of [this series](#next-steps) for specific patterns of window and service worker communication.

## How workers can improve your website <a href="#how-workers-can-improve-your-website" class="w-headline-link">#</a>

The browser uses a single thread (the [main thread](https://developer.mozilla.org/en-US/docs/Glossary/Main_thread)) to run all the JavaScript in a web page, as well as to perform tasks like rendering the page and performing garbage collection. Running excessive JavaScript code can block the main thread, delaying the browser from performing these tasks and leading to a poor user experience.

In iOS/Android application development, a common pattern to ensure that the app's main thread remains free to respond to user events is to offload operations to additional threads. In fact, in the latest versions of Android, blocking the main thread for too long [leads to an app crash](https://www.youtube.com/watch?v=eHjHlujp3Tg&feature=youtu.be&t=806).

On the web, JavaScript was designed around the concept of a single thread, and lacks capabilities needed to implement a multithreading model like the one apps have, like shared memory.

Despite these limitations, a similar pattern can be achieved in the web by using workers to run scripts in background threads, allowing them to perform tasks without interfering with the main thread. Workers are an entire JavaScript scope running on a separate thread, without any shared memory.

In this post you'll learn about two different types of workers (web workers and service workers), their similarities and differences, and the most common patterns for using them in production websites.

## <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format" sizes="(min-width: 728px) 728px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eN5kePr9U0aZMgCyekhJ.png?auto=format&amp;w=1456 1456w" width="728" height="418" /></figure>Web workers and service workers <a href="#web-workers-and-service-workers" class="w-headline-link">#</a>

### Similarities <a href="#similarities" class="w-headline-link">#</a>

[Web workers](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers) and [service workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers) are two types of workers available to websites. They have some things in common:

- Both run in a secondary thread, allowing JavaScript code to execute without blocking the main thread and the user interface.
- They don't have access to the [`Window`](https://developer.mozilla.org/en-US/docs/Web/API/Window) and [`Document`](https://developer.mozilla.org/en-US/docs/Web/API/Document) objects, so they can't interact with the DOM directly, and they have limited access to browser APIs.

### Differences <a href="#differences" class="w-headline-link">#</a>

One might think that most things that can be delegated to a web worker can be done in a service worker and vice versa, but there are important differences between them:

- Unlike web workers, service workers allow you to intercept network requests (via the [`fetch`](https://developer.mozilla.org/en-US/docs/Web/API/FetchEvent) event) and to listen for Push API events in the background (via the [`push`](https://developer.mozilla.org/en-US/docs/Web/API/PushEvent) event).
- A page can spawn multiple web workers, but a single service worker controls all the active tabs under the [scope](https://developer.mozilla.org/en-US/docs/Web/API/ServiceWorkerRegistration/scope) it was registered with.
- The lifespan of the web worker is tightly coupled to the tab it belongs to, while the [service worker's lifecycle](https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle) is independent of it. For that reason, closing the tab where a web worker is running will terminate it, while a service worker can continue running in the background, even when the site doesn't have any active tabs open.

For relatively short bits of work like sending a message, the browser won't likely terminate a service worker when there are no active tabs, but if the task takes too long the browser will terminate the service worker, otherwise it's a risk to the user's privacy and battery. APIs like [Background Fetch](https://developers.google.com/web/updates/2018/12/background-fetch), that can let you avoid the service worker's termination.

## Use cases <a href="#use-cases" class="w-headline-link">#</a>

The differences between both types of workers suggest in which situations one might want to use one or the other:

**Use cases for web workers** are more commonly related to offloading work (like [heavy computations](https://www.youtube.com/watch?v=mDdgfyRB5kg&feature=youtu.be&t=875)) to a secondary thread, to avoid blocking the UI.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format" sizes="(min-width: 500px) 500px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZCC24V8uqi6HfFjRzuPq.png?auto=format&amp;w=1000 1000w" width="500" height="175" /></figure>-   **Example:** the team that built the videogame [PROXX](https://proxx.app/) wanted to leave the main thread as free as possible to take care of user input and animations. To achieve that, they [used web workers](/proxx-announce/#web-workers) to run the game logic and state maintenance on a separate thread.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xXNCbahCtPrS8rw6uf1z.png?auto=format" sizes="(min-width: 225px) 225px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xXNCbahCtPrS8rw6uf1z.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xXNCbahCtPrS8rw6uf1z.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xXNCbahCtPrS8rw6uf1z.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xXNCbahCtPrS8rw6uf1z.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xXNCbahCtPrS8rw6uf1z.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xXNCbahCtPrS8rw6uf1z.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xXNCbahCtPrS8rw6uf1z.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xXNCbahCtPrS8rw6uf1z.png?auto=format&amp;w=450 450w" width="225" height="403" /></figure>**Service workers tasks** are generally more related to acting as a network proxy, handling background tasks, and things like caching and offline.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format" sizes="(min-width: 624px) 624px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/GmGcVnb2y1yNc4ZIFFQ8.png?auto=format&amp;w=1248 1248w" width="624" height="267" /></figure>**Example:** In a [podcast PWA](https://bgfetch-http203.glitch.me/), one might want to allow users to download complete episodes to listen to them while offline. A service worker, and, in particular, the [Background Fetch API](https://developers.google.com/web/updates/2018/12/background-fetch) can be used to that end. That way, if the user closes the tab while the episode is downloading, the task doesn't have to be interrupted.

## <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format" alt="The UI is updated to indicate the progress of a download (left). Thanks to service workers, the operation can continue running when all tabs have been closed (right)." sizes="(min-width: 500px) 500px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/oUH6K2JvcmfdAynTMjxQ.png?auto=format&amp;w=1000 1000w" width="500" height="310" /><figcaption>The UI is updated to indicate the progress of a download (left). Thanks to service workers, the operation can continue running when all tabs have been closed (right).</figcaption></figure>Tools and libraries <a href="#tools-and-libraries" class="w-headline-link">#</a>

Window and worker communication can be implemented by using different lower level APIs. Fortunately, there are libraries that abstract this process, taking care of the most common use cases. In this section, we'll cover two of them that take care of window to web workers and service workers respectively: [Comlink](https://github.com/GoogleChromeLabs/comlink) and [Workbox](https://developers.google.com/web/tools/workbox).

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format" sizes="(min-width: 500px) 500px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/MNMwX5KuJt5iOLZJbdO0.png?auto=format&amp;w=1000 1000w" width="500" height="269" /></figure>### Comlink <a href="#comlink" class="w-headline-link">#</a>

[Comlink](https://github.com/GoogleChromeLabs/comlink) is a small (1.6k) [RPC](https://en.wikipedia.org/wiki/Remote_procedure_call) library that takes care of many underlying details when building websites that use Web Workers. It has been used in websites like [PROXX](https://proxx.app/) and [Squoosh](https://squoosh.app/). A summary of its motivations and code samples can be found [here](https://surma.dev/things/when-workers/).

### Workbox <a href="#workbox" class="w-headline-link">#</a>

[Workbox](https://developers.google.com/web/tools/workbox) is a popular library to build websites that use service workers. It packages a set of best practices around things like caching, offline, background synchronization, etc. The [`workbox-window`](https://developers.google.com/web/tools/workbox/modules/workbox-window) module provides a convenient way to exchange messages between the service worker and the page.

## Next steps <a href="#next-steps" class="w-headline-link">#</a>

The rest of this series focuses on patterns for window and service worker communication:

- [Imperative caching guide](/imperative-caching-guide): Calling a service worker from the page to cache resources in advance (e.g. in prefetching scenarios).
- [Broadcast updates](/broadcast-updates-guide/): Calling the page from the service worker to inform about important updates (e.g. a new version of the website is available).
- [Two-way communication](/two-way-communication-guide/): Delegating a task to a service worker (e.g. a heavy download), and keeping the page informed on the progress.

For patterns of window and web worker communication check out: [Use web workers to run JavaScript off the browser's main thread](/off-main-thread/).

<a href="/tags/service-worker/" class="w-chip">Service Worker</a> <a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/offline/" class="w-chip">Offline</a>

<span class="w-mr--sm">Last updated: Dec 8, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/workers-overview/index.md)

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
