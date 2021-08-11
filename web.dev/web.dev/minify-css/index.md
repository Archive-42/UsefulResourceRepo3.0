## <a href="#minify-css" class="w-toc__header--link">Minify CSS</a>

- [Loading unminified CSS](#loading-unminified-css)
- [Measure](#measure)
- [CSS Minification with webpack](#css-minification-with-webpack)
- [Verify](#verify)
- [Next steps and resources](#next-steps-and-resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Minify CSS

May 2, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

- <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
- <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

CSS files can contain unnecessary characters, such as comments, whitespaces, and indentation. In production, these characters can be safely removed, to reduce file size without affecting how the browser processes the styles. This technique is called **minification**.

## Loading unminified CSS <a href="#loading-unminified-css" class="w-headline-link">#</a>

Take a look at the following CSS block:

    body {
      font-family: "Benton Sans", "Helvetica Neue", helvetica, arial, sans-serif;
      margin: 2em;
    }

    /* all titles need to have the same font, color and background */
    h1 {
      font-style: italic;
      color: #373fff;
      background-color: #000000;
    }

    h2 {
      font-style: italic;
      color: #373fff;
      background-color: #000000;
    }

This content is easy to read, at the cost of producing a larger than necessary file:

- It uses spaces for indentation purposes and contains comments, which are ignored by the browser, so they can be removed.
- The `<h1>` and `<h2>` elements have the same styles: instead of declaring them separately: "`h1 {...} h2 {...}`" they could be expressed as "`h1, h2{...}`".
- The **background-color**, `#000000` could be expressed as just `#000`.

After making these changes, you would obtain a more compact version of the same styles:

    body{font-family:"Benton Sans","Helvetica Neue",helvetica,arial,sans-serif;margin:2em}h1,h2{font-style:italic;color:#373fff;background-color:#000}

You probably don't want to write CSS like that. Instead, you can write CSS as usual, and add a minification step to your build process. In this guide, you'll learn how to do it by using a popular build tool: [webpack](https://webpack.js.org/).

## Measure <a href="#measure" class="w-headline-link">#</a>

You'll apply CSS minification to a site that has been used in other guides: [Fav Kitties](https://fav-kitties-animated.glitch.me/). This version of the site uses a cool CSS library: [animate.css](https://github.com/daneden/animate.css), to animate different page elements when a user votes for a cat 😺.

As a first step, you need to understand what would be the opportunity after minifying this file:

1.  Open [the measure page](/measure).
2.  Enter the URL: `https://fav-kitties-animated.glitch.me` and click **Run Audit**.
3.  Click **View report**.
4.  Click on **Performance** and go the **Opportunities** section.

The resulting report shows that up to **16 KB** can be saved from the **animate.css** file:

<img src="https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format" alt="Lighthouse: Minify CSS opportunity." class="screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/RFMk5OMAIvOlkUZJTsh4.png?auto=format&amp;w=1600 1600w" width="800" height="172" />

Now inspect the content of the CSS:

1.  Open the [Fav Kitties site](https://fav-kitties-animated.glitch.me/) in Chrome. (It might take a while for Glitch servers to respond the first time.)
2.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
3.  Click the **Network** tab.
4.  Click the **CSS** filter.
5.  Select the **Disable cache** checkbox.
6.  Reload the app.

<img src="https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format" alt="DevTools CSS unoptimized trace" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/WgneNAyftk8jneyXxMih.png?auto=format&amp;w=1600 1600w" width="800" height="138" />

The page is requesting two CSS files, of **1.9KB** and **76.2KB** respectively.

1.  Click **animate.css**.
2.  Click the **Response** tab, to see the file contents.

Note that the stylesheet contains characters for whitespaces and indentation:

<img src="https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format" alt="DevTools CSS unoptimized response" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/UEB5Xxe5IHhGtMx3XfKD.png?auto=format&amp;w=1600 1600w" width="800" height="286" />

Next, you'll add some webpack plugins to your build process to minify these files.

**Note:** the previous Lighthouse report only lists `animate.css` as an opportunity for minification. Minifying `style.css` will also save some bytes, but not enough for Lighthouse to consider it a significant savings. However, minifying CSS is a general best practice; so it makes sense to minify all of your CSS files.

## CSS Minification with webpack <a href="#css-minification-with-webpack" class="w-headline-link">#</a>

Before jumping into the optimizations, take some time understanding how build process for the [Fav Kitties site](https://glitch.com/edit/#!/fav-kitties-animated?path=webpack.config.js:1:0%5D) works:

By default, the resulting JS bundle that webpack produces would contain the content of the CSS files inlined. Since we want to maintain separate CSS files, we are using two complementary plugins:

- [mini-css-extract-plugin](https://github.com/webpack-contrib/mini-css-extract-plugin) will extract each style sheet into its own file, as one of the steps of the build process.
- [webpack-fix-style-only-entries](https://github.com/fqborges/webpack-fix-style-only-entries) is used to correct an issue in wepback 4, to avoid generating an extra JS file for each CSS file listed in **webpack-config.js**.

You will now make some changes in the project:

1.  Open [the Fav Kitties project in Glitch](https://glitch.com/~fav-kitties-animated).
2.  To view the source, press **View Source**.
3.  Click **Remix to Edit** to make the project editable.
4.  Click **Tools**.
5.  Click **Logs**.
6.  Click **Console**.

To minify the resulting CSS, you'll use the [optimize-css-assets-webpack-plugin](https://github.com/NMFR/optimize-css-assets-webpack-plugin):

1.  In Glitch console, run `npm install --save-dev optimize-css-assets-webpack-plugin`.
2.  Run `refresh`, so the changes are synchronized with the Glitch editor.

Next, go back to the Glitch editor, open the **webpack.config.js** file, and make the following modifications:

Load the module at the beginning of the file:

    const OptimizeCSSAssetsPlugin = require("optimize-css-assets-webpack-plugin");

Then, pass an instance of the plugin to the **plugins** array:

      plugins: [
        new HtmlWebpackPlugin({template: "./src/index.html"}),
        new MiniCssExtractPlugin({filename: "[name].css"}),
        new FixStyleOnlyEntriesPlugin(),
        new OptimizeCSSAssetsPlugin({})
      ]

After making the changes a rebuild of the project will be triggered. This is how the resulting **webpack.config.js** will look like:

Next, you'll check the result of this optimization with performance tools.

## Verify <a href="#verify" class="w-headline-link">#</a>

- To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

If you got lost in any previous step, you can click [here](https://fav-kitties-animated-min.glitch.me/), to open an optimized version of the site.

To inspect the size and content of the files:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Network** tab.
3.  Click the **CSS** filter.
4.  Select the **Disable cache** checkbox if it isn't already.
5.  Reload the app.

<img src="https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format" alt="DevTools CSS unoptimized response" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/id5kWwB3NilmVPWPTM59.png?auto=format&amp;w=1600 1600w" width="800" height="130" />

You can inspect these files, and see that the new versions don't contain any whitespaces. Both files are much smaller, in particular, the [animate.css](http://fav-kitties-animated-min.glitch.me/animate.css) has been reduced in **~26%**, saving **~20KB**!

As a final step:

1.  Open [the measure page](/measure).
2.  Enter the URL of the optimized site.
3.  Click **View report**.
4.  Click on **Performance** and find the **Opportunities** section.

The report doesn't show "Minify CSS" as "Opportunity" anymore, and has now moved to "Passed Audits" section:

<img src="https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format" alt="Lighthouse Passed Audits for optimized page." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/zegn2qIHYYK58w1GhgYd.png?auto=format&amp;w=1600 1600w" width="800" height="163" />

Since CSS files are [render-blocking resources](https://developers.google.com/web/tools/lighthouse/audits/blocking-resources), if you apply minification on sites that use large CSS files, you can see improvements on metrics like [First Contentful Paint](/first-contentful-paint).

## Next steps and resources <a href="#next-steps-and-resources" class="w-headline-link">#</a>

In this guide, we've covered CSS Minification with webpack, but the same approach can be followed with other build tools, like [gulp-clean-css](https://www.npmjs.com/package/gulp-clean-css) for [Gulp](https://gulpjs.com/), or [grunt-contrib-cssmin](https://www.npmjs.com/package/grunt-contrib-cssmin) for [Grunt](https://gruntjs.com/).

Minification can also be applied to other types of files. Check out the [Minify and compress network payloads guide](/fast/reduce-network-payloads-using-text-compression) to learn more about tools to minify JS, and some complementary techniques, like compression.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: May 2, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/minify-css/index.md)

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
