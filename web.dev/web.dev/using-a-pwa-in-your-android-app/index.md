<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#using-a-pwa-in-your-android-app" class="w-toc__header--link">Using a PWA in your Android app</a>
----------------------------------------------------------------------------------------------------------

-   [Start a PWA in an Android app](#start-a-pwa-in-an-android-app)
-   [Existing solutions were limited](#existing-solutions-were-limited)
-   [Trusted Web Activity is a new container for Web apps on Android](#trusted-web-activity-is-a-new-container-for-web-apps-on-android)
-   [Quality Criteria](#quality-criteria)
-   [Tooling](#tooling)
-   [Bubblewrap](#bubblewrap)
-   [PWABuilder](#pwabuilder)
-   [Verifying ownership of the PWA in the Android app](#verifying-ownership-of-the-pwa-in-the-android-app)
-   [Where to go next](#where-to-go-next)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Using a PWA in your Android app
===============================

Mar 19, 2020 <span class="w-author__separator">•</span> Updated Apr 30, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/progressive-web-apps" class="w-post-signpost__link">Progressive Web Apps</a>

[<img src="https://web-dev.imgix.net/image/admin/XVGMhdOgHJhch3EBcw89.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="André Cipriani Bandarra" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/XVGMhdOgHJhch3EBcw89.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/XVGMhdOgHJhch3EBcw89.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/XVGMhdOgHJhch3EBcw89.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/XVGMhdOgHJhch3EBcw89.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/XVGMhdOgHJhch3EBcw89.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/andreban/)

<a href="/authors/andreban/" class="w-author__name-link">André Cipriani Bandarra</a>

-   <a href="https://twitter.com/andreban" class="w-author__link">Twitter</a>
-   <a href="https://github.com/andreban" class="w-author__link">GitHub</a>
-   <a href="https://bandarra.me/" class="w-author__link">Blog</a>

Start a PWA in an Android app <a href="#start-a-pwa-in-an-android-app" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------

[Progressive Web Apps](/progressive-web-apps/) (PWA) are web applications that use app-like features to create high quality experiences that are fast, reliable and engaging.

The web has incredible reach and offers powerful ways for users to discover new experiences. But users are also used to searching for applications in their operating system store. Those users are, in many cases, already familiar with the brand or service they're seeking and have a high level of intentionality that results in higher than average engagement metrics.

The Play Store is a store for Android apps, and developers often want to open their Progressive Web Apps from their Android apps.

Trusted Web Activity is an open standard that allows browsers to provide a fully web platform compatible container that renders PWAs inside an Android app. The feature is available in [Chrome](https://play.google.com/store/apps/details?id=com.android.chrome), and in development in [Firefox Nightly](https://play.google.com/store/apps/details?id=org.mozilla.fenix).

### Existing solutions were limited <a href="#existing-solutions-were-limited" class="w-headline-link">#</a>

It has always been possible to include web experiences in an Android app, using technologies like the [Android WebView](https://developer.android.com/reference/android/webkit/WebView) or frameworks like [Cordova](https://cordova.apache.org/).

The limitation with Android WebView is that it's not intended as a browser replacement. The Android WebView is a developer tool for using web UI in an Android app and it doesn't provide complete access to modern web platform features such as [contact picker](/contact-picker/), or [filesystem](/file-system-access/), [among others](/fugu-status/).

Cordova was designed to augment the shortcomings of WebView, but the APIs are then limited to the Cordova environment. That means you need to maintain an additional codebase for using Cordova APIs for your Android app, separate from your PWA on the open web.

In addition, feature discoverability often doesn't always work as expected and compatibility issues between Android versions and OEMs can also be a problem. When using one of those solutions, developers need additional quality assurance processes and incur an extra development cost to detect and create workarounds.

### Trusted Web Activity is a new container for Web apps on Android <a href="#trusted-web-activity-is-a-new-container-for-web-apps-on-android" class="w-headline-link">#</a>

Developers can now use a [Trusted Web Activity](https://developers.google.com/web/updates/2019/02/using-twa) as a container to include a PWA as a launch activity for an Android app. The technology leverages the browser to render the PWA in full screen, ensuring the Trusted Web Activity has the same compatibility with the Web Platform features and APIs that the underlying browser does. There are also open source utilities to make implementing an Android app using a Trusted Web Activity even easier.

Another advantage not available in other solutions is that the container shares storage with the browser. Login states and users preferences are shared seamlessly across experiences.

#### Browser Compatibility <a href="#browser-compatibility" class="w-headline-link">#</a>

The feature has been available in Chrome since version 75, with Firefox implementing it in their nightly version.

### Quality Criteria <a href="#quality-criteria" class="w-headline-link">#</a>

Web developers should use a Trusted Web Activity when they want to include web content in an Android app.

Web content in a Trusted Web Activity must meet the PWA installability criteria.

Additionally, to match the behavior users expect from Android applications, [Chrome 86 introduced a change](https://blog.chromium.org/2020/06/changes-to-quality-criteria-for-pwas.html) where failing to handle the following scenarios is considered a crash:

-   Failure to verify digital asset links at application launch.
-   Failure to return HTTP 200 for an offline network resource request.
-   A navigation request returning an HTTP 404 or 5xx error".

When one of those scenarios happens in the Trusted Web Activity, it causes a user visible crash of the Android application. Check out the [guidance](https://developer.chrome.com/docs/android/trusted-web-activity/whats-new/#updates-to-the-quality-criteria) on handling those scenarios in your service worker.

The application must also meet additional Android-specific criteria such as [policy compliance](https://play.google.com/about/developer-content-policy/).

**Caution**: When your app is designed primarily for children under 13, additional [Play Family policies](https://play.google.com/about/families/) apply, which may be incompatible with using Trusted Web Activity.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format" alt="The PWA badge in Lighthouse shows if your PWA passes the installability criteria." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Z70W3aCI8ropKpMXHcz.png?auto=format&amp;w=1600 1600w" width="800" height="141" /><figcaption>The PWA badge in Lighthouse shows if your PWA passes the installability criteria.</figcaption></figure>Tooling <a href="#tooling" class="w-headline-link">#</a>
--------------------------------------------------------

Web developers who want to take advantage of Trusted Web Activity don't need to learn new technologies or APIs to transform their PWA into an Android Application. Together, Bubblewrap and PWABuilder provide developer tooling in the form of a library, Command Line Interface (CLI) and Graphical User Interface (GUI).

### Bubblewrap <a href="#bubblewrap" class="w-headline-link">#</a>

The [Bubblewrap](https://github.com/GoogleChromeLabs/bubblewrap) project generates Android apps in the form of a NodeJS library and a Command Line Interface (CLI).

Bootstrapping a new project is achieved by running the tool and passing the URL of the Web Manifest:

    npx @bubblewrap/cli init --manifest=https://pwa-directory.appspot.com/manifest.json

The tool can also build the project, and running the command below will output an Android application ready to be uploaded to the Play Store:

    npx @bubblewrap/cli build

After running this command, a file called `app-release-signed.apk` will be available in the root directory for the project. This is the file that will be [uploaded to the Play Store](https://support.google.com/googleplay/android-developer/answer/3131213?hl=en-GB).

### PWABuilder <a href="#pwabuilder" class="w-headline-link">#</a>

[PWABuilder](https://pwabuilder.com/) helps developers transform existing websites into Progressive Web Apps. It also integrates with Bubblewrap to provide a GUI interface to wrap those PWAs into an Android app. The PWABuilder team has put together a [great blog post](https://www.davrous.com/2020/02/07/publishing-your-pwa-in-the-play-store-in-a-couple-of-minutes-using-pwa-builder/) on how to generate an Android application using the tool.

Verifying ownership of the PWA in the Android app <a href="#verifying-ownership-of-the-pwa-in-the-android-app" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------

A developer building a great Progressive Web App wouldn't want another developer to build an Android app with it without their permission. To ensure this doesn't happen, the Android application must be paired with the Progressive Web App using a tool called [Digital Asset Links](https://developers.google.com/digital-asset-links/v1/getting-started).

Bubblewrap and PWABuilder take care of the necessary configuration on the Android application, but a last step remains, which is adding the `assetlinks.json` file to the PWA.

To generate this file, developers need the SHA-256 signature of the key used to sign the APK that is being downloaded by the users.

The key can be generated in multiple ways, and the easiest way to find which key that signed the APK being served to end users is to download it from the Play Store itself.

To avoid showing a broken application to users, deploy the application to a [closed test channel](https://support.google.com/googleplay/android-developer/answer/3131213?hl=en-GB), install it into a test device then use [Peter's Asset Link Tool](https://play.google.com/store/apps/details?id=dev.conn.assetlinkstool) to generate the correct `assetlinks.json` file for the app. Make the generated `assetlinks.json` file available at `/.well-known/assetlinks.json`, in the domain being validated.

Where to go next <a href="#where-to-go-next" class="w-headline-link">#</a>
--------------------------------------------------------------------------

A Progressive Web App is a high quality web experience. Trusted Web Activity is a new way to open those high quality experiences from an Android app when they meet the minimum quality criteria.

If you are getting started with Progressive Web Apps, read [our guidance on how to build a great PWA](/progressive-web-apps/). For developers who already have a PWA, use [Lighthouse](https://developers.google.com/web/tools/lighthouse) to verify if it meets the quality criteria.

Then, use [Bubblewrap](https://github.com/GoogleChromeLabs/bubblewrap) or [PWABuilder](https://pwabuilder.com/) to generate the Android application, [upload the application to a closed test channel on the Play Store](https://support.google.com/googleplay/android-developer/answer/3131213?hl=en-GB) and pair it with the PWA using [Peter's Asset Link Tool](https://play.google.com/store/apps/details?id=dev.conn.assetlinkstool).

Finally, move your application from the closed test channel to production!

<a href="/tags/progressive-web-apps/" class="w-chip">Progressive Web Apps</a>

<span class="w-mr--sm">Last updated: Apr 30, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/progressive-web-apps/using-a-pwa-in-your-android-app/index.md)

<a href="/progressive-web-apps" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
