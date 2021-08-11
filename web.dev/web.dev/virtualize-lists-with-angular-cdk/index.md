<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format" alt="Stacks of vinyl records." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/bGHUmFg8d3zHg6dJ29YT.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#virtualize-large-lists-with-the-angular-cdk" class="w-toc__header--link">Virtualize large lists with the Angular CDK</a>
----------------------------------------------------------------------------------------------------------------------------------

-   [Virtual scrolling in Angular with the Component Dev Kit](#virtual-scrolling-in-angular-with-the-component-dev-kit)
-   [Setting up virtual scrolling](#setting-up-virtual-scrolling)
-   [Add ScrollingModule to your app](#add-scrollingmodule-to-your-app)
-   [Create a viewport](#create-a-viewport)
-   [Going further](#going-further)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Virtualize large lists with the Angular CDK
===========================================

Make large lists more responsive by implementing virtual scrolling.

Jul 12, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/angular" class="w-post-signpost__link">Angular</a>

[<img src="https://web-dev.imgix.net/image/admin/s111dYyDIM2JRjTQbbu1.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Stephen Fluin" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/s111dYyDIM2JRjTQbbu1.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/s111dYyDIM2JRjTQbbu1.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/s111dYyDIM2JRjTQbbu1.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/s111dYyDIM2JRjTQbbu1.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/s111dYyDIM2JRjTQbbu1.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/sfluin/)

<a href="/authors/sfluin/" class="w-author__name-link">Stephen Fluin</a>

-   <a href="https://twitter.com/stephenfluin" class="w-author__link">Twitter</a>
-   <a href="https://github.com/stephenfluin" class="w-author__link">GitHub</a>

The scrolling list is one of the most common UI patterns today, whether it's browsing an infinitely scrolling feed on your favorite social media site, or navigating an enterprise dashboard. When scrolling lists become very long (hundreds, thousands, or hundreds of thousands of items), application performance can suffer.

Large lists can be slow to load because the application must load and render all the data up front. They can also be slow to render and navigate because each item in the list can have rich data , media, and functionality.

Users can experience problems when they load or scroll the page, leading to frustration and page abandonment.

Virtual scrolling in Angular with the Component Dev Kit <a href="#virtual-scrolling-in-angular-with-the-component-dev-kit" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------------------

Virtual scrolling is the primary technique used to address these scale problems. Virtual scrolling gives the impression of a very large list—by providing an appropriately sized scroll bar—and the ability to navigate the list without requiring the application to hold the entire list in memory or render it on the page.

In Angular, virtual scrolling is provided by the [Component Dev Kit (CDK)](https://material.angular.io/cdk/categories). By modifying the way you iterate through lists, and by supplying a couple of additional configuration parameters, the CDK's virtual scrolling will automatically manage the virtual rendering of your lists, improving page performance and responsiveness.

Instead of rendering the entire list at a time, only a subset of the items that fits on the screen (plus a small buffer) will be rendered. As the user navigates, a new subset of items is calculated and rendered, re-using the existing DOM if desired.

The rest of this post walks through how to set up basic virtual scrolling. You can see a full working example in this sample app:

Setting up virtual scrolling <a href="#setting-up-virtual-scrolling" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------

First make sure you've installed `@angular/cdk` using your favorite package manager. To install it using npm run this command in the terminal:

    npm install --save @angular/cdk

### Add `ScrollingModule` to your app <a href="#add-scrollingmodule-to-your-app" class="w-headline-link">#</a>

With the CDK installed, import `ScrollingModule`, which handles virtual scrolling, from the `@angular/cdk/scrolling` package. Then add it to the imports array of your module:

    import {ScrollingModule} from '@angular/cdk/scrolling';

    ...
    imports: [
      ScrollingModule
    ...
    ]
    ...

### Create a viewport <a href="#create-a-viewport" class="w-headline-link">#</a>

To see how the package works, try creating a component with a simple list of numbers from 0 to 99,999:

    @Component({
      template: `<div *ngFor="let item of list">{{item}}</div>`
    })
    export class ScrollComponent {
      list = Array.from({length: 100000}).map((_, i) => i);
    }

When the browser renders the app, it has to render 100,000 individual `<div>` elements. This might be fine for simple text nodes, but any complexity in the repeated template will not scale well, and any event listeners will be multiplied significantly.

To add virtual scrolling and avoid those problems, you need to create a viewport by wrapping the list in a `<cdk-virtual-scroll-viewport>` element:

    @Component({
      template: `<cdk-virtual-scroll-viewport>
        <div *ngFor="let item of list">{{item}}</div>
        </cdk-virtual-scroll-viewport>`
    })
    export class ScrollComponent {
      list = Array.from({length: 100000}).map((_, i) => i);
    }

Because `ScrollingModule` dynamically renders subsets of the list, you have to specify the height of the viewport via standard CSS. You also need to give the viewport a hint about its content by specifying the `itemSize`. The module uses this information to determine how many items to keep in the DOM at a given time and how to render an appropriately sized scrollbar.

    @Component({
      template: `<cdk-virtual-scroll-viewport itemSize="18" style="height:80vh">
        <div *ngFor="let item of list">{{item}}</div>
        </cdk-virtual-scroll-viewport>`
    })
    export class ScrollComponent {
      list = Array.from({length: 100000}).map((_, i) => i);
    }

Finally, convert `*ngFor` to `*cdkVirtualFor`:

    @Component({
      template: `<cdk-virtual-scroll-viewport itemSize="18" style="height:80vh">
        <div *cdkVirtualFor="let item of list">{{item}}</div>
        </cdk-virtual-scroll-viewport>`
    })
    export class ScrollComponent {
      list = Array.from({length: 100000}).map((_, i) => i);
    }

Instead of iterating through the entire list, the viewport will dynamically identify and iterate through the correct subset of the list for the user. Now when the user loads the page, the CDK should render the subset of the list that fits on the screen (plus a bit of buffer), and any scrolling events in the viewport will load and render the appropriate subset of the list:

The CDK rendering subsets of a list as the user scrolls.

Going further <a href="#going-further" class="w-headline-link">#</a>
--------------------------------------------------------------------

The CDK's virtual scroll abilities go much further than this basic example. In the [sample app](https://stackblitz.com/edit/scroll-list?file=src/app/app.component.ts), the entire list was in memory, but the list could be fetched on demand for more complex applications. You can learn more about the other capabilities of `ScrollingModule` and the `cdkVirtualOf` directive by reading about `Scrolling` in the [CDK documentation](https://material.angular.io/cdk/scrolling/overview).

*Hero image by Mr Cup / Fabien Barral on [Unsplash](https://unsplash.com/photos/o6GEPQXnqMY).*

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jul 12, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/angular/virtualize-lists-with-angular-cdk/index.md)

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
