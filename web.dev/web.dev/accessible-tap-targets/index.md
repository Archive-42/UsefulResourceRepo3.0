## <a href="#accessible-tap-targets" class="w-toc__header--link">Accessible tap targets</a>

- [Testing your touch targets](#testing-your-touch-targets)
- [Using media queries to detect touchscreen use](#using-media-queries-to-detect-touchscreen-use)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Accessible tap targets

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

When your design is displayed on a mobile device, you should ensure that interactive elements like buttons or links are large enough, and have enough space around them, to make them easy to press without accidentally overlapping onto other elements. This benefits all users, but is especially helpful for anyone with a motor impairment.

A minimum recommended touch target size is around 48 device independent pixels on a site with a properly set mobile viewport. For example, while an icon may only have a width and height of 24px, you can use additional padding to bring the tap target size up to 48px. The 48x48 pixel area corresponds to around 9mm, which is about the size of a person's finger pad area.

In the demo, I have added padding to all of the links in order to make sure they meet the minimum size.

Touch targets should also be spaced about 8 pixels apart, both horizontally and vertically, so that a user's finger pressing on one tap target does not inadvertently touch another tap target.

## Testing your touch targets <a href="#testing-your-touch-targets" class="w-headline-link">#</a>

If your target is text and you have used relative values such as `em` or `rem` to size the text and any padding, you can use DevTools to check that the computed value of that area is large enough. In the example below I am using `em` for my text and padding.

Inspect the `a` of the link, and in Chrome DevTools switch to the [Computed pane](https://developers.google.com/web/tools/chrome-devtools/css/overrides#computed) where you can inspect the various parts of the box and see what pixel size they resolve to. In Firefox DevTools there is a Layout Panel. In that Panel you get the actual size of the inspected element.

## <figure><img src="https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/vmFzREveRttHVDfLqqCx.jpg?auto=format&amp;w=1600 1600w" width="800" height="565" /></figure>Using media queries to detect touchscreen use <a href="#using-media-queries-to-detect-touchscreen-use" class="w-headline-link">#</a>

One of the media features we can now test for with media queries is whether the user's primary input is a touchscreen. The `pointer` feature will return `fine` or `coarse`. A fine pointer will be someone using a mouse or trackpad, even if that mouse is connected via Bluetooth to a phone. A `coarse` pointer indicates a touchscreen, which could be a mobile device but may also be a laptop screen or large tablet.

If you are adjusting your CSS within a media query to increase the touch target, testing for a coarse pointer allows you to increase the tap targets for all touchscreen users. This gives the larger tap area whether the device is a phone or larger device, while testing for width only gives you mobile users.

    .container a {
      padding: .2em;
    }

    @media (pointer: coarse) {
      .container a {
        padding: .8em;
      }
    }

You can find out more about interaction media features such as pointer in the [Responsive web design basics](/responsive-web-design-basics/) article.

<a href="/tags/accessibility/" class="w-chip">Accessibility</a>

<span class="w-mr--sm">Last updated: May 29, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/accessible/accessible-tap-targets/index.md)

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
