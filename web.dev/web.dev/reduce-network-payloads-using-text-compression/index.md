





<a href="#minify-and-compress-network-payloads" class="w-toc__header--link">Minify and compress network payloads</a>
--------------------------------------------------------------------------------------------------------------------

-   [Measure](#measure)
-   [Minification](#minification)
-   [Data compression](#data-compression)
-   [Dynamic compression](#dynamic-compression)
-   [Static compression](#static-compression)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Minify and compress network payloads
====================================

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

There are two useful techniques that can be used to improve the performance of your web page:

-   Minification
-   Data compression

Incorporating both of these techniques reduces payload sizes and in turn improves page load times.

Measure <a href="#measure" class="w-headline-link">#</a>
--------------------------------------------------------

Lighthouse displays a failed audit if it detects any CSS or JS resources on your page that can be minified.

<img src="https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format" alt="Lighthouse Minify CSS Audit" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/ZT9ESeCStegt0SklYbni.png?auto=format&amp;w=1600 1600w" width="800" height="90" /> <img src="https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format" alt="Lighthouse Minify JS Audit" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/vDaAnUSvQxmGcoasQj1k.png?auto=format&amp;w=1600 1600w" width="800" height="112" />

It also audits for any uncompressed assets.

<img src="https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format" alt="Lighthouse: Enable text compression" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/xfqzdLuu3w3lanxo5Ggc.png?auto=format&amp;w=1600 1600w" width="800" height="123" />

Minification <a href="#minification" class="w-headline-link">#</a>
------------------------------------------------------------------

**Minification** is the process of removing whitespace and any code that is not necessary to create a smaller but perfectly valid code file. [Terser](https://github.com/terser-js/terser) is a popular JavaScript compression tool and [webpack](https://webpack.js.org/) v4 includes a plugin for this library by default to create minified build files.

-   If you're using webpack v4 or greater, you should be good to go without doing any additional work. 👍
-   If you are using an older version of webpack, install and include `TerserWebpackPlugin` into your webpack configuration settings. Follow the [documentation](https://webpack.js.org/plugins/terser-webpack-plugin/) to learn how.
-   If you are not using a module bundler, use `Terser` as a CLI tool or include it directly as a dependency to your application. The project [documentation](https://github.com/terser-js/terser) provides instructions.

Data compression <a href="#data-compression" class="w-headline-link">#</a>
--------------------------------------------------------------------------

**Compression** is the process of modifying data using a compression algorithm. [Gzip](https://www.youtube.com/watch?v=whGwm0Lky2s&feature=youtu.be&t=14m11s) is the most widely used compression format for server and client interactions. [Brotli](https://opensource.googleblog.com/2015/09/introducing-brotli-new-compression.html) is a newer compression algorithm which can provide even better compression results than Gzip.

Compressing files can significantly improve the performance of a webpage, but you rarely need to do this yourself. Many hosting platforms, CDNs and reverse proxy servers either encode assets with compression by default or allow you to easily configure them. Read the documentation for the tool that you are using to see if compression is already supported before attempting to roll out your own solution.

There are two different ways to compress files sent to a browser:

-   Dynamically
-   Statically

Both approaches have their own advantages and disadvantages which is covered in the next section. Use whichever works best for your application.

Dynamic compression <a href="#dynamic-compression" class="w-headline-link">#</a>
--------------------------------------------------------------------------------

This process involves compressing assets on-the-fly as they get requested by the browser. This can be simpler than compressing files manually or with a build process, but can cause delays if high compression levels are used.

[Express](https://expressjs.com/) is a popular web framework for Node and provides a [compression](https://github.com/expressjs/compression) middleware library. Use it to compress any asset as it gets requested. Here is an example of an entire server file that uses it correctly:

    const express = require('express');
    const compression = require('compression');

    const app = express();

    app.use(compression());

    app.use(express.static('public'));

    const listener = app.listen(process.env.PORT, function() {
        console.log('Your app is listening on port ' + listener.address().port);
    });

This compresses your assets using `gzip`. If your web server supports it, consider using a separate module like [shrink-ray](https://github.com/aickin/shrink-ray#readme) to compress via Brotli to achieve better compression ratios.

**Try it**! Use express.js to compress assets with [gzip](/codelab-text-compression) and [Brotli](/codelab-text-compression-brotli).

Static compression <a href="#static-compression" class="w-headline-link">#</a>
------------------------------------------------------------------------------

Static compression involves compressing and saving assets ahead of time. This can make the build process take longer, especially if high compression levels are used, but ensures that no delays happen when the browser fetches the compressed resource.

If your web server supports Brotli, use a plugin like [BrotliWebpackPlugin](https://github.com/mynameiswhm/brotli-webpack-plugin) with webpack to compress your assets as part of your build step. Otherwise, use [CompressionPlugin](https://github.com/webpack-contrib/compression-webpack-plugin) to compress your assets with gzip. It can be included just like any other plugin in the webpack configurations file:

    module.exports = {
        //...
      plugins: [
         //...
          new CompressionPlugin()
        ]
    }

Once compressed files are part of the build folder, create a route in your server to handle all JS endpoints to serve the compressed files. Here is an example of how this can be done with Node and Express for gzipped assets.

    const express = require('express');
    const app = express();

    app.get('*.js', (req, res, next) => {
        req.url = req.url + '.gz';
        res.set('Content-Encoding', 'gzip');
        next();
    });

    app.use(express.static('public'));

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/reduce-network-payloads-using-text-compression/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-text-compression/" class="w-callout__link w-callout__link--codelab">Minify and compress network payloads with gzip</a>
-   <a href="/codelab-text-compression-brotli/" class="w-callout__link w-callout__link--codelab">Minify and compress network payloads with brotli</a>

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
