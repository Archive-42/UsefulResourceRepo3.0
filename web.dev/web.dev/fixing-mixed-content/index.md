## <a href="#fixing-mixed-content" class="w-toc__header--link">Fixing mixed content</a>

- [Finding mixed content by visiting your site](#finding-mixed-content-by-visiting-your-site)
- [Finding mixed content in your site](#finding-mixed-content-in-your-site)
- [Fixing mixed content](#fixing-mixed-content)
- [Beware of non-standard tag usage](#beware-of-non-standard-tag-usage)
- [Handle mixed content at scale](#handle-mixed-content-at-scale)
- [Content security policy](#content-security-policy)
- [Finding mixed content with content security policy](#finding-mixed-content-with-content-security-policy)
- [Alternatives to reporting with CSP](#alternatives-to-reporting-with-csp)
- [Upgrading insecure requests](#upgrading-insecure-requests)
- [Blocking all mixed content](#blocking-all-mixed-content)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Fixing mixed content

Sep 7, 2019 <span class="w-author__separator">•</span> Updated Sep 23, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/secure" class="w-post-signpost__link">Safe and secure</a>

[<img src="https://web-dev.imgix.net/image/admin/Qfxylpir4hHF23rUgEQP.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jo-el van Bergen" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Qfxylpir4hHF23rUgEQP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/Qfxylpir4hHF23rUgEQP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/Qfxylpir4hHF23rUgEQP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/Qfxylpir4hHF23rUgEQP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/Qfxylpir4hHF23rUgEQP.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/johyphenel/)

<a href="/authors/johyphenel/" class="w-author__name-link">Jo-el van Bergen</a>

- <a href="https://twitter.com/johyphenel" class="w-author__link">Twitter</a>

[<img src="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rachel Andrew" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rachelandrew/)

<a href="/authors/rachelandrew/" class="w-author__name-link">Rachel Andrew</a>

- <a href="https://twitter.com/rachelandrew" class="w-author__link">Twitter</a>
- <a href="https://github.com/rachelandrew" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@rachelandrew" class="w-author__link">Glitch</a>
- <a href="https://rachelandrew.co.uk/" class="w-author__link">Blog</a>

Supporting HTTPS for your website is an important step to protecting your site and your users from attack, but mixed content can render that protection useless. Increasingly insecure mixed content will be blocked by browsers, as explained in [What is mixed content?](/what-is-mixed-content)

In this guide we will demonstrate techniques and tools for fixing existing mixed content issues and preventing new ones from happening.

## Finding mixed content by visiting your site <a href="#finding-mixed-content-by-visiting-your-site" class="w-headline-link">#</a>

When visiting an HTTPS page in Google Chrome, the browser alerts you to mixed content as errors and warnings in the JavaScript console.

In [What is mixed content?](/what-is-mixed-content), you can find a number of examples and see how the problems are reported in Chrome DevTools.

The example of [passive mixed content](https://passive-mixed-content.glitch.me/) will give the following warnings. If the browser is able to find the content at an `https` URL it automatically upgrades it, then shows a message.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Y7b4EWAbSL6BgI07FdQq.jpg?auto=format&amp;w=1600 1600w" width="800" height="294" /></figure>[Active mixed content](https://active-mixed-content.glitch.me/) is blocked and displays a warning.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/KafrfEz1adCP2eUHQEWy.jpg?auto=format&amp;w=1600 1600w" width="800" height="304" /></figure>If you find warnings like these for `http://` URLs on your site, you need to fix them in your site's source. It's helpful to make a list of these URLs, along with the page you found them on, for use when you fix them.

Mixed content errors and warnings are only shown for the page you are currently viewing, and the JavaScript console is cleared every time you navigate to a new page. This means you will have to view every page of your site individually to find these errors.

### Finding mixed content in your site <a href="#finding-mixed-content-in-your-site" class="w-headline-link">#</a>

You can search for mixed content directly in your source code. Search for `http://` in your source and look for tags that include HTTP URL attributes. Note that having `http://` in the `href` attribute of anchor tags (`<a>`) is often not a mixed content issue, with some notable exceptions discussed later.

If your site is published using a content management system, it is possible that links to insecure URLs are inserted when pages are published. For example, images may be included with a full URL rather than a relative path. You will need to find and fix these within the CMS content.

### Fixing mixed content <a href="#fixing-mixed-content" class="w-headline-link">#</a>

Once you've found mixed content in your site's source, you can follow these steps to fix it.

If you get a console message that a resource request has been automatically upgraded from HTTP to HTTPS, you can safely change the `http://` URL for the resource in your code to `https://`. You can also check to see if a resource is available securely by changing `http://` to `https://` in the browser URL bar and attempting to open the URL in a browser tab.

If the resource is not available via `https://`, you should consider one of the following options:

- Include the resource from a different host, if one is available.
- Download and host the content on your site directly, if you are legally allowed to do so.
- Exclude the resource from your site altogether.

Having fixed the problem, view the page where you found the error originally and verify that the error no longer appears.

### Beware of non-standard tag usage <a href="#beware-of-non-standard-tag-usage" class="w-headline-link">#</a>

Beware of non-standard tag usage on your site. For instance, anchor (`<a>`) tag URLs don't result in mixed content errors, as they cause the browser to navigate to a new page. This means they usually don't need to be fixed. However some image gallery scripts override the functionality of the `<a>` tag and load the HTTP resource specified by the `href` attribute into a lightbox display on the page, causing a mixed content problem.

## Handle mixed content at scale <a href="#handle-mixed-content-at-scale" class="w-headline-link">#</a>

The manual steps above work well for smaller websites; but for large websites or sites with many separate development teams, it can be tough to keep track of all the content being loaded. To help with this task, you can use content security policy to instruct the browser to notify you about mixed content and ensure that your pages never unexpectedly load insecure resources.

### Content security policy <a href="#content-security-policy" class="w-headline-link">#</a>

[Content security policy](https://developers.google.com/web/fundamentals/security/csp/) (CSP) is a multi-purpose browser feature that you can use to manage mixed content at scale. The CSP reporting mechanism can be used to track mixed content on your site, and provide enforcement policies to protect users by upgrading or blocking mixed content.

You can enable these features for a page by including the `Content-Security-Policy` or `Content-Security-Policy-Report-Only` header in the response sent from your server. Additionally you can set `Content-Security-Policy` (though **not** `Content-Security-Policy-Report-Only`) using a `<meta>` tag in the `<head>` section of your page.

Modern browsers enforce all content security policies that they receive. Multiple CSP header values received by the browser in the response header or `<meta>` elements are combined and enforced as a single policy; reporting policies are likewise combined. Policies are combined by taking the intersection of the policies; that is to say, each policy after the first can only further restrict the allowed content, not broaden it.

### Finding mixed content with content security policy <a href="#finding-mixed-content-with-content-security-policy" class="w-headline-link">#</a>

You can use content security policy to collect reports of mixed content on your site. To enable this feature, set the `Content-Security-Policy-Report-Only` directive by adding it as a response header for your site.

Response header:

`Content-Security-Policy-Report-Only: default-src https: 'unsafe-inline' 'unsafe-eval'; report-uri https://example.com/reportingEndpoint`

The [report-uri](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/report-uri) response header is being deprecated in favor of [report-to](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/report-to). Browser support for `report-to` is currently limited to Chrome and Edge. You can provide both headers, in which case `report-uri` will be ignored if the browser supports `report-to`.

Whenever a user visits a page on your site, their browser sends JSON-formatted reports regarding anything that violates the content security policy to `https://example.com/reportingEndpoint`. In this case, anytime a subresource is loaded over HTTP, a report is sent. These reports include the page URL where the policy violation occurred and the subresource URL that violated the policy. If you configure your reporting endpoint to log these reports, you can track the mixed content on your site without visiting each page yourself.

The two caveats to this are:

- Users have to visit your page in a browser that understands the CSP header. This is true for most modern browsers.
- You only get reports for pages visited by your users. So if you have pages that don't get much traffic, it might be some time before you get reports for your entire site.

The [Content security policy](https://developers.google.com/web/fundamentals/security/csp/) guide has more information and an example endpoint.

### Alternatives to reporting with CSP <a href="#alternatives-to-reporting-with-csp" class="w-headline-link">#</a>

If your site is hosted for you by a platform such as Blogger, you may not have access to modify headers and add a CSP. Instead, a viable alternative could be to use a website crawler to find issues across your site for you, such as [HTTPSChecker](https://httpschecker.net/how-it-works#httpsChecker) or [Mixed Content Scan](https://github.com/bramus/mixed-content-scan).

### Upgrading insecure requests <a href="#upgrading-insecure-requests" class="w-headline-link">#</a>

Browsers are beginning to upgrade and block insecure requests. You can use CSP directives to force automatic upgrading or blocking of these assets.

The [`upgrade-insecure-requests`](https://www.w3.org/TR/upgrade-insecure-requests/) CSP directive instructs the browser to upgrade insecure URLs before making network requests.

As an example, if a page contains an image tag with an HTTP URL such as `<img src="http://example.com/image.jpg">`

The browser instead makes a secure request for `https://example.com/image.jpg`, thus saving the user from mixed content.

You can enable this behavior either by sending a `Content-Security-Policy` header with this directive:

    Content-Security-Policy: upgrade-insecure-requests

Or by embedding that same directive inline in the document's `<head>` section using a `<meta>` element:

    <meta http-equiv="Content-Security-Policy" content="upgrade-insecure-requests">

As with browser automatic upgrading, if the resource is not available over HTTPS, the upgraded request fails and the resource is not loaded. This maintains the security of your page. The `upgrade-insecure-requests` directive will go further than automatic browser upgrading, attempting to upgrade requests that the browser currently does not.

The `upgrade-insecure-requests` directive cascades into `<iframe>` documents, ensuring the entire page is protected.

### Blocking all mixed content <a href="#blocking-all-mixed-content" class="w-headline-link">#</a>

An alternative option for protecting users is the [`block-all-mixed-content`](https://www.w3.org/TR/mixed-content/#strict-checking) CSP directive. This directive instructs the browser to never load mixed content; all mixed content resource requests are blocked, including both active and passive mixed content. This option also cascades into `<iframe>` documents, ensuring the entire page is mixed content free.

A page can opt itself into this behavior either by sending a `Content-Security-Policy` header with this directive:

    Content-Security-Policy: block-all-mixed-content

Or by embedding that same directive inline in the document's `<head>` section using a `<meta>` element:

    <meta http-equiv="Content-Security-Policy" content="block-all-mixed-content">

If you set both `upgrade-insecure-requests` and `block-all-mixed-content` `upgrade-insecure-requests` will be evaluated and used first. The browser will not go on to block requests. Therefore you should use one or the other.

<a href="/tags/security/" class="w-chip">Security</a> <a href="/tags/network/" class="w-chip">Network</a> <a href="/tags/privacy/" class="w-chip">Privacy</a> <a href="/tags/html/" class="w-chip">HTML</a> <a href="/tags/css/" class="w-chip">CSS</a> <a href="/tags/javascript/" class="w-chip">JavaScript</a> <a href="/tags/images/" class="w-chip">Images</a> <a href="/tags/media/" class="w-chip">Media</a>

<span class="w-mr--sm">Last updated: Sep 23, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/secure/fixing-mixed-content/index.md)

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
