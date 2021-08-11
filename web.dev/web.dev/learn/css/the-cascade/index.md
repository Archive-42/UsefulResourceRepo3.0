<a href="#main" class="skip-link w-button">Skip to main</a>

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

- - [Learn](/learn/)
- [Learn CSS!](/learn/css/)

Share

On this page

- <a href="#position-and-order-of-appearance" class="toc__anchor">Position and order of appearance</a>
- <a href="#specificity" class="toc__anchor">Specificity</a>
  - <a href="#specificity-is-cumulative" class="toc__anchor">Specificity is cumulative</a>
- <a href="#origin" class="toc__anchor">Origin</a>
- <a href="#importance" class="toc__anchor">Importance</a>
- <a href="#using-devtools-to-find-out-why-some-css-is-not-applying" class="toc__anchor">Using DevTools to find out why some CSS is not applying</a>
- <a href="#resources" class="toc__anchor">Resources</a>

003

# The cascade

Sometimes two or more competing CSS rules could apply to an element. In this module find out how the browser chooses which to use, and how to control this selection.

On this page

- <a href="#position-and-order-of-appearance" class="toc__anchor">Position and order of appearance</a>
- <a href="#specificity" class="toc__anchor">Specificity</a>
  - <a href="#specificity-is-cumulative" class="toc__anchor">Specificity is cumulative</a>
- <a href="#origin" class="toc__anchor">Origin</a>
- <a href="#importance" class="toc__anchor">Importance</a>
- <a href="#using-devtools-to-find-out-why-some-css-is-not-applying" class="toc__anchor">Using DevTools to find out why some CSS is not applying</a>
- <a href="#resources" class="toc__anchor">Resources</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 004: The Cascade

CSS stands for Cascading Stylesheets. The cascade is the algorithm for solving conflicts where multiple CSS rules apply to an HTML element. It's the reason that the text of the button styled with the following CSS will be blue.

    button {
      color: red;
    }

    button {
      color: blue;
    }

Understanding the cascade algorithm helps you understand how the browser resolves conflicts like this. The cascade algorithm is split into 4 distinct stages.

1.  **Position and order of appearance**: the order of which your CSS rules appear
2.  **Specificity**: an algorithm which determines which CSS selector has the strongest match
3.  **Origin**: the order of when CSS appears and where it comes from, whether that is a browser style, CSS from a browser extension, or your authored CSS
4.  **Importance**: some CSS rules are weighted more heavily than others, especially with the `!important` rule type

## Position and order of appearance <a href="#position-and-order-of-appearance" class="w-headline-link">#</a>

The order in which your CSS rules appear and how they appear is taken into consideration by the cascade while it calculates conflict resolution.

The demo right at the start of this lesson is the most straightforward example of position. There are two rules that have selectors of identical specificity, so the last one to be declared won.

Styles can come from various sources on an HTML page, such as a `<link>` tag, an embedded `<style>` tag, and inline CSS as defined in an element's `style` attribute.

If you have a `<link>` that includes CSS at the top of your HTML page, then another `<link>` that includes CSS at the bottom of your page: the bottom `<link>` will have the most specificity. The same thing happens with embedded `<style>` elements, too. They get more specific, the further down the page they are.

The button has a blue background, as defined by CSS which is included by a `<link />` element. A CSS rule that sets it to be dark is in a second linked stylesheet and is applied because of its later position.

This ordering also applies to embedded `<style>` elements. If they are declared before a `<link>`, the linked stylesheet's CSS will have the most specificity.

The `<style>` element is declared in the `<head>`, while the `<link />` element is declared in the `<body>`. This means it gets more specificity than the `<style>` element

An inline `style` attribute with CSS declared in it will override all other CSS, regardless of its position, unless a declaration has `!important` defined.

Position also applies in the order of your CSS rule. In this example, the element will have a purple background because `background: purple` was declared last. Because the green background was declared before the purple background, it is now ignored by the browser.

    .my-element {
      background: green;
      background: purple;
    }

Being able to specify two values for the same property can be a simple way to create fallbacks for browsers that do not support a particular value. In this next example, `font-size` is declared twice. If `clamp()` is supported in the browser, then the previous `font-size` declaration will be discarded. If `clamp()` isn't supported by the browser, the initial declaration will be honored, and the font-size will be 1.5rem

    .my-element {
      font-size: 1.5rem;
      font-size: clamp(1.5rem, calc(1rem + 3vw), 2rem);
    }

This approach of declaring the same property twice works because browsers ignore values they don't understand. Unlike some other programming languages, CSS will not throw an error or break your program when it detects a line it cannot parse—the value it cannot parse is invalid and therefore ignored. The browser then continues to process the rest of the CSS without breaking stuff it already understands.

If you have the following HTML on your page:

    <!DOCTYPE html>
    <html lang="en">
      <head>
        <link rel="stylesheet" href="styles.css" />
      </head>
      <body>
        <button>I am a button</button>
        <style>
          button {
            background: pink;
          }
        </style>
      </body>
    </html>

Inside `styles.css`, is the following CSS rule:

    button {
      background: yellow;
    }

What color is the button's background?

<span data-role="option">pink</span> <span data-role="option">yellow</span>

The embedded `<style>` origin is further down the page than the `<link>` tag, so while the specificity of `button` is the same, the **position** of the style rule makes it win.

To the HTML document, the yellow button background may have been read first, but a newer rule of the same specificity was discovered later, making this rule not apply to the button.

## Specificity <a href="#specificity" class="w-headline-link">#</a>

Specificity is an algorithm which determines which CSS selector is the most specific, using a weighting or scoring system to make those calculations. By making a rule more specific, you can cause it to be applied even if some other CSS that matches the selector appears later in the CSS.

In [the next lesson](/learn/css/specificity) you can learn the details of how specificity is calculated, however keeping a few things in mind will help you avoid too many specificity issues.

CSS targeting a class on an element will make that rule more specific, and therefore seen as more important to be applied, than CSS targeting the element alone. This means that with the following CSS, the `h1` will be colored red even though both rules match and the rule for the `h1` selector comes later in the stylesheet.

    <h1 class="my-element">Heading</h1>

    .my-element {
      color: red;
    }

    h1 {
      color: blue;
    }

An `id` makes the CSS even more specific, so styles applied to an ID will override those applied many other ways. This is one reason why it is generally not a good idea to attach styles to an `id`. It can make it difficult to overwrite that style with something else.

### Specificity is cumulative <a href="#specificity-is-cumulative" class="w-headline-link">#</a>

As you can find out in the next lesson, each type of selector is awarded points which indicate how specific it is, the points for all of the selectors you have used to target an element are added together. This means that if you target an element with a selector list such as `a.my-class.another-class[href]:hover` you get something quite hard to overwrite with other CSS. For this reason, and to help make your CSS more reusable, it's a good idea to keep your selectors as simple as possible. Use specificity as a tool to get at elements when you need to, but always consider refactoring long, specific selector lists, if you can.

## Origin <a href="#origin" class="w-headline-link">#</a>

The CSS that you write isn't the only CSS applied to a page. The cascade takes into account the origin of the CSS. This origin includes the browser's internal stylesheet, styles added by browser extensions or the operating system, and your authored CSS. The **order of specificity of these origins**, from least specific, to most specific is as follows:

1.  **User agent base styles**. These are the styles that your browser applies to HTML elements by default.
2.  **Local user styles**. These can come from the operating system level, such as a base font size, or a preference of reduced motion. They can also come from browser extensions, such as a browser extension that allows a user to write their own custom CSS for a webpage.
3.  **Authored CSS**. The CSS that you author.
4.  **Authored `!important`**. Any `!important` that you add to your authored declarations.
5.  **Local user styles `!important`**. Any `!important` that come from the operating system level, or browser extension level CSS.
6.  **User agent `!important`**. Any `!important` that are defined in the default CSS, provided by the browser.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/zPdaZ6G11oYrgJ78EfF7.svg" width="800" height="347" /></figure>If you have an `!important` rule type in the CSS you have authored and the user has an `!important` rule type in their custom CSS, whose CSS wins?

**Test your knowledge of cascade origins**, consider the following style rules from various origins:

#### User-agent style

    h1 { margin-block-start: 0.83em; }

#### Bootstrap

    h1 { margin-block-start: 20px; }

#### Page Author styles

    h1 { margin-block-start: 2ch; }

    @media (max-width: 480px) {
      h1 { margin-block-start: 1ch; }
    }

#### User custom style

    h1 { margin-block-start: 2rem !important; }

Then, given the following HTML:

    <h1>Lorem ipsum</h1>

What is the final `margin-block-start` of the `h1`?

<span data-role="option">20px</span> <span data-role="option">0.83em</span> <span data-role="option">2rem</span> <span data-role="option">2ch</span> <span data-role="option">1ch</span>

Bootstrap is part of the authored origin, which loses to the important local user style.

The user agent style origin loses to the important local user style.

This `!important` user custom style has the most specific origin.

This author style is part of the authored origin, which loses to the important local user style.

This author style is part of the authored origin, which loses to the important local user style.

## Importance <a href="#importance" class="w-headline-link">#</a>

Not all CSS rules are calculated the same as each other, or given the same specificity as each other.

The **order of importance**, from least important, to most important is as follows:

1.  normal rule type, such as `font-size`, `background` or `color`
2.  `animation` rule type
3.  `!important` rule type (following the same order as origin)
4.  `transition` rule type

Active animation and transition rule types have higher importance than normal rules. In the case of transitions higher importance than `!important` rule types. This is because when an animation or transition becomes active, its expected behaviour is to change visual state.

## Using DevTools to find out why some CSS is not applying <a href="#using-devtools-to-find-out-why-some-css-is-not-applying" class="w-headline-link">#</a>

Browser DevTools will typically show all CSS that could match an element, with those which are not being used crossed out.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Z6aLsqcqjGAUsWzq7DZs.png?auto=format&amp;w=1600 1600w" width="800" height="446" /></figure>If the CSS you expected to apply doesn't appear at all, then it didn't match the element. In that case you need to look elsewhere, perhaps for a typo in a class or element name or some invalid CSS.

The Cascade can be used for...

<span data-role="option">Resolving conflicts when multiple styles apply to an element.</span> <span data-role="option">Ensuring there's only one style value for each property at draw time.</span> <span data-role="option">Scoring and weighting style rules.</span> <span data-role="option">Sorting and filtering style attributes.</span>

This is one of it's primary goals, conflict resolution.

The text can only be one color, and The Cascade is a way of determining which it should be.

Scoring and weighting are part of the sorting phase of The Cascade.

Sorting and filtering are phases of The Cascade to help understand aspects of conflict resolution.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [A highly interactive explainer of the cascade](https://wattenberger.com/blog/css-cascade)
- [MDN cascade reference](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Cascade_and_inheritance)

<a href="/learn/css/selectors/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">002</span>

Selectors

<a href="/learn/css/specificity/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">004</span>

Specificity

This module takes a deeper look at specificity, a key part of the cascade.

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
