## <a href="#accessible-responsive-design" class="w-toc__header--link">Accessible responsive design</a>

- [Use the viewport meta tag](#use-the-viewport-meta-tag)
- [Allow users to zoom](#allow-users-to-zoom)
- [Design with flexibility](#design-with-flexibility)
- [Use relative units for text](#use-relative-units-for-text)
- [Avoid disconnecting the visual view from the source order](#avoid-disconnecting-the-visual-view-from-the-source-order)
- [Take care with spatial clues](#take-care-with-spatial-clues)
- [Ensure tap targets are large enough on touchscreen devices](#ensure-tap-targets-are-large-enough-on-touchscreen-devices)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Accessible responsive design

Mar 31, 2020 <span class="w-author__separator">•</span> Updated May 29, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/accessible" class="w-post-signpost__link">Accessible to all</a>

[<img src="https://web-dev.imgix.net/image/admin/SVZgPh6bWnji4cQyL38l.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Dave Gash" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/SVZgPh6bWnji4cQyL38l.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/SVZgPh6bWnji4cQyL38l.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/SVZgPh6bWnji4cQyL38l.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/SVZgPh6bWnji4cQyL38l.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/SVZgPh6bWnji4cQyL38l.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/dgash/)

<a href="/authors/dgash/" class="w-author__name-link">Dave Gash</a>

[<img src="https://web-dev.imgix.net/image/admin/1sJM27b1jwZmcKa6yJEf.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Meggin Kearney" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1sJM27b1jwZmcKa6yJEf.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/1sJM27b1jwZmcKa6yJEf.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/1sJM27b1jwZmcKa6yJEf.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/1sJM27b1jwZmcKa6yJEf.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/1sJM27b1jwZmcKa6yJEf.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/megginkearney/)

<a href="/authors/megginkearney/" class="w-author__name-link">Meggin Kearney</a>

- <a href="https://twitter.com/megginkearney" class="w-author__link">Twitter</a>

[<img src="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rachel Andrew" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rachelandrew/)

<a href="/authors/rachelandrew/" class="w-author__name-link">Rachel Andrew</a>

- <a href="https://twitter.com/rachelandrew" class="w-author__link">Twitter</a>
- <a href="https://github.com/rachelandrew" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@rachelandrew" class="w-author__link">Glitch</a>
- <a href="https://rachelandrew.co.uk/" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rob Dodson" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/robdodson/)

<a href="/authors/robdodson/" class="w-author__name-link">Rob Dodson</a>

- <a href="https://twitter.com/rob_dodson" class="w-author__link">Twitter</a>
- <a href="https://github.com/robdodson" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@robdodson" class="w-author__link">Glitch</a>
- <a href="https://robdodson.me" class="w-author__link">Blog</a>

We know that it's a good idea to design responsively to provide the best multi-device experience, but responsive design also yields a win for accessibility.

Consider a site like [Udacity](https://udacity.com):

<figure><img src="https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/5q9dDtEubSM23SzokQNu.jpg?auto=format&amp;w=1600 1600w" width="800" height="393" /></figure>A low-vision user who has difficulty reading small print might zoom in the page, perhaps as much as 400%. Because the site is designed responsively, the UI will rearrange itself for the "smaller viewport" (actually for the larger page), which is great for desktop users who require screen magnification and for mobile screen reader users as well. It's a win-win. Here's the same page magnified to 400%:

<figure><img src="https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/WKHO21uWQz5lJ7Aqej1E.jpg?auto=format&amp;w=1600 1600w" width="800" height="393" /></figure>In fact, just by designing responsively, we're meeting rule [1.4.4 of the WebAIM checklist](https://webaim.org/standards/wcag/checklist#sc1.4.4), which states that a page "… should be readable and functional when the text size is doubled."

Going over all of responsive design is outside the scope of this guide, but here are a few important takeaways that will benefit your responsive experience and give your users better access to your content.

## Use the viewport meta tag <a href="#use-the-viewport-meta-tag" class="w-headline-link">#</a>

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

Setting `width=device-width` will match the screen's width in device-independent pixels, and setting `initial-scale=1` establishes a 1:1 relationship between CSS pixels and device-independent pixels. Doing this instructs the browser to fit your content to the screen size, so users don't just see a bunch of scrunched-up text.

See [Size content to viewport](/responsive-web-design-basics/#viewport) to learn more.

## Allow users to zoom <a href="#allow-users-to-zoom" class="w-headline-link">#</a>

It is possible to use the viewport meta tag to prevent zooming, by setting `maximum-scale=1` or `user-scaleable=no`. Avoid doing this, and let your users zoom in if they need to.

## Design with flexibility <a href="#design-with-flexibility" class="w-headline-link">#</a>

Avoid targetting specific screen sizes and instead use a flexible grid, making changes to the layout when the content dictates. As we saw with the Udacity example above, this approach ensures that the design responds whether the reduced space is due to a smaller screen or a higher zoom level.

You can read more about these techniques in the [Responsive web design basics](/responsive-web-design-basics/) article.

## Use relative units for text <a href="#use-relative-units-for-text" class="w-headline-link">#</a>

To get the best out of your flexible grid use relative units like em or rem for things like text size, instead of pixel values. Some browsers support resizing text only in user preferences, and if you're using a pixel value for text, this setting will not affect your copy. If, however, you've used relative units throughout, then the site copy will update to reflect the user's preference.

This will enable the whole site to reflow as the user zooms, creating the reading experience they need to use your site.

## Avoid disconnecting the visual view from the source order <a href="#avoid-disconnecting-the-visual-view-from-the-source-order" class="w-headline-link">#</a>

A visitor who is tabbing through your site with the keyboard will be following the order of the content in the HTML document. When using modern layout methods such as [Flexbox](/responsive-web-design-basics/#flexbox) and [Grid](/responsive-web-design-basics/#grid), it is easy to make the visual rendering not match the source order. This can lead to disconcerting jumps around the page for someone using the keyboard to move around.

Make sure to test your design at each breakpoint by tabbing through the content, does the flow through the page still make sense?

Read more about [the source and visual display disconnect](/content-reordering/).

## Take care with spatial clues <a href="#take-care-with-spatial-clues" class="w-headline-link">#</a>

When writing microcopy avoid using language which indicates the location of an element on the page. For example, referring to navigation "on your left" makes no sense in a mobile version when the navigation is at the top of the screen.

## Ensure tap targets are large enough on touchscreen devices <a href="#ensure-tap-targets-are-large-enough-on-touchscreen-devices" class="w-headline-link">#</a>

On touchscreen devices make sure your tap targets are large enough to make them easy to activate without hitting other links. A good size for any tappable element is 48px, read more guidance on [tap targets](/accessible-tap-targets/).

<a href="/tags/accessibility/" class="w-chip">Accessibility</a>

<span class="w-mr--sm">Last updated: May 29, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/accessible/accessible-responsive-design/index.md)

<a href="/accessible" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
