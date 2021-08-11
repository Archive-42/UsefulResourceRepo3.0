<a href="/" class="header-default__logo-link gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="header-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="header-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="header-default__link gc-analytics-event">Blog</a> <a href="/about/" class="header-default__link gc-analytics-event">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="drawer-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="drawer-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="drawer-default__link gc-analytics-event">Blog</a> <a href="/about/" class="drawer-default__link gc-analytics-event">About</a>

## <a href="#precaching-with-workbox" class="w-toc__header--link">Precaching with Workbox</a>

- [Why should you use Workbox?](#why-should-you-use-workbox)
- [Precache manifests](#precache-manifests)
- [Serving precached resources](#serving-precached-resources)
- [Efficient updates](#efficient-updates)
- [Updates to precached resources](#updates-to-precached-resources)
- [True "app store" install experience](#true-)
- [Which of your assets should be precached?](#which-of-your-assets-should-be-precached)

Share <a href="/newsletter/" class="w-actions__fab w-actions__fab--subscribe gc-analytics-event"><span>subscribe</span></a>

# Precaching with Workbox

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75 1x,     https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x,     https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x,     https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x,     https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

- <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
- <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
- <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

One feature of service workers is the ability to save files to the cache when the service worker is installing. This is referred to as "precaching". Precaching makes it possible to serve cached files to the browser without going to the network. Use precaching for critical assets that your site needs even when offline: main page, styles, fallback image and essential scripts.

## Why should you use Workbox? <a href="#why-should-you-use-workbox" class="w-headline-link">#</a>

Using Workbox for precaching is optional. You can write your own code to [precache critical assets when the service worker is installing](https://developers.google.com/web/ilt/pwa/caching-files-with-service-worker). The primary benefit of using Workbox is its out-of-the-box version control. You'll run into a lot less trouble updating precached assets using Workbox than if you had to manage the versioning and updating of these files on your own.

## Precache manifests <a href="#precache-manifests" class="w-headline-link">#</a>

Precaching is driven by a list of URLs and associated versioning information for each URL. Taken together, this information is known as a [**precache manifest**](https://developers.google.com/web/tools/workbox/modules/workbox-precaching#explanation_of_the_precache_list). The manifest is the "source of truth" for the state of everything meant to be in the precache for a given version of a web app. A precache manifest, in the format used by [Workbox](https://developers.google.com/web/tools/workbox/), looks something like:

    [{
      url: 'app.abcd1234.js'
    }, {
      url: 'offline.svg',
      revision: '7836745f'
    }, {
      url: 'index.html',
      revision: '518747aa'
    }]

When the service worker is installed, three cache entries are created in the Cache Storage, for each of the three listed URLs. The first asset has versioning information already included in its URL (`app` is the actual file name, and `.abcd1234` contains the versioning information, right before the file extension `.js`). Workbox's build tools can detect this and exclude a revision field. The other two assets do not include any versioning info in their URLs, so Workbox's build tools create a separate `revision` field, containing a hash of the local file's contents.

## Serving precached resources <a href="#serving-precached-resources" class="w-headline-link">#</a>

Adding assets to the cache is just one part of the precaching story—once the assets are cached, they need to respond to outgoing requests. That requires a `fetch` event listener in your service worker that can check which URLs have been precached, and return those cached responses reliably, bypassing the network in the process. Since the service worker checks the cache for responses (and uses those before the network), this is called a [**cache-first strategy**](https://developers.google.com/web/tools/workbox/modules/workbox-strategies#cache_first_cache_falling_back_to_network).

## Efficient updates <a href="#efficient-updates" class="w-headline-link">#</a>

A precache manifest provides an exact representation of the expected cache state; if a URL/revision combination in the manifest changes, a service worker _knows_ that the previous cached entry is no longer valid, and needs to be updated. It only takes a single network request, made automatically by the browser as part of the service worker [update check](https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle#updates), to determine which precached URLs need to be refreshed.

## Updates to precached resources <a href="#updates-to-precached-resources" class="w-headline-link">#</a>

As you release new versions of your web app over time, you need to keep previously precached URLs up to date, precache new assets, and delete outdated entries. As long as you continue generating a full precache manifest each time you rebuild your site, that manifest serves as the "source of truth" for your precache state at any point in time.

If there's an existing URL with a new revision field, or if any URLs have been added or dropped from the manifest, that's a sign to your service worker that updates need to be performed, as part of the [`install`](https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle#install_1) and [`activate`](https://developers.google.com/web/fundamentals/primers/service-workers/lifecycle#activate_1) event handlers. For instance, if you've made some changes to your site and rebuilt, your latest precache manifest might have undergone the following changes:

    [{
      url: 'app.ffaa4455.js'
    }, {
      url: 'offline.svg',
      revision: '7836745f'
    }, {
      url: 'index.html',
      revision: '518747aa'
    }]

Each of these changes tells your service worker that new requests need to be made to update previously cached entries (`'offline.svg'` and `'index.html'`) and cache new URLs (`'app.ffaa4455.js'`), as well as deletions to clean up URLs that are no longer used (`'app.abcd1234.js'`).

## True "app store" install experience <a href="#true-%22app-store%22-install-experience" class="w-headline-link">#</a>

Another benefit of precaching is that you can give your users an experience that would otherwise be difficult to achieve outside of an "app store" installation. Once a user visits any page on your web app for the first time, you can potentially precache _all_ of the URLs needed to display _any_ of your web app's views ahead of time, without having to wait until they visit each individual view.

When a user installs an app, they expect every part to display quickly, not just the views that they've gone to in the past. Precaching brings that same experience to web apps.

## Which of your assets should be precached? <a href="#which-of-your-assets-should-be-precached" class="w-headline-link">#</a>

Refer back to the [Identify what's being loaded](/identify-resources-via-network-panel/) guide to get a good picture of which URLs make the most sense to precache. The general rule is to precache any HTML, JavaScript, or CSS that's loaded early on and is crucial to displaying the basic structure of a given page.

It's preferable to avoid precaching media or other assets that are loaded later (unless crucial for your web app's functionality). Instead, use a [runtime caching strategy](/runtime-caching-with-workbox/) to ensure these assets are cached-as-you-go.

Always keep in mind that precaching involves using network bandwidth and storage on a user's device (just like installing an app from an app store does). It's up to you as the developer to precache judiciously, and avoid a bloated precache manifest.

Workbox's build tools help by telling you the number of items in the precache manifest as well as the total size of the precache payload.

Repeat visitors to your web app benefit in the long run from the upfront cost of precaching, since the ability it offers to avoid the network quickly pays for itself in saved bandwidth over time.

<span class="w-mr--sm"> Last updated: Nov 5, 2018 </span> [Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/precache-with-workbox/index.md)

<a href="/reliable" class="w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single gc-analytics-event">Return to all articles</a>

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
