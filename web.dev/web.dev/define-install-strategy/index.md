





## <a href="#how-to-define-your-install-strategy" class="w-toc__header--link">How to define your install strategy</a>

- [Why make your web app installable?](#why-make-your-web-app-installable)
- [Promoting the installing of your PWA through the browser](#promoting-the-installing-of-your-pwa-through-the-browser)
- [PWA as primary installable experience](#pwa-as-primary-installable-experience)
- [Prevent your PWA from cannibalizing your platform-specific app install rate](#prevent-your-pwa-from-cannibalizing-your-platform-specific-app-install-rate)
- [Promoting the installing of your PWA through an app store](#promoting-the-installing-of-your-pwa-through-an-app-store)
- [Promoting Lightweight Apps](#promoting-lightweight-apps)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# How to define your install strategy

May 12, 2020 <span class="w-author__separator">•</span> Updated Aug 20, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/progressive-web-apps" class="w-post-signpost__link">Progressive Web Apps</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

- <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
- <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

[<img src="https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Pete LePage" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/petelepage/)

<a href="/authors/petelepage/" class="w-author__name-link">Pete LePage</a>

- <a href="https://twitter.com/petele" class="w-author__link">Twitter</a>
- <a href="https://github.com/petele" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@petele" class="w-author__link">Glitch</a>
- <a href="https://petelepage.com" class="w-author__link">Blog</a>

In the past, app installs were only possible in the context of platform-specific applications. Today, modern web apps offer installable experiences that provide the same level of integration and reliability as platform-specific apps.

You can achieve this in different ways:

- Installing the PWA [from the browser](/customize-install/).
- Installing the PWA [from the app store](https://developers.google.com/web/android/trusted-web-activity).

Having different distribution channels is a powerful way of reaching a broad number of users, but choosing the right strategy to promote them can be challenging.

This guide explores best practices for combining different installation offerings to increase installation rates and avoid platform competition and cannibalization. The installation offerings covered include PWAs installed from both the browser and the App Store, as well as platform-specific apps.

## Why make your web app installable? <a href="#why-make-your-web-app-installable" class="w-headline-link">#</a>

Installed Progressive Web Apps run in a standalone window instead of a browser tab. They're launchable from the user's home screen, dock, taskbar, or shelf. It's possible to search for them on a device and jump between them with the app switcher, making them feel like part of the device they're installed on.

But having both an installable web app and a platform-specific app can be confusing for users. For some users platform-specific apps may be the best choice, but for others they can present some drawbacks:

- **Storage constraints:** Installing a new app might mean deleting others, or cleaning up space, by removing valuable content. This is especially disadvantageous for users on low-end devices.
- **Available bandwidth:** Downloading an app can be a costly and slow process, even more for users on slow connections and expensive data plans.
- **Friction:** Leaving a website and moving to a store to download an app creates additional friction and delays a user action that could be performed directly in the web.
- **Update cycle:** Making changes in platform-specific apps might require going through an app review process, which can slow down changes and experiments (e.g. A/B tests).

In some cases, the percentage of users that won't download your platform-specific app might be large, for example: those that think that they won't use the app very often, or can't justify spending several megabytes of storage or data. You can determine the size of this segment in several ways, for example by using an analytics setup to track the percentage of "mobile web only" users.

If the size of this segment is considerable, that's a good indication that you need to provide alternative ways of installing your experiences.

## Promoting the installing of your PWA through the browser <a href="#promoting-the-installing-of-your-pwa-through-the-browser" class="w-headline-link">#</a>

If you have a high quality PWA, it may be better to promote its installation over your platform-specific app. For example, if the platform-specific app is missing functionality offered by your PWA, or if it hasn't been updated in a while. It can also be helpful to promote installation of your PWA if the platform-specific app wasn't optimized for bigger screens, such as on Chrome OS.

For some apps, driving platform-specific app installations is a key part of the business model, in that case, it makes business sense to show a platform-specific app install promotion. But, some users might be more comfortable staying on the web. If that segment can be identified, the PWA prompt can be shown only to them (what we call "PWA as fallback").

In this section we'll explore different ways of maximizing the installation rate of PWAs installed through the browser.

### PWA as primary installable experience <a href="#pwa-as-primary-installable-experience" class="w-headline-link">#</a>

Once a PWA meets the [installability criteria](/install-criteria/), most browsers will show an indication that the PWA is installable. For example, Desktop Chrome will show an installable icon in the address bar, and on mobile, it will show a mini-infobar:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format" alt="The mini-infobar" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1VOvbQjeenZOBAmzjVN5.png?auto=format&amp;w=1600 1600w" width="800" height="417" /><figcaption>The mini-infobar</figcaption></figure>While that may be enough for some experiences, if your goal is to drive installations of your PWA, we highly recommend you listen for the [`BeforeInstallPromptEvent`](https://developer.mozilla.org/en-US/docs/Web/API/BeforeInstallPromptEvent), and follow the [patterns for promoting the installation](/promote-install/) of your PWA.

## Prevent your PWA from cannibalizing your platform-specific app install rate <a href="#prevent-your-pwa-from-cannibalizing-your-platform-specific-app-install-rate" class="w-headline-link">#</a>

In some cases, you may choose to promote the installation of your platform-specific app over your PWA, but in this case, we still recommend you provide a mechanism to allow users to install your PWA. This fallback option makes it possible for users who can't, or don't want to install your platform-specific app to get a similar, installed experience.

The first step to implement this strategy is to define a heuristic for when you'll show the user an install promotion for your PWA, for example:

**"A PWA user is a user that has seen the platform-specific app install prompt and not installed the platform-specific app. They have returned to the site at least five times, or they have clicked the app banner, but have continued using the website instead."**

Then, the heuristic can be implemented in the following way:

1.  Show the platform-specific app install banner.
2.  If a user dismisses the banner, set a cookie with that information (e.g. `document.cookie = "app-install-banner=dismissed"`).
3.  Use another cookie to track the number of user visits to the site (e.g. `document.cookie = "user-visits=1"`).
4.  Write a function, such as `isPWAUser()`, that uses the information previously stored in the cookies along with the [`getInstalledRelatedApps()`](/get-installed-related-apps/) API to determine if a user is considered a "PWA user".
5.  At the moment when the user performs a meaningful action, call `isPWAUser()`. If the function returns true and the PWA install prompt was saved previously, you can show the PWA install button.

## Promoting the installing of your PWA through an app store <a href="#promoting-the-installing-of-your-pwa-through-an-app-store" class="w-headline-link">#</a>

Apps that are available in App stores can be built with different technologies, including PWA techniques. In [Blending PWA into native environments](https://youtu.be/V7YX4cZ_Cto) you can find a summary of the technologies that can be used to that end.

In this section we'll classify apps in the store in two groups:

- **Platform-specific apps:** These apps are mostly built with platform-specific code. Their size depends on the platform, but it's usually above 10MB in Android, and 30MB in iOS. You might want to promote your platform-specific app if you don't have a PWA, or if the platform-specific app presents a more complete feature set.
- **Lightweight apps:** These apps can be built with platform-specific code as well, but they are commonly built with web technology, packaged in a platform-specific wrapper. Full PWAs can be uploaded to the stores as well. Some companies opt to provide these as "lite" experiences, and others have used this approach for their flagship (core) apps as well.

### Promoting Lightweight Apps <a href="#promoting-lightweight-apps" class="w-headline-link">#</a>

According to a [Google Play study](https://medium.com/googleplaydev/shrinking-apks-growing-installs-5d3fcba23ce2), for every 6 MB increase to an APK's size, the install conversion rate decreases by 1%. This means that the download completion rate of an app of 10 MB could be approximately **30% higher than an app of 100 MB!**

To address this, some companies are leveraging their PWA to provide a lightweight version of their app in the Play Store using Trusted Web Activities. [Trusted Web Activities](https://developers.google.com/web/android/trusted-web-activity) make it possible to deliver your PWA in the Play Store, and because it's built using the web, the app size is usually only a few megabytes.

Oyo, one of India's largest hospitality companies, built a [Lite version of their app](/oyo-lite-twa/), and made it available in the Play Store using TWA. It's only 850 KB, just 7% the size of their Android app. And once installed, it's indistinguishable from their Android app:

OYO Lite in action.

Oyo kept both the flagship and "lite" app versions in the store, leaving the final decision to users.

#### Providing a lightweight web experience <a href="#providing-a-lightweight-web-experience" class="w-headline-link">#</a>

Intuitively, users on low-end devices, might be more inclined to download lightweight versions of apps than users on high-end phones. Therefore, if it's possible to identify a user's device, one could prioritize the lightweight app install banner over the heavier platform-specific app version.

On the web, it's possible to obtain device signals and approximately map them to device categories (e.g. "high", "mid", or "low"). You can obtain this information in different ways, using either JavaScript APIs or client hints.

#### Using JavaScript APIs <a href="#using-javascript-apis" class="w-headline-link">#</a>

Using JavaScript APIs like [navigator.hardwareConcurrency](https://developer.mozilla.org/en-US/docs/Web/API/NavigatorConcurrentHardware/hardwareConcurrency), [navigator.deviceMemory](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/deviceMemory), and [navigator.connection](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/connection) you can get information about the device CPU, memory and network status respectively. For example:

    const deviceCategory = req.get('Device-Memory') < 1 ? 'lite' : 'full';`

#### Using client hints <a href="#using-client-hints" class="w-headline-link">#</a>

Device signals can be also inferred in HTTP request headers, through [client hints](https://developer.mozilla.org/en-US/docs/Glossary/Client_hints). Here's how you can implement the previous code for device memory with client hints:

First, tell the browser you are interested in receiving device memory hints in the header of the HTTP response for any first-party request:

    HTTP/1.1 200 OK
    Content-Type: text/html
    Accept-CH: Device-Memory

Then, you'll start receiving Device-Memory information in the request header of HTTP requests:

    GET /main.js HTTP/1.1
    Device-Memory: 0.5

You can use this information in your backends to store a cookie with the category of the user's device:

    app.get('/route', (req, res) => {
      // Determine device category

     const deviceCategory = req.get('Device-Memory') < 1 ? 'lite' : 'full';

      // Set cookie
      res.setCookie('Device-Category', deviceCategory);
      …
    });

Finally, create your own logic to map this information to device categories, and show the corresponding app install prompt on each case:

    if (isDeviceMidOrLowEnd()) {
       // show "Lite app" install banner or PWA A2HS prompt
    } else {
      // show "Core app" install banner
    }

Covering in depth techniques on how to map device signals to device categories is out of the scope of this guide, but you can check out Addy Osmani's [adaptive loading guide](https://dev.to/addyosmani/adaptive-loading-improving-web-performance-on-low-end-devices-1m69), Philip Walton's [The Device Memory API](https://developers.google.com/web/updates/2017/12/device-memory) and Jeremy Wagner's [Adapting to Users with Client Hints](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/client-hints/) for more information on best practices around this.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

The ability to have an icon in the user's home screen is one of the most engaging features of applications. Given that historically this was only possible for apps installed from app stores, companies might think that showing an app store install banner would be enough to convince users to install their experiences. Currently there are more options to have the user install an app, including offering lightweight app experiences in the stores, and letting users add PWAs to the homescreen, by prompting them to do it directly from the website.

<a href="/tags/progressive-web-apps/" class="w-chip">Progressive Web Apps</a>

<span class="w-mr--sm">Last updated: Aug 20, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/progressive-web-apps/define-install-strategy/index.md)

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
