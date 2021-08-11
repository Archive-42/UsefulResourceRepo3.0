





<a href="#use-semantic-html-for-easy-keyboard-wins" class="w-toc__header--link">Use semantic HTML for easy keyboard wins</a>
----------------------------------------------------------------------------------------------------------------------------

-   [Keyboard support for free (and better mobile experiences)](#keyboard-support-for-free-(and-better-mobile-experiences))
-   [Use button instead of div](#use-button-instead-of-div)
-   [Links versus buttons](#links-versus-buttons)
-   [Styling](#styling)
-   [Next steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Use semantic HTML for easy keyboard wins
========================================

Nov 18, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/accessible" class="w-post-signpost__link">Accessible to all</a>

[<img src="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rob Dodson" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/robdodson/)

<a href="/authors/robdodson/" class="w-author__name-link">Rob Dodson</a>

-   <a href="https://twitter.com/rob_dodson" class="w-author__link">Twitter</a>
-   <a href="https://github.com/robdodson" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@robdodson" class="w-author__link">Glitch</a>
-   <a href="https://robdodson.me" class="w-author__link">Blog</a>

By using the correct semantic HTML elements you may be able to meet most or all of your keyboard access needs. That means less time fiddling with `tabindex`, and more happy users!

Keyboard support for free (and better mobile experiences) <a href="#keyboard-support-for-free-(and-better-mobile-experiences)" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------------------------------------

There are a number of built-in interactive elements with proper semantics and keyboard support. The ones most developers use are:

-   [`<a>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)
-   [`<button>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button)
-   [`<input>` (and its many types)](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/input#Form_%3Cinput%3E_types)
-   [`<select>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/select)
-   [`<textarea>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/textarea)

In addition, elements with the [`contenteditable`](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/contenteditable) attribute are sometimes used for freeform text entry.

It's easy to overlook the built-in keyboard support that these elements offer. Below are some example elements to explore. Instead of using your mouse, try using your keyboard to operate them. You can use `TAB` (or `SHIFT + TAB`) to move between controls, and you can use the arrow keys and keys like `ENTER` and `SPACE` to manipulate their values.

If you have a phone handy, you can see that many times these built-in elements have unique interactions on mobile. Attempting to reproduce these mobile interactions yourself is a lot of work! It's another good reason to stick to built-in elements whenever possible.

Use `button` instead of `div` <a href="#use-button-instead-of-div" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------

A common accessibility anti-pattern is to treat a non-interactive element, like a `div` or a `span`, as a button by adding a click handler to it.

But to be considered accessible, a button should:

-   Be focusable via the keyboard
-   Support being disabled
-   Support the `ENTER` or `SPACE` keys to perform an action
-   Be announced properly by a screen reader

A `div` button has none of these things. That means you'll need to write additional code to replicate what the `button` element gives you for free!

For example, `button` elements have a neat trick called ****synthetic click activation****. If you add a "click" handler to a `button`, it will run when the user presses `ENTER` or `SPACE`. A `div` button doesn't have this feature, so you'll need to write additional code to listen for the `keydown` event, check that the keycode is `ENTER` or `SPACE`, and then run your click handler. Ouch! That's a lot of extra work!

Compare the difference in this example. `TAB` to either control, and use `ENTER` and `SPACE` to attempt to click on them.

If you have `div` buttons in your existing site or application, consider swapping them out for `button` elements. `button` is easy to style and full of accessibility wins!

Links versus buttons <a href="#links-versus-buttons" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

Another common anti-pattern is to treat links as buttons by attaching JavaScript behavior to them.

    <a href="#" onclick="// perform some action">

Both buttons and links support some form of synthetic click activation. So which should you choose?

-   If clicking on the element will perform an *action* on the page, use `<button>`.
-   If clicking on the element will *navigate* the user to a new page then use `<a>`. This includes single page web apps that load new content and update the URL using the [History API](https://developer.mozilla.org/en-US/docs/Web/API/History).

The reason for this is that buttons and links are announced differently by screen readers. Using the correct element helps screen reader users know which outcome to expect.

Check whether code samples should use buttons or links

    See <a href="https://webaim.org/intro/" rel="noopener">WebAIM's Introduction to Web Accessibility</a> for more information.

Should this sample use a button or a link?

This sample should use a **link**. The sample is **correct**.

When selected, the element navigates the user to another page on a different domain, so a link is semantic.

    See the <a href="/semantics-and-screen-readers">Semantics and screen readers page</a> for more information.

Should this sample use a button or a link?

This sample should use a **link**. The sample is **correct**.

When selected, the element navigates the user to a different page on the same domain. No matter where a resource is located, use a link to semantically indicate navigation.

When selected, this element opens a modal dialog:

    <a href="#" onclick="openDialog()">

Should this sample use a button or a link?

This sample should use a **button**. The sample is **incorrect**.

When selected, the element runs a function that opens a modal dialog on the same page; since the element isn't navigating the user to a separate page, a button is semantic.

When selected, this element opens a navigation menu:

    <a href="#" onclick="openNavMenu()">

Should this sample use a button or a link?

This sample should use a **button**. The sample is **incorrect**.

When selected, the element runs a function that opens a navigation menu on the same page. Opening the menu is an action, so a button is semantic.

This code renders a horizontal navigation menu at the top of a website:

    <nav>
      <button>About</button>
      <button>Services</button>
      <button>Work</button>
      <button>Contact</button>
    </nav>

Should this sample use buttons or links?

This sample should use **links**. The sample is **incorrect**.

The elements in the `<nav>` menu navigate the user to other pages. Those pages may be separate resources in a static site, or they may be views in a [single-page application](https://developers.google.com/web/fundamentals/architecture/app-shell). Either way, since the user is navigating somewhere else, links are semantic.

Styling <a href="#styling" class="w-headline-link">#</a>
--------------------------------------------------------

Some built-in elements, in particular `<input>`, can be difficult to style. With a bit of clever CSS you may be able to work around some of these limitations. The (hilariously named) [WTFForms](http://wtfforms.com/) project contains an [example stylesheet](https://github.com/mdo/wtf-forms/blob/master/wtf-forms.css) that demonstrates a number of techniques for styling some of the tougher built-in elements.

Next steps <a href="#next-steps" class="w-headline-link">#</a>
--------------------------------------------------------------

Using built-in HTML elements can greatly improve the accessibility of your site, and significantly cut down on your workload. Try tabbing through your site and look for any controls which lack keyboard support. If possible, switch them out for standardized HTML alternatives.

Sometimes you may find an element that doesn't have a counterpart in HTML. That's okay! Read on to learn how to add keyboard support to custom interactive controls using `tabindex`.

<span class="w-mr--sm">Last updated: Nov 18, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/accessible/use-semantic-html/index.md)

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
