<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#create-an-offline-fallback-page" class="w-toc__header--link">Create an offline fallback page</a>
----------------------------------------------------------------------------------------------------------

-   [An offline fallback page with a custom service worker](#an-offline-fallback-page-with-a-custom-service-worker)
-   [Registering the service worker](#registering-the-service-worker)
-   [The service worker code](#the-service-worker-code)
-   [The offline fallback page](#the-offline-fallback-page)
-   [Demo](#demo)
-   [Side note on making your app installable](#side-note-on-making-your-app-installable)
-   [Side note on serving an offline fallback page with Workbox.js](#side-note-on-serving-an-offline-fallback-page-with-workbox.js)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Create an offline fallback page
===============================

Sep 24, 2020 <span class="w-author__separator">•</span> Updated May 19, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/progressive-web-apps" class="w-post-signpost__link">Progressive Web Apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

-   <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
-   <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
-   <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Pete LePage" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/petelepage/)

<a href="/authors/petelepage/" class="w-author__name-link">Pete LePage</a>

-   <a href="https://twitter.com/petele" class="w-author__link">Twitter</a>
-   <a href="https://github.com/petele" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@petele" class="w-author__link">Glitch</a>
-   <a href="https://petelepage.com" class="w-author__link">Blog</a>

What do the Google Assistant app, the Slack app, the Zoom app, and almost any other platform-specific app on your phone or computer have in common? Right, they always at least give you *something*. Even when you do not have a network connection, you can still open the Assistant app, or enter Slack, or launch Zoom. You might not get anything particularly meaningful or even be unable to achieve what you wanted to achieve, but at least you get *something* and the app is in control.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format" alt="Google Assistant." sizes="(min-width: 621px) 621px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gr49coayhLfP1UVJ2EeR.jpg?auto=format&amp;w=1242 1242w" width="621" height="1344" /><figcaption>Google Assistant.</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format" alt="Slack." sizes="(min-width: 621px) 621px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/D4P00CQ15IE0plUEY3di.jpg?auto=format&amp;w=1242 1242w" width="621" height="1344" /><figcaption>Slack.</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format" alt="Zoom." sizes="(min-width: 621px) 621px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gw1LQG4JNYUDxQ2NOJHC.jpg?auto=format&amp;w=1242 1242w" width="621" height="1344" /><figcaption>Zoom.</figcaption></figure>With platform-specific apps, even when you do not have a network connection, you never get nothing.

In contrast, on the Web, traditionally you get nothing when you are offline. Chrome gives you the [offline dino game](https://www.blog.google/products/chrome/chrome-dino/), but that is it.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format" alt="Google Chrome for iOS." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yEf0wzIQ1hIf85xtUwse.png?auto=format&amp;w=1600 1600w" width="800" height="1731" /><figcaption>Google Chrome for iOS.</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format" alt="Google Chrome for macOS." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vrqfLVP132LcydIWcYbh.png?auto=format&amp;w=1600 1600w" width="800" height="607" /><figcaption>Google Chrome for macOS.</figcaption></figure>On the Web, when you do not have a network connection, by default you get nothing.

An offline fallback page with a custom service worker <a href="#an-offline-fallback-page-with-a-custom-service-worker" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------

It does not have to be this way, though. Thanks to [service workers and the Cache Storage API](/service-workers-cache-storage/), you can provide a customized offline experience for your users. This can be a simple branded page with the information that the user is currently offline, but it can just as well be a more creative solution, like, for example, the famous [trivago offline maze game](https://www.trivago.com/offline) with a manual **Reconnect** button and an automatic reconnection attempt countdown.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format" alt="The trivago offline maze." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0yvun9EV5758sRO9wSgY.png?auto=format&amp;w=1600 1600w" width="800" height="616" /><figcaption>The trivago offline maze.</figcaption></figure>### Registering the service worker <a href="#registering-the-service-worker" class="w-headline-link">#</a>

The way to make this happen is through a service worker. You can register a service worker from your main page like in the code sample below. Usually you do this once your app has loaded.

    window.addEventListener("load", () => {
      if ("serviceWorker" in navigator) {
        navigator.serviceWorker.register("service-worker.js");
      }
    });

### The service worker code <a href="#the-service-worker-code" class="w-headline-link">#</a>

The contents of the actual service worker file may seem a little involved at first sight, but the comments in the sample below should clear things up. The core idea is to pre-cache a file named `offline.html` that gets only served on *failing* navigation requests, and to let the browser handle all other cases:

    /*
    Copyright 2015, 2019, 2020, 2021 Google LLC. All Rights Reserved.
     Licensed under the Apache License, Version 2.0 (the "License");
     you may not use this file except in compliance with the License.
     You may obtain a copy of the License at
     http://www.apache.org/licenses/LICENSE-2.0
     Unless required by applicable law or agreed to in writing, software
     distributed under the License is distributed on an "AS IS" BASIS,
     WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
     See the License for the specific language governing permissions and
     limitations under the License.
    */

    // Incrementing OFFLINE_VERSION will kick off the install event and force
    // previously cached resources to be updated from the network.
    // This variable is intentionally declared and unused.
    // Add a comment for your linter if you want:
    // eslint-disable-next-line no-unused-vars
    const OFFLINE_VERSION = 1;
    const CACHE_NAME = "offline";
    // Customize this with a different URL if needed.
    const OFFLINE_URL = "offline.html";

    self.addEventListener("install", (event) => {
      event.waitUntil(
        (async () => {
          const cache = await caches.open(CACHE_NAME);
          // Setting {cache: 'reload'} in the new request will ensure that the
          // response isn't fulfilled from the HTTP cache; i.e., it will be from
          // the network.
          await cache.add(new Request(OFFLINE_URL, { cache: "reload" }));
        })()
      );
      // Force the waiting service worker to become the active service worker.
      self.skipWaiting();
    });

    self.addEventListener("activate", (event) => {
      event.waitUntil(
        (async () => {
          // Enable navigation preload if it's supported.
          // See https://developers.google.com/web/updates/2017/02/navigation-preload
          if ("navigationPreload" in self.registration) {
            await self.registration.navigationPreload.enable();
          }
        })()
      );

      // Tell the active service worker to take control of the page immediately.
      self.clients.claim();
    });

    self.addEventListener("fetch", (event) => {
      // We only want to call event.respondWith() if this is a navigation request
      // for an HTML page.
      if (event.request.mode === "navigate") {
        event.respondWith(
          (async () => {
            try {
              // First, try to use the navigation preload response if it's supported.
              const preloadResponse = await event.preloadResponse;
              if (preloadResponse) {
                return preloadResponse;
              }

              // Always try the network first.
              const networkResponse = await fetch(event.request);
              return networkResponse;
            } catch (error) {
              // catch is only triggered if an exception is thrown, which is likely
              // due to a network error.
              // If fetch() returns a valid HTTP response with a response code in
              // the 4xx or 5xx range, the catch() will NOT be called.
              console.log("Fetch failed; returning offline page instead.", error);

              const cache = await caches.open(CACHE_NAME);
              const cachedResponse = await cache.match(OFFLINE_URL);
              return cachedResponse;
            }
          })()
        );
      }

      // If our if() condition is false, then this fetch handler won't intercept the
      // request. If there are any other fetch handlers registered, they will get a
      // chance to call event.respondWith(). If no fetch handlers call
      // event.respondWith(), the request will be handled by the browser as if there
      // were no service worker involvement.
    });

### The offline fallback page <a href="#the-offline-fallback-page" class="w-headline-link">#</a>

The `offline.html` file is where you can get creative and adapt it to your needs and add your branding. The example below shows the bare minimum of what is possible. It demonstrates both manual reload based on a button press as well as automatic reload based on the [`online` event](https://developer.mozilla.org/en-US/docs/Web/API/Window/online_event) and regular server polling.

**Gotchas!**

You need to cache all resources required by your offline page. One way to deal with this is to inline everything, so the offline page is self-contained. This is what I do in the example below.

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <meta charset="utf-8" />
        <meta http-equiv="X-UA-Compatible" content="IE=edge" />
        <meta name="viewport" content="width=device-width, initial-scale=1" />

        <title>You are offline</title>

        <!-- Inline the page's stylesheet. -->
        <style>
          body {
            font-family: helvetica, arial, sans-serif;
            margin: 2em;
          }

          h1 {
            font-style: italic;
            color: #373fff;
          }

          p {
            margin-block: 1rem;
          }

          button {
            display: block;
          }
        </style>
      </head>
      <body>
        <h1>You are offline</h1>

        <p>Click the button below to try reloading.</p>
        <button type="button">⤾ Reload</button>

        <!-- Inline the page's JavaScript file. -->
        <script>
          // Manual reload feature.
          document.querySelector("button").addEventListener("click", () => {
            window.location.reload();
          });

          // Listen to changes in the network state, reload when online.
          // This handles the case when the device is completely offline.
          window.addEventListener('online', () => {
            window.location.reload();
          });

          // Check if the server is responding and reload the page if it is.
          // This handles the case when the device is online, but the server
          // is offline or misbehaving.
          async function checkNetworkAndReload() {
            try {
              const response = await fetch('.');
              // Verify we get a valid response from the server
              if (response.status >= 200 && response.status < 500) {
                window.location.reload();
                return;
              }
            } catch {
              // Unable to connect to the server, ignore.
            }
            window.setTimeout(checkNetworkAndReload, 2500);
          }

          checkNetworkAndReload();
        </script>
      </body>
    </html>

Demo <a href="#demo" class="w-headline-link">#</a>
--------------------------------------------------

You can see the offline fallback page in action in the [demo](https://offline-fallback-demo.glitch.me/index.html) embedded below. If you are interested, you can explore the [source code](https://glitch.com/edit/#!/offline-fallback-demo) on Glitch.

### Side note on making your app installable <a href="#side-note-on-making-your-app-installable" class="w-headline-link">#</a>

Now that your site has an offline fallback page, you might wonder about next steps. To make your app installable, you need to add a [web app manifest](/add-manifest/) and optionally come up with an [install strategy](/define-install-strategy/).

### Side note on serving an offline fallback page with Workbox.js <a href="#side-note-on-serving-an-offline-fallback-page-with-workbox.js" class="w-headline-link">#</a>

You may have heard of [Workbox.js](https://developers.google.com/web/tools/workbox). Workbox.js is a set of JavaScript libraries for adding offline support to web apps. If you prefer to write less service worker code yourself, you can use the Workbox.js recipe for an [offline page only](https://developers.google.com/web/tools/workbox/guides/advanced-recipes#offline_page_only).

Up next, learn [how to define an install strategy](/define-install-strategy/) for your app.

<a href="/tags/progressive-web-apps/" class="w-chip">Progressive Web Apps</a>

<span class="w-mr--sm">Last updated: May 19, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/progressive-web-apps/offline-fallback-page/index.md)

<a href="/progressive-web-apps" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
