<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#optimize-css-background-images-with-media-queries" class="w-toc__header--link">Optimize CSS background images with media queries</a>
----------------------------------------------------------------------------------------------------------------------------------------------

-   [Prerequisites](#prerequisites)
-   [Understand responsive background images](#understand-responsive-background-images)
-   [Use media queries](#use-media-queries)
-   [Measure for different devices](#measure-for-different-devices)
-   [Summary](#summary)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Optimize CSS background images with media queries
=================================================

Mar 5, 2020 <span class="w-author__separator">•</span> Updated Mar 5, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

-   <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
-   <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

Many sites request heavy resources, like images, that are not optimized for certain screens, and send large CSS files containing styles that some devices will never use. Using media queries is a popular technique for delivering tailored stylesheets and assets to different screens to reduce the amount of data transferred to users and improve page load performance. This guide shows you how to use media queries to send images that are only as large as they need to be, a technique commonly known as **responsive images**.

Prerequisites <a href="#prerequisites" class="w-headline-link">#</a>
--------------------------------------------------------------------

This guide assumes that you're familiar with [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools). You can use another browser's DevTools instead if you prefer. You'll just need to map the Chrome DevTools screenshots in this guide back to the relevant features in your browser of choice.

Understand responsive background images <a href="#understand-responsive-background-images" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------

First, analyze the network traffic of the unoptimized demo:

1.  Open the [unoptimized demo](https://use-media-queries-unoptimized.glitch.me/) in a new Chrome tab.
2.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
3.  Click the **Network** tab.
4.  Reload the page.

Check out [Inspect Network Activity With Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/network/) if you need more help with DevTools.

You'll see that the only image that's being requested is `background-desktop.jpg`, which has a size of **1006KB**:

<figure><img src="https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/K8P4MHp2FSnZYTw3ZVkG.png?auto=format&amp;w=1600 1600w" width="800" height="126" /></figure>Resize the browser window and notice that the Network Log isn't showing any new requests being made by the page. This means that the same image background is being used for all screen sizes.

You can see the styles that control the background image in [style.css](https://use-media-queries-unoptimized.glitch.me/style.css):

    body {
      background-position: center center;
      background-attachment: fixed;
      background-repeat: no-repeat; background-size: cover;
      background-image: url(images/background-desktop.jpg);
    }

Here's the meaning of each of the properties used:

-   `background-position: center center`: Center the image vertically and horizontally.
-   `background-repeat: no-repeat`: Show the image only once.
-   `background-attachment: fixed`: Avoid making the background image scroll.
-   `background-size: cover`: Resize the image to cover the entire container.
-   `background-image: url(images/background-desktop.jpg)`: The URL of the image.

When combined, these styles tell the browser to adapt the background image to different screen heights and widths. This is the first step towards achieving a responsive background.

Using a single background image for all screen sizes has some limitations:

-   The same amount of bytes are sent, regardless of the screen size, even when, for some devices, like phones, a smaller and more lightweight image background would look just as good. In general, you want to send the smallest possible image that still looks good on the user's screen to improve performance and save user data.
-   In smaller devices the image will be stretched or cut to cover the entire screen, potentially hiding relevant parts of the background to users.

In the next section, you'll learn how to apply an optimization to load different background images, according to the user's device.

Use media queries <a href="#use-media-queries" class="w-headline-link">#</a>
----------------------------------------------------------------------------

Using media queries is a common technique to declare stylesheets that will only apply to certain media or device types. They are implemented by using [@media rules](https://developer.mozilla.org/en-US/docs/Web/CSS/@media), which let you define a set of breakpoints, where specific styles are defined. When the conditions defined by the `@media` rule are met (for example, a certain screen width), the group of styles defined inside the breakpoint will be applied.

The following steps can be used to apply media queries to [the site](https://use-media-queries-unoptimized.glitch.me/) so that different images are used, depending on the maximum width of the device requesting the page.

-   In `style.css` remove the line that contains the background image URL:

<!-- -->

    body {
      background-position: center center;
      background-attachment: fixed;
      background-repeat: no-repeat; background-size: cover;
      background-image: url(images/background-desktop.jpg);
    }

-   Next, create a breakpoint for each screen width, based on the common dimensions in pixels that mobile, tablet, and desktop screens usually have:

For mobile:

    @media (max-width: 480px) {
        body {
            background-image: url(images/background-mobile.jpg);
        }
    }

For tablets:

    @media (min-width: 481px) and (max-width: 1024px) {
        body {
            background-image: url(images/background-tablet.jpg);
        }
    }

For desktop devices:

    @media (min-width: 1025px) {
        body {
           background-image: url(images/background-desktop.jpg);
       }
    }

Open the optimized version of [style.css](https://use-media-queries-optimized.glitch.me/style.css) in your browser to see the changes made.

The images used in the optimized demo are already resized to fit into different screen sizes. Showing how to resize images is out of the scope of this guide, but if you want to know more about this, the [Serve responsive images guide](/serve-responsive-images/) covers some useful tools, like the [sharp npm package](https://www.npmjs.com/package/sharp) and the [ImageMagick CLI](https://www.imagemagick.org/script/index.php).

Measure for different devices <a href="#measure-for-different-devices" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------

Next visualize the resulting site in different screen sizes and in simulated mobile devices:

1.  Open the [optimized site](https://use-media-queries-optimized.glitch.me/) in a new Chrome tab.
2.  Make your viewport narrow (less than `480px`).
3.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
4.  Click the **Network** tab.
5.  Reload the page. Notice how the `background-mobile.jpg` image was requested.
6.  Make your viewport wider. Once it's wider than `480px` notice how `background-tablet.jpg` is requested. Once it's wider than `1025px` notice how `background-desktop.jpg` is requested.

When the width of the browser screen is changed, new images are requested.

In particular when the width is below the value defined in the mobile breakpoint (480px), you see the following Network Log:

<figure><img src="https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/jd2kHIefYf91udpFEmvx.png?auto=format&amp;w=1600 1600w" width="800" height="125" /></figure>The size of the new mobile background is **67% smaller** than the desktop one.

Summary <a href="#summary" class="w-headline-link">#</a>
--------------------------------------------------------

In this guide you've learned to apply media queries to request background images tailored to specific screen sizes and save bytes when accessing the site on smaller devices, like mobile phones. You used the `@media` rule to implement a responsive background. This technique is widely supported by all browsers. A new CSS feature: [image-set()](https://drafts.csswg.org/css-images-4/#image-set-notation), can be used for the same purpose with fewer lines of code. At the time of this writing, this feature is not supported in all browsers, but you might want to keep an eye on how adoption evolves, as it can represent an interesting alternative to this technique.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Mar 5, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/optimize-css-background-images-with-media-queries/index.md)

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