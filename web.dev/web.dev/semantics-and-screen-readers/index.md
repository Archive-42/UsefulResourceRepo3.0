





<a href="#semantics-and-screen-readers" class="w-toc__header--link">Semantics and screen readers</a>
----------------------------------------------------------------------------------------------------

-   [Affordances and semantics](#affordances-and-semantics)
-   [Use semantic HTML](#use-semantic-html)
-   [Semantic properties and the accessibility tree](#semantic-properties-and-the-accessibility-tree)
-   [The accessibility tree](#the-accessibility-tree)
-   [Next steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Semantics and screen readers
============================

Nov 18, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/accessible" class="w-post-signpost__link">Accessible to all</a>

[<img src="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rob Dodson" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/robdodson/)

<a href="/authors/robdodson/" class="w-author__name-link">Rob Dodson</a>

-   <a href="https://twitter.com/rob_dodson" class="w-author__link">Twitter</a>
-   <a href="https://github.com/robdodson" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@robdodson" class="w-author__link">Glitch</a>
-   <a href="https://robdodson.me" class="w-author__link">Blog</a>

Have you ever stopped to wonder *how* assistive technology, such as a screen reader, knows what to announce to users? The answer is that these technologies rely on developers marking up their pages with **semantic** HTML. But what are semantics, and how do screen readers use them?

Affordances and semantics <a href="#affordances-and-semantics" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

Before diving into semantics, it's helpful to understand another term: **affordances**. An affordance is any object that offers, or affords, its user the opportunity to perform an action. A classic example is the teapot:

<figure><img src="https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format" alt="A teapot&#39;s handle is a natural affordance." sizes="(min-width: 640px) 640px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/EXqR31Kq3mosH6jv6jiG.png?auto=format&amp;w=1280 1280w" width="640" height="446" /><figcaption>A teapot's handle is a natural affordance.</figcaption></figure>This teapot doesn't need an instruction manual; instead, its physical design conveys to the user how it should be operated. It has a handle, and because you've seen other objects in the world with similar handles, you can infer how you should pick it up and operate it.

When we build graphical user interfaces, we use things like CSS to add **visual affordances** to our UI. For instance, you might give a button a drop shadow and border so that it resembles an actual button in the real world.

But if a user is unable to see the screen, then these visual affordances will not be conveyed to them. Therefore, you need to make sure that your UI is constructed in a way that can convey these same affordances to assistive technology. This non-visual exposure of a UI element's affordances is called its **semantics**.

Use semantic HTML <a href="#use-semantic-html" class="w-headline-link">#</a>
----------------------------------------------------------------------------

The easiest way of conveying proper semantics is to use semantically rich HTML elements.

Using CSS, it's possible to style the `<div>` and `<button>` elements so they convey the same visual affordances, but the two experiences are very different when using a screen reader. A `<div>` is just a generic grouping element, so a screen reader only announces the text content of the `<div>`. The `<button>` is announced as a "button," a much stronger signal to the user that it's something they can interact with.

The simplest and often best solution to this problem is to avoid custom interactive controls altogether. For example, replace a `<div>` that's acting like a button with an actual `<button>`.

Semantic properties and the accessibility tree <a href="#semantic-properties-and-the-accessibility-tree" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------

Generally speaking, every HTML element will have some of the following semantic properties:

-   A **role** or type
-   A **name**
-   A **value** (optional)
-   A **state** (optional)

An element's **role** describes its type, i.e. "button," "input," or even just "group" for things like `div`'s and `span`'s.

An element's **name** is its computed label. Screen readers typically announce an element's name followed by its role, e.g. "Sign Up, button." The algorithm that determines an element's name factors in things like if there is any text content inside the element, whether or not it has attributes such as `title` or `placeholder`, whether or not the element is associated with an actual `<label>` element, and if the element has any ARIA attributes such as `aria-label` and `aria-labelledby`.

Some elements *may* have a **value**. For instance, `<input type="text">` may have a value that reflects whatever the user has typed into the text field.

Some elements *may* also have a **state**, which conveys their current status. For instance, a `<select>` element can be in either an *expanded* or a *collapsed* state, depending on if it's open or closed.

### The accessibility tree <a href="#the-accessibility-tree" class="w-headline-link">#</a>

For each node in the DOM, the browser determines if the node is semantically "interesting" and adds it to [the accessibility tree](https://developers.google.com/web/fundamentals/accessibility/semantics-builtin/the-accessibility-tree). When assistive technology, like a screen reader, is providing an alternative UI to the user, it is often doing so by walking this accessibility tree.

Browsers will often remove semantically uninteresting nodes like `div` and `span` from the accessibility tree, especially if they're just being used to position their children with CSS. For instance, if you have a `button` nested inside of 5 `div`'s, the browser may prune out some of the `div`'s in the middle to cut down on noise.

Using Chrome's DevTools you can [inspect an element's semantic properties](https://developers.google.com/web/tools/chrome-devtools/accessibility/reference#pane) and explore its position in the accessibility tree.

Next steps <a href="#next-steps" class="w-headline-link">#</a>
--------------------------------------------------------------

Once you know a bit about semantics and how they aid screen reader navigation, you can't help but look at the pages you build differently. In the next section, we'll take a step back and consider how the entire outline of a page can be conveyed using effective [headings and landmarks](/headings-and-landmarks/).

<span class="w-mr--sm">Last updated: Nov 18, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/accessible/semantics-and-screen-readers/index.md)

<a href="/accessible" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
