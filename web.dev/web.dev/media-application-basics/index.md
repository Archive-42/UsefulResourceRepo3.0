## <a href="#media-application-basics" class="w-toc__header--link">Media application basics</a>

- [Shaka Packager](#shaka-packager)
- [FFmpeg](#ffmpeg)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Media application basics

Jun 9, 2017 <span class="w-author__separator">•</span> Updated Sep 24, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/media" class="w-post-signpost__link">Media</a>

[<img src="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Joe Medley" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/joemedley/)

<a href="/authors/joemedley/" class="w-author__name-link">Joe Medley</a>

- <a href="https://twitter.com/medleyjp" class="w-author__link">Twitter</a>
- <a href="https://github.com/jpmedley" class="w-author__link">GitHub</a>

Much media work requires changing characteristics of media files, such as bitrate or resolution. Finding a straightforward way to get started can be bewildering and intimidating. On this page, I provide an onramp into that world.

You'll notice in what follows that the word 'resolution' doesn't appear. What the two applications output are just the dimensions, the numbers themselves. That's because resolution is just an informal shorthand for the dimensions of a video. In every case that follows, I talk about specific numbers.

This page describes the basic usage for two common command-line media utilities: [Shaka Packager](https://github.com/google/shaka-packager) and [FFmpeg](https://ffmpeg.org/download.html). Why cover two applications? While both are powerful and useful by themselves, neither does everything needed to prepare media for the web. I've also created a [cheat sheet](/media-cheat-sheet) showing common operations with those applications.

These aren't the only options available for many file manipulation tasks. But they are two of the most common and powerful. Other options include the GUI applications [Miro](http://www.mirovideoconverter.com/), [HandBrake](//handbrake.fr/), and [VLC](//www.videolan.org/). There are also online encoding/transcoding services such as [Zencoder](//en.wikipedia.org/wiki/Zencoder) and [Amazon Elastic Encoder](//aws.amazon.com/elastictranscoder).

## Shaka Packager <a href="#shaka-packager" class="w-headline-link">#</a>

[Shaka Packager](https://github.com/google/shaka-packager) is a free media packaging SDK. If you were using a media player on your site, Shaka Packager is what you would use to prepare the files. It supports conversion for the two most common video streaming protocols: [Dynamic Adaptive Streaming over HTTP (DASH)](https://developer.mozilla.org/en-US/docs/Web/HTML/DASH_Adaptive_Streaming_for_HTML_5_Video) or [HTTP Live Streaming (HLS)](https://developer.apple.com/documentation/http_live_streaming). Shaka Packager supports key security features: common encryption and Widevine digital rights management (DRM). It can also handle live video, and video-on-demand. Those concepts are beyond the scope of this article.

Despite what it says on the package, this utility is for more than C++ developers. You can use it as both a library for building media software and as a command-line utility for preparing media files for playback. It's the latter capacity that's useful for us here. In fact, for web media creators, Shaka Packager is the only way to do some tasks without spending money on expensive commercial applications.

Here's the basic pattern for a Shaka Packager command:

    packager stream_descriptor [stream_descriptor-2 [stream_descriptor-n]] [flags]

This isn't quite what you get if you type `packager -help`. This is how I think of it, and this reflects the examples in the [Shaka Packager documentation](https://google.github.io/shaka-packager/html/). Note that there are multiple `stream_descriptor` items in the pattern. Though I don't show it, you could manipulate the video and audio streams of a file directly.

Compare this basic pattern with a simple use that displays file characteristics. In the example, I've lined up equivalent parts.

    packager stream_descriptor [stream_descriptor-n] [flags]

    packager input=glocken.mp4                       --dump_stream_info

The command outputs this:

    [0416/140029:INFO:demuxer.cc(88)] Demuxer::Run() on file 'glocken.mp4'.
    [0416/140029:INFO:demuxer.cc(160)] Initialize Demuxer for file 'glocken.mp4'.

    File "glocken.mp4":
    Found 2 stream(s).
    Stream [0] type: Video
     codec_string: avc1.640028
     time_scale: 30000
     duration: 300300 (10.0 seconds)
     is_encrypted: false
     codec: H264
     width: 1920
     height: 1080
     pixel_aspect_ratio: 1:1
     trick_play_factor: 0
     nalu_length_size: 4

    Stream [1] type: Audio
     codec_string: mp4a.40.2
     time_scale: 48000
     duration: 481280 (10.0 seconds)
     is_encrypted: false
     codec: AAC
     sample_bits: 16
     num_channels: 2
     sampling_frequency: 48000
     language: eng
     seek_preroll_ns: 20833

    Packaging completed successfully.

Look for the characteristics discussed in [Media file basics](/media-file-basics) and notice a few things. The height and width are correct for full HD, and the audio and video codecs are among the preferred codecs for their container types, AAC for audio and H264 for video. Notice also that streams are identified with numbers. These are useful for operations that manipulate the audio and video separately.

Notice that the output above doesn't show the bitrate. Despite what's missing, this output is easier to read, so I use it whenever I can. When I need information that Shaka Packager can't get, such as the bitrate, I use FFmpeg.

## FFmpeg <a href="#ffmpeg" class="w-headline-link">#</a>

[FFmpeg](https://ffmpeg.org/download.html) is also a free application for recording, converting, and streaming media files. Its capabilities aren't better or worse than Shaka Packager's. They're just different.

The basic pattern for an FFmpeg command looks like this:

    ffmpeg [GeneralOptions] [InputFileOptions] -i input [OutputFileOptions] output

Like Shaka Packager this application can handle multiple streams. Some of its options are used in multiple locations and have different effects on file output depending on where they are in the command. Be aware of this as you look at [FFmpeg questions on Stack Overflow](https://stackoverflow.com/questions/tagged/ffmpeg) and similar sites.

I'll again compare the basic pattern to the example for displaying file characteristics.

        ffmpeg [GeneralOptions] [InputFileOptions] -i input        [OutputFileOptions] output

        ffmpeg                                     -i glocken.mp4

In addition to the information I requested, this also prints an error message as shown in the example below. That's because this is technically an incorrect usage of FFmpeg. I use it because it displays information I care about.

    Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'glocken.mp4':
      Metadata:
        major_brand     : isom
        minor_version   : 512
        compatible_brands: isomiso2avc1mp41
        encoder         : Lavf58.17.100
      Duration: 00:01:47.53, start: 0.000000, bitrate: 10715 kb/s
        Stream #0:0(eng): Video: h264 (High) (avc1 / 0x31637661), yuvj420p(pc), 1920x1080, 10579 kb/s, 29.97 fps, 29.97 tbr, 30k tbn, 59.94 tbc (default)
        Metadata:
          handler_name    : VideoHandler
        Stream #0:1(eng): Audio: aac (LC) (mp4a / 0x6134706D), 48000 Hz, stereo, fltp, 128 kb/s (default)
        Metadata:
          handler_name    : SoundHandler
    At least one output file must be specified

Now that you've tried your hand at using Shaka and FFmpeg, it's time to [Prepare media files for the web](/prepare-media).

<a href="/tags/media/" class="w-chip">Media</a>

<span class="w-mr--sm">Last updated: Sep 24, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/media/media-application-basics/index.md)

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
