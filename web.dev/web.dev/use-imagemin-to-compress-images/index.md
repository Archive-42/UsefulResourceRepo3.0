## <a href="#use-imagemin-to-compress-images" class="w-toc__header--link">Use Imagemin to compress images</a>

- [Why should you care?](#why-should-you-care)
- [Measure](#measure)
- [Imagemin](#imagemin)
- [Plugins](#plugins)
- [Imagemin CLI](#imagemin-cli)
- [Imagemin npm module](#imagemin-npm-module)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Use Imagemin to compress images

Nov 5, 2018 <span class="w-author__separator">•</span> Updated Apr 6, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

- <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
- <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
- <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

## Why should you care? <a href="#why-should-you-care" class="w-headline-link">#</a>

Uncompressed images bloat your pages with unnecessary bytes. The photo on the right is 40% smaller than the one on the left, yet would probably look identical to the average user.

<table><colgroup><col style="width: 50%" /><col style="width: 50%" /></colgroup><thead><tr class="header"><th><p><img src="https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format" sizes="(min-width: 376px) 376px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/LRE2JJAuShXTjQF5ZSaR.jpg?auto=format&amp;w=752 752w" width="376" height="250" /></p>20 KB</th><th><p><img src="https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format" sizes="(min-width: 376px) 376px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/u9hncwN4TsT7zw2ObU10.jpg?auto=format&amp;w=752 752w" width="376" height="250" /></p>12 KB</th></tr></thead><tbody></tbody></table>

## Measure <a href="#measure" class="w-headline-link">#</a>

Run Lighthouse to check for opportunities to improve page load by compressing images. These opportunities are listed under "Efficiently encode images":

<img src="https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format" alt="image" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/LnIukPEZHuVJwBtuJ7mc.png?auto=format&amp;w=1600 1600w" width="800" height="552" />

Lighthouse currently reports on opportunities to compress images in JPEG format only.

## Imagemin <a href="#imagemin" class="w-headline-link">#</a>

Imagemin is an excellent choice for image compression because it supports a wide variety of image formats and is easily integrated with build scripts and build tools. Imagemin is available as both a [CLI](https://github.com/imagemin/imagemin-cli) and an [npm module](https://www.npmjs.com/package/imagemin). Generally, the npm module is the best choice because it offers more configuration options, but the CLI can be a decent alternative if you want to try Imagemin without touching any code.

### Plugins <a href="#plugins" class="w-headline-link">#</a>

Imagemin is built around "plugins." A plugin is an npm package that compresses a particular image format (e.g. "mozjpeg" compresses JPEGs). Popular image formats may have multiple plugins to pick from.

The most important thing to consider when choosing a plugin is whether it is "lossy" or "lossless." In lossless compression, no data is lost. Lossy compression reduces file size, but at the expense of possibly reducing image quality. If a plugin doesn't mention whether it is "lossy" or "lossless," you can tell by its API: if you can specify the image quality of the output, then it is "lossy."

For most people, lossy plugins are the best choice. They offer significantly greater filesize savings, and you can customize the compression levels to meet your needs. The table below lists popular Imagemin plugins. These aren't the only plugins available, but they'd all be good choices for your project.

<table><thead><tr class="header"><th>Image Format</th><th>Lossy Plugin(s)</th><th>Lossless Plugin(s)</th></tr></thead><tbody><tr class="odd"><td>JPEG</td><td><a href="https://www.npmjs.com/package/imagemin-mozjpeg">imagemin-mozjpeg</a></td><td><a href="https://www.npmjs.com/package/imagemin-jpegtran">imagemin-jpegtran</a></td></tr><tr class="even"><td>PNG</td><td><a href="https://www.npmjs.com/package/imagemin-pngquant">imagemin-pngquant</a></td><td><a href="https://www.npmjs.com/package/imagemin-optipng">imagemin-optipng</a></td></tr><tr class="odd"><td>GIF</td><td><a href="https://www.npmjs.com/package/imagemin-giflossy">imagemin-giflossy</a></td><td><a href="https://www.npmjs.com/package/imagemin-gifsicle">imagemin-gifsicle</a></td></tr><tr class="even"><td>SVG</td><td><a href="https://www.npmjs.com/package/imagemin-svgo">Imagemin-svgo</a></td><td></td></tr><tr class="odd"><td>WebP</td><td><a href="https://www.npmjs.com/package/imagemin-webp">imagemin-webp</a></td><td></td></tr></tbody></table>

### Imagemin CLI <a href="#imagemin-cli" class="w-headline-link">#</a>

The Imagemin CLI works with 5 different plugins: imagemin-gifsicle, imagemin-jpegtran, imagemin-optipng, imagemin-pngquant, and imagemin-svgo. Imagemin uses the appropriate plugin based on the image format of the input.

To compress the images in the "images/" directory and save them to the same directory, run the following command (overwrites the original files):

    $ imagemin images/* --out-dir=images

### Imagemin npm module <a href="#imagemin-npm-module" class="w-headline-link">#</a>

If you use one of these build tools, checkout out the codelabs for Imaginemin with [webpack](/codelab-imagemin-webpack), [gulp](/codelab-imagemin-gulp), or [grunt](/codelab-imagemin-grunt).

You can also use Imagemin by itself as a Node script. This code uses the "imagemin-mozjpeg" plugin to compress JPEG files to a quality of 50 ('0' being the worst; '100' being the best):

    const imagemin = require('imagemin');
    const imageminMozjpeg = require('imagemin-mozjpeg');

    (async() => {
      const files = await imagemin(
          ['source_dir/*.jpg', 'another_dir/*.jpg'],
          {
            destination: 'destination_dir',
            plugins: [imageminMozjpeg({quality: 50})]
          }
      );
      console.log(files);
    })();

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Apr 6, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/use-imagemin-to-compress-images/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-imagemin-webpack/" class="w-callout__link w-callout__link--codelab">Using Imagemin with webpack</a>
- <a href="/codelab-imagemin-gulp/" class="w-callout__link w-callout__link--codelab">Using Imagemin with Gulp</a>
- <a href="/codelab-imagemin-grunt/" class="w-callout__link w-callout__link--codelab">Using Imagemin with Grunt</a>

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
