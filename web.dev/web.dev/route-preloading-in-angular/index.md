





<img src="https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format" alt="Glass crystal ball" class="w-hero w-hero--bottom w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/q4b86k6REnNHkpjQnsLK.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#route-preloading-strategies-in-angular" class="w-toc__header--link">Route preloading strategies in Angular</a>
------------------------------------------------------------------------------------------------------------------------

-   [Route preloading strategies in Angular](#route-preloading-strategies-in-angular)
-   [Using the PreloadAllModules strategy](#using-the-preloadallmodules-strategy)
-   [Using the Quicklink preloading strategy](#using-the-quicklink-preloading-strategy)
-   [Using the Quicklink preloading strategy across multiple lazy-loaded modules](#using-the-quicklink-preloading-strategy-across-multiple-lazy-loaded-modules)
-   [Going beyond basic preloading](#going-beyond-basic-preloading)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Route preloading strategies in Angular
======================================

Preload routes ahead of time to speed up users' navigation.

Jul 9, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/angular" class="w-post-signpost__link">Angular</a>

[<img src="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Minko Gechev" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mgechev/)

<a href="/authors/mgechev/" class="w-author__name-link">Minko Gechev</a>

-   <a href="https://twitter.com/mgechev" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mgechev" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@mgechev" class="w-author__link">Glitch</a>
-   <a href="https://blog.mgechev.com/" class="w-author__link">Blog</a>

[Route-level code splitting](/route-level-code-splitting-in-angular) can help you reduce the initial load time of an application by delaying the JavaScript associated with routes that aren't initially needed. This way, the Angular router waits until a user navigates to a given route before triggering a network request to download the associated JavaScript.

While this technique is great for initial page load, it can slow down navigation, depending on the users' network latency and bandwidth. One way to tackle this problem is **route preloading**. Using preloading, when the user is at a given route, you can download and cache JavaScript associated with routes that are likely to be needed next. The Angular router provides this functionality out of the box.

In this post, you'll learn how to speed up navigation when using route-level code splitting by taking advantage of JavaScript preloading in Angular.

Route preloading strategies in Angular <a href="#route-preloading-strategies-in-angular" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------

The Angular router provides a configuration property called `preloadingStrategy`, which defines the logic for preloading and processing lazy-loaded Angular modules. We'll cover two possible strategies:

-   `PreloadAllModules`, which preloads all lazy-loaded routes, as the name implies
-   `QuicklinkStrategy`, which preloads only the routes associated with links on the current page.

*The rest of this post refers to a sample Angular app. You can find the source code [on GitHub](https://github.com/mgechev/route-preloading-web-dev).*

### Using the `PreloadAllModules` strategy <a href="#using-the-preloadallmodules-strategy" class="w-headline-link">#</a>

The sample app has several lazy-loaded routes. To preload all of them using the `PreloadAllModules` strategy—which is built into Angular—specify it as the value for the `preloadingStrategy` property in the router configuration:

    import { RouterModule, PreloadAllModules } from '@angular/router';
    // …

    RouterModule.forRoot([
      …
    ], {
      preloadingStrategy: PreloadAllModules
    })
    // …

Now serve the application and look at the **Network** panel in Chrome DevTools:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Network** tab.

You should see that the router downloaded `nyan-nyan-module.js` and `about-about-module.js` in the background when you opened the application:

The PreloadAllModules strategy in action.

The router also registered the modules' route declarations so that when you navigate to a URL associated with any of the preloaded modules, the transition is instantaneous.

### Using the Quicklink preloading strategy <a href="#using-the-quicklink-preloading-strategy" class="w-headline-link">#</a>

`PreloadAllModules` is useful in a lot of cases. When you have dozens of modules, however, its aggressive preloading can really increase network usage. Also, since the router needs to register the routes in all the preloaded modules, it can cause intensive computations in the UI thread and lead to sluggish user experience.

The [quicklink](https://github.com/GoogleChromeLabs/quicklink) library provides a better strategy for larger apps. It uses the [IntersectionObserver](https://developers.google.com/web/updates/2019/02/intersectionobserver-v2) API to preload only modules associated with links that are currently visible on the page.

You can add quicklink to an Angular app by using the [ngx-quicklink](https://www.npmjs.com/package/ngx-quicklink) package. Start by installing the package from npm:

    npm install --save ngx-quicklink

Once it's available in your project, you can use `QuicklinkStrategy` by specifying the router's `preloadingStrategy` and importing the `QuicklinkModule`:

    import {QuicklinkStrategy, QuicklinkModule} from 'ngx-quicklink';
    …

    @NgModule({
      …
      imports: [
        …
        QuicklinkModule,
        RouterModule.forRoot([…], {
          preloadingStrategy: QuicklinkStrategy
        })
      ],
      …
    })
    export class AppModule {}

Now when you open the application again, you'll notice that the router only preloads `nyan-nyan-module.js` since the button in the center of the page has a router link to it. And when you open the side navigation, you'll notice that the router then preloads the "About" route:

A demo of the quicklink preloading strategy.

### Using the Quicklink preloading strategy across multiple lazy-loaded modules <a href="#using-the-quicklink-preloading-strategy-across-multiple-lazy-loaded-modules" class="w-headline-link">#</a>

The above example will work for a basic application but if your application contains multiple lazy-loaded modules you will need to import the `QuicklinkModule` into a shared module, export it and then import the shared module into your lazy-loaded modules.

First import the `QuicklinkModule` from `ngx-quicklink` into your shared module and export it:

    import { QuicklinkModule } from 'ngx-quicklink';
    …

    @NgModule({
      …
      imports: [
        QuicklinkModule
      ],
      exports: [
        QuicklinkModule
      ],
      …
    })
    export class SharedModule {}

Then import your `SharedModule` into all of your lazy-loaded modules:

    import { SharedModule } from '@app/shared/shared.module';
    …

    @NgModule({
      …
      imports: [
          SharedModule
      ],
      …
    });

`Quicklinks` will now be available in your lazy-loaded modules.

Going beyond basic preloading <a href="#going-beyond-basic-preloading" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------

While selective preloading via quicklink can significantly speed up navigation, you can make your preloading strategy even more network efficient by using predictive preloading—which is implemented by [Guess.js](https://github.com/guess-js/guess). By analyzing a report from Google Analytics or another analytics provider, Guess.js can predict a user's navigation journey and preload only the JavaScript chunks that are likely to be needed next.

You can learn how to use Guess.js with Angular on [this page from the Guess.js site](https://guess-js.github.io/docs/angular).

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

To speed up navigation when using route-level code splitting:

1.  Pick the right preloading strategy depending on the size of your application:
    -   Applications with few modules can use Angular's built-in `PreloadAllModules` strategy.
    -   Applications with many modules should use a custom preloading strategy, like Angular's quicklink, or predictive preloading, as implemented in Guess.js.
2.  Configure the preloading strategy by setting the `preloadStrategy` property of the Angular router.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jul 9, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/angular/route-preloading-in-angular/index.md)

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
