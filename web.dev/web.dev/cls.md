<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#cumulative-layout-shift-(cls)" class="w-toc__header--link">Cumulative Layout Shift (CLS)</a>
------------------------------------------------------------------------------------------------------

-   [What is CLS?](#what-is-cls)
-   [What is a good CLS score?](#what-is-a-good-cls-score)
-   [Layout shifts in detail](#layout-shifts-in-detail)
-   [Layout shift score](#layout-shift-score)
-   [Impact fraction](#impact-fraction)
-   [Distance fraction](#distance-fraction)
-   [Expected vs. unexpected layout shifts](#expected-vs.-unexpected-layout-shifts)
-   [How to measure CLS](#how-to-measure-cls)
-   [Field tools](#field-tools)
-   [Lab tools](#lab-tools)
-   [Measure CLS in JavaScript](#measure-cls-in-javascript)
-   [How to improve CLS](#how-to-improve-cls)
-   [Additional resources](#additional-resources)
-   [CHANGELOG](#changelog)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Cumulative Layout Shift (CLS)
=============================

Jun 11, 2019 <span class="w-author__separator">•</span> Updated Jun 1, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/learn-web-vitals" class="w-post-signpost__link">Web Vitals</a><span class="w-post-signpost__divider">|</span><a href="/metrics" class="w-post-signpost__link">Metrics</a>

[<img src="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Philip Walton" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ovBM8MF9rYDxVVHUVlcG.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/philipwalton/)

<a href="/authors/philipwalton/" class="w-author__name-link">Philip Walton</a>

-   <a href="https://twitter.com/philwalton" class="w-author__link">Twitter</a>
-   <a href="https://github.com/philipwalton" class="w-author__link">GitHub</a>
-   <a href="https://philipwalton.com" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

-   <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
-   <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

**Jun 1, 2021:** The implementation of CLS has changed. To learn more about the reasons behind the change, check out [Evolving the CLS metric](/evolving-cls).

**Key Term**: Cumulative Layout Shift (CLS) is an important, user-centric metric for measuring [visual stability](/user-centric-performance-metrics/#types-of-metrics) because it helps quantify how often users experience unexpected layout shifts—a low CLS helps ensure that the page is [delightful](/user-centric-performance-metrics/#questions).

Have you ever been reading an article online when something suddenly changes on the page? Without warning, the text moves, and you've lost your place. Or even worse: you're about to tap a link or a button, but in the instant before your finger lands—BOOM—the link moves, and you end up clicking something else!

Most of the time these kinds of experiences are just annoying, but in some cases, they can cause real damage.

A screencast illustrating how layout instability can negatively affect users.

Unexpected movement of page content usually happens because resources are loaded asynchronously or DOM elements get dynamically added to the page above existing content. The culprit might be an image or video with unknown dimensions, a font that renders larger or smaller than its fallback, or a third-party ad or widget that dynamically resizes itself.

What makes this issue even more problematic is that how a site functions in development is often quite different from how users experience it. Personalized or third-party content often doesn't behave the same in development as it does in production, test images are often already in the developer's browser cache, and API calls that run locally are often so fast that the delay isn't noticeable.

The Cumulative Layout Shift (CLS) metric helps you address this problem by measuring how often it's occurring for real users.

What is CLS? <a href="#what-is-cls" class="w-headline-link">#</a>
-----------------------------------------------------------------

CLS is a measure of the largest burst of *layout shift scores* for every [unexpected](/cls/#expected-vs.-unexpected-layout-shifts) layout shift that occurs during the entire lifespan of a page.

A *layout shift* occurs any time a visible element changes its position from one rendered frame to the next. (See below for details on how individual [layout shift scores](#layout-shift-score) are calculated.)

A burst of layout shifts, known as a [*session window*](/evolving-cls/#why-a-session-window), is when one or more individual layout shifts occur in rapid succession with less than 1-second in between each shift and a maximum of 5 seconds for the total window duration.

The largest burst is the session window with the maximum cumulative score of all layout shifts within that window.

Example of session windows. Blue bars represent the scores of each individual layout shift.

**Caution**: Previously CLS measured the sum total of *all individual layout shift scores* that occurred during the entire lifespan of the page. To see which tools still provide the ability to benchmark against the original implementation, check out [Evolving Cumulative Layout Shift in web tooling](/cls-web-tooling).

### What is a good CLS score? <a href="#what-is-a-good-cls-score" class="w-headline-link">#</a>

To provide a good user experience, sites should strive to have a CLS score of **0.1** or less. To ensure you're hitting this target for most of your users, a good threshold to measure is the **75th percentile** of page loads, segmented across mobile and desktop devices.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/uqclEgIlTHhwIgNTXN3Y.svg" alt="Good CLS values are under 0.1, poor values are greater than 0.25 and anything in between needs improvement" class="w-screenshot w-screenshot--filled width-full" width="400" height="300" />

To learn more about the research and methodology behind this recommendation, see: [Defining the Core Web Vitals metrics thresholds](/defining-core-web-vitals-thresholds/)

Layout shifts in detail <a href="#layout-shifts-in-detail" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

Layout shifts are defined by the [Layout Instability API](https://github.com/WICG/layout-instability), which reports `layout-shift` entries any time an element that is visible within the viewport changes its start position (for example, its top and left position in the default [writing mode](https://developer.mozilla.org/en-US/docs/Web/CSS/writing-mode)) between two frames. Such elements are considered *unstable elements*.

Note that layout shifts only occur when existing elements change their start position. If a new element is added to the DOM or an existing element changes size, it doesn't count as a layout shift—as long as the change doesn't cause other visible elements to change their start position.

### Layout shift score <a href="#layout-shift-score" class="w-headline-link">#</a>

To calculate the *layout shift score*, the browser looks at the viewport size and the movement of *unstable elements* in the viewport between two rendered frames. The layout shift score is a product of two measures of that movement: the *impact fraction* and the *distance fraction* (both defined below).

    layout shift score = impact fraction * distance fraction

### Impact fraction <a href="#impact-fraction" class="w-headline-link">#</a>

The [impact fraction](https://github.com/WICG/layout-instability#Impact-Fraction) measures how *unstable elements* impact the viewport area between two frames.

The union of the visible areas of all *unstable elements* for the previous frame *and* the current frame—as a fraction of the total area of the viewport—is the *impact fraction* for the current frame.

[<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format" alt="Impact fraction example with one _unstable element_" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format&amp;w=1600 1600w" width="800" height="600" />](https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BbpE9rFQbF8aU6iXN1U6.png?auto=format)

In the image above there's an element that takes up half of the viewport in one frame. Then, in the next frame, the element shifts down by 25% of the viewport height. The red, dotted rectangle indicates the union of the element's visible area in both frames, which, in this case, is 75% of the total viewport, so its *impact fraction* is `0.75`.

### Distance fraction <a href="#distance-fraction" class="w-headline-link">#</a>

The other part of the layout shift score equation measures the distance that unstable elements have moved, relative to the viewport. The *distance fraction* is the greatest distance any *unstable element* has moved in the frame (either horizontally or vertically) divided by the viewport's largest dimension (width or height, whichever is greater).

[<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format" alt="Distance fraction example with one _unstable element_" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format&amp;w=1600 1600w" width="800" height="600" />](https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ASnfpVs2n9winu6mmzdk.png?auto=format)

In the example above, the largest viewport dimension is the height, and the unstable element has moved by 25% of the viewport height, which makes the *distance fraction* 0.25.

So, in this example the *impact fraction* is `0.75` and the *distance fraction* is `0.25`, so the *layout shift score* is `0.75 * 0.25 = 0.1875`.

Initially, the layout shift score was calculated based only on *impact fraction*. The *distance fraction* was introduced to avoid overly penalizing cases where large elements shift by a small amount.

The next example illustrates how adding content to an existing element affects the layout shift score:

[<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format" alt="Layout shift example with stable and _unstable elements_ and viewport clipping" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format&amp;w=1600 1600w" width="800" height="600" />](https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xhN81DazXCs8ZawoCj0T.png?auto=format)

The "Click Me!" button is appended to the bottom of the gray box with black text, which pushes the green box with white text down (and partially out of the viewport).

In this example, the gray box changes size, but its start position does not change so it's not an *unstable element*.

The "Click Me!" button was not previously in the DOM, so its start position doesn't change either.

The start position of the green box, however, does change, but since it's been moved partially out of the viewport, the invisible area is not considered when calculating the *impact fraction*. The union of the visible areas for the green box in both frames (illustrated by the red, dotted rectangle) is the same as the area of the green box in the first frame—50% of the viewport. The *impact fraction* is `0.5`.

The *distance fraction* is illustrated with the purple arrow. The green box has moved down by about 14% of the viewport so the *distance fraction* is `0.14`.

The layout shift score is `0.5 x 0.14 = 0.07`.

This last example illustrates multiple *unstable elements*:

[<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format" alt="Layout shift example with multiple stable and _unstable elements_" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format&amp;w=1600 1600w" width="800" height="600" />](https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FdCETo2dLwGmzw0V5lNT.png?auto=format)

In the first frame above there are four results of an API request for animals, sorted in alphabetical order. In the second frame, more results are added to the sorted list.

The first item in the list ("Cat") does not change its start position between frames, so it's stable. Similarly, the new items added to the list were not previously in the DOM, so their start positions don't change either. But the items labelled "Dog", "Horse", and "Zebra" all shift their start positions, making them *unstable elements*.

Again, the red, dotted rectangles represent the union of these three *unstable elements*' before and after areas, which in this case is around 38% of the viewport's area (*impact fraction* of `0.38`).

The arrows represent the distances that *unstable elements* have moved from their starting positions. The "Zebra" element, represented by the blue arrow, has moved the most, by about 30% of the viewport height. That makes the *distance fraction* in this example `0.3`.

The layout shift score is `0.38 x 0.3 = 0.1172`.

### Expected vs. unexpected layout shifts <a href="#expected-vs.-unexpected-layout-shifts" class="w-headline-link">#</a>

Not all layout shifts are bad. In fact, many dynamic web applications frequently change the start position of elements on the page.

#### User-initiated layout shifts <a href="#user-initiated-layout-shifts" class="w-headline-link">#</a>

A layout shift is only bad if the user isn't expecting it. On the other hand, layout shifts that occur in response to user interactions (clicking a link, pressing a button, typing in a search box and similar) are generally fine, as long as the shift occurs close enough to the interaction that the relationship is clear to the user.

For example, if a user interaction triggers a network request that may take a while to complete, it's best to create some space right away and show a loading indicator to avoid an unpleasant layout shift when the request completes. If the user doesn't realize something is loading, or doesn't have a sense of when the resource will be ready, they may try to click something else while waiting—something that could move out from under them.

Layout shifts that occur within 500 milliseconds of user input will have the [`hadRecentInput`](https://wicg.github.io/layout-instability/#dom-layoutshift-hadrecentinput) flag set, so they can be excluded from calculations.

**Caution**: The `hadRecentInput` flag will only be true for discrete input events like tap, click, or keypress. Continuous interactions such as scrolls, drags, or pinch and zoom gestures are not considered "recent input". See the [Layout Instability Spec](https://github.com/WICG/layout-instability#recent-input-exclusion) for more details.

#### Animations and transitions <a href="#animations-and-transitions" class="w-headline-link">#</a>

Animations and transitions, when done well, are a great way to update content on the page without surprising the user. Content that shifts abruptly and unexpectedly on the page almost always creates a bad user experience. But content that moves gradually and naturally from one position to the next can often help the user better understand what's going on, and guide them between state changes.

Be sure to respect [`prefers-reduced-motion`](/prefers-reduced-motion/) browser settings, as some site visitors can experience ill effects or attention issues from animation.

CSS [`transform`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) property allows you to animate elements without triggering layout shifts:

-   Instead of changing the `height` and `width` properties, use `transform: scale()`.
-   To move elements around, avoid changing the `top`, `right`, `bottom`, or `left` properties and use `transform: translate()` instead.

How to measure CLS <a href="#how-to-measure-cls" class="w-headline-link">#</a>
------------------------------------------------------------------------------

CLS can be measured [in the lab](/user-centric-performance-metrics/#in-the-lab) or [in the field](/user-centric-performance-metrics/#in-the-field), and it's available in the following tools:

**Caution**: Lab tools typically load pages in a synthetic environment and are thus only able to measure layout shifts that occur during page load. As a result, CLS values reported by lab tools for a given page may be less than what real users experience in the field.

### Field tools <a href="#field-tools" class="w-headline-link">#</a>

-   [Chrome User Experience Report](https://developers.google.com/web/tools/chrome-user-experience-report)
-   [PageSpeed Insights](https://developers.google.com/speed/pagespeed/insights/)
-   [Search Console (Core Web Vitals report)](https://support.google.com/webmasters/answer/9205520)
-   [`web-vitals` JavaScript library](https://github.com/GoogleChrome/web-vitals)

### Lab tools <a href="#lab-tools" class="w-headline-link">#</a>

-   [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/)
-   [Lighthouse](https://developers.google.com/web/tools/lighthouse/)
-   [WebPageTest](https://webpagetest.org/)

### Measure CLS in JavaScript <a href="#measure-cls-in-javascript" class="w-headline-link">#</a>

To measure CLS in JavaScript, you can use the [Layout Instability API](https://github.com/WICG/layout-instability). The following example shows how to create a [`PerformanceObserver`](https://developer.mozilla.org/en-US/docs/Web/API/PerformanceObserver) that listens for unexpected `layout-shift` entries, groups them into sessions, and logs the maximum session value any time it changes.

    let clsValue = 0;
    let clsEntries = [];

    let sessionValue = 0;
    let sessionEntries = [];

    new PerformanceObserver((entryList) => {
      for (const entry of entryList.getEntries()) {
        // Only count layout shifts without recent user input.
        if (!entry.hadRecentInput) {
          const firstSessionEntry = sessionEntries[0];
          const lastSessionEntry = sessionEntries[sessionEntries.length - 1];

          // If the entry occurred less than 1 second after the previous entry and
          // less than 5 seconds after the first entry in the session, include the
          // entry in the current session. Otherwise, start a new session.
          if (sessionValue &&
              entry.startTime - lastSessionEntry.startTime < 1000 &&
              entry.startTime - firstSessionEntry.startTime < 5000) {
            sessionValue += entry.value;
            sessionEntries.push(entry);
          } else {
            sessionValue = entry.value;
            sessionEntries = [entry];
          }

          // If the current session value is larger than the current CLS value,
          // update CLS and the entries contributing to it.
          if (sessionValue > clsValue) {
            clsValue = sessionValue;
            clsEntries = sessionEntries;

            // Log the updated value (and its entries) to the console.
            console.log('CLS:', clsValue, clsEntries)
          }
        }
      }
    }).observe({type: 'layout-shift', buffered: true});

**Warning**:

This code shows the basic way to calculate and log CLS. However, accurately measuring CLS in a way that matches what is measured in the [Chrome User Experience Report](https://developers.google.com/web/tools/chrome-user-experience-report) (CrUX) is more complicated. See below for details:

In most cases, the current CLS value at the time the page is being unloaded is the final CLS value for that page, but there are a few important exceptions:

The following section lists the differences between what the API reports and how the metric is calculated.

#### Differences between the metric and the API <a href="#differences-between-the-metric-and-the-api" class="w-headline-link">#</a>

-   If a page is loaded in the background, or if it's backgrounded prior to the browser painting any content, then it should not report any CLS value.
-   If a page is restored from the [back/forward cache](/bfcache/#impact-on-core-web-vitals), its CLS value should be reset to zero since users experience this as a distinct page visit.
-   The API does not report `layout-shift` entries for shifts that occur within iframes, but to properly measure CLS you should consider them. Sub-frames can use the API to report their `layout-shift` entries to the parent frame for [aggregation](https://github.com/WICG/layout-instability#cumulative-scores).

In addition to these exceptions, CLS has some added complexity due to the fact that it measures the entire lifespan of a page:

-   Users might keep a tab open for a *very* long time—days, weeks, months. In fact, a user might never close a tab.
-   On mobile operating systems, browsers typically do not run page unload callbacks for background tabs, making it difficult to report the "final" value.

To handle such cases, CLS should be reported any time a page is background—in addition to any time it's unloaded (the [`visibilitychange` event](https://developers.google.com/web/updates/2018/07/page-lifecycle-api#event-visibilitychange) covers both of these scenarios). And analytics systems receiving this data will then need to calculate the final CLS value on the backend.

Rather than memorizing and grappling with all of these cases yourself, developers can use the [`web-vitals` JavaScript library](https://github.com/GoogleChrome/web-vitals) to measure CLS, which accounts for everything mentioned above:

    import {getCLS} from 'web-vitals';

    // Measure and log CLS in all situations
    // where it needs to be reported.
    getCLS(console.log);

You can refer to [the source code for `getCLS)`](https://github.com/GoogleChrome/web-vitals/blob/master/src/getCLS.ts) for a complete example of how to measure CLS in JavaScript.

In some cases (such as cross-origin iframes) it's not possible to measure CLS in JavaScript. See the [limitations](https://github.com/GoogleChrome/web-vitals#limitations) section of the `web-vitals` library for details.

How to improve CLS <a href="#how-to-improve-cls" class="w-headline-link">#</a>
------------------------------------------------------------------------------

For most websites, you can avoid all unexpected layout shifts by sticking to a few guiding principles:

-   **Always include size attributes on your images and video elements, or otherwise reserve the required space with something like [CSS aspect ratio boxes](https://css-tricks.com/aspect-ratio-boxes/).** This approach ensures that the browser can allocate the correct amount of space in the document while the image is loading. Note that you can also use the [unsized-media feature policy](https://github.com/w3c/webappsec-feature-policy/blob/master/policies/unsized-media.md) to force this behavior in browsers that support feature policies.
-   **Never insert content above existing content, except in response to a user interaction.** This ensures any layout shifts that occur are expected.
-   **Prefer transform animations to animations of properties that trigger layout changes.** Animate transitions in a way that provides context and continuity from state to state.

For a deep dive on how to improve CLS, see [Optimize CLS](/optimize-cls/) and [Debug layout shifts](/debug-layout-shifts) .

Additional resources <a href="#additional-resources" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

-   Google Publisher Tag's guidance on [minimizing layout shift](https://developers.google.com/doubleclick-gpt/guides/minimize-layout-shift)
-   [Understanding Cumulative Layout Shift](https://youtu.be/zIJuY-JCjqw) by [Annie Sullivan](https://anniesullie.com/) and [Steve Kobes](https://kobes.ca/) at [\#PerfMatters](https://perfmattersconf.com/) (2020)

CHANGELOG <a href="#changelog" class="w-headline-link">#</a>
------------------------------------------------------------

Occasionally, bugs are discovered in the APIs used to measure metrics, and sometimes in the definitions of the metrics themselves. As a result, changes must sometimes be made, and these changes can show up as improvements or regressions in your internal reports and dashboards.

To help you manage this, all changes to either the implementation or definition of these metrics will be surfaced in this [CHANGELOG](http://bit.ly/chrome-speed-metrics-changelog).

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/metrics/" class="w-chip">Metrics</a> <a href="/tags/web-vitals/" class="w-chip">Web Vitals</a>

<span class="w-mr--sm">Last updated: Jun 1, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/metrics/cls/index.md)

<a href="/learn-web-vitals" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
