<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#how-search-works" class="w-toc__header--link">How search works</a>

- [What does a search engine do?](#what-does-a-search-engine-do)
- [How crawlers browse the web](#how-crawlers-browse-the-web)
- [Building an index](#building-an-index)
- [Serving the most useful results](#serving-the-most-useful-results)
- [Next steps: how to optimize for search engines](#next-steps:-how-to-optimize-for-search-engines)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# How search works

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/discoverable" class="w-post-signpost__link">Easily discoverable</a>

[<img src="https://web-dev.imgix.net/image/admin/qAnatGOMJMeJhHbHwbWp.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Lizzi Harvey" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/qAnatGOMJMeJhHbHwbWp.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/qAnatGOMJMeJhHbHwbWp.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/qAnatGOMJMeJhHbHwbWp.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/qAnatGOMJMeJhHbHwbWp.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/qAnatGOMJMeJhHbHwbWp.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/ekharvey/)

<a href="/authors/ekharvey/" class="w-author__name-link">Lizzi Harvey</a>

- <a href="https://twitter.com/HarveyLizzi" class="w-author__link">Twitter</a>
- <a href="https://github.com/ekharvey" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@ekharvey" class="w-author__link">Glitch</a>

## What does a search engine do? <a href="#what-does-a-search-engine-do" class="w-headline-link">#</a>

Search engines are the digital version of a librarian. They use a comprehensive index to help find the right information for a query. Understanding the basics of search prepares you to make your content **discoverable** for users.

## How crawlers browse the web <a href="#how-crawlers-browse-the-web" class="w-headline-link">#</a>

Crawling is like reading through all the books in the library. Before search engines can bring any search results, they need to have as much information from the web as possible. To do this, search engines use a crawler—a program that travels from site to site and acts like a browser.

If a book or document is missing or damaged, the crawler can't read it. Crawlers try to fetch each URL to determine the state of the document. If a document returns an error status code, crawlers cannot use any of its content, and might retry the URL at a later time. This ensures only publicly accessible documents get into the index.

If crawlers discover a redirection status code (like 301 or 302), they follow the redirection to a new URL and continue there. Once they get a successful response, meaning they've found a document accessible to users, they check if it's allowed to be crawled and then download the content.

This check includes the HTML and all content mentioned in the HTML, such as images, videos, or JavaScript. Crawlers also extract the links from HTML documents so that the crawler can visit the linked URLs as well. Following links is how crawlers find new pages on the web.

Crawlers don't actively click links or buttons, but instead send URLs to a queue to crawl them later. When accessing a new URL, no cookies, service workers or local storage (like IndexedDB) are available.

## Building an index <a href="#building-an-index" class="w-headline-link">#</a>

After retrieving a document, the crawler hands the content to the search engine to add it to the index. The search engine now renders and analyzes the content to understand it. Rendering means displaying the page as a browser would ([with some limitations](https://developers.google.com/search/docs/guides/rendering)).

Search engines look at keywords, the title, links, headings, text, and many other things. These are called **signals** which describe the content and context of the page. Signals allow search engines to answer any given query with the best possible page.

Search engines might find the same content at different URLs. For example a recipe for "apple pie" might live under `/recipes/apple-pie` and under `/recipes/1234`. To avoid indexing and showing the recipe twice, search engines determine what the main URL should be and discard the alternative URLs showing the same content.

## Serving the most useful results <a href="#serving-the-most-useful-results" class="w-headline-link">#</a>

Search engines do more work then just matching the query to keywords in the index. To give useful results, they might consider context, alternative wording, location of the user, and more. For example, "silicon valley" might refer to the geographic region or the TV show. But if the query is "silicon valley cast", results on the region aren't very helpful.

Some queries can be indirect, like "the song from pulp fiction", and search engines need to interpret that and show results for the music in the film. When a user searches for something, search engines determine the most useful results and then show them to the user. Ranking, or ordering, the pages happens based on the query. The order can often change over time if better information becomes available.

## Next steps: how to optimize for search engines <a href="#next-steps:-how-to-optimize-for-search-engines" class="w-headline-link">#</a>

Now that you understand the basics of how search engines work, you may see the value in optimizing for search engines. This is called SEO, or 'Search Engine Optimization.' By making sure search engines can find and automatically understand your content, you are improving the visibility of your site for relevant searches. This can result in more interested users coming to your site. Audit your site with Lighthouse and check the SEO results to see how well search engines can surface your content.

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/discoverable/how-search-works/index.md)

<a href="/discoverable" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
