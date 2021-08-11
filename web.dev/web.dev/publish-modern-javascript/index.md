





<img src="https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/UQbMiPKbXL1EDjtWsLju.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#publish-ship-and-install-modern-javascript-for-faster-applications" class="w-toc__header--link">Publish, ship, and install modern JavaScript for faster applications</a>
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [Modern JavaScript](#modern-javascript)
-   [Legacy JavaScript](#legacy-javascript)
-   [Modern JavaScript on npm](#modern-javascript-on-npm)
-   [Modern-only](#modern-only)
-   [Modern with legacy fallback](#modern-with-legacy-fallback)
-   [Modern with legacy fallback and ESM bundler optimizations](#modern-with-legacy-fallback-and-esm-bundler-optimizations)
-   [Modern JavaScript in applications](#modern-javascript-in-applications)
-   [webpack](#webpack)
-   [Optimize Plugin](#optimize-plugin)
-   [BabelEsmPlugin](#babelesmplugin)
-   [Configure babel-loader to transpile node\_modules](#configure-babel-loader-to-transpile-node_modules)
-   [Rollup](#rollup)
-   [@rollup/plugin-babel](#@rollupplugin-babel)
-   [Additional build tools](#additional-build-tools)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

-   <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
-   <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

Publish, ship, and install modern JavaScript for faster applications
====================================================================

Improve performance by turning on modern JavaScript dependencies and output.

Dec 10, 2020 <span class="w-author__separator">•</span> Updated Dec 16, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jason Miller" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/developit/)

<a href="/authors/developit/" class="w-author__name-link">Jason Miller</a>

-   <a href="https://twitter.com/_developit" class="w-author__link">Twitter</a>
-   <a href="https://github.com/developit" class="w-author__link">GitHub</a>
-   <a href="https://jasonformat.com" class="w-author__link">Blog</a>

Over 90% of browsers are capable of running modern JavaScript, but the prevalence of legacy JavaScript remains one of the biggest contributors to performance problems on the web today. [EStimator.dev](http://estimator.dev/) is a simple web-based tool that calculates the size and performance improvement a site could achieve by delivering modern JavaScript syntax.

<figure><img src="https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format" alt="EStimator.dev" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/FHHnXqdjdsC6PNSSnnC4.png?auto=format&amp;w=1600 1600w" width="800" height="785" /><figcaption>EStimator.dev</figcaption></figure>The web today is limited by legacy JavaScript, and no single optimization will improve performance as much as writing, publishing, and shipping your web page or package using **ES2017** syntax.

Modern JavaScript <a href="#modern-javascript" class="w-headline-link">#</a>
----------------------------------------------------------------------------

Modern JavaScript is not characterized as code written in a specific ECMAScript specification version, but rather in syntax that is supported by all modern browsers. Modern web browsers like Chrome, Edge, Firefox, and Safari make up more than [90% of the browser market](https://www.caniuse.com/usage-table), and different browsers that rely on the same underlying rendering engines make up an additional 5%. This means that 95% of global web traffic comes from browsers that support the most widely used JavaScript language features from the past 10 years, including:

-   Classes (ES2015)
-   Arrow functions (ES2015)
-   Generators (ES2015)
-   Block scoping (ES2015)
-   Destructuring (ES2015)
-   Rest and spread parameters (ES2015)
-   Object shorthand (ES2015)
-   Async/await (ES2017)

Features in newer versions of the language specification generally have less consistent support across modern browsers. For example, many ES2020 and ES2021 features are only supported in 70% of the browser market—still the majority of browsers, but not enough that it's safe to rely on those features directly. This means that although "modern" JavaScript is a moving target, ES2017 has the widest range of browser compatibility [while including most of the commonly used modern syntax features](https://dev.to/garylchew/bringing-modern-javascript-to-libraries-432c). In other words, **ES2017 is the closest to modern syntax today**.

Legacy JavaScript <a href="#legacy-javascript" class="w-headline-link">#</a>
----------------------------------------------------------------------------

Legacy JavaScript is code that specifically avoids using all the above language features. Most developers write their source code using modern syntax, but compile everything to legacy syntax for increased browser support. Compiling to legacy syntax does increase browser support, however the effect is often smaller than we realize. In many cases the support increases from around 95% to 98% while incurring a significant cost:

-   Legacy JavaScript is typically around 20% larger and slower than equivalent modern code. Tooling deficiencies and misconfiguration often widen this gap even further.

-   Installed libraries account for as much as 90% of typical production JavaScript code. Library code incurs an even higher legacy JavaScript overhead due to polyfill and helper duplication that could be avoided by publishing modern code.

Modern JavaScript on npm <a href="#modern-javascript-on-npm" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------

Recently, Node.js has standardized an `"exports"` field to define [entry points for a package](https://nodejs.org/api/packages.html#packages_package_entry_points):

    {
      "exports": "./index.js"
    }

Modules referenced by the `"exports"` field imply a Node version of at least 12.8, which supports ES2019. This means that any module referenced using the `"exports"` field can be *written in modern JavaScript*. Package consumers must assume modules with an `"exports"` field contain modern code and transpile if necessary.

### Modern-only <a href="#modern-only" class="w-headline-link">#</a>

If you want to publish a package with modern code and leave it up to the consumer to handle transpiling it when they use it as a dependency—use only the `"exports"` field.

    {
      "name": "foo",
      "exports": "./modern.js"
    }

**Caution**: This approach is *not recommended*. In a perfect world, every developer would have already configured their build system to transpile all dependencies (`node_modules`) to their required syntax. However, this is not currently the case, and publishing your package using only modern syntax would prevent its usage in applications that would be accessed through legacy browsers.

### Modern with legacy fallback <a href="#modern-with-legacy-fallback" class="w-headline-link">#</a>

Use the `"exports"` field along with `"main"` in order to publish your package using modern code but also include an ES5 + CommonJS fallback for legacy browsers.

    {
      "name": "foo",
      "exports": "./modern.js",
      "main": "./legacy.cjs"
    }

### Modern with legacy fallback and ESM bundler optimizations <a href="#modern-with-legacy-fallback-and-esm-bundler-optimizations" class="w-headline-link">#</a>

In addition to defining a fallback CommonJS entrypoint, the `"module"` field can be used to point to a similar legacy fallback bundle, but one that uses JavaScript module syntax (`import` and `export`).

    {
      "name": "foo",
      "exports": "./modern.js",
      "main": "./legacy.cjs",
      "module": "./module.js"
    }

Many bundlers, such as webpack and Rollup, rely on this field to take advantage of module features and enable [tree shaking](/commonjs-larger-bundles/#how-does-commonjs-affect-your-final-bundle-size). This is still a legacy bundle that does not contain any modern code aside from `import`/`export` syntax, so use this approach to ship modern code with a legacy fallback that is still optimized for bundling.

Modern JavaScript in applications <a href="#modern-javascript-in-applications" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

Third-party dependencies make up the vast majority of typical production JavaScript code in web applications. While npm dependencies have historically been published as legacy ES5 syntax, this is no longer a safe assumption and risks dependency updates breaking browser support in your application.

With an increasing number of npm packages moving to modern JavaScript, it's important to ensure that the build tooling is set up to handle them. There's a good chance some of the npm packages you depend on are already using modern language features. There are a number of options available to use modern code from npm without breaking your application in older browsers, but the general idea is to have the build system transpile dependencies to the same syntax target as your source code.

webpack <a href="#webpack" class="w-headline-link">#</a>
--------------------------------------------------------

As of webpack 5, it is now possible to configure what syntax webpack will use when generating code for bundles and modules. This doesn't transpile your code or dependencies, it only affects the "glue" code generated by webpack. To specify the browser support target, add a [browserslist configuration](https://github.com/browserslist/browserslist#readme) to your project, or do it directly in your webpack configuration:

    module.exports = {
      target: ['web', 'es2017'],
    };

It is also possible to configure webpack to generate optimized bundles that omit unnecessary wrapper functions when targeting a modern ES Modules environment. This also configures webpack to load code-split bundles using `<script type="module">`.

    module.exports = {
      target: ['web', 'es2017'],
      output: {
        module: true,
      },
      experiments: {
        outputModule: true,
      },
    };

There are a number of webpack plugins available that make it possible to compile and ship modern JavaScript while still supporting legacy browsers, such as Optimize Plugin and BabelEsmPlugin.

### Optimize Plugin <a href="#optimize-plugin" class="w-headline-link">#</a>

[Optimize Plugin](https://github.com/developit/optimize-plugin) is a webpack plugin that transforms final bundled code from modern to legacy JavaScript instead of each individual source file. It's a self-contained setup that allows your webpack configuration to assume everything is modern JavaScript with no special branching for multiple outputs or syntaxes.

Since Optimize Plugin operates on bundles instead of individual modules, it processes your application's code and your dependencies equally. This makes it safe to use modern JavaScript dependencies from npm, because their code will be bundled and transpiled to the correct syntax. It can also be faster than traditional solutions involving two compilation steps, while still generating separate bundles for modern and legacy browsers. The two sets of bundles are designed to be loaded using the [module/nomodule pattern](/serve-modern-code-to-modern-browsers/).

    // webpack.config.js
    const OptimizePlugin = require('optimize-plugin');

    module.exports = {
      // ...
      plugins: [new OptimizePlugin()],
    };

`Optimize Plugin` can be faster and more efficient than custom webpack configurations, which typically bundle modern and legacy code separately. It also handles running [Babel](https://babeljs.io/) for you, and minifies bundles using [Terser](https://terser.org/) with separate optimal settings for the modern and legacy outputs. Finally, polyfills needed by the generated legacy bundles are extracted into a dedicated script so they are never duplicated or unnecessarily loaded in newer browsers.

Comparison: transpiling source modules twice versus transpiling generated bundles.

### BabelEsmPlugin <a href="#babelesmplugin" class="w-headline-link">#</a>

[BabelEsmPlugin](https://github.com/prateekbh/babel-esm-plugin) is a webpack plugin that works along with [@babel/preset-env](https://babeljs.io/docs/en/babel-preset-env) to generate modern versions of existing bundles to ship less transpiled code to modern browsers. It is the most popular off-the-shelf solution for module/nomodule, used by [Next.js](https://nextjs.org/) and [Preact CLI](https://preactjs.com/cli/).

    // webpack.config.js
    const BabelEsmPlugin = require('babel-esm-plugin');

    module.exports = {
      //...
      module: {
        rules: [
          // your existing babel-loader configuration:
          {
            test: /\.js$/,
            exclude: /node_modules/,
            use: {
              loader: 'babel-loader',
              options: {
                presets: ['@babel/preset-env'],
              },
            },
          },
        ],
      },
      plugins: [new BabelEsmPlugin()],
    };

`BabelEsmPlugin` supports a wide array of webpack configurations, because it runs two largely separate builds of your application. Compiling twice can take a little bit of extra time for large applications, however this technique allows `BabelEsmPlugin` to integrate seamlessly into existing webpack configurations and makes it one of the most convenient options available.

### Configure babel-loader to transpile node\_modules <a href="#configure-babel-loader-to-transpile-node_modules" class="w-headline-link">#</a>

If you are using `babel-loader` without one of the previous two plugins, there's an important step required in order to consume modern JavaScript npm modules. Defining two separate `babel-loader` configurations makes it possible to automatically compile modern language features found in `node_modules` to ES2017, while still transpiling your own first-party code with the Babel plugins and presets defined in your project's configuration. This doesn't generate modern and legacy bundles for a module/nomodule setup, but it does make it possible to install and use npm packages that contain modern JavaScript without breaking older browsers.

[webpack-plugin-modern-npm](https://www.npmjs.com/package/webpack-plugin-modern-npm) uses this technique to compile npm dependencies that have an `"exports"` field in their `package.json`, since these may contain modern syntax:

    // webpack.config.js
    const ModernNpmPlugin = require('webpack-plugin-modern-npm');

    module.exports = {
      plugins: [
        // auto-transpile modern stuff found in node_modules
        new ModernNpmPlugin(),
      ],
    };

Alternatively, you can implement the technique manually in your webpack configuration by checking for an `"exports"` field in the `package.json` of modules as they are resolved. Omitting caching for brevity, a custom implementation might look like this:

    // webpack.config.js
    module.exports = {
      module: {
        rules: [
          // Transpile for your own first-party code:
          {
            test: /\.js$/i,
            loader: 'babel-loader',
            exclude: /node_modules/,
          },
          // Transpile modern dependencies:
          {
            test: /\.js$/i,
            include(file) {
              let dir = file.match(/^.*[/\\]node_modules[/\\](@.*?[/\\])?.*?[/\\]/);
              try {
                return dir && !!require(dir[0] + 'package.json').exports;
              } catch (e) {}
            },
            use: {
              loader: 'babel-loader',
              options: {
                babelrc: false,
                configFile: false,
                presets: ['@babel/preset-env'],
              },
            },
          },
        ],
      },
    };

When using this approach, you'll need to ensure modern syntax is supported by your minifier. Both [Terser](https://github.com/terser/terser#minify-options) and [uglify-es](https://github.com/mishoo/UglifyJS/tree/harmony#minify-options) have an option to specify `{ecma: 2017}` in order to preserve and in some cases generate ES2017 syntax during compression and formatting.

Rollup <a href="#rollup" class="w-headline-link">#</a>
------------------------------------------------------

Rollup has built-in support for generating multiple sets of bundles as part of a single build, and generates modern code by default. As a result, Rollup can be configured to generate modern and legacy bundles with the official plugins you're likely already using.

### @rollup/plugin-babel <a href="#@rollupplugin-babel" class="w-headline-link">#</a>

If you use Rollup, the [`getBabelOutputPlugin()` method](https://github.com/rollup/plugins/tree/master/packages/babel#running-babel-on-the-generated-code) (provided by Rollup's [official Babel plugin](https://github.com/rollup/plugins/tree/master/packages/babel)) transforms the code in generated bundles rather than individual source modules. Rollup has built-in support for generating multiple sets of bundles as part of a single build, each with their own plugins. You can use this to produce different bundles for modern and legacy by passing each through a different Babel output plugin configuration:

    // rollup.config.js
    import {getBabelOutputPlugin} from '@rollup/plugin-babel';

    export default {
      input: 'src/index.js',
      output: [
        // modern bundles:
        {
          format: 'es',
          plugins: [
            getBabelOutputPlugin({
              presets: [
                [
                  '@babel/preset-env',
                  {
                    targets: {esmodules: true},
                    bugfixes: true,
                    loose: true,
                  },
                ],
              ],
            }),
          ],
        },
        // legacy (ES5) bundles:
        {
          format: 'amd',
          entryFileNames: '[name].legacy.js',
          chunkFileNames: '[name]-[hash].legacy.js',
          plugins: [
            getBabelOutputPlugin({
              presets: ['@babel/preset-env'],
            }),
          ],
        },
      ],
    };

Additional build tools <a href="#additional-build-tools" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------

Rollup and webpack are highly-configurable, which generally means each project must update its configuration enable modern JavaScript syntax in dependencies. There are also higher-level build tools that favor convention and defaults over configuration, like [Parcel](https://parceljs.org/), [Snowpack](https://www.snowpack.dev/), [Vite](https://github.com/vitejs/vite) and [WMR](https://github.com/preactjs/wmr). Most of these tools assume npm dependencies may contain modern syntax, and will transpile them to the appropriate syntax level(s) when building for production.

In addition to dedicated plugins for webpack and Rollup, modern JavaScript bundles with legacy fallbacks can be added to any project using [devolution](https://github.com/theKashey/devolution). Devolution is a standalone tool that transforms the output from a build system to produce legacy JavaScript variants, allowing bundling and transformations to assume a modern output target.

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

[EStimator.dev](http://estimator.dev/) was built to provide an easy way to assess how much of an impact it can make to switch to modern-capable JavaScript code for the majority of your users. Today, ES2017 is the closest to modern syntax and tools such as npm, Babel, webpack, and Rollup have made it possible to configure your build system and write your packages using this syntax. This post covers several approaches, and you should use the easiest option that works for your use case.

  

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Dec 16, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/publish-modern-javascript/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-serve-modern-code/" class="w-callout__link w-callout__link--codelab">Serve modern code to modern browsers for faster page loads</a>

<a href="/blog" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
