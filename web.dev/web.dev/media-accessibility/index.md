## <a href="#media-accessibility" class="w-toc__header--link">Media accessibility</a>

- [Define captions in track file](#define-captions-in-track-file)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Media accessibility

Aug 20, 2020 <span class="w-author__separator">•</span> Updated Aug 27, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/accessible" class="w-post-signpost__link">Accessible to all</a><span class="w-post-signpost__divider">|</span><a href="/media" class="w-post-signpost__link">Media</a>

[<img src="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Joe Medley" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ynJFmvKEbD9diZZsTdkD.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/joemedley/)

<a href="/authors/joemedley/" class="w-author__name-link">Joe Medley</a>

- <a href="https://twitter.com/medleyjp" class="w-author__link">Twitter</a>
- <a href="https://github.com/jpmedley" class="w-author__link">GitHub</a>

Accessibility isn't like icing on a cake. It's never anything you put on a backlog with the hope of introducing it later. Captions and screen reader descriptions are the only way many users can experience your videos, and in some jurisdictions, they're even required by law or regulation.

To add captions or screen reader descriptions to a web video, add a [`<track>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/track) tag to a `<video>` tag. In addition to captions and screen reader descriptions, tags may also be used for subtitles and chapter titles. The can also help search engines understand what's in a video. Those capabilities are outside the scope of this article.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format" alt="Screenshot showing captions displayed using the track element in Chrome on Android" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/vbNDp5R05MwQmsxZ0RLI.jpg?auto=format&amp;w=1600 1600w" width="800" height="480" /><figcaption>Screenshot showing captions displayed using the track element in Chrome on Android</figcaption></figure>An example `<video>` tag with two `<track>` tags is shown below. There's also a sample you can [view on Glitch](https://track-demonstration.glitch.me) ([source](https://glitch.com/edit/#!/track-demonstration)).

To add captions to your video add a track element as a child of the video element:

    <video controls>
      <source src="https://storage.googleapis.com/webfundamentals-assets/videos/chrome.webm" type="video/webm" />
      <source src="https://storage.googleapis.com/webfundamentals-assets/videos/chrome.mp4" type="video/mp4" />
      <track src="chrome-subtitles-en.vtt" label="English captions"
             kind="captions" srclang="en" default>
      <track src="chrome-subtitles-zh.vtt" label="中文字幕"
             kind="captions" srclang="zh">
      <p>This browser does not support the video element.</p>
    </video>

The `<track>` tag is similar to the `<source>` element in that both have a `src` attribute that points to referenced content. For a `<track>` tag, it points to a [WebVTT file](https://developer.mozilla.org/en-US/docs/Web/API/WebVTT_API). The `label` attribute specifies the how a particular track will be identified in the interface. To provide tracks for multiple languages add a separate `<track>` tag for each WebVTT file you're providing and indicate the language using the `srclang` attribute. The `default` attribute indicates which language track is the default.

## Define captions in track file <a href="#define-captions-in-track-file" class="w-headline-link">#</a>

Below is a hypothetical WebVTT file for the demo linked to above. The file is a text file containing a series of _cues_. Each cue is a block of text to display on screen and the time range during which it will be displayed.

    WEBVTT

    00:00.000 --> 00:04.999
    Man sitting on a tree branch, using a laptop.

    00:05.000 --> 00:08.000
    The branch breaks, and he starts to fall.

    ...

Each item in a track file is called a cue. Each cue has a start time and end time separated by an arrow, with cue text in the line below. Cues can optionally also have IDs: `railroad` and `manuscript` in the example below. Cues are separated by an empty line.

    WEBVTT

    railroad
    00:00:10.000 --> 00:00:12.500
    Left uninspired by the crust of railroad earth

    manuscript
    00:00:13.200 --> 00:00:16.900
    that touched the lead to the pages of your manuscript.

Cue times are in hours:minutes:seconds:milliseconds format. Parsing is strict. Numbers must be zero padded if necessary: hours, minutes, and seconds must have two digits (00 for a zero value) and milliseconds must have three digits (000 for zero). There is an excellent WebVTT validator at [Live WebVTT Validator](https://quuz.org/webvtt/), which checks for errors in time formatting, and problems such as non-sequential times.

You can create a VTT file by hand, thought there are [services that will create them for you](https://www.google.com/search?q=webvtt+services).

<a href="/tags/media/" class="w-chip">Media</a> <a href="/tags/accessibility/" class="w-chip">Accessibility</a>

<span class="w-mr--sm">Last updated: Aug 27, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/media/media-accessibility/index.md)

<a href="/accessible" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
