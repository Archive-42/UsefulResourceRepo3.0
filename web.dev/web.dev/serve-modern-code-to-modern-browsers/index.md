

<a href="/" class="header-default__logo-link gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="header-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="header-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="header-default__link gc-analytics-event">Blog</a> <a href="/about/" class="header-default__link gc-analytics-event">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="drawer-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="drawer-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="drawer-default__link gc-analytics-event">Blog</a> <a href="/about/" class="drawer-default__link gc-analytics-event">About</a>

<a href="#serve-modern-code-to-modern-browsers-for-faster-page-loads" class="w-toc__header--link">Serve modern code to modern browsers for faster page loads</a>
----------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [Identify which browsers you want to target](#identify-which-browsers-you-want-to-target)
-   [Use @babel/preset-env](#use-@babelpreset-env)
-   [Enable modern bugfixes](#enable-modern-bugfixes)
-   [Use &lt;script type="module"&gt;](#use-lessscript-type)

Share <a href="/newsletter/" class="w-actions__fab w-actions__fab--subscribe gc-analytics-event"><span>subscribe</span></a>

Serve modern code to modern browsers for faster page loads
==========================================================

Nov 5, 2018 <span class="w-author__separator">•</span> Updated Jun 23, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75 1x,     https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x,     https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x,     https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x,     https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

Building websites that work well on all major browsers is a core tenet of an open web ecosystem. However, this means additional work of ensuring that all of the code you write is supported in each browser that you plan to target. If you want to use new JavaScript language features, you need to transpile these features to backwards-compatible formats for browsers that do not yet support them.

[Babel](https://babeljs.io/docs/en) is the most widely used tool to compile code that contains newer syntax into code that different browsers and environments (such as Node) can understand. This guide assumes you are using Babel, so you need to follow the [setup instructions](https://babeljs.io/setup) to include it into your application if you haven't already. Select `webpack` in `Build Systems` if you are using webpack as the module bundler in your app.

Fun fact: Lebab is a separate library that does the opposite of what Babel does. It converts older code into newer syntax.

To use Babel to only transpile what is needed for your users, you need to:

1.  Identify which browsers you want to target.
2.  Use `@babel/preset-env` with appropriate browser targets.
3.  Use `<script type="module">` to stop sending transpiled code to browsers that don't need it.

Identify which browsers you want to target <a href="#identify-which-browsers-you-want-to-target" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------

Before you begin to modify how the code in your application is transpiled, you need to identify which browsers access your application. Analyze which browsers your users are currently using as well as those that you plan to target to make an informed decision.

Use @babel/preset-env <a href="#use-@babelpreset-env" class="w-headline-link">#</a>
-----------------------------------------------------------------------------------

Transpiling code usually results in a file that is larger than the original larger file sizes than their original forms. By minimizing the amount of compilation that you do you can reduce the size of your bundles to improve the performance of a web page.

Instead of including specific plugins to selectively compile certain language features you are using, Babel provides a number of presets that bundles plugins together. Use [@babel/preset-env](https://babeljs.io/docs/en/babel-preset-env) to only include the transforms and polyfills needed for the browsers you plan on targeting.

Include `@babel/preset-env` within the `presets` array in your Babel configurations file, `.babelrc`:

    {
     "presets": [
       [
         "@babel/preset-env",
         {
           "targets": ">0.25%"
         }
       ]
     ]
    }

Use the `targets` field to specify which browser versions you want to include by adding an appropriate query to the `browsers` field. `@babel/preset-env` integrates with browserslist, an open-source configuration shared between different tools for targeting browsers. A full list of compatible queries is in the [browserslist documentation](https://github.com/browserslist/browserslist#full-list). Another option is to use a [`.browserslistrc`](https://babeljs.io/docs/en/babel-preset-env#browserslist-integration) file to list the environments you wish to target.

The `">0.25%"` value tells Babel to only include the transforms needed to support browsers that make up more than 0.25% of global usage. This ensures your bundle does not contain unnecessary transpiled code for browsers that are used by a very small percentage of users.

In most cases, this is a better approach than using the following configuration:

      "targets": "last 2 versions"

The `"last 2 versions"` value transpiles your code for the [last two versions](http://browserl.ist/?q=last+2+versions) of every browser, which means support is provided for discontinued browsers such as Internet Explorer. This can unnecessarily increase the size of your bundle if you do not expect these browsers to be used to access your application.

Ultimately, you should select the appropriate combination of queries to only target browsers that fit your needs.

### Enable modern bugfixes <a href="#enable-modern-bugfixes" class="w-headline-link">#</a>

`@babel/preset-env` groups multiple JavaScript syntax features into collections and enables/disables them based on the target browsers specified. Although this works well, an entire collection of syntax features is transformed when a targeted browser contains a bug with just a single feature. This often results in more transformed code than is necessary.

Originally developed as a [separate preset](https://github.com/babel/preset-modules), the [bugfixes option](https://babeljs.io/docs/en/babel-preset-env#bugfixes) in `@babel/preset-env` solves this problem by converting modern syntax that is broken in some browsers to the closest equivalent syntax that is not broken in those browsers. The result is nearly identical modern code with a few small syntax tweaks that guarantee compatibility in all target browsers. To use this optimization, make sure you have `@babel/preset-env` 7.10 or later installed, then set the [`bugfixes`](https://babeljs.io/docs/en/babel-preset-env#bugfixes) property to `true`:

    {
     "presets": [
       [
         "@babel/preset-env",
         {
           "bugfixes": true
         }
       ]
     ]
    }

In Babel 8, the `bugfixes` option will be enabled by default.

Use `<script type="module">` <a href="#use-lessscript-type%22module%22greater" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

JavaScript modules, or ES modules, are a relatively new feature supported in [all major browsers](https://caniuse.com/#feat=es6-module). You can use modules to create scripts that can import and export from other modules, but you can also use them with `@babel/preset-env` to only target browsers that support them.

Instead of querying for specific browser versions or market share, consider specifying `"esmodules" : true` inside your `.babelrc` file's `targets` field.

    {
       "presets":[
          [
             "@babel/preset-env",
             {
                "targets":{
                   "esmodules": true
                }
             }
          ]
       ]
    }

Many newer ECMAScript features compiled with Babel are already supported in environments that support JavaScript modules. So by doing this, you simplify the process of making sure that only transpiled code is used for browsers that actually need it.

Browsers that support modules ignore scripts with a `nomodule` attribute. Conversely, browsers that do not support modules ignore script elements with `type="module"`. This means you can include a module as well as a compiled fallback.

Ideally, the two version scripts of an application are included like this:

      <script type="module" src="main.mjs"></script>
      <script nomodule src="compiled.js" defer></script>

Browsers that support modules fetch and execute `main.mjs` and ignore `compiled.js`. The browsers that do not support modules do the opposite.

Module scripts are deferred by default. The `defer` attribute is added to the `nomodule` script for the same behavior.

If you use webpack, you can set different targets in your configurations for two separate versions of your application:

-   A version only for browsers that support modules.
-   A version that includes a compiled script which works in any legacy browser. This has a larger file size, since transpilation needs to support a wider range of browsers.

Although this HTML approach can provide performance benefits, certain browsers have been found to double-fetch when specifying both module and nomodule scripts. Jason Miller's [Modern Script Loading](https://jasonformat.com/modern-script-loading/) explains this in more detail and covers a few options that can be used to circumvent this.

*With thanks to Connor Clark and Jason Miller for their reviews.*

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm"> Last updated: Jun 23, 2020 </span> [Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/serve-modern-code-to-modern-browsers/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-serve-modern-code/" class="w-callout__link w-callout__link--codelab">Serve modern code to modern browsers for faster page loads</a>

<a href="/fast" class="w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single gc-analytics-event">Return to all articles</a>

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
