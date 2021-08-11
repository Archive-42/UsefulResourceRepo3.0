<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format" alt="A hand dipping a paintbrush in one of several buckets of paint." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/DX8MXZivFjz3NqMtFcK4.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#get-started:-optimize-an-angular-application" class="w-toc__header--link">Get started: optimize an Angular application</a>
------------------------------------------------------------------------------------------------------------------------------------

-   [What's Angular?](#what's-angular)
-   [What's in this collection?](#what's-in-this-collection)
-   [What's not in this collection?](#what's-not-in-this-collection)
-   [Start a project](#start-a-project)
-   [Set up the CLI](#set-up-the-cli)
-   [Create the project](#create-the-project)
-   [What's next?](#what's-next)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Get started: optimize an Angular application
============================================

Want to make your Angular site as fast and accessible as possible? You've come to the right place!

Jun 24, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/angular" class="w-post-signpost__link">Angular</a>

[<img src="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Minko Gechev" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mgechev/)

<a href="/authors/mgechev/" class="w-author__name-link">Minko Gechev</a>

-   <a href="https://twitter.com/mgechev" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mgechev" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@mgechev" class="w-author__link">Glitch</a>
-   <a href="https://blog.mgechev.com/" class="w-author__link">Blog</a>

What's Angular? <a href="#what&#39;s-angular" class="w-headline-link">#</a>
---------------------------------------------------------------------------

Angular is a framework for building user interfaces. It provides building blocks to help you quickly set up a maintainable, scalable application. Angular empowers developers to create applications that live on the web, mobile, or the desktop.

What's in this collection? <a href="#what&#39;s-in-this-collection" class="w-headline-link">#</a>
-------------------------------------------------------------------------------------------------

This collection focuses on five major areas for optimizing an Angular application:

-   Improving the **performance** of your application to increase user conversion and engagement
-   Improving your application's **reliability** on poor networks by precaching assets with the Angular service worker
-   Making your application **discoverable** for search engines and social media bots using prerendering and server-side rendering
-   Making your application **installable** to provide a user experience similar to an iOS/Android app's
-   Improving the **accessibility of** your application to make it usable and understandable for all users

Each post in the collection will describe techniques that you can directly apply to your own applications.

What's *not* in this collection? <a href="#what&#39;s-not-in-this-collection" class="w-headline-link">#</a>
-----------------------------------------------------------------------------------------------------------

This collection assumes that you're already familiar with Angular and TypeScript. If you're not feeling confident with them yet, check out the TypeScript [documentation](https://www.typescriptlang.org/docs/home.html) and the [Getting Started with Angular](https://angular.io/start) guide on [angular.io](https://angular.io).

Start a project <a href="#start-a-project" class="w-headline-link">#</a>
------------------------------------------------------------------------

The [Angular command line interface (CLI)](https://cli.angular.io/) lets you quickly set up a simple client-side Angular application. This post has a short introduction to the CLI, while other posts in the collection show how to add more advanced features like server-side rendering and deployment support.

### Set up the CLI <a href="#set-up-the-cli" class="w-headline-link">#</a>

To begin, install the CLI globally and verify that you have the latest version by running these commands:

    npm i -g @angular/cli
    ng --version

Make sure the last command outputs version 8.0.3 or newer.

Alternatively, if you don't want to install the CLI globally, you can install it locally and run it with the `npx` command:

    npm i @angular/cli
    npx ng --version

### Create the project <a href="#create-the-project" class="w-headline-link">#</a>

To create a new project run:

    ng new my-app

This command will create the initial files and folder structure for your application and install the node modules it needs.

Once the setup process completes successfully, start your application by running:

    cd my-app
    ng serve

You should now be able to access your application at <http://localhost:4200>.

What's next? <a href="#what&#39;s-next" class="w-headline-link">#</a>
---------------------------------------------------------------------

In the rest of this collection you'll learn how to improve the performance, accessibility, and SEO of your Angular application. Here's what's covered:

-   Route-Level code splitting in Angular
-   Performance Budgets with the Angular CLI
-   Route Prefetching Strategies in Angular
-   Change detection optimization in Angular
-   Virtualize large lists with the Angular CDK
-   Precaching with the Angular Service Worker
-   Pre-render routes with Angular CLI
-   Server-side rendering with Angular Universal
-   Add a web app manifest with Angular CLI
-   Accessibility auditing with codelyzer

<span class="w-mr--sm">Last updated: Jun 24, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/angular/get-started-optimize-angular/index.md)

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
