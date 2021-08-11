





## <a href="#cross-origin-resource-sharing-(cors)" class="w-toc__header--link">Cross-Origin Resource Sharing (CORS)</a>

- [How does a resource request work on the web?](#how-does-a-resource-request-work-on-the-web)
- [header](#header)
- [body](#body)
- [How does CORS work?](#how-does-cors-work)
- [Step 1: client (browser) request](<#step-1:-client-(browser)-request>)
- [Step 2: server response](#step-2:-server-response)
- [Step 3: browser receives response](#step-3:-browser-receives-response)
- [See CORS in action](#see-cors-in-action)
- [Share credentials with CORS](#share-credentials-with-cors)
- [Request](#request)
- [Response](#response)
- [Preflight requests for complex HTTP calls](#preflight-requests-for-complex-http-calls)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Cross-Origin Resource Sharing (CORS)

Share cross-origin resources safely

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/secure" class="w-post-signpost__link">Safe and secure</a>

[<img src="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Mariko Kosaka" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/kosamari/)

<a href="/authors/kosamari/" class="w-author__name-link">Mariko Kosaka</a>

- <a href="https://twitter.com/kosamari" class="w-author__link">Twitter</a>
- <a href="https://github.com/kosamari" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@kosamari" class="w-author__link">Glitch</a>
- <a href="https://kosamari.com/" class="w-author__link">Blog</a>

The browser's same-origin policy blocks reading a resource from a different origin. This mechanism stops a malicious site from reading another site's data, but it also prevents legitimate uses. What if you wanted to get weather data from another country?

In a modern web application, an application often wants to get resources from a different origin. For example, you want to retrieve JSON data from a different domain or load images from another site into a `<canvas>` element.

In other words, there are **public resources** that should be available for anyone to read, but the same-origin policy blocks that. Developers have used work-arounds such as [JSONP](https://stackoverflow.com/questions/2067472/what-is-jsonp-all-about), but **Cross-Origin Resource Sharing (CORS)** fixes this in a standard way.

Enabling **CORS** lets the server tell the browser it's permitted to use an additional origin.

## How does a resource request work on the web? <a href="#how-does-a-resource-request-work-on-the-web" class="w-headline-link">#</a>

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format" alt="Figure: Illustrated client request and server response" sizes="(min-width: 668px) 668px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8J6A0Bk5YXdvyoj8HVzs.png?auto=format&amp;w=1336 1336w" width="668" height="327" /><figcaption>Figure: Illustrated client request and server response</figcaption></figure>A browser and a server can exchange data over the network using the **Hypertext Transfer Protocol** (HTTP). HTTP defines the communication rules between the requester and the responder, including what information is needed to get a resource.

The HTTP header is used to negotiate the type of message exchange between the client and the server and is used to determine access. Both the browser's request and the server's response message are divided into two parts: **header** and **body**:

### header <a href="#header" class="w-headline-link">#</a>

Information about the message such as the type of message or the encoding of the message. A header can include a [variety of information](https://en.wikipedia.org/wiki/List_of_HTTP_header_fields) expressed as key-value pairs. The request header and response header contain different information.

It's important to note that headers cannot contain comments.

**Sample Request header**

    Accept: text/html
    Cookie: Version=1

The above is equivalent to saying "I want to receive HTML in response. Here is a cookie I have."

**Sample Response header**

    Content-Encoding: gzip
    Cache-Control: no-store

The above is equivalent to saying "Data is encoded with gzip. Do not cache this please."

### body <a href="#body" class="w-headline-link">#</a>

The message itself. This could be plain text, an image binary, JSON, HTML, and so on.

## How does CORS work? <a href="#how-does-cors-work" class="w-headline-link">#</a>

Remember, the same-origin policy tells the browser to block cross-origin requests. When you want to get a public resource from a different origin, the resource-providing server needs to tell the browser "This origin where the request is coming from can access my resource". The browser remembers that and allows cross-origin resource sharing.

### Step 1: client (browser) request <a href="#step-1:-client-(browser)-request" class="w-headline-link">#</a>

When the browser is making a cross-origin request, the browser adds an `Origin` header with the current origin (scheme, host, and port).

### Step 2: server response <a href="#step-2:-server-response" class="w-headline-link">#</a>

On the server side, when a server sees this header, and wants to allow access, it needs to add an `Access-Control-Allow-Origin` header to the response specifying the requesting origin (or `*` to allow any origin.)

### Step 3: browser receives response <a href="#step-3:-browser-receives-response" class="w-headline-link">#</a>

When the browser sees this response with an appropriate `Access-Control-Allow-Origin` header, the browser allows the response data to be shared with the client site.

## See CORS in action <a href="#see-cors-in-action" class="w-headline-link">#</a>

Here is a tiny web server using Express.

The first endpoint (line 8) does not have any response header set, it just sends a file in response.

- Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
- Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
- Click the **Console** tab.
- Try the following command:

<!-- -->

    fetch('https://cors-demo.glitch.me/', {mode:'cors'})

You should see an error saying:

    request has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header
    is present on the requested resource.

The second endpoint (line 13) sends the same file in response but adds `Access-Control-Allow-Origin: *` in the header. From the console, try

    fetch('https://cors-demo.glitch.me/allow-cors', {mode:'cors'})

This time, your request should not be blocked.

## Share credentials with CORS <a href="#share-credentials-with-cors" class="w-headline-link">#</a>

For privacy reasons, CORS is normally used for "anonymous requests"—ones where the request doesn't identify the requestor. If you want to send cookies when using CORS (which could identify the sender), you need to add additional headers to the request and response.

### Request <a href="#request" class="w-headline-link">#</a>

Add `credentials: 'include'` to the fetch options like below. This will include the cookie with the request.

    fetch('https://example.com', {
      mode: 'cors',
      credentials: 'include'
    })

### Response <a href="#response" class="w-headline-link">#</a>

`Access-Control-Allow-Origin` must be set to a specific origin (no wildcard using `*`) and must set `Access-Control-Allow-Credentials` to `true`.

    HTTP/1.1 200 OK
    Access-Control-Allow-Origin: https://example.com
    Access-Control-Allow-Credentials: true

## Preflight requests for complex HTTP calls <a href="#preflight-requests-for-complex-http-calls" class="w-headline-link">#</a>

If a web app needs a complex HTTP request, the browser adds a **[preflight request](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS#preflighted_requests)** to the front of the request chain.

The CORS specification defines a **complex request** as

- A request that uses methods other than GET, POST, or HEAD
- A request that includes headers other than `Accept`, `Accept-Language` or `Content-Language`
- A request that has a `Content-Type` header other than `application/x-www-form-urlencoded`, `multipart/form-data`, or `text/plain`

Browsers create a preflight request if it is needed. It's an `OPTIONS` request like below and is sent before the actual request message.

    OPTIONS /data HTTP/1.1
    Origin: https://example.com
    Access-Control-Request-Method: DELETE

On the server side, an application needs to respond to the preflight request with information about the methods the application accepts from this origin.

    HTTP/1.1 200 OK
    Access-Control-Allow-Origin: https://example.com
    Access-Control-Allow-Methods: GET, DELETE, HEAD, OPTIONS

The server response can also include an `Access-Control-Max-Age` header to specify the duration (in seconds) to cache preflight results so the client does not need to make a preflight request every time it sends a complex request.

<a href="/tags/security/" class="w-chip">Security</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/secure/cross-origin-resource-sharing/index.md)

<a href="/secure" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
