





<a href="#offscreen-content-is-hidden-from-assistive-technology" class="w-toc__header--link">Offscreen content is hidden from assistive technology</a>
------------------------------------------------------------------------------------------------------------------------------------------------------

-   [How to manually test](#how-to-manually-test)
-   [How to fix](#how-to-fix)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Offscreen content is hidden from assistive technology
=====================================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

Ensure that only relevant parts of the page are exposed to screen readers and other assistive technologies. For instance, content that's offscreen or just presentational should be hidden from assistive technologies.

How to manually test <a href="#how-to-manually-test" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

To check that offscreen content is hidden, you need to manually test that content using a screen reader.

-   For Mac users, check out [this video on using VoiceOver](https://www.youtube.com/watch?v=5R-6WvAihms&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g&index=6).
-   For PC users, check out [this video on using NVDA](https://www.youtube.com/watch?v=Jao3s_CwdRU&list=PLNYkxOF6rcICWx0C9LVWWVqvHlYJyqw7g&index=4).
-   For Chromebooks users, check out [ChromeVox, the built-in screen reader](https://support.google.com/chromebook/answer/7031755?hl=en).

Use the `TAB` key to tab through your page. The screen reader shouldn't announce hidden content.

How to fix <a href="#how-to-fix" class="w-headline-link">#</a>
--------------------------------------------------------------

To hide offscreen content, remove the element containing that content from the tab order by setting it to `display: none` or `visibility: hidden`.

For example:

    .remove-me {
      visibility: hidden;
    }

    <button class="remove-me">Can't reach me with the TAB key!</button>

See also [Correctly set the visibility of offscreen content](/keyboard-access/#correctly-set-the-visibility-of-offscreen-content).

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

[Source code for **Offscreen content is hidden from assistive technology** audit](https://github.com/GoogleChrome/lighthouse/blob/ecd10efc8230f6f772e672cd4b05e8fbc8a3112d/lighthouse-core/audits/accessibility/manual/offscreen-content-hidden.js)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/offscreen-content-hidden/index.md)

<a href="/lighthouse-accessibility" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
