<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="header-default__logo-link gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="header-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="header-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="header-default__link gc-analytics-event">Blog</a> <a href="/about/" class="header-default__link gc-analytics-event">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="drawer-default__link gc-analytics-event">Learn</a> <a href="/measure/" class="drawer-default__link gc-analytics-event">Measure</a> <a href="/blog/" class="drawer-default__link gc-analytics-event">Blog</a> <a href="/about/" class="drawer-default__link gc-analytics-event">About</a>

<a href="#control-focus-with-tabindex" class="w-toc__header--link">Control focus with tabindex</a>
--------------------------------------------------------------------------------------------------

-   [Check if your controls are keyboard accessible](#check-if-your-controls-are-keyboard-accessible)
-   [Insert an element into the tab order](#insert-an-element-into-the-tab-order)
-   [Remove an element from the tab order](#remove-an-element-from-the-tab-order)
-   [Avoid tabindex &gt; 0](#avoid-tabindex-greater-0)
-   [Create accessible components with "roving tabindex"](#create-accessible-components-with-)
-   [Keyboard access recipes](#keyboard-access-recipes)

Share <a href="/newsletter/" class="w-actions__fab w-actions__fab--subscribe gc-analytics-event"><span>subscribe</span></a>

Control focus with tabindex
===========================

Nov 18, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/accessible" class="w-post-signpost__link">Accessible to all</a>

[<img src="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rob Dodson" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75 1x,     https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x,     https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x,     https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x,     https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/robdodson/)

<a href="/authors/robdodson/" class="w-author__name-link">Rob Dodson</a>

-   <a href="https://twitter.com/rob_dodson" class="w-author__link">Twitter</a>
-   <a href="https://github.com/robdodson" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@robdodson" class="w-author__link">Glitch</a>
-   <a href="https://robdodson.me" class="w-author__link">Blog</a>

Standard HTML elements such as `<button>` or `<input>` have keyboard accessibility built in for free. If you're building *custom* interactive components, however, use the `tabindex` attribute to ensure that they're keyboard accessible.

Whenever possible, use a built-in HTML element rather than building your own custom version. `<button>`, for example, is very easy to style and already has full keyboard support. This will save you from needing to manage `tabindex` or add semantics with ARIA.

Check if your controls are keyboard accessible <a href="#check-if-your-controls-are-keyboard-accessible" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------

A tool like Lighthouse is great at detecting certain accessibility issues, but some things can only be tested by a human.

Try pressing the `Tab` key to navigate through your site. Are you able to reach all the interactive controls on the page? If not, you may need to use [`tabindex`](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/tabindex) to improve the focusability of those controls.

**Warning**: If you don't see a focus indicator at all, it may be hidden by your CSS. Check for any styles that mention `:focus { outline: none; }`. You can learn how to fix this in our guide on [styling focus](/style-focus).

Insert an element into the tab order <a href="#insert-an-element-into-the-tab-order" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------

Insert an element into the natural tab order using `tabindex="0"`. For example:

    <div tabindex="0">Focus me with the TAB key</div>

To focus an element, press the `Tab` key or call the element's `focus()` method.

Remove an element from the tab order <a href="#remove-an-element-from-the-tab-order" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------

Remove an element using `tabindex="-1"`. For example:

    <button tabindex="-1">Can't reach me with the TAB key!</button>

This removes an element from the natural tab order, but the element can still be focused by calling its `focus()` method.

Note that applying `tabindex="-1"` to an element doesn't affect its children; if they're in the tab order naturally or because of a `tabindex` value, they'll remain in the tab order. To remove an element and all its children from the tab order, consider using [the WICG's `inert` polyfill](https://github.com/WICG/inert). The polyfill emulates the behavior of a proposed `inert` attribute, which prevents elements from being selected or read by assistive technologies.

**Caution**: The `inert` polyfill is experimental and may not work as expected in all cases. Test carefully before using in production.

Avoid `tabindex > 0` <a href="#avoid-tabindex-greater-0" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------

Any `tabindex` greater than 0 jumps the element to the front of the natural tab order. If there are multiple elements with a `tabindex` greater than 0, the tab order starts from the lowest value greater than zero and works its way up.

Using a `tabindex` greater than 0 is considered an **anti-pattern** because screen readers navigate the page in DOM order, not tab order. If you need an element to come sooner in the tab order, it should be moved to an earlier spot in the DOM.

Lighthouse makes it easy to identify elements with a `tabindex` &gt; 0. Run the Accessibility Audit (Lighthouse &gt; Options &gt; Accessibility) and look for the results of the "No element has a \[tabindex\] value greater than 0" audit.

Create accessible components with "roving `tabindex`" <a href="#create-accessible-components-with-%22roving-tabindex%22" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------------------------------

If you're building a complex component, you may need to add additional keyboard support beyond focus. Consider the built-in `select` element. It is focusable and you can use the arrow keys to expose additional functionality (the selectable options).

To implement similar functionality in your own components, use a technique known as "roving `tabindex`". Roving tabindex works by setting `tabindex` to -1 for all children except the currently-active one. The component then uses a keyboard event listener to determine which key the user has pressed.

When this happens, the component sets the previously focused child's `tabindex` to -1, sets the to-be-focused child's `tabindex` to 0, and calls the `focus()` method on it.

**Before**

    <div role="toolbar">
      <button tabindex="-1">Undo</div>
      <button tabindex="0">Redo</div>
      <button tabindex="-1">Cut</div>
    </div>

**After**

    <div role="toolbar">
      <button tabindex="-1">Undo</div>
      <button tabindex="-1">Redo</div>
      <button tabindex="0">Cut</div>
    </div>

Curious what those `role=""` attributes are for? They let you change the semantics of an element so it will be announced properly by a screen reader. You can learn more about them in our guide on [screen reader basics](/semantics-and-screen-readers).

Test your knowledge of tab order

This HTML renders a modal dialog:

    <div role="dialog" aria-labelledby="dialog-header">
      <button aria-label="Close"></button>
      <h2 id="dialog-header">
        Do you want to allow notifications from this website?
      </h2>
      <button>No</button>
      <button>Yes</button>
    </div>

What is the tab order for the elements in the sample?

1.  The **Close** button
2.  The **No** button
3.  The **Yes** button

Only the `<button>` elements are included in the tab order because they're the only standardized HTML form elements. To insert other elements into the tab order, you would add a `tabindex` attribute.

    <section tabindex="-1">
      <h2>Cat facts</h2>
      <ul>
        <li>A group of cats is called a <a href="https://m-w.com/dictionary/clowder">clowder</a>.</li>
        <li>Most cats are <a href="https://www.catfacts.org/catnip.html"> unaffected by catnip</a>.</li>
      </ul>
    </section>

Which elements from the sample are included in the tab order?

Only the `<a>` elements are included in the tab order.

The `<section>` element is not in the tab order because it has a negative `tabindex` value. (It can, however, be focused using the `focus()` method.) The `tabindex` value for the `<section>` element doesn't affect its children.

This HTML renders a popup menu followed by a search input:

    <div role="menu" tabindex="0">
      <a role="menuitem" href="/learn/" tabindex="-1">Learn</a>
      <a role="menuitem" href="/measure/" tabindex="-1">Measure</a>
      <a role="menuitem" href="/blog/" tabindex="-1">Blog</a>
      <a role="menuitem" href="/about/" tabindex="-1">About</a>
    </div>
    <input tabindex="1" type="text" role="search" aria-label="Search" placeholder="Search">

Which element in the sample comes first in the tab order?

The **Search** text input comes first in the tab order. Because it has a `tabindex` greater than zero, it jumps to the front of the tab order.

(This behavior is likely to cause confusion if the menu is positioned on the page before the search input. This is an example of why having a `tabindex` value greater than zero is considered an anti-pattern.)

This HTML renders a custom radio group, which should have a [roving `tabindex`](#create-accessible-components-with-%22roving-tabindex%22). (To keep things simpler, ignore the [`aria-*` attributes](/semantics-and-screen-readers) for now.)

    <div role="radiogroup" aria-labelledby="breed-header">
      <h3 id="breed-header">Your cat's breed</h3>
      <div role="radio" aria-checked="false" tabindex="0">Persian</div>
      <div role="radio" aria-checked="false" tabindex="-1">Bengal</div>
      <div role="radio" aria-checked="false" tabindex="-1">Maine Coon</div>
    </div>

When a `role="radio"` element is focused, what should happen when a user presses the `Right` arrow key?

-   Change the `tabindex` values for all radio elements in the group to -1.
-   If there's a radio element after the one that's focused, set its `tabindex` value to 0.
-   If there's no radio element after the one that's focused, set the `tabindex` value of the first radio element in the group to 0.
-   Focus the radio element that now has a `tabindex` of 0.

That's a lot—and it doesn't even include ARIA attributes! This is an example of why it's easier to use built-in elements with built-in keyboard behavior whenever you can.

Keyboard access recipes <a href="#keyboard-access-recipes" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

If you're unsure what level of keyboard support your custom components might need, you can refer to the [ARIA Authoring Practices 1.1](https://www.w3.org/TR/wai-aria-practices-1.1/). This handy guide lists common UI patterns and identifies which keys your components should support.

<span class="w-mr--sm"> Last updated: Nov 18, 2018 </span> [Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/accessible/control-focus-with-tabindex/index.md)

<a href="/accessible" class="w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single gc-analytics-event">Return to all articles</a>

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
