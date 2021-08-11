<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#choose-the-correct-level-of-compression" class="w-toc__header--link">Choose the correct level of compression</a>
--------------------------------------------------------------------------------------------------------------------------

-   [Optimizing vector images](#optimizing-vector-images)
-   [Lossless versus lossy image compression](#lossless-versus-lossy-image-compression)
-   [Image optimization checklist](#image-optimization-checklist)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Choose the correct level of compression
=======================================

Aug 30, 2018 <span class="w-author__separator">•</span> Updated Jun 18, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Ilya Grigorik" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/ilyagrigorik/)

<a href="/authors/ilyagrigorik/" class="w-author__name-link">Ilya Grigorik</a>

-   <a href="https://twitter.com/igrigorik" class="w-author__link">Twitter</a>
-   <a href="https://github.com/igrigorik" class="w-author__link">GitHub</a>

Images often account for most of the downloaded bytes on a web page and also often occupy a significant amount of visual space. As a result, optimizing images can often yield some of the largest byte savings and performance improvements for your website: the fewer bytes the browser has to download, the less competition there is for the client's bandwidth and the faster the browser can download and render useful content on the screen.

Image optimization is both an art and science: an art because there is no one definitive answer for how best to compress an individual image, and a science because there are many well developed techniques and algorithms that can significantly reduce the size of an image. Finding the optimal settings for your image requires careful analysis along many dimensions: format capabilities, content of encoded data, quality, pixel dimensions, and more.

Optimizing vector images <a href="#optimizing-vector-images" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------

All modern browsers support Scalable Vector Graphics (SVG), which is an XML-based image format for two-dimensional graphics. You can embed the SVG markup directly on the page or as an external resource. Most vector-based drawing software can create SVG files or you can write them by hand directly in your favorite text editor.

    <?xml version="1.0" encoding="utf-8"?>
    <!-- Generator: Adobe Illustrator 17.1.0, SVG Export Plug-In . SVG Version: 6.00 Build 0)  -->
    <svg version="1.2" baseProfile="tiny" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink"
        x="0px" y="0px" viewBox="0 0 612 792" xml:space="preserve">
    <g id="XMLID_1_">
      <g>
        <circle fill="red" stroke="black" stroke-width="2" stroke-miterlimit="10" cx="50" cy="50" r="40"/>
      </g>
    </g>
    </svg>

The above example renders the below simple circle shape with a black outline and red background and was exported from Adobe Illustrator.

As you can tell, it contains a lot of metadata, such as layer information, comments, and XML namespaces that are often unnecessary to render the asset in the browser. As a result, it is always a good idea to minify your SVG files by running through a tool like [SVGO](https://github.com/svg/svgo).

Case in point, SVGO reduces the size of the above SVG file generated by Illustrator by 58%, taking it from 470 to 199 bytes.

    <svg version="1.2" baseProfile="tiny" xmlns="http://www.w3.org/2000/svg" viewBox="0 0 612 792"><circle fill="red" stroke="#000" stroke-width="2" stroke-miterlimit="10" cx="50" cy="50" r="40"/></svg>

Because SVG is an XML-based format, you can also apply GZIP compression to reduce its transfer size—make sure your server is configured to compress SVG assets!

A raster image is simply a two-dimensional grid of individual "pixels"—for example, a 100x100 pixel image is a sequence of 10,000 pixels. In turn, each pixel stores the "[RGBA](https://en.wikipedia.org/wiki/RGBA_color_space)" values: (R) red channel, (G) green channel, (B) blue channel, and (A) alpha (transparency) channel.

Internally, the browser allocates 256 values (shades) for each channel, which translates to 8 bits per channel (2 ^ 8 = 256), and 4 bytes per pixel (4 channels x 8 bits = 32 bits = 4 bytes). As a result, if we know the dimensions of the grid we can easily calculate the filesize:

-   100x100 pixel image is composed of 10,000 pixels
-   10,000 pixels x 4 bytes = 40,000 bytes
-   40,000 bytes / 1024 = 39 KB

As an aside, regardless of the image format used to transfer the data from the server to the client, when the image is decoded by the browser, each pixel always occupies 4 bytes of memory. This can be an important constraint for large images and devices which do not have a lot of available memory —for example, low-end mobile devices.

<table><thead><tr class="header"><th>Dimensions</th><th>Pixels</th><th>File size</th></tr></thead><tbody><tr class="odd"><td>100 x 100</td><td>10,000</td><td>39 KB</td></tr><tr class="even"><td>200 x 200</td><td>40,000</td><td>156 KB</td></tr><tr class="odd"><td>300 x 300</td><td>90,000</td><td>351 KB</td></tr><tr class="even"><td>500 x 500</td><td>250,000</td><td>977 KB</td></tr><tr class="odd"><td>800 x 800</td><td>640,000</td><td>2500 KB</td></tr></tbody></table>

39 KB for a 100x100 pixel image may not seem like a big deal, but the filesize quickly explodes for larger images and makes image assets both slow and expensive to download. This post has so far only focused on the "uncompressed" image format. Thankfully, a lot can be done to reduce the image file size.

One simple strategy is to reduce the "bit-depth" of the image from 8 bits per channel to a smaller color palette: 8 bits per channel gives us 256 values per channel and 16,777,216 (256 ^ 3) colors in total. What if you reduce the palette to 256 colors? Then you would only need 8 bits in total for the RGB channels and immediately save two bytes per pixel—that's 50% compression savings over the original 4 bytes per pixel format!

<figure><img src="https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format" alt="Left to right (PNG): 32-bit (16M colors), 7-bit (128 colors), 5-bit (32 colors)." sizes="(min-width: 612px) 612px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/ssek7uXzhs67joEbp0P8.png?auto=format&amp;w=1224 1224w" width="612" height="266" /><figcaption>Left to right (PNG): 32-bit (16M colors), 7-bit (128 colors), 5-bit (32 colors).</figcaption></figure>Complex scenes with gradual color transitions (for example, gradients or sky) require larger color palettes to avoid visual artifacts such as the pixelated sky in the 5-bit asset. On the other hand, if the image only uses a few colors, then a large palette is simply wasting precious bits!

Next, once you've optimized the data stored in individual pixels you could get more clever and look at nearby pixels as well: turns out, many images, and especially photos, have many nearby pixels with similar colors— for example, the sky, repeating textures, and so on. Using this information to your advantage the compressor can apply [delta encoding](https://en.wikipedia.org/wiki/Delta_encoding) where instead of storing the individual values for each pixel, you can store the difference between nearby pixels: if the adjacent pixels are the same, then the delta is "zero" and you only need to store a single bit! But why stop there…

The human eye has different level of sensitivity to different colors: you can optimize your color encoding to account for this by reducing or increasing the palette for those colors. "Nearby" pixels form a two-dimensional grid. This means that each pixel has multiple neighbors: you can use this fact to further improve delta encoding. Instead of looking at just the immediate neighbors for each pixel, you can look at larger blocks of nearby pixels and encode different blocks with different settings.

As you can tell, image optimization gets complicated quickly (or fun, depending on your perspective), and is an active area of academic and commercial research. Images occupy a lot of bytes and there is a lot of value in developing better image compression techniques! If you're curious to learn more, head to the [Wikipedia page](https://en.wikipedia.org/wiki/Image_compression), or check out the [WebP compression techniques whitepaper](https://developers.google.com/speed/webp/docs/compression) for a hands-on example.

So, once again, this is all great, but also very academic: how does it help you to optimize images on your site? Well, it's important to understand the shape of the problem: RGBA pixels, bit-depth, and various optimization techniques. All of these concepts are critical to understand and keep in mind before you dive into the discussions of various raster image formats.

Lossless versus lossy image compression <a href="#lossless-versus-lossy-image-compression" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------

For certain types of data, such as source code for a page, or an executable file, it is critical that a compressor does not alter or lose any of the original information: a single missing or wrong bit of data could completely change the meaning of the contents of the file, or worse, break it entirely. For some other types of data, such as images, audio, and video, it may be perfectly acceptable to deliver an "approximate" representation of the original data.

In fact, due to how the eye works, we can often get away with discarding some information about each pixel in order to reduce the filesize of an image— for example, our eyes have different sensitivity to different colors, which means that we can use fewer bits to encode some colors. As a result, a typical image optimization pipeline consists of two high level steps:

1.  Image is processed with a [lossy](https://en.wikipedia.org/wiki/Lossy_compression) filter that eliminates some pixel data.
2.  Image is processed with a [lossless](https://en.wikipedia.org/wiki/Lossless_compression) filter that compresses the pixel data.

The first step is optional, and the exact algorithm will depend on the particular image format, but it is important to understand that any image can undergo a lossy compression step to reduce its size. In fact, the difference between various image formats, such as GIF, PNG, JPEG, and others, is in the combination of the specific algorithms they use (or omit) when applying the lossy and lossless steps.

So, what is the "optimal" configuration of lossy and lossless optimization? The answer depends on the image contents and your own criteria such as the tradeoff between filesize and artifacts introduced by lossy compression: In some cases, you may want to skip lossy optimization to communicate intricate detail in its full fidelity. In other cases, you may be able to apply aggressive lossy optimization to reduce the filesize of the image asset. This is where your own judgment and context need to come into play—there is no one universal setting.

As a hands-on example, when using a lossy format such as JPEG, the compressor will typically expose a customizable "quality" setting (for example, the quality slider provided by the "Save for Web" functionality in Adobe Photoshop), which is typically a number between 1 and 100 that controls the inner workings of the specific collection of lossy and lossless algorithms. For best results, experiment with various quality settings for your images, and don't be afraid to dial down the quality—the visual results are often very good and the filesize savings can be quite large.

Note that quality levels for different image formats are not directly comparable due to differences in algorithms used to encode the image: quality 90 JPEG will produce a very different result than a quality 90 WebP. In fact, even quality levels for the same image format may produce visibly different output based on implementation of the compressor!

Image optimization checklist <a href="#image-optimization-checklist" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------

Some tips and techniques to keep in mind as you work on optimizing your images:

-   **Prefer vector formats:** vector images are resolution and scale independent, which makes them a perfect fit for the multi-device and high-resolution world.
-   **Minify and compress SVG assets:** XML markup produced by most drawing applications often contains unnecessary metadata which can be removed; Ensure that your servers are configured to apply GZIP compression for SVG assets.
-   **Prefer WebP over older raster formats**: [WebP images](/serve-images-webp/) will usually be far smaller than older images.
-   **Pick best raster image format:** determine your functional requirements and [select the one that suits each particular asset](/choose-the-right-image-format/).
-   **Experiment with optimal quality settings for raster formats:** don't be afraid to dial down the "quality" settings, the results are often very good and byte savings are significant.
-   **Remove unnecessary image metadata:** many raster images contain unnecessary metadata about the asset: geo information, camera information, and so on. Use appropriate tools to strip this data.
-   **Serve scaled images:** [resize images](/serve-images-with-correct-dimensions/) and ensure that the "display" size is as close as possible to the "natural" size of the image. Pay close attention to large images in particular, as they account for largest overhead when resized!
-   **Automate, automate, automate:** invest into automated tools and infrastructure that will ensure that all of your image assets are always optimized.

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/images/" class="w-chip">Images</a>

<span class="w-mr--sm">Last updated: Jun 18, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/compress-images/index.md)

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
