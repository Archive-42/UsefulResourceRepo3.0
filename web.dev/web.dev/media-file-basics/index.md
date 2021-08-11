## <a href="#media-file-basics" class="w-toc__header--link">Media file basics</a>

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Media file basics

Jun 19, 2020 <span class="w-author__separator">•</span> Updated Aug 27, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/media" class="w-post-signpost__link">Media</a>

[<img src="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Joe Medley" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/joemedley/)

<a href="/authors/joemedley/" class="w-author__name-link">Joe Medley</a>

- <a href="https://twitter.com/medleyjp" class="w-author__link">Twitter</a>
- <a href="https://github.com/jpmedley" class="w-author__link">GitHub</a>

You might think that you can take a video camera and upload it to the web as is. Indeed, video streaming sites such as [YouTube](https://www.youtube.com/) or [Vimeo](https://vimeo.com/) let you do this. These sites simplify video processing and uploading for the sake of customer service. Preparing a video for serving from your own site is a bit more complicated.

Video files come in a variety of formats. The format that comes off your camera, typically a `.mov` file, is good for recording and for editing and other early post-production processes. Its size means it's not good for streaming over the web. Because browsers support different file formats, you'll need to create multiple files. Before converting files you need to understand a few basics about them and about their characteristics.

The file that you see in your operating system shell is a _container_, identified by a file extension (`.mp4`, `.webm`, etc.). The container houses one or more _streams_. A media file can have any number of streams, of [more types](https://developer.mozilla.org/en-US/docs/Web/Media/Formats) than I will go into here.

The sample files used later in this section contain at most two streams: an audio stream and a video stream. Among the other types you might encounter are captions and data, both of which are beyond the scope of this article. There are instances where audio and video streams are dealt with separately. Most files you'll encounter will only contain a single audio stream and a single video stream.

Within the audio and video streams, the actual data is compressed using a codec. A _codec_, or coder/decoder, is a compression format for video or audio data. The distinction between a container and a codec is important because files with the same container can have their contents encoded with different codecs.

The image below illustrates this structure. On the left is the basic structure. On the right are the specifics of that structure for a single WebM file.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format" alt="Parts of a media file." sizes="(min-width: 560px) 560px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QwNEBBa8LEMpedJh5imG.png?auto=format&amp;w=1120 1120w" width="560" height="250" /><figcaption>Parts of a media file.</figcaption></figure>Not all browsers support up-to-date containers and codecs. For example, WebM is high-quality and open source. Files in WebM packages can be orders of magnitude smaller than other formats, making them a good choice for mobile download. Although WebM was created specifically for the web, its support is not yet universal. Safari in particular does not, as of this writing, [support](https://caniuse.com/#feat=webm) WebM for embedded video.

All modern browsers support MP4 files, making them a good general choice for a media container and the best choice as the backup container for WebM.

Many file formats support multiple codecs for the same container type. A complete list of available [video codecs](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Video_codecs) and [audio codecs](https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Audio_codecs) would be a whole website itself. The links just provided are for MDN's practical lists of what's usable on the web. Listed below are the currently preferred file types and the codecs they may use. Follow the links for browser support lists.

<table><thead><tr class="header"><th>File type</th><th>Video Codec</th><th>Audio Codec</th></tr></thead><tbody><tr class="odd"><td><a href="https://caniuse.com/#search=mp4">MP4</a></td><td><a href="https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Video_codecs#AV1">AV1</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Video_codecs#AVC_H.264">AVC (H.264)</a>*, <a href="https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Video_codecs#VP9">VP9</a></td><td><a href="https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Audio_codecs#AAC">aac</a></td></tr><tr class="even"><td><a href="https://caniuse.com/#feat=webm">WebM</a></td><td><a href="https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Video_codecs#AV1">AV1</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Video_codecs#VP9">VP9</a>*</td><td><a href="https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Audio_codecs#Vorbis">vorbis</a>, <a href="https://developer.mozilla.org/en-US/docs/Web/Media/Formats/Audio_codecs#Opus">opus</a></td></tr></tbody></table>

\* Indicates the preferred video codec.

_Bitrate_ is the maximum number of bits used to encode one second of a stream. The more bits used to encode a second of stream, the higher the potential detail and fidelity.

_Resolution_ is the amount of information in a single frame of video, given as the number of logical pixels in each dimension. I provide more information about this concept in [Resolution](/resolution).

In [Media application basics](/media-application-basics/), I'll show you how to examine these characteristics using two command line tools: Shaka Packager and FFmpeg.

<a href="/tags/media/" class="w-chip">Media</a>

<span class="w-mr--sm">Last updated: Aug 27, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/media/media-file-basics/index.md)

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
