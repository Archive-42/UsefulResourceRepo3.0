<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#choose-the-right-image-format" class="w-toc__header--link">Choose the right image format</a>
------------------------------------------------------------------------------------------------------

-   [Choose the right image format](#choose-the-right-image-format)
-   [Implications of high-resolution screens](#implications-of-high-resolution-screens)
-   [Features of different raster image formats](#features-of-different-raster-image-formats)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Choose the right image format
=============================

Aug 30, 2018 <span class="w-author__separator">•</span> Updated Jun 18, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Ilya Grigorik" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/ilyagrigorik/)

<a href="/authors/ilyagrigorik/" class="w-author__name-link">Ilya Grigorik</a>

-   <a href="https://twitter.com/igrigorik" class="w-author__link">Twitter</a>
-   <a href="https://github.com/igrigorik" class="w-author__link">GitHub</a>

The very first question you should ask yourself is whether an image is, in fact, required to achieve the effect you are after. Good design is simple and will also always yield the best performance. If you can eliminate an image resource, which often requires a large number of bytes relative to HTML, CSS, JavaScript and other assets on the page, then that is always the best optimization strategy. That said, a well-placed image can also communicate more information than a thousand words, so it is up to you to find that balance.

Next, you should consider if there is an alternative technology that could deliver the desired results, but in a more efficient manner:

-   **CSS effects** (such as shadows or gradients) and CSS animations can be used to produce resolution-independent assets that always look sharp at every resolution and zoom level, often at a fraction of the bytes required by an image file.
-   **Web fonts** enable use of beautiful typefaces while preserving the ability to select, search, and resize text—a significant improvement in usability.

If you ever find yourself encoding text in an image asset, stop and reconsider. Great typography is critical to good design, branding, and readability, but text-in-images delivers a poor user experience: the text is not selectable, not searchable, not zoomable, not accessible, and not friendly for high-DPI devices. The use of web fonts requires its [own set of optimizations](https://www.igvita.com/2014/01/31/optimizing-web-font-rendering-performance/), but it addresses all of these concerns and is always a better choice for displaying text.

Choose the right image format <a href="#choose-the-right-image-format" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------

If you are sure an image is the correct option, you should carefully select the right kind of image for the job.

<figure><img src="https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format" alt="Zoomed-in vector image (L) raster image (R)" sizes="(min-width: 585px) 585px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/dJuB2DQcbhtwD5VdPVlR.png?auto=format&amp;w=1170 1170w" width="585" height="313" /><figcaption>Zoomed-in vector image (L) raster image (R)</figcaption></figure>-   [Vector graphics](https://en.wikipedia.org/wiki/Vector_graphics) use lines, points, and polygons to represent an image.
-   [Raster graphics](https://en.wikipedia.org/wiki/Raster_graphics) represent an image by encoding the individual values of each pixel within a rectangular grid.

Each format has its own set of pros and cons. Vector formats are ideally suited for images that consist of simple geometric shapes such as logos, text, or icons. They deliver sharp results at every resolution and zoom setting, which makes them an ideal format for high-resolution screens and assets that need to be displayed at varying sizes.

However, vector formats fall short when the scene is complicated (for example, a photo): the amount of SVG markup to describe all the shapes can be prohibitively high and the output may still not look "photorealistic". When that's the case, that's when you should be using a raster image format such as PNG, JPEG, or WebP.

Raster images do not have the same nice properties of being resolution or zoom independent —when you scale up a raster image you'll see jagged and blurry graphics. As a result, you may need to save multiple versions of a raster image at various resolutions to deliver the optimal experience to your users.

Implications of high-resolution screens <a href="#implications-of-high-resolution-screens" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------

There are two different kinds of pixels: CSS pixels and device pixels. A single CSS pixel may correspond directly to a single device pixel, or may be backed by multiple device pixels. What's the point? Well, the more device pixels there are, the finer the detail of the displayed content on the screen.

<figure><img src="https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format" alt="The difference between CSS pixels and device pixels." sizes="(min-width: 470px) 470px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/oQV7qJ9fUMkYsKlUMrL4.png?auto=format&amp;w=940 940w" width="470" height="205" /><figcaption>The difference between CSS pixels and device pixels.</figcaption></figure>High DPI (HiDPI) screens produce beautiful results, but there is one obvious tradeoff: image assets require more detail in order to take advantage of the higher device pixel counts. The good news is, vector images are ideally suited for this task, as they can be rendered at any resolution with sharp results— you might incur a higher processing cost to render the finer detail, but the underlying asset is the same and is resolution independent.

On the other hand, raster images pose a much larger challenge because they encode image data on a per-pixel basis. Hence, the larger the number of pixels, the larger the filesize of a raster image. As an example, let's consider the difference between a photo asset displayed at 100x100 (CSS) pixels:

<table><thead><tr class="header"><th>Screen resolution</th><th>Total pixels</th><th>Uncompressed filesize (4 bytes per pixel)</th></tr></thead><tbody><tr class="odd"><td>1x</td><td>100 x 100 = 10,000</td><td>40,000 bytes</td></tr><tr class="even"><td>2x</td><td>100 x 100 x 4 = 40,000</td><td>160,000 bytes</td></tr><tr class="odd"><td>3x</td><td>100 x 100 x 9 = 90,000</td><td>360,000 bytes</td></tr></tbody></table>

When we double the resolution of the physical screen, the total number of pixels increases by a factor of four: double the number of horizontal pixels, times double the number of vertical pixels. Hence, a "2x" screen not just doubles, but quadruples the number of required pixels!

So, what does this mean in practice? High-resolution screens enable you to deliver beautiful images, which can be a great product feature. However, high-resolution screens also require high-resolution images, therefore:

-   Prefer vector images whenever possible as they are resolution-independent and always deliver sharp results.
-   If a raster image is required, serve [responsive images](/serve-responsive-images/).

Features of different raster image formats <a href="#features-of-different-raster-image-formats" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------

In addition to different lossy and lossless compression algorithms, different image formats support different features such as animation and transparency (alpha) channels. As a result, the choice of the "right format" for a particular image is a combination of desired visual results and functional requirements.

<table><thead><tr class="header"><th>Format</th><th>Transparency</th><th>Animation</th><th>Browser</th></tr></thead><tbody><tr class="odd"><td><a href="http://en.wikipedia.org/wiki/Portable_Network_Graphics">PNG</a></td><td>Yes</td><td>No</td><td>All</td></tr><tr class="even"><td><a href="http://en.wikipedia.org/wiki/JPEG">JPEG</a></td><td>No</td><td>No</td><td>All</td></tr><tr class="odd"><td><a href="http://en.wikipedia.org/wiki/WebP">WebP</a></td><td>Yes</td><td>Yes</td><td>All modern browsers. See <a href="https://caniuse.com/#feat=webp">Can I use?</a></td></tr></tbody></table>

There are two universally supported raster image formats: PNG and JPEG. In addition to these formats, modern browsers support the newer format WebP, which offers better overall compression and more features. So, which format should you use?

The WebP format will generally provide better compression than older formats, and should be used where possible. You can use WebP along with another image format as a fallback. See [Use WebP images](/serve-images-webp/) for more details.

In terms of older image formats, consider the following:

1.  **Do you need animation? Use `<video>` elements.**
    -   What about GIF? GIF limits the color palette to at most 256 colors, and creates significantly larger file sizes than `<video>` elements. See [Replace animated GIFs with video](/replace-gifs-with-videos/).
2.  **Do you need to preserve fine detail with highest resolution? Use PNG.**
    -   PNG does not apply any lossy compression algorithms beyond the choice of the size of the color palette. As a result, it will produce the highest quality image, but at a cost of significantly higher filesize than other formats. Use judiciously.
    -   If the image asset contains imagery composed of geometric shapes, consider converting it to a vector (SVG) format!
    -   If the image asset contains text, stop and reconsider. Text in images is not selectable, searchable, or "zoomable". If you need to convey a custom look (for branding or other reasons), use a web font instead.
3.  **Are you optimizing a photo, screenshot, or a similar image asset? Use JPEG.**
    -   JPEG uses a combination of lossy and lossless optimization to reduce filesize of the image asset. Try several JPEG quality levels to find the best quality versus filesize tradeoff for your asset.

Finally, note that if you are using a WebView to render content in your platform-specific application, then you have full control of the client and can use WebP exclusively! Facebook and many others use WebP to deliver all of their images within their applications— the savings are definitely worth it.

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/images/" class="w-chip">Images</a>

<span class="w-mr--sm">Last updated: Jun 18, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/choose-the-right-image-format/index.md)

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
