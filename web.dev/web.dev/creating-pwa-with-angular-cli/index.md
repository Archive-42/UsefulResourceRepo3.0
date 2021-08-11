<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format" alt="Network cables." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/8lEoUW3i1nEU1q10N1YK.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#create-a-progressive-web-app-with-the-angular-cli" class="w-toc__header--link">Create a Progressive Web App with the Angular CLI</a>
----------------------------------------------------------------------------------------------------------------------------------------------

-   [Create an installable PWA](#create-an-installable-pwa)
-   [Customize your PWA](#customize-your-pwa)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Create a Progressive Web App with the Angular CLI
=================================================

You want to make your Angular app installable? Wait no more!

Aug 15, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/angular" class="w-post-signpost__link">Angular</a>

[<img src="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Minko Gechev" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mgechev/)

<a href="/authors/mgechev/" class="w-author__name-link">Minko Gechev</a>

-   <a href="https://twitter.com/mgechev" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mgechev" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@mgechev" class="w-author__link">Glitch</a>
-   <a href="https://blog.mgechev.com/" class="w-author__link">Blog</a>

In this post, you'll learn how to use the Angular command line interface (CLI) to make a [Progressive Web App (PWA)](/discover-installable).

*You can find the code sample from this guide [on GitHub](https://github.com/mgechev/manifest-web-dev).*

This post assumes you're already familiar with PWAs and their benefits. If you need a refresher, check out the [Installable](/installable) collection.

Create an installable PWA <a href="#create-an-installable-pwa" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

To make your Angular application a PWA, all you need to do is run a single command:

    ng add @angular/pwa

This command will:

-   Create a [service worker](/precaching-with-the-angular-service-worker) with a default caching configuration.
-   Create a [manifest file](/add-manifest), which tells the browser how your app should behave when installed on the user's device.
-   Add a link to the manifest file in `index.html`.
-   Add the [`theme-color`](/themed-omnibox) `<meta>` tag to `index.html`.
-   Create app icons in the `src/assets` directory.

By default, your service worker should be registered within a few seconds of the first page load. If it isn't, consider modifying the [`registrationStrategy`](https://angular.io/api/service-worker/SwRegistrationOptions).

Customize your PWA <a href="#customize-your-pwa" class="w-headline-link">#</a>
------------------------------------------------------------------------------

The [Precaching with the Angular service worker](/precaching-with-the-angular-service-worker) post explains how to configure the Angular service worker. There you can find how to specify which resources you want the service worker to cache and what strategy it should use to do so.

The manifest file of your app lets you specify your app's name, short name, icons, theme color, and other details. Read about the full set of properties you can set on the [Add a web app manifest](/add-manifest/) post.

Take a peek at the manifest file generated by the Angular CLI:

    {
      "name": "manifest-web-dev",
      "short_name": "manifest-web-dev",
      "theme_color": "#1976d2",
      "background_color": "#fafafa",
      "display": "standalone",
      "scope": "/",
      "start_url": "/",
      "icons": [
        {
          "src": "assets/icons/icon-72x72.png",
          "sizes": "72x72",
          "type": "image/png"
        },
        …
        {
          "src": "assets/icons/icon-512x512.png",
          "sizes": "512x512",
          "type": "image/png"
        }
      ]
    }

You can customize any of these properties by changing the relevant value in `manifest.webmanifest`.

A PWA references its manifest file with a `link` element in `index.html`. Once the browser finds the reference, it'll show the **Add to Home screen** prompt:

<figure><img src="https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format" sizes="(min-width: 344px) 344px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/IgMnFCuRU1Fx9JLZWXuT.png?auto=format&amp;w=688 688w" width="344" height="650" /></figure>Since the `ng-add` schematics add everything needed to make your app [installable](/discover-installable/), they generate some shortcut icons that are shown once the user adds the app to their desktop:

<figure><img src="https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format" sizes="(min-width: 344px) 344px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/3h7Yuj3MJPiNzbh2xdlB.png?auto=format&amp;w=688 688w" width="344" height="650" /></figure>Make sure you customize the manifest properties and icons before you deploy your PWA to production!

If you want to change your PWA back to a standard web app, just remove the reference to `manifest.webmanifest` from `index.html`.

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

To make an installable Angular app:

1.  Add `@angular/pwa` to your project using the Angular CLI.
2.  Edit the options in the `manifest.webmanifest` file to suit your project.
3.  Update the icons in the `src/assets/icons` directory to suit your project.
4.  Optionally, edit the `theme-color` in `index.html`.

<span class="w-mr--sm">Last updated: Aug 15, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/angular/creating-pwa-with-angular-cli/index.md)

<a href="/angular" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
