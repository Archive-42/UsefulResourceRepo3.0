<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#why-https-matters" class="w-toc__header--link">Why HTTPS matters</a>
------------------------------------------------------------------------------

-   [Summary](#summary)
-   [HTTPS protects the integrity of your website](#integrity)
-   [HTTPS protects the privacy and security of your users](#privacy)
-   [HTTPS is the future of the web](#capabilities)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Why HTTPS matters
=================

Nov 23, 2015 <span class="w-author__separator">•</span> Updated Apr 7, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/secure" class="w-post-signpost__link">Safe and secure</a>

[<img src="https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Kayce Basques" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/7GdPR4YDRHSS6llepBOd.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/kaycebasques/)

<a href="/authors/kaycebasques/" class="w-author__name-link">Kayce Basques</a>

-   <a href="https://twitter.com/kaycebasques" class="w-author__link">Twitter</a>
-   <a href="https://github.com/kaycebasques" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@kaycebasques" class="w-author__link">Glitch</a>
-   <a href="https://kayce.basqu.es/" class="w-author__link">Blog</a>

You should always protect all of your websites with HTTPS, even if they don't handle sensitive communications. Aside from providing critical security and data integrity for both your websites and your users' personal information, HTTPS is a requirement for many new browser features, particularly those required for [progressive web apps](/progressive-web-apps).

Summary <a href="#summary" class="w-headline-link">#</a>
--------------------------------------------------------

-   Intruders both malignant and benign exploit every unprotected resource between your websites and users.
-   Many intruders look at aggregate behaviors to identify your users.
-   HTTPS doesn't just block misuse of your website. It's also a requirement for many cutting-edge features and an enabling technology for app-like capabilities such as service workers.

HTTPS protects the integrity of your website <a href="#integrity" class="w-headline-link">#</a>
-----------------------------------------------------------------------------------------------

HTTPS helps prevent intruders from tampering with the communications between your websites and your users' browsers. Intruders include intentionally malicious attackers, and legitimate but intrusive companies, such as ISPs or hotels that inject ads into pages.

Intruders exploit unprotected communications to trick your users into giving up sensitive information or installing malware, or to insert their own advertisements into your resources. For example, some third parties inject advertisements into websites that potentially break user experiences and create security vulnerabilities.

Intruders exploit every unprotected resource that travels between your websites and your users. Images, cookies, scripts, HTML… they're all exploitable. Intrusions can occur at any point in the network, including a user's machine, a Wi-Fi hotspot, or a compromised ISP, just to name a few.

HTTPS protects the privacy and security of your users <a href="#privacy" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------

HTTPS prevents intruders from being able to passively listen to communications between your websites and your users.

One common misconception about HTTPS is that the only websites that need HTTPS are those that handle sensitive communications. Every unprotected HTTP request can potentially reveal information about the behaviors and identities of your users. Although a single visit to one of your unprotected websites may seem benign, some intruders look at the aggregate browsing activities of your users to make inferences about their behaviors and intentions, and to [de-anonymize](https://en.wikipedia.org/wiki/De-anonymization) their identities. For example, employees might inadvertently disclose sensitive health conditions to their employers just by reading unprotected medical articles.

HTTPS is the future of the web <a href="#capabilities" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

Powerful, new web platform features, such as taking pictures or recording audio with `getUserMedia()`, enabling offline app experiences with [service workers](/service-workers-cache-storage/), or building [progressive web apps](/progressive-web-apps), require explicit permission from the user before executing. Many older APIs are also being updated to require permission to execute, such as the [Geolocation API](https://developer.mozilla.org/docs/Web/API/Geolocation/Using_geolocation). HTTPS is a key component to the permission workflows for both these new features and updated APIs.

<a href="/tags/security/" class="w-chip">Security</a>

<span class="w-mr--sm">Last updated: Apr 7, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/secure/why-https-matters/index.md)

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
