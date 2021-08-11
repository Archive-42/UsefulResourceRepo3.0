## <a href="#security-should-not-be-so-scary!" class="w-toc__header--link">Security should not be so scary!</a>

- [What is a security vulnerability?](#what-is-a-security-vulnerability)
- [What are security features?](#what-are-security-features)
- [What's the impact?](#what's-the-impact)
- [Wrap up](#wrap-up)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Security should not be so scary!

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/secure" class="w-post-signpost__link">Safe and secure</a>

[<img src="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Mariko Kosaka" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/TaVHIb4KixCUF6XheH7z.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/kosamari/)

<a href="/authors/kosamari/" class="w-author__name-link">Mariko Kosaka</a>

- <a href="https://twitter.com/kosamari" class="w-author__link">Twitter</a>
- <a href="https://github.com/kosamari" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@kosamari" class="w-author__link">Glitch</a>
- <a href="https://kosamari.com/" class="w-author__link">Blog</a>

What do you imagine when someone says "security"?

Hackers? Attacks? Defenses? A programmer in a black hoodie in a dark room?

When the word "security" comes to mind, it's usually in the context of bad news. You often encounter headlines like "A big social network leaked login passwords" or "an attacker stole credit card information from a shopping site".

But security is something to be taken as a positive and necessary part of web development just like "user experience" or "accessibility".

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format" alt="A hacker in hoodie is a negative security image. A team working on a project together is a positive security image." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/M5QZ4By9jyroim97MO0m.png?auto=format&amp;w=1600 1600w" width="800" height="359" /><figcaption>A hacker in hoodie is a negative security image. A team working on a project together is a positive security image.</figcaption></figure>In the next few guides, you'll learn how to keep your business and your users' content secure.

## What is a security vulnerability? <a href="#what-is-a-security-vulnerability" class="w-headline-link">#</a>

In software development, when an application does not work the way it is intended to work, it's called "a bug". Sometimes a bug displays wrong information or crashes on a certain action. A **vulnerability** (sometimes called a **security bug**) is a type of bug that could be used for abuse.

Bugs are common in the day to day activities of a developer. Which means, vulnerabilities are also frequently introduced into applications. What's important is that you are aware of common vulnerabilities in order to mitigate them as much as you can. It is just like minimizing other bugs by following common patterns and techniques.

Most security techniques are just good programming, for example:

- Check values entered by a user (not null, not an empty string, checking the amount of data).
- Ensure a single user can't take up too much time.
- Build unit tests so security bugs can't slip in by accident.

## What are security features? <a href="#what-are-security-features" class="w-headline-link">#</a>

Your first lines of defense are security features such as HTTPS and CORS. (You'll learn about these acronyms later so don't worry about them for now.) For example, encrypting data using HTTPS might not be fixing a bug, but it protects the data you're exchanging with users to other parties. (Intercepting data is a common attack.)

## What's the impact? <a href="#what&#39;s-the-impact" class="w-headline-link">#</a>

When an application is not secure, different people could be affected.

<table><colgroup><col style="width: 50%" /><col style="width: 50%" /></colgroup><tbody><tr class="odd"><td><strong>Impact on users</strong></td><td><ul><li>Sensitive information, such as personal data, could be leaked or stolen.</li><li>Content could be tampered with. A tampered site could direct users to a malicious site.</li></ul></td></tr><tr class="even"><td><strong>Impact on the application</strong></td><td><ul><li>User trust may be lost.</li><li>Business could be lost due to downtime or loss of confidence as a result of tampering or system shortage.</li></ul></td></tr><tr class="odd"><td><strong>Impact on other systems</strong></td><td><ul><li>A hijacked application could be used to attack other systems, such as with a denial-of-service attack using a botnet.</li></ul></td></tr></tbody></table>

Actively securing your application is not only crucial for you and your business but also for your users, protecting them and other systems from attacks launched from your site.

## Wrap up <a href="#wrap-up" class="w-headline-link">#</a>

Congratulations! You are halfway through this introduction. Now you know the difference between security vulnerabilities and features, and you are aware that not only you but everyone else gets affected when your application is not secure. The next guide covers the types of attacks in depth to make security even less scary.

<a href="/tags/security/" class="w-chip">Security</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/secure/security-not-scary/index.md)

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
