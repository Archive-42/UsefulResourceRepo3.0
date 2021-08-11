<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="header-default__logo-link gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="header-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="header-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="header-default__link gc-analytics-event">Blog</a> <a href="/about/" class="header-default__link gc-analytics-event">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="drawer-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="drawer-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="drawer-default__link gc-analytics-event">Blog</a> <a href="/about/" class="drawer-default__link gc-analytics-event">About</a>

<a href="#serve-images-with-correct-dimensions" class="w-toc__header--link">Serve images with correct dimensions</a>
--------------------------------------------------------------------------------------------------------------------

-   [Identify incorrectly sized images](#identify-incorrectly-sized-images)
-   [Determine the correct image size](#determine-the-correct-image-size)
-   [A quick note on CSS units](#a-quick-note-on-css-units)
-   [The "Good" Approach](#the-)
-   [The "Better" approach](#the-)
-   [Resize images](#resize-images)
-   [Verify](#verify)

Share <a href="/newsletter/" class="w-actions__fab w-actions__fab--subscribe gc-analytics-event"><span>subscribe</span></a>

Serve images with correct dimensions
====================================

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75 1x,     https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x,     https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x,     https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x,     https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

-   <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
-   <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
-   <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

We've all been there: you forgot to scale down an image before adding it to the page. The image looks fine, but it is wasting users' data and hurting page performance.

Identify incorrectly sized images <a href="#identify-incorrectly-sized-images" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

Lighthouse makes it easy to identify incorrectly-sized images. Run the Performance Audit (**Lighthouse &gt; Options &gt; Performance**) and look for the results of the **Properly size images** audit. The audit lists any images that need to be resized.

Determine the correct image size <a href="#determine-the-correct-image-size" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------

Image sizing can be deceptively complicated. For this reason, we've provided two approaches: the "good" and the "better." Both will improve performance, but the "better" approach may take a bit longer to understand and implement. However, it will also reward you with bigger performance improvements. The best choice for you is the one that you feel comfortable implementing.

### A quick note on CSS units <a href="#a-quick-note-on-css-units" class="w-headline-link">#</a>

There are two types of CSS units for specifying the size of HTML elements, including images:

-   Absolute units: Elements styled using absolute units will always be displayed at the same size, regardless of device. Examples of valid, absolute CSS units: px, cm, mm, in.
-   Relative units: Elements styled using relative units will be displayed at varying sizes, depending on the relative length specified. Examples of valid, relative CSS units: %, vw (1vw = 1% of the width of the viewport), em (1.5 em = 1.5 times font size).

### The "Good" Approach <a href="#the-%22good%22-approach" class="w-headline-link">#</a>

For images with sizing based on…

-   **Relative units**: Resize the image to a size that will work across all devices.

You may find it helpful to check your analytics data (e.g. Google Analytics) to see which display sizes are commonly used by your users. Alternatively, [screensiz.es](http://screensiz.es/) provides information about the displays of many common devices.

-   **Absolute units**: Resize the image to match the size that it is displayed at.

The DevTools Elements panel can be used to determine what size an image is displayed at.

<img src="https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format" alt="DevTools element&#39;s panel" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=200 200w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=228 228w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=260 260w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=296 296w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=338 338w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=385 385w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=439 439w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=500 500w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=571 571w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=650 650w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=741 741w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=845 845w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=964 964w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=1098 1098w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=1252 1252w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=1428 1428w,     https://web-dev.imgix.net/image/admin/pKQa0Huu0KGInOekdz6M.png?auto=format&amp;w=1600 1600w" width="800" height="364" />

### The "Better" approach <a href="#the-%22better%22-approach" class="w-headline-link">#</a>

For images with sizing based on…

-   **Absolute units:** Use [srcset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/source#attr-srcset) and [sizes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/source#attr-sizes) attributes to serve different images to different display densities. (Read the guide on Responsive Images [here](/serve-responsive-images).)

"Display density" refers to the fact that different displays have different densities of pixels. All other things being equal, a high pixel density display will look sharper than a low pixel density display.

As a result, multiple image versions are necessary if you want users to experience the crispest possible images, regardless of the pixel density of their device.

Some sites find that this difference in image quality matters, some find that it does not.

Responsive image techniques make this possible by allowing you to list multiple image versions and for the device to choose the image that works best for it.

-   **Relative units:** Use responsive images to serve different images to display sizes. (Read the guide [here](/serve-responsive-images).)

An image that works across all devices will be unnecessarily large for smaller devices. Responsive image techniques, specifically [srcset](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/source#attr-srcset%22) and [sizes](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/source#attr-sizes), allow you to specify multiple image versions and for the device to choose the size that works best for it.

Resize images <a href="#resize-images" class="w-headline-link">#</a>
--------------------------------------------------------------------

Regardless of the approach that you choose, you may find it helpful to use ImageMagick to resize your images. [ImageMagick](https://www.imagemagick.org/script/index.php) is the most popular command line tool for creating and editing images. Most people can resize images far more quickly when using the CLI than a GUI-based image editor.

Resize image to 25% the size of the original:

    convert flower.jpg -resize 25% flower_small.jpg

Scale image to fit within "200px wide by 100px tall":

    # macOS/Linux
    convert flower.jpg -resize 200x100 flower_small.jpg

    # Windows
    magick convert flower.jpg -resize 200x100 flower_small.jpg

If you'll be resizing many images, you may find it more convenient to use a script or service to automate the process. You can learn more about this in the Responsive Images guide.

Verify <a href="#verify" class="w-headline-link">#</a>
------------------------------------------------------

Once you've resized all your images, re-run Lighthouse to verify that you didn't miss anything.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm"> Last updated: Nov 5, 2018 </span> [Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/serve-images-with-correct-dimensions/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-serve-images-correct-dimensions/" class="w-callout__link w-callout__link--codelab">Serve images with correct dimensions</a>

<a href="/fast" class="w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single gc-analytics-event">Return to all articles</a>

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
