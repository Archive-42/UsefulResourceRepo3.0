<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#performance-as-a-default-with-next.js" class="w-toc__header--link">Performance as a default with Next.js</a>
----------------------------------------------------------------------------------------------------------------------

-   [What will you learn?](#what-will-you-learn)
-   [How is Next.js different from React?](#how-is-next.js-different-from-react)
-   [Setting up](#setting-up)
-   [What's next?](#what's-next)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Performance as a default with Next.js
=====================================

Next.js takes care of many optimizations in your React app so you don’t have to

Nov 8, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

[Next.js](https://nextjs.org/) is an opinionated [React](https://reactjs.org/) framework with a number of performance optimizations baked in. The main idea behind the framework is to ensure applications start and remain as performant as possible by having these capabilities included by default.

This introduction will briefly cover many features provided by the framework at a high level. The other guides in this collection will explore the features in more detail.

Chrome is collaborating with Next.js to improve the framework for any developer looking to build a fast, server-rendered React application. A number of newer optimizations were recently added such as [module/nomodule support](https://github.com/zeit/next.js/issues/7563) and an [improved granular chunking strategy](https://github.com/zeit/next.js/issues/7631).

What will you learn? <a href="#what-will-you-learn" class="w-headline-link">#</a>
---------------------------------------------------------------------------------

Although Next.js provides a number of performance optimizations by default, these guides aim to explain them in more detail and show you how you can use them to build a fast and performant experience.

This collection assumes that you have a basic knowledge of React. If not, check out [React's Getting Started page](https://reactjs.org/docs/getting-started.html).

There are many optimizations that can be added to React sites in general that would also work for applications built with Next.js. These will not be covered since the focus is on what Next.js specifically provides. To learn more about general React optimizations, check out our [React collection](/react).

How is Next.js different from React? <a href="#how-is-next.js-different-from-react" class="w-headline-link">#</a>
-----------------------------------------------------------------------------------------------------------------

React is a library that makes it easier to build user interfaces using a component-based approach. Although powerful, React is specifically a UI library. Many developers include additional tooling such as a module bundler ([webpack](https://webpack.js.org/) for example) and a transpiler ([Babel](https://babeljs.io/) for example) to have a complete build toolchain.

In the [React collection](/react), we took the approach of using [Create React App](https://create-react-app.dev/) (CRA) to spin up React apps quickly. CRA takes the hassle out of setting up a React application by providing a complete build toolchain with a single command.

Although there are a few default optimizations baked into CRA, the tool aims to provide a simple and straightforward setup. The choice is given to developers to decide whether to [eject](https://create-react-app.dev/docs/available-scripts#npm-run-eject) and modify the configurations themselves.

Next.js, which can also be used to create a new React application, takes a different approach. It immediately provides a number of common optimizations that many developers would like to have but find difficult to set up, such as:

-   Server-side rendering
-   Automatic code-splitting
-   Route prefetching
-   File-system routing
-   CSS-in-JS styling ([`styled-jsx`](https://github.com/zeit/styled-jsx))

Setting up <a href="#setting-up" class="w-headline-link">#</a>
--------------------------------------------------------------

To create a new Next.js application, run the following command:

    npx create-next-app new-app

[npx](https://medium.com/@maybekatz/introducing-npx-an-npm-package-runner-55f7d4bd282b) is a package runner that is installed automatically with npm 5.2.0 or later. It simplifies quite a few processes involved with managing packages including running CLI commands (like `create-next-app`) without having to install them globally on your machine.

Then navigate to the directory and start the development server:

    cd new-app
    npm run dev

You can also add Next.js to an existing React application. Check out [Manual Setup](https://nextjs.org/docs#manual-setup) to learn how.

The following embed shows the directory structure of a new Next.js app.

-   Click **Remix to Edit** to make the project editable.
-   To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

Notice that a `pages/` directory is created with a single file: `index.jsx`. Next.js follows a file-system routing approach, where every page within this directory is served as a separate route. Creating a new file in this directory, such as `about.js`, will automatically create a new route (`/about`).

Components can also be created and used like any other React application. A `components/` directory has already been created with a single component, `nav.js`, which is already imported in `index.js`. By default, every import used in Next.js is only fetched when that page is loaded, providing the benefits of **automated code-splitting**.

Moreover, every initial page load in Next.js is **server-side rendered**. If you open the Network panel in DevTools, you can see the initial request for the document returns a fully server-rendered page.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format" alt="The Preview tab of the Network panel shows that Next.js returns visually complete HTML when a page is requested." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bq2tjbZwvpwqQhFsHp0Q.png?auto=format&amp;w=1600 1600w" width="800" height="529" /><figcaption>The Preview tab of the Network panel shows that Next.js returns visually complete HTML when a page is requested.</figcaption></figure>Check out [Server Rendering](https://developers.google.com/web/updates/2019/02/rendering-on-the-web#server-rendering) to learn how server-side rendering often results in a better experience for users.

These are only a few of the many features provided by Next.js automatically. Many are customizable and can be modified for different use cases.

What's next? <a href="#what&#39;s-next" class="w-headline-link">#</a>
---------------------------------------------------------------------

Pun intended 😛

Every other guide in this collection will explore a specific Next.js feature in detail:

-   [Route prefetching](/route-prefetching-in-nextjs/) to speed up page navigations
-   [Serving hybrid and AMP-only pages](/how-amp-can-guarantee-fastness-in-your-nextjs-app) for faster loading from search engines
-   [Code-splitting components with dynamic imports](/code-splitting-with-dynamic-imports-in-nextjs/) to reduce JavaScript footprints

<span class="w-mr--sm">Last updated: Nov 8, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/performance-as-a-default-with-nextjs/index.md)

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
