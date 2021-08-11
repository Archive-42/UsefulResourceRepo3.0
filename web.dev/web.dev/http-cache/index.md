

## <a href="#prevent-unnecessary-network-requests-with-the-http-cache" class="w-toc__header--link">Prevent unnecessary network requests with the HTTP Cache</a>

- [Browser compatibility](#browser-compatibility)
- [How the HTTP Cache works](#overview)
- [Request headers: stick with the defaults (usually)](#request-headers)
- [Response headers: configure your web server](#response-headers)
- [Which response header values should you use?](#response-header-strategies)
- [Long-lived caching for versioned URLs](#versioned-urls)
- [Server revalidation for unversioned URLs](#unversioned-urls)
- [Summary](#summary)
- [Learn more](#learn-more)
- [Appendix: More tips](#tips)
- [Appendix: Cache-Control flowchart](#flowchart)
- [Appendix: Cache-Control examples](#examples)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Prevent unnecessary network requests with the HTTP Cache

Nov 5, 2018 <span class="w-author__separator">•</span> Updated Apr 17, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/reliable" class="w-post-signpost__link">Network reliability</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

- <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
- <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
- <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Ilya Grigorik" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/ZkKPT8vEyGOWvy60ML7R.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/ilyagrigorik/)

<a href="/authors/ilyagrigorik/" class="w-author__name-link">Ilya Grigorik</a>

- <a href="https://twitter.com/igrigorik" class="w-author__link">Twitter</a>
- <a href="https://github.com/igrigorik" class="w-author__link">GitHub</a>

Fetching resources over the network is both slow and expensive:

- Large responses require many roundtrips between the browser and the server.
- Your page won't load until all of its [critical resources](https://developers.google.com/web/fundamentals/performance/critical-rendering-path) have downloaded completely.
- If a person is accessing your site with a limited mobile data plan, every unnecessary network request is a waste of their money.

How can you avoid unnecessary network requests? The browser's HTTP Cache is your first line of defense. It's not necessarily the most powerful or flexible approach, and you have limited control over the lifetime of cached responses, but it's effective, it's supported in all browsers, and it doesn't require much work.

This guide shows you the basics of an effective HTTP caching implementation.

## Browser compatibility <a href="#browser-compatibility" class="w-headline-link">#</a>

There isn't actually a single API called the HTTP Cache. It's the general name for a collection of web platform APIs. Those APIs are supported in all browsers:

- [`Cache-Control`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Cache-Control#Browser_compatibility)
- [`ETag`](https://developer.mozilla.org/docs/Web/HTTP/Headers/ETag#Browser_compatibility)
- [`Last-Modified`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Last-Modified#Browser_compatibility)

## How the HTTP Cache works <a href="#overview" class="w-headline-link">#</a>

All HTTP requests that the browser makes are first routed to the browser cache to check whether there is a valid cached response that can be used to fulfill the request. If there's a match, the response is read from the cache, which eliminates both the network latency and the data costs that the transfer incurs.

The HTTP Cache's behavior is controlled by a combination of [request headers](https://developer.mozilla.org/en-US/docs/Glossary/Request_header) and [response headers](https://developer.mozilla.org/en-US/docs/Glossary/Response_header). In an ideal scenario, you'll have control over both the code for your web application (which will determine the request headers) and your web server's configuration (which will determine the response headers).

Check out MDN's [HTTP Caching](https://developer.mozilla.org/docs/Web/HTTP/Caching) article for a more in-depth conceptual overview.

## Request headers: stick with the defaults (usually) <a href="#request-headers" class="w-headline-link">#</a>

While there are a number of important headers that should be included in your web app's outgoing requests, the browser almost always takes care of setting them on your behalf when it makes requests. Request headers that affect checking for freshness, like [`If-None-Match`](https://developer.mozilla.org/docs/Web/HTTP/Headers/If-None-Match) and [`If-Modified-Since`](https://developer.mozilla.org/docs/Web/HTTP/Headers/If-Modified-Since) just appear based on the browser's understanding of the current values in the HTTP Cache.

This is good news—it means that you can continue including tags like `<img src="my-image.png">` in your HTML, and the browser automatically takes care of HTTP caching for you, without extra effort.

Developers who do need more control over the HTTP Cache in their web application have an alternative—you can "drop down" a level, and manually use the [Fetch API](https://developer.mozilla.org/en-US/docs/Web/API/Fetch_API), passing it [`Request`](https://developer.mozilla.org/en-US/docs/Web/API/Request) objects with specific [`cache`](https://developer.mozilla.org/en-US/docs/Web/API/Request/cache) overrides set. That's beyond the scope of this guide, though!

## Response headers: configure your web server <a href="#response-headers" class="w-headline-link">#</a>

The part of the HTTP caching setup that matters the most is the headers that your web server adds to each outgoing response. The following headers all factor into effective caching behavior:

- [`Cache-Control`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Cache-Control). The server can return a `Cache-Control` directive to specify how, and for how long, the browser and other intermediate caches should cache the individual response.
- [`ETag`](https://developer.mozilla.org/docs/Web/HTTP/Headers/ETag). When the browser finds an expired cached response, it can send a small token (usually a hash of the file's contents) to the server to check if the file has changed. If the server returns the same token, then the file is the same, and there's no need to re-download it.
- [`Last-Modified`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Last-Modified). This header serves the same purpose as `ETag`, but uses a time-based strategy to determine if a resource has changed, as opposed to the content-based strategy of `ETag`.

Some web servers have built-in support for setting those headers by default, while others leave the headers out entirely unless you explicitly configure them. The specific details of _how_ to configure headers varies greatly depending on which web server you use, and you should consult your server's documentation to get the most accurate details.

To save you some searching, here are instructions on configuring a few popular web servers:

- [Express](https://expressjs.com/en/api.html#express.static)
- [Apache](https://httpd.apache.org/docs/2.4/caching.html)
- [nginx](http://nginx.org/en/docs/http/ngx_http_headers_module.html)
- [Firebase Hosting](https://firebase.google.com/docs/hosting/full-config)
- [Netlify](https://www.netlify.com/blog/2017/02/23/better-living-through-caching/)

Leaving out the `Cache-Control` response header does not disable HTTP caching! Instead, browsers [effectively guess](https://www.mnot.net/blog/2017/03/16/browser-caching#heuristic-freshness) what type of caching behavior makes the most sense for a given type of content. Chances are you want more control than that offers, so take the time to configure your response headers.

## Which response header values should you use? <a href="#response-header-strategies" class="w-headline-link">#</a>

There are two important scenarios that you should cover when configuring your web server's response headers.

### Long-lived caching for versioned URLs <a href="#versioned-urls" class="w-headline-link">#</a>

#### How versioned URLs can help your caching strategy

Versioned URLs are a good practice because they make it easier to invalidate cached responses.

Suppose your server instructs browsers to cache a CSS file for 1 year (`Cache-Control: max-age=31536000`) but your designer just made an emergency update that you need to roll out immediately. How do you notify browsers to update the "stale" cached copy of the file? You can't, at least not without changing the URL of the resource. After the browser caches the response, the cached version is used until it's no longer fresh, as determined by `max-age` or `expires`, or until it is evicted from the cache for some other reason—for example, the user clearing their browser cache. As a result, different users might end up using different versions of the file when the page is constructed: users who just fetched the resource use the new version, while users who cached an earlier (but still valid) copy use an older version of its response. How do you get the best of both worlds: client-side caching and quick updates? You change the URL of the resource and force the user to download the new response whenever its content changes. Typically, you do this by embedding a fingerprint of the file, or a version number, in its filename—for example, `style.x234dff.css`.

When responding to requests for URLs that contain "[fingerprint](<https://en.wikipedia.org/wiki/Fingerprint_(computing)>)" or versioning information, and whose contents are never meant to change, add `Cache-Control: max-age=31536000` to your responses.

Setting this value tells the browser that when it needs to load the same URL anytime over the next one year (31,536,000 seconds; the maximum supported value), it can immediately use the value in the HTTP Cache, without having to make a network request to your web server at all. That's great—you've immediately gained the reliability and speed that comes from avoiding the network!

Build tools like webpack can [automate the process](https://webpack.js.org/guides/caching/#output-filenames) of assigning hash fingerprints to your asset URLs.

You can also add the [`immutable` property](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Cache-Control#Revalidation_and_reloading) to your `Cache-Control` header as a further optimization, though it [will be ignored](https://www.keycdn.com/blog/cache-control-immutable#browser-support) in some browsers.

### Server revalidation for unversioned URLs <a href="#unversioned-urls" class="w-headline-link">#</a>

Unfortunately, not all of the URLs you load are versioned. Maybe you're not able to include a build step prior to deploying your web app, so you can't add hashes to your asset URLs. And every web application needs HTML files—those files are (almost!) never going to include versioning information, since no one will bother to use your web app if they need to remember that the URL to visit is `https://example.com/index.34def12.html`. So what can you do for those URLs?

This is one scenario in which you need to admit defeat. HTTP caching alone isn't powerful enough to avoid the network completely. (Don't worry—you'll soon learn about [service workers](/service-workers-cache-storage/), which will provide the support we need to swing the battle back in your favor.) But there are a few steps you can take to make sure that network requests are as quick and efficient as possible.

The following `Cache-Control` values can help you fine-tune where and how unversioned URLs are cached:

- `no-cache`. This instructs the browser that it must revalidate with the server every time before using a cached version of the URL.
- `no-store`. This instructs the browser and other intermediate caches (like CDNs) to never store any version of the file.
- `private`. Browsers can cache the file but intermediate caches cannot.
- `public`. The response can be stored by any cache.

Check out [Appendix: `Cache-Control` flowchart](#flowchart) to visualize the process of deciding which `Cache-Control` value(s) to use. Note also that `Cache-Control` can accept a comma-separated list of directives. See [Appendix: `Cache-Control` examples](#examples).

Along with that, setting one of two additional response headers can also help: either [`ETag`](https://developer.mozilla.org/docs/Web/HTTP/Headers/ETag) or [`Last-Modified`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Last-Modified). As mentioned in [Response headers](#response-headers), `ETag` and `Last-Modified` both serve the same purpose: determining if the browser needs to re-download a cached file that has expired. `ETag` is the recommended approach because it's more accurate.

#### ETag example

Assume that 120 seconds have passed since the initial fetch and the browser has initiated a new request for the same resource. First, the browser checks the HTTP Cache and finds the previous response. Unfortunately, the browser can't use the previous response because the response has now expired. At this point, the browser could dispatch a new request and fetch the new full response. However, that's inefficient because if the resource hasn't changed, then there's no reason to download the same information that's already in the cache! That's the problem that validation tokens, as specified in the `ETag` header, are designed to solve. The server generates and returns an arbitrary token, which is typically a hash or some other fingerprint of the contents of the file. The browser doesn't need to know how the fingerprint is generated; it only needs to send it to the server on the next request. If the fingerprint is still the same, then the resource hasn't changed and the browser can skip the download.

By setting `ETag` or `Last-Modified`, you'll end up making the revalidation request much more efficient. They end up triggering the [`If-Modified-Since`](https://developer.mozilla.org/docs/Web/HTTP/Headers/If-Modified-Since) or [`If-None-Match`](https://developer.mozilla.org/docs/Web/HTTP/Headers/If-None-Match) request headers that were mentioned in [Request headers](#request-headers).

When a properly configured web server sees those incoming request headers, it can confirm whether the version of the resource that the browser already has in its HTTP Cache matches the latest version on the web server. If there's a match, then the server can respond with a [`304 Not Modified`](https://developer.mozilla.org/docs/Web/HTTP/Status/304) HTTP response, which is the equivalent of "Hey, keep using what you've already got!" There's very little data to transfer when sending this type of response, so it's usually much faster than having to actually send back a copy of the actual resource being requested.

## <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format" alt="The browser requests /file from the server and includes the If-None-Match header to instruct the server to only return the full file if the ETag of the file on the server doesn&#39;t match the browser&#39;s If-None-Match value. In this case, the 2 values did match, so the server returns a 304 Not Modified response with instructions on how much longer the file should be cached (Cache-Control: max-age=120)." sizes="(min-width: 474px) 474px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/e2bN6glWoVbWIcwUF1uh.png?auto=format&amp;w=948 948w" width="474" height="215" /><figcaption>The browser requests <code>/file</code> from the server and includes the <code>If-None-Match</code> header to instruct the server to only return the full file if the <code>ETag</code> of the file on the server doesn't match the browser's <code>If-None-Match</code> value. In this case, the 2 values did match, so the server returns a <code>304 Not Modified</code> response with instructions on how much longer the file should be cached (<code>Cache-Control: max-age=120</code>).</figcaption></figure>Summary <a href="#summary" class="w-headline-link">#</a>

The HTTP Cache is an effective way to improve load performance because it reduces unnecessary network requests. It's supported in all browsers and doesn't take too much work to set up.

The following `Cache-Control` configurations are a good start:

- `Cache-Control: no-cache` for resources that should be revalidated with the server before every use.
- `Cache-Control: no-store` for resources that should never be cached.
- `Cache-Control: max-age=31536000` for versioned resources.

And the `ETag` or `Last-Modified` header can help you revalidate expired cache resources more efficiently.

**Try it**! Try the [HTTP Cache codelab](/codelab-http-cache) to get hands-on experience with `Cache-Control` and `ETag` in Express.

## Learn more <a href="#learn-more" class="w-headline-link">#</a>

If you're looking to go beyond the basics of using the `Cache-Control` header, check out Jake Archibald's [Caching best practices & max-age gotchas](https://jakearchibald.com/2016/caching-best-practices/) guide.

See [Love your cache](/love-your-cache) for guidance on how to optimize your cache usage for return visitors.

## Appendix: More tips <a href="#tips" class="w-headline-link">#</a>

If you have more time, here are further ways that you can optimize your usage of the HTTP Cache:

- Use consistent URLs. If you serve the same content on different URLs, then that content will be fetched and stored multiple times.
- Minimize churn. If part of a resource (such as a CSS file) updates frequently, whereas the rest of the file does not (such as library code), consider splitting the frequently updating code into a separate file and using a short duration caching strategy for the frequently updating code and a long caching duration strategy for the code that doesn't change often.
- Check out the new [`stale-while-revalidate`](/stale-while-revalidate/) directive if some degree of staleness is acceptable in your `Cache-Control` policy.

## Appendix: `Cache-Control` flowchart <a href="#flowchart" class="w-headline-link">#</a>

<img src="https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format" alt="Flowchart" sizes="(min-width: 595px) 595px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/htXr84PI8YR0lhgLPiqZ.png?auto=format&amp;w=1190 1190w" width="595" height="600" />

## Appendix: `Cache-Control` examples <a href="#examples" class="w-headline-link">#</a>

<table><thead><tr class="header"><th><code>Cache-Control</code> value</th><th>Explanation</th></tr></thead><tbody><tr class="odd"><td><code>max-age=86400</code></td><td>The response can be cached by browsers and intermediary caches for up to 1 day (60 seconds x 60 minutes x 24 hours).</td></tr><tr class="even"><td><code>private, max-age=600</code></td><td>The response can be cached by the browser (but not intermediary caches) for up to 10 minutes (60 seconds x 10 minutes).</td></tr><tr class="odd"><td><code>public, max-age=31536000</code></td><td>The response can be stored by any cache for 1 year.</td></tr><tr class="even"><td><code>no-store</code></td><td>The response is not allowed to be cached and must be fetched in full on every request.</td></tr></tbody></table>

<span class="w-mr--sm">Last updated: Apr 17, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/reliable/http-cache/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-http-cache/" class="w-callout__link w-callout__link--codelab">Configuring HTTP caching behavior</a>

<a href="/reliable" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
