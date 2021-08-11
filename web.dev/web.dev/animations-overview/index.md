





## <a href="#why-are-some-animations-slow" class="w-toc__header--link">Why are some animations slow?</a>

- [Animation performance and frame rate](#fps)
- [The rendering pipeline](#pipeline)
- [Animating layout properties](#layout)
- [Animating paint properties](#paint)
- [Animating composite properties](#composite)
- [What is a layer?](#layers)
- [CSS vs JavaScript performance](#css-js)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Why are some animations slow?

Oct 6, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/animations" class="w-post-signpost__link">Animations</a>

[<img src="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rachel Andrew" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rachelandrew/)

<a href="/authors/rachelandrew/" class="w-author__name-link">Rachel Andrew</a>

- <a href="https://twitter.com/rachelandrew" class="w-author__link">Twitter</a>
- <a href="https://github.com/rachelandrew" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@rachelandrew" class="w-author__link">Glitch</a>
- <a href="https://rachelandrew.co.uk/" class="w-author__link">Blog</a>

Modern browsers can animate two CSS properties cheaply: `transform` and `opacity`. If you animate anything else, the chances are you're not going to hit a silky smooth 60 frames per second (FPS). This post explains why this is the case.

## Animation performance and frame rate <a href="#fps" class="w-headline-link">#</a>

It is widely accepted that a frame rate of 60 FPS is the target when animating anything on the web. This frame rate will ensure that your animations look smooth. On the web a frame is the time that it takes to do all of the work required to update and repaint the screen. If each frame does not complete within 16.7ms (1000ms / 60 ≈ 16.7), then users will perceive the delay.

## The rendering pipeline <a href="#pipeline" class="w-headline-link">#</a>

To display something on a webpage the browser has to go through the following sequential steps:

1.  **Style**: Calculate the styles that apply to the elements.
2.  **Layout**: Generate the geometry and position for each element.
3.  **Paint**: Fill out the pixels for each element into [layers](#layers).
4.  **Composite**: Draw the layers to the screen.

These four steps are known as the browser's **rendering pipeline**.

When you animate something on a page that has already loaded these steps have to happen again. This process begins from the step that has to be changed in order to allow the animation to take place.

As mentioned before, these steps are **sequential**. For example, if you animate something that changes layout, the paint and composite steps also have to run again. Animating something that changes layout is therefore more expensive than animating something that only changes compositing.

For an in-depth look at exactly how this process happens in the browser read [From Braces to Pixels](https://alistapart.com/article/braces-to-pixels/) and [Inside look at modern browser browser](https://developers.google.com/web/updates/2018/09/inside-browser-part3).

### Animating layout properties <a href="#layout" class="w-headline-link">#</a>

Layout changes involve calculating the geometry (position and size) of all the elements affected by the change. If you change one element, the geometry of other elements may need to be recalculated. For example, if you change the width of the `<html>` element any of its children may be affected. Due to the way elements overflow and affect one another, changes further down the tree can sometimes result in layout calculations all the way back up to the top.

The larger the tree of visible elements, the longer it takes to perform layout calculations.

### Animating paint properties <a href="#paint" class="w-headline-link">#</a>

[Paint](https://developers.google.com/web/updates/2018/09/inside-browser-part3#paint) is the process of determining in what order elements should be painted to the screen. It is often the longest-running of all tasks in the pipeline.

The majority of painting in modern browsers is done in [software rasterizers](https://software.intel.com/content/www/us/en/develop/articles/software-vs-gpu-rasterization-in-chromium.html). Depending on how the elements in your app are grouped into layers, other elements besides the one that changed may also need to be painted.

### Animating composite properties <a href="#composite" class="w-headline-link">#</a>

[Compositing](https://developers.google.com/web/updates/2018/09/inside-browser-part3#what_is_compositing) is the process of separating the page into layers, converting the information about how the page should look into pixels (rasterization), and putting the layers together to create a page (compositing).

This is why the `opacity` property is included in the list of things which are cheap to animate. As long as this property is in its own layer, changes to it can be handled by the GPU during the compositing step. Chromium-based browsers and WebKit create a new layer for any element which has a CSS transition or animation on `opacity`.

For an in-depth look at compositing see the article [GPU Animation: Doing It Right](https://www.smashingmagazine.com/2016/12/gpu-animation-doing-it-right/)

## What is a layer? <a href="#layers" class="w-headline-link">#</a>

By placing the things that will be animated or transitioned onto a new layer, the browser only needs to repaint those items and not everything else. You may be familiar with Photoshop's concept of a layer which contains a bunch of elements that can be moved together. Browser rendering layers are similar to that idea.

While the browser does a good job of making decisions about what elements should be on a new layer, if it misses one there are ways to force layer creation. You can find out about that in [How to create high-performance animations](/animations-guide). However, creating new layers should be done with care because each layer uses memory. On devices with limited memory creating new layers may cause more of a performance problem than the one you are trying to solve. In addition, each layer's textures need to be uploaded to the GPU. Therefore you may well hit constraints of bandwidth between the CPU and GPU.

You can read a good explanation of layers, and how to create them in [Layers and how to force them](https://dassur.ma/things/forcing-layers/).

## CSS vs JavaScript performance <a href="#css-js" class="w-headline-link">#</a>

You might wonder: is it better from a performance perspective to use CSS or JavaScript for animations?

CSS-based animations, and [Web Animations](/web-animations/) (in the browsers that support the API), are typically handled on a thread known as the _compositor thread_. This is different from the browser's _main thread_, where styling, layout, painting, and JavaScript are executed. This means that if the browser is running some expensive tasks on the main thread, these animations can keep going without being interrupted.

As explained in this article, other changes to transforms and opacity can, in many cases, also be handled by the compositor thread.

If any animation triggers paint, layout, or both, the main thread will be required to do work. This is true for both CSS and JavaScript animations, and the overhead of layout or paint will likely dwarf any work associated with CSS or JavaScript execution, rendering the question moot.

<a href="/tags/animations/" class="w-chip">Animations</a> <a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Oct 6, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/animations/animations-overview/index.md)

<a href="/animations" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
