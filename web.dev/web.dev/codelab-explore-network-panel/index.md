# Explore DevTools Network panel

Nov 5, 2018

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

- <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
- <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
- <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

This codelab uses Chrome DevTools. [Download Chrome](https://www.google.com/chrome) if you don't already have it.

This codelab walks you through the process of interpreting all of the network traffic for a somewhat complex sample application. At the end of the exercise, you'll have the skills you need to figure out _what_ your own web application is loading and _when_ it's making each request.

The screenshots and instructions in this codelab assume that you're using Chrome. Each browser has its own DevTools experience, which might not match what you see in this codelab.

## Navigate to the Network Panel <a href="#navigate-to-the-network-panel" class="w-headline-link">#</a>

Navigate to the Network panel to see the network traffic for the demo application.

1.  To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

2.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.

3.  Click the **Network** tab.

4.  Reload the page to see the network traffic.

The Network panel shows all the assets loaded because of your initial navigation:

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format" alt="Chrome DevTools&#39; network panel." class="screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kofLXSq1f3ekY7KY9QK7.png?auto=format&amp;w=1600 1600w" width="800" height="219" />

The actual columns you see in the Network panel may be different; the screenshot shows a simplified view with everything but the **Name**, **Type**, and **Waterfall** columns hidden.

## How to interpret the entries <a href="#how-to-interpret-the-entries" class="w-headline-link">#</a>

Each row of recorded network traffic represents a single request and response pair.

The first row, with type `document`, is the initial navigation request for the web app's HTML. This is the source for the waterfall; each of the subsequent requests for additional assets (known as subresources of the main document) flow from this original source.

The second and third rows, showing a CSS `stylesheet` and a `script` subresource being loaded, are dependent requests that were initiated by the main document.

Looking at _when_ those requests are made, the waterfall diagram shows that they're not started until very late in the process of responding to the navigation request.

Taken together, the requests for the HTML document, CSS, and JavaScript are needed to display the full page during the initial navigation.

## Create some additional runtime requests <a href="#create-some-additional-runtime-requests" class="w-headline-link">#</a>

With the **Network** panel still open and recording, it's time to simulate something common for a lot of web apps: additional API requests used to add more data to the page after the initial navigation is complete.

Trigger these additional requests by clicking **Find Me** in the app and then **Allow** in the popup that appears. This will allow the site to access your current location:

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format" alt="The allow location permission prompt." sizes="(min-width: 638px) 638px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/TJTq6re6eiVf74N8SwWE.png?auto=format&amp;w=1276 1276w" width="638" height="257" />

You could also deny geolocation permission, in which case the web app will fall back to a default location.

Once the web app has a location to work with, clicking **Find Nearby Wikipedia Entries** results in several additional network requests. You should see something like this:

<img src="https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format" alt="image" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/Y9EAf75LBCkkpXyatG3f.png?auto=format&amp;w=1600 1600w" width="800" height="567" />

## Interpret the new entries <a href="#interpret-the-new-entries" class="w-headline-link">#</a>

As before, each row of recorded network traffic represents a single request and response pair.

The first row of the new entries represents a request with a type of `fetch`, which corresponds to the [way the web app requests data](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API) from the Wikipedia API.

The following rows all are images (`png` or `jpeg`) associated with the Wikipedia entries. Although it's a little hard to see from the screenshot, their entries in the Waterfall column directly flow from the API response.

For all of these additional requests, the _when_ is going to vary based on how long you've had the page open before you click on **Find Nearby Wikipedia Entries**. Most important here is that the _when_ is disconnected from the initial navigation request. You can tell this from the large gap that exists in the Waterfall display, representing a period of time that passed in between the initial loading and when the Wikipedia API request is made.

Requests made after a gap of time following a navigation fall into the category of "runtime requests," as opposed to the initial set of requests used to display the page when you first navigated to it.

## Summing things up <a href="#summing-things-up" class="w-headline-link">#</a>

Having gone through the steps in this codelab, you're now familiar with the tools you can use to analyze what _any_ web application loads.

The Network panel helps you answer the question of _what_'s being loaded, via the URLs in the Name column and the data in the Type column, along with _when_ it's being loaded, via the waterfall display.

You've also seen that requests made by a web page can (usually) be grouped into one of two categories:

1.  Initial requests, made right after navigating to a new page, for the HTML, JavaScript, CSS (and potentially other assets).
2.  Runtime requests made as a result of user interaction with the page. This can often start with a request to an API, and then flow into several follow-up requests based on the API data retrieved.

<a href="/identify-resources-via-network-panel" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to article</a>

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
