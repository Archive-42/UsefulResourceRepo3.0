<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>


- [For video acting as an animated GIF replacement](#video-gif-replacement)
- [Lazy-loading libraries](#libraries)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Lazy-loading video

Aug 16, 2019 <span class="w-author__separator">•</span> Updated Jun 5, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeremy Wagner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/VUpz95xT3Znav1EP6ikP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeremywagner/)

<a href="/authors/jeremywagner/" class="w-author__name-link">Jeremy Wagner</a>

- <a href="https://twitter.com/malchata" class="w-author__link">Twitter</a>
- <a href="https://github.com/malchata" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rachel Andrew" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rachelandrew/)

<a href="/authors/rachelandrew/" class="w-author__name-link">Rachel Andrew</a>

- <a href="https://twitter.com/rachelandrew" class="w-author__link">Twitter</a>
- <a href="https://github.com/rachelandrew" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@rachelandrew" class="w-author__link">Glitch</a>
- <a href="https://rachelandrew.co.uk/" class="w-author__link">Blog</a>

As with [image elements](/lazy-loading-images), you can also lazy-load video. Videos are commonly loaded with the `<video>` element (although [an alternate method using `<img>`](https://calendar.perfplanet.com/2017/animated-gif-without-the-gif/) has emerged with limited implementation). _How_ to lazy-load `<video>` depends on the use case, though. Let's discuss a couple of scenarios that each require a different solution.

## For video that doesn't autoplay <a href="#video-no-autoplay" class="w-headline-link">#</a>

For videos where playback is initiated by the user (i.e., videos that _don't_ autoplay), specifying the [`preload` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#attr-preload) on the `<video>` element may be desirable:

    <video controls preload="none" poster="one-does-not-simply-placeholder.jpg">
      <source src="one-does-not-simply.webm" type="video/webm">
      <source src="one-does-not-simply.mp4" type="video/mp4">
    </video>

The example above uses a `preload` attribute with a value of `none` to prevent browsers from preloading _any_ video data. The `poster` attribute gives the `<video>` element a placeholder that will occupy the space while the video loads. The reason for this is that default behaviors for loading video can vary from browser to browser:

- In Chrome, the default for `preload` used to be `auto`, but as of Chrome 64, it now defaults to `metadata`. Even so, on the desktop version of Chrome, a portion of the video may be preloaded using the `Content-Range` header. Firefox, Edge and Internet Explorer 11 behave similarly.
- As with Chrome on desktop, 11.0 desktop versions of Safari will preload a range of the video. From version 11.2, only the video metadata is preloaded. [In Safari on iOS, videos are never preloaded](https://developer.apple.com/library/content/documentation/AudioVideo/Conceptual/Using_HTML5_Audio_Video/AudioandVideoTagBasics/AudioandVideoTagBasics.html#//apple_ref/doc/uid/TP40009523-CH2-SW9).
- When [Data Saver mode](https://support.google.com/chrome/answer/2392284) is enabled, `preload` defaults to `none`.

Because browser default behaviors with regard to `preload` are not set in stone, being explicit is probably your best bet. In this cases where the user initiates playback, using `preload="none"` is the easiest way to defer loading of video on all platforms. The `preload` attribute isn't the only way to defer the loading of video content. [_Fast Playback with Video Preload_](https://developers.google.com/web/fundamentals/media/fast-playback-with-video-preload) may give you some ideas and insight into working with video playback in JavaScript.

Unfortunately, it doesn't prove useful when you want to use video in place of animated GIFs, which is covered next.

## For video acting as an animated GIF replacement <a href="#video-gif-replacement" class="w-headline-link">#</a>

While animated GIFs enjoy wide use, they're subpar to video equivalents in a number of ways, particularly in file size. Animated GIFs can stretch into the range of several megabytes of data. Videos of similar visual quality tend to be far smaller.

Using the `<video>` element as a replacement for animated GIF is not as straightforward as the `<img>` element. Animated GIFs have three characteristics:

1.  They play automatically when loaded.
2.  They loop continuously ([though that's not always the case](https://davidwalsh.name/prevent-gif-loop)).
3.  They don't have an audio track.

Achieving this with the `<video>` element looks something like this:

    <video autoplay muted loop playsinline>
      <source src="one-does-not-simply.webm" type="video/webm">
      <source src="one-does-not-simply.mp4" type="video/mp4">
    </video>

The `autoplay`, `muted`, and `loop` attributes are self-explanatory. [`playsinline` is necessary for autoplaying to occur in iOS](https://webkit.org/blog/6784/new-video-policies-for-ios/). Now you have a serviceable video-as-GIF replacement that works across platforms. But how to go about lazy-loading it? To start, modify your `<video>` markup accordingly:

    <video class="lazy" autoplay muted loop playsinline width="610" height="254" poster="one-does-not-simply.jpg">
      <source data-src="one-does-not-simply.webm" type="video/webm">
      <source data-src="one-does-not-simply.mp4" type="video/mp4">
    </video>

You'll notice the addition of the [`poster` attribute](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/video#attr-poster), which lets you specify a placeholder to occupy the `<video>` element's space until the video is lazy-loaded. As with the [`<img>` lazy-loading examples](/lazy-loading-images/), stash the video URL in the `data-src` attribute on each `<source>` element. From there, use JavaScript code similar to the Intersection Observer-based image lazy-loading examples:

    document.addEventListener("DOMContentLoaded", function() {
      var lazyVideos = [].slice.call(document.querySelectorAll("video.lazy"));

      if ("IntersectionObserver" in window) {
        var lazyVideoObserver = new IntersectionObserver(function(entries, observer) {
          entries.forEach(function(video) {
            if (video.isIntersecting) {
              for (var source in video.target.children) {
                var videoSource = video.target.children[source];
                if (typeof videoSource.tagName === "string" && videoSource.tagName === "SOURCE") {
                  videoSource.src = videoSource.dataset.src;
                }
              }

              video.target.load();
              video.target.classList.remove("lazy");
              lazyVideoObserver.unobserve(video.target);
            }
          });
        });

        lazyVideos.forEach(function(lazyVideo) {
          lazyVideoObserver.observe(lazyVideo);
        });
      }
    });

When you lazy-load a `<video>` element, you need to iterate through all of the child `<source>` elements and flip their `data-src` attributes to `src` attributes. Once you've done that, you need to trigger loading of the video by calling the element's `load` method, after which the media will begin playing automatically per the `autoplay` attribute.

Using this method, you have a video solution that emulates animated GIF behavior, but doesn't incur the same intensive data usage as animated GIFs do, and you can lazy-load that content.

## Lazy-loading libraries <a href="#libraries" class="w-headline-link">#</a>

The following libraries can help you to lazy-load video:

- [lozad.js](https://github.com/ApoorvSaxena/lozad.js) is a super lightweight option that uses Intersection Observer only. As such, it's highly performant, but will need to be polyfilled before you can use it on older browsers.
- [yall.js](https://github.com/malchata/yall.js) is a library that uses Intersection Observer and falls back to event handlers. It's compatible with IE11 and major browsers.
- If you need a React-specific lazy-loading library, you might consider [react-lazyload](https://github.com/jasonslyvia/react-lazyload). While it doesn't use Intersection Observer, it _does_ provide a familiar method of lazy loading images for those accustomed to developing applications with React.

Each of these lazy-loading libraries is well documented, with plenty of markup patterns for your various lazy-loading endeavors.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jun 5, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/lazy-loading-video/index.md)

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
