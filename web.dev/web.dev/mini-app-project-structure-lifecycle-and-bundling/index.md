## <a href="#project-structure-lifecycle-and-bundling" class="w-toc__header--link">Project structure, lifecycle, and bundling</a>

- [Mini app project structure](#mini-app-project-structure)
- [Mini app lifecycle](#mini-app-lifecycle)
- [Page lifecycle](#page-lifecycle)
- [The build process](#the-build-process)
- [Acknowledgements](#acknowledgements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Project structure, lifecycle, and bundling

Mar 3, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/mini-apps" class="w-post-signpost__link">Mini apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

- <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
- <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
- <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

This post is part of an article collection where each article builds upon previous articles. If you just landed here, you may want to start reading from the [beginning](/mini-app-super-apps/).

## Mini app project structure <a href="#mini-app-project-structure" class="w-headline-link">#</a>

As before with the markup languages, the styling languages, and the components; with the mini app project structure, too, the details like the file extensions or the default names vary. The overall idea, though, is the same for all super app providers. The project structure always consists of:

- A root file `app.js` that initializes the mini app.
- A configuration file `app.json` that _roughly_ corresponds to a [web app manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest).
- An optional common style sheet file `app.css` with shared default styles.
- A `project.config.json` file that contains build information.

All the pages are stored in individual subfolders in a `pages` folder. Each page subfolder contains a CSS file, a JS file, an HTML file, and an optional configuration JSON file. All files must be named like their containing folder, apart from the file extensions. Like that, the mini app just needs a pointer to the directory in the `app.json` file (the manifest-like file), and can find all subresources dynamically. From the perspective of a web developer, mini apps are thus multi page apps.

    ├── app.js               # Initialization logic
    ├── app.json             # Common configuration
    ├── app.css              # Common style sheet
    ├── project.config.json  # Project configuration
    └── pages                # List of pages
       ├── index               # Home page
       │   ├── index.css         # Page style sheet
       │   ├── index.js          # Page logic
       │   ├── index.json        # Page configuration
       │   └── index.html        # Page markup
       └── other               # Other page
           ├── other.css         # Page style sheet
           ├── other.js          # Page logic
           ├── other.json        # Page configuration
           └── other.html        # Page markup

## Mini app lifecycle <a href="#mini-app-lifecycle" class="w-headline-link">#</a>

A mini app must be registered with the super app by calling the globally defined `App()` method. Referring to the project structure outlined [before](/project-structure-lifecycle-and-bundling/#mini-app-project-structure), this happens in `app.js`. The mini app lifecycle essentially consists of four events: `launch`, `show`, `hide`, and `error`. Handlers for these events can be passed to the `App()` method in the form of a configuration object, which can also contain a `globalData` property that holds data that should be globally available across all pages.

    /* app.js */
    App({
      onLaunch(options) {
        // Do something when the app is launched initially.
      },
      onShow(options) {
        // Do something when the app is shown.
      },
      onHide() {
        // Do something when the app is hidden.
      },
      onError(msg) {
        console.log(msg);
      },
      globalData: "I am global data",
    });

As usual, the individual details vary, but the concept is the same for [WeChat](https://developers.weixin.qq.com/miniprogram/en/dev/reference/api/App.html), [Alipay](https://opendocs.alipay.com/mini/framework/app-detail), [Baidu](https://smartprogram.baidu.com/docs/develop/framework/app_service_register/), [ByteDance](https://microapp.bytedance.com/docs/zh-CN/mini-app/develop/framework/logic-layer/start-app/), and also [Quick App](https://doc.quickapp.cn/tutorial/framework/lifecycle.html#app-%E7%9A%84%E7%94%9F%E5%91%BD%E5%91%A8%E6%9C%9F).

## Page lifecycle <a href="#page-lifecycle" class="w-headline-link">#</a>

Similar to the app lifecycle, the page lifecycle, too, has lifecycle events that the developer can listen for and react upon. These core events are `load`, `show`, `ready`, `hide`, and `unload`. Some platforms offer additional events like `pulldownrefresh`. Setting up the event handlers happens in the `Page()` method that is defined for each page. For the `index` or the `other` pages from the project structure [before](/project-structure-lifecycle-and-bundling/#mini-app-project-structure), this would happen in `index.js` or `other.js` respectively.

    /* index.js */
    Page({
      data: {
        text: "This is page data.",
      },
      onLoad: function (options) {
        // Do something when the page is initially loaded.
      },
      onShow: function () {
        // Do something when the page is shown.
      },
      onReady: function () {
        // Do something when the page is ready.
      },
      onHide: function () {
        // Do something when the page is hidden.
      },
      onUnload: function () {
        // Do something when the page is closed.
      },
      onPullDownRefresh: function () {
        // Do something when the user pulls down to refresh.
      },
      onReachBottom: function () {
        // Do something when the user scrolls to the bottom.
      },
      onShareAppMessage: function () {
        // Do something when the user shares the page.
      },
      onPageScroll: function () {
        // Do something when the user scrolls the page.
      },
      onResize: function () {
        // Do something when the user resizes the page.
      },
      onTabItemTap(item) {
        // Do something when the user taps the page's tab.
      },
      customData: {
        foo: "bar",
      },
    });

## The build process <a href="#the-build-process" class="w-headline-link">#</a>

The build process of mini apps is abstracted away from the developer. Under the hood, it is using industry tools like the [Babel](https://babeljs.io/) compiler for transpilation and minification and the [postcss](https://postcss.org/) CSS transformer. The build experience is comparable to that of [Next.js](https://nextjs.org/) or [`create-react-app`](https://reactjs.org/docs/create-a-new-react-app.html), where developers, if they explicitly choose not to, never touch the build parameters. The resulting processed files are finally signed, encrypted, and packaged in one or several (sub)packages that then get uploaded to the servers of the super app providers. Subpackages are meant for lazy-loading, so a mini app does not have to be downloaded all at once. The packaging details are meant to be private and are not documented, but some package formats like WeChat's `wxapkg` format have been [reverse-engineered](https://github.com/sjatsh/unwxapkg).

**Success**: The next chapter provides insights on the [mini app standardization effort](/mini-app-standardization/).

## Acknowledgements <a href="#acknowledgements" class="w-headline-link">#</a>

This article was reviewed by [Joe Medley](https://github.com/jpmedley), [Kayce Basques](https://github.com/kaycebasques), [Milica Mihajlija](https://github.com/mihajlija), [Alan Kent](https://github.com/alankent), and Keith Gu.

<a href="/tags/mini-apps/" class="w-chip">Mini apps</a>

<span class="w-mr--sm">Last updated: Mar 3, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/mini-apps/mini-app-project-structure-lifecycle-and-bundling/index.md)

<a href="/mini-apps" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

- ### Contribute

  - <a href="https://github.com/GoogleChrome/web.dev/issues/new?assignees=&amp;labels=bug&amp;template=bug_report.md&amp;title=" class="w-footer__linkbox-link">File a bug</a>
  - <a href="https://github.com/googlechrome/web.dev" class="w-footer__linkbox-link">View source</a>

- ### Related content

  - <a href="https://blog.chromium.org/" class="w-footer__linkbox-link">Chrome updates</a>
  - <a href="https://developers.google.com/web/" class="w-footer__linkbox-link">Web Fundamentals</a>
  - <a href="https://developers.google.com/web/showcase/" class="w-footer__linkbox-link">Case studies</a>
  - <a href="https://devwebfeed.appspot.com/" class="w-footer__linkbox-link">DevWeb Content Firehose</a>
  - <a href="/podcasts/" class="w-footer__linkbox-link">Podcasts</a>
  - <a href="/shows/" class="w-footer__linkbox-link">Shows</a>

- ### Connect

  - <a href="https://www.twitter.com/ChromiumDev" class="w-footer__linkbox-link">Twitter</a>
  - <a href="https://www.youtube.com/user/ChromeDevelopers" class="w-footer__linkbox-link">YouTube</a>

<a href="https://developers.google.com/" class="w-footer__utility-logo-link"><img src="/images/lockup-color.png" alt="Google Developers" class="w-footer__utility-logo" width="185" height="33" /></a>

- <a href="https://developer.chrome.com/" class="w-footer__utility-link">Chrome</a>
- <a href="https://firebase.google.com/" class="w-footer__utility-link">Firebase</a>
- <a href="https://cloud.google.com/" class="w-footer__utility-link">Google Cloud Platform</a>
- <a href="https://developers.google.com/products" class="w-footer__utility-link">All products</a>

<!-- -->

- <a href="https://policies.google.com/" class="w-footer__utility-link">Terms &amp; Privacy</a>
- <a href="/community-guidelines/" class="w-footer__utility-link">Community Guidelines</a>

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/terms/site-policies).
