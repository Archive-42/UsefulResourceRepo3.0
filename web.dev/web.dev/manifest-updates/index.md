## <a href="#how-chrome-handles-updates-to-the-web-app-manifest" class="w-toc__header--link">How Chrome handles updates to the web app manifest</a>

- [Updates on desktop Chrome](#cr-desktop)
- [Which properties will trigger an update?](#cr-desktop-trigger)
- [What happens when the display field is updated?](#what-happens-when-the-display-field-is-updated)
- [Testing manifest updates](#cr-desktop-test)
- [References](#cr-desktop-ref)
- [Updates on Chrome for Android](#cr-android)
- [Which properties will trigger an update?](#cr-android-trigger)
- [Testing manifest updates](#cr-android-test)
- [References](#cr-android-ref)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# How Chrome handles updates to the web app manifest

What it takes to change icons, shortcuts, colors, and other metadata for your PWA

Oct 14, 2020 <span class="w-author__separator">•</span> Updated Apr 5, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/progressive-web-apps" class="w-post-signpost__link">Progressive Web Apps</a>

[<img src="https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Pete LePage" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/petelepage/)

<a href="/authors/petelepage/" class="w-author__name-link">Pete LePage</a>

- <a href="https://twitter.com/petele" class="w-author__link">Twitter</a>
- <a href="https://github.com/petele" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@petele" class="w-author__link">Glitch</a>
- <a href="https://petelepage.com" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/SeARmcA1EicLXagFnVOe0ou9cqK2/4KNPR11Y1YYxUi6ASIE1.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Adriana Jara" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/SeARmcA1EicLXagFnVOe0ou9cqK2/4KNPR11Y1YYxUi6ASIE1.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/SeARmcA1EicLXagFnVOe0ou9cqK2/4KNPR11Y1YYxUi6ASIE1.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/SeARmcA1EicLXagFnVOe0ou9cqK2/4KNPR11Y1YYxUi6ASIE1.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/SeARmcA1EicLXagFnVOe0ou9cqK2/4KNPR11Y1YYxUi6ASIE1.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/SeARmcA1EicLXagFnVOe0ou9cqK2/4KNPR11Y1YYxUi6ASIE1.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/ajara/)

<a href="/authors/ajara/" class="w-author__name-link">Adriana Jara</a>

- <a href="https://twitter.com/tropicadri" class="w-author__link">Twitter</a>
- <a href="https://github.com/tropicadri" class="w-author__link">GitHub</a>

We are currently gathering data on browsers other than Chrome. If you would like to help us gather this data or add content to this page, please leave a comment in [issue \#4038](https://github.com/GoogleChrome/web.dev/issues/4038).

When a PWA is installed, the browser uses information from the web app manifest for the app name, the icons the app should use, and the URL that should be opened when the app is launched. But what if you need to update app shortcuts or try a new theme color? When and how are those changes reflected in the browser?

**Caution**: Do not change the name or location of your web app manifest file, doing so may prevent the browser from updating your PWA.

In most cases, changes should be reflected within a day or two of the PWA being launched, after the manifest has been updated.

## Updates on desktop Chrome <a href="#cr-desktop" class="w-headline-link">#</a>

When the PWA is launched, or opened in a browser tab, Chrome determines the last time the local manifest was checked for changes. If the manifest hasn't been checked since the browser last started, or it hasn't been checked in the last 24 hours, Chrome will make a network request for the manifest, then compare it against the local copy.

If select properties in the manifest have changed (see list below), Chrome queues the new manifest, and after all windows have been closed, installs it. Once installed, all fields from the new manifest (except `name`, `short_name`, `start_url` and `icons`) are updated.

### Which properties will trigger an update? <a href="#cr-desktop-trigger" class="w-headline-link">#</a>

- `display` (see below)
- `scope`
- `shortcuts`
- `theme_color`

**Caution**: Changes to `name`, `short_name`, `icons` and `start_url` are **not** currently supported on desktop Chrome, though work is underway to support them.

### What happens when the `display` field is updated? <a href="#what-happens-when-the-display-field-is-updated" class="w-headline-link">#</a>

If you update your app's display mode from `browser` to `standalone` your existing users will not have their apps open in a window after updating. There are two display settings for a web app, the one from the manifest (that you control) and a window/browser tab setting controlled by the user. The user preference is always respected.

### Testing manifest updates <a href="#cr-desktop-test" class="w-headline-link">#</a>

The `about://internals/web-app` page (available in Chrome 85 or later), includes detailed information about all of the PWAs installed on the device, and can help you understand when the manifest was last updated, how often it's updated, and more.

To manually force Chrome to check for an updated manifest, restart Chrome (use `about://restart`), this resets the timer so that Chrome will check for an updated manifest when the PWA is next launched. Then launch the PWA. After closing the PWA, it should be updated with the new manifest properties.

### References <a href="#cr-desktop-ref" class="w-headline-link">#</a>

- [Updatable Web Manifest Fields](https://docs.google.com/document/d/1twU_yAoTDp4seZMmqrDzJFQtrM7Z60jXHkXjMIO2VpM/preview)

## Updates on Chrome for Android <a href="#cr-android" class="w-headline-link">#</a>

When the PWA is launched, Chrome determines the last time the local manifest was checked for changes. If the manifest hasn't been checked in the last 24 hours, Chrome will schedule a network request for the manifest, then compare it against the local copy.

If select properties in the manifest have changed (see list below), Chrome queues the new manifest, and after all windows of the PWA have been closed, the device is plugged in, and connected to WiFi, Chrome requests an updated WebAPK from the server. Once updated, all fields from the new manifest are used.

### Which properties will trigger an update? <a href="#cr-android-trigger" class="w-headline-link">#</a>

- `background_color`
- `display`
- `orientation`
- `scope`
- `shortcuts`
- `start_url`
- `theme_color`
- `web_share_target`

If Chrome is unable to get an updated manifest from the server, it may increase the time between checks to 30 days.

**Caution**: Changes to `name`, `short_name` and `icons` are **not** currently supported on Android Chrome, though work is underway to support them.

### Testing manifest updates <a href="#cr-android-test" class="w-headline-link">#</a>

The `about://webapks` page includes detailed information about all of the PWAs installed on the device, and can tell you when the manifest was last updated, how often it's updated, and more.

To manually schedule an update to the manifest, overriding the timer and local manifest do the following:

1.  Plug in the device and ensure it's connected to WiFi.
2.  Use the Android task manager to shut down the PWA, then use the App panel in Android settings to force stop the PWA.
3.  In Chrome, open `about://webapks` and click the "Update" button for the PWA. "Update Status" should change to "Pending".
4.  Launch the PWA, and verify it's loaded properly.
5.  Use the Android task manager to shut down the PWA, then use the App panel in Android settings to force stop the PWA.

The PWA usually updates within a few minutes, once the update has completed, "Update Status" should change to "Successful"

### References <a href="#cr-android-ref" class="w-headline-link">#</a>

- [`UpdateReason` enum](https://cs.chromium.org/chromium/src/chrome/browser/android/webapk/webapk.proto?l=35) for Chrome on Android

<a href="/tags/progressive-web-apps/" class="w-chip">Progressive Web Apps</a>

<span class="w-mr--sm">Last updated: Apr 5, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/progressive-web-apps/manifest-updates/index.md)

<a href="/progressive-web-apps" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
