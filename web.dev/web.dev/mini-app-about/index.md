<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#what-are-mini-apps" class="w-toc__header--link">What are mini apps?</a>
---------------------------------------------------------------------------------

-   [Building blocks and compatibility](#building-blocks-and-compatibility)
-   [Discovery](#discovery)
-   [The user experience](#the-user-experience)
-   [UI paradigms](#ui-paradigms)
-   [Serving](#serving)
-   [Caching, updates, and deep-linking](#caching-updates-and-deep-linking)
-   [Security and permissions](#security-and-permissions)
-   [Access to powerful features](#access-to-powerful-features)
-   [Access to cloud services](#access-to-cloud-services)
-   [Identity, payment, social graph](#identity-payment-social-graph)
-   [Acknowledgements](#acknowledgements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

What are mini apps?
===================

Mar 3, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/mini-apps" class="w-post-signpost__link">Mini apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

-   <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
-   <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
-   <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

This post is part of an article collection where each article builds upon previous articles. If you just landed here, you may want to start reading from the [beginning](/mini-app-super-apps/).

Building blocks and compatibility <a href="#building-blocks-and-compatibility" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

Mini apps are small (commonly less than 4MB) apps that require a [super app](/mini-app-super-apps/#for-mini-apps-you-need-super-apps) to run. What they have in common, independent of the super app, is that they are built with ("dialects" of) the web technologies HTML, CSS, and JavaScript. The runtime of a mini app is a [WebView](https://research.google/pubs/pub46739/) in the super app, not the underlying operating system, which makes mini apps cross platform. The same mini app can run in the same super app, no matter if the super app runs on Android, iOS, or another OS. However, not all mini apps can run in all super apps, more on this [later](/mini-app-standardization/).

Discovery <a href="#discovery" class="w-headline-link">#</a>
------------------------------------------------------------

Mini apps are often discovered *ad-hoc* via branded 2D barcodes, which solves an important offline-to-online challenge, for example, getting from a physical restaurant menu to a payment mini app, or from a physical e-scooter to a rental mini app. The image below shows an example of such a branded 2D barcode for [WeChat's demo mini app](https://github.com/wechat-miniprogram/miniprogram-demo). When the code is scanned with the WeChat super app, the mini app launches directly. Other super apps will typically not be able to recognize the barcode.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/SOisfOqKQWr0GZZvUaqn.jpg?auto=format" alt="Scanning this 2d barcode with the WeChat app launches a demo mini app." sizes="(min-width: 250px) 250px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/SOisfOqKQWr0GZZvUaqn.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/SOisfOqKQWr0GZZvUaqn.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/SOisfOqKQWr0GZZvUaqn.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/SOisfOqKQWr0GZZvUaqn.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/SOisfOqKQWr0GZZvUaqn.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/SOisfOqKQWr0GZZvUaqn.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/SOisfOqKQWr0GZZvUaqn.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/SOisfOqKQWr0GZZvUaqn.jpg?auto=format&amp;w=500 500w" width="250" height="250" /><figcaption>Scanning this 2d barcode with the WeChat app launches a demo mini app.</figcaption></figure>Mini apps can also be discovered through regular in-app search in the super app, be shared in chat messages, or be part of a news item in a news feed. Some super apps have the notion of verified accounts that can contain mini apps in their profiles. Mini apps can be highlighted when they are physically geographically close, like the mini app of a business in front of which the user stands, or virtually close, like when the user gets directions on a map shown in the super app. Frequently used mini apps are available in an app drawer that in many super apps can be accessed through a swipe down gesture or through a special section in the super app menu.

The user experience <a href="#the-user-experience" class="w-headline-link">#</a>
--------------------------------------------------------------------------------

All super apps have more or less the same user interface for mini apps. A themeable top bar with the mini app's name, and, in the upper corner of the screen, a close button on the far right preceded by an action menu that provides access to common features like sharing the app, adding it to a favorites list or the home screen, reporting abusive apps, providing feedback, and settings. The screenshot below shows a shopping mini app running in the context of the Alipay super app with the action menu opened.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format" alt="Opened action menu of a shopping mini app running in the Alipay super app." sizes="(min-width: 300px) 300px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PkjzF8AyxDVIAMZmhVrr.jpg?auto=format&amp;w=600 600w" width="300" height="649" /><figcaption>Opened action menu of a shopping mini app running in the Alipay super app.</figcaption></figure>UI paradigms <a href="#ui-paradigms" class="w-headline-link">#</a>
------------------------------------------------------------------

Usually there is a bottom tab bar for the mini app's main navigation. Most [super app providers offer components](/mini-app-components/) that help developers quickly implement common UI paradigms, such as carousels, accordions, progress bars, spinners, switches, maps, and so on. This also helps make the user experience between different mini apps consistent, which is encouraged by [WeChat's Mini Program Design Guidelines](https://developers.weixin.qq.com/miniprogram/en/design/). This is similar to what Apple incentivizes with its [Apple Human Interface Guidelines](https://developer.apple.com/design/human-interface-guidelines/ios/overview/themes/), and Google with its [Design for Android](https://developer.android.com/design) recommendations.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format" alt="Douyin&#39;s slider (carousel) component with various options." sizes="(min-width: 300px) 300px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/nFVCU3HqKERzl7Lops6Q.png?auto=format&amp;w=600 600w" width="300" height="617" /><figcaption>Douyin's slider (carousel) component with various options.</figcaption></figure>Serving <a href="#serving" class="w-headline-link">#</a>
--------------------------------------------------------

Rather than being served piece by piece as separate resources, mini apps are served as encrypted packaged apps, that is, as archives that contain all resources in just one file. Unlike regular web apps, they are also not served from the particular origin of the mini app creator, but from the super app provider directly. They can still access APIs from the servers of the mini app creator, but the core resources (commonly referred to as the app shell), must be served from the super app provider. Mini apps have to declare the origins they request additional data from.

Caching, updates, and deep-linking <a href="#caching-updates-and-deep-linking" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

Mini apps are kept in the cache of the super app, so the next time the user launches a cached mini app, it loads almost instantly. If there is an update, a new app package is loaded. The version number can be part of the launch URI (see [Discovery](/mini-app-about/#discovery)), so the super app knows early on if the locally cached version is still current. The launch URI also optionally contains the desired page of the mini app, so deep-linking into specific pages of mini apps is possible. Via a sitemap, mini apps can declare which of their pages should be indexable by the super app provider's mini app crawler.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format" alt="Mini apps are cached as encrypted packaged apps." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ZKLNvNnm3Rr6aBmYbons.png?auto=format&amp;w=1600 1600w" width="800" height="465" /><figcaption>Mini apps are cached as encrypted packaged apps.</figcaption></figure>Security and permissions <a href="#security-and-permissions" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------

Mini apps are reviewed by the super app provider, which means users perceive them as more secure than web apps. They need to declare their potentially required permissions beforehand in a manifest or mini app configuration file, which, for some providers, also requires explanations for why each permission is needed. Mini apps can of course still lie, but they would have a hard time justifying why they are, for example, [trying to access motion sensors](https://twitter.com/search?q=why%20website%20access%20%22motion%20sensors%22%20&src=typed_query&f=live) without a reason that is apparent to the user. The incentive to fingerprint the user is notably a lot lower compared to the web, since the user is typically already logged in to the super app anyway (see [Identity, payement, and social graph](/mini-app-about/#identity-payment-social-graph)).

Whenever a mini app performs an operation that requires a special permission, a prompt is shown to the user that, if enforced by the platform, also includes the usage justification, as stated by the developer. The screenshot below shows the [Douyin demo mini app](https://microapp.bytedance.com/docs/zh-CN/mini-app/introduction/plug-in/example/) as it asks the user for permission to share their location. In some super apps, there is also an imperative API that mini apps can leverage to request permissions without immediately using them, or to only check the status of a permission. This may even include an API to open the central super app permission settings, which corresponds to [Chrome's *Site Settings*](about://settings/content/siteDetails?site=https%3A%2F%2Fexample.com%2F). Mini apps also have to declare beforehand the origins of all servers that they potentially will request data from.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format" alt="The Douyin demo mini app asking for the geolocation permission." sizes="(min-width: 300px) 300px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8To8DiUqnP4qqFfpPNqk.png?auto=format&amp;w=600 600w" width="300" height="617" /><figcaption>The Douyin demo mini app asking for the geolocation permission.</figcaption></figure>Access to powerful features <a href="#access-to-powerful-features" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------

The hosting super app offers access to powerful APIs via a JavaScript bridge that gets injected into the WebView offered by the super app (see [Building blocks and compatibility](/mini-app-about/#building-blocks-and-compatibility)). This JavaScript bridge provides hooks into the operating system's APIs. For example, a mini app JavaScript function like `getConnectedWifi()`—the capability of a mini app to obtain the name of the currently active Wi-Fi network—under the hood is facilitated through Android's [`getConnectionInfo()`](https://developer.android.com/reference/android/net/wifi/WifiManager#getConnectionInfo()) API or iOS' [`CNCopyCurrentNetworkInfo()`](https://developer.apple.com/documentation/systemconfiguration/1614126-cncopycurrentnetworkinfo) API. Other examples of powerful device APIs exposed in common super apps are Bluetooth, NFC, iBeacon, GPS, system clipboard, orientation sensors, battery information, calendar access, phonebook access, screen brightness control, file system access, vibration hardware for physical feedback, camera and microphone access, screen recording and screenshot creation, network status, UDP sockets, barcode scanning, device memory information, and more.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format" alt="The WeChat demo mini app setting the device&#39;s screen brightness to the maximum." sizes="(min-width: 300px) 300px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNEKyoLVeq3IUKGXEZEZ.png?auto=format&amp;w=600 600w" width="300" height="649" /><figcaption>The WeChat demo mini app setting the device's screen brightness to the maximum.</figcaption></figure>Access to cloud services <a href="#access-to-cloud-services" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------

Many super apps also provide "serverless" access to cloud services of the super app provider that, apart from raw cloud computing and cloud storage, frequently also include higher-level tasks like text translation, object detection or content classification in images, speech recognition, or other Machine Learning tasks. Mini apps can be monetized with ads, which are commonly made available by super apps providers. Super app platforms usually also provide cloud analytics data, so mini app developers can better understand how users interact with their apps.

Identity, payment, social graph <a href="#identity-payment-social-graph" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------

A very important feature of mini apps is the identity and social graph information that is shared from the super app. Super apps like Douyin or WeChat started as social networking sites in the broadest sense, where users have a (sometimes even government-verified) identity, a friend or follower network, and frequently also payment data stored. For example, a shopping mini app can (or sometimes even must) process any payments directly through the payment APIs of the super app and, upon user consent, can obtain user data like their shipping address, phone number, and full name, all without ever having to force the user to painfully fill out forms. Below, you can see the Walmart mini app running in WeChat, opened for the very first time, greeting me with a familiar face.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format" alt="The Walmart mini app with a personalized &quot;Me&quot; view on the first visit." sizes="(min-width: 300px) 300px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HzPx6ZSqQWvsUDT04ex2.png?auto=format&amp;w=600 600w" width="300" height="649" /><figcaption>The Walmart mini app with a personalized "Me" view on the first visit.</figcaption></figure>Mini apps can get highly popular by letting people share their achievements like highscores in a game and challenge their contacts through status updates. The mini app is then only a tap away, so users can enter into competition without any friction and the mini app thereby grow its reach.

**Success**: In the next chapter, you will learn [what sets mini apps apart from H5 apps and QuickApp](/mini-app-what-are-h5-and-quickapp).

Acknowledgements <a href="#acknowledgements" class="w-headline-link">#</a>
--------------------------------------------------------------------------

This article was reviewed by [Joe Medley](https://github.com/jpmedley), [Kayce Basques](https://github.com/kaycebasques), [Milica Mihajlija](https://github.com/mihajlija), [Alan Kent](https://github.com/alankent), and Keith Gu.

<a href="/tags/mini-apps/" class="w-chip">Mini apps</a>

<span class="w-mr--sm">Last updated: Mar 3, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/mini-apps/mini-app-about/index.md)

<a href="/mini-apps" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
