## <a href="#lesscodegreaterrobots.txtlesscodegreater-is-not-valid" class="w-toc__header--link"><code>robots.txt</code> is not valid</a>

- [How the Lighthouse robots.txt audit fails](#how-the-lighthouse-robots.txt-audit-fails)
- [How to fix problems with robots.txt](#how-to-fix-problems-with-robots.txt)
- [Make sure robots.txt doesn't return an HTTP 5XX status code](#make-sure-robots.txt-doesn't-return-an-http-5xx-status-code)
- [Keep robots.txt smaller than 500 KiB](#keep-robots.txt-smaller-than-500-kib)
- [Fix any format errors](#fix-any-format-errors)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# `robots.txt` is not valid

May 2, 2019 <span class="w-author__separator">•</span> Updated May 29, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-seo" class="w-post-signpost__link">SEO audits</a>

The `robots.txt` file tells search engines which of your site's pages they can crawl. An invalid `robots.txt` configuration can cause two types of problems:

- It can keep search engines from crawling public pages, causing your content to show up less often in search results.
- It can cause search engines to crawl pages you may not want shown in search results.

## How the Lighthouse `robots.txt` audit fails <a href="#how-the-lighthouse-robots.txt-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags invalid `robots.txt` files:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format" class="w-screenshot w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/X29ztochZPiUVwPo2rg3.png?auto=format&amp;w=1600 1600w" width="800" height="203" /></figure>Most Lighthouse audits only apply to the page that you're currently on. However, since `robots.txt` is defined at the host-name level, this audit applies to your entire domain (or subdomain).

Expand the **`robots.txt` is not valid** audit in your report to learn what's wrong with your `robots.txt`.

Common errors include:

- `No user-agent specified`
- `Pattern should either be empty, start with "/" or "*"`
- `Unknown directive`
- `Invalid sitemap URL`
- `$ should only be used at the end of the pattern`

Lighthouse doesn't check that your `robots.txt` file is in the correct location. To function correctly, the file must be in the root of your domain or subdomain.

Each SEO audit is weighted equally in the Lighthouse SEO Score, except for the manual **[Structured data is valid](/structured-data)** audit. Learn more in the [Lighthouse Scoring Guide](https://developers.google.com/web/tools/lighthouse/v3/scoring).

## How to fix problems with `robots.txt` <a href="#how-to-fix-problems-with-robots.txt" class="w-headline-link">#</a>

### Make sure `robots.txt` doesn't return an HTTP 5XX status code <a href="#make-sure-robots.txt-doesn&#39;t-return-an-http-5xx-status-code" class="w-headline-link">#</a>

If your server returns a server error (an [HTTP status code](/http-status-code) in the 500s) for `robots.txt`, search engines won't know which pages should be crawled. They may stop crawling your entire site, which would prevent new content from being indexed.

To check the HTTP status code, open `robots.txt` in Chrome and [check the request in Chrome DevTools](https://developers.google.com/web/tools/chrome-devtools/network/reference#analyze).

### Keep `robots.txt` smaller than 500 KiB <a href="#keep-robots.txt-smaller-than-500-kib" class="w-headline-link">#</a>

Search engines may stop processing `robots.txt` midway through if the file is larger than 500 KiB. This can confuse the search engine, leading to incorrect crawling of your site.

To keep `robots.txt` small, focus less on individually excluded pages and more on broader patterns. For example, if you need to block crawling of PDF files, don't disallow each individual file. Instead, disallow all URLs containing `.pdf` by using `disallow: /*.pdf`.

### Fix any format errors <a href="#fix-any-format-errors" class="w-headline-link">#</a>

- Only empty lines, comments, and directives matching the "name: value" format are allowed in `robots.txt`.
- Make sure `allow` and `disallow` values are either empty or start with `/` or `*`.
- Don't use `$` in the middle of a value (for example, `allow: /file$html`).

#### Make sure there's a value for `user-agent` <a href="#make-sure-there&#39;s-a-value-for-user-agent" class="w-headline-link">#</a>

User-agent names to tell search engine crawlers which directives to follow. You must provide a value for each instance of `user-agent` so search engines know whether to follow the associated set of directives.

To specify a particular search engine crawler, use a user-agent name from its published list. (For example, here's [Google's list of user-agents used for crawling](https://support.google.com/webmasters/answer/1061943).)

Use `*` to match all otherwise unmatched crawlers.

Don't

    user-agent:
    disallow: /downloads/

No user agent is defined.

Do

    user-agent: *
    disallow: /downloads/

    user-agent: magicsearchbot
    disallow: /uploads/

A general user agent and a `magicsearchbot` user agent are defined.

#### Make sure there are no `allow` or `disallow` directives before `user-agent` <a href="#make-sure-there-are-no-allow-or-disallow-directives-before-user-agent" class="w-headline-link">#</a>

User-agent names define the sections of your `robots.txt` file. Search engine crawlers use those sections to determine which directives to follow. Placing a directive _before_ the first user-agent name means that no crawlers will follow it.

Don't

    # start of file
    disallow: /downloads/

    user-agent: magicsearchbot
    allow: /

No search engine crawler will read the `disallow: /downloads` directive.

Do

    # start of file
    user-agent: *
    disallow: /downloads/

All search engines are disallowed from crawling the `/downloads` folder.

Search engine crawlers only follow directives in the section with the most specific user-agent name. For example, if you have directives for `user-agent: *` and `user-agent: Googlebot-Image`, Googlebot Images will only follow the directives in the `user-agent: Googlebot-Image` section.

#### Provide an absolute URL for `sitemap` <a href="#provide-an-absolute-url-for-sitemap" class="w-headline-link">#</a>

[Sitemap](https://support.google.com/webmasters/answer/156184) files are a great way to let search engines know about pages on your website. A sitemap file generally includes a list of the URLs on your website, together with information about when they were last changed.

If you choose to submit a sitemap file in `robots.txt`, make sure to use an [absolute URL](https://tools.ietf.org/html/rfc3986#page-27).

Don't

    sitemap: /sitemap-file.xml

Do

    sitemap: https://example.com/sitemap-file.xml

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **`robots.txt` is not valid** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/seo/robots-txt.js)
- [Create a `robots.txt file`](https://support.google.com/webmasters/answer/6062596)
- [Robots.txt](https://moz.com/learn/seo/robotstxt)
- [Robots meta tag and X-Robots-Tag HTTP header specifications](https://developers.google.com/search/reference/robots_meta_tag)
- [Learn about sitemaps](https://support.google.com/webmasters/answer/156184)
- [Google crawlers (user agents)](https://support.google.com/webmasters/answer/1061943)

<span class="w-mr--sm">Last updated: May 29, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-seo/robots-txt/index.md)

<a href="/lighthouse-seo" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
