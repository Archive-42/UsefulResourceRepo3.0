<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#reduce-javascript-payloads-with-code-splitting" class="w-toc__header--link">Reduce JavaScript payloads with code splitting</a>
----------------------------------------------------------------------------------------------------------------------------------------

-   [Measure](#measure)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Reduce JavaScript payloads with code splitting
==============================================

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

Nobody likes waiting. **[Over 50% of users abandon a website if it takes longer than 3 seconds to load](https://www.thinkwithgoogle.com/intl/en-154/insights-inspiration/research-data/need-mobile-speed-how-mobile-latency-impacts-publisher-revenue/)**.

Sending large JavaScript payloads impacts the speed of your site significantly. Instead of shipping all the JavaScript to your user as soon as the first page of your application is loaded, split your bundle into multiple pieces and only send what's necessary at the very beginning.

Measure <a href="#measure" class="w-headline-link">#</a>
--------------------------------------------------------

Lighthouse displays a failed audit when a significant amount of time is taken to execute all the JavaScript on a page.

<img src="https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format" alt="A failing Lighthouse audit showing scripts taking too long to execute." class="w-screenshot" sizes="(min-width: 797px) 797px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/p0Ahh3pzXog3jPdDp6La.png?auto=format&amp;w=1594 1594w" width="797" height="100" />

Split the JavaScript bundle to only send the code needed for the initial route when the user loads an application. This minimizes the amount of script that needs to be parsed and compiled, which results in faster page load times.

Popular module bundlers like [webpack](https://webpack.js.org/guides/code-splitting/), [Parcel](https://parceljs.org/code_splitting.html), and [Rollup](https://rollupjs.org/guide/en#dynamic-import) allow you to split your bundles using [dynamic imports](https://developers.google.com/web/updates/2017/11/dynamic-import). For example, consider the following code snippet that shows an example of a `someFunction` method that gets fired when a form is submitted.

    import moduleA from "library";

    form.addEventListener("submit", e => {
      e.preventDefault();
      someFunction();
    });

    const someFunction = () => {
      // uses moduleA
    }

In here, `someFunction` uses a module imported from a particular library. If this module is not being used elsewhere, the code block can be modified to use a dynamic import to fetch it only when the form is submitted by the user.

    form.addEventListener("submit", e => {
      e.preventDefault();
      import('library.moduleA')
        .then(module => module.default) // using the default export
        .then(someFunction())
        .catch(handleError());
    });

    const someFunction = () => {
        // uses moduleA
    }

The code that makes up the module does not get included into the initial bundle and is now **lazy loaded**, or provided to the user only when it is needed after the form submission. To further improve page performance, [preload critical chunks to prioritize and fetch them sooner](/preload-critical-assets).

Although the previous code snippet is a simple example, lazy loading third party dependencies is not a common pattern in larger applications. Usually, third party dependencies are split into a separate vendor bundle that can be cached since they don't update as often. You can read more about how the [**SplitChunksPlugin**](https://webpack.js.org/plugins/split-chunks-plugin/) can help you do this.

Splitting on the route or component level when using a client-side framework is a simpler approach to lazy loading different parts of your application. Many popular frameworks that use webpack provide abstractions to make lazy loading easier than diving into the configurations yourself.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/reduce-javascript-payloads-with-code-splitting/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-code-splitting/" class="w-callout__link w-callout__link--codelab">Reduce JavaScript payloads with code splitting</a>

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
