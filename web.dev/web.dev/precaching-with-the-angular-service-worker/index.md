<img src="https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format" alt="Sparks flying off a metal grinder." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/r1NlrtasqQuMo11wlSva.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#precaching-with-the-angular-service-worker" class="w-toc__header--link">Precaching with the Angular service worker</a>

- [Dealing with limited connectivity](#dealing-with-limited-connectivity)
- [Introducing the Angular service worker](#introducing-the-angular-service-worker)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Precaching with the Angular service worker

Use the Angular service worker to make your app faster and more reliable on networks with poor connectivity.

Jul 2, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/angular" class="w-post-signpost__link">Angular</a>

[<img src="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Minko Gechev" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mgechev/)

<a href="/authors/mgechev/" class="w-author__name-link">Minko Gechev</a>

- <a href="https://twitter.com/mgechev" class="w-author__link">Twitter</a>
- <a href="https://github.com/mgechev" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@mgechev" class="w-author__link">Glitch</a>
- <a href="https://blog.mgechev.com/" class="w-author__link">Blog</a>

## Dealing with limited connectivity <a href="#dealing-with-limited-connectivity" class="w-headline-link">#</a>

When users have limited network access—or none at all—web app functionality can significantly degrade and often fails. Using a [service worker](https://developers.google.com/web/fundamentals/primers/service-workers/) to provide precaching lets you intercept network requests and deliver responses directly from a local cache instead of retrieving them from the network. Once your app's assets have been cached, this approach can really speed up an app and make it work when the user is offline.

This post walks through how to set up precaching in an Angular app. It assumes you're already familiar with precaching and service workers in general. If you need a refresher, check out the [Service workers and the Cache Storage API](/service-workers-cache-storage/) post.

_You can find the code for the current example [on GitHub](https://github.com/mgechev/service-worker-web-dev)._

## Introducing the Angular service worker <a href="#introducing-the-angular-service-worker" class="w-headline-link">#</a>

The Angular team offers a service worker module with precaching functionality that's well integrated with the framework and the [Angular command line interface (CLI)](https://cli.angular.io/).

To add the service worker, run this command in the CLI:

    ng add @angular/pwa

If you have multiple projects in the Angular CLI workspace, you can optionally specify a `--project` property with the project name you want to add the service worker to.

`@angular/service-worker` and `@angular/pwa` should now be installed in the app and should appear in `package.json`. The `ng-add` [schematic](https://angular.io/guide/schematics) also adds a file called `ngsw-config.json` to the project, which you can use to configure the service worker. (The file includes a default configuration that you'll customize a little later.)

Now build the project for production:

    ng build --prod

Inside the `dist/service-worker-web-dev` directory you'll find a file called `ngsw.json`. This file tells the Angular service worker how to cache the assets in the app. The file is generated during the build process based on the configuration (`ngsw-config.json`) and the assets produced at build time.

Now start an HTTP server in the directory containing your app's production assets, open the public URL, and check out its network requests in Chrome DevTools:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Network** tab.

Note that the network tab has a bunch of static assets directly downloaded in the background by the `ngsw-worker.js` script:

<img src="https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format" alt="Sample app" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/XL0o6p4YbQiBJmWW8Kw4.png?auto=format&amp;w=1600 1600w" width="800" height="599" />

This is the Angular service worker precaching the static assets specified in the generated `ngsw.json` manifest file.

One important asset is missing though: `nyan.png`. To precache this image you need to add a pattern that includes it to `ngsw-config.json`, which lives in the root of the workspace:

    {
      "$schema": "./node_modules/@angular/service-worker/config/schema.json",
      "index": "/index.html",
      "assetGroups": [
        {
          "name": "app",
          "installMode": "prefetch",
          "resources": {
          "files": [
            "/favicon.ico",
            "/index.html",
            "/*.css",
            "/*.js",
            "/assets/*.png"
            ]
          }
        },
        ...
    }

This change adds all PNG images in the `/assets` folder to the `app` resource asset group. Since the `installMode` for this asset group is set to `prefetch`, the service worker will precache all the specified assets—which now include PNG images.

Specifying other assets to be precached is just as straightforward: update the patterns in the `app` resource asset group.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

Using a service worker for precaching can improve the performance of your apps by saving assets to a local cache, which makes them more reliable on poor networks. To use precaching with Angular and the Angular CLI:

1.  Add the `@angular/pwa` package to your project.
2.  Control what the service worker caches by editing `ngsw-config.json`.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jul 2, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/angular/precaching-with-the-angular-service-worker/index.md)

<a href="/angular" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
