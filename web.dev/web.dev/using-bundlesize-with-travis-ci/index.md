<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#using-bundlesize-with-travis-ci" class="w-toc__header--link">Using bundlesize with Travis CI</a>
----------------------------------------------------------------------------------------------------------

-   [Set the performance budget](#set-the-performance-budget)
-   [Create a test script](#create-a-test-script)
-   [Set up continuous integration](#set-up-continuous-integration)
-   [Integrate GitHub and Travis CI](#integrate-github-and-travis-ci)
-   [Authorize bundlesize to post on pull requests](#authorize-bundlesize-to-post-on-pull-requests)
-   [Try it out](#try-it-out)
-   [Trigger your first bundlesize test](#trigger-your-first-bundlesize-test)
-   [Optimize](#optimize)
-   [Re-run test](#re-run-test)
-   [Monitor](#monitor)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Using bundlesize with Travis CI
===============================

Feb 1, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

-   <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
-   <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

Using [bundlesize](https://github.com/siddharthkp/bundlesize) with [Travis CI](https://travis-ci.com/) lets you define performance budgets with minimal setup and enforce them as part of your development workflow. Travis CI is a service that runs tests for your app in the cloud every time you push code to GitHub. You can [configure your repository](https://help.github.com/articles/about-required-status-checks/) so that it won't allow merging pull-requests unless the bundlesize tests have passed.

Bundlesize's GitHub checks include a size comparison to the main branch and a warning in case of a big jump in size.

<img src="https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format" alt="Bundlesize check on GitHub" sizes="(min-width: 769px) 769px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/8Mm1WPga9dbeIzGrv2fQ.jpg?auto=format&amp;w=1538 1538w" width="769" height="316" />

You can also use bundlesize with [Circle CI](https://circleci.com), [Wrecker](https://app.wercker.com) and [Drone](https://readme.drone.io).

To see it in action, here's an app bundled with [webpack](https://webpack.js.org/) that lets you [vote for your favorite kitty](https://glitch.com/edit/#!/scarce-pixie).

[<img src="https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format" alt="Cat voting app" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/DGSSFfpAMIaFqX8MwWss.png?auto=format&amp;w=1600 1600w" width="800" height="567" />](https://glitch.com/edit/#!/scarce-pixie)

Set the performance budget <a href="#set-the-performance-budget" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------

[This Glitch](https://glitch.com/edit/#!/scarce-pixie) already contains bundlesize.

-   Click **Remix to Edit** to make the project editable.

The main bundle of this app is in the public folder. To test its size, add the following section to the `package.json` file:

    "bundlesize": [
      {
        "path": "./public/*.bundle.js",
        "maxSize": "170 kB"
      }
    ]

You can also set [different thresholds for different files](https://github.com/siddharthkp/bundlesize#1-add-the-path-and-maxsize-in-your-packagejson). This is especially useful if you are [splitting a bundle](/reduce-javascript-payloads-with-code-splitting) in your application.

To keep the compressed JavaScript bundle size [under the recommended limit](/your-first-performance-budget#budget-for-quantity-based-metrics), set the performance budget to 170KB in the `maxSize` field.

Bundlesize supports [glob patterns](https://github.com/isaacs/node-glob) and the \* wildcard character in the file path will match all bundle names in the public folder.

By default, bundlesize tests gzipped sizes. You can use the [compression option](https://github.com/siddharthkp/bundlesize#1-add-the-path-and-maxsize-in-your-packagejson) to switch to [brotli](https://en.wikipedia.org/wiki/Brotli) compression or turn it off completely.

### Create a test script <a href="#create-a-test-script" class="w-headline-link">#</a>

Since Travis needs a test to run, add a test script to `package.json`:

    "scripts": {
      "start": "webpack && http-server -c-1",
      "test": "bundlesize"
    }

Set up continuous integration <a href="#set-up-continuous-integration" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------

### Integrate GitHub and Travis CI <a href="#integrate-github-and-travis-ci" class="w-headline-link">#</a>

First, create a new repository for this project on your GitHub account and initialize it with a `README.md`.

You'll need to [register an account on Travis](https://docs.travis-ci.com/user/tutorial) and activate GitHub Apps integration under the Settings section of your profile.

<img src="https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format" alt="GitHub Apps integration on Travis CI" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/kMgVmB5rzRJN3DlqP08R.png?auto=format&amp;w=1600 1600w" width="800" height="508" />

Once you have an account, go to **Settings** under your profile, click the **Sync account** button, and make sure your new repo is listed on Travis.

<img src="https://web-dev.imgix.net/image/admin/Zi9Oo5SCfM5P7IxejYd3.png?auto=format" alt="Travis CI Sync button" sizes="(min-width: 160px) 160px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Zi9Oo5SCfM5P7IxejYd3.png?auto=format&amp;w=160 160w, https://web-dev.imgix.net/image/admin/Zi9Oo5SCfM5P7IxejYd3.png?auto=format&amp;w=182 182w, https://web-dev.imgix.net/image/admin/Zi9Oo5SCfM5P7IxejYd3.png?auto=format&amp;w=208 208w, https://web-dev.imgix.net/image/admin/Zi9Oo5SCfM5P7IxejYd3.png?auto=format&amp;w=237 237w, https://web-dev.imgix.net/image/admin/Zi9Oo5SCfM5P7IxejYd3.png?auto=format&amp;w=270 270w, https://web-dev.imgix.net/image/admin/Zi9Oo5SCfM5P7IxejYd3.png?auto=format&amp;w=308 308w, https://web-dev.imgix.net/image/admin/Zi9Oo5SCfM5P7IxejYd3.png?auto=format&amp;w=320 320w" width="160" height="54" />

### Authorize bundlesize to post on pull requests <a href="#authorize-bundlesize-to-post-on-pull-requests" class="w-headline-link">#</a>

Bundlesize needs authorization to be able to post on pull requests, so [visit this link to get the bundlesize token](https://github.com/login/oauth/authorize?scope=repo%3Astatus&client_id=6756cb03a8d6528aca5a) that will be stored in the Travis configuration.

<img src="https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format" alt="bundlesize token" sizes="(min-width: 619px) 619px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/GkEMv2VCb25oC9lDSARQ.jpg?auto=format&amp;w=1238 1238w" width="619" height="330" />

In your project's Travis dashboard, go to **More options** &gt; **Settings** &gt; **Environment variables**.

<img src="https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format" alt="Adding environment variables on Travis CI" sizes="(min-width: 789px) 789px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/gol14FsIsYPyPWwIeYfI.png?auto=format&amp;w=1578 1578w" width="789" height="233" />

Add a new environment variable with the token as the value field and BUNDLESIZE\_GITHUB\_TOKEN as the name.

The last thing you need to kick-off continuous integration is a `.travis.yml` file, which tells Travis CI what to do. To speed things up, it is already included in the project and it specifies that the app is using NodeJS.

With this step, you're all set up and bundlesize will warn you if your JavaScript ever goes over the budget. Even when you start off great, over time, as you add new features, kilobytes can pile up. With automated performance budget monitoring, you can rest easy knowing that it won't go unnoticed.

Try it out <a href="#try-it-out" class="w-headline-link">#</a>
--------------------------------------------------------------

### Trigger your first bundlesize test <a href="#trigger-your-first-bundlesize-test" class="w-headline-link">#</a>

To see how the app stacks up against the performance budget, add the code to the GitHub repo that you created in step 3.

1.  On Glitch, click **Tools** &gt; **Git, Import, and Export** &gt; **Export to GitHub**.

2.  In the pop-up, enter your GitHub username and the name of the repo as `username/repo`. Glitch will export your app to a new branch named "glitch".

3.  Create a new pull request by clicking the **New pull request** button on the homepage of the repository.

You'll now see status checks in progress on the pull request page.

<img src="https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format" alt="Github checks in progress" sizes="(min-width: 774px) 774px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/SrdHGr9z5QY1vEfBwNIY.png?auto=format&amp;w=1548 1548w" width="774" height="351" />

It won't take long until all checks are done. Unfortunately, the cat voting app is a bit bloated and does not pass the performance budget check. The main bundle is 266 KB and the budget is 170 KB.

<img src="https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format" alt="Failed bundlesize check" sizes="(min-width: 774px) 774px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/Dt31nFkMvJjn1me6cir3.png?auto=format&amp;w=1548 1548w" width="774" height="347" />

### Optimize <a href="#optimize" class="w-headline-link">#</a>

Luckily, there are some easy performance wins you can make by [removing unused code](/remove-unused-code). There are two main imports in `src/index.js`:

    import firebase from "firebase";
    import * as moment from 'moment';

The app is using [Firebase Realtime Database](https://firebase.google.com/products/realtime-database/) to store the data, but it's importing the entire firebase package which consists of a lot more than just a database (auth, storage, messaging etc.).

Fix this by importing only the package that the app needs in the `src/index.js` file:

    import firebase from "firebase";
    import firebase from 'firebase/app';
    import 'firebase/database';

The `firebase/app` import, which sets up the API surface for each of the different services, is always required.

### Re-run test <a href="#re-run-test" class="w-headline-link">#</a>

Since the source file has been updated, you need to run webpack to build the new bundle file.

1.  Click the **Tools** button.

2.  Then click the **Console** button. This will open the console in another tab.

3.  In the console, type `webpack` and wait for it to finish the build.

4.  Export the code to GitHub from **Tools** &gt; **Git, Import, and Export** &gt; **Export to GitHub**.

5.  Go to the pull request page on GitHub and wait for all checks to finish.

<img src="https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format" alt="Passed bundlesize check" sizes="(min-width: 778px) 778px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/3aKOqNvvavQ32gl15PmU.png?auto=format&amp;w=1556 1556w" width="778" height="355" />

Success! The new size of the bundle is 125.5 KB and all the checks have passed. 🎉

Unlike Firebase, importing parts of the moment library cannot be done as easily, but it's worth a shot. Check out how you can further optimize the app in the [Remove unused code codelab](/codelab-remove-unused-code).

### Monitor <a href="#monitor" class="w-headline-link">#</a>

The app is now under the budget and all is well. Travis CI and bundlesize will keep monitoring the performance budget for you, making sure your app stays fast.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Feb 1, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/using-bundlesize-with-travis-ci/index.md)

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
