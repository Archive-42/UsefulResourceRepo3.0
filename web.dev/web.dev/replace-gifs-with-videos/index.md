## <a href="#replace-animated-gifs-with-video-for-faster-page-loads" class="w-toc__header--link">Replace animated GIFs with video for faster page loads</a>

- [Measure first](#measure-first)
- [Create MPEG videos](#create-mpeg-videos)
- [Create WebM videos](#create-webm-videos)
- [Compare the difference](#compare-the-difference)
- [Replace the GIF img with a video](#replace-the-gif-img-with-a-video)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Replace animated GIFs with video for faster page loads

Nov 5, 2018 <span class="w-author__separator">•</span> Updated Aug 29, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

- <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
- <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
- <a href="https://houssein.me/" class="w-author__link">Blog</a>

Have you ever seen an animated GIF on a service like Imgur or Gfycat, inspected it in your dev tools, only to find out that GIF was really a video? There's a good reason for that. Animated GIFs can be downright _huge_.

<img src="https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format" alt="DevTools network panel showing a 13.7 MB gif." class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/3UZ0b9dDotVIXWQT5Auk.png?auto=format&amp;w=1600 1600w" width="800" height="155" />

Thankfully, this is one of those areas of loading performance where you can do relatively little work to realize huge gains! **By converting large GIFs to videos, you can save big on users' bandwidth**.

## Measure first <a href="#measure-first" class="w-headline-link">#</a>

Use Lighthouse to check your site for GIFs that can be converted to videos. In DevTools, click on the Audits tab and check the Performance checkbox. Then run Lighthouse and check the report. If you have any GIFs that can be converted, you should see a suggestion to "Use video formats for animated content":

<img src="https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format" alt="A failing Lighthouse audit, use video formats for animated content." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/KOSr9IivnkyaFk6RJ5u1.png?auto=format&amp;w=1600 1600w" width="800" height="173" />

## Create MPEG videos <a href="#create-mpeg-videos" class="w-headline-link">#</a>

There are a number of ways to convert GIFs to video, **[FFmpeg](https://www.ffmpeg.org/)** is the tool used in this guide. To use FFmpeg to convert the GIF, `my-animation.gif` to an MP4 video, run the following command in your console:

    ffmpeg -i my-animation.gif -b:v 0 -crf 25 -f mp4 -vcodec libx264 -pix_fmt yuv420p my-animation.mp4

This tells FFmpeg to take `my-animation.gif` as the **input**, signified by the `-i` flag, and to convert it to a video called `my-animation.mp4`.

The libx264 encoder only works with files that have even dimensions, like 320px by 240px. If the input GIF has odd dimensions you can include a crop filter to avoid FFmpeg throwing a 'height/width not divisible by 2' error:

    ffmpeg -i my-animation.gif -vf "crop=trunc(iw/2)*2:trunc(ih/2)*2" -b:v 0 -crf 25 -f mp4 -vcodec libx264 -pix_fmt yuv420p my-animation.mp4

## Create WebM videos <a href="#create-webm-videos" class="w-headline-link">#</a>

While MP4 has been around since 1999, WebM is a relatively new file format initially released in 2010. WebM videos are much smaller than MP4 videos, but not all browsers support WebM so it makes sense to generate both.

To use FFmpeg to convert `my-animation.gif` to a WebM video, run the following command in your console:

    ffmpeg -i my-animation.gif -c vp9 -b:v 0 -crf 41 my-animation.webm

## Compare the difference <a href="#compare-the-difference" class="w-headline-link">#</a>

The cost savings between a GIF and a video can be pretty significant.

<img src="https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format" alt="File size comparison showing 3.7 MB for the gif, 551 KB for the mp4 and 341 KB for the webm." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/LWzvOWaOdMnNLTPWjayt.png?auto=format&amp;w=1600 1600w" width="800" height="188" />

In this example, the initial GIF is 3.7 MB, compared to the MP4 version, which is 551 KB, and the WebM version, which is only 341 KB!

## Replace the GIF img with a video <a href="#replace-the-gif-img-with-a-video" class="w-headline-link">#</a>

Animated GIFs have three key traits that a video needs to replicate:

- They play automatically.
- They loop continuously (usually, but it is possible to prevent looping).
- They're silent.

Luckily, you can recreate these behaviors using the `<video>` element.

    <video autoplay loop muted playsinline></video>

A `<video>` element with these attributes plays automatically, loops endlessly, plays no audio, and plays inline (i.e., not full screen), all the hallmark behaviors expected of animated GIFs! 🎉

Finally, the `<video>` element requires one or more `<source>` child elements pointing to different video files that the browser can choose from, depending on the browser's format support. Provide both WebM and MP4, so that if a browser doesn't support WebM, it can fall back to MP4.

    <video autoplay loop muted playsinline>
      <source src="my-animation.webm" type="video/webm">
      <source src="my-animation.mp4" type="video/mp4">
    </video>

**Try it**! [Replace an animated GIF with a video](/codelab-replace-gifs-with-video).

Browsers don't speculate about which `<source>` is optimal, so the order of `<source>`'s matters. For example, if you specify an MP4 video first and the browser supports WebM, browsers will skip the WebM `<source>` and use the MPEG-4 instead. If you prefer a WebM `<source>` be used first, specify it first!

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Aug 29, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/replace-gifs-with-videos/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-replace-gifs-with-video/" class="w-callout__link w-callout__link--codelab">Replace GIFs with video</a>

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
