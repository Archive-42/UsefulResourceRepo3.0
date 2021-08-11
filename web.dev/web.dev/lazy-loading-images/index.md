<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

- [Using browser-level lazy-loading](#images-inline-browser-level)
- [Using Intersection Observer](#images-inline-intersection-observer)
- [Using event handlers for Internet Explorer support](#images-inline-event-handlers)
- [Images in CSS](#images-css)
- [Lazy-loading libraries](#libraries)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Lazy-loading images

Aug 16, 2019 <span class="w-author__separator">•</span> Updated Jun 9, 2020

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

Images can appear on a webpage due to being inline in the HTML as `<img>` elements or as CSS background images. In this post you will find out how to lazy-load both types of image.

## Inline images <a href="#images-inline" class="w-headline-link">#</a>

The most common lazy-loading candidates are images as used in `<img>` elements. With inline images we have three options for lazy-loading, which may be used in combination for the best compatibility across browsers:

- [Using browser-level lazy-loading](#images-inline-browser-level)
- [Using Intersection Observer](#images-inline-intersection-observer)
- [Using scroll and resize event handlers](#images-inline-event-handlers)

### Using browser-level lazy-loading <a href="#images-inline-browser-level" class="w-headline-link">#</a>

Chrome and Firefox both support lazy-loading with the `loading` attribute. This attribute can be added to `<img>` elements, and also to `<iframe>` elements. A value of `lazy` tells the browser to load the image immediately if it is in the viewport, and to fetch other images when the user scrolls near them.

Note `<iframe loading="lazy">` is currently non-standard. While implemented in Chromium, it does not yet have a specification and is subject to future change when this does happen. We suggest not to lazy-load iframes using the `loading` attribute until it becomes part of the specification.

See the `loading` field of MDN's [browser compatibility](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/img#Browser_compatibility) table for details of browser support. If the browser does not support lazy-loading then the attribute will be ignored and images will load immediately, as normal.

For most websites, adding this attribute to inline images will be a performance boost and save users loading images that they may not ever scroll to. If you have large numbers of images and want to be sure that users of browsers without support for lazy-loading benefit you will need to combine this with one of the methods explained next.

To learn more, check out [Browser-level lazy-loading for the web](/browser-level-image-lazy-loading/).

### Using Intersection Observer <a href="#images-inline-intersection-observer" class="w-headline-link">#</a>

To polyfill lazy-loading of `<img>` elements, we use JavaScript to check if they're in the viewport. If they are, their `src` (and sometimes `srcset`) attributes are populated with URLs to the desired image content.

If you've written lazy-loading code before, you may have accomplished your task by using event handlers such as `scroll` or `resize`. While this approach is the most compatible across browsers, modern browsers offer a more performant and efficient way to do the work of checking element visibility via [the Intersection Observer API](https://developers.google.com/web/updates/2016/04/intersectionobserver).

Intersection Observer is not supported in all browsers, notably IE11 and below. If compatibility across browsers is crucial, be sure to read [the next section](#images-inline-event-handlersy), which shows you how to lazy-load images using less performant (but more compatible!) scroll and resize event handlers.

Intersection Observer is easier to use and read than code relying on various event handlers, because you only need to register an observer to watch elements rather than writing tedious element visibility detection code. All that's left to do is to decide what to do when an element is visible. Let's assume this basic markup pattern for your lazily loaded `<img>` elements:

    <img class="lazy" src="placeholder-image.jpg" data-src="image-to-lazy-load-1x.jpg" data-srcset="image-to-lazy-load-2x.jpg 2x, image-to-lazy-load-1x.jpg 1x" alt="I'm an image!">

There are three relevant pieces of this markup that you should focus on:

1.  The `class` attribute, which is what you'll select the element with in JavaScript.
2.  The `src` attribute, which references a placeholder image that will appear when the page first loads.
3.  The `data-src` and `data-srcset` attributes, which are placeholder attributes containing the URL for the image you'll load once the element is in the viewport.

Now let's see how to use Intersection Observer in JavaScript to lazy-load images using this markup pattern:

    document.addEventListener("DOMContentLoaded", function() {
      var lazyImages = [].slice.call(document.querySelectorAll("img.lazy"));

      if ("IntersectionObserver" in window) {
        let lazyImageObserver = new IntersectionObserver(function(entries, observer) {
          entries.forEach(function(entry) {
            if (entry.isIntersecting) {
              let lazyImage = entry.target;
              lazyImage.src = lazyImage.dataset.src;
              lazyImage.srcset = lazyImage.dataset.srcset;
              lazyImage.classList.remove("lazy");
              lazyImageObserver.unobserve(lazyImage);
            }
          });
        });

        lazyImages.forEach(function(lazyImage) {
          lazyImageObserver.observe(lazyImage);
        });
      } else {
        // Possibly fall back to event handlers here
      }
    });

On the document's `DOMContentLoaded` event, this script queries the DOM for all `<img>` elements with a class of `lazy`. If Intersection Observer is available, create a new observer that runs a callback when `img.lazy` elements enter the viewport.

Intersection Observer is available in all modern browsers. Therefore using it as a polyfill for `loading="lazy"` will ensure that lazy-loading is available for most visitors. It is not available in Internet Explorer. If Internet Explorer support is critical, read on.

### Using event handlers for Internet Explorer support <a href="#images-inline-event-handlers" class="w-headline-link">#</a>

While you _should_ use Intersection Observer for lazy-loading, your application requirements may be such that browser compatibility is critical. [You _can_ polyfill Intersection Observer support](https://github.com/w3c/IntersectionObserver/tree/master/polyfill) (and this would be easiest), but you could also fall back to code using [`scroll`](https://developer.mozilla.org/en-US/docs/Web/Events/scroll), [`resize`](https://developer.mozilla.org/en-US/docs/Web/Events/resize), and possibly [`orientationchange`](https://developer.mozilla.org/en-US/docs/Web/Events/orientationchange) event handlers in concert with [`getBoundingClientRect`](https://developer.mozilla.org/en-US/docs/Web/API/Element/getBoundingClientRect) to determine whether an element is in the viewport.

Assuming the same markup pattern from before, this Glitch example uses `getBoundingClientRect` in a `scroll` event handler to check if any of `img.lazy` elements are in the viewport. A `setTimeout` call is used to delay processing, and an `active` variable contains the processing state which is used to throttle function calls. As images are lazy-loaded, they're removed from the elements array. When the elements array reaches a `length` of `0`, the scroll event handler code is removed.

While this code works in pretty much any browser, it has potential performance issues in that repetitive `setTimeout` calls can be wasteful, even if the code within them is throttled. In this example, a check is being run every 200 milliseconds on document scroll or window resize regardless of whether there's an image in the viewport or not. Plus, the tedious work of tracking how many elements are left to lazy-load and unbinding the scroll event handler are left to the developer. You can find out more about this technique in [The Complete Guide to Lazy Loading Images](https://css-tricks.com/the-complete-guide-to-lazy-loading-images/#method-1-trigger-the-image-load-using-javascript-events).

Simply put: Use browser-level lazy-loading with a fallback Intersection Observer implementation wherever possible, and only use event handlers if the widest possible compatibility is a critical application requirement.

## Images in CSS <a href="#images-css" class="w-headline-link">#</a>

While `<img>` tags are the most common way of using images on web pages, images can also be invoked via the CSS [`background-image`](https://developer.mozilla.org/en-US/docs/Web/CSS/background-image) property (and other properties). Browser-level lazy-loading does not apply to CSS background images, so you need to consider other methods if you have background images to lazy-load.

Unlike `<img>` elements which load regardless of their visibility, image loading behavior in CSS is done with more speculation. When [the document and CSS object models](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/constructing-the-object-model) and [render tree](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/render-tree-construction) are built, the browser examines how CSS is applied to a document before requesting external resources. If the browser has determined a CSS rule involving an external resource doesn't apply to the document as it's currently constructed, the browser doesn't request it.

This speculative behavior can be used to defer the loading of images in CSS by using JavaScript to determine when an element is within the viewport, and subsequently applying a class to that element that applies styling invoking a background image. This causes the image to be downloaded at the time of need instead of at initial load. For example, let's take an element that contains a large hero background image:

    <div class="lazy-background">
      <h1>Here's a hero heading to get your attention!</h1>
      <p>Here's hero copy to convince you to buy a thing!</p>
      <a href="/buy-a-thing">Buy a thing!</a>
    </div>

The `div.lazy-background` element would normally contain the hero background image invoked by some CSS. In this lazy-loading example, however, you can isolate the `div.lazy-background` element's `background-image` property via a `visible` class added to the element when it's in the viewport:

    .lazy-background {
      background-image: url("hero-placeholder.jpg"); /* Placeholder image */
    }

    .lazy-background.visible {
      background-image: url("hero.jpg"); /* The final image */
    }

From here, use JavaScript to check if the element is in the viewport (with Intersection Observer!), and add the `visible` class to the `div.lazy-background` element at that time, which loads the image:

    document.addEventListener("DOMContentLoaded", function() {
      var lazyBackgrounds = [].slice.call(document.querySelectorAll(".lazy-background"));

      if ("IntersectionObserver" in window) {
        let lazyBackgroundObserver = new IntersectionObserver(function(entries, observer) {
          entries.forEach(function(entry) {
            if (entry.isIntersecting) {
              entry.target.classList.add("visible");
              lazyBackgroundObserver.unobserve(entry.target);
            }
          });
        });

        lazyBackgrounds.forEach(function(lazyBackground) {
          lazyBackgroundObserver.observe(lazyBackground);
        });
      }
    });

As indicated earlier, if you need Internet Explorer support for lazy-loading of background images, you will need to polyfill the Intersection Observer code, due to lack of support in that browser.

## Lazy-loading libraries <a href="#libraries" class="w-headline-link">#</a>

The following libraries can be used to lazy-load images.

- [lazysizes](https://github.com/aFarkas/lazysizes) is a full-featured lazy loading library that lazy-loads images and iframes. The pattern it uses is quite similar to the code examples shown here in that it automatically binds to a `lazyload` class on `<img>` elements, and requires you to specify image URLs in `data-src` and/or `data-srcset` attributes, the contents of which are swapped into `src` and/or `srcset` attributes, respectively. It uses Intersection Observer (which you can polyfill), and can be extended with [a number of plugins](https://github.com/aFarkas/lazysizes#available-plugins-in-this-repo) to do things like lazy-load video. [Find out more about using lazysizes](/use-lazysizes-to-lazyload-images/).
- [vanilla-lazyload](https://github.com/verlok/vanilla-lazyload) is a lightweight option for lazy-loading images, background images, videos, iframes, and scripts. It leverages Intersection Observer, supports responsive images, and enables browser-level lazy loading.
- [lozad.js](https://github.com/ApoorvSaxena/lozad.js) is a another lightweight option that uses Intersection Observer only. As such, it's highly performant, but will need to be polyfilled before you can use it on older browsers.
- [yall.js](https://github.com/malchata/yall.js) is a library that uses Intersection Observer and falls back to event handlers. It's compatible with IE11 and major browsers.
- If you need a React-specific lazy-loading library, consider [react-lazyload](https://github.com/jasonslyvia/react-lazyload). While it doesn't use Intersection Observer, it _does_ provide a familiar method of lazy loading images for those accustomed to developing applications with React.

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/images/" class="w-chip">Images</a>

<span class="w-mr--sm">Last updated: Jun 9, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/lazy-loading-images/index.md)

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
