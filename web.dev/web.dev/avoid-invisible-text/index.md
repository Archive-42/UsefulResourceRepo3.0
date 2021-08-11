<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#avoid-invisible-text-during-font-loading" class="w-toc__header--link">Avoid invisible text during font loading</a>
----------------------------------------------------------------------------------------------------------------------------

-   [Why should you care?](#why-should-you-care)
-   [Display text immediately](#display-text-immediately)
-   [Option1: Use font-display \#](#option-1:-use-font-display)
-   [Option2: Wait to use custom fonts until they are loaded \#](#option-2:-wait-to-use-custom-fonts-until-they-are-loaded)
-   [Verify](#verify)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Avoid invisible text during font loading
========================================

Nov 5, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

-   <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
-   <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
-   <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

Why should you care? <a href="#why-should-you-care" class="w-headline-link">#</a>
---------------------------------------------------------------------------------

Fonts are often large files that take awhile to load. To deal with this, some browsers hide text until the font loads (the "flash of invisible text"). If you're optimizing for performance, you'll want to avoid the "flash of invisible text" and show content to users immediately using a system font (the "flash of unstyled text").

Display text immediately <a href="#display-text-immediately" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------

This guide outlines two ways to achieve this: the first approach is very simple but does not have universal browser [support](https://caniuse.com/#search=font-display); the second approach is more work but has full browser support. The best choice for you is the one that you'll actually implement and maintain.

Option \#1: Use font-display <a href="#option-1:-use-font-display" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------

<table><thead><tr class="header"><th>Before</th><th>After</th></tr></thead><tbody><tr class="odd"><td><code>@font-face { font-family: Helvetica; }</code></td><td><code>@font-face { font-family: Helvetica; font-display: swap; }</code></td></tr></tbody></table>

[`font-display`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face/font-display) is an API for specifying font display strategy. `swap` tells the browser that text using this font should be displayed immediately using a system font. Once the custom font is ready, the system font is swapped out.

If a browser does not support `font-display`, the browser continues to follow it's default behavior for loading fonts. Check which browsers support `font-display` [here](https://caniuse.com/#search=font-display).

These are the default font-loading behaviors for common browsers:

<table><thead><tr class="header"><th><strong>Browser</strong></th><th><strong>Default behavior if font is not ready…</strong></th></tr></thead><tbody><tr class="odd"><td>Edge</td><td>Uses a system font until font is ready. Swaps out font.</td></tr><tr class="even"><td>Chrome</td><td>Will hide text for up to 3 seconds. If text is still not ready, uses a system font until font is ready. Swaps out font.</td></tr><tr class="odd"><td>Firefox</td><td>Will hide text for up to 3 seconds. If text is still not ready, uses a system font until font is ready. Swaps out font.</td></tr><tr class="even"><td>Safari</td><td>Hides text until font is ready.</td></tr></tbody></table>

Option \#2: Wait to use custom fonts until they are loaded <a href="#option-2:-wait-to-use-custom-fonts-until-they-are-loaded" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------------------------------------

With a bit more work, the same behavior can be implemented to work across all browsers.

There are three parts to this approach:

-   Don't use a custom font on initial page load. This ensures that the browser displays text immediately using a system font.
-   Detect when your custom font is loaded. This can be accomplished with a couple lines of JavaScript code, thanks to the [FontFaceObserver](https://github.com/bramstein/fontfaceobserver) library.
-   Update page styling to use the custom font.

Here are the changes you can expect to make in order to implement this:

-   Refactor your CSS to not use a custom font on initial page load.
-   Add a script to your page. This script detects when the custom font is loaded and then will update the page styling.

**Try it**! [Use Font Face Observer to display text immediately](/codelab-avoid-invisible-text).

Verify <a href="#verify" class="w-headline-link">#</a>
------------------------------------------------------

Run Lighthouse to verify the site is using `font-display: swap` to display text:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Lighthouse** tab.
3.  Make sure the **Performance** checkbox is selected in the *Categories* list.
4.  Click the **Generate report** button.

Confirm that the **Ensure text remains visible during webfont load** audit is passing.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Nov 5, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/avoid-invisible-text/index.md)

Codelabs
--------

See it in action

Learn more and put this guide into action.

-   <a href="/codelab-avoid-invisible-text/" class="w-callout__link w-callout__link--codelab">Avoid flash of invisible text</a>

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
