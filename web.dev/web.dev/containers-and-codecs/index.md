<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#containers-and-codecs" class="w-toc__header--link">Containers and codecs</a>
--------------------------------------------------------------------------------------

-   [Check your work](#check-your-work)
-   [Codecs](#codecs)
-   [Video](#video)
-   [Audio](#audio)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Containers and codecs
=====================

Jun 30, 2017 <span class="w-author__separator">•</span> Updated Sep 24, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/media" class="w-post-signpost__link">Media</a>

[<img src="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Joe Medley" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/joemedley/)

<a href="/authors/joemedley/" class="w-author__name-link">Joe Medley</a>

-   <a href="https://twitter.com/medleyjp" class="w-author__link">Twitter</a>
-   <a href="https://github.com/jpmedley" class="w-author__link">GitHub</a>

To support multiple browsers, you'll need to use FFmpeg to convert your mov file to two different containers: an MP4 container and a WebM container. In actual practice, you would likely specify a codec at the same time. For now, I'm letting FFmpeg use its defaults.

To create the MP4:

    ffmpeg -i glocken.mov glocken.mp4

To create the WebM:

    ffmpeg -i glocken.mov glocken.webm

To create this article, I used FFmpeg version 4.2.2-tessus. If the command lines don't work for your version of FFmpeg, consult the FFmpeg documentation.

Webm takes longer to create than MP4. This isn't surprising when you look at the results. While MP4 compresses to about two-thirds of the original file's size, WebM is down to a mere fraction of the original's size. Though, your results may vary. You can see this for yourself using the [`ls -a` bash command](https://www.tecmint.com/15-basic-ls-command-examples-in-linux/) in the folder where your media files are located. For example:

    -rw-r--r-- 1 jmedley  eng  12080306 Apr 21 13:13 glocken.mov
    -rw-r--r-- 1 jmedley  eng  10146121 Apr 21 13:25 glocken.mp4
    -rw-r--r-- 1 jmedley  eng    491743 Apr 21 13:30 glocken.webm

Check your work <a href="#check-your-work" class="w-headline-link">#</a>
------------------------------------------------------------------------

To verify your results, use FFmpeg and Shaka Packager as already shown in [Media Application basics](/media-application-basics):

    packager input=glocken.mp4 --dump_stream_info

    ffmpeg -i glocken.mp4

Codecs <a href="#codecs" class="w-headline-link">#</a>
------------------------------------------------------

Next the codec. As stated in [Media file basics](/media-file-basics), a codec is *not* the same thing as a container (file type). Two files of the same container type could hold data compressed using different codecs. The WebM format for example allows audio to be encoded using either [vorbis](https://en.wikipedia.org/wiki/Vorbis) or [opus](https://en.wikipedia.org/wiki/Opus_(audio_format)). To change the codec I use FFmpeg. For example, this command outputs an mkv file with a vorbis audio codec and an av1 video codec.

    ffmpeg -i glocken.mov -c:a vorbis -c:v av1 glocken.mkv

In this example, the `-c:a` flag and the `-c:v` are for specifying the audio and video codecs respectively.

The [cheat sheet](/media-cheat-sheet#codec) lists commands needed to convert codecs. The tables below summarize the libraries used in FFmpeg to perform the codec conversions for WebM and MP4 files. These are the formats recommended for DASH and HLS respectively.

Video <a href="#video" class="w-headline-link">#</a>
----------------------------------------------------

<table><thead><tr class="header"><th>Codec</th><th>Extension</th><th>Library</th></tr></thead><tbody><tr class="odd"><td>av1</td><td>WebM<br />
mkv</td><td>libaom-av1</td></tr><tr class="even"><td>h264</td><td>MP4</td><td>libx264</td></tr><tr class="odd"><td>vp9</td><td>WebM</td><td>libvpx-vp9</td></tr></tbody></table>

Audio <a href="#audio" class="w-headline-link">#</a>
----------------------------------------------------

<table><thead><tr class="header"><th>Codec</th><th>Extension</th><th>Library</th></tr></thead><tbody><tr class="odd"><td>aac</td><td>MP4</td><td>aac</td></tr><tr class="even"><td>opus</td><td>WebM</td><td>libopus</td></tr><tr class="odd"><td>vorbis</td><td>WebM</td><td>libvorbis</td></tr></tbody></table>

Next, I'll show you how to change the file's [bitrate](/bitrate).

<a href="/tags/media/" class="w-chip">Media</a>

<span class="w-mr--sm">Last updated: Sep 24, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/media/containers-and-codecs/index.md)

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
