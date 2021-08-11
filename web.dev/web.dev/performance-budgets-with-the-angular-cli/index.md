<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format" alt="A closeup photo of a calculator." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/dDEEMFg0WKylKvlOwlQ3.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#performance-budgets-with-the-angular-cli" class="w-toc__header--link">Performance budgets with the Angular CLI</a>
----------------------------------------------------------------------------------------------------------------------------

-   [Calculate your performance budget](#calculate-your-performance-budget)
-   [Configure a performance budget in the Angular CLI](#configure-a-performance-budget-in-the-angular-cli)
-   [Enforce your budget as part of continuous integration](#enforce-your-budget-as-part-of-continuous-integration)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Performance budgets with the Angular CLI
========================================

Monitor the sizes of your bundles over time to make sure your application stays fast.

Jul 2, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/angular" class="w-post-signpost__link">Angular</a>

[<img src="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Minko Gechev" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mgechev/)

<a href="/authors/mgechev/" class="w-author__name-link">Minko Gechev</a>

-   <a href="https://twitter.com/mgechev" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mgechev" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@mgechev" class="w-author__link">Glitch</a>
-   <a href="https://blog.mgechev.com/" class="w-author__link">Blog</a>

Optimizing an Angular application is important, but how do you make sure its performance doesn't regress over time? By introducing performance metrics and monitoring them on each code change!

One important metric is the size of the JavaScript shipped with your application. By introducing a [performance budget](/performance-budgets-101) that you monitor on each build or pull request, you can make sure your optimizations persist over time.

Calculate your performance budget <a href="#calculate-your-performance-budget" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

You can use [this online budget calculator](https://bit.ly/perf-budget-calculator) to estimate how much JavaScript your app can afford to load, depending on the [Time to Interactive](/interactive) you're aiming for.

<img src="https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format" alt="Budget calculator" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/TWPRBRI7ja8d33unYYK6.png?auto=format&amp;w=1600 1600w" width="800" height="524" />

Configure a performance budget in the Angular CLI <a href="#configure-a-performance-budget-in-the-angular-cli" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------

Once you have a target JavaScript budget, you can enforce it using the [Angular command line interface (CLI)](https://cli.angular.io/). To see how that works, check out [this sample app on GitHub](https://github.com/mgechev/budgets-web-dev/blob/master/angular.json#L33-L38).

You'll see that the following budget has been configured in `angular.json`:

    "budgets": [{
      "type": "bundle",
      "name": "main",
      "maximumWarning": "170kb",
      "maximumError": "250kb"
    }]

Here's a summary of what's being specified:

-   There's a budget for a JavaScript bundle called `main`.
-   If the `main` bundle gets bigger than 170 KB, the Angular CLI will show a warning in the console when you build the app.
-   If the `main` bundle gets bigger than 250 KB, the build will fail.

Now try building the app by running `ng build --prod`.

You should see this error in the console:

<img src="https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format" alt="Budget failure" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/KXJS3kX1XGnItcrS8HJS.png?auto=format&amp;w=1600 1600w" width="800" height="258" />

To fix the build error, take a look at `app.component.ts`, which includes an import from `rxjs/internal/operators`. This is a private import that's not supposed to be used by consumers of `rxjs`. It increases the bundle size a lot! When you update to the correct import, `rxjs/operators`, and run the build again, you'll see that it passes the budget check successfully.

Note that, since [differential loading](https://dev.to/lacolaco/differential-loading-a-new-feature-of-angular-cli-v8-4jl) is enabled by default in the Angular CLI, the `ng build` command produces two builds of the app:

-   A build for browsers *with* ECMAScript 2015 support. This build includes fewer polyfills and more modern JavaScript syntax. That syntax is more expressive, which leads to smaller bundles.
-   A build for older browsers *without* ECMAScript 2015 support. The older syntax is less expressive and requires more polyfills, which leads to larger bundles.

The `index.html` file of the sample app refers to both builds so that modern browsers can take advantage of the smaller ECMAScript 2015 build and older browsers can fall back to the ECMAScript 5 build.

Enforce your budget as part of continuous integration <a href="#enforce-your-budget-as-part-of-continuous-integration" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------

[Continuous integration (CI)](https://en.wikipedia.org/wiki/Continuous_integration) offers a convenient way to monitor the budget of your app over time. And, luckily, the quickest way to set that up is to build your app with the Angular CLI—no extra steps required! Whenever the JavaScript bundle exceeds the budget, the process will exit with code 1, and the build will fail.

If you prefer, you can also enforce a performance budget using [bundlesize](https://github.com/siddharthkp/bundlesize) and [Lighthouse](/using-lighthouse-bot-to-set-a-performance-budget/). The main difference between performance budgets in the Angular CLI and Lighthouse is when the checks get performed. The Angular CLI performs the checks at build time, looking at the production assets and verifying their sizes. Lighthouse, however, opens the deployed version of the application and measures the asset size. Both approaches have their pros and cons. The check that Angular CLI performs is less robust but much faster since it's a single disk lookup. On the other hand, the LightWallet of Lighthouse can perform a very accurate check by considering dynamically loaded resources, but it needs to deploy and open the app each time it runs.

bundlesize is quite similar to the Angular CLI's budget check; the main difference is that bundlesize can show the check results directly in GitHub's user interface.

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

Establish performance budgets with the Angular CLI to make sure your Angular app's performance doesn't regress over time:

1.  Set a baseline for the resource size either by using a budget calculator or by following your organization's practices.
2.  Configure size budgets in `angular.json` under `projects.[PROJECT-NAME].architect.build.configurations.production.budgets`
3.  The budgets will be automatically enforced on each build with the Angular CLI.
4.  Consider introducing budget monitoring as part of continuous integration (which can also be achieved with the Angular CLI).

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jul 2, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/angular/performance-budgets-with-the-angular-cli/index.md)

<a href="/angular" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
