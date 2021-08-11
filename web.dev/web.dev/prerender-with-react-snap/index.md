<img src="https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/LTvlmRgA6MLec9QT4Tsv.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#pre-render-routes-with-react-snap" class="w-toc__header--link">Pre-render routes with react-snap</a>

- [Why is this useful?](#why-is-this-useful)
- [react-snap](#react-snap)
- [Flash of unstyled content](#flash-of-unstyled-content)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Pre-render routes with react-snap

Not server-side rendering but still want to speed up the performance of your React site? Try pre-rendering!

Apr 29, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

- <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
- <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
- <a href="https://houssein.me/" class="w-author__link">Blog</a>

[`react-snap`](https://github.com/stereobooster/react-snap) is a third-party library that pre-renders pages on your site into static HTML files. This can improve [First Paint](https://developers.google.com/web/fundamentals/performance/user-centric-performance-metrics#first_paint_and_first_contentful_paint) times in your application.

Here's a comparison of the same application with and without pre-rendering loaded on a simulated 3G connection and mobile device:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format" class="w-screenshot" sizes="(min-width: 600px) 600px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t5OiDw1VGxrbqbcxMh3J.gif?auto=format&amp;w=1200 1200w" width="600" height="435" /></figure>`react-snap` is not the only library that can pre-render static HTML content for your React application. [`react-snapshot`](https://github.com/geelen/react-snapshot) is another alternative.

## Why is this useful? <a href="#why-is-this-useful" class="w-headline-link">#</a>

The main performance problem with large single-page applications is that the user needs to wait for the JavaScript bundle(s) that make up the site to finish downloading before they can see any real content. The larger the bundles, the longer the user will have to wait.

To solve this, many developers take the approach of rendering the application on the server instead of only booting it up on the browser. With each page/route transition, the complete HTML is generated on the server and sent to the browser, which reduces First Paint times but comes at the cost of a slower Time to First Byte.

**Pre-rendering** is a separate technique that is less complex than server rendering, but also provides a way to improve First Paint times in your application. A headless browser, or a browser without a user interface, is used to generate static HTML files of every route during _build time_. These files can then be shipped along with the JavaScript bundles that are needed for the application.

## react-snap <a href="#react-snap" class="w-headline-link">#</a>

`react-snap` uses [Puppeteer](https://github.com/GoogleChrome/puppeteer) to create pre-rendered HTML files of different routes in your application. To begin, install it as a development dependency:

    npm install --save-dev react-snap

Then add a `postbuild` script in your `package.json`:

    "scripts": {
      //...
      "postbuild": "react-snap"
    }

This would automatically run the `react-snap` command every time a new build of the applications made (`npm build`).

`npm` supports _pre_ and _post_ commands for main and arbitrary scripts which will always run directly before or after the original script respectively. You can learn more in the [npm documentation](https://docs.npmjs.com/misc/scripts).

The last thing you will need to do is change how the application is booted. Change the `src/index.js` file to the following:

    import React from 'react';
    import ReactDOM from 'react-dom';
    import './index.css';
    import App from './App';

    ReactDOM.render(<App />, document.getElementById('root'));
    const rootElement = document.getElementById("root");

    if (rootElement.hasChildNodes()) {
      ReactDOM.hydrate(<App />, rootElement);
    } else {
      ReactDOM.render(<App />, rootElement);
    }

Instead of only using `ReactDOM.render` to render the root React element directly into the DOM, this checks to see if any child nodes are already present to determine whether HTML contents were pre-rendered (or rendered on the server). If that's the case, `ReactDOM.hydrate` is used instead to attach event listeners to the already created HTML instead of creating it anew.

Building the application will now generate static HTML files as payloads for each route that is crawled. You can take a look at what the HTML payload looks like by clicking the URL of the HTML request and then clicking the **Previews** tab within Chrome DevTools.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format" alt="A before and after comparison. The after shot shows content has rendered." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/l5U36PBU7H7Boswn5Gfq.png?auto=format&amp;w=1600 1600w" width="800" height="450" />

`react-snap` can be used for other frameworks than React! This includes Vue and Preact. More instructions about this can be found in the [`react-snap` README](https://github.com/stereobooster/react-snap).

## Flash of unstyled content <a href="#flash-of-unstyled-content" class="w-headline-link">#</a>

Although static HTML is now rendered almost immediately, it still remains unstyled by default which may cause the issue of showing a "flash of unstyled content" (FOUC). This can be especially noticeable if you are using a CSS-in-JS library to generate selectors since the JavaScript bundle will have to finish executing before any styles can be applied.

To help prevent this, the **critical** CSS, or the minimum amount of CSS that is needed for the initial page to render, can be inlined directly to the `<head>` of the HTML document. `react-snap` uses another third-party library under the hood, [`minimalcss`](https://github.com/peterbe/minimalcss), to extract any critical CSS for different routes. You can enable this by specifying the following in your `package.json` file:

    "reactSnap": {
      "inlineCss": true
    }

Taking a look at the response preview in Chrome DevTools will now show the styled page with critical CSS inlined.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format" alt="A before and after comparison. The after shot shows content has rendered and is styled because of inlined critical CSS." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/sgxwVZfvpYchXnn1mQrY.png?auto=format&amp;w=1600 1600w" width="800" height="450" />

**Caution**: The `inlineCSS` option is still experimental. It is worth double-checking to make sure styles are being applied correctly for your routes.

### Conclusion <a href="#conclusion" class="w-headline-link">#</a>

If you are not server-side rendering routes in your application, use `react-snap` to pre-render static HTML to your users.

1.  Install it as a development dependency and begin with just the default settings.
2.  Use the experimental `inlineCss` option to inline critical CSS if it works for your site.
3.  If you are using code splitting on a component level within any routes, be careful not to pre-render a loading state to your users. The [`react-snap` README](https://github.com/stereobooster/react-snap#async-components) covers this in more detail.

<span class="w-mr--sm">Last updated: Apr 29, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/prerender-with-react-snap/index.md)

<a href="/react" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
