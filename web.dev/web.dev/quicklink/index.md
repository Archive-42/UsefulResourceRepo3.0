<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/S4BkwUJKPdL9ijtgtEJA.png?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#speed-up-navigations-in-react-with-quicklink" class="w-toc__header--link">Speed up navigations in React with Quicklink</a>
------------------------------------------------------------------------------------------------------------------------------------

-   [Determine chunks associated with each route](#determine-chunks-associated-with-each-route)
-   [Prefetch chunks for in-viewport routes](#prefetch-chunks-for-in-viewport-routes)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Speed up navigations in React with Quicklink
============================================

Automatically prefetch in-viewport links with quicklink for React single page applications.

Jun 8, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Addy Osmani" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/addyosmani/)

<a href="/authors/addyosmani/" class="w-author__name-link">Addy Osmani</a>

-   <a href="https://twitter.com/addyosmani" class="w-author__link">Twitter</a>
-   <a href="https://github.com/addyosmani" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

-   <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
-   <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

[<img src="https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Anton Karlovskiy" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/antonkarlovskiy/)

<a href="/authors/antonkarlovskiy/" class="w-author__name-link">Anton Karlovskiy</a>

-   <a href="https://twitter.com/antonkarlovskiy" class="w-author__link">Twitter</a>
-   <a href="https://github.com/anton-karlovskiy" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@anton-karlovskiy" class="w-author__link">Glitch</a>

[Prefetching](/link-prefetch/) is a technique to speed up navigations by downloading the resources for the next page, ahead of time. [Quicklink](https://github.com/GoogleChromeLabs/quicklink) is a library that allows you to implement this technique at scale, by automatically prefetching links as they come into the view.

In multi-page apps the library prefetches documents (e.g. `/article.html`), for in-viewport links, so that when the user clicks on these links they can be picked up from the [HTTP cache](/http-cache/).

[Single-page apps](https://en.wikipedia.org/wiki/Single-page_application) commonly use a technique called [route-based code splitting](/reduce-javascript-payloads-with-code-splitting/). This allows the site to load the code for a given route only when the user navigates to it. These files (JS, CSS) are commonly referred to as "chunks".

With that said, in these sites, instead of prefetching documents the biggest performance gains come from prefetching these chunks before the page needs them.

Achieving this presents some challenges:

-   It's not trivial to determine which chunks (e.g. `article.chunk.js`) are associated with a given route (e.g. `/article`) before landing on it.
-   The final URL names of these chunks can't be predicted, as modern module bundlers typically use long-term hashing for versioning (e.g. `article.chunk.46e51.js`).

This guide explains how Quicklink solves these challenges and allows you to achieve prefetching at scale in React single page apps.

At the moment this solution is only compatible with [react-router](https://www.npmjs.com/package/react-router).

**Try it**! Check out the [Prefetching in create-react-app with Quicklink](/codelab-quicklink/) codelab for a guided, hands-on demonstration of Quicklink.

Determine chunks associated with each route <a href="#determine-chunks-associated-with-each-route" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------

One of the core components of `quicklink` is [webpack-route-manifest](https://github.com/lukeed/webpack-route-manifest), a [webpack](https://webpack.js.org/) plugin that lets you generate a JSON dictionary of routes and chunks. This allows the library to know which files are going to be needed by each route of the application and prefetch them as the routes come into the view.

After [integrating the plugin](https://github.com/lukeed/webpack-route-manifest#install) with the project, it will produce a JSON manifest file associating each route with its corresponding chunks:

    {
      '/about': [
        {
          type: 'style',
          href: '/static/css/about.f6fd7d80.chunk.css',
        },
        {
          type: 'script',
          href: '/static/js/about.1cdfef3b.chunk.js',
        },
      ],
      '/blog': [
        {
          type: 'style',
          href: '/static/css/blog.85e80e75.chunk.css',
        },
        {
          type: 'script',
          href: '/static/js/blog.35421503.chunk.js',
        },
      ],
    }

This manifest file can be requested in two ways:

-   By URL, e.g. `https://site_url/rmanifest.json`.
-   Through the window object, at `window.__rmanifest`.

Prefetch chunks for in-viewport routes <a href="#prefetch-chunks-for-in-viewport-routes" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------

Once the manifest file is available, the next step is to install Quicklink by running `npm install quicklink`.

Then, the [higher order component (HOC)](https://reactjs.org/docs/higher-order-components.html) `withQuicklink()` can be used to indicate that a given route should be prefetched when the link comes into the view.

The following code belongs to an `App` component of a React app that renders a top menu with four links:

    const App = () => (
      <div className={style.app}>
        <Hero />
        <main className={style.wrapper}>
          <Suspense fallback={<div>Loading…</div>}>
            <Route path="/" exact component={Home} />
            <Route path="/blog" exact component={Blog} />
            <Route path="/blog/:title" component={Article} />
            <Route path="/about" exact component={About} />
          </Suspense>
        </main>
        <Footer />
      </div>
    );

To tell Quicklink that these routes should be prefetched as they come into the view:

1.  Import the `quicklink` HOC at the beginning of the component.
2.  Wrap each route with the `withQuicklink()` HOC, passing the page component and options parameter to it.

<!-- -->

    const options = {
      origins: [],
    };
    const App = () => (
      <div className={style.app}>
        <Hero />
        <main className={style.wrapper}>
          <Suspense fallback={<div>Loading…</div>}>
            <Route path="/" exact component={withQuicklink(Home, options)} />
            <Route path="/blog" exact component={withQuicklink(Blog, options)} />
            <Route
              path="/blog/:title"
              component={withQuicklink(Article, options)}
            />
            <Route path="/about" exact component={withQuicklink(About, options)} />
          </Suspense>
        </main>
        <Footer />
      </div>
    );

The `withQuicklink()` HOC uses the path of the route as a key to obtain its associated chunks from `rmanifest.json`. Under the hood, as links come into the view, the library injects a `<link rel="prefetch">` tag in the page for each chunk so they can be prefetched. Prefetched resources will be requested at the lowest priority by the browser and kept in the [HTTP Cache](/http-cache/) for 5 minutes, after which point, the `cache-control` rules of the resource apply. As a result of this, when a user clicks on a link and moves to a given route, the chunks will be retrieved from the cache, greatly improving the time it takes to render that route.

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

Prefetching can greatly improve load times for future navigations. In React single-page apps, this can be achieved by loading the chunks associated with each route, before the user lands in them. Quicklink's solution for React SPA uses `webpack-route-manifest` to create a map of routes and chunks, in order to determine which files to prefetch, when a link comes into the view. Implementing this technique throughout your site can greatly improve navigations to the point of making them appear instant.

<span class="w-mr--sm">Last updated: Jun 8, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/quicklink/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-quicklink/" class="w-callout__link w-callout__link--codelab">Prefetching in create-react-app with Quicklink</a>

<a href="/react" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
