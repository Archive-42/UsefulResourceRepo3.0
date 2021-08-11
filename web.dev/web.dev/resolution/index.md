





<a href="#resolution" class="w-toc__header--link">Resolution</a>
----------------------------------------------------------------

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Resolution
==========

Jun 30, 2017 <span class="w-author__separator">•</span> Updated Aug 27, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/media" class="w-post-signpost__link">Media</a>

[<img src="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Joe Medley" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/joemedley/)

<a href="/authors/joemedley/" class="w-author__name-link">Joe Medley</a>

-   <a href="https://twitter.com/medleyjp" class="w-author__link">Twitter</a>
-   <a href="https://github.com/jpmedley" class="w-author__link">GitHub</a>

In previous sections I showed you how to change a media file's [codec, containers](/containers-and-codecs), and [bitrate](/bitrate). This page covers resolution. Then I'll move on to [adding them to a web page](/add-media).

*Resolution* is the amount of information in a single frame of video, given as the number of logical pixels in each dimension. For example, a resolution of 1920 by 1080 works out to 1080 stacked horizontal lines, each of which is one logical pixel high and 1920 logical pixels wide. This resolution is frequently abbreviated 1080p because technically the width can vary. The dimensions 1080 by 1920 produce an [aspect ratio](https://en.wikipedia.org/wiki/Aspect_ratio_(image)) of 16:9, which is the ratio of movie screens and modern television sets. By the way this is the resolution defined as [full HD](https://www.google.com/search?q=what+is+hd+resolution&oq=what+is+hd+resolution&aqs=chrome.0.0l6.3183j0j8&sourceid=chrome&ie=UTF-8#q=full+hd+resolution).

[YouTube recommends](https://support.google.com/youtube/answer/6375112) the following resolutions for video uploads, all in the 16:9 aspect ratio. There's nothing specific to YouTube about this list. It's just a list of common 16:9 video resolutions.

<table><thead><tr class="header"><th>Abbreviation</th><th>Dimensions</th></tr></thead><tbody><tr class="odd"><td>2160p</td><td>3840 x 2160</td></tr><tr class="even"><td>1440p</td><td>2560 x 1440</td></tr><tr class="odd"><td>1080p</td><td>1920 x 1080</td></tr><tr class="even"><td>720p</td><td>1280 x 720</td></tr><tr class="odd"><td>480p</td><td>854 x 480</td></tr><tr class="even"><td>360p</td><td>640 x 360</td></tr><tr class="odd"><td>240p</td><td>426 x 240</td></tr></tbody></table>

Which one should you use? That depends on your application. For simple embedding you may chose a single resolution. If you're preparing files for DASH or HLS, you may chose one, several, or all. Fortunately, this is one of the simplest transformations you'll make with FFmpeg.

    ffmpeg -i glocken.webm -s 640x360 glocken_640x360.webm

It's worth reiterating that you should start from the highest resolution and bitrate file you have available. If you're upgrading an older site, you'll want to find your original camera or other high resolution sources and convert from that rather than from your older web site files (for example, flv or f4v files).

Now that your files are prepared, it's time to [add them to a web page](/add-media).

<a href="/tags/media/" class="w-chip">Media</a>

<span class="w-mr--sm">Last updated: Aug 27, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/media/resolution/index.md)

<a href="/media" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
