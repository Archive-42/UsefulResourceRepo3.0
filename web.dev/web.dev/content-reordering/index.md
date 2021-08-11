





## <a href="#content-reordering" class="w-toc__header--link">Content reordering</a>

- [Source vs. visual order](#source-vs.-visual-order)
- [Which CSS properties can cause reordering?](#which-css-properties-can-cause-reordering)
- [Testing for the problem](#testing-for-the-problem)
- [Content reordering and responsive web design](#content-reordering-and-responsive-web-design)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Content reordering

May 29, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/accessible" class="w-post-signpost__link">Accessible to all</a>

[<img src="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rachel Andrew" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rachelandrew/)

<a href="/authors/rachelandrew/" class="w-author__name-link">Rachel Andrew</a>

- <a href="https://twitter.com/rachelandrew" class="w-author__link">Twitter</a>
- <a href="https://github.com/rachelandrew" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@rachelandrew" class="w-author__link">Glitch</a>
- <a href="https://rachelandrew.co.uk/" class="w-author__link">Blog</a>

The order of content in your document is important for the accessibility of your site. A screen reader will read out content based on the document order, using the HTML elements that you have selected to give meaning to that content. A person navigating the site using a keyboard, rather than a touchscreen or mouse, will tab around the document. This means that they will jump from active element to active element, tabbing between links and form fields, once again in the order they exist in the document.

Starting with a well-structured document and using all of the right HTML elements is therefore a key part of creating an accessible site. However, it is possible to undo some of that good work when you start using CSS. Let's take a look at why.

## Source vs. visual order <a href="#source-vs.-visual-order" class="w-headline-link">#</a>

Website navigation is often marked up as a list of links. You can then use [Flexbox](/responsive-web-design-basics/#flexbox) to turn these into a horizontal bar. In the Glitch example below, I have created this commonly used pattern. Click into the example, and tab between the links. The focus will move in a logical direction from left to right, the order that we read in English.

If you have created this sort of pattern and then were asked to move **Contact Us**, which is second in the source, to the end. You could use the `order` property which works in Flexbox. Try tabbing through the items in the example below, which has used the `order` property to rearrange the items.

The focus jumps to the final item and then back again. As far as the tab order is concerned that item is the second item. Visually however, it's the last item.

The above example highlights the problem that we face if we rearrange and reorder content using CSS. If you were dealing with this issue then the right thing to do would be to change the order in the source, rather than using CSS.

## Which CSS properties can cause reordering? <a href="#which-css-properties-can-cause-reordering" class="w-headline-link">#</a>

Any layout method that allows you to move elements around can cause this problem. The following CSS properties commonly cause content reordering problems:

- Using `position: absolute` and taking an item out of flow visually.
- The `order` property in Flexbox and Grid layout.
- The `row-reverse` and `column-reverse` values for `flex-direction` in Flexbox.
- The `dense` value for `grid-auto-flow` in Grid Layout.
- Any positioning by line name or number, or with `grid-template-areas` in Grid Layout.

In this next example, I have created a layout using CSS Grid and positioned the items using line numbers, without considering where they are in the source.

Try tabbing around this example, and see how the focus jumps about. This makes for a very confusing experience, especially if this is a long page.

## Testing for the problem <a href="#testing-for-the-problem" class="w-headline-link">#</a>

A very simple test is to keyboard navigate through your page. Can you get to everything? Are there any strange jumps as you do so?

For a visual demonstration of content reordering, try the Tab Stop checker in the [Accessibility Insights](https://accessibilityinsights.io/) extension for Chrome. The image below shows the CSS Grid example in that tool. You can see how the focus has to jump around the layout.

## <figure><img src="https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/n0i0TJf3OdZYvwswrHDV.jpg?auto=format&amp;w=1600 1600w" width="800" height="919" /></figure>Content reordering and responsive web design <a href="#content-reordering-and-responsive-web-design" class="w-headline-link">#</a>

If you only have one presentation of your content, then having your source in a logical order, and reflecting that in layout is not usually difficult. It can become harder, when you consider the layout at different breakpoints. It might make sense to have an element moved to the bottom of the layout on smaller screens for example.

There is not at this time a good solution for this problem. In most situations developing "mobile first", will help you keep your source and layout in order. The choices you make about priority on mobile, are often solid ones for the content in general. The key is to be aware when there is a possibility of this type of content reordering, and to test that the end experience is not too jarring at each breakpoint.

<a href="/tags/accessibility/" class="w-chip">Accessibility</a>

<span class="w-mr--sm">Last updated: May 29, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/accessible/content-reordering/index.md)

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
