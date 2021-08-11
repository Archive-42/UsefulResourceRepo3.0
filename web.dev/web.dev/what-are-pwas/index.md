





<a href="#what-are-progressive-web-apps" class="w-toc__header--link">What are Progressive Web Apps?</a>
-------------------------------------------------------------------------------------------------------

-   [The three app pillars](#the-three-app-pillars)
-   [Capable](#capable)
-   [Reliable](#reliable)
-   [Installable](#installable)
-   [The best of both worlds](#the-best-of-both-worlds)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

What are Progressive Web Apps?
==============================

Jan 6, 2020 <span class="w-author__separator">•</span> Updated Feb 24, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/progressive-web-apps" class="w-post-signpost__link">Progressive Web Apps</a>

[<img src="https://web-dev.imgix.net/image/admin/5kuER6QRWs54zbYIJ4zS.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Sam Richard" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/5kuER6QRWs54zbYIJ4zS.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/5kuER6QRWs54zbYIJ4zS.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/5kuER6QRWs54zbYIJ4zS.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/5kuER6QRWs54zbYIJ4zS.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/5kuER6QRWs54zbYIJ4zS.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/samrichard/)

<a href="/authors/samrichard/" class="w-author__name-link">Sam Richard</a>

-   <a href="https://twitter.com/snugug" class="w-author__link">Twitter</a>
-   <a href="https://github.com/snugug" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@snugug" class="w-author__link">Glitch</a>
-   <a href="https://snugug.com" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Pete LePage" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/petelepage/)

<a href="/authors/petelepage/" class="w-author__name-link">Pete LePage</a>

-   <a href="https://twitter.com/petele" class="w-author__link">Twitter</a>
-   <a href="https://github.com/petele" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@petele" class="w-author__link">Glitch</a>
-   <a href="https://petelepage.com" class="w-author__link">Blog</a>

The web is an incredible platform. Its mix of ubiquity across devices and operating systems, its user-centered security model, and the fact that neither its specification nor its implementation is controlled by a single company makes the web a unique platform to develop software on. Combined with its inherent linkability, it's possible to search it and share what you've found with anyone, anywhere. Whenever you go to a website, it's up-to-date, and your experience with that site can be as ephemeral or as permanent as you'd like. Web applications can reach *anyone, anywhere, on any device* with a single codebase.

Platform-specific applications, are known for being incredibly rich and reliable. They're ever-present, on home screens, docks, and taskbars. They work regardless of network connection. They launch in their own standalone experience. They can read and write files from the local file system, access hardware connected via USB, serial or bluetooth, and even interact with data stored on your device, like contacts and calendar events. In these applications, you can do things like take pictures, see playing songs listed on the home screen, or control song playback while in another app. Platform-specific applications feel like *part* of the device they run on.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DKtUFjXLJbiiruKA9P1.svg" alt="Capabilities vs. reach of platform-specific apps, web app, and progressive web apps." width="370" height="367" /><figcaption>Capabilities vs. reach of platform-specific apps, web app, and progressive web apps.</figcaption></figure>If you think about platform-specific apps and web apps in terms of capabilities and reach, platform-specific apps represent the best of capabilities whereas web apps represent the best of reach. So where do Progressive Web Apps fit in?

Progressive Web Apps (PWA) are built and enhanced with modern APIs to deliver enhanced capabilities, reliability, and installability while reaching *anyone, anywhere, on any device* with a single codebase.

The three app pillars <a href="#the-three-app-pillars" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

Progressive Web Apps are web applications that have been designed so they are capable, reliable, and installable. These three pillars transform them into an experience that feels like a platform-specific application.

### Capable <a href="#capable" class="w-headline-link">#</a>

The web is quite capable in its own right today. For example, you can build a hyper-local video chat app using WebRTC, geolocation, and push notifications. You can make that app installable and take those conversations virtual with WebGL and WebVR. With the introduction of WebAssembly, developers can tap into other ecosystems, like C, C++, and Rust, and bring decades of work and capabilities to the web too. [Squoosh.app](https://squoosh.app/), for instance, leverages this for its advanced image compression.

Until recently, only platform-specific apps could really lay claim to these capabilities. While some capabilities are still out of the web's reach, new and upcoming APIs are looking to change that, expanding what the web can do with features like file system access, media controls, app badging, and full clipboard support. All of these capabilities are built with the web's secure, user-centric permission model, ensuring that going to a website is never a scary proposition for users.

Between modern APIs, WebAssembly, and new and upcoming APIs, web applications are more capable than ever, and those capabilities are only growing.

### Reliable <a href="#reliable" class="w-headline-link">#</a>

A reliable Progressive Web App feels fast and dependable regardless of the network.

Speed is critical for getting users to *use* your experience. In fact, as page load times go from 1 second to ten seconds, the probability of a user bouncing [increases by 123%](https://www.thinkwithgoogle.com/marketing-resources/data-measurement/mobile-page-speed-new-industry-benchmarks/). Performance doesn't stop after the `onload` event. Users should never wonder whether their interaction—for example, clicking a button—was registered or not. Scrolling and animation should feel smooth. Performance affects your entire experience, from how users perceive your application to how it actually performs.

Finally, reliable applications need to be usable regardless of network connection. Users expect apps to start up on slow or flaky network connections or even when offline. They expect the most recent content they've interacted with, like media tracks or tickets and itineraries, to be available and usable even if getting a request to your server is hard. When a request isn't possible, they expect to be told there's trouble instead of silently failing or crashing.

Users love apps that respond to interaction in the blink of an eye, and an experience they can depend on.

### Installable <a href="#installable" class="w-headline-link">#</a>

Installed Progressive Web Apps run in a standalone window instead of a browser tab. They're launchable from on the user's home screen, dock, taskbar, or shelf. It's possible to search for them on a device and jump between them with the app switcher, making them feel like part of the device they're installed on.

New capabilities open up after a web app is installed. Keyboard shortcuts usually reserved when running in the browser, become available. Progressive Web Apps can register to accept content from other applications, or to be the default application to handle different types of files.

When a Progressive Web App moves out of a tab and into a standalone app window, it transforms how users think about it and interact with it.

The best of both worlds <a href="#the-best-of-both-worlds" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

At their heart, Progressive Web Apps are just web applications. Using progressive enhancement, new capabilities are enabled in modern browsers. Using service workers and a web app manifest, your web application becomes reliable and installable. If the new capabilities aren't available, users still get the core experience.

The numbers don't lie! Companies that have launched Progressive Web Apps have seen impressive results. For example, Twitter saw a 65% increase in pages per session, 75% more Tweets, and a 20% decrease in bounce rate, all while reducing the size of their app by over 97%. After switching to a PWA, Nikkei saw 2.3 times more organic traffic, 58% more subscriptions, and 49% more daily active users. Hulu replaced their platform-specific desktop experience with a Progressive Web App and saw a 27% increase in return visits.

Progressive Web Apps provide you with a unique opportunity to deliver a web experience your users will love. Using the latest web features to bring enhanced capabilities and reliability, Progressive Web Apps allow what you build to be installed by *anyone, anywhere, on any device* with a single codebase.

<a href="/tags/progressive-web-apps/" class="w-chip">Progressive Web Apps</a>

<span class="w-mr--sm">Last updated: Feb 24, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/progressive-web-apps/what-are-pwas/index.md)

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
