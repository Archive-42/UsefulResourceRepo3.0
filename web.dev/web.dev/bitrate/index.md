## <a href="#bitrate" class="w-toc__header--link">Bitrate</a>

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Bitrate

Jun 30, 2017 <span class="w-author__separator">•</span> Updated Aug 27, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/media" class="w-post-signpost__link">Media</a>

[<img src="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Joe Medley" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/joemedley/)

<a href="/authors/joemedley/" class="w-author__name-link">Joe Medley</a>

- <a href="https://twitter.com/medleyjp" class="w-author__link">Twitter</a>
- <a href="https://github.com/jpmedley" class="w-author__link">GitHub</a>

In the [previous section](/containers-and-codecs), I showed you how to change a media file's container and codec. In this section, I show how to change bitrate before explaining [resolution](/resolution) and, finally, [how to embed your file in a page](/add-media).

Bitrate and resolution correlate to the amount of data in a media file. It probably goes without saying, but I'm going to say it anyway. You can always lower bitrate and resolution, but increasing them is a problem. Without special software and algorithms, quality is going to take a hit.

So always start your conversion process with the highest quality source file you can get your hands on. Before doing anything, even before changing the codec or container, [check the file characteristics](/media-cheat-sheet/#display-characteristics) and verify that your source file has a higher bitrate or resolution than your desired result.

_Bitrate_ is the maximum number of bits used to encode one second of a media stream. The more bits used to encode a second of stream, the higher the fidelity.

Unsurprisingly, bitrates the web can handle are low. The table below shows you what bitrate you should target for common network conditions. For the sake of comparison, I've thrown in values for Blu-rays and DVDs.

The web numbers are approximations. This chart should not be a substitute for doing your own testing.

<table><colgroup><col style="width: 50%" /><col style="width: 50%" /></colgroup><thead><tr class="header"><th>Delivery method</th><th>Bitrate</th></tr></thead><tbody><tr class="odd"><td>Blu-ray</td><td>20Mbs</td></tr><tr class="even"><td>DVD</td><td>6 Mbs</td></tr><tr class="odd"><td>Desktop web</td><td>2 Mbs</td></tr><tr class="even"><td>4G mobile</td><td>0.7 Mbs</td></tr><tr class="odd"><td>3G mobile</td><td>0.35 Mbs</td></tr><tr class="even"><td>2G mobile</td><td>Depends on network type.<ul><li>EDGE: 0.4 Mbs</li><li>GPRS: 0.04Mbs</li></ul></td></tr></tbody></table>

Which value should I use for video on my web pages? The short answer is at least: desktop, 4G, and 3G. If you're serving video in one of the markets referred to as "the next billion users", say India, for example, you'll want to include 2G as well. For demonstration purposes, I'm going to target 3G.

In FFmpeg you set the bitrate with the (surprise!) bitrate (`-b`) flag.

    ffmpeg -i glocken.mov -b:v 350k -b:a 64k glocken.mp4

Notice that there are two bitrate flags, `-b:a` and `-b:v`. One is for audio and the other is for video.

Now that your files are prepared, it's time to [adjust their resolutions](/resolution).

<a href="/tags/media/" class="w-chip">Media</a>

<span class="w-mr--sm">Last updated: Aug 27, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/media/bitrate/index.md)

<a href="/media" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
