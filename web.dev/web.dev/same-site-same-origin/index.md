<a href="/" class="header-default__logo-link gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="header-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="header-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="header-default__link gc-analytics-event">Blog</a> <a href="/about/" class="header-default__link gc-analytics-event">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="drawer-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="drawer-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="drawer-default__link gc-analytics-event">Blog</a> <a href="/about/" class="drawer-default__link gc-analytics-event">About</a>

## <a href="#understanding-andquotsame-siteandquot-and-andquotsame-originandquot" class="w-toc__header--link">Understanding "same-site" and "same-origin"</a>

- [Origin](#origin)
- ["same-origin" and "cross-origin"](#same-origin-and-cross-origin)
- [Site](#site)
- ["same-site" and "cross-site"](#same-site-cross-site)
- ["schemeful same-site"](#)
- [How to check if a request is "same-site", "same-origin", or "cross-site"](#how-to-check-if-a-request-is-)

Share <a href="/newsletter/" class="w-actions__fab w-actions__fab--subscribe gc-analytics-event"><span>subscribe</span></a>

# Understanding "same-site" and "same-origin"

Apr 15, 2020 <span class="w-author__separator">•</span> Updated Jun 10, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/secure" class="w-post-signpost__link">Safe and secure</a>

[<img src="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Eiji Kitamura" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75 1x,     https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x,     https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x,     https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x,     https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/agektmr/)

<a href="/authors/agektmr/" class="w-author__name-link">Eiji Kitamura</a>

- <a href="https://twitter.com/agektmr" class="w-author__link">Twitter</a>
- <a href="https://github.com/agektmr" class="w-author__link">GitHub</a>
- <a href="https://blog.agektmr.com" class="w-author__link">Blog</a>

"same-site" and "same-origin" are frequently cited but often misunderstood terms. For example, they are mentioned in the context of page transitions, `fetch()` requests, cookies, opening popups, embedded resources, and iframes.

## Origin <a href="#origin" class="w-headline-link">#</a>

<img src="https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format" alt="Origin" sizes="(min-width: 680px) 680px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=200 200w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=228 228w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=260 260w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=296 296w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=338 338w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=385 385w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=439 439w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=500 500w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=571 571w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=650 650w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=741 741w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=845 845w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=964 964w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=1098 1098w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=1252 1252w,     https://web-dev.imgix.net/image/admin/PX5HrIMPlgcbzYac3FHV.png?auto=format&amp;w=1360 1360w" width="680" height="100" />

"Origin" is a combination of a [scheme](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Identifying_resources_on_the_Web#Scheme_or_protocol) (also known as the [protocol](https://developer.mozilla.org/en-US/docs/Glossary/Protocol), for example [HTTP](https://developer.mozilla.org/en-US/docs/Glossary/HTTP) or [HTTPS](https://developer.mozilla.org/en-US/docs/Glossary/HTTPS)), [hostname](https://en.wikipedia.org/wiki/Hostname), and [port](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Identifying_resources_on_the_Web#Port) (if specified). For example, given a URL of `https://www.example.com:443/foo` , the "origin" is `https://www.example.com:443`.

### "same-origin" and "cross-origin" <a href="#same-origin-and-cross-origin" class="w-headline-link">#</a>

Websites that have the combination of the same scheme, hostname, and port are considered "same-origin". Everything else is considered "cross-origin".

Origin A

Origin B

Explanation of whether Origin A and B are "same-origin" or "cross-origin"

https://www.example.com:443

https://**www.evil.com**:443

cross-origin: different domains

https://**example.com**:443

cross-origin: different subdomains

https://**login**.example.com:443

cross-origin: different subdomains

**http**://www.example.com:443

cross-origin: different schemes

https://www.example.com:**80**

cross-origin: different ports

**https://www.example.com:443**

**same-origin: exact match**

**https://www.example.com**

**same-origin: implicit port number (443) matches**

## Site <a href="#site" class="w-headline-link">#</a>

<img src="https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format" alt="Site" sizes="(min-width: 680px) 680px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=200 200w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=228 228w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=260 260w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=296 296w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=338 338w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=385 385w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=439 439w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=500 500w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=571 571w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=650 650w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=741 741w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=845 845w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=964 964w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=1098 1098w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=1252 1252w,     https://web-dev.imgix.net/image/admin/oSRJzCJIr4OjGzUhcNDP.png?auto=format&amp;w=1360 1360w" width="680" height="142" />

Top-level domains (TLDs) such as `.com` and `.org` are listed in the [Root Zone Database](https://www.iana.org/domains/root/db). In the example above, "site" is the combination of the TLD and the part of the domain just before it. For example, given a URL of `https://www.example.com:443/foo` , the "site" is `example.com`.

However, for domains such as `.co.jp` or `.github.io`, just using the TLD of `.jp` or `.io` is not granular enough to identify the "site". And there is no way to algorithmically determine the level of registrable domains for a particular TLD. That's why a list of "effective TLDs"(eTLDs) was created. These are defined in the [Public Suffix List](https://wiki.mozilla.org/Public_Suffix_List). The list of eTLDs is maintained at [publicsuffix.org/list](https://publicsuffix.org/list/).

The whole site name is known as the eTLD+1. For example, given a URL of `https://my-project.github.io` , the eTLD is `.github.io` and the eTLD+1 is `my-project.github.io`, which is considered a "site". In other words, the eTLD+1 is the effective TLD and the part of the domain just before it.

<img src="https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format" alt="eTLD+1" sizes="(min-width: 695px) 695px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=200 200w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=228 228w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=260 260w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=296 296w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=338 338w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=385 385w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=439 439w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=500 500w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=571 571w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=650 650w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=741 741w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=845 845w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=964 964w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=1098 1098w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=1252 1252w,     https://web-dev.imgix.net/image/admin/qmr35hpnIvpouOe9591g.png?auto=format&amp;w=1390 1390w" width="695" height="136" />

### "same-site" and "cross-site" <a href="#same-site-cross-site" class="w-headline-link">#</a>

Websites that have the same eTLD+1 are considered "same-site". Websites that have a different eTLD+1 are "cross-site".

Origin A

Origin B

Explanation of whether Origin A and B are "same-site" or "cross-site"

https://www.example.com:443

https://**www.evil.com**:443

cross-site: different domains

https://**login**.example.com:443

**same-site: different subdomains don't matter**

**http**://www.example.com:443

**same-site: different schemes don't matter**

https://www.example.com:**80**

**same-site: different ports don't matter**

**https://www.example.com:443**

**same-site: exact match**

**https://www.example.com**

**same-site: ports don't matter**

### "schemeful same-site" <a href="#%22schemeful-same-site%22" class="w-headline-link">#</a>

<img src="https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format" alt="schemeful same-site" sizes="(min-width: 677px) 677px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=200 200w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=228 228w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=260 260w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=296 296w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=338 338w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=385 385w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=439 439w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=500 500w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=571 571w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=650 650w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=741 741w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=845 845w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=964 964w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=1098 1098w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=1252 1252w,     https://web-dev.imgix.net/image/admin/Y9LbVyxYzg4k6mwSEqyE.png?auto=format&amp;w=1354 1354w" width="677" height="105" />

The definition of "same-site" is evolving to consider the URL scheme as part of the site in order to prevent HTTP being used as [a weak channel](https://tools.ietf.org/html/draft-west-cookie-incrementalism-01#page-8). As browsers move to this interpretation you may see references to "scheme-less same-site" when referring to the older definition and "[schemeful same-site](/schemeful-samesite/)" referring to the stricter definition. In that case, `http://www.example.com` and `https://www.example.com` are considered cross-site because the schemes don't match.

Origin A

Origin B

Explanation of whether Origin A and B are "schemeful same-site"

https://www.example.com:443

https://**www.evil.com**:443

cross-site: different domains

https://**login**.example.com:443

**schemeful same-site: different subdomains don't matter**

**http**://www.example.com:443

cross-site: different schemes

https://www.example.com:**80**

**schemeful same-site: different ports don't matter**

**https://www.example.com:443**

**schemeful same-site: exact match**

**https://www.example.com**

**schemeful same-site: ports don't matter**

## How to check if a request is "same-site", "same-origin", or "cross-site" <a href="#how-to-check-if-a-request-is-%22same-site%22-%22same-origin%22-or-%22cross-site%22" class="w-headline-link">#</a>

Chrome sends requests along with a `Sec-Fetch-Site` HTTP header. No other browsers support `Sec-Fetch-Site` as of April 2020. This is part of a larger [Fetch Metadata Request Headers](https://www.w3.org/TR/fetch-metadata/) proposal. The header will have one of the following values:

- `cross-site`
- `same-site`
- `same-origin`
- `none`

By examining the value of `Sec-Fetch-Site`, you can determine if the request is "same-site", "same-origin", or "cross-site" ("schemeful-same-site" is not captured in `Sec-Fetch-Site`).

<a href="/tags/security/" class="w-chip">Security</a>

<span class="w-mr--sm"> Last updated: Jun 10, 2020 </span> [Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/secure/same-site-same-origin/index.md)

<a href="/secure" class="w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single gc-analytics-event">Return to all articles</a>

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
