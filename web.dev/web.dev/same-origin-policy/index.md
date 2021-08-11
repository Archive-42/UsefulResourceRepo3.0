





<a href="#same-origin-policy" class="w-toc__header--link">Same-origin policy</a>
--------------------------------------------------------------------------------

-   [What's considered same-origin?](#what's-considered-same-origin)
-   [What is permitted and what is blocked?](#what-is-permitted-and-what-is-blocked)
-   [How to prevent Clickjacking](#how-to-prevent-clickjacking)
-   [Wrap up](#wrap-up)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Same-origin policy
==================

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/secure" class="w-post-signpost__link">Safe and secure</a>

[<img src="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Mariko Kosaka" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/kosamari/)

<a href="/authors/kosamari/" class="w-author__name-link">Mariko Kosaka</a>

-   <a href="https://twitter.com/kosamari" class="w-author__link">Twitter</a>
-   <a href="https://github.com/kosamari" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@kosamari" class="w-author__link">Glitch</a>
-   <a href="https://kosamari.com/" class="w-author__link">Blog</a>

The same-origin policy is a browser security feature that restricts how documents and scripts on one origin can interact with resources on another origin.

A browser can load and display resources from multiple sites at once. You might have multiple tabs open at the same time, or a site could embed multiple iframes from different sites. If there is no restriction on interactions between these resources, and a script is compromised by an attacker, the script could expose everything in a user's browser.

The same-origin policy prevents this from happening by blocking read access to resources loaded from a different origin. "But wait," you say, "I load images and scripts from other origins *all the time*." Browsers allow a few tags to embed resources from a different origin. This policy is mostly a historical artifact and can expose your site to vulnerabilities such as [clickjacking using iframes](#how-to-prevent-clickjacking). You can restrict cross-origin reading of these tags using a [Content Security Policy](https://developers.google.com/web/fundamentals/security/csp/).

What's considered same-origin? <a href="#what&#39;s-considered-same-origin" class="w-headline-link">#</a>
---------------------------------------------------------------------------------------------------------

An origin is defined by the scheme (also known as the protocol, for example HTTP or HTTPS), port (if it is specified), and host. When all three are the same for two URLs, they are considered same-origin. For example, `http://www.example.com/foo` is the same origin as `http://www.example.com/bar` but not `https://www.example.com/bar` because the scheme is different.

**Try it**! [See how the same-origin policy works when fetching resources](/codelab-same-origin-fetch).

What is permitted and what is blocked? <a href="#what-is-permitted-and-what-is-blocked" class="w-headline-link">#</a>
---------------------------------------------------------------------------------------------------------------------

Generally, embedding a cross-origin resource is permitted, while reading a cross-origin resource is blocked.

<table><tbody><tr class="odd"><td>iframes</td><td>Cross-origin embedding is usually permitted (depending on the <code>X-Frame-Options</code> directive), but cross-origin reading (such as using JavaScript to access a document in an iframe) isn't.</td></tr><tr class="even"><td>CSS</td><td>Cross-origin CSS can be embedded using a <code>&lt;link&gt;</code> element or an <code>@import</code> in a CSS file. The correct <code>Content-Type</code> header may be required.</td></tr><tr class="odd"><td>forms</td><td>Cross-origin URLs can be used as the <code>action</code> attribute value of form elements. A web application can write form data to a cross-origin destination.</td></tr><tr class="even"><td>images</td><td>Embedding cross-origin images is permitted. However, reading cross-origin images (such as loading a cross-origin image into a <code>canvas</code> element using JavaScript) is blocked.</td></tr><tr class="odd"><td>multimedia</td><td>Cross-origin video and audio can be embedded using <code>&lt;video&gt;</code> and <code>&lt;audio&gt;</code> elements.</td></tr><tr class="even"><td>script</td><td>Cross-origin scripts can be embedded; however, access to certain APIs (such as cross-origin fetch requests) might be blocked.</td></tr></tbody></table>

**Try it**! [See how the same-origin policy works when accessing data inside an iframe](/codelab-same-origin-iframe).

Check whether specified actions in cross-origin resources are allowed

A webpage on the web.dev domain includes this iframe:

    <iframe id="iframe" src="https://example.com/some-page.html" alt="Sample iframe"></iframe>

The webpage's JavaScript includes this code to get the text content from an element in the embedded page:

    const iframe = document.getElementById('iframe');
    const message = iframe.contentDocument.getElementById('message').innerText;

Is this JavaScript allowed?

**No**. Since the iframe is not on the same origin as the host webpage, the browser doesn't allow reading of the embedded page.

A webpage on the web.dev domain includes this form:

    <form action="https://example.com/results.json">
      <label for="email">Enter your email: </label>
      <input type="email" name="email" id="email" required>
      <button type="submit">Subscribe</button>
    </form>

Can this form be submitted?

**Yes**. Form data can be written to a cross-origin URL specified in the `action` attribute of the `<form>` element.

A webpage on the web.dev domain includes this iframe:

    <iframe src="https://example.com/some-page.html" alt="Sample iframe"></iframe>

Is this iframe embed allowed?

**Usually**. Cross-origin iframe embeds are allowed as long as the origin owner hasn't set the [`X-Frame-Options`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options) HTTP header to `deny` or `sameorigin`.

A webpage on the web.dev domain includes this canvas:

    <canvas id="bargraph"></canvas>

The webpage's JavaScript includes this code to draw an image on the canvas:

    var context = document.getElementById('bargraph').getContext('2d');
    var img = new Image();
      img.onload = function() {
      context.drawImage(img, 0, 0);
    };
    img.src = 'https://example.com/graph-axes.svg';

Can this image be drawn on the canvas?

**It depends!** 😅 The image is on a different origin. If the origin's owner gave the image the appropriate [CORS header](/cross-origin-resource-sharing), the image can be safely drawn. If not, the image will [cause an error](https://developer.mozilla.org/en-US/docs/Web/HTML/CORS_enabled_image#What_is_a_.22tainted.22_canvas.3F).

### How to prevent Clickjacking <a href="#how-to-prevent-clickjacking" class="w-headline-link">#</a>

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format" alt="Figure: Clickjacking mechanism illustrated in 3 separate layers (base site, iframed site, transparent button)." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jFXSbDjBonhdGD65rCc1.png?auto=format&amp;w=1600 1600w" width="800" height="408" /><figcaption>Figure: Clickjacking mechanism illustrated in 3 separate layers (base site, iframed site, transparent button).</figcaption></figure>An attack called "clickjacking" embeds a site in an `iframe` and overlays transparent buttons which link to a different destination. Users are tricked into thinking they are accessing your application while sending data to attackers.

To block other sites from embedding your site in an iframe, add a content security policy with [`frame-ancestors` directive](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) to the HTTP headers.

Alternatively, you can add `X-Frame-Options` to the HTTP headers see [MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/X-Frame-Options) for list of options.

Wrap up <a href="#wrap-up" class="w-headline-link">#</a>
--------------------------------------------------------

Hopefully you feel a little relieved that browsers work hard to be a gatekeeper of security on the web. Even though browsers try to be safe by blocking access to resources, sometimes you want to access cross-origin resources in your applications. In the next guide, learn about Cross-Origin Resource Sharing (CORS) and how to tell the browser that loading of cross-origin resources is allowed from trusted sources.

<a href="/tags/security/" class="w-chip">Security</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/secure/same-origin-policy/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-same-origin-fetch/" class="w-callout__link w-callout__link--codelab">Same Origin Policy &amp; Fetch requests</a>
-   <a href="/codelab-same-origin-iframe/" class="w-callout__link w-callout__link--codelab">Same Origin Policy &amp; iframe</a>

<a href="/secure" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
