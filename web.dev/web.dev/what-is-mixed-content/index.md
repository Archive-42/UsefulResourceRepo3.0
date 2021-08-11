## <a href="#what-is-mixed-content" class="w-toc__header--link">What is mixed content?</a>

- [The two types of mixed content](#the-two-types-of-mixed-content)
- [Passive mixed content](#passive-mixed-content)
- [Active mixed content](#active-mixed-content)
- [The mixed content specification](#the-mixed-content-specification)
- [Older browsers](#older-browsers)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# What is mixed content?

Sep 7, 2019 <span class="w-author__separator">•</span> Updated Sep 24, 2020

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

**Mixed content** occurs when initial HTML is loaded over a secure [HTTPS](/why-https-matters/) connection, but other resources (such as images, videos, stylesheets, scripts) are loaded over an insecure HTTP connection. This is called mixed content because both HTTP and HTTPS content are being loaded to display the same page, and the initial request was secure over HTTPS.

Requesting subresources using the insecure HTTP protocol weakens the security of the entire page, as these requests are vulnerable to [**on-path attacks**](https://www.ietf.org/rfc/rfc7835.html#section-2.1.1), where an attacker eavesdrops on a network connection and views or modifies the communication between two parties. Using these resources, attackers can track users and replace content on a website, and in the case of active mixed content, take complete control over the page, not just the insecure resources.

Although many browsers report mixed content warnings to the user, by the time this happens, it is too late: the insecure requests have already been performed and the security of the page is compromised.

This is why browsers are increasingly blocking mixed content. If you have mixed content on your site, then fixing it will ensure the content continues to load as browsers become more strict.

## The two types of mixed content <a href="#the-two-types-of-mixed-content" class="w-headline-link">#</a>

The two types of mixed content are: active and passive.

**Passive mixed content** refers to content that doesn't interact with the rest of the page, and thus a man-in-the-middle attack is restricted to what they can do if they intercept or change that content. Passive mixed content is defined as images, video, and audio content.

**Active mixed content** interacts with the page as a whole and allows an attacker to do almost anything with the page. Active mixed content includes scripts, stylesheets, iframes, and other code that the browser can download and execute.

### Passive mixed content <a href="#passive-mixed-content" class="w-headline-link">#</a>

Passive mixed content is seen as less problematic yet still poses a security threat to your site and your users. For example, an attacker can intercept HTTP requests for images on your site and swap or replace these images; the attacker can swap the _save_ and _delete_ button images, causing your users to delete content without intending to; replace your product diagrams with lewd or pornographic content, defacing your site; or replace your product pictures with ads for a different site or product.

Even if the attacker doesn't alter the content of your site, an attacker can track users via mixed content requests. The attacker can tell which pages a user visits and which products they view based on images or other resources that the browser loads.

If passive mixed content is present most browsers will indicate in the URL bar that the page is not secure, even when the page itself was loaded over HTTPS. You can observe this behavior with this [demo](https://passive-mixed-content.glitch.me/) that contains examples of passive mixed content.

Until recently passive mixed content was loaded in all browsers, as to block it would have broken many websites. This is now beginning to change and so it is vital to update any instances of mixed content on your site.

[Chrome is currently rolling out](https://blog.chromium.org/2019/10/no-more-mixed-messages-about-https.html) automatic upgrading of passive mixed content where possible. Automatic upgrading means that if the asset is available over HTTPS, but has been hardcoded as HTTP, the browser will load the HTTPS version. If no secure version can be found the asset will not load.

Whenever it detects mixed content or auto-upgrades passive mixed content, Chrome logs detailed messages to the **Issues** tab in DevTools to guide you on how to fix the specific issue.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/HNxoomaHi2ksvYHGuNiE.jpg?auto=format&amp;w=1600 1600w" width="800" height="310" /></figure>### Active mixed content <a href="#active-mixed-content" class="w-headline-link">#</a>

Active mixed content poses a greater threat than passive mixed content. An attacker can intercept and rewrite active content, thereby taking full control of your page or even your entire website. This allows the attacker to change anything about the page, including displaying entirely different content, stealing user passwords or other login credentials, stealing user session cookies, or redirecting the user to a different site entirely.

Due to the severity of this threat, most browsers already block this type of content by default to protect users, but functionality varies between browser vendors and versions.

This other [demo](https://active-mixed-content.glitch.me/) contains examples of active mixed content. [Load the example over HTTP](http://active-mixed-content.glitch.me/) to see the content that's blocked when you [load the example over HTTPS](https://active-mixed-content.glitch.me/). Blocked content will also be detailed in the **Issues** tab.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xRG5zpKLr0Z3OwfYpn2H.jpg?auto=format&amp;w=1600 1600w" width="800" height="361" /></figure>Browsers also highlight blocked content in their DevTools. Blocked content issues are detailed in the **Issues** tab in Chromium-based browsers. Firefox and Safari log messages in the console.

## The mixed content specification <a href="#the-mixed-content-specification" class="w-headline-link">#</a>

Browsers follow the [mixed content specification](https://w3c.github.io/webappsec-mixed-content/), which defines the [**optionally blockable content**](https://w3c.github.io/webappsec-mixed-content/#optionally-blockable-mixed-content) and [**blockable content**](https://w3c.github.io/webappsec-mixed-content/#category-blockable) categories.

From the spec, a resource qualifies as optionally blockable content "when the risk of allowing its usage as mixed content is outweighed by the risk of breaking significant portions of the web"; this is a subset of the passive mixed content category described above.

All content that is not **optionally blockable** is considered **blockable**, and should be blocked by the browser.

There is a [Level 2 of the Mixed Content specification](https://w3c.github.io/webappsec-mixed-content/level2.html) in progress, which will add automatic upgrading to the spec.

In recent years, [HTTPS usage has risen dramatically](https://transparencyreport.google.com/https/overview), and has become the clear default on the web. This makes it more feasible now for browsers to consider blocking all mixed content, even those subresource types defined in the [mixed content specification](https://w3c.github.io/webappsec/specs/mixedcontent/) as **optionally blockable**. This is why we now see Chrome taking a stricter approach to these subresources.

### Older browsers <a href="#older-browsers" class="w-headline-link">#</a>

It is important to remember that not every visitor to your website uses the most up-to-date browsers. Different versions from different browser vendors each treat mixed content differently. At worst, older browsers and versions don't block any mixed content at all, which is very unsafe for the user.

By fixing your mixed content problems you ensure that your content is visible in new browsers. You also help protect users from dangerous content that isn't blocked by older browsers.

<a href="/tags/security/" class="w-chip">Security</a> <a href="/tags/network/" class="w-chip">Network</a> <a href="/tags/privacy/" class="w-chip">Privacy</a> <a href="/tags/html/" class="w-chip">HTML</a> <a href="/tags/css/" class="w-chip">CSS</a> <a href="/tags/javascript/" class="w-chip">JavaScript</a> <a href="/tags/images/" class="w-chip">Images</a> <a href="/tags/media/" class="w-chip">Media</a>

<span class="w-mr--sm">Last updated: Sep 24, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/secure/what-is-mixed-content/index.md)

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
