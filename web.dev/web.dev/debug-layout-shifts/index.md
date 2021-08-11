





<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format" alt="Picture of a layout shift." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/N65l8ccOUEDESpnnEkje.png?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#debug-layout-shifts" class="w-toc__header--link">Debug layout shifts</a>

- [Tooling](#tooling)
- [Layout Instability API](#layout-instability-api)
- [DevTools](#devtools)
- [Thought process for identifying the cause of layout shifts](#thought-process-for-identifying-the-cause-of-layout-shifts)
- [Identifying the cause of a layout shift](#identifying-the-cause-of-a-layout-shift)
- [Reproducing layout shifts](#reproducing-layout-shifts)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Debug layout shifts

Learn how to identify and fix layout shifts.

Mar 11, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/learn-web-vitals" class="w-post-signpost__link">Web Vitals</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

- <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
- <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
- <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

The first part of this article discusses tooling for debugging layout shifts, while the second part discusses the thought process to use when identifying the cause of a layout shift.

## Tooling <a href="#tooling" class="w-headline-link">#</a>

### Layout Instability API <a href="#layout-instability-api" class="w-headline-link">#</a>

The [Layout Instability API](https://wicg.github.io/layout-instability/) is the browser mechanism for measuring and reporting layout shifts. All tools for debugging layout shifts, including DevTools, are ultimately built upon the Layout Instability API. However, using the Layout Instability API directly is a powerful debugging tool due to its flexibility.

The Layout Instability API is only [supported](https://caniuse.com/mdn-api_layoutshift) by Chromium browsers. At the current time there is no way to measure or debug layout shifts in non-Chromium browsers.

#### Usage <a href="#usage" class="w-headline-link">#</a>

The same code [snippet](/cls/#measure-cls-in-javascript) that measures [Cumulative Layout Shift (CLS)](/cls/) can also serve to debug layout shifts. The snippet below logs information about layout shifts to the console. Inspecting this log will provide you information about when, where, and how a layout shift occurred.

    let cls = 0;
    new PerformanceObserver((entryList) => {
      for (const entry of entryList.getEntries()) {
        if (!entry.hadRecentInput) {
          cls += entry.value;
          console.log('Current CLS value:', cls, entry);
        }
      }
    }).observe({type: 'layout-shift', buffered: true});

When running this script be aware that:

- The `buffered: true` option indicates that the [`PerformanceObserver`](https://developer.mozilla.org/en-US/docs/Web/API/PerformanceObserver) should check the browser's [performance entry buffer](https://www.w3.org/TR/performance-timeline-2/#dfn-performance-entry-buffer) for performance entries that were created before the observer's initialization. As a result, the `PerformanceObserver` will report layout shifts that happened both before and after it was initialized. Keep this in mind when inspecting the console logs. An initial glut of layout shifts can reflect a reporting backlog, rather than the sudden occurrence of numerous layout shifts.
- To avoid impacting performance, the `PerformanceObserver` waits until the main thread is idle to report on layout shifts. As a result, depending on how busy the main thread is, there may be a slight delay between when a layout shift occurs and when it is logged in the console.
- This script ignores layout shifts that occurred within 500 ms of user input and therefore do not count towards CLS.

Information about layout shifts is reported using a combination of two APIs: the [`LayoutShift`](https://wicg.github.io/layout-instability/#layoutshift) and [`LayoutShiftAttribution`](https://wicg.github.io/layout-instability/#sec-layout-shift-attribution) interfaces. Each of these interfaces are explained in more detail in the following sections.

#### LayoutShift <a href="#layoutshift" class="w-headline-link">#</a>

Each layout shift is reported using the `LayoutShift` interface. The contents of an entry look like this:

    duration: 0
    entryType: "layout-shift"
    hadRecentInput: false
    lastInputTime: 0
    name: ""
    sources: (3) [LayoutShiftAttribution, LayoutShiftAttribution, LayoutShiftAttribution]
    startTime: 11317.934999999125
    value: 0.17508567530168798

The entry above indicates a layout shift during which three DOM elements changed position. The layout shift score of this particular layout shift was `0.175`.

These are the properties of a `LayoutShift` instance that are most relevant to debugging layout shifts:

<table><thead><tr class="header"><th>Property</th><th>Description</th></tr></thead><tbody><tr class="odd"><td><code>sources</code></td><td>The <code>sources</code> property lists the DOM elements that moved during the layout shift. This array can contain up to five sources. In the event that there are more than five elements impacted by the layout shift, the five largest (as measured by impact on layout stability) sources of layout shift are reported. This information is reported using the LayoutShiftAttribution interface (explained in more detail below).</td></tr><tr class="even"><td><code>value</code></td><td>The <code>value</code> property reports the <a href="/cls/#layout-shift-score">layout shift score</a> for a particular layout shift.</td></tr><tr class="odd"><td><code>hadRecentInput</code></td><td>The <code>hadRecentInput</code> property indicates whether a layout shift occurred within 500 milliseconds of user input.</td></tr><tr class="even"><td><code>startTime</code></td><td>The <code>startTime</code> property indicates when a layout shift occurred. <code>startTime</code> is indicated in milliseconds and is measured relative to the <a href="https://www.w3.org/TR/hr-time-2/#sec-time-origin">time that the page load was initiated</a>.</td></tr><tr class="odd"><td><code>duration</code></td><td>The <code>duration</code> property will always be set to <code>0</code>. This property is inherited from the <a href="https://developer.mozilla.org/en-US/docs/Web/API/PerformanceEntry"><code>PerformanceEntry</code></a> interface (the <code>LayoutShift</code> interface extends the <code>PerformanceEntry</code> interface). However, the concept of duration does not apply to layout shift events, so it is set to <code>0</code>. For information on the <code>PerformanceEntry</code> interface, refer to the <a href="https://w3c.github.io/performance-timeline/#the-performanceentry-interface">spec</a>.</td></tr></tbody></table>

The [Web Vitals Extension](https://chrome.google.com/webstore/detail/web-vitals/ahfhijdlegdabablpippeagghigmibma) can log layout shift info to the console. To enable this feature, go to **Options &gt; Console Logging**.

#### LayoutShiftAttribution <a href="#layoutshiftattribution" class="w-headline-link">#</a>

The `LayoutShiftAttribution` interface describes a single shift of a single DOM element. If multiple elements shift during a layout shift, the `sources` property contains multiple entries.

For example, the JSON below corresponds to a layout shift with one source: the downward shift of the `<div id='banner'>` DOM element from `y: 76` to `y:246`.

    // ...
      "sources": [
        {
          "node": "div#banner",
          "previousRect": {
            "x": 311,
            "y": 76,
            "width": 4,
            "height": 18,
            "top": 76,
            "right": 315,
            "bottom": 94,
            "left": 311
          },
          "currentRect": {
            "x": 311,
            "y": 246,
            "width": 4,
            "height": 18,
            "top": 246,
            "right": 315,
            "bottom": 264,
            "left": 311
          }
        }
      ]

The `node` property identifies the HTML element that shifted. Hovering on this property in DevTools highlights the corresponding page element.

The `previousRect` and `currentRect` properties report the size and position of the node.

- The `x` and `y` coordinates report the x-coordinate and y-coordinate respectively of the top-left corner of the element
- The `width` and `height` properties report the width and height respectively of the element.
- The `top`, `right`, `bottom`, and `left` properties report the x or y coordinate values corresponding to the given edge of the element. In other words, the value of `top` is equal to `y`; the value of `bottom` is equal to `y+height`.

If all properties of `previousRect` are set to 0 this means that the element has shifted into view. If all properties of `currentRect` are set to 0 this means that the element has shifted out of view.

**Caution**: Layout Instability API currently does not ignore elements that shifted but were not visible due to another element being positioned in front of them. Use `display: none`, `visibility: hidden`, or `opacity: 0` to avoid layout shifts in cases where you need to run layout on some elements before you make them visible to the user.

One of the most important things to understand when interpreting these outputs is that elements listed as _sources_ are the elements that shifted during the layout shift. However, it's possible that these elements are only indirectly related to the "root cause" of layout instability. Here are a few examples.

**Example \#1**

This layout shift would be reported with one source: element B. However, the root cause of this layout shift is the change in size of element A.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format" alt="Example showing a layout shift caused by a change in element dimensions" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/oaM41OYL7mFtGcpIN8KF.png?auto=format&amp;w=1600 1600w" width="800" height="452" />

**Example \#2**

The layout shift in this example would be reported with two sources: element A and element B. The root cause of this layout shift is the change in position of element A.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format" alt="Example showing a layout shift caused by a change in element position" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AhaslIEWb5fFMMgiZcI2.png?auto=format&amp;w=1600 1600w" width="800" height="451" />

**Example \#3**

The layout shift in this example would be reported with one source: element B. Changing the position of element B resulted in this layout shift.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format" alt="Example showing a layout shift caused by a change in element position" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/6zKjd4Ua6YJ94LMlqiMR.png?auto=format&amp;w=1600 1600w" width="800" height="451" />

**Example \#4**

Although element B changes size, there is no layout shift in this example.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format" alt="Example showing a element changing size but not causing a layout shift" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/ZujHWxsXI3C7tupe42oD.png?auto=format&amp;w=1600 1600w" width="800" height="446" />

Check out a [demo of how DOM changes are reported by the Layout Instability API](https://desert-righteous-router.glitch.me/).

### DevTools <a href="#devtools" class="w-headline-link">#</a>

#### Performance panel <a href="#performance-panel" class="w-headline-link">#</a>

The **Experience** pane of the DevTools **Performance** panel displays all layout shifts that occur during a given performance trace—even if they occur within 500 ms of a user interaction and therefore don't count towards CLS. Hovering over a particular layout shift in the **Experience** panel highlights the affected DOM element.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format" alt="Screenshot of a layout shift displayed in the DevTools Network panel" class="w-screenshot" sizes="(min-width: 724px) 724px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/Uug2fnJT8mOc2YQmxo2l.png?auto=format&amp;w=1448 1448w" width="724" height="629" />

To view more information about the layout shift, click on the layout shift, then open the **Summary** drawer. Changes to the element's dimensions are listed using the format `[width, height]`; changes to the element's position are listed using the format `[x,y]`. The **Had recent input** property indicates whether a layout shift occurred within 500 ms of a user interaction.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format" alt="Screenshot of the DevTools &#39;Summary&#39; tab for a layout shift" class="w-screenshot" sizes="(min-width: 612px) 612px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/AfVjsH9Nl9w0lJwQZEjR.png?auto=format&amp;w=1224 1224w" width="612" height="354" />

For information on the duration of a layout shift, open the **Event Log** tab. The duration of a layout shift can also be approximated by looking in the **Experience** pane for the length of the red layout shift rectangle.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format" alt="Screenshot of the DevTools &#39;Event Log&#39; tab for a layout shift" class="w-screenshot" sizes="(min-width: 612px) 612px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/124Dm7vV3EGM7M9fiugs.png?auto=format&amp;w=1224 1224w" width="612" height="354" />

The duration of a layout shift has no impact on its layout shift score.

For more information on using the **Performance** panel, refer to [Performance Analysis Reference](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/reference).

#### Highlight layout shift regions <a href="#highlight-layout-shift-regions" class="w-headline-link">#</a>

Highlighting layout shift regions can be a helpful technique for getting a quick, at-a-glance feel for the location and timing of the layout shifts occurring on a page.

To enable Layout Shift Regions in DevTools, go to **Settings &gt; More Tools &gt; Rendering &gt; Layout Shift Regions** then refresh the page that you wish to debug. Areas of layout shift will be briefly highlighted in purple.

## Thought process for identifying the cause of layout shifts <a href="#thought-process-for-identifying-the-cause-of-layout-shifts" class="w-headline-link">#</a>

You can use the steps below to identify the cause of layout shifts regardless of when or how the layout shift occurs. These steps can be supplemented with running Lighthouse—however, keep in mind that Lighthouse can only identify layout shifts that occurred during the initial page load. In addition, Lighthouse also can only provide suggestions for some causes of layout shifts—for example, image elements that do not have explicit width and height.

### Identifying the cause of a layout shift <a href="#identifying-the-cause-of-a-layout-shift" class="w-headline-link">#</a>

Layout shifts can be caused by the following events:

- Changes to the position of a DOM element
- Changes to the dimensions of a DOM element
- Insertion or removal of a DOM element
- Animations that trigger layout

In particular, the DOM element immediately preceding the shifted element is the element most likely to be involved in "causing" layout shift. Thus, when investigating why a layout shift occurred consider:

- Did the position or dimensions of the preceding element change?
- Was a DOM element inserted or removed before the shifted element?
- Was the position of the shifted element explicitly changed?

If the preceding element did not cause the layout shift, continue your search by considering other preceding and nearby elements.

In addition, the direction and distance of a layout shift can provide hints about root cause. For example, a large downward shift often indicates the insertion of a DOM element, whereas a 1 px or 2 px layout shift often indicates the application of conflicting CSS styles or the loading and application of a web font.

<figure><img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format" alt="In this example, font swapping caused page elements to shift upwards by five pixels." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/g0892nhvz3SnSaasaO1b.png?auto=format&amp;w=1600 1600w" width="800" height="452" /><figcaption>In this example, font swapping caused page elements to shift upwards by five pixels.</figcaption></figure>These are some of the specific behaviors that most frequently cause layout shift events:

#### Changes to the position of an element (that aren't due to the movement of another element) <a href="#changes-to-the-position-of-an-element-(that-aren&#39;t-due-to-the-movement-of-another-element)" class="w-headline-link">#</a>

This type of change is often a result of:

- Stylesheets that are loaded late or overwrite previously declared styles.
- Animation and transition effects.

#### Changes to the dimensions of an element <a href="#changes-to-the-dimensions-of-an-element" class="w-headline-link">#</a>

This type of change is often a result of:

- Stylesheets that are loaded late or overwrite previously declared styles.
- Images and iframes without `width` and `height` attributes that load after their "slot" has been rendered.
- Text blocks without `width` or `height` attributes that swap fonts after the text has been rendered.

#### The insertion or removal of DOM elements <a href="#the-insertion-or-removal-of-dom-elements" class="w-headline-link">#</a>

This is often the result of:

- Insertion of ads and other third-party embeds.
- Insertion of banners, alerts, and modals.
- Infinite scroll and other UX patterns that load additional content above existing content.

#### Animations that trigger layout <a href="#animations-that-trigger-layout" class="w-headline-link">#</a>

Some animation effects can [trigger layout](https://gist.github.com/paulirish/5d52fb081b3570c81e3a). A common example of this is when DOM elements are 'animated' by incrementing properties like `top` or `left` rather than using CSS's [`transform`](https://developer.mozilla.org/en-US/docs/Web/CSS/transform) property. Read [How to create high-performance CSS animations](/animations-guide/) for more information.

### Reproducing layout shifts <a href="#reproducing-layout-shifts" class="w-headline-link">#</a>

You can't fix layout shifts that you can't reproduce. One of the simplest, yet most effective things you can do to get a better sense of your site's layout stability is take 5-10 minutes to interact with your site with the goal triggering layout shifts. Keep the console open while doing this and use the Layout Instability API to report on layout shifts.

For hard to locate layout shifts, consider repeating this exercise with different devices and connection speeds. In particular, using a slower connection speed can make it easier to identify layout shifts. In addition, you can use a `debugger` statement to make it easier to step through layout shifts.

    new PerformanceObserver((entryList) => {
      for (const entry of entryList.getEntries()) {
        if (!entry.hadRecentInput) {
          cls += entry.value;
          debugger;
          console.log('Current CLS value:', cls, entry);
        }
      }
    }).observe({type: 'layout-shift', buffered: true});

Lastly, for layout issues that aren't reproducible in development, consider using the Layout Instability API in conjunction with your front-end logging tool of choice to collect more information on these issues. Check out the example [code for how to track the largest shifted element on a page](https://github.com/GoogleChromeLabs/web-vitals-report/blob/71b0879334798c732f460945ded5267cab5a36bf/src/js/analytics.js#L104-L118).

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/web-vitals/" class="w-chip">Web Vitals</a>

<span class="w-mr--sm">Last updated: Mar 11, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/debug-layout-shifts/index.md)

<a href="/blog" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
