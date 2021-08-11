<img src="https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format" alt="Inspecting a laptop with a magnifying glass." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/8ZJRM6xxTNs8wBPph7ZO.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#identify-slow-third-party-javascript" class="w-toc__header--link">Identify slow third-party JavaScript</a>

- [If you only have 5 minutes](#if-you-only-have-5-minutes)
- [Third-party usage](#third-party-usage)
- [Reduce JavaScript execution time](#reduce-javascript-execution-time)
- [Avoid enormous network payloads](#avoid-enormous-network-payloads)
- [Block network requests in Chrome DevTools](#block-network-requests-in-chrome-devtools)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Identify slow third-party JavaScript

Supercharge your performance detective skills with Lighthouse and Chrome DevTools.

Aug 14, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

- <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
- <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
- <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

As a developer, you often don't have control over [which third-party scripts](/third-party-javascript/#network) your site loads. Before you can optimize third-party content you have to do some detective work to find out what's making your site slow. 🕵️

In this post, you'll learn how to use [Lighthouse](https://developers.google.com/web/tools/lighthouse/) and [Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/) to identify slow third-party resources. The post walks through increasingly robust techniques which are best used in combination.

## If you only have 5 minutes <a href="#if-you-only-have-5-minutes" class="w-headline-link">#</a>

The Lighthouse [Performance audit](/lighthouse-performance) helps you discover opportunities to speed up page loads. Slow third-party scripts are likely to appear in the **Diagnostics** section under the **Reduce JavaScript execution time** and **Avoid enormous network payloads** audits.

To run an audit:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Lighthouse** tab.
3.  Click **Mobile**.
4.  Select the **Performance** checkbox. (You can clear the rest of the checkboxes in the Audits section.)
5.  Click **Simulated Fast 3G, 4x CPU Slowdown**.
6.  Select the **Clear Storage** checkbox.
7.  Click **Run audits**.

<img src="https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format" alt="Screenshot of the Chrome DevTools Audits panel." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/XLNFxdEOc7739bcIwERq.png?auto=format&amp;w=1600 1600w" width="800" height="1068" />

### Third-party usage <a href="#third-party-usage" class="w-headline-link">#</a>

The Lighthouse **Third-party usage** audit shows a list of the third-party providers a page uses. This overview can help you better understand the big picture and identify redundant third-party code. The audit is available in the [Lighthouse extension](https://chrome.google.com/webstore/detail/lighthouse/blipmdconlkpinefehnmjammfjpmpbjk?hl=en) and will soon be added to DevTools in Chrome 77.

<figure><img src="https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format" alt="Third-party provider names generated with Startup generator. Any similarity to actual startups, living or dead, is purely coincidental." class="w-screenshot" sizes="(min-width: 728px) 728px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/4JXHK0FkgJIfKED16BnF.png?auto=format&amp;w=1456 1456w" width="728" height="646" /><figcaption>Third-party provider names generated with <a href="http://tiffzhang.com/startup/?s=641553836036">Startup generator</a>. Any similarity to actual startups, living or dead, is purely coincidental.</figcaption></figure>### Reduce JavaScript execution time <a href="#reduce-javascript-execution-time" class="w-headline-link">#</a>

The Lighthouse [Reduce JavaScript execution time](/bootup-time) audit highlights scripts that take a long time to parse, compile, or evaluate. Select the **Show 3rd-party resources** checkbox to discover CPU-intensive third-party scripts.

<img src="https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format" alt="Screenshot showing that the &#39;Show third-party resources&#39; checkbox is checked." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/O7vN1En6dtbL3Q8TbufC.png?auto=format&amp;w=1600 1600w" width="800" height="981" />

### Avoid enormous network payloads <a href="#avoid-enormous-network-payloads" class="w-headline-link">#</a>

The Lighthouse [Avoid enormous network payloads](/total-byte-weight) audit identifies network requests—including those from third-parties—that may slow down page load time. The audit fails when your network payload exceeds 4,000 KB.

<img src="https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format" alt="Screenshot of the Chrome DevTools &#39;Avoid enormous network payloads&#39; audit." class="w-screenshot" sizes="(min-width: 799px) 799px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/9Pnoz73MLeNzooUQLuam.png?auto=format&amp;w=1598 1598w" width="799" height="631" />

## Block network requests in Chrome DevTools <a href="#block-network-requests-in-chrome-devtools" class="w-headline-link">#</a>

Chrome DevTools [network request blocking](https://developers.google.com/web/updates/2017/04/devtools-release-notes#block-requests) allows you to see how your page behaves when a particular script, stylesheet, or other resource isn't available. After you identify third-party scripts that you suspect affect performance, measure how your load time changes by blocking the requests to those scripts.

To enable request blocking:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Network** tab.
3.  Right-click any request in the **Network** panel.
4.  Select **Block request URL**.

<img src="https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format" alt="A screenshot of the context menu in the Chrome DevTools Performance panel. The &#39;Block request URL&#39; option is highlighted." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/UbedvjrtP9si1l0X2QVA.png?auto=format&amp;w=1600 1600w" width="800" height="529" />

A **Request blocking** tab will appear in the DevTools drawer. You can manage which requests have been blocked there.

To measure the impact of third-party scripts:

1.  Measure how long your page takes to load using the **Network** panel. To emulate real-world conditions, turn on [network throttling](https://developers.google.com/web/tools/chrome-devtools/network-performance/#emulate) and [CPU throttling](https://developers.google.com/web/updates/2017/07/devtools-release-notes#throttling). (On faster connections and desktop hardware, the impact of expensive scripts may not be as representative as it would be on a mobile phone.)
2.  Block the URLs or domains responsible for third-party scripts you believe are an issue.
3.  Reload the page and re-measure how long it takes to load without the blocked third-party scripts.

You should hopefully see a speed improvement, but occasionally blocking third-party scripts might not have the effect you expect. If that's the case, reduce the list of blocked URLs until you isolate the one that's causing slowness.

Note that doing three or more runs of measurement and looking at the median values will likely produce more stable results. As third-party content can occasionally pull in different resources per page load, this approach can give you a more realistic estimate. [DevTools now supports multiple recordings](https://twitter.com/ChromeDevTools/status/963820146388221952) in the **Performance** panel, making this a little easier.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Aug 14, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/identify-slow-third-party-javascript/index.md)

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
