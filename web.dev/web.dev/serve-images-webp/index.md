<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#use-webp-images" class="w-toc__header--link">Use WebP images</a>
--------------------------------------------------------------------------

-   [Why should you care?](#why-should-you-care)
-   [Convert images to WebP](#convert-images-to-webp)
-   [Use cwebp](#use-cwebp)
-   [Use Imagemin](#use-imagemin)
-   [Serve WebP images](#serve-webp-images)
-   [picture](#picture)
-   [source](#source)
-   [img](#img)
-   [Verify WebP usage](#verify-webp-usage)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Use WebP images
===============

Nov 5, 2018 <span class="w-author__separator">•</span> Updated Apr 6, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

-   <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
-   <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
-   <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

Why should you care? <a href="#why-should-you-care" class="w-headline-link">#</a>
---------------------------------------------------------------------------------

WebP images are smaller than their JPEG and PNG counterparts—usually on the magnitude of a 25–35% reduction in filesize. This decreases page sizes and improves performance.

-   YouTube found that switching to WebP thumbnails resulted in [10% faster page loads](https://www.youtube.com/watch?v=rqXMwLbYEE4).
-   Facebook [experienced](https://code.fb.com/android/improving-facebook-on-android/) a 25-35% filesize savings for JPEGs and an 80% filesize savings for PNGs when they switched to using WebP.

WebP is an excellent replacement for JPEG, PNG, and GIF images. In addition, WebP offers both lossless and lossy compression. In lossless compression no data is lost. Lossy compression reduces file size, but at the expense of possibly reducing image quality.

Convert images to WebP <a href="#convert-images-to-webp" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------

People generally use one of the following approaches for converting their images to WebP: the [cwebp command-line tool](https://developers.google.com/speed/webp/docs/using) or the [Imagemin WebP plugin](https://github.com/imagemin/imagemin-webp) (npm package). The Imagemin WebP plugin is generally the best choice if your project uses build scripts or build tools (e.g. Webpack or Gulp), whereas the CLI is a good choice for simple projects or if you'll only need to convert images once.

When you convert images to WebP, you have the option to set a wide variety of compression settings—but for most people the only thing you'll ever need to care about is the quality setting. You can specify a quality level from 0 (worst) to 100 (best). It's worth playing around with this find which level is the right tradeoff between image quality and filesize for your needs.

### Use cwebp <a href="#use-cwebp" class="w-headline-link">#</a>

Convert a single file, using cwebp's default compression settings:

    cwebp images/flower.jpg -o images/flower.webp

Convert a single file, using a quality level of `50`:

    cwebp -q 50 images/flower.jpg -o images/flower.webp

Convert all files in a directory:

    for file in images/*; do cwebp "$file" -o "${file%.*}.webp"; done

### Use Imagemin <a href="#use-imagemin" class="w-headline-link">#</a>

The Imagemin WebP plugin can be used by itself or with your favorite build tool (Webpack/Gulp/Grunt/etc.). This usually involves adding ~10 lines of code to a build script or the configuration file for your build tool. Here are examples of how to do that for [Webpack](https://glitch.com/~webp-webpack), [Gulp](https://glitch.com/~webp-gulp), and [Grunt](https://glitch.com/~webp-grunt).

If you are not using one of those build tools, you can use Imagemin by itself as a Node script. This script will convert the files in the `images` directory and save them in the `compressed_images` directory.

    const imagemin = require('imagemin');
    const imageminWebp = require('imagemin-webp');

    imagemin(['images/*'], {
      destination: 'compressed_images',
      plugins: [imageminWebp({quality: 50})]
    }).then(() => {
      console.log('Done!');
    });

Serve WebP images <a href="#serve-webp-images" class="w-headline-link">#</a>
----------------------------------------------------------------------------

If your site only supports WebP compatible [browsers](https://caniuse.com/#search=webp), you can stop reading. Otherwise, serve WebP to newer browsers and a fallback image to older browsers:

**Before:**

    <img src="flower.jpg" alt="">

**After:**

    <picture>
      <source type="image/webp" srcset="flower.webp">
      <source type="image/jpeg" srcset="flower.jpg">
      <img src="flower.jpg" alt="">
    </picture>

The [`<picture>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/picture), [`<source>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/source), and `<img>` tags, including how they are ordered relative to each other, all interact to achieve this end result.

### picture <a href="#picture" class="w-headline-link">#</a>

The `<picture>` tag provides a wrapper for zero or more `<source>` tags and one `<img>` tag.

### source <a href="#source" class="w-headline-link">#</a>

The `<source>` tag specifies a media resource.

The browser uses the first listed source that's in a format it supports. If the browser does not support any of the formats listed in the `<source>` tags, it falls back to loading the image specified by the `<img>` tag.

**Gotchas!**

-   The `<source>` tag for the "preferred" image format (in this case that is WebP) should be listed first, before other `<source>` tags.

-   The value of the `type` attribute should be the MIME type corresponding to the image format. An image's [MIME type](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/MIME_types/Complete_list_of_MIME_types) and its file extension are often similar, but they aren't necessarily the same thing (e.g. `.jpg` vs. `image/jpeg`).

### img <a href="#img" class="w-headline-link">#</a>

The `<img>` tag is what makes this code work on browsers that don't support the `<picture>` tag. If a browser does not support the `<picture>` tag, it will ignore the tags it doesn't support. Thus, it only "sees" the `<img src="flower.jpg" alt="">` tag and loads that image.

**Gotchas!**

-   The `<img>` tag should always be included, and it should always be listed last, after all `<source>` tags.
-   The resource specified by the `<img>` tag should be in a universally supported format (e.g. JPEG), so it can be used as a fallback.

Verify WebP usage <a href="#verify-webp-usage" class="w-headline-link">#</a>
----------------------------------------------------------------------------

Lighthouse can be used to verify that all images on your site are being served using WebP. Run the Lighthouse Performance Audit (**Lighthouse &gt; Options &gt; Performance**) and look for the results of the **Serve images in next-gen formats** audit. Lighthouse will list any images that are not being served in WebP.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Apr 6, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/serve-images-webp/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-serve-images-webp/" class="w-callout__link w-callout__link--codelab">Creating WebP Images with the Command Line</a>

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
