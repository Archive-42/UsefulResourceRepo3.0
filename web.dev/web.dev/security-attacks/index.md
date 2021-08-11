<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#what-are-security-attacks" class="w-toc__header--link">What are security attacks?</a>
-----------------------------------------------------------------------------------------------

-   [Active attacks vs passive attacks](#active-attacks-vs-passive-attacks)
-   [Active attacks](#active-attacks)
-   [Passive attack](#passive-attack)
-   [Defense against attacks](#defense-against-attacks)
-   [Wrap up](#wrap-up)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

What are security attacks?
==========================

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/secure" class="w-post-signpost__link">Safe and secure</a>

[<img src="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Mariko Kosaka" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/kosamari/)

<a href="/authors/kosamari/" class="w-author__name-link">Mariko Kosaka</a>

-   <a href="https://twitter.com/kosamari" class="w-author__link">Twitter</a>
-   <a href="https://github.com/kosamari" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@kosamari" class="w-author__link">Glitch</a>
-   <a href="https://kosamari.com/" class="w-author__link">Blog</a>

An insecure application could expose users and systems to various types of damage. When a malicious party uses vulnerabilities or lack of security features to their advantage to cause damage, it is called an **attack**. We'll take a look at different types of attacks in this guide so you know what to look for when securing your application.

Active attacks vs passive attacks <a href="#active-attacks-vs-passive-attacks" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

Attacks can be divided into two different types: active and passive.

### Active attacks <a href="#active-attacks" class="w-headline-link">#</a>

With an **active attack,** the attacker tries to break into the application directly. There are a variety of ways this could be done, from using a false identity to access sensitive data (masquerade attack) to flooding your server with massive amounts of traffic to make your application unresponsive (denial of service attack).

Active attacks can also be done to data in transit. An attacker could modify your application data before it gets to a user's browser, showing modified information on the site or direct the user to an unintended destination. This is sometimes called **modification of messages**.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format" alt="A web site being tampered by attacker to guide user to a phishing site." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/qrf4KBAceYxf2E5A8f6J.png?auto=format&amp;w=1600 1600w" width="800" height="475" /><figcaption>A web site being tampered by attacker to guide user to a phishing site.</figcaption></figure>Have you ever logged into free public wifi and seen ads wrapped around web pages you are accessing? That's exactly what **modification of message** is! The wifi access point injected their advertising into a website before it got to your browser. In many cases, you might dismiss it as "just ads for free wifi", but imagine if the same technique is used to replace some of the javascript or link to a phishing site. Your site may be used by an attacker to misguide users without you noticing.

### Passive attack <a href="#passive-attack" class="w-headline-link">#</a>

With a **passive attack**, the attacker tries to collect or learn information from the application but does not affect the application itself.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format" alt="Attacker eavesdropping communication between a user and a server." sizes="(min-width: 547px) 547px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/QtAWlZRXJULRaQLQ7bKQ.png?auto=format&amp;w=1094 1094w" width="547" height="344" /><figcaption>Attacker eavesdropping communication between a user and a server.</figcaption></figure>Imagine someone is eavesdropping on your conversation with friends and family, collecting information about your personal life, who your friends are, and where you hang out. The same thing could be done on your web traffic. An attacker could capture data between the browser and the server collecting usernames & passwords, users' browsing history, and data exchanged.

Defense against attacks <a href="#defense-against-attacks" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

Attackers can directly harm your application or perform a malicious operation on your site without you or your users noticing it. You need mechanisms to detect and protect against attacks.

Unfortunately, there is no single solution to make your application 100% secure. In practice, many security features and techniques are used in layers to prevent or further delay the attack (this is called **defense in depth**). If your application contains a form, you might check inputs in the browser, then on the server, and finally at the database; you would also use HTTPS to secure the data in transit.

Wrap up <a href="#wrap-up" class="w-headline-link">#</a>
--------------------------------------------------------

Since many attacks can happen without ever hitting your server, it is sometimes hard to detect if attacks are happening or not. The good news is that web browsers have powerful security features already built in. Follow the next topic "How browser mitigates against attacks" to learn more.

<a href="/tags/security/" class="w-chip">Security</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/secure/security-attacks/index.md)

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
