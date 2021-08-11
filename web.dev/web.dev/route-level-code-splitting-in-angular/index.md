





<img src="https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/WVwZbWEEXUfXzVTtAlha.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#route-level-code-splitting-in-angular" class="w-toc__header--link">Route-level code splitting in Angular</a>
----------------------------------------------------------------------------------------------------------------------

-   [Why code splitting matters](#why-code-splitting-matters)
-   [Code splitting techniques](#code-splitting-techniques)
-   [Sample application](#sample-application)
-   [Route-level code splitting](#route-level-code-splitting)
-   [Show a spinner](#show-a-spinner)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Route-level code splitting in Angular
=====================================

Improve the performance of your app by using route-level code splitting!

Jun 24, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/angular" class="w-post-signpost__link">Angular</a>

[<img src="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Minko Gechev" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mgechev/)

<a href="/authors/mgechev/" class="w-author__name-link">Minko Gechev</a>

-   <a href="https://twitter.com/mgechev" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mgechev" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@mgechev" class="w-author__link">Glitch</a>
-   <a href="https://blog.mgechev.com/" class="w-author__link">Blog</a>

This post explains how to set up route-level [code splitting](/reduce-javascript-payloads-with-code-splitting/) in an Angular application, which can reduce JavaScript bundle size and dramatically improve [Time to Interactive](/interactive).

*You can find the code samples from this article on [GitHub](https://github.com/mgechev/code-splitting-web-dev). The eager routing example is available in the [eager branch](https://github.com/mgechev/code-splitting-web-dev/tree/eager). The route-level code splitting example is in the [lazy branch](https://github.com/mgechev/code-splitting-web-dev/tree/lazy).*

This post assumes understanding of the Angular router. For a guide on how to use it, visit Angular's [official documentation](https://angular.io/guide/router).

Why code splitting matters <a href="#why-code-splitting-matters" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------

The ever growing complexity of web applications has led to a significant increase in the amount of JavaScript shipped to users. Large JavaScript files can noticeably delay interactivity, so it can be a costly resource, especially on mobile.

The most efficient way to shrink JavaScript bundles without sacrificing features in your applications is to introduce aggressive code splitting.

**[Code splitting](/reduce-javascript-payloads-with-code-splitting/)** lets you divide the JavaScript of your application into multiple chunks associated with different routes or features. This approach only sends users the JavaScript they need during the initial application load, keeping load times low.

By using code splitting, [Twitter and Tinder](https://medium.com/@addyosmani/the-cost-of-javascript-in-2018-7d8950fbb5d4) observed improvements of up to 50% for their [Time to Interactive](/interactive).

Code splitting techniques <a href="#code-splitting-techniques" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

Code splitting can be done at two levels: the **component level** and the **route level**.

-   In component-level code splitting, you move components to their own JavaScript chunks and load them lazily when they are needed.
-   In route-level code splitting, you encapsulate the functionality of each route into a separate chunk. When users navigate your application they fetch the chunks associated with the individual routes and get the associated functionality when they need it.

This post focuses on setting up route-level splitting in Angular.

### Sample application <a href="#sample-application" class="w-headline-link">#</a>

Before digging into how to use route level code splitting in Angular, let's look at a sample app:

Check out the implementation of the app's modules. Inside `AppModule` two routes are defined: the default route associated with `HomeComponent` and a `nyan` route associated with `NyanComponent`:

    @NgModule({
      ...
      imports: [
        BrowserModule,
        RouterModule.forRoot([
          {
            path: '',
            component: HomeComponent,
            pathMatch: 'full'
          },
          {
            path: 'nyan',
            component: NyanComponent
          }
        ])
      ],
      ...
    })
    export class AppModule {}

### Route-level code splitting <a href="#route-level-code-splitting" class="w-headline-link">#</a>

To set up code splitting, the `nyan` eager route needs to be refactored.

Version 8.1.0 of the Angular CLI can do everything for you with this command:

    ng g module nyan --module app --route nyan

This will generate:

-   A new routing module called `NyanModule`
-   A route in `AppModule` called `nyan` that will dynamically load the `NyanModule`
-   A default route in the `NyanModule`
-   A component called `NyanComponent` that will be rendered when the user hits the default route

Let's go through these steps manually so we get a better understanding of implementing code splitting with Angular!

When the user navigates to the `nyan` route, the router will render the `NyanComponent` in the router outlet.

To use route-level code splitting in Angular, set the `loadChildren` property of the route declaration and combine it with a dynamic import:

    {
      path: 'nyan',
      loadChildren: () => import('./nyan/nyan.module').then(m => m.NyanModule)
    }

There are a two key differences from the eager route:

1.  You set `loadChildren` instead of `component`. When using route-level code splitting you need to point to dynamically loaded modules, instead of components.
2.  In `loadChildren`, once the promise is resolved you return the `NyanModule` instead of pointing to the `NyanComponent`.

The snippet above specifies that when the user navigates to `nyan`, Angular should dynamically load `nyan.module` from the `nyan` directory and render the component associated with the default route declared in the module.

You can associate the default route with a component using this declaration:

    import { NgModule } from '@angular/core';
    import { NyanComponent } from './nyan.component';
    import { RouterModule } from '@angular/router';

    @NgModule({
      declarations: [NyanComponent],
      imports: [
        RouterModule.forChild([{
          path: '',
          pathMatch: 'full',
          component: NyanComponent
        }])
      ]
    })
    export class NyanModule {}

This code renders `NyanComponent` when the user navigates to `https://example.com/nyan`.

To check that the Angular router downloads the `nyan.module` lazily in your local environment:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.

2.  Click the **Network** tab.

3.  Click **NYAN** in the sample app.

4.  Note that the `nyan-nyan-module.js` file appears in the network tab.

<img src="https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format" alt="Lazy-loading of JavaScript bundles with route-level code splitting" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/wT4xLV2OkrZ2b7QaQz8L.png?auto=format&amp;w=1600 1600w" width="800" height="524" />

*Find this example [on GitHub](https://github.com/mgechev/code-splitting-web-dev/tree/lazy/src).*

### Show a spinner <a href="#show-a-spinner" class="w-headline-link">#</a>

Right now, when the user clicks the **NYAN** button, the application doesn't indicate that it's loading JavaScript in the background. To give the user feedback while loading the script you'll probably want to add a spinner.

To do that, start by adding markup for the indicator inside the `router-outlet` element in `app.component.html`:

    <router-outlet>
      <span class="loader" *ngIf="loading"></span>
    </router-outlet>

Then add an `AppComponent` class to handle routing events. This class will set the `loading` flag to `true` when it hears the `RouteConfigLoadStart` event and set the flag to `false` when it hears the `RouteConfigLoadEnd` event.

    @Component({
      selector: 'app-root',
      templateUrl: './app.component.html',
      styleUrls: ['./app.component.css']
    })
    export class AppComponent {
      loading: boolean;
      constructor(router: Router) {
        this.loading = false;
        router.events.subscribe(
          (event: RouterEvent): void => {
            if (event instanceof NavigationStart) {
              this.loading = true;
            } else if (event instanceof NavigationEnd) {
              this.loading = false;
            }
          }
        );
      }
    }

In the example below we've introduced an artificial 500 ms latency so that you can see the spinner in action.

**Warning**: Code splitting can significantly improve an app's initial load time, but it comes at the cost of slowing down subsequent navigation. In the [next post](/route-preloading-in-angular) on route preloading you'll see how to work around this problem!

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

You can shrink the bundle size of your Angular applications by applying route-level code splitting:

1.  Use the Angular CLI lazy-loaded module generator to automatically scaffold a dynamically loaded route.
2.  Add a loading indicator when the user navigates to a lazy route to show there's an ongoing action.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jun 24, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/angular/route-level-code-splitting-in-angular/index.md)

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
