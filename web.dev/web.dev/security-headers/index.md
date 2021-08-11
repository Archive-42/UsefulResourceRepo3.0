





<img src="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format" alt="A keylock in front of compressed code" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/E3BVnrBFNV6w2Uqxn3bQ.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

<a href="#security-headers-quick-reference" class="w-toc__header--link">Security headers quick reference</a>
------------------------------------------------------------------------------------------------------------

-   [Protect your site from injection vulnerabilities](#protect-your-site-from-injection-vulnerabilities)
-   [Content Security Policy (CSP)](#csp)
-   [Isolate your site from other websites](#isolate-your-site-from-other-websites)
-   [Trusted Types](#tt)
-   [Build a powerful website securely](#build-a-powerful-website-securely)
-   [X-Content-Type-Options](#xcto)
-   [Encrypt traffic to your site](#encrypt-traffic-to-your-site)
-   [X-Frame-Options](#xfo)
-   [Recommended usages](#recommended-usages)
-   [Cross-Origin Resource Policy (CORP)](#corp)
-   [Supported browsers](#supported-browsers)
-   [Cross-Origin Opener Policy (COOP)](#coop)
-   [Other things to note about CSP](#other-things-to-note-about-csp)
-   [Cross-Origin Resource Sharing (CORS)](#cors)
-   [Learn more](#learn-more)
-   [Cross-Origin Embedder Policy (COEP)](#coep)
-   [Recommended usages](#recommended-usages-2)
-   [HTTP Strict Transport Security (HSTS)](#hsts)
-   [Supported browsers](#supported-browsers-2)
-   [Further reading](#further-reading)
-   [Learn more](#learn-more-2)
-   [Recommended usages](#recommended-usages-3)
-   [Supported browsers](#supported-browsers-3)
-   [Learn more](#learn-more-3)
-   [Recommended usages](#recommended-usages-4)
-   [Supported browsers](#supported-browsers-4)
-   [Learn more](#learn-more-4)
-   [Recommended usages](#recommended-usages-5)
-   [Supported browsers](#supported-browsers-5)
-   [Learn more](#learn-more-5)
-   [Recommended usages](#recommended-usages-6)
-   [Supported browsers](#supported-browsers-6)
-   [Learn more](#learn-more-6)
-   [Recommended usages](#recommended-usages-7)
-   [Supported browsers](#supported-browsers-7)
-   [Learn more](#learn-more-7)
-   [Example usages](#example-usages)
-   [Supported browsers](#supported-browsers-8)
-   [Learn more](#learn-more-8)
-   [Recommended usages](#recommended-usages-8)
-   [Supported browsers](#supported-browsers-9)
-   [Learn more](#learn-more-9)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

-   <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
-   <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

Security headers quick reference
================================

Learn more about headers that can keep your site safe and quickly look up the most important details.

May 18, 2021 <span class="w-author__separator">•</span> Updated Aug 5, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/secure" class="w-post-signpost__link">Safe and secure</a>

[<img src="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Eiji Kitamura" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/agektmr/)

<a href="/authors/agektmr/" class="w-author__name-link">Eiji Kitamura</a>

-   <a href="https://twitter.com/agektmr" class="w-author__link">Twitter</a>
-   <a href="https://github.com/agektmr" class="w-author__link">GitHub</a>
-   <a href="https://blog.agektmr.com" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/F620GZorjY0JjKas3p3J.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Maud Nalpas" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/F620GZorjY0JjKas3p3J.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/F620GZorjY0JjKas3p3J.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/F620GZorjY0JjKas3p3J.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/F620GZorjY0JjKas3p3J.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/F620GZorjY0JjKas3p3J.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/maudn/)

<a href="/authors/maudn/" class="w-author__name-link">Maud Nalpas</a>

-   <a href="https://twitter.com/maudnals" class="w-author__link">Twitter</a>
-   <a href="https://github.com/maudnals" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/hwvmzV4b6VQpTNrNF3wK.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Artur Janc" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/hwvmzV4b6VQpTNrNF3wK.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/hwvmzV4b6VQpTNrNF3wK.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/hwvmzV4b6VQpTNrNF3wK.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/hwvmzV4b6VQpTNrNF3wK.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/hwvmzV4b6VQpTNrNF3wK.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/arturjanc/)

<a href="/authors/arturjanc/" class="w-author__name-link">Artur Janc</a>

-   <a href="https://twitter.com/arturjanc" class="w-author__link">Twitter</a>
-   <a href="https://github.com/arturjanc" class="w-author__link">GitHub</a>

This article lists the most important security headers you can use to protect your website. Use it to understand web-based security features, learn how to implement them on your website, and as a reference for when you need a reminder.

Security headers recommended for websites that handle sensitive user data:  
[Content Security Policy (CSP)](#csp)

[Trusted Types](#tt)

Security headers recommended for all websites:  
[X-Content-Type-Options](#xcto)

[X-Frame-Options](#xfo)

[Cross-Origin Resource Policy (CORP)](#corp)

[Cross-Origin Opener Policy (COOP)](#coop)

[HTTP Strict Transport Security (HSTS)](#hsts)

Security headers for websites with advanced capabilities:  
[Cross-Origin Resource Sharing (CORS)](#cors)

[Cross-Origin Embedder Policy (COEP)](#coep)

Known threats on the web
------------------------

Before diving into security headers, learn about known threats on the web and why you'd want to use these security headers.

Before diving into security headers, learn about known threats on the web and why you'd want to use these security headers.

### Protect your site from injection vulnerabilities <a href="#protect-your-site-from-injection-vulnerabilities" class="w-headline-link">#</a>

Injection vulnerabilities arise when untrusted data processed by your application can affect its behavior and, commonly, lead to the execution of attacker-controlled scripts. The most common vulnerability caused by injection bugs is [cross-site scripting](https://portswigger.net/web-security/cross-site-scripting) (XSS) in its various forms, including [reflected XSS](https://portswigger.net/web-security/cross-site-scripting/reflected), [stored XSS](https://portswigger.net/web-security/cross-site-scripting/stored), [DOM-based XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based), and other variants.

An XSS vulnerability can typically give an attacker complete access to user data processed by the application and any other information hosted in the same [web origin](/same-site-same-origin/#origin).

Traditional defenses against injections include consistent use of autoescaping HTML template systems, avoiding the use of [dangerous JavaScript APIs](https://domgo.at/cxss/sinks), and properly processing user data by hosting file uploads in a separate domain and sanitizing user-controlled HTML.

-   Use [Content Security Policy (CSP)](#csp) to control which scripts can be executed by your application to mitigate the risk of injections.
-   Use [Trusted Types](#tt) to enforce sanitization of data passed into dangerous JavaScript APIs.
-   Use [X-Content-Type-Options](#xcto) to prevent the browser from misinterpreting the MIME types of your website's resources, which can lead to script execution.

### Isolate your site from other websites <a href="#isolate-your-site-from-other-websites" class="w-headline-link">#</a>

The openness of the web allows websites to interact with each other in ways that can violate an application's security expectations. This includes unexpectedly making authenticated requests or embedding data from another application in the attacker's document, allowing the attacker to modify or read application data.

Common vulnerabilities that undermine web isolation include [clickjacking](https://portswigger.net/web-security/clickjacking), [cross-site request forgery](https://portswigger.net/web-security/csrf) (CSRF), [cross-site script inclusion](https://www.scip.ch/en/?labs.20160414) (XSSI), and various [cross-site leaks](https://xsleaks.dev).

-   Use [X-Frame-Options](#xfo) to prevent your documents from being embedded by a malicious website.
-   Use [Cross-Origin Resource Policy (CORP)](#corp) to prevent your website's resources from being included by a cross-origin website.
-   Use [Cross-Origin Opener Policy (COOP)](#coop) to protect your website's windows from interactions by malicious websites.
-   Use [Cross-Origin Resource Sharing (CORS)](#cors) to control access to your website's resources from cross-origin documents.

[Post-Spectre Web Development](https://www.w3.org/TR/post-spectre-webdev/) is a great read if you are interested in these headers.

### Build a powerful website securely <a href="#build-a-powerful-website-securely" class="w-headline-link">#</a>

[Spectre](https://ieeexplore.ieee.org/document/8835233) puts any data loaded into the same [browsing context group](/why-coop-coep/) potentially readable despite [same-origin policy](/same-origin-policy/). Browsers restrict features that may possibly exploit the vulnerability behind a special environment called "[cross-origin isolation](/coop-coep/)". With cross-origin isolation, you can use powerful features such as `SharedArrayBuffer`.

-   Use [Cross-Origin Embedder Policy (COEP)](#coep) along with [COOP](#coop) to enable cross-origin isolation.

### Encrypt traffic to your site <a href="#encrypt-traffic-to-your-site" class="w-headline-link">#</a>

Encryption issues appear when an application does not fully encrypt data in transit, allowing eavesdropping attackers to learn about the user's interactions with the application.

Insufficient encryption can arise in the following cases: not using HTTPS, [mixed content](/what-is-mixed-content/), setting cookies without the [`Secure` attribute](https://developer.mozilla.org/docs/Web/HTTP/Cookies#restrict_access_to_cookies) (or [`__Secure` prefix](https://developer.mozilla.org/docs/Web/HTTP/Cookies#Cookie_prefixes)), or [lax CORS validation logic](https://blog.detectify.com/2018/04/26/cors-misconfigurations-explained/).

-   Use [HTTP Strict Transport Security (HSTS)](#hsts) to consisitently serve your contents through HTTPS.

Content Security Policy (CSP) <a href="#csp" class="w-headline-link">#</a>
--------------------------------------------------------------------------

[Cross-Site Scripting (XSS)](https://www.google.com/about/appsecurity/learning/xss/) is an attack where a vulnerability on a website allows a malicious script to be injected and executed.

`Content-Security-Policy` provides an added layer to mitigate XSS attacks by restricting which scripts can be executed by the page.

It's recommended that you enable strict CSP using one of the following approaches:

-   If you render your HTML pages on the server, use **a nonce-based strict CSP**.
-   If your HTML has to be served statically or cached, for example if it's a single-page application, use **a hash-based strict CSP**.

Example usage: A nonce-based CSP

    Content-Security-Policy:
      script-src 'nonce-{RANDOM1}' 'strict-dynamic' https: 'unsafe-inline';
      object-src 'none';
      base-uri 'none';

How to use CSP
--------------

### Recommended usages <a href="#recommended-usages" class="w-headline-link">#</a>

A CSP can be an *extra* protection against XSS attacks; you should still make sure to escape (and sanitize) user input.

#### 1. Use a nonce-based strict CSP <a href="#nonce-based-csp" class="w-headline-link">#</a>

If you render your HTML pages on the server, use **a nonce-based strict CSP**.

**Caution**:

A nonce is a random number used only once. A nonce-based CSP is only secure if you can generate a different nonce for each response. If you can't do this, use [a hash-based CSP](#hash-based-csp) instead.

Generate a new script nonce value for every request on the server side and set the following header:

server configuration file

    Content-Security-Policy:
      script-src 'nonce-{RANDOM1}' 'strict-dynamic' https: 'unsafe-inline';
      object-src 'none';
      base-uri 'none';

In HTML, in order to load the scripts, set the `nonce` attribute of all `<script>` tags to the same `{RANDOM1}` string.

index.html

    <script nonce="{RANDOM1}" src="https://example.com/script1.js"></script>
    <script nonce="{RANDOM1}">
      // Inline scripts can be used with the `nonce` attribute.
    </script>

[Google Photos](https://photos.google.com/) is a good nonce-based strict CSP example. Use DevTools to see how it's used.

#### 2. Use a hash-based strict CSP <a href="#hash-based-csp" class="w-headline-link">#</a>

If your HTML has to be served statically or cached, for example if you're building a single-page application, use **a hash-based strict CSP**.

server configuration file

    Content-Security-Policy:
      script-src 'sha256-{HASH1}' 'sha256-{HASH2}' 'strict-dynamic' https: 'unsafe-inline';
      object-src 'none';
      base-uri 'none';

In HTML, you'll need to inline your scripts in order to apply a hash-based policy, because [most browsers don't support hashing external scripts](https://wpt.fyi/results/content-security-policy/script-src/script-src-sri_hash.sub.html?label=master&label=experimental&aligned).

index.html

    <script>
    ...// your script1, inlined
    </script>
    <script>
    ...// your script2, inlined
    </script>

To load external scripts, read "Load sourced scripts dynamically" under [Option B: Hash-based CSP Response Header](/strict-csp/#hash-based-csp) section.

[CSP Evaluator](https://csp-evaluator.withgoogle.com/) is a good tool to evaluate your CSP, but at the same time a good nonce-based strict CSP example. Use DevTools to see how it's used.

### Supported browsers <a href="#supported-browsers" class="w-headline-link">#</a>

Chrome, Firefox, Edge, Safari

**Gotchas!**

-   `https:` is a fallback for Safari and `unsafe-inline` is a fallback for very old browser versions. `https:` and `unsafe-inline` don't make your policy less safe because they will be ignored by browsers who support `strict-dynamic`. Read more in [Add fallbacks to support Safari and older browsers](/strict-csp/#step-4:-add-fallbacks-to-support-safari-and-older-browsers).
-   Safari does *not* support `strict-dynamic` yet. But a strict CSP like in the examples above is safer than an allowlist CSP (and much safer than no CSP at all) for all of your users. Even in Safari, a strict CSP protects your site from some types of XSS attacks, because the presence of the CSP disallows certain unsafe patterns.

See [more compatibilities](https://developer.mozilla.org/docs/Web/HTTP/CSP#browser_compatibility).

### Other things to note about CSP <a href="#other-things-to-note-about-csp" class="w-headline-link">#</a>

-   [`frame-ancestors`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) directive protects your site from clickjacking—a risk that arises if you allow untrusted sites to embed yours. If you prefer simpler solution, you can use [`X-Frame-Options`](#xfo) to block being loaded, but `frame-ancestors` gives you an advanced configuration to only allow specific origins as embedders.
-   You may have used [a CSP to ensure that all of your site's resources are loaded over HTTPS](/fixing-mixed-content/#content-security-policy). This has become less relevant: nowadays, most browsers block [mixed-content](/what-is-mixed-content/).
-   You can also set a CSP in [report-only mode](/strict-csp/#step-2:-set-a-strict-csp-and-prepare-your-scripts).
-   If you can't set a CSP as a header server-side, you can also set it as a meta tag. Note that you can't use **report-only** mode for meta tags (though [this may change](https://github.com/w3c/webappsec-csp/issues/277)).

### Learn more <a href="#learn-more" class="w-headline-link">#</a>

-   [Mitigate XSS with a Strict Content Security Policy (CSP)](/strict-csp)
-   [Content Security Policy Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Content_Security_Policy_Cheat_Sheet.html)

Trusted Types <a href="#tt" class="w-headline-link">#</a>
---------------------------------------------------------

[DOM-based XSS](https://portswigger.net/web-security/cross-site-scripting/dom-based) is an attack where a malicious data is passed into a sink that supports dynamic code execution such as `eval()` or `.innerHTML`.

Trusted Types provide the tools to write, security review, and maintain applications free of DOM XSS. They can be enabled via [CSP](#csp) and make JavaScript code secure by default by limiting dangerous web APIs to only accept a special object—a Trusted Type.

To create these objects you can define security policies in which you can ensure that security rules (such as escaping or sanitization) are consistently applied before the data is written to the DOM. These policies are then the only places in code that could potentially introduce DOM XSS.

Example usages

    Content-Security-Policy: require-trusted-types-for 'script'

    // Feature detection
    if (window.trustedTypes && trustedTypes.createPolicy) {
      // Name and create a policy
      const policy = trustedTypes.createPolicy('escapePolicy', {
        createHTML: str => {
          return str.replace(/\</g, '&amplt;').replace(/>/g, '&ampgt;');
        }
      });
    }

    // Assignment of raw strings is blocked by Trusted Types.
    el.innerHTML = 'some string'; // This throws an exception.

    // Assignment of Trusted Types is accepted safely.
    const escaped = policy.createHTML('<img src=x onerror=alert(1)>');
    el.innerHTML = escaped;  // '&amplt;img src=x onerror=alert(1)&ampgt;'

How to use Trusted Types
------------------------

### Recommended usages <a href="#recommended-usages-2" class="w-headline-link">#</a>

1.  Enforce Trusted Types for dangerous DOM sinks

    CSP and Trusted Types header:

        Content-Security-Policy: require-trusted-types-for 'script'

    Currently `'script'` is the only acceptable value for `require-trusted-types-for` directive.

    Of course, you can combine Trusted Types with other CSP directives:

    Merging a nonce-based CSP from above with Trusted Types:

        Content-Security-Policy:
          script-src 'nonce-{RANDOM1}' 'strict-dynamic' https: 'unsafe-inline';
          object-src 'none';
          base-uri 'none';
          require-trusted-types-for 'script';

    You may limit allowed Trusted Types policy names by setting an additional `trusted-types` directive (for example, `trusted-types myPolicy`). However, this is not a requirement.

2.  Define a policy

    Policy:

        // Feature detection
        if (window.trustedTypes && trustedTypes.createPolicy) {
          // Name and create a policy
          const policy = trustedTypes.createPolicy('escapePolicy', {
            createHTML: str => {
              return str.replace(/\</g, '&amplt;').replace(/>/g, '&ampgt;');
            }
          });
        }

    You can define policies with arbitrary names unless you limit the names of allowed Trusted Types policies by setting the `trusted-types` directive.

3.  Apply the policy

    Use the policy when writing data to the DOM:

        // Assignment of raw strings are blocked by Trusted Types.
        el.innerHTML = 'some string'; // This throws an exception.

        // Assignment of Trusted Types is accepted safely.
        const escaped = policy.createHTML('<img src=x onerror=alert(1)>');
        el.innerHTML = escaped;  // '&amplt;img src=x onerror=alert(1)&ampgt;'

    With `require-trusted-types-for 'script'`, using a trusted type is a requirement. Using any dangerous DOM API with a string will result in an error.

### Supported browsers <a href="#supported-browsers-2" class="w-headline-link">#</a>

Chrome, Edge

See [more compatibilities](https://caniuse.com/?search=trusted%20types).

### Learn more <a href="#learn-more-2" class="w-headline-link">#</a>

-   [Prevent DOM-based cross-site scripting vulnerabilities with Trusted Types](/trusted-types/)
-   [CSP: require-trusted-types-for - HTTP | MDN](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/require-trusted-types-for)
-   [CSP: trusted-types - HTTP | MDN](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/trusted-types)
-   [Trusted Types demo](https://www.compass-demo.com/trusted-types/)—open DevTools Inspector and see what is happening

X-Content-Type-Options <a href="#xcto" class="w-headline-link">#</a>
--------------------------------------------------------------------

When a malicious HTML document is served from your domain (for example, if an image uploaded to a photo service contains valid HTML markup), some browsers will treat it as an active document and allow it to execute scripts in the context of the application, leading to a [cross-site scripting bug](https://www.google.com/about/appsecurity/learning/xss/).

`X-Content-Type-Options: nosniff` prevents it by instructing the browser that the [MIME type](https://mimesniff.spec.whatwg.org/#introduction) set in the `Content-Type` header for a given response is correct. This header is recommended for **all of your resources**.

Example usage

    X-Content-Type-Options: nosniff

How to use X-Content-Type-Options
---------------------------------

### Recommended usages <a href="#recommended-usages-3" class="w-headline-link">#</a>

`X-Content-Type-Options: nosniff` is recommended for all resources served from your server along with the correct `Content-Type` header.

<img src="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format" alt="X-Content-Type-Options: nosniff" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/IWqRWe9R1mOJImmMbLoM.png?auto=format&amp;w=1600 1600w" width="800" height="237" />

Example headers sent with a document HTML

    X-Content-Type-Options: nosniff
    Content-Type: text/html; charset=utf-8

### Supported browsers <a href="#supported-browsers-3" class="w-headline-link">#</a>

Chrome, Firefox, Safari, Edge

See [more compatibilities](https://caniuse.com/mdn-http_headers_x-content-type-options).

### Learn more <a href="#learn-more-3" class="w-headline-link">#</a>

-   [X-Content-Type-Options - HTTP MDN](https://developer.mozilla.org/docs/Web/HTTP/Headers/X-Content-Type-Options)

X-Frame-Options <a href="#xfo" class="w-headline-link">#</a>
------------------------------------------------------------

If a malicious website can embed your site as an iframe, this may allow attackers to invoke unintended actions by the user with [clickjacking](https://portswigger.net/web-security/clickjacking). Also, in some cases [Spectre-type attacks](https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)) give malicious websites a chance to learn about the contents of an embedded document.

`X-Frame-Options` indicates whether or not a browser should be allowed to render a page in a `<frame>`, `<iframe>`, `<embed>`, or `<object>`. **All documents** are recommended to send this header to indicate whether they allow being embedded by other documents.

If you need more granular control such as allowing only a specific origin to embed the document, use the [CSP](#csp) [`frame-ancestors`](https://developer.mozilla.org/docs/Web/HTTP/Headers/Content-Security-Policy/frame-ancestors) directive.

Example usage

    X-Frame-Options: DENY

How to use X-Frame-Options
--------------------------

### Recommended usages <a href="#recommended-usages-4" class="w-headline-link">#</a>

All documents that are not designed to be embedded should use `X-Frame-Options` header.

You can try how the following configurations affect loading an iframe on [this demo](https://first-party-test.glitch.me/). Change the `X-Frame-Options` dropdown menu and click the **Reload the iframe** button.

#### Protects your website from being embedded by any other websites <a href="#protects-your-website-from-being-embedded-by-any-other-websites" class="w-headline-link">#</a>

Deny being embedded by any other documents.

<img src="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format" alt="X-Frame-Options: DENY" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2ZM5obgGK38CMcZ75PkH.png?auto=format&amp;w=1600 1600w" width="800" height="237" />

    X-Frame-Options: DENY

#### Protects your website from being embedded by any cross-origin websites <a href="#protects-your-website-from-being-embedded-by-any-cross-origin-websites" class="w-headline-link">#</a>

Allow being embedded only by same-origin documents.

    X-Frame-Options: SAMEORIGIN

**Gotchas!**

Documents being embeddable by default means the web developers need to explicitly send `DENY` or `SAMEORIGIN` to stop being embedded and protect themselves from side-channel attacks. The Chrome team is considering switching to block document embeds by default so that websites will be secure even if they don't explicitly set the header. In that new world, documents would need to explicitly opt-in to be embedded.

### Supported browsers <a href="#supported-browsers-4" class="w-headline-link">#</a>

Chrome, Firefox, Safari, Edge

See [more compatibilities](https://developer.mozilla.org/docs/Web/HTTP/Headers/X-Frame-Options#browser_compatibility).

### Learn more <a href="#learn-more-4" class="w-headline-link">#</a>

-   [X-Frame-Options - HTTP](https://developer.mozilla.org/docs/Web/HTTP/Headers/X-Frame-Options)

Cross-Origin Resource Policy (CORP) <a href="#corp" class="w-headline-link">#</a>
---------------------------------------------------------------------------------

An attacker can embed resources from another origin, for example from your site, to learn information about them by exploiting web-based [cross-site leaks](https://xsleaks.dev/).

`Cross-Origin-Resource-Policy` mitigates this risk by indicating the set of websites it can be loaded by. The header takes one of three values: `same-origin`, `same-site`, and `cross-origin`. **All resources** are recommended to send this header to indicate whether they allow being loaded by other websites.

Example usage

    Cross-Origin-Resource-Policy: same-origin

How to use CORP
---------------

### Recommended usages <a href="#recommended-usages-5" class="w-headline-link">#</a>

It is recommended that **all** resources are served with one of the following three headers.

You can try how the following configurations affect loading resources under a [`Cross-Origin-Embedder-Policy: require-corp` environment](#coep) on [this demo](https://first-party-test.glitch.me/?coep=require-corp&). Change the **Cross-Origin-Resource-Policy** dropdown menu and click the **Reload the iframe** or **Reload the image** button to see the effect.

#### Allow resources to be loaded `cross-origin` <a href="#allow-resources-to-be-loaded-cross-origin" class="w-headline-link">#</a>

It's recommended that CDN-like services apply `cross-origin` to resources (since they are usually loaded by cross-origin pages), unless they are already served through [CORS](#cors) which has a similar effect.

<img src="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format" alt="Cross-Origin-Resource-Policy: cross-origin" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/qP2mspVMC6RazxDjWUrL.png?auto=format&amp;w=1600 1600w" width="800" height="234" />

    Cross-Origin-Resource-Policy: cross-origin

#### Limit resources to be loaded from the `same-origin` <a href="#limit-resources-to-be-loaded-from-the-same-origin" class="w-headline-link">#</a>

`same-origin` should be applied to resources that are intended to be loaded only by same-origin pages. You should apply this to resources that include sensitive information about the user, or responses of an API that is intended to be called only from the same origin.

Keep in mind that resources with this header can still be loaded directly, for example by navigating to the URL in a new browser window. Cross-Origin Resource Policy only protects the resource from being embedded by other websites.

<img src="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format" alt="Cross-Origin-Resource-Policy: same-origin" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/7UzYMWsbKkh89m5ZImvj.png?auto=format&amp;w=1600 1600w" width="800" height="238" />

    Cross-Origin-Resource-Policy: same-origin

#### Limit resources to be loaded from the `same-site` <a href="#limit-resources-to-be-loaded-from-the-same-site" class="w-headline-link">#</a>

`same-site` is recommended to be applied to resources that are similar to above but are intended to be loaded by other subdomains of your site.

<img src="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format" alt="Cross-Origin-Resource-Policy: same-site" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/R9yNRGSJ4xABc560WRJI.png?auto=format&amp;w=1600 1600w" width="800" height="233" />

    Cross-Origin-Resource-Policy: same-site

To learn more about the difference between same-origin and same-site, check out [Understanding "same-site" and "same-origin"](/same-site-same-origin/).

### Supported browsers <a href="#supported-browsers-5" class="w-headline-link">#</a>

Chrome, Firefox, Safari, Edge

See [more compatibilities](https://caniuse.com/mdn-http_headers_cross-origin-resource-policy).

### Learn more <a href="#learn-more-5" class="w-headline-link">#</a>

-   [Consider deploying cross-origin resource policy](https://resourcepolicy.fyi/)
-   [Making your website "cross-origin isolated" using COOP and COEP](/coop-coep/)
-   [Why you need "cross-origin isolated" for powerful features](/why-coop-coep/)

Cross-Origin Opener Policy (COOP) <a href="#coop" class="w-headline-link">#</a>
-------------------------------------------------------------------------------

An attacker's website can open another site in a popup window to learn information about it by exploiting web-based [cross-site leaks](https://xsleaks.dev/). In some cases, this may also allow the exploitation of side-channel attacks based on [Spectre](https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)).

The `Cross-Origin-Opener-Policy` header provides a way for a document to isolate itself from cross-origin windows opened through `window.open()` or a link with `target="_blank"` without `rel="noopener"`. As a result, any cross-origin opener of the document will have no reference to it and will not be able to interact with it.

Example usage

    Cross-Origin-Opener-Policy: same-origin-allow-popups

How to use COOP
---------------

### Recommended usages <a href="#recommended-usages-6" class="w-headline-link">#</a>

You can try how the following configurations affect communication with a cross-origin popup window on [this demo](https://first-party-test.glitch.me/). Change the **Cross-Origin-Opener-Policy** dropdown menu for both the document and the popup window, click the **Open a popup** button then click **Send a postMessage** to see if the message is actually delivered.

#### Isolate a document from cross-origin windows <a href="#isolate-a-document-from-cross-origin-windows" class="w-headline-link">#</a>

Setting `same-origin` puts the document to be isolated from cross-origin document windows.

<img src="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format" alt="Cross-Origin-Opener-Policy: same-origin" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/mSDG9auD7r5asxGJvJjg.png?auto=format&amp;w=1600 1600w" width="800" height="235" />

    Cross-Origin-Opener-Policy: same-origin

#### Isolate a document from cross-origin windows but allow popups <a href="#isolate-a-document-from-cross-origin-windows-but-allow-popups" class="w-headline-link">#</a>

Setting `same-origin-allow-popups` allows a document to retain a reference to its popup windows unless they set COOP with `same-origin` or `same-origin-allow-popups`. This means `same-origin-allow-popups` can still protect the document from being referenced when opened as a popup window, but allow it to communicate with its own popups.

<img src="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format" alt="Cross-Origin-Opener-Policy: same-origin-allow-popups" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/2uJZ0s2VnjxJUcBI2Ol9.png?auto=format&amp;w=1600 1600w" width="800" height="233" />

    Cross-Origin-Opener-Policy: same-origin-allow-popups

#### Allow a document to be referenced by cross-origin windows <a href="#allow-a-document-to-be-referenced-by-cross-origin-windows" class="w-headline-link">#</a>

`unsafe-none` is the default value but you can explicitly indicate that this document can be opened by a cross-origin window and retain mutual access.

<img src="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format" alt="Cross-Origin-Opener-Policy: unsafe-none" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/YLflGBAPWecgtKJLqCJHSzHqe2J2/oSco89ZT3RP7gZzNKDjY.png?auto=format&amp;w=1600 1600w" width="800" height="233" />

**Gotchas!**

`unsafe-none` being the default means the web developers need to send `same-origin` or `same-origin-allow-popups` explicitly to protect their website from side-channel attacks.

    Cross-Origin-Opener-Policy: unsafe-none

Features such as `SharedArrayBuffer` or `performance.measureUserAgentSpecificMemory()` are disabled by default. Some browsers allow you to use them in "cross-origin isolated" contexts, which require you to set [COOP](#coop) and [COEP](#coep) headers.

To learn more, read [Making your website "cross-origin isolated" using COOP and COEP](/coop-coep/).

#### Report patterns incompatible with COOP <a href="#report-patterns-incompatible-with-coop" class="w-headline-link">#</a>

You can receive reports when COOP prevents cross-window interactions with the Reporting API.

    Cross-Origin-Opener-Policy: same-origin; report-to="coop"

COOP also supports a report-only mode so you can receive reports without actually blocking communication between cross-origin documents.

    Cross-Origin-Opener-Policy-Report-Only: same-origin; report-to="coop"

### Supported browsers <a href="#supported-browsers-6" class="w-headline-link">#</a>

Chrome, Firefox, Edge

See [more compatibilities](https://caniuse.com/mdn-http_headers_cross-origin-opener-policy).

### Learn more <a href="#learn-more-6" class="w-headline-link">#</a>

-   [Why you need "cross-origin isolated" for powerful features](/why-coop-coep/)

Cross-Origin Resource Sharing (CORS) <a href="#cors" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

Unlike other items in this article, Cross-Origin Resource Sharing (CORS) is not a header, but a browser mechanism that requests and permits access to cross-origin resources.

By default, browsers enforce [the same-origin policy](/same-origin-policy/) to prevent a web page from accessing cross-origin resources. For example, when a cross-origin image is loaded, even though it's displayed on the web page visually, the JavaScript on the page doesn't have access to the image's data. The resource provider can relax restrictions and allow other websites to read the resource by opting-in with CORS.

Example usage

    Access-Control-Allow-Origin: https://example.com
    Access-Control-Allow-Credentials: true

How to use CORS
---------------

Before looking into how to configure CORS, it's helpful to understand the distinction between request types. Depending on request details, a request will be classified as a **simple request** or a **preflighted request**.

Criteria for a simple request:

-   The method is `GET`, `HEAD`, or `POST`.
-   The custom headers only include `Accept`, `Accept-Language`, `Content-Language`, and `Content-Type`.
-   The `Content-Type` is `application/x-www-form-urlencoded`, `multipart/form-data`, or `text/plain`.

Everything else is classified as a preflighted request. For more details, check out [Cross-Origin Resource Sharing (CORS) - HTTP | MDN](https://developer.mozilla.org/docs/Web/HTTP/CORS#simple_requests).

### Recommended usages <a href="#recommended-usages-7" class="w-headline-link">#</a>

#### Simple request <a href="#simple-request" class="w-headline-link">#</a>

When a request meets the simple request criteria, the browser sends a cross-origin request with an `Origin` header that indicates the requesting origin.

Example request header

    Get / HTTP/1.1
    Origin: https://example.com

Example response header

    Access-Control-Allow-Origin: https://example.com
    Access-Control-Allow-Credentials: true

-   `Access-Control-Allow-Origin: https://example.com` indicates that the `https://example.com` can access the contents of the response. Resources meant to be readable by any site can set this header to `*`, in which case the browser will only require the request to be made [without credentials](https://developer.mozilla.org/en-US/docs/Web/API/Request/credentials#value).
-   `Access-Control-Allow-Credentials: true` indicates that requests which carry credentials (cookies) are allowed to load the resource. Otherwise, authenticated requests will be rejected even if the requesting origin is present in the `Access-Control-Allow-Origin` header.

You can try how the simple request affect loading resources under a [`Cross-Origin-Embedder-Policy: require-corp` environment](#coep) on [this demo](https://first-party-test.glitch.me/?coep=require-corp&). Click the **Cross-Origin Resource Sharing** checkbox and click the **Reload the image** button to see the effect.

#### Preflighted requests <a href="#preflighted-requests" class="w-headline-link">#</a>

A preflighted request is preceded with an `OPTIONS` request to check if the subsequent request is allowed to be sent.

Example request header

    OPTIONS / HTTP/1.1
    Origin: https://example.com
    Access-Control-Request-Method: POST
    Access-Control-Request-Headers: X-PINGOTHER, Content-Type

-   `Access-Control-Request-Method: POST` allows the following request to be made with the `POST` method.
-   `Access-Control-Request-Headers: X-PINGOTHER, Content-Type` allows the requester to set the `X-PINGOTHER` and `Content-Type` HTTP headers in the subsequent request.

Example response headers

    Access-Control-Allow-Origin: https://example.com
    Access-Control-Allow-Credentials: true
    Access-Control-Allow-Methods: POST, GET, OPTIONS
    Access-Control-Allow-Headers: X-PINGOTHER, Content-Type
    Access-Control-Max-Age: 86400

-   `Access-Control-Allow-Methods: POST, GET, OPTIONS` indicates that subsequent requests can be made with the `POST`, `GET` and `OPTIONS` methods.
-   `Access-Control-Allow-Headers: X-PINGOTHER, Content-Type` indicates subsequent requests can include the `X-PINGOTHER` and `Content-Type` headers.
-   `Access-Control-Max-Age: 86400` indicates that the result of the preflighted request can be cached for 86400 seconds.

### Supported browsers <a href="#supported-browsers-7" class="w-headline-link">#</a>

Chrome, Firefox, Safari, Edge

See [more compatibilities](https://caniuse.com/mdn-http_headers_content-length_cors_response_safelist).

### Learn more <a href="#learn-more-7" class="w-headline-link">#</a>

-   [Cross-Origin Resource Sharing (CORS)](/cross-origin-resource-sharing/)
-   [Cross-Origin Resource Sharing (CORS) - HTTP | MDN](https://developer.mozilla.org/docs/Web/HTTP/CORS)

Cross-Origin Embedder Policy (COEP) <a href="#coep" class="w-headline-link">#</a>
---------------------------------------------------------------------------------

To reduce the ability of [Spectre-based attacks](https://en.wikipedia.org/wiki/Spectre_(security_vulnerability)) to steal cross-origin resources, features such as `SharedArrayBuffer` or `performance.measureUserAgentSpecificMemory()` are disabled by default.

`Cross-Origin-Embedder-Policy: require-corp` prevents documents and workers from loading cross-origin resources such as images, scripts, stylesheets, iframes and others unless these resources explicitly opt into being loaded via [CORS](#cors) or [CORP](#corp) headers. COEP can be combined with`Cross-Origin-Opener-Policy` to opt a document into [cross-origin isolation](/cross-origin-isolation-guide/).

Use `Cross-Origin-Embedder-Policy: require-corp` when you want to enable [cross-origin isolation](/coop-coep/) for your document.

Example usage

    Cross-Origin-Embedder-Policy: require-corp

How to use COEP
---------------

### Example usages <a href="#example-usages" class="w-headline-link">#</a>

COEP takes a single value of `require-corp`. By sending this header, you can instruct the browser to block loading resources that do not opt-in via [CORS](#cors) or [CORP](#corp).

<img src="https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format" alt="How COEP works" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/MAhaVZdShm8tRntWieU4.png?auto=format&amp;w=1600 1600w" width="800" height="410" />

You can try how the following configurations affect loading resources on [this demo](https://first-party-test.glitch.me/). Change the **Cross-Origin-Embedder-Policy** dropdown menu, the **Cross-Origin-Resource-Policy** dropdown menu, the **Report Only** checkbox etc to see how they affect loading resources. Also, open [the reporting endpoint demo](https://reporting-endpoint.glitch.me/) to see if the blocked resources are reported.

#### Enable cross-origin isolation <a href="#enable-cross-origin-isolation" class="w-headline-link">#</a>

Enable [cross-origin isolation](/coop-coep) by sending `Cross-Origin-Embedder-Policy: require-corp` along with `Cross-Origin-Opener-Policy: same-origin`.

    Cross-Origin-Embedder-Policy: require-corp
    Cross-Origin-Opener-Policy: same-origin

#### Report resources incompatible withn COEP <a href="#report-resources-incompatible-withn-coep" class="w-headline-link">#</a>

You can receive reports of blocked resources caused by COEP with the Reporting API.

    Cross-Origin-Embedder-Policy: require-corp; report-to="coep"

COEP also supports report-only mode so you can receive reports without actually blocking loading resources.

    Cross-Origin-Embedder-Policy-Report-Only: require-corp; report-to="coep"

### Supported browsers <a href="#supported-browsers-8" class="w-headline-link">#</a>

Chrome, Firefox, Edge

See [more compatibilities](https://caniuse.com/mdn-http_headers_cross-origin-embedder-policy).

### Learn more <a href="#learn-more-8" class="w-headline-link">#</a>

-   [Making your website "cross-origin isolated" using COOP and COEP](/coop-coep/)
-   [Why you need "cross-origin isolated" for powerful features](/why-coop-coep/)
-   [A guide to enable cross-origin isolation](/cross-origin-isolation-guide/)

HTTP Strict Transport Security (HSTS) <a href="#hsts" class="w-headline-link">#</a>
-----------------------------------------------------------------------------------

Communication over a plain HTTP connection is not encrypted, making the transferred data accessible to network-level eavesdroppers.

`Strict-Transport-Security` header informs the browser that it should never load the site using HTTP and use HTTPS instead. Once it's set, the browser will use HTTPS instead of HTTP to access the domain without a redirect for a duration defined in the header.

Example usage

    Strict-Transport-Security: max-age=31536000

How to use HSTS
---------------

### Recommended usages <a href="#recommended-usages-8" class="w-headline-link">#</a>

All websites that transition from HTTP to HTTPS should respond with a `Strict-Transport-Security` header when a request with HTTP is received.

    Strict-Transport-Security: max-age=31536000

### Supported browsers <a href="#supported-browsers-9" class="w-headline-link">#</a>

Chrome, Firefox, Safari, Edge

See [more compatibilities](https://caniuse.com/stricttransportsecurity).

### Learn more <a href="#learn-more-9" class="w-headline-link">#</a>

-   [Strict-Transport-Security - HTTP](https://developer.mozilla.org/docs/Web/HTTP/Headers/Strict-Transport-Security)

Further reading <a href="#further-reading" class="w-headline-link">#</a>
------------------------------------------------------------------------

-   [Post-Spectre Web Development](https://www.w3.org/TR/post-spectre-webdev/)

<a href="/tags/security/" class="w-chip">Security</a>

<span class="w-mr--sm">Last updated: Aug 5, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/secure/security-headers/index.md)

<a href="/blog" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
