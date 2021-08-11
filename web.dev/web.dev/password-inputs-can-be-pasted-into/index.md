





<a href="#prevents-users-from-pasting-into-password-fields" class="w-toc__header--link">Prevents users from pasting into password fields</a>
--------------------------------------------------------------------------------------------------------------------------------------------

-   [How this Lighthouse audit fails](#how-this-lighthouse-audit-fails)
-   [How to enable pasting into password fields](#how-to-enable-pasting-into-password-fields)
-   [Find the code that's preventing pasting](#find-the-code-that's-preventing-pasting)
-   [Remove the code that's preventing pasting](#remove-the-code-that's-preventing-pasting)
-   [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Prevents users from pasting into password fields
================================================

May 2, 2019 <span class="w-author__separator">•</span> Updated Jun 4, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-best-practices" class="w-post-signpost__link">Best Practices audits</a>

Some websites claim that allowing users to paste passwords reduces security. However, password pasting actually *improves* security because it enables the use of password managers.

Password managers typically generate strong passwords for users, store them securely, and then automatically paste them into password fields whenever users need to log in. This approach is generally more secure than forcing users to type in passwords that are short enough to remember.

How this Lighthouse audit fails <a href="#how-this-lighthouse-audit-fails" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags code that prevents users from pasting into password fields:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0tAkhHny7nQu4pYJ9m9E.png?auto=format&amp;w=1600 1600w" width="800" height="163" /></figure>Lighthouse gathers all `<input type="password">` elements, pastes some text into each element, and then verifies that the element's content has been set to the pasted text.

If a page doesn't use `<input type="password">` for its password input fields, Lighthouse doesn't detect those elements. It's also possible to prevent pasting outside of a `paste` event listener. Lighthouse doesn't detect that scenario, either.

Each Best Practices audit is weighted equally in the Lighthouse Best Practices Score. Learn more in [The Best Practices score](https://developers.google.com/web/tools/lighthouse/v3/scoring#best-practices).

How to enable pasting into password fields <a href="#how-to-enable-pasting-into-password-fields" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------

### Find the code that's preventing pasting <a href="#find-the-code-that&#39;s-preventing-pasting" class="w-headline-link">#</a>

To quickly find and inspect the code that's preventing pasting:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Sources** tab.
3.  Expand the [**Event Listener Breakpoints**](https://developers.google.com/web/tools/chrome-devtools/javascript/breakpoints#event-listeners) pane.
4.  Expand the **Clipboard** list.
5.  Select the **`paste`** checkbox.
6.  Paste some text into a password field on your page.
7.  DevTools should pause on the first line of code in the relevant `paste` event listener.

### Remove the code that's preventing pasting <a href="#remove-the-code-that&#39;s-preventing-pasting" class="w-headline-link">#</a>

The source of the problem is often a call to `preventDefault()` within the `paste` event listener that's associated with the password input element:

    let input = document.querySelector('input');

    input.addEventListener('paste', (e) => {
      e.preventDefault(); // This is what prevents pasting.
    });

If you're only listening to paste events to preempt them, remove the entire event listener.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

[Source code for **Prevents users from pasting into password fields** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/dobetterweb/password-inputs-can-be-pasted-into.js)

<span class="w-mr--sm">Last updated: Jun 4, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-best-practices/password-inputs-can-be-pasted-into/index.md)

<a href="/lighthouse-best-practices" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
