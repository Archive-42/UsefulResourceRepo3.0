

## <a href="#incorporate-performance-budgets-into-your-build-process" class="w-toc__header--link">Incorporate performance budgets into your build process</a>

- [Lighthouse performance budgets](#lighthouse-performance-budgets)
- [Webpack performance hints](#webpack-performance-hints)
- [Bundlesize](#bundlesize)
- [Bundlesize CLI](#bundlesize-cli)
- [Bundlesize for CI](#bundlesize-for-ci)
- [Lighthouse Bot](#lighthouse-bot)
- [Summary](#summary)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Incorporate performance budgets into your build process

Feb 1, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

- <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
- <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
- <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

Once you've defined a performance budget, it's time to set up the build process to keep track of it. There are a number of tools that let you define thresholds for chosen performance metrics and warn you if you go over budget. Find out how to choose one that best fits your needs and current setup. 🕵️‍♀️

## Lighthouse performance budgets <a href="#lighthouse-performance-budgets" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) is an auditing tool that tests sites in a few key areas—performance, accessibility, best practices and how well your site performs as a progressive web application.

The [command line version](https://developers.google.com/web/tools/lighthouse/#cli) of Lighthouse (v5+) supports setting [performance budgets](https://developers.google.com/web/tools/lighthouse/audits/budgets) based on:

- resource size
- resource count

You can set budgets for any of the following resource types:

- `document`
- `font`
- `image`
- `media`
- `other`
- `script`
- `stylesheet`
- `third-party`
- `total`

Budgets are set in a JSON file and after defining them the new "Over Budget" column tells you whether you're exceeding any limits.

## <figure><img src="https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format" alt="&quot;Budgets&quot; section in Lighthouse report" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/fsRNXJXQ5JESUuwsIlLn.png?auto=format&amp;w=1600 1600w" width="800" height="199" /><figcaption>"Budgets" section in Lighthouse report</figcaption></figure>Webpack performance hints <a href="#webpack-performance-hints" class="w-headline-link">#</a>

[Webpack](https://developers.google.com/web/fundamentals/performance/webpack/) is a powerful build tool for optimizing how your code is delivered to the users. It also supports setting performance budgets based on **asset size**.

Turn on [performance hints](https://webpack.js.org/configuration/performance/) in `webpack.config.js` to get command line warnings or errors when your bundle size grows over the limit. It's a great way to stay mindful about asset sizes throughout the development.

After the build step, webpack outputs a color-coded list of assets and their sizes. Anything over budget is highlighted in yellow.

<figure><img src="https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format" alt="The highlighted bundle.js is bigger than your budget" class="w-screenshot w-screenshot--filled" sizes="(min-width: 617px) 617px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/G96Z2pZVL6aowVRa49rA.png?auto=format&amp;w=1234 1234w" width="617" height="86" /><figcaption>The highlighted bundle.js is bigger than your budget</figcaption></figure>The default limit for both assets and entry-points is **250 KB**. You can set your own targets in the configuration file.

<figure><img src="https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format" alt="Webpack bundle size warning ⚠️" class="w-screenshot w-screenshot--filled" sizes="(min-width: 566px) 566px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/StfxwSScNVzmeM70gwp4.jpg?auto=format&amp;w=1132 1132w" width="566" height="104" /><figcaption>Webpack bundle size warning ⚠️</figcaption></figure>The budgets are compared against **uncompressed asset sizes**. Uncompressed [JavaScript size is related to the execution time](https://v8.dev/blog/cost-of-javascript-2019) and big files can take a long time to execute, especially on mobile devices.

Compressed asset sizes affect the transfer time, which is very important on slow networks.

## <figure><img src="https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format" alt="Bonus feature: webpack won’t only warn you, it will give you a recommendation on how to downsize your bundles. 💁" class="w-screenshot w-screenshot--filled" sizes="(min-width: 556px) 556px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/ogH1cMiF96iyhj8CiENK.jpg?auto=format&amp;w=1112 1112w" width="556" height="84" /><figcaption>Bonus feature: webpack won’t only warn you, it will give you a recommendation on how to downsize your bundles. 💁</figcaption></figure>Bundlesize <a href="#bundlesize" class="w-headline-link">#</a>

[Bundlesize](https://github.com/siddharthkp/bundlesize) is a simple npm package that tests asset size against a threshold you've set. It can run locally and integrate with your CI.

### Bundlesize CLI <a href="#bundlesize-cli" class="w-headline-link">#</a>

Run [bundlesize CLI](https://github.com/siddharthkp/bundlesize#cli) by specifying a threshold and the file that you want to test.

    bundlesize -f "dist/bundle.js" -s 170kB

Bundlesize outputs color-coded test results in one line.

<figure><img src="https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format" alt="Failing bundlesize CLI test ❌" class="w-screenshot w-screenshot--filled" sizes="(min-width: 473px) 473px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/6YsTnhpUlzbTB1ja23yP.png?auto=format&amp;w=946 946w" width="473" height="36" /><figcaption>Failing bundlesize CLI test ❌</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format" alt="Passing bundlesize CLI test ✔️" class="w-screenshot w-screenshot--filled" sizes="(min-width: 460px) 460px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/TjynyaIzZlRa6xE2uVcD.png?auto=format&amp;w=920 920w" width="460" height="36" /><figcaption>Passing bundlesize CLI test ✔️</figcaption></figure>### Bundlesize for CI <a href="#bundlesize-for-ci" class="w-headline-link">#</a>

You'll get the most value out of bundlesize if you integrate it with a CI to automatically enforce size limits on pull requests. **If bundlesize test fails, that pull request is not merged.** It works for pull requests on GitHub with [Travis CI](https://travis-ci.org/), [CircleCI](https://circleci.com/), [Wercker](http://www.wercker.com/), and [Drone](http://readme.drone.io/).

<figure><img src="https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format" alt="Bundlesize check status on Github" class="screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/RKpNwfcXRoKZ34qDoxcO.jpg?auto=format&amp;w=1600 1600w" width="800" height="326" /><figcaption>Bundlesize check status on Github</figcaption></figure>You may have a fast app today, but adding new code can often change this. Checking pull requests with bundlesize will help you avoid performance regressions. Bootstrap, Tinder, Trivago and many others use it to keep their budgets in check.

With bundlesize, it's possible to set thresholds for each file separately. This is especially useful if you are splitting a bundle in your application.

By default, **it tests gzipped asset sizes**. You can use the compression option to switch to [brotli compression](https://css-tricks.com/brotli-static-compression/) or turn it off completely.

## Lighthouse Bot <a href="#lighthouse-bot" class="w-headline-link">#</a>

<figure><img src="https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/5zLlIEUm06wEbu3J1WjG.png?auto=format&amp;w=1600 1600w" width="800" height="267" /></figure>[Lighthouse Bot](https://github.com/ebidel/lighthouse-ci) integrates with Travis CI and enforces budgets based on any of the five Lighthouse audit categories. For example, a budget of 100 for your Lighthouse performance score. It's sometimes simpler to keep an eye on a single number than individual asset budgets and Lighthouse scores take many things into account.

<figure><img src="https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format" alt="Lighthouse scores 💯" class="screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/6yVLSYcr0eCytJixZ1bK.png?auto=format&amp;w=1600 1600w" width="800" height="211" /><figcaption>Lighthouse scores 💯</figcaption></figure>Lighthouse Bot runs an audit after you deploy a site to staging server. In `.travis.yml` set budgets for particular Lighthouse categories with `--perf`, `--a11y`, `--bp`, `--seo` or `--pwa` options. Aim to stay in the green zone with scores of at least 90.

    after_success:
      - ./deploy.sh # Deploy the PR changes to staging server
      - npm run lh -- --perf=96 https://staging.example.com # Run Lighthouse test

If the scores for a pull request on GitHub fall below the threshold you've set, **Lighthouse Bot can prevent pull request from being merged**. ⛔

<figure><img src="https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format" alt="Lighthouse Bot check status on Github" class="screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/nVDqJAA1DZDFqpOaQA9J.png?auto=format&amp;w=1600 1600w" width="800" height="175" /><figcaption>Lighthouse Bot check status on Github</figcaption></figure>**Lighthouse Bot** then comments on your pull request with updated scores. This is a neat feature which encourages conversation about performance as code changes are happening.

<figure><img src="https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format" alt="Lighthouse reporting scores on pull request 💬" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/q1BUp838y2oSs70Suxyb.png?auto=format&amp;w=1600 1600w" width="800" height="383" /><figcaption>Lighthouse reporting scores on pull request 💬</figcaption></figure>If you find your pull request blocked by a poor Lighthouse score, run an audit with [Lighthouse CLI](https://developers.google.com/web/tools/lighthouse/#cli) or in [Dev Tools](https://developers.google.com/web/tools/lighthouse/#devtools). It generates a report with details about bottlenecks and hints for simple optimizations.

## Summary <a href="#summary" class="w-headline-link">#</a>

<table><colgroup><col style="width: 25%" /><col style="width: 25%" /><col style="width: 25%" /><col style="width: 25%" /></colgroup><thead><tr class="header"><th>Tool</th><th>CLI</th><th>CI</th><th>Summary</th></tr></thead><tbody><tr class="odd"><td>Lighthouse</td><td>✔️</td><td>❌</td><td><ul><li>Budgets for different types of resources based on their size or count.</li></ul></td></tr><tr class="even"><td>webpack</td><td>✔️</td><td>❌</td><td><ul><li>Budgets based on sizes of assets generated by webpack.</li><li>Checks uncompressed sizes.</li></ul></td></tr><tr class="odd"><td>bundlesize</td><td>✔️</td><td>✔️</td><td><ul><li>Budgets based on sizes of specific resources.</li><li>Checks compressed or uncompressed sizes.</li></ul></td></tr><tr class="even"><td>Lighthouse Bot</td><td>❌</td><td>✔️</td><td><ul><li>Budgets based on Lighthouse scores.</li></ul></td></tr></tbody></table>

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Feb 1, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/incorporate-performance-budgets-into-your-build-tools/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-setting-performance-budgets-with-webpack/" class="w-callout__link w-callout__link--codelab">Setting performance budgets with webpack</a>

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
