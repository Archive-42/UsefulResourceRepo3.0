





## <a href="#defer-non-critical-css" class="w-toc__header--link">Defer non-critical CSS</a>

- [Loading CSS in a suboptimal way](#loading-css-in-a-suboptimal-way)
- [Measure](#measure)
- [Optimize](#optimize)
- [Monitor](#monitor)
- [Next steps & references](#next-steps-and-references)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Defer non-critical CSS

Feb 17, 2019 <span class="w-author__separator">•</span> Updated Jun 12, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

- <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
- <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

CSS files are [render-blocking resources](https://developers.google.com/web/tools/lighthouse/audits/blocking-resources): they must be loaded and processed before the browser renders the page. Web pages that contain unnecessarily large styles take longer to render.

In this guide, you'll learn how to defer non-critical CSS with the goal of optimizing the [Critical Rendering Path](https://developers.google.com/web/fundamentals/performance/critical-rendering-path/), and improving [First Contentful Paint (FCP)](/first-contentful-paint).

## Loading CSS in a suboptimal way <a href="#loading-css-in-a-suboptimal-way" class="w-headline-link">#</a>

The following example contains an accordion with three hidden paragraphs of text, each of which is styled with a different class:

This page requests a CSS file with eight classes, but not all of them are necessary to render the "visible" content.

The goal of this guide is to optimize this page, so only the **critical** styles are loaded synchronously, while the rest (like the ones applied to paragraphs), are loaded in a non-blocking way.

## Measure <a href="#measure" class="w-headline-link">#</a>

Run [Lighthouse](/discover-performance-opportunities-with-lighthouse/#run-lighthouse-from-chrome-devtools) on [the page](https://defer-css-unoptimized.glitch.me/) and go to the **Performance** section.

The report shows the **First Contentful Paint** metric with a value of "1s", and the opportunity **Eliminate render-blocking resources**, pointing to the **style.css** file:

<figure><img src="https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/eZtuQ2IwL3Mtnmz09bmp.png?auto=format&amp;w=1600 1600w" width="800" height="640" /></figure>The CSS we are using for this demo site is quite small. If you were requesting larger CSS files (which are not uncommon in production scenarios), and if Lighthouse detects that a page has at least 2048 bytes of CSS rules that weren't used while rendering the **above the fold** content, you'll also receive a suggestion called **Remove Unused CSS**.

To visualize how this CSS blocks rendering:

1.  Open [the page](https://defer-css-unoptimized.glitch.me/) in Chrome.
2.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
3.  Click the **Performance** tab.
4.  In the Performance panel, click **Reload**.

In the resulting trace, you'll see that the **FCP** marker is placed immediately after the CSS finishes loading:

<figure><img src="https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/WhpaDYb98Rf03JmuPenp.png?auto=format&amp;w=1600 1600w" width="800" height="352" /></figure>This means that the browser needs to wait for all CSS to load and get processed before painting a single pixel on the screen.

## Optimize <a href="#optimize" class="w-headline-link">#</a>

To optimize this page, you need to know which classes are considered "critical". You'll use the [Coverage Tool](https://developer.chrome.com/docs/devtools/css/reference/#coverage) for that:

1.  In DevTools, open the [Command Menu](https://developers.google.com/web/tools/chrome-devtools/command-menu), by pressing `Control+Shift+P` or `Command+Shift+P` (Mac).
2.  Type "Coverage" and select **Show Coverage**.
3.  Click the **Reload** button, to reload the page and start capturing the coverage.

<figure><img src="https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/JTFK7wjhlTzd2cCfkpps.png?auto=format&amp;w=1600 1600w" width="800" height="82" /></figure>Double-click on the report, to see classes marked in two colors:

- Green (**critical**): These are the classes the browser needs to render the visible content (like the title, subtitle, and accordion buttons).
- Red (**non-critical**): These styles apply to content that's not immediately visible (like the paragraphs inside the accordions).

With this information, optimize your CSS so that the browser starts processing critical styles immediately after page loads, while deferring non-critical CSS for later:

- Extract the class definitions marked with green in the report obtained from the coverage tool, and put those classes inside a `<style>` block at the head of the page:

<!-- -->

    <style type="text/css">
    .accordion-btn {background-color: #ADD8E6;color: #444;cursor: pointer;padding: 18px;width: 100%;border: none;text-align: left;outline: none;font-size: 15px;transition: 0.4s;}.container {padding: 0 18px;display: none;background-color: white;overflow: hidden;}h1 {word-spacing: 5px;color: blue;font-weight: bold;text-align: center;}
    </style>

- Then, load the rest of the classes asynchronously, by applying the following pattern:

<!-- -->

    <link rel="preload" href="styles.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
    <noscript><link rel="stylesheet" href="styles.css"></noscript>

This is not the standard way of loading CSS. Here's how it works:

- `link rel="preload" as="style"` requests the stylesheet asynchronously. You can learn more about `preload` in the [Preload critical assets guide](/preload-critical-assets).
- The `onload` attribute in the `link` allows the CSS to be processed when it finishes loading.
- "nulling" the `onload` handler once it is used helps some browsers avoid re-calling the handler upon switching the rel attribute.
- The reference to the stylesheet inside of a `noscript` element works as a fallback for browsers that don't execute JavaScript.

In this guide, you used vanilla code to implement this optimization. In a real production scenario, it's a good practice to use functions like [loadCSS](https://github.com/filamentgroup/loadCSS/blob/master/README.md), that can encapsulate this behavior and work well across browsers.

The [resulting page](https://defer-css-optimized.glitch.me/) looks exactly like the previous version, even when most styles load asynchronously. Here's how the inlined styles and asynchronous request to the CSS file look like in the HTML file:

## Monitor <a href="#monitor" class="w-headline-link">#</a>

Use DevTools to run another **Performance** trace on the [optimized page](https://defer-css-optimized.glitch.me/).

The **FCP** marker appears before the page requests the CSS, which means the browser doesn't need to wait for the CSS to load before rendering the page:

<figure><img src="https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/0mVq3q760y37JSn2MmCP.png?auto=format&amp;w=1600 1600w" width="800" height="389" /></figure>As a final step, run Lighthouse on the optimized page.

In the report you'll see that the FCP page has been reduced by **0.2s** (a 20% improvement!):

<figure><img src="https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/oTDQFSlfQwS9SbqE0D0K.png?auto=format&amp;w=1600 1600w" width="800" height="324" /></figure>The **Eliminate render-blocking resources** suggestion is no longer under **Opportunities**, and now belongs to the **Passed Audits** section:

## <figure><img src="https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/yDjEvZAcjPouC6I3I7qB.png?auto=format&amp;w=1600 1600w" width="800" height="237" /></figure>Next steps & references <a href="#next-steps-and-references" class="w-headline-link">#</a>

In this guide, you learned how to defer non-critical CSS by manually extracting the unused code in the page. As a complement to this, the [extract critical CSS guide](/extract-critical-css/) covers some of the most popular tools to extract critical CSS and includes [a codelab](/codelab-extract-and-inline-critical-css/) to see how they work in practice.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jun 12, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/defer-non-critical-css/index.md)

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
