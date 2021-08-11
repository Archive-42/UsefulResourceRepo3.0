<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#concluding-thoughts-about-mini-apps-from-a-web-developer" class="w-toc__header--link">Concluding thoughts about mini apps from a web developer</a>
------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [Where does this leave us?](#where-does-this-leave-us)
-   [Closing thoughts](#closing-thoughts)
-   [Acknowledgements](#acknowledgements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Concluding thoughts about mini apps from a web developer
========================================================

Mar 3, 2021 <span class="w-author__separator">•</span> Updated Jun 12, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/mini-apps" class="w-post-signpost__link">Mini apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

-   <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
-   <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
-   <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

This post is part of an article collection where each article builds upon previous articles. If you just landed here, you may want to start reading from the [beginning](/mini-app-super-apps/).

Where does this leave us? <a href="#where-does-this-leave-us" class="w-headline-link">#</a>
-------------------------------------------------------------------------------------------

Writing and researching mini apps has been quite a ride, but one that I do not regret. On the one hand, the success and the popularity of mini apps have proven their creators right about their approach. On the other hand, though, this success is geographically concentrated in regions where the few popular super apps are dominant, at least at the time of writing. What is undoubtedly true is that the ecosystem is highly fascinating and well worth a look. This collection of articles has provided deep-dives into many of the aspects that make a difference when using and creating mini apps. From the [DevTools](/mini-app-devtools/) experience to the [mark-up](/mini-app-markup-styling-and-scripting/#markup-languages), [styling](/mini-app-markup-styling-and-scripting/#styling), and [scripting](/mini-app-markup-styling-and-scripting/#scripting) approaches, over to the [component model](/mini-app-components/), and finally to the overall [architecture](/mini-app-project-structure-lifecycle-and-bundling/); mini apps provide learning and inspiration opportunities for app developers, and even so for those who purely aim for the web.

My initial experiments with [building a web application the mini app way](/mini-app-example-project/) were successful. Future work will show to what extent this model is performant and flexible enough to cater for the many shapes that web apps can take. My current *ad-hoc* approach can be formalized by packaging up the relevant pieces of code in a dedicated library, `mini-app.js` if you will. What is interesting is that this kind of programming goes back all the way to `frameset`. Just that today it is about applications and not documents.

I see great potential for improvement with the entire web development experience by taking inspiration from the various mini apps DevTools. From the easy [(remote) on-device testing feature](/mini-app-devtools/#simulator-and-real-device-testing-and-debugging) to the packaging and [building](/mini-app-project-structure-lifecycle-and-bundling/#the-build-process) experience; the integration of the [IDE](/mini-app-devtools/#mini-app-ides) with the DevTools environment offers a lot of starting points for making developers' lives easier.

Closing thoughts <a href="#closing-thoughts" class="w-headline-link">#</a>
--------------------------------------------------------------------------

From a features point of view, the web is becoming more and more powerful with each release of essentially *any* browser. The ever-growing [list of capabilities](/fugu-status/) makes use cases possible on the web that were unthinkable a mere year ago. At the same time, the need for [mini apps standardization](/mini-app-standardization/) shows that developers are not willing or able to build the same mini app for each super app. On the horizon maybe there is a desire for an abstraction layer on the browser level that allows for mini apps to run on the web, while noting that the web is not immune from fragmentation, especially when looking at different browser vendors and what they choose to implement and what not. Concluding, I am looking forward to seeing where all this is headed. Thinking outside of the box and taking input and inspiration from outside of one's own bubble can definitely help when building a better future on the web.

**Success**: Congratulations, you have reached the end of the [mini apps collection](/mini-apps/).

Acknowledgements <a href="#acknowledgements" class="w-headline-link">#</a>
--------------------------------------------------------------------------

This article was reviewed by [Joe Medley](https://github.com/jpmedley), [Kayce Basques](https://github.com/kaycebasques), [Milica Mihajlija](https://github.com/mihajlija), [Alan Kent](https://github.com/alankent), and Keith Gu.

<a href="/tags/mini-apps/" class="w-chip">Mini apps</a>

<span class="w-mr--sm">Last updated: Jun 12, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/mini-apps/mini-app-conclusion/index.md)

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
