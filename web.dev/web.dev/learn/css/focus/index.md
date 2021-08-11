<a href="#main" class="skip-link w-button">Skip to main</a>

<span class="w-tooltip w-tooltip--left">Open menu</span>

<span class="w-tooltip">Close</span>

<span class="font-mono drawer-course__link-counter">000</span> <span class="drawer-course__link-title gap-left-400">Learn CSS</span>

<span class="font-mono drawer-course__link-counter">001</span> <span class="drawer-course__link-title gap-left-400">Box Model</span>

<span class="font-mono drawer-course__link-counter">002</span> <span class="drawer-course__link-title gap-left-400">Selectors</span>

<span class="font-mono drawer-course__link-counter">003</span> <span class="drawer-course__link-title gap-left-400">The cascade</span>

<span class="font-mono drawer-course__link-counter">004</span> <span class="drawer-course__link-title gap-left-400">Specificity</span>

<span class="font-mono drawer-course__link-counter">005</span> <span class="drawer-course__link-title gap-left-400">Inheritance</span>

<span class="font-mono drawer-course__link-counter">006</span> <span class="drawer-course__link-title gap-left-400">Color</span>

<span class="font-mono drawer-course__link-counter">007</span> <span class="drawer-course__link-title gap-left-400">Sizing Units</span>

<span class="font-mono drawer-course__link-counter">008</span> <span class="drawer-course__link-title gap-left-400">Layout</span>

<span class="font-mono drawer-course__link-counter">009</span> <span class="drawer-course__link-title gap-left-400">Flexbox</span>

<span class="font-mono drawer-course__link-counter">010</span> <span class="drawer-course__link-title gap-left-400">Grid</span>

<span class="font-mono drawer-course__link-counter">011</span> <span class="drawer-course__link-title gap-left-400">Logical Properties</span>

<span class="font-mono drawer-course__link-counter">012</span> <span class="drawer-course__link-title gap-left-400">Spacing</span>

<span class="font-mono drawer-course__link-counter">013</span> <span class="drawer-course__link-title gap-left-400">Pseudo-elements</span>

<span class="font-mono drawer-course__link-counter">014</span> <span class="drawer-course__link-title gap-left-400">Pseudo-classes</span>

<span class="font-mono drawer-course__link-counter">015</span> <span class="drawer-course__link-title gap-left-400">Borders</span>

<span class="font-mono drawer-course__link-counter">016</span> <span class="drawer-course__link-title gap-left-400">Shadows</span>

<span class="font-mono drawer-course__link-counter">017</span> <span class="drawer-course__link-title gap-left-400">Focus</span>

<span class="font-mono drawer-course__link-counter">018</span> <span class="drawer-course__link-title gap-left-400">Z-index and stacking contexts</span>

<span class="font-mono drawer-course__link-counter">019</span> <span class="drawer-course__link-title gap-left-400">Functions</span>

<span class="font-mono drawer-course__link-counter">020</span> <span class="drawer-course__link-title gap-left-400">Gradients</span>

<span class="font-mono drawer-course__link-counter">021</span> <span class="drawer-course__link-title gap-left-400">Animations</span>

<span class="font-mono drawer-course__link-counter">022</span> <span class="drawer-course__link-title gap-left-400">Filters</span>

<span class="font-mono drawer-course__link-counter">023</span> <span class="drawer-course__link-title gap-left-400">Blend Modes</span>

<span class="font-mono drawer-course__link-counter">024</span> <span class="drawer-course__link-title gap-left-400">Conclusion and next steps</span>

-   -   [Learn](/learn/)
-   [Learn CSS!](/learn/css/)

Share

On this page

-   <a href="#why-is-focus-important" class="toc__anchor">Why is focus important?</a>
-   <a href="#how-elements-get-focus" class="toc__anchor">How elements get focus</a>
-   <a href="#styling-focus" class="toc__anchor">Styling focus</a>
-   <a href="#in-summary" class="toc__anchor">In summary</a>

017

Focus
=====

Understand the importance of focus in your web applications. You'll find out how to manage focus, and how to make sure the path through your page works for people using a mouse, and those using the keyboard to navigate.

On this page

-   <a href="#why-is-focus-important" class="toc__anchor">Why is focus important?</a>
-   <a href="#how-elements-get-focus" class="toc__anchor">How elements get focus</a>
-   <a href="#styling-focus" class="toc__anchor">Styling focus</a>
-   <a href="#in-summary" class="toc__anchor">In summary</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 018: Focus

On your webpage, you click a link that skips the user to the main content of the website. These are often referred to as skip links, or anchor links. When that link is activated by a keyboard, using the *tab* and *enter* keys, the main content container has a focus ring around it. Why is that?

This is because the `<main>` has a `tabindex="-1"` attribute value, which means it can be programmatically focused. When the `<main>` is targeted—because the `#main-content` in the browser URL bar matches the `id`—it receives programmatic focus. It's tempting to remove the focus styles in these situations, but handling focus appropriately and with care helps to create a good, accessible, user experience. It can also be a great place to add some interest to interactions.

Why is focus important? <a href="#why-is-focus-important" class="w-headline-link">#</a>
---------------------------------------------------------------------------------------

As a web developer, it's your job to make a website accessible and inclusive to all. Creating accessible focus states with CSS is a part of this responsibility.

Focus styles assist people who use a device such as a keyboard or a [switch control](https://www.24a11y.com/2018/i-used-a-switch-control-for-a-day/) to navigate and interact with a website. If an element receives focus and there is no visual indication, a user may lose track of what is in focus. This can create navigation issues and result in unwanted behaviour if, say, the wrong link is followed. You can [read more on focus and how to manage it in this guide](https://developers.google.com/web/fundamentals/accessibility/focus).

How elements get focus <a href="#how-elements-get-focus" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------

Certain elements are automatically focusable; these are elements that accept interaction and input, such as `<a>`, `<button>`, `<input>` and `<select>`. In short, all form elements, buttons and links. You can typically navigate a website's focusable elements using the *tab* key to move forward on the page, and *shift* + *tab* to move backward.

There is also a HTML attribute called `tabindex` which allows you to change the tabbing index—which is order in which elements are focused—every time someone presses their tab key, or focus is shifted with a hash change in the URL or by a JavaScript event. If `tabindex` on a HTML element is set to `0`, it can receive focus via the tab key and it will honour the global tab index, which is defined by the document source order.

If you set `tabindex` to `-1`, it can only receive focus programmatically, which means only when a JavaScript event happens or a hash change (matching the element's `id` in the URL) occurs. If you set `tabindex` to be anything higher than `0`, it will be removed from the global tab index, defined by document source order. Tabbing order will now be defined by the value of `tabindex`, so an element with `tabindex="1"` will receive focus before an element with `tabindex="2"`, for example.

**Warning**: Honoring document source order is really important, and focus order should only be changed if you **absolutely have to change it**. This applies both when setting `tabindex` **and** changing visual order with CSS layout, such as flexbox and grid. Anything that creates unpredictable focus on the web can create an inaccessible experience for the user.

Styling focus <a href="#styling-focus" class="w-headline-link">#</a>
--------------------------------------------------------------------

The default browser behavior when an element receives focus is to present a focus ring. This focus ring varies between both browser and operating systems.

This behavior can be changed with CSS, using the `:focus`, `:focus-within` and `:focus-visible` pseudo-classes that you learned about in the [pseudo-classes lesson](/learn/css/pseudo-classes). It is important to set a focus style which has **contrast** with the default style of an element. For example, a common approach is to utilize the `outline` property.

    a:focus {
      outline: 2px solid slateblue;
    }

The `outline` property could appear too close to the text of a link, but the `outline-offset` property can help with that, as it adds extra visual `padding` without affecting the geometric size that the element fills. A positive number value for `outline-offset` will push the outline outwards, a negative value will pull the outline inwards.

Currently in some browsers, if you have a `border-radius` set on your element and use `outline`, it won't match—the outline will have sharp corners. Due to this, it is tempting to use a `box-shadow` with a small blur radius because `box-shadow` clips to the shape, honouring `border-radius`, but **this style will not show in Windows High Contrast Mode**. This is because Windows High Contrast Mode doesn't apply shadows, and mostly ignores background images to favor the user's preferred settings.

In summary <a href="#in-summary" class="w-headline-link">#</a>
--------------------------------------------------------------

Creating a focus state that has contrast with an element's default state is incredibly important. The default browser styles do this already for you, but if you want to change this behaviour, remember the following:

-   Avoid using `outline: none` on an element that can receive keyboard focus
-   Avoid replacing `outline` styles with `box-shadow` as they don't show up in Windows High Contrast Mode
-   Only set a positive value for `tabindex` on an HTML element if you absolutely have to
-   Make sure the focus state is very clear vs the default state

Test your knowledge of focus

Which of the following are automatically focusable elements?

<span data-role="option">`<a>`</span> <span data-role="option">`<p>`</span> <span data-role="option">`<button>`</span> <span data-role="option">`<input>`</span> <span data-role="option">`<output>`</span> <span data-role="option">`<select>`</span>

🎉

Try again!

🎉

🎉

Try again!

🎉

Which of the following input devices can set focus?

<span data-role="option">Gamepad</span> <span data-role="option">Keyboard</span> <span data-role="option">Mouse</span> <span data-role="option">Assistive technology (screen reader, switch, etc)</span> <span data-role="option">A potato</span>

Gamepads often send keyboard events when their buttons are pressed.

Definitely causes focus when used to navigate the web.

A mouse requires vision and no longer puts focus on elements when used. All browsers used to put focus on things like buttons when clicked, but that has changed.

Definitely causes focus when used to navigate the web.

Sorry, while a potato can be used as a pointer on touch screens, it does not cause focus after interacting with on screen inputs.

<a href="/learn/css/shadows/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">016</span>

Shadows

<a href="/learn/css/z-index/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">018</span>

Z-index and stacking contexts

In this module find out how to control the order in which things layer on top of each other, by using z-index and the stacking context.

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
