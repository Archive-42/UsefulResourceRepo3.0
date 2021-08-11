<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#programming-the-mini-app-way" class="w-toc__header--link">Programming the mini app way</a>
----------------------------------------------------------------------------------------------------

-   [What has worked well for mini apps](#what-has-worked-well-for-mini-apps)
-   [Components](#components)
-   [Model-view-viewmodel](#model-view-viewmodel)
-   [Page-wise thinking](#page-wise-thinking)
-   [Build process](#build-process)
-   [Powerful capabilities](#powerful-capabilities)
-   [Acknowledgements](#acknowledgements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Programming the mini app way
============================

Mar 3, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/mini-apps" class="w-post-signpost__link">Mini apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

-   <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
-   <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
-   <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

This post is part of an article collection where each article builds upon previous articles. If you just landed here, you may want to start reading from the [beginning](/mini-app-super-apps/).

What has worked well for mini apps <a href="#what-has-worked-well-for-mini-apps" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------

In this chapter, I want to look at lessons I learned from researching mini apps from a web developer's point of view, or answer the question what does it mean to develop the mini app way.

Components <a href="#components" class="w-headline-link">#</a>
--------------------------------------------------------------

Rather than reinvent the wheel and make developers build yet another implementation of common UI paradigms like tabs, accordions, carousels, etc., mini apps just ship with a default selection of components that is extensible in case you need more. On the web, there are likewise many options, some of which I have listed in the [chapter on mini app components](/mini-app-components/#web-components). In an ideal world, component libraries on the web were built in a way that you could mix them freely. In practice, too many times, there is a certain lock-in regarding a design system you need to buy in to when you use a component, or the component library is distributed in a way that it is all or nothing, but no individual components can be easily added to a project. There are, however, atomic components that you can use in isolation, or libraries like [generic-components](https://github.com/thepassle/generic-components) that are unstyled on purpose. Finding an using those seems like a good idea.

Model-view-viewmodel <a href="#model-view-viewmodel" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

The [model–view–viewmodel](/mini-app-markup-styling-and-scripting/#markup-languages) (MVVM) architectural pattern—that facilitates the separation of the development of the graphical user interface (the view) via a markup language from the development of the back-end logic (the model)—means the view is not dependent on any specific model platform. While there are some documented [disadvantages](https://docs.microsoft.com/en-us/archive/blogs/johngossman/advantages-and-disadvantages-of-m-v-vm) of the pattern, in general it works really well for applications of the complexity of mini apps. It can shine especially with rich templating libraries (see [next chapter](mini-app-example-project/)).

Page-wise thinking <a href="#page-wise-thinking" class="w-headline-link">#</a>
------------------------------------------------------------------------------

Debugging mini apps shows that they are essentially multi-page applications (MPA). This has many advantages, like, for example, it allows for trivial routing and conflict-free per-page styling. People have [successfully applied MPA architectures](https://medium.com/elemefe/upgrading-ele-me-to-progressive-web-app-2a446832e509) to Progressive Web Apps. Thinking in pages also helps manage resources like each page's CSS and JavaScript files, and other assets like images and videos. Most importantly, building this way means you get route-based code splitting for free if you do not load anything else. In that case, each page by definition strictly only loads what it needs to function.

Build process <a href="#build-process" class="w-headline-link">#</a>
--------------------------------------------------------------------

Mini apps have [no visible build process](/mini-app-project-structure-lifecycle-and-bundling/#the-build-process). On the web, modern build tools like [Snowpack](https://www.snowpack.dev/) leverage JavaScript's built-in [module system](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) (known as ESM) to avoid unnecessary work and stay fast no matter how big a project grows. While it is early days for technologies like [Web Bundles](/web-bundles/), it is something that can be easily added to the build process.

Powerful capabilities <a href="#powerful-capabilities" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

The web platform has gained many [new capabilities](/tags/capabilities/) recently. Access to [devices](/tags/devices/) via [Bluetooth](/bluetooth/), [USB](/usb/), [HID](/hid/), [serial](/serial/), and [NFC](/nfc/) is all possible now. Where mini apps run in WebViews and depend on a [JavaScript bridge](/mini-app-markup-styling-and-scripting/#javascript-bridge-api), on the web, these powerful capabilities are available directly, so you do not program against an API provided by the JavaScript bridge, but against the browser API without an intermediate actor.

**Success**: Read on to see an [example project](/mini-app-example-project/) that puts this way of programming into practice.

Acknowledgements <a href="#acknowledgements" class="w-headline-link">#</a>
--------------------------------------------------------------------------

This article was reviewed by [Joe Medley](https://github.com/jpmedley), [Kayce Basques](https://github.com/kaycebasques), [Milica Mihajlija](https://github.com/mihajlija), [Alan Kent](https://github.com/alankent), and Keith Gu.

<a href="/tags/mini-apps/" class="w-chip">Mini apps</a>

<span class="w-mr--sm">Last updated: Mar 3, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/mini-apps/mini-app-programming-way/index.md)

<a href="/mini-apps" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
