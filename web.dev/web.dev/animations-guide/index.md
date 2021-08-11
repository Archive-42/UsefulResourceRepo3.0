<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#how-to-create-high-performance-css-animations" class="w-toc__header--link">How to create high-performance CSS animations</a>
--------------------------------------------------------------------------------------------------------------------------------------

-   [Browser compatibility](#browser-compatibility)
-   [Move an element](#move)
-   [Resize an element](#resize)
-   [Change an element's visibility](#visibility)
-   [Avoid properties that trigger layout or paint](#triggers)
-   [Force layer creation](#force)
-   [Debug slow or janky animations](#debug)
-   [Check if an animation triggers layout](#layout)
-   [Check if an animation is dropping frames](#fps)
-   [Check if an animation triggers paint](#paint)
-   [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

How to create high-performance CSS animations
=============================================

Oct 6, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/animations" class="w-post-signpost__link">Animations</a>

[<img src="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rachel Andrew" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rachelandrew/)

<a href="/authors/rachelandrew/" class="w-author__name-link">Rachel Andrew</a>

-   <a href="https://twitter.com/rachelandrew" class="w-author__link">Twitter</a>
-   <a href="https://github.com/rachelandrew" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@rachelandrew" class="w-author__link">Glitch</a>
-   <a href="https://rachelandrew.co.uk/" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Kayce Basques" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/kaycebasques/)

<a href="/authors/kaycebasques/" class="w-author__name-link">Kayce Basques</a>

-   <a href="https://twitter.com/kaycebasques" class="w-author__link">Twitter</a>
-   <a href="https://github.com/kaycebasques" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@kaycebasques" class="w-author__link">Glitch</a>
-   <a href="https://kayce.basqu.es/" class="w-author__link">Blog</a>

This guide teaches you how to create high-performance CSS animations.

See [Why are some animations slow?](/animations-overview/) to learn the theory behind these recommendations.

Browser compatibility <a href="#browser-compatibility" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

All of the CSS properties that this guide recommends have good cross-browser support.

-   [`transform`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform#Browser_compatibility)
-   [`opacity`](https://developer.mozilla.org/en-US/docs/Web/CSS/opacity#Browser_compatibility)
-   [`will-change`](https://developer.mozilla.org/en-US/docs/Web/CSS/will-change#Browser_compatibility)

Move an element <a href="#move" class="w-headline-link">#</a>
-------------------------------------------------------------

To move an element, use the `translate` or `rotation` keyword values of the [`transform`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) property.

For example to slide an item into view, use `translate`.

    .animate {
      animation: slide-in 0.7s both;
    }

    @keyframes slide-in {
      0% {
        transform: translateY(-1000px);
      }
      100% {
        transform: translateY(0);
      }
    }

Items can also be rotated, in the example below 360 degrees.

    .animate {
      animation: rotate 0.7s ease-in-out both;
    }

    @keyframes rotate {
      0% {
        transform: rotate(0);
      }
      100% {
        transform: rotate(360deg);
      }
    }

Resize an element <a href="#resize" class="w-headline-link">#</a>
-----------------------------------------------------------------

To resize an element, use the `scale` keyword value of the [`transform`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) property.

    .animate {
      animation: scale 1.5s both;
    }

    @keyframes scale {
      50% {
        transform: scale(0.5);
      }
      100% {
        transform: scale(1);
      }
    }

Change an element's visibility <a href="#visibility" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

To show or hide an element, use [`opacity`](https://developer.mozilla.org/en-US/docs/Web/CSS/opacity).

    .animate {
      animation: opacity 2.5s both;
    }

    @keyframes opacity {
      0% {
        opacity: 1;
      }
      50% {
        opacity: 0;
      }
      100% {
        opacity: 1;
      }
    }

Find copy and paste examples of various animations at [Animista](https://animista.net/).

Avoid properties that trigger layout or paint <a href="#triggers" class="w-headline-link">#</a>
-----------------------------------------------------------------------------------------------

Before using any CSS property for animation (other than `transform` and `opacity`), go to [CSS Triggers](https://csstriggers.com/) to determine the property's impact on the [rendering pipeline](/animations-overview/#pipeline). Avoid any property that triggers layout or paint unless absolutely necessary.

<figure><img src="https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/lo6imreXGzuZzsHVWUFf.jpg?auto=format&amp;w=1600 1600w" width="800" height="432" /></figure>**Warning**: If you must use a property that triggers layout or paint, it is unlikely that you will be able to make the animation smooth and high-performance.

Force layer creation <a href="#force" class="w-headline-link">#</a>
-------------------------------------------------------------------

As explained in [Why are some animations slow?](/animations-overview), by placing elements on a new layer they can be repainted without also requiring the rest of the layout to be repainted.

Browsers will often make good decisions about which items should be placed on a new layer, but you can manually force layer creation with the [`will-change`](https://developer.mozilla.org/en-US/docs/Web/CSS/will-change) property. As the name suggests, this property tells the browser that this element is going to be changed in some way.

**Caution**: As layer creation can cause other performance issues, this property should not be used as a premature optimization. Instead, you should only use it when you are seeing jank and think that promoting the element to a new layer may help.

In CSS this property can be applied to any selector:

    body > .sidebar {
      will-change: transform;
    }

However, [the specification](https://drafts.csswg.org/css-will-change/) suggests this approach should only be taken for elements that are always about to change. If the above example was a sidebar the user could slide in and out, that might be the case. Some items on your page may not frequently change, and so it would be better to apply `will-change` using JavaScript at a point where it becomes likely the change will occur. You'll need to make sure to give the browser enough time to perform the optimizations needed and then remove the property once the changing has stopped.

For more information and examples of correct use of `will-change` read [Everything You Need To Know About The CSS `will-change` Property](https://dev.opera.com/articles/css-will-change-property/).

If you need a way to force layer creation in one of the rare browsers that doesn't support `will-change` (most likely Internet Explorer at this point), you can set `transform: translateZ(0)`.

Debug slow or janky animations <a href="#debug" class="w-headline-link">#</a>
-----------------------------------------------------------------------------

Chrome DevTools and Firefox DevTools have lots of tools to help you figure out why your animations are slow or janky.

### Check if an animation triggers layout <a href="#layout" class="w-headline-link">#</a>

An animation that moves an element using something other than `transform`, is likely to be slow. In the following example, I have achieved the same visual result animating `top` and `left`, and using `transform`.

Don't

    .box {
      position: absolute;
      top: 10px;
      left: 10px;
      animation: move 3s ease infinite;
    }

    @keyframes move {
      50% {
         top: calc(90vh - 160px);
         left: calc(90vw - 200px);
      }
    }

Do

    .box {
      position: absolute;
      top: 10px;
      left: 10px;
      animation: move 3s ease infinite;
    }

    @keyframes move {
      50% {
         transform: translate(calc(90vw - 200px), calc(90vh - 160px));
      }
    }

You can test this in the following two Glitch examples, and explore performance using DevTools.

-   [Before](https://glitch.com/~animation-with-top-left).
-   [After](https://glitch.com/~animation-with-transform).

#### Chrome DevTools <a href="#layout-chrome" class="w-headline-link">#</a>

1.  Open the **Performance** panel.
2.  [Record runtime performance](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#record-runtime) while your animation is happening.
3.  Inspect the **Summary** tab.

If you see a nonzero value for **Rendering** in the **Summary** tab, it may mean that your animation is causing the browser to do layout work.

<figure><img src="https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format" alt="The animation-with-top-left example causes rendering work." class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/cMNQR2jBEwa6ku5POXtZ.jpg?auto=format&amp;w=1600 1600w" width="800" height="699" /><figcaption>The <a href="https://animation-with-top-left.glitch.me/">animation-with-top-left</a> example causes rendering work.</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format" alt="The animation-with-transform example does not cause rendering work." class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/3bn44P9h6lR93uBNRXY3.jpg?auto=format&amp;w=1600 1600w" width="800" height="639" /><figcaption>The <a href="https://animation-with-transform.glitch.me/">animation-with-transform</a> example does not cause rendering work.</figcaption></figure>#### Firefox DevTools <a href="#layout-firefox" class="w-headline-link">#</a>

In Firefox DevTools the [Waterfall](https://developer.mozilla.org/en-US/docs/Tools/Performance/Waterfall) can help you to understand where the browser is spending time.

1.  Open the **Performance** panel.
2.  In the panel Start Recording Performance while your animation is happening.
3.  Stop the recording and inspect the **Waterfall** tab.

If you see entries for [**Recalculate Style**](https://developer.mozilla.org/en-US/docs/Tools/Performance/Scenarios/Animating_CSS_properties) then the browser is having to begin at the start of the [rendering waterfall](https://developer.mozilla.org/en-US/docs/Tools/Performance/Scenarios/Animating_CSS_properties).

<figure><img src="waterfall-before.jpg" alt="The animation-with-top-left example causes style recalculation." class="w-screenshot w-screenshot--filled" /><figcaption>The <a href="https://animation-with-top-left.glitch.me/">animation-with-top-left</a> example causes style recalculation.</figcaption></figure><figure><img src="waterfall-after.jpg" alt="The animation-with-transform example does not cause style recalculation." class="w-screenshot w-screenshot--filled" /><figcaption>The <a href="https://animation-with-transform.glitch.me/">animation-with-transform</a> example does not cause style recalculation.</figcaption></figure>### Check if an animation is dropping frames <a href="#fps" class="w-headline-link">#</a>

1.  Open the [**Rendering** tab](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#rendering) of Chrome DevTools.
2.  Enable the **FPS meter** checkbox.
3.  Watch the values as your animation runs.

At the top of the **FPS meter** UI you see the label **Frames**. Below that you see a value along the lines of `50% 1 (938 m) dropped of 1878`. A high-performance animation will have a high percentage, e.g. `99%`. A high percentage means that few frames are being dropped and the animation will look smooth.

<figure><img src="https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format" alt="The animation-with-top-left example causes 50% of frames to be dropped" class="w-screenshot w-screenshot--filled" sizes="(min-width: 710px) 710px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/i9Cg7nswyO7jB768kpdQ.jpg?auto=format&amp;w=1420 1420w" width="710" height="469" /><figcaption>The <a href="https://animation-with-top-left.glitch.me/">animation-with-top-left</a> example causes 50% of frames to be dropped</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format" alt="The animation-with-transform example causes only 1% of frames to be dropped." class="w-screenshot w-screenshot--filled" sizes="(min-width: 710px) 710px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/FGROZ0i15tCAoiIOoEdG.jpg?auto=format&amp;w=1420 1420w" width="710" height="468" /><figcaption>The <a href="https://animation-with-transform.glitch.me/">animation-with-transform</a> example causes only 1% of frames to be dropped.</figcaption></figure>### Check if an animation triggers paint <a href="#paint" class="w-headline-link">#</a>

When it comes to painting, some things are more expensive than others. For example, anything that involves a blur (like a shadow, for example) is going to take longer to paint than drawing a red box. In terms of CSS, however, this isn't always obvious: `background: red;` and `box-shadow: 0, 4px, 4px, rgba(0,0,0,0.5);` don't necessarily look like they have vastly different performance characteristics, but they do.

Browser DevTools can help you to identify which areas need to be repainted, and performance issues related to painting.

#### Chrome DevTools <a href="#paint-chrome" class="w-headline-link">#</a>

1.  Open the [**Rendering** tab](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#rendering) of Chrome DevTools.
2.  Select **Paint Flashing**.
3.  Move the pointer around the screen.

<figure><img src="https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format" alt="In this example from Google Maps you can see the elements that will be repainted." class="w-screenshot" sizes="(min-width: 708px) 708px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/MzAeQc5PvCltcm3gWaNV.jpg?auto=format&amp;w=1416 1416w" width="708" height="185" /><figcaption>In this example from Google Maps you can see the elements that will be repainted.</figcaption></figure>If you see the whole screen flashing, or areas that you don't think should change highlighted then you can do some investigation.

If you need to dig into whether a particular property is causing performance issues due to painting, the [paint profiler](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference#paint-profiler) in Chrome DevTools can help.

#### Firefox DevTools <a href="#paint-firefox" class="w-headline-link">#</a>

1.  Open **Settings** and add a Toolbox button for [Toggle paint flashing](https://developer.mozilla.org/en-US/docs/Tools/Paint_Flashing_Tool).
2.  On the page you want to inspect, toggle the button on and move your mouse or scroll to see highlighted areas.

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

Where possible restrict animations to `opacity` and `transform` in order to keep animations on the compositing stage of the rendering path. Use DevTools to check which stage of the path is being affected by your animations.

Use the paint profiler to see if any paint operations are particularly expensive. If you find anything, see if a different CSS property will give the same look and feel with better performance.

Use the `will-change` property sparingly, and only if you encounter a performance issue.

<a href="/tags/animations/" class="w-chip">Animations</a> <a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Oct 6, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/animations/animations-guide/index.md)

<a href="/animations" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
