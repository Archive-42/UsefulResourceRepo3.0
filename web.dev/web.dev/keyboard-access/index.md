## <a href="#keyboard-access-fundamentals" class="w-toc__header--link">Keyboard access fundamentals</a>

- [Focus and the tab order](#focus-and-the-tab-order)
- [Arrange elements in the DOM to be in logical order](#arrange-elements-in-the-dom-to-be-in-logical-order)
- [Correctly set the visibility of offscreen content](#correctly-set-the-visibility-of-offscreen-content)
- [Next steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Keyboard access fundamentals

Nov 18, 2018

<span class="w-post-signpost__title">Appears in:</span> <a href="/accessible" class="w-post-signpost__link">Accessible to all</a>

[<img src="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rob Dodson" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/1Yk1TThRpbQr08rC9tmL.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/robdodson/)

<a href="/authors/robdodson/" class="w-author__name-link">Rob Dodson</a>

- <a href="https://twitter.com/rob_dodson" class="w-author__link">Twitter</a>
- <a href="https://github.com/robdodson" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@robdodson" class="w-author__link">Glitch</a>
- <a href="https://robdodson.me" class="w-author__link">Blog</a>

Many different users rely on the keyboard to navigate applications—from users with temporary and permanent motor impairments to users who use keyboard shortcuts to be more efficient and productive. Having a good keyboard navigation strategy for your application creates a better experience for everyone.

## Focus and the tab order <a href="#focus-and-the-tab-order" class="w-headline-link">#</a>

At a given moment, **focus** refers to what element in your application (such as a field, checkbox, button, or link) currently receives input from the keyboard. In addition to receiving keyboard events, the focused element also gets content that is pasted from the clipboard.

To move the focus on a page, use `TAB` to navigate "forward" and `SHIFT + TAB` to navigate "backward." The currently focused element is often indicated by a **focus ring**, and various browsers style their focus rings differently. The order in which focus proceeds forward and backward through interactive elements is called the **tab order**.

Interactive HTML elements like text fields, buttons, and select lists are **implicitly focusable**: they are automatically inserted into the tab order based on their position in the [DOM](https://developer.mozilla.org/en-US/docs/Web/API/Document_Object_Model). These interactive elements also have built-in keyboard event handling. Elements such as paragraphs and divs are not implicitly focusable because users typically do not need to interact with them.

Implementing a logical tab order is an important part of providing your users with a smooth keyboard navigation experience. There are two main ideas to keep in mind when assessing and adjusting your tab order:

1.  Arrange elements in the DOM to be in logical order
2.  Correctly set the visibility of offscreen content that should not receive focus

## Arrange elements in the DOM to be in logical order <a href="#arrange-elements-in-the-dom-to-be-in-logical-order" class="w-headline-link">#</a>

To check if your application's tab order is logical, try tabbing through your page. In general, focus should follow reading order, moving from left to right, from the top to the bottom of your page.

If the focus order seems wrong, you should rearrange the elements in the DOM to make the tab order more natural. **If you want something to appear visually earlier on the screen, move it earlier in the DOM**.

Try tabbing through the two sets of buttons below to experience a logical tab order versus an illogical tab order:

**Logical tab order**

**Illogical tab order**

The code for these two examples is compared below:

**Logical tab order**

    <button>Kiwi</button>
    <button>Peach</button>
    <button>Coconut</button>

**Illogical tab order**

    <button style="float: right">Kiwi</button>
    <button>Peach</button>
    <button>Coconut</button>

Be careful when changing the visual position of elements using CSS to avoid creating an illogical tab order. To fix the illogical tab order above, move the floating "Kiwi" button so it comes after the "Coconut" button in the DOM, and remove the inline style.

## Correctly set the visibility of offscreen content <a href="#correctly-set-the-visibility-of-offscreen-content" class="w-headline-link">#</a>

Sometimes offscreen interactive elements need to be in the DOM but should not be in your tab order. For example, if you have a responsive side-nav that opens when you click a button, the user should not be able to focus on the side-nav when it's closed.

To prevent a particular interactive element from receiving focus, you should give the element either of the following CSS properties:

- `display: none`
- `visibility: hidden`

To add the element back into the tab order, for example when the side-nav is opened, replace the above CSS properties respectively with:

- `display: block`
- `visibility: visible`

If you can't figure out where the focus on your page is as you're tabbing, open the console and type: `document.activeElement`. This property will return the element that currently has focus.

## Next steps <a href="#next-steps" class="w-headline-link">#</a>

For users who operate their computer almost entirely with the keyboard or another input device, a logical tab order is essential for making your application accessible and usable. As a good habit for checking your tab order, try **tabbing through your application before each publish**.

<span class="w-mr--sm">Last updated: Nov 18, 2018 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/accessible/keyboard-access/index.md)

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
