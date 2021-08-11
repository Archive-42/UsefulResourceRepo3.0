<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#style-focus" class="w-toc__header--link">Style focus</a>
------------------------------------------------------------------

-   [Use :focus to always show a focus indicator](#use-:focus-to-always-show-a-focus-indicator)
-   [Use :focus-visible to selectively show a focus indicator](#use-:focus-visible-to-selectively-show-a-focus-indicator)
-   [Use :focus-within to style the parent of a focused element](#use-:focus-within-to-style-the-parent-of-a-focused-element)
-   [When to display a focus indicator](#when-to-display-a-focus-indicator)
-   [Avoid outline: none](#avoid-outline:-none)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Style focus
===========

Nov 18, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/accessible" class="w-post-signpost__link">Accessible to all</a>

[<img src="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rob Dodson" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/robdodson/)

<a href="/authors/robdodson/" class="w-author__name-link">Rob Dodson</a>

-   <a href="https://twitter.com/rob_dodson" class="w-author__link">Twitter</a>
-   <a href="https://github.com/robdodson" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@robdodson" class="w-author__link">Glitch</a>
-   <a href="https://robdodson.me" class="w-author__link">Blog</a>

The focus indicator (often signified by a "focus ring") identifies the currently focused element on your page. For users who are unable to use a mouse, this indicator is *extremely important* because it acts as a stand-in for their mouse-pointer.

If the browser's default focus indicator clashes with your design, you can use CSS to restyle it. Just remember to keep your keyboard users in mind!

Use `:focus` to always show a focus indicator <a href="#use-:focus-to-always-show-a-focus-indicator" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------

The [`:focus`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus) pseudo-class is applied any time an element is focused, regardless of the input device (mouse, keyboard, stylus, etc.) or method used to focus it. For example, the `<div>` below has a `tabindex` which makes it focusable. It also has a custom style for its `:focus` state:

    div[tabindex="0"]:focus {  
      outline: 4px dashed orange;  
    }  

Regardless of whether you use a mouse to click on it or a keyboard to tab to it, the `<div>` will *always* look the same.

Unfortunately browsers can be inconsistent with how they apply focus. Whether or not an element receives focus may depend on the browser and the operating system.

For example, the `<button>` below also has a custom style for its `:focus` state.

    button:focus {  
      outline: 4px dashed orange;  
    }  

If you click on the `<button>` with a mouse in Chrome on macOS you should see its custom focus style. However, you will not see the custom focus style if you click on the `<button>` in Firefox or Safari on macOS. This is because in Firefox and Safari the element does not receive focus when you click on it.

See the [MDN reference for `<button>` focus behavior](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/button#Clicking_and_focus) for a summary of which browsers and operating systems will apply focus to `<button>` elements.

Because the behavior of focus is inconsistent, it may require a bit of testing on different devices to ensure your focus styles are acceptable to your users.

Use `:focus-visible` to selectively show a focus indicator <a href="#use-:focus-visible-to-selectively-show-a-focus-indicator" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------------------------------------

The new [`:focus-visible`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-visible) pseudo-class is applied any time that an element receives focus and the browser determines via heuristics that displaying a focus indicator would be beneficial to the user. In particular, if the most recent user interaction was via the keyboard and the key press did not include a meta, `ALT` / `OPTION`, or `CONTROL` key, then `:focus-visible` will match.

`:focus-visible` is currently only supported in Chrome behind a flag, but there is a [lightweight polyfill](https://github.com/WICG/focus-visible) that can be added to your app to make it work.

The button in the example below will *selectively* show a focus indicator. If you use a mouse to click on it, the results are different than if you first use a keyboard to tab to it.

    button:focus-visible {  
      outline: 4px dashed orange;  
    }  

Use `:focus-within` to style the parent of a focused element <a href="#use-:focus-within-to-style-the-parent-of-a-focused-element" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------------------------------

The [`:focus-within`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-within) pseudo-class is applied to an element either when the element itself receives focus or when another element inside that element receives focus.

It can be used to highlight a region of the page to draw the user's attention to that area. For example, the form below receives focus both when the form itself is selected and also when any of its radio buttons are selected.

    form:focus-within {
      background: #ffecb3;
    }

When to display a focus indicator <a href="#when-to-display-a-focus-indicator" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

A good rule of thumb is to ask yourself, "If you clicked on this control while using a mobile device, would you expect it to display a keyboard?"

If the answer is "yes," then the control should probably *always* show a focus indicator, regardless of the input device used to focus it. A good example is the `<input type="text">` element. The user will need to send input to the element via the keyboard regardless of how the input element originally received focus, so it's helpful to always display a focus indicator.

If the answer is "no," then the control may choose to selectively show a focus indicator. A good example is the `<button>` element. If a user clicks on it with a mouse or touch screen, the action is complete, and a focus indicator may not be necessary. However, if the user is *navigating* with a keyboard, it's useful to show a focus indicator so the user can decide whether or not they want to click the control using the `ENTER` or `SPACE` keys.

Avoid `outline: none` <a href="#avoid-outline:-none" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

The way browsers decide when to draw a focus indicator is, frankly, very confusing. Changing the appearance of a `<button>` element with CSS or giving an element a `tabindex` will cause the browser's default focus ring behavior to kick-in.

A very common anti-pattern is to remove the focus indicator using CSS such as:

    /* Don't do this!!! */  
    :focus {  
      outline: none;  
    }  

A better way to work around this issue is to use a combination of `:focus` and the `:focus-visible` polyfill. The first block of code below demonstrates how the polyfill works, and the sample app beneath it provides an example of using the polyfill to change the focus indicator on a button.

    /*  
      This will hide the focus indicator if the element receives focus via the
      mouse, but it will still show up on keyboard focus.  
    */  
    .js-focus-visible :focus:not(.focus-visible) {  
      outline: none;  
    }

    /*  
      Optionally: Define a strong focus indicator for keyboard focus.  
      If you choose to skip this step, then the browser's default focus  
      indicator will be displayed instead.  
    */  
    .js-focus-visible .focus-visible {  
      …  
    }  

<span class="w-mr--sm">Last updated: Nov 18, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/accessible/style-focus/index.md)

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
