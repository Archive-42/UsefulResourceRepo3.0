## <a href="#ensure-csp-is-effective-against-xss-attacks" class="w-toc__header--link">Ensure CSP is effective against XSS attacks</a>

- [Required practices for a non-bypassable CSP](#required-practices-for-a-non-bypassable-csp)
- [CSP targets XSS](#csp-targets-xss)
- [CSP uses nonces or hashes to avoid allowlist bypasses](#csp-uses-nonces-or-hashes-to-avoid-allowlist-bypasses)
- [Additional recommendations for a secure CSP](#additional-recommendations-for-a-secure-csp)
- [Configure CSP reporting](#configure-csp-reporting)
- [Define the CSP in an HTTP header](#define-the-csp-in-an-http-header)
- [Ensure CSP is backwards compatible](#ensure-csp-is-backwards-compatible)
- [How to develop a strict CSP](#how-to-develop-a-strict-csp)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Ensure CSP is effective against XSS attacks

Jun 16, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-best-practices" class="w-post-signpost__link">Best Practices audits</a>

A Content Security Policy (CSP) helps to ensure any content loaded in the page is trusted by the site owner. CSPs mitigate cross-site scripting (XSS) attacks because they can block unsafe scripts injected by attackers. However, the CSP can easily be bypassed if it is not strict enough. Check out [Mitigate cross-site scripting (XSS) with a strict Content Security Policy (CSP)](/strict-csp/) for more information. Lighthouse collects CSPs enforced on the main document, and reports issues from [CSP Evaluator](https://csp-evaluator.withgoogle.com/) if they can be bypassed.

## <figure><img src="https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format" alt="Lighthouse report warning that no CSP is found in enforcement mode." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/9B7J9oWjgsWbuE84mmxDaY37Wpw2/EFTWlPiCrPOn6ETCRiGr.png?auto=format&amp;w=1600 1600w" width="800" height="165" /><figcaption>Lighthouse report warning that no CSP is found in enforcement mode.</figcaption></figure>Required practices for a non-bypassable CSP <a href="#required-practices-for-a-non-bypassable-csp" class="w-headline-link">#</a>

Implement the following practices to ensure that your CSP can't be bypassed. If the CSP can be bypassed, Lighthouse will emit a high severity warning.

### CSP targets XSS <a href="#csp-targets-xss" class="w-headline-link">#</a>

To target XSS, a CSP should include the `script-src`, `object-src`, and `base-uri` directives. The CSP should also be free of syntax errors.

`script-src` and `object-src` secures a page from unsafe scripts and unsafe plugins respectively. Alternatively, `default-src` can be used to configure a broad policy in place of [many directives](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Content-Security-Policy/default-src) including `script-src` and `object-src`.

`base-uri` prevents the injection of unauthorized `<base>` tags which can be used to redirect all relative URLs (like scripts) to an attacker-controlled domain.

### CSP uses nonces or hashes to avoid allowlist bypasses <a href="#csp-uses-nonces-or-hashes-to-avoid-allowlist-bypasses" class="w-headline-link">#</a>

A CSP that configures an allowlist for `script-src` relies on the assumption that all responses coming from a trusted domain are safe, and can be executed as scripts. However, this assumption does not hold for modern applications; some common, benign patterns such as exposing [JSONP interfaces](https://lcamtuf.blogspot.ch/2011/08/subtle-deadly-problem-with-csp.html) and [hosting copies of the AngularJS library](https://github.com/cure53/XSSChallengeWiki/wiki/H5SC-Minichallenge-3:-%22Sh*t,-it's-CSP!%22) allow attackers to escape the confines of CSP.

In practice, while it may not be obvious to application authors, [the majority of `script-src` allowlists can be circumvented](https://research.google.com/pubs/pub45542.html) by an attacker with an XSS bug, and provide little protection against script injection. In contrast, the [nonce-based and hash-based approaches](https://web.dev/strict-csp/#what-is-a-strict-content-security-policy) do not suffer from these problems and make it easier to adopt and maintain a more secure policy.

For example, this code uses a JSONP endpoint hosted on a trusted domain to inject an attacker controlled script:

CSP:

    script-src https://trusted.example.com

HTML:

    <script src="https://trusted.example.com/path/jsonp?callback=alert(document.domain)//"></script>

To avoid being bypassed, a CSP should allow scripts individually using nonces or hashes and use 'strict-dynamic' instead of an allowlist.

## Additional recommendations for a secure CSP <a href="#additional-recommendations-for-a-secure-csp" class="w-headline-link">#</a>

Implement the following practices for added security and compatibility. If the CSP does not follow one of the recommendations, Lighthouse will emit a medium severity warning.

### Configure CSP reporting <a href="#configure-csp-reporting" class="w-headline-link">#</a>

[Configuring a reporting destination](https://developers.google.com/web/updates/2018/09/reportingapi) will help monitor for any breakages. You can set the reporting destination by using the `report-uri` or `report-to` directives. `report-to` is not currently supported by all modern browsers so it is recommended to use both or just `report-uri`.

If any content violates the CSP, the browser will send a report to the configured destination. Make sure you have an application configured at this destination handling these reports.

### Define the CSP in an HTTP header <a href="#define-the-csp-in-an-http-header" class="w-headline-link">#</a>

A CSP can be defined in a meta tag like this:

    <meta http-equiv="Content-Security-Policy" content="script-src 'none'">

However, you should define a CSP in an HTTP response header if you can. An injection before the meta tag will bypass the CSP. Additionally, `frame-ancestors`, `sandbox` and reporting are not supported in meta tag CSPs.

### Ensure CSP is backwards compatible <a href="#ensure-csp-is-backwards-compatible" class="w-headline-link">#</a>

Not all browsers support CSP nonces/hashes, therefore adding `unsafe-inline` as a fallback for non-compliant browsers is recommended. If the browser does support nonces/hashes, `unsafe-inline` will be ignored.

Similarly, `strict-dynamic` is not supported by all browsers. It is recommended to set an allowlist as a fallback for any non-compliant browsers. The allowlist will be ignored in browsers that support `strict-dynamic`.

## How to develop a strict CSP <a href="#how-to-develop-a-strict-csp" class="w-headline-link">#</a>

Below is an example of using a strict CSP with a nonce-based policy.

CSP:

    script-src 'nonce-random123' 'strict-dynamic' 'unsafe-inline' https:;
    object-src 'none';
    base-uri 'none';
    report-uri https://reporting.example.com;

HTML:

    <script nonce="random123" src="https://trusted.example.com/trusted_script.js"></script>

`random123` would be any base64 string generated server-side every time the page loads. `unsafe-inline` and `https:` are ignored in modern browsers because of the nonce and `strict-dynamic`. For more information about adopting a strict CSP, check out the [Strict CSP guide](https://web.dev/strict-csp/#adopting-a-strict-csp).

You can check a CSP for potential bypasses using Lighthouse and [CSP Evaluator](https://csp-evaluator.withgoogle.com/). If you want to test a new CSP without the risk of breaking existing pages, define the CSP in report-only mode by using `Content-Security-Policy-Report-Only` as the header name. This will send CSP violations to any reporting destinations you have configured with `report-to` and `report-uri`, but it will not actually enforce the CSP.

<span class="w-mr--sm">Last updated: Jun 16, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-best-practices/csp-xss/index.md)

<a href="/lighthouse-best-practices" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
