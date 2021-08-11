





# Configuring HTTP caching behavior

Nov 5, 2018

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

- <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
- <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
- <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

This codelab uses Chrome DevTools. [Download Chrome](https://www.google.com/chrome) if you don't already have it.

This codelab shows you how to change the HTTP caching headers returned by a Node.js-based web server, running the [Express](https://expressjs.com/) serving framework. It will also show how to confirm that the caching behavior you expect is actually being applied, using the Network panel in Chrome's DevTools.

While the specific instructions are tailored towards Express, the general principles about choosing the correct caching headers apply to any web server environment.

## Get familiar with the sample project <a href="#get-familiar-with-the-sample-project" class="w-headline-link">#</a>

These are the key files you will be working with in the sample project:

- `server.js` contains the Node.js code that serves the web app's content. It uses [Express](https://expressjs.com/) to handle HTTP requests and responses. In particular, `express.static()` is used to serve all of the local files in the public directory, so the `serve-static` [documentation](https://expressjs.com/en/resources/middleware/serve-static.html) will come in handy.
- `public/index.html` is the web app's HTML. Like most HTML files, it does not contain any versioning information as part of its URL.
- `public/app.15261a07.js` and `public/style.391484cf.css` are the web app's JavaScript and CSS assets. These files each contain a hash in their URLs, corresponding to their contents. The `index.html` is responsible for keeping track of which specific versioned URL to load.

In the "real world", the process of assigning hashes and updating HTML files to include references to the latest versioned URL would be handled by a build tool, like [webpack](https://webpack.js.org/guides/caching/#output-filenames). For the purposes of this codelab, assume that the hashes were generated as part of a build process that already took place.

## Configure caching headers for our HTML <a href="#configure-caching-headers-for-our-html" class="w-headline-link">#</a>

When responding to requests for URLs that don't contain versioning info, make sure you add `Cache-Control: no-cache` to your response messages. Along with that, setting one of two additional response headers is recommended: either [`Last-Modified`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Last-Modified) or [`ETag`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/ETag). The `index.html` falls into this category. You can break this down into two steps.

First, the `Last-Modified` and `ETag` headers are controlled by the [`etag`](https://expressjs.com/en/resources/middleware/serve-static.html#etag) and [`lastModified`](https://expressjs.com/en/resources/middleware/serve-static.html#lastmodified) configuration options. Both of these options actually default to `true` for all HTTP responses, so in this current setup, you don't _have_ to opt-in to get that behavior. But you can be explicit in your configuration anyway.

Second, you need to be able to add in the `Cache-Control: no-cache` header, but only for your HTML documents (`index.html`, in this case). The easiest way to conditionally set this header is to write a custom [`setHeaders function`](https://expressjs.com/en/resources/middleware/serve-static.html#setheaders), and within that, check to see if the incoming request is for an HTML document.

- Click **Remix to Edit** to make the project editable.

The static serving configuration in `server.js` starts out as this:

    app.use(express.static('public'));

- Make the changes described above, and you should end up with something that looks like:

<!-- -->

    app.use(express.static('public', {
      etag: true, // Just being explicit about the default.
      lastModified: true,  // Just being explicit about the default.
      setHeaders: (res, path) => {
        if (path.endsWith('.html')) {
          // All of the project's HTML files end in .html
          res.setHeader('Cache-Control', 'no-cache');
        }
      },
    }));

## Configure caching headers for the versioned URLs <a href="#configure-caching-headers-for-the-versioned-urls" class="w-headline-link">#</a>

When responding to requests for URLs that contain "[fingerprint](<https://en.wikipedia.org/wiki/Fingerprint_(computing)>)" or versioning information, and whose contents are never meant to change, add `Cache-Control: max-age=31536000` to your responses. The `app.15261a07.js` and `style.391484cf.css` fall into this category.

Building off the [`setHeaders function`](https://expressjs.com/en/resources/middleware/serve-static.html#setheaders) used in the last step, you can add in additional logic to check whether a given request is for a versioned URL, and if so, add the `Cache-Control: max-age=31536000` header.

The most robust way of doing this is to use a [regular expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Regular_Expressions) to see whether the asset being requested matches a specific pattern that you know the hashes fall into. In the case of this sample project, it's always eight characters from the set of digits 0–9 and the lowercase letters a–f (i.e. [hexadecimal](https://en.wikipedia.org/wiki/Hexadecimal) characters). The hash is always separated by a `.` character on either side.

A regular expression that [matches those general rules](https://jex.im/regulex/#!flags=&re=%5C.%5B0-9a-f%5D%7B8%7D%5C.) can be expressed as `new RegExp('\\.[0-9a-f]{8}\\.')`.

It helps to be as specific as possible when coming up with these rules, to protect against future problems. A more general match, such as checking for the `.js` or `.css` file extension, could end up being a problem down the road if you end up adding in additional, unversioned JavaScript or CSS assets to your project.

- Modify the `setHeaders` function so it looks like this:

<!-- -->

    app.use(express.static('public', {
      etag: true, // Just being explicit about the default.
      lastModified: true,  // Just being explicit about the default.
      setHeaders: (res, path) => {
        const hashRegExp = new RegExp('\\.[0-9a-f]{8}\\.');

        if (path.endsWith('.html')) {
          // All of the project's HTML files end in .html
          res.setHeader('Cache-Control', 'no-cache');
        } else if (hashRegExp.test(path)) {
          // If the RegExp matched, then we have a versioned URL.
          res.setHeader('Cache-Control', 'max-age=31536000');
        }
      },
    }));

## Confirm the new behavior using DevTools <a href="#confirm-the-new-behavior-using-devtools" class="w-headline-link">#</a>

You can get familiar with the Network panel in Chrome's DevTools by working through [this codelab](/codelab-explore-network-panel).

With the modifications to the static file server in place, you can check to make sure that the right headers are being set by previewing the live app with the DevTools Network panel open.

- To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

- Customize the columns that are displayed in the Network panel to include the information that is most relevant, by right-clicking in the column header:

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format" alt="Configuring DevTools&#39; Network panel." class="screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/L98OANnCWWOU36dTwd8r.png?auto=format&amp;w=1600 1600w" width="800" height="931" />

Here, the columns to pay attention to are `Name`, `Status`, `Cache-Control`, `ETag`, and `Last-Modified`.

- With the DevTools open to the Network panel, refresh the page.

After the page has loaded, you should see entries in the Network panel that look like the following:

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format" alt="Network panel columns." class="screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/PQbDCXUvXPlqThlPbLIp.png?auto=format&amp;w=1600 1600w" width="800" height="172" />

The first row is for the HTML document that you navigated to. This is properly served with `Cache-Control: no-cache`. The HTTP response status for that request is a [`304`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/304). This means that the browser knew not to use the cached HTML immediately, but instead made an HTTP request to the web server, using the `Last-Modified` and `ETag` information to see if there was any update to the HTML that it already had in its cache. The HTTP 304 response indicates that there is not updated HTML.

`Cache-Control: no-cache` doesn't mean "never used the cached copy". It means "always check with the server first, and use the cached copy if there's a HTTP 304 response."

The next two rows are for the versioned JavaScript and CSS assets. You should see them served with `Cache-Control: max-age=31536000`, and the HTTP status for each is [`200`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status/200). Because of the configuration used, there is no actual request being made to the Node.js server, and clicking on the entry will show you additional detail, including that the response came "(from disk cache)".

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format" alt="A network response status of 200." class="screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bx1DtsiX7e9tdOSf1ogZ.png?auto=format&amp;w=1600 1600w" width="800" height="175" />

The actual values for the ETag and Last-Modified columns don't matter much. The important thing is to confirm that they're being set.

## Summing things up <a href="#summing-things-up" class="w-headline-link">#</a>

Having gone through the steps in this codelab, you're now familiar with how to configure the HTTP response headers in a Node.js-based web server using Express, for optimal use of the HTTP cache. You also have the steps you need to confirm that the expected caching behavior is being used, via the Network panel in Chrome's DevTools.

<a href="/http-cache" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to article</a>

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
