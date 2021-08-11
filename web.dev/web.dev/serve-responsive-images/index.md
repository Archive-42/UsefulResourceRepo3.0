<a href="/" class="header-default__logo-link gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="header-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="header-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="header-default__link gc-analytics-event">Blog</a> <a href="/about/" class="header-default__link gc-analytics-event">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="drawer-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="drawer-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="drawer-default__link gc-analytics-event">Blog</a> <a href="/about/" class="drawer-default__link gc-analytics-event">About</a>

## <a href="#serve-responsive-images" class="w-toc__header--link">Serve responsive images</a>

- [Resize images](#resize-images)
- [sharp](#sharp)
- [ImageMagick](#imagemagick)
- [How many image versions should you create?](#how-many-image-versions-should-you-create)
- [Other options](#other-options)
- [Serve multiple image versions](#serve-multiple-image-versions)
- [The "src" attribute](#the-)
- [The "srcset" attribute](#the-)
- [The "sizes" attribute](#the-)
- [(Even more) Extra Credit](<#(even-more)-extra-credit>)
- [Verify](#verify)

Share <a href="/newsletter/" class="w-actions__fab w-actions__fab--subscribe gc-analytics-event"><span>subscribe</span></a>

# Serve responsive images

Nov 5, 2018 <span class="w-author__separator">•</span> Updated Jun 4, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75 1x,     https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x,     https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x,     https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x,     https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

- <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
- <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
- <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

Serving desktop-sized images to mobile devices can use 2–4x more data than needed. Instead of a "one-size-fits-all" approach to images, serve different image sizes to different devices.

## Resize images <a href="#resize-images" class="w-headline-link">#</a>

Two of the most popular image resizing tools are the [sharp npm package](https://www.npmjs.com/package/sharp) and the [ImageMagick CLI tool](https://www.imagemagick.org/script/index.php).

The sharp package is a good choice for automating image resizing (for example, generating multiple sizes of thumbnails for all the videos on your website). It is fast and easily integrated with build scripts and tools. On the other hand, ImageMagick is convenient for one-off image resizing because it is used entirely from the command line.

### sharp <a href="#sharp" class="w-headline-link">#</a>

To use sharp as a Node script, save this code as a separate script in your project, and then run it to convert your images:

    const sharp = require('sharp');
    const fs = require('fs');
    const directory = './images';

    fs.readdirSync(directory).forEach(file => {
      sharp(`${directory}/${file}`)
        .resize(200, 100) // width, height
        .toFile(`${directory}/${file}-small.jpg`);
      });

### ImageMagick <a href="#imagemagick" class="w-headline-link">#</a>

To resize an image to 33% of its original size, run the following command in your terminal:

    convert -resize 33% flower.jpg flower-small.jpg

To resize an image to fit within 300px wide by 200px high, run the following command:

    # macOS/Linux
    convert flower.jpg -resize 300x200 flower-small.jpg

    # Windows
    magick convert flower.jpg -resize 300x200 flower-small.jpg

### How many image versions should you create? <a href="#how-many-image-versions-should-you-create" class="w-headline-link">#</a>

There is no single "correct" answer to this question. However, it's common to serve 3-5 different sizes of an image. Serving more image sizes is better for performance, but will take up more space on your servers and require writing a tiny bit more HTML.

### Other options <a href="#other-options" class="w-headline-link">#</a>

Image services like [Thumbor](https://github.com/thumbor/thumbor) (open-source) and [Cloudinary](https://cloudinary.com/) are also worth checking out. Image services provide responsive images (and image manipulation) on-demand. Thumbor is setup by installing it on a server; Cloudinary takes care of these details for you and requires no server setup. Both are easy ways to create responsive images.

## Serve multiple image versions <a href="#serve-multiple-image-versions" class="w-headline-link">#</a>

Specify multiple image versions and the browser will choose the best one to use:

<table><thead><tr class="header"><th><strong>Before</strong></th><th><strong>After</strong></th></tr></thead><tbody><tr class="odd"><td>&lt;img src="flower-large.jpg"&gt;</td><td>&lt;img src="flower-large.jpg" srcset="flower-small.jpg 480w, flower-large.jpg 1080w" sizes="50vw"&gt;</td></tr></tbody></table>

The `<img>` tag's [`src`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#attr-src), [`srcset`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#attr-srcset), and [`sizes`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#attr-sizes) attributes all interact to achieve this end result.

### The "src" attribute <a href="#the-%22src%22-attribute" class="w-headline-link">#</a>

The src attribute makes this code work for browsers that don't [support](https://caniuse.com/#search=srcset) the `srcset` and `sizes` attributes. If a browser does not support these attributes, it will fall back to loading the resource specified by the `src` attribute.

**Gotchas!**

The resource specified by the `src` attribute should be large enough to work well on all device sizes.

### The "srcset" attribute <a href="#the-%22srcset%22-attribute" class="w-headline-link">#</a>

The `srcset` attribute is a comma-separated list of image filenames and their width or density descriptors.

This example uses [width descriptors](https://www.w3.org/TR/html5/semantics-embedded-content.html#width-descriptor). `480w` is a width descriptor tells the browser that `flower-small.jpg` is 480px wide; `1080w` is a width descriptor tells the browser that `flower-large.jpg` is 1080px wide.

"Width descriptor" sounds fancy but is just a way to tell the browser the width of an image. This saves the browser from needing to download the image to determine its size.

**Gotchas!**

Use the `w` unit (instead of `px`) to write width descriptors. For example, a 1024px wide image would be written as `1024w`.

**Extra Credit:** You don't need to know about density descriptors to serve different image sizes. However, if you're curious about how density descriptors work, check out the [Resolution Switching code lab](/codelab-density-descriptors). Density descriptors are used to serve different images based on the device's [pixel density](https://en.wikipedia.org/wiki/Pixel_density).

### The "sizes" attribute <a href="#the-%22sizes%22-attribute" class="w-headline-link">#</a>

The sizes attribute tells the browser how wide the image will be when it is displayed. However, the sizes attribute has no effect on display size; you still need CSS for that.

The browser uses this information, along with what it knows about the user's device (i.e. its dimensions and pixel density), to determine which image to load.

If a browser does not recognize the "`sizes`" attribute, it will fallback to loading the image specified by the "`src`" attribute. (Browsers shipped support for the "`sizes`" and "`srcset`" attributes at the same time, so a browser will either support both attributes or neither.)

**Gotchas!**

Slot width can be specified using a variety of units. The following are all valid sizes:

- `100px`
- `33vw`
- `20em`
- `calc(50vw-10px)`

The following is not a valid size:

- `25%` (percentages cannot be used with the sizes attribute)

**Extra Credit:** If you want to be fancy, you can also use the sizes attribute to specify multiple slot sizes. This accommodates websites that use different layouts for different viewport sizes. Check out this [multiple slot code sample](/codelab-specifying-multiple-slot-widths) to learn how to do this.

### (Even more) Extra Credit <a href="#(even-more)-extra-credit" class="w-headline-link">#</a>

In addition to all the extra credit already listed (images are complex!), you can also use these same concepts for [art direction](https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images#Art_direction). Art direction is the practice of serving completely different looking images (rather than different versions of the same image) to different viewports. You can learn more in the [Art Direction code lab](/codelab-art-direction).

## Verify <a href="#verify" class="w-headline-link">#</a>

Once you've implemented responsive images, you can use Lighthouse to make sure that you didn't miss any images. Run the Lighthouse Performance Audit (**Lighthouse &gt; Options &gt; Performance**) and look for the results of the **Properly size images** audit. These results will list the images that need to be resized.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm"> Last updated: Jun 4, 2021 </span> [Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/serve-responsive-images/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-specifying-multiple-slot-widths/" class="w-callout__link w-callout__link--codelab">Specifying multiple slot widths</a>
- <a href="/codelab-art-direction/" class="w-callout__link w-callout__link--codelab">Art direction</a>
- <a href="/codelab-density-descriptors/" class="w-callout__link w-callout__link--codelab">Use density descriptors</a>

<a href="/fast" class="w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single gc-analytics-event">Return to all articles</a>

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
