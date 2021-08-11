## <a href="#prepare-media-files-for-the-web" class="w-toc__header--link">Prepare media files for the web</a>

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Prepare media files for the web

Jun 30, 2017 <span class="w-author__separator">•</span> Updated Aug 27, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/media" class="w-post-signpost__link">Media</a>

[<img src="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Joe Medley" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/joemedley/)

<a href="/authors/joemedley/" class="w-author__name-link">Joe Medley</a>

- <a href="https://twitter.com/medleyjp" class="w-author__link">Twitter</a>
- <a href="https://github.com/jpmedley" class="w-author__link">GitHub</a>

Now that I've introduced you to [applications used for manipulating media files](/media-application-basics), over the next few pages, I'm going to take a raw video file off a camera and transform it into a resource that you can embed in a web page. I'm specifically going to show you how to format your video for mobile playback, and how to create multiple files to cover a range of browsers. Specifically, I'll create a WebM file for use on Chrome and an MP4 file for use on other browsers.

This section provides explanations of file manipulation concepts, with command lines only to illustrate the concepts. There is a companion [cheat sheet](/media-cheat-sheet) that shows more commands and is designed as a quick reference for someone who knows the concepts.

The result of this procedure will be media resources with the following characteristics:

- Versions of a media file in common web-friendly formats containing both audio and video streams.
- A resolution appropriate for your users' devices.
- A bitrate that doesn't overload your users' network bandwidth.
- Viewable on all major browsers using appropriate technologies.

By "appropriate technologies" I mean [Dynamic Adaptive Streaming over HTTP (DASH)](https://developer.mozilla.org/en-US/docs/Web/HTML/DASH_Adaptive_Streaming_for_HTML_5_Video) or [HTTP Live Streaming (HLS)](https://developer.apple.com/documentation/http_live_streaming), which are the two primary means of providing video in HTML on the major browsers. What those terms mean and how to use them is a whole topic itself. I won't be getting into those, and you don't really need to know much about them, but by the end of this article, you'll be able to create media files that are ready for use in DASH and HLS.

One final note: my selection of the file formats, bitrate, and resolution are not arbitrary. I've selected these values for speedy playback on the mobile web.

If you want to play along at home, you'll need a raw video file off a camera, preferably one that contains both audio and video. If you don't have one handy, then here's [ten seconds of an `.mov` file](https://storage.googleapis.com/web-dev-assets/prepare-media/glocken.mov) that I took of the [Rathaus-Glockenspiel](https://en.wikipedia.org/wiki/Rathaus-Glockenspiel) in Munich's MarienPlatz.

Now, let's create a media file using the correct [containers and codecs](/containers-and-codecs).

This section covers four tasks. You will need to do all of them to prepare an `.mov` file for display on the web.

- In [Containers and codecs](/containers-and-codecs) I show you how to convert an `.mov` file to the formats required for web playback.

- In [Bitrate](/bitrate) and [Resolution](/resolution) you'll learn to make your files smaller and hence friendlier for low-bandwidth and mobile download.

After your files are prepared, you'll [add them to a web page](/add-media).

<a href="/tags/media/" class="w-chip">Media</a>

<span class="w-mr--sm">Last updated: Aug 27, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/media/prepare-media/index.md)

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
