





<a href="#remove-unused-code" class="w-toc__header--link">Remove unused code</a>
--------------------------------------------------------------------------------

-   [Analyze your bundle](#analyze-your-bundle)
-   [Remove unused libraries](#remove-unused-libraries)
-   [Remove unneeded libraries](#remove-unneeded-libraries)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Remove unused code
==================

npm makes adding code to your project a breeze. But are you really using all  
those extra bytes?

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

Registries like [npm](https://docs.npmjs.com/getting-started/what-is-npm) have transformed the JavaScript world for the better by allowing anyone to easily download and use over *half a million* public packages. But we often include libraries we're not fully utilizing. To fix this issue, **analyze your bundle** to detect unused code. Then remove **unused** and **unneeded** libraries.

Analyze your bundle <a href="#analyze-your-bundle" class="w-headline-link">#</a>
--------------------------------------------------------------------------------

DevTools makes it easy to see the size of all network requests:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Network** tab.
3.  Select the **Disable cache** checkbox.
4.  Reload the page.

<img src="https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format" alt="Network panel with bundle request" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/aq6QZj5p4KTuaWnUJnLC.png?auto=format&amp;w=1600 1600w" width="800" height="169" />

The [Coverage](https://developers.google.com/web/updates/2017/04/devtools-release-notes#coverage) tab in DevTools will also tell you how much CSS and JS code in your application is unused.

<img src="https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format" alt="Code Coverage in DevTools" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/xlPdOMaeykJhYqGcaMJr.png?auto=format&amp;w=1600 1600w" width="800" height="562" />

By specifying a full Lighthouse configuration through its Node CLI, an "Unused JavaScript" audit can also be used to trace how much unused code is being shipped with your application.

<img src="https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format" alt="Lighthouse Unused JS Audit" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/tdC0d65gEIiHZy6eyo82.png?auto=format&amp;w=1600 1600w" width="800" height="347" />

If you happen to be using [webpack](https://webpack.js.org/) as your bundler, [Webpack Bundle Analyzer](https://github.com/webpack-contrib/webpack-bundle-analyzer) will help you investigate what makes up the bundle. Include the plugin in your webpack configurations file like any other plugin:

    module.exports = {
      //...
      plugins: [
        //...
        new BundleAnalyzerPlugin()
      ]
    }

Although webpack is commonly used to build single-page applications, other bundlers, such as [Parcel](https://parceljs.org/) and [Rollup](https://rollupjs.org/guide/en), also have visualization tools that you can use to analyze your bundle.

Reloading the application with this plugin included shows a zoomable treemap of your entire bundle.

<img src="https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format" alt="Webpack Bundle Analyzer" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/pLAHEtl5C011wTk2IJij.png?auto=format&amp;w=1600 1600w" width="800" height="468" />

Using this visualization allows you to inspect which parts of your bundle are larger than others, as well as get a better idea of all the libraries that you're importing. This can help identify if you are using any unused or unnecessary libraries.

Remove unused libraries <a href="#remove-unused-libraries" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

In the previous treemap image, there are quite a few packages within a single `@firebase` domain. If your website only needs the firebase database component, update the imports to fetch that library:

    import firebase from 'firebase';
    import firebase from 'firebase/app';
    import 'firebase/database';

It is important to emphasize that this process is significantly more complex for larger applications.

For the mysterious looking package that you're quite sure is not being used anywhere, take a step back and see which of your top-level dependencies are using it. Try to find a way to only import the components that you need from it. If you aren't using a library, remove it. If the library isn't required for the initial page load, consider if it can be [lazy loaded](/reduce-javascript-payloads-with-code-splitting).

And in case you're using webpack, check out [the list of plugins that automatically remove unused code from popular libraries](https://github.com/GoogleChromeLabs/webpack-libs-optimizations).

**Try it**! [Remove unused code.](/codelab-remove-unused-code)

Remove unneeded libraries <a href="#remove-unneeded-libraries" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

Not all libraries can be easily broken down into parts and selectively imported. In these scenarios, consider if the library could be removed entirely. Building a custom solution or leveraging a lighter alternative should always be options worth considering. However, it is important to weigh the complexity and effort required for either of these efforts before removing a library entirely from an application.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/remove-unused-code/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-remove-unused-code/" class="w-callout__link w-callout__link--codelab">Remove unused code</a>

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
