





<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format" alt="Picture of cookie notices." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/V8rNgYUkkAWET3EkBL6H.png?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#best-practices-for-cookie-notices" class="w-toc__header--link">Best practices for cookie notices</a>

- [Performance](#performance)
- [Best practices](#best-practices)
- [Performance measurement](#performance-measurement)
- [Real User Monitoring (RUM)](<#real-user-monitoring-(rum)>)
- [Synthetic monitoring](#synthetic-monitoring)
- [Testing cookie notices with WebPageTest](#testing-cookie-notices-with-webpagetest)
- [Testing cookie notices with Lighthouse](#testing-cookie-notices-with-lighthouse)
- [User experience](#user-experience)
- [Placement](#placement)
- [Configurability](#configurability)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Best practices for cookie notices

Optimize cookie notices for performance and usability.

Mar 30, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/learn-web-vitals" class="w-post-signpost__link">Web Vitals</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

- <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
- <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
- <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

This article discusses how cookie notices can affect performance, performance measurement, and user experience.

## Performance <a href="#performance" class="w-headline-link">#</a>

Cookie notices can have a significant impact on page performance due to the fact that they are typically loaded early in the page load process, are shown to all users, and can potentially influence the loading of ads and other page content.

Here's how cookie notices can impact Web Vitals metrics:

- **Largest Contentful Paint (LCP):** Most cookie consent notices are fairly small and therefore typically don't contain a page's LCP element. However, this can happen—particularly on mobile devices. On mobile devices, a cookie notice typically takes up a larger portion of the screen. This usually occurs when a cookie notice contains a large block of text (text blocks can be LCP elements too).

- **First Input Delay (FID):** Generally speaking, your cookie consent solution in and of itself should have a minimal impact on FID—cookie consent requires little JavaScript execution. However, the technologies that these cookies enable—namely advertising and tracking scripts—may have a significant impact on page interactivity. Delaying these scripts until cookie acceptance can serve as a technique to decrease First Input Delay (FID).

- **Cumulative Layout Shift (CLS):** Cookie consent notices are a very common source of layout shifts.

Generally speaking, you can expect a cookie notice from third-party providers to have a greater impact on performance than a cookie notice that you build yourself. This is not a problem unique to cookie notices—but rather the nature of third-party scripts in general.

### Best practices <a href="#best-practices" class="w-headline-link">#</a>

The best practices in this section focus on third-party cookie notices. Some, but not all, of these best practices will also be applicable to first-party cookie notices.

#### Load cookie notices scripts asynchronously <a href="#load-cookie-notices-scripts-asynchronously" class="w-headline-link">#</a>

Cookie notice scripts should be loaded asynchronously. To do this, add the [`async`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/script#attr-async) attribute to the script tag.

    <script src="https://cookie-notice.com/script.js" async>

Scripts that are not asynchronous block the browser parser. This delays page load and LCP. For more information, see [Efficiently load third-party JavaScript](/efficiently-load-third-party-javascript/).

If you must use synchronous scripts (for example, some cookie notices rely on synchronous scripts to implement cookie blocking) you should make sure that this request loads as quickly as possible. One way to do this is to [use resource hints](/preconnect-and-dns-prefetch/).

#### Load cookie notice scripts directly <a href="#load-cookie-notice-scripts-directly" class="w-headline-link">#</a>

Cookie notice scripts should be loaded "directly" by placing the script tag in the HTML of the main document—rather than loaded by a tag manager or other script. Using a tag manager or secondary script to inject the cookie notice script delays the loading of the cookie notice script: it obscures the script from the browser's lookahead parser and it prevents the script from loading before JavaScript execution.

#### Establish an early connection with the cookie notice origin <a href="#establish-an-early-connection-with-the-cookie-notice-origin" class="w-headline-link">#</a>

All sites that load their cookie notice scripts from a third-party location should use either the `dns-prefetch` or `preconnect` resource hints to help establish an early connection with the origin that hosts cookie notice resources. For more information, see [Establish network connections early to improve perceived page speed](/preconnect-and-dns-prefetch/).

    <link rel="preconnect" href="https://cdn.cookie-notice.com/">

It is common for cookie notices to load resources from multiple origins— for example, loading resources from both `www.cookie-notice.com` and `cdn.cookie-notice.com`. Separate origins require separate connections and therefore separate resource hints.

#### Preload cookie notices as appropriate <a href="#preload-cookie-notices-as-appropriate" class="w-headline-link">#</a>

Some sites would benefit from using the [`preload`](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content) resource hint to load their cookie notice script. The `preload` resource hint informs the browser to initiate an early request for the specified resource.

    <link rel="preload" href="https://www.cookie-notice.com/cookie-script.js">

`preload` is most powerful when its usage is limited to fetching a couple key resources per page. Thus, the usefulness of preloading the cookie notice script will vary depending on the situation.

#### Be aware of performance tradeoffs when styling cookie notices <a href="#be-aware-of-performance-tradeoffs-when-styling-cookie-notices" class="w-headline-link">#</a>

Customizing the look and feel of a third-party cookie notice may incur additional performance costs. For example, third-party cookie notices aren't always able to reuse the same resources (for example, web fonts) that are used elsewhere on the page. In addition, third-party cookie notices tend to load styling at the end of long request chains. To avoid any surprises, be aware of how your cookie notice loads and applies styling and related resources.

#### Avoid layout shifts <a href="#avoid-layout-shifts" class="w-headline-link">#</a>

These are some of the most common layout shift issues associated with cookie notices:

- **Top-of-screen cookie notices:** Top-of-screen cookie notices are a very common source of layout shift. If a cookie notice is inserted into the DOM after the surrounding page has already rendered, it will push the page elements below it further down the page. This type of layout shift can be eliminated by reserving space in the DOM for the consent notice. If this is not a feasible solution—for example, if the dimensions of your cookie notice vary by geography, consider using a sticky footer or modal to display the cookie notice. Because both of these alternative approaches display the cookie notice as an "overlay" on top of the rest of the page, the cookie notice should not cause content shifts when it loads.
- **Animations**: Many cookie notices use animations—for example, "sliding in" a cookie notice is a common design pattern. Depending on how these effects are implemented, they can cause layout shifts. For more information, see [Debugging layout shifts](/debugging-layout-shifts/).
- **Fonts**: Late-loading fonts can block render and or cause layout shifts. This phenomena is more apparent on slow connections.

#### Advanced loading optimizations <a href="#advanced-loading-optimizations" class="w-headline-link">#</a>

These techniques take more work to implement but can further optimize the loading of cookie notice scripts:

- Caching and serving third-party cookie notice scripts from your own servers can improve the delivery speed of these resources.
- Using [service workers](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API/Using_Service_Workers) can allow you more control over the [fetching and caching of third-party scripts](https://developers.google.com/web/tools/workbox/guides/handle-third-party-requests) such as cookie notice scripts.

## Performance measurement <a href="#performance-measurement" class="w-headline-link">#</a>

Cookie notices can impact performance measurements. This section discusses some of these implications and techniques for mitigating them.

### Real User Monitoring (RUM) <a href="#real-user-monitoring-(rum)" class="w-headline-link">#</a>

Some analytics and RUM tools use cookies to collect performance data. In the event that a user declines usage of cookies these tools cannot capture performance data.

Sites should be aware of this phenomenon; it is also worthwhile to understand the mechanisms that your RUM tooling uses to collect its data. However, for the typical site this discrepancy probably isn't a cause for alarm given the direction and magnitude of the data skew. Cookie usage is not a technical requirement for performance measurement. The [web-vitals](https://github.com/GoogleChrome/web-vitals) JavaScript library is an example of a library that does not use cookies.

Depending on how your site uses cookies to collect performance data (that is, whether the cookies contain personal information), as well as the legislation in question, the use of cookies for performance measurement might not be subject to the same legislative requirements as some of the cookies used on your site for other purposes—for example, advertising cookies. Some sites choose to break out performance cookies as a separate category of cookies when asking for user consent.

### Synthetic monitoring <a href="#synthetic-monitoring" class="w-headline-link">#</a>

Without custom configuration, most synthetic tools (such as Lighthouse and WebPageTest) will only measure the experience of a first-time user who has not responded to a cookie consent notice. However, not only do variations in cache state (for example, an initial visit versus a repeat visit) need to be considered when collecting performance data, but also variations in cookie acceptance state—accepted, rejected, or unresponded.

The following sections discuss WebPageTest and Lighthouse settings that can be helpful for incorporating cookie notices into performance measurement workflows. However, cookies and cookie notices are just one of many factors that can be difficult to perfectly simulate in lab environments. For this reason, it is important to make [RUM data](/user-centric-performance-metrics/#how-metrics-are-measured) the cornerstone of your performance benchmarking, rather than synthetic tooling.

### Testing cookie notices with WebPageTest <a href="#testing-cookie-notices-with-webpagetest" class="w-headline-link">#</a>

#### Scripting <a href="#scripting" class="w-headline-link">#</a>

You can use scripting to have a [WebPageTest](https://webpagetest.org/) "click" the cookie consent banner while collecting a trace.

Add a script by going to the **Script** tab. The script below navigates to the URL to be tested and then clicks the DOM element with the id `cookieButton`.

**Caution**: WebPageTest scripts are [tab-delimited](https://github.com/WPO-Foundation/webpagetest-docs/blob/main/src/scripting.md#scripting).

    combineSteps
    navigate    %URL%
    clickAndWait    id=cookieButton

When using this script be aware that:

- `combineSteps` tells WebPageTest to "combine" the results of the scripting steps that follow into a single set of traces and measurements. Running this script without `combineSteps` can also be useful—separate traces make it easy to see whether resources were loaded before or after cookie acceptance.
- `%URL%` is a WebPageTest convention that refers to the URL that is being tested.
- `clickAndWait` tells WebPageTest to click on the element indicated by `attribute=value` and wait for the subsequent browser activity to complete. It follows the format `clickAndWait attribute=Value`.

If you've configured this script correctly, the screenshot taken by WebPageTest should not show a cookie notice (the cookie notice has been accepted).

For more information on WebPageTest scripting, check out [WebPageTest documentation](https://docs.webpagetest.org/scripting/).

#### Set cookies <a href="#set-cookies" class="w-headline-link">#</a>

To run WebPageTest with a cookie set, go to the **Advanced** tab and add the cookie header to the **Custom headers** field:

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format" alt="Screeshot showing the &#39;Custom headers&#39; field in WebPageTest" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/qSccrAxF0H4yoSzYRYdh.png?auto=format&amp;w=1600 1600w" width="800" height="181" />

#### Change the test location <a href="#change-the-test-location" class="w-headline-link">#</a>

To change the test location used by WebPageTest, click the **Test Location** dropdown located on the **Advanced Testing** tab.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format" alt="Screenshot of the &#39;Test Location&#39; dropdown in WebPageTest" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/J27NcDQ5LTtXYloaA1DN.png?auto=format&amp;w=1600 1600w" width="800" height="267" />

### Testing cookie notices with Lighthouse <a href="#testing-cookie-notices-with-lighthouse" class="w-headline-link">#</a>

Setting cookies on a Lighthouse run can serve as a mechanism for getting a page into a particular state for testing by Lighthouse. Lighthouse's cookie behavior varies slightly by context (DevTools, CLI, or PageSpeed Insights).

#### DevTools <a href="#devtools" class="w-headline-link">#</a>

Cookies are not cleared when Lighthouse is run from DevTools. However, other types of storage are cleared by default. This behavior can be changed by using the **Clear Storage** option in the **Lighthouse** settings panel.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format" alt="Screenshot higlighting the Lighthouse &#39;Clear Storage&#39; option" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/nmNDeSoGEQUVKeTP7q7R.png?auto=format&amp;w=1600 1600w" width="800" height="304" />

#### CLI <a href="#cli" class="w-headline-link">#</a>

Running Lighthouse from the CLI uses a fresh Chrome instance, so no cookies are set by default. To run Lighthouse from the CLI with a particular cookie set, use the following [command](https://github.com/GoogleChrome/lighthouse#cli-options):

    lighthouse <url> --extra-headers "{\"Cookie\":\"cookie1=abc; cookie2=def; \_id=foo\"}"

For more information on setting custom request headers in Lighthouse CLI, see [Running Lighthouse on Authenticated Pages](https://github.com/GoogleChrome/lighthouse/blob/master/docs/authenticated-pages.md).

#### PageSpeed Insights <a href="#pagespeed-insights" class="w-headline-link">#</a>

Running Lighthouse from PageSpeed Insights uses a fresh Chrome instance and does not set any cookies. PageSeed Insights cannot be configured to set particular cookies.

## User experience <a href="#user-experience" class="w-headline-link">#</a>

The user experience (UX) of different cookie consent notices is primarily the result of two decisions: the location of the cookie notice within the page and the extent to which the user can customize a site's use of cookies. This section discusses potential approaches to these two decisions.

**Caution**: Cookie notice UX is often heavily influenced by legislation which can vary widely by geography. Thus, some of the design patterns discussed in this section may not be relevant to your particular situation. This article should not be considered a substitute for legal advice.

When considering potential designs for your cookie notice, here are some things to think about:

- UX: Is this a good user experience? How will this particular design affect existing page elements and user flows?
- Business: What is your site's cookie strategy? What are your goals for the cookie notice?
- Legal: Does this comply with legal requirements?
- Engineering: How much work would this be to implement and maintain? How difficult would it be to change?

### Placement <a href="#placement" class="w-headline-link">#</a>

Cookie notices can be displayed as a header, inline element, or footer. They can also be displayed on top of page content using a modal or served as an [interstitial](https://en.wikipedia.org/wiki/Interstitial_webpage).

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format" alt="Diagram showing examples of different placement options for cookie notices" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/LLqHAhp7W6x4E3rZh0Oc.png?auto=format&amp;w=1600 1600w" width="800" height="345" />

#### Header, footer, and inline cookie notices <a href="#header-footer-and-inline-cookie-notices" class="w-headline-link">#</a>

Cookie notices are commonly placed in the header or footer. Of these two options, the footer placement is generally preferable because it is unobtrusive, does not compete for attention with banner ads or notifications, and typically does not cause CLS. In addition, it is a common place for placing privacy policies and terms of use.

Although inline cookie notices are an option, they can be difficult to integrate into existing user interfaces, and therefore are uncommon.

#### Modals <a href="#modals" class="w-headline-link">#</a>

Modals are cookie consent notices that are displayed on top of page content. Modals can look and perform quite differently depending on their size.

Smaller, partial-screen modals can be a good alternative for sites that are struggling to implement cookie notices in a way that doesn't cause [layout shifts](/cls/).

On the other hand, large modals that obscure the majority of page content should be used carefully. In particular, smaller sites may find that users bounce rather than accept the cookie notice of an unfamiliar site with obscured content. Although they are not necessarily synonymous concepts, if you are considering using a full-screen cookie consent modal, you should be aware of legislation regarding [cookie walls](https://techcrunch.com/2020/05/06/no-cookie-consent-walls-and-no-scrolling-isnt-consent-says-eu-data-protection-body/).

Large modals can be considered a type of interstitial. Google Search [does not penalize](https://developers.google.com/search/blog/2016/08/helping-users-easily-access-content-on) the usage of interstitials when they are used to comply with legal regulations such as in the case of cookie banners. However, ther usage of interstitials in other contexts—particularly if they are intrusive or create a poor user experience—may be penalized.

### Configurability <a href="#configurability" class="w-headline-link">#</a>

Cookie notice interfaces give users varying levels of control over which cookies they accept.

#### No configurability <a href="#no-configurability" class="w-headline-link">#</a>

These notice-style cookie banners do not present users with direct UX controls for opting out of cookies. Instead, they typically include a link to the site's cookie policy which may provide users with information about managing cookies using their web browser. These notices typically include either a "dismiss" and/or "Accept" button.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format" alt="Diagram showing examples of cookie notices with no cookie configurability" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/RlAg8DCjBC0bX7Ki5MuE.png?auto=format&amp;w=1600 1600w" width="800" height="518" />

#### Some configurability <a href="#some-configurability" class="w-headline-link">#</a>

These cookie notices give the user the option of declining cookies but do not support more granular controls. This approach to cookie notices is less common.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format" alt="Diagram showing examples of cookie notices with some cookie configurability" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/MOl8u9NcnyjCWogxzjdz.png?auto=format&amp;w=1600 1600w" width="800" height="508" />

#### Full configurability <a href="#full-configurability" class="w-headline-link">#</a>

These cookie notices provide users with more fine-grained controls for configuring the cookie usage that they accept.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format" alt="Diagram showing examples of chookie notices with full cookie configurability" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/QfFoqkkmdKHAYlftIH0n.png?auto=format&amp;w=1600 1600w" width="800" height="467" />

- **UX:** Controls for configuring cookie usage are most commonly displayed using a separate modal that is launched when the user responds to the initial cookie consent notice. However, if space permits, some sites will display these controls inline within the initial cookie consent notice.

- **Granularity:** The most common approach to cookie configurability is to allow users to opt-in to cookies by cookie "category". Examples of common cookie categories include functional, targeting, and social media cookies.

  However, some sites will go a step further and allow users to opt-in on a per-cookie basis. Alternatively, another way of providing users with more specific controls is to break down cookie categories like "advertising" into specific use cases—for example, allowing users to separately opt-in to "basic ads" and "personalized ads".

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format" alt="Diagram showing examples of cookie notices with full cookie configurability" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/z7zFPtCkFi8GEpkfubek.png?auto=format&amp;w=1600 1600w" width="800" height="372" />

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/web-vitals/" class="w-chip">Web Vitals</a>

<span class="w-mr--sm">Last updated: Mar 30, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/cookie-notice-best-practices/index.md)

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
