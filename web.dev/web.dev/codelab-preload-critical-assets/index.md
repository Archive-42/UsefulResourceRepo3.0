<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

Codelab: Preload critical assets to improve loading speed
=========================================================

Apr 24, 2019

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

This codelab uses Chrome DevTools. [Download Chrome](https://www.google.com/chrome) if you don't already have it.

In this codelab, the performance of the following web page is improved by preloading and prefetching a few resources:

<img src="https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format" alt="App Screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/Ln5Oxy5vp8QWTn0GoOFh.png?auto=format&amp;w=1600 1600w" width="800" height="578" />

Measure <a href="#measure" class="w-headline-link">#</a>
--------------------------------------------------------

First measure how the website performs before adding any optimizations.

-   To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

Run the Lighthouse performance audit (**Lighthouse &gt; Options &gt; Performance**) on the live version of your Glitch (see also [Discover performance opportunities with Lighthouse](/discover-performance-opportunities-with-lighthouse)).

Lighthouse shows the following failed audit for a resource that is fetched late:

<img src="https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format" alt="Lighthouse: Preload key requests audit" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/AMhzorWlWYejd0tA11rY.png?auto=format&amp;w=1600 1600w" width="800" height="231" />

-   Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
-   Click the **Network** tab.

<img src="https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format" alt="Network panel with late-discovered resource" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/pO1f6x9pOqzYwPciKnTy.png?auto=format&amp;w=1600 1600w" width="800" height="166" />

The `main.css` file is not fetched by a Link element (`<link>`) placed in the HTML document, but a separate JavaScript file, `fetch-css.js`, attaches the Link element to the DOM after the `window.onLoad` event. This means that the file is only fetched *after* the browser finishes parsing and executing the JS file. Similarly, a web font (`K2D.woff2`) specified within `main.css` is only fetched once the CSS file has finished downloading.

The **critical request chain** represents the order of resources that are prioritized and fetched by the browser. For this web page, it currently looks like this:

    ├─┬ / (initial HTML file)
      └── fetch-css.js
        └── main.css
          └── K2D.woff2

Since the CSS file is on the third level of the request chain, Lighthouse has identified it as a late-discovered resource.

Preload critical resources <a href="#preload-critical-resources" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------

The `main.css` file is a critical asset that's needed immediately as soon as the page is loaded. For important files like this resource that are fetched late in your application, use a link preload tag to inform the browser to download it sooner by adding a Link element to the head of the document.

Add a preload tag for this application:

    <head>
      <!-- ... -->
      <link rel="preload" href="main.css" as="style">
    </head>

The `as` attribute is used to identify which type of resource is being fetched, and `as="style"` is used to preload stylesheet files.

Reload the application and take a look at the **Network** panel in DevTools.

<img src="https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format" alt="Network panel with preloaded resource" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/3xjh4kLTps0fCqs7wRwP.png?auto=format&amp;w=1600 1600w" width="800" height="166" />

Notice how the browser fetches the CSS file before the JavaScript responsible for fetching it has even been finished parsing. With preload, the browser knows to make a preemptive fetch for the resource with the assumption that it is critical for the web page.

If this was a real production app, it would make more sense to just place a `<link>` element in index.html to fetch the CSS file instead of using JavaScript to append it. Browsers already know to fetch a CSS file defined at the head of an HTML document with a high priority as soon as possible. However, preload is used in this codelab to demonstrate the best course of action for files that are fetched late in the request chain. For a large application, this can happen quite often.

If not used correctly, preload can harm performance by making unnecessary requests for resources that aren't used. In this application, `details.css` is another CSS file located at the root of the project but is used for a separate `/details route`. To show an example of how preload can be used incorrectly, add a preload hint for this resource as well.

    <head>
      <!-- ... -->
      <link rel="preload" href="main.css" as="style">
      <link rel="preload" href="details.css" as="style">
    </head>

Reload the application and take a look at the **Network** panel. A request is made to retrieve `details.css` even though it is not being used by the web page.

<img src="https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format" alt="Network panel with unecessary preload" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/vOyq8M3X2UPd5JUTvex0.png?auto=format&amp;w=1600 1600w" width="800" height="189" />

Chrome displays a warning in the **Console** panel when a preloaded resource is not used by the page within a few seconds after it has loaded.

<img src="https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format" alt="Preload warning in console" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/elfGvORyRu1s0slntYHo.png?auto=format&amp;w=1600 1600w" width="800" height="150" />

Use this warning as an indicator to identify if you have any preloaded resources that are not being used immediately by your web page. You can now remove the unnecessary preload link for this page.

    <head>
      <!-- ... -->
      <link rel="preload" href="main.css" as="style">
      <link rel="preload" href="details.css" as="style">
    </head>

For a list of all the types of resources that can be fetched along with the correct values that should be used for the `as` attribute, refer to the [MDN article on Preloading](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content#What_types_of_content_can_be_preloaded).

Cross-origin resources can also be preloaded using the `crossorigin` attribute. Moreover, same-origin font resources must be fetched using anonymous mode CORS which is why the `crossorigin` attribute is also used in this preload tag. The [Cross Origin Resource Sharing](/cross-origin-resource-sharing) guide explains the topic of same-origin and cross-origin requests in more detail.

Prefetch future resources <a href="#prefetch-future-resources" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

**Prefetch** is another browser hint that can be used to make a request for an asset used for a different navigation route but at a lower priority than other important assets needed for the current page.

In this website, clicking the image takes you to a separate `details/` route.

<img src="https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format" alt="Details route" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/KLzVOClmdtwTZ3nhzGz5.png?auto=format&amp;w=1600 1600w" width="800" height="585" />

A separate CSS file, `details.css`, contains all the styles needed for this simple page. Add a link element to `index.html` to prefetch this resource.

    <head>
      <!-- ... -->
      <link rel="prefetch" href="details.css">
    </head>

To understand how this triggers a request for the file, open the **Network** panel in DevTools and uncheck the **Disable cache** option.

<img src="https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format" alt="Disable cache in Chrome DevTools" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/dddEy2ERtrha2WZKN5Ou.png?auto=format&amp;w=1600 1600w" width="800" height="145" />

Reload the application and notice how a very low priority request is made for `details.css` after all the other files have been fetched.

<img src="https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format" alt="Network panel with prefetched resource" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/STiBaCDoaZ1Ghzbp5fOH.png?auto=format&amp;w=1600 1600w" width="800" height="211" />

With DevTools open, click the image on the website to navigate to the `details` page. Since a link element is used in `details.html` to fetch `details.css`, a request is made for the resource as expected.

<img src="https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format" alt="Details page network requests" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/AfkaIGXdHifq8n1xD8YQ.png?auto=format&amp;w=1600 1600w" width="800" height="106" />

Click the `details.css` network request in DevTools to view its details. You'll notice that the file is retrieved from the browser's disk cache.

<img src="https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format" alt="Details request fetched from disk cache" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/3pPpPCjbwugX1nnqCf5e.png?auto=format&amp;w=1600 1600w" width="800" height="170" />

By taking advantage of browser idle time, prefetch makes an early request for a resource needed for a different page. This speeds up future navigation requests by allowing the browser to cache the asset sooner and serve it from the cache when needed.

Preloading and prefetching with webpack <a href="#preloading-and-prefetching-with-webpack" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------

The [Reduce JavaScript payloads with code splitting](/reduce-javascript-payloads-with-code-splitting) post explores the use of dynamic imports to split a bundle into multiple chunks. This is demonstrated with a simple application that dynamically imports a module from [Lodash](https://lodash.com/) when a form is submitted.

<img src="https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format" alt="Magic Sorter app that demonstrates code splitting" class="w-screenshot" sizes="(min-width: 600px) 600px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/yg2lFaDyWQFBvw7YaJ3g.gif?auto=format&amp;w=1200 1200w" width="600" height="375" />

You can access [the Glitch for this application here](https://glitch.com/edit/#!/code-splitting).

The following block of code, which lives in `src/index.js,` is responsible for dynamically importing the method when the button is clicked.

    form.addEventListener("submit", e => {
      e.preventDefault()
      import('lodash.sortby')
        .then(module => module.default)
        .then(sortInput())
        .catch(err => { alert(err) });
    });

Splitting a bundle improves page loading times by reducing its initial size. Version 4.6.0 of webpack provides support to preload or prefetch chunks that are imported dynamically. Using this application as an example, the `lodash` method can be prefetched at browser idle time; when a user presses the button, there is no delay for the resource to be fetched.

Use the specific `webpackPrefetch` comment parameter within a dynamic import to prefetch a particular chunk. Here is how it would look with this particular application.

    form.addEventListener("submit", e => {
      e.preventDefault()
      import(/* webpackPrefetch: true */ 'lodash.sortby')
        .then(module => module.default)
        .then(sortInput())
        .catch(err => { alert(err) });
    });

Once the application is reloaded, webpack injects a prefetch tag for the resource into the head of the document. This can be seen in the **Elements** panel in DevTools.

<img src="https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format" alt="Elements panel with prefetch tag" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/5Zs5L6UMnkUJXyfwtru7.png?auto=format&amp;w=1600 1600w" width="800" height="520" />

Observing the requests in the **Network** panel also shows that this chunk is fetched with a low priority after all other resources have been requested.

<img src="https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format" alt="Network panel with prefetched request" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/nGh06M2LqgTfBUwPaXK7.png?auto=format&amp;w=1600 1600w" width="800" height="181" />

Although prefetch makes more sense for this use case, webpack also provides support for preloading chunks that are dynamically imported.

    import(/* webpackPreload: true */ 'module')

Conclusion <a href="#conclusion" class="w-headline-link">#</a>
--------------------------------------------------------------

With this codelab, you should have a solid understanding of how preloading or prefetching certain assets can improve the user experience of your site. It is important to mention that these techniques should not be used for every resource and using them incorrectly can harm performance. The best results are noticed by only preloading or prefetching selectively.

To summarize:

-   Use **preload** for resources that are discovered late but are critical to the current page.
-   Use **prefetch** for resources that are needed for a future navigation route or user action.

Not all browsers currently support both preload and prefetch. This means that not all users of your application may notice performance improvements.

-   [Browser support: Preload](https://caniuse.com/#feat=link-rel-preload)
-   [Browser support: Prefetch](https://caniuse.com/#feat=link-rel-prefetch)

If you would like more information about specific aspects of how preloading and prefetching can affect your web page, refer to these articles:

-   [Preload, Prefetch and Priorities in Chrome](https://medium.com/reloading/preload-prefetch-and-priorities-in-chrome-776165961bbf)
-   [&lt;link rel="prefetch/preload"&gt; in webpack](https://medium.com/webpack/link-rel-prefetch-preload-in-webpack-51a52358f84c)

<a href="/preload-critical-assets" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to article</a>

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
