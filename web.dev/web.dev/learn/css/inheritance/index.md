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

-   <a href="#inheritance-flow" class="toc__anchor">Inheritance flow</a>
-   <a href="#which-properties-are-inheritable" class="toc__anchor">Which properties are inheritable?</a>
-   <a href="#how-inheritance-works" class="toc__anchor">How inheritance works</a>
-   <a href="#how-to-explicitly-inherit-and-control-inheritance" class="toc__anchor">How to explicitly inherit and control inheritance</a>
    -   <a href="#the-inherit-keyword" class="toc__anchor">The inherit keyword</a>
    -   <a href="#the-initial-keyword" class="toc__anchor">The initial keyword</a>
    -   <a href="#the-unset-keyword" class="toc__anchor">The unset keyword</a>
-   <a href="#resources" class="toc__anchor">Resources</a>

005

Inheritance
===========

Some CSS properties inherit if you don't specify a value for them. Find out how this works, and how to use it to your advantage in this module.

On this page

-   <a href="#inheritance-flow" class="toc__anchor">Inheritance flow</a>
-   <a href="#which-properties-are-inheritable" class="toc__anchor">Which properties are inheritable?</a>
-   <a href="#how-inheritance-works" class="toc__anchor">How inheritance works</a>
-   <a href="#how-to-explicitly-inherit-and-control-inheritance" class="toc__anchor">How to explicitly inherit and control inheritance</a>
    -   <a href="#the-inherit-keyword" class="toc__anchor">The inherit keyword</a>
    -   <a href="#the-initial-keyword" class="toc__anchor">The initial keyword</a>
    -   <a href="#the-unset-keyword" class="toc__anchor">The unset keyword</a>
-   <a href="#resources" class="toc__anchor">Resources</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 005: Inheritance

Say you just wrote some CSS to make elements look like a button.

    <a href="http://example.com" class="my-button">I am a button link</a>

    .my-button {
      display: inline-block;
      padding: 1rem 2rem;
      text-decoration: none;
      background: pink;
      font: inherit;
      text-align: center;
    }

You then add a link element to an article of content, with a `class` value of `.my-button`. However there's an issue, the text is not the color that you expected it to be. How did this happen?

Some CSS properties inherit if you don't specify a value for them. In the case of this button, it **inherited** the `color` from this CSS:

    article a {
      color: maroon;
    }

In this lesson you'll learn why that happens and how inheritance is a powerful feature to help you write less CSS.

Inheritance flow <a href="#inheritance-flow" class="w-headline-link">#</a>
--------------------------------------------------------------------------

Let's take a look at how inheritance works, using this snippet of HTML:

    <html>
      <body>
        <article>
          <p>Lorem ipsum dolor sit amet.</p>
        </article>
      </body>
    </html>

The root element (`<html>`) won't inherit anything because it is the first element in the document. Add some CSS on the HTML element, and it starts to cascade down the document.

    html {
      color: lightslategray;
    }

The `color` property is inheritable by other elements. The `html` element has `color: lightslategray`, therefore all elements that can inherit color will now have a color of `lightslategray`.

    body {
      font-size: 1.2em;
    }

Because this demo sets the font size on the `body` element, the `html` element will still have the initial font size set by the browser (user agent stylesheet), but the `article` and `p` will inherit the font size declared by the `body`. This is because inheritance only cascades downwards.

    p {
      font-style: italic;
    }

Only the `<p>` will have italic text because it's the deepest nested element. Inheritance only flows downwards, not back up to parent elements.

Which properties are inheritable? <a href="#which-properties-are-inheritable" class="w-headline-link">#</a>
-----------------------------------------------------------------------------------------------------------

Not all CSS properties are inheritable, but there are a lot that are. For reference, here is the entire list of inheritable properties, taken from the W3 reference of all CSS properties:

-   [azimuth](https://developer.mozilla.org/en-US/docs/Web/CSS/azimuth)
-   [border-collapse](https://developer.mozilla.org/en-US/docs/Web/CSS/border-collapse)
-   [border-spacing](https://developer.mozilla.org/en-US/docs/Web/CSS/border-spacing)
-   [caption-side](https://developer.mozilla.org/en-US/docs/Web/CSS/caption-side)
-   [color](https://developer.mozilla.org/en-US/docs/Web/CSS/color)
-   [cursor](https://developer.mozilla.org/en-US/docs/Web/CSS/cursor)
-   [direction](https://developer.mozilla.org/en-US/docs/Web/CSS/direction)
-   [empty-cells](https://developer.mozilla.org/en-US/docs/Web/CSS/empty-cells)
-   [font-family](https://developer.mozilla.org/en-US/docs/Web/CSS/font-family)
-   [font-size](https://developer.mozilla.org/en-US/docs/Web/CSS/font-size)
-   [font-style](https://developer.mozilla.org/en-US/docs/Web/CSS/font-style)
-   [font-variant](https://developer.mozilla.org/en-US/docs/Web/CSS/font-variant)
-   [font-weight](https://developer.mozilla.org/en-US/docs/Web/CSS/font-weight)
-   [font](https://developer.mozilla.org/en-US/docs/Web/CSS/font)
-   [letter-spacing](https://developer.mozilla.org/en-US/docs/Web/CSS/letter-spacing)
-   [line-height](https://developer.mozilla.org/en-US/docs/Web/CSS/line-height)
-   [list-style-image](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-image)
-   [list-style-position](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-position)
-   [list-style-type](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style-type)
-   [list-style](https://developer.mozilla.org/en-US/docs/Web/CSS/list-style)
-   [orphans](https://developer.mozilla.org/en-US/docs/Web/CSS/orphans)
-   [quotes](https://developer.mozilla.org/en-US/docs/Web/CSS/quotes)
-   [text-align](https://developer.mozilla.org/en-US/docs/Web/CSS/text-align)
-   [text-indent](https://developer.mozilla.org/en-US/docs/Web/CSS/text-indent)
-   [text-transform](https://developer.mozilla.org/en-US/docs/Web/CSS/text-transform)
-   [visibility](https://developer.mozilla.org/en-US/docs/Web/CSS/visibility)
-   [white-space](https://developer.mozilla.org/en-US/docs/Web/CSS/white-space)
-   [widows](https://developer.mozilla.org/en-US/docs/Web/CSS/widows)
-   [word-spacing](https://developer.mozilla.org/en-US/docs/Web/CSS/word-spacing)

How inheritance works <a href="#how-inheritance-works" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

Every HTML element has every CSS property defined by default with an initial value. An initial value is a property that's not inherited and shows up as a default if the cascade fails to calculate a value for that element.

Properties that can be inherited cascade downwards, and child elements will get a computed value which represents its parent's value. This means that if a parent has `font-weight` set to `bold` all child elements will be bold, unless their `font-weight` is set to a different value, or the user agent stylesheet has a value for `font-weight` for that element.

How to explicitly inherit and control inheritance <a href="#how-to-explicitly-inherit-and-control-inheritance" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------

Inheritance can affect elements in unexpected ways so CSS has tools to help with that.

### The `inherit` keyword <a href="#the-inherit-keyword" class="w-headline-link">#</a>

You can make any property inherit its parent's computed value with the `inherit` keyword. A useful way to use this keyword is to create exceptions.

    strong {
      font-weight: 900;
    }

This CSS snippet sets all `<strong>` elements to have a `font-weight` of `900`, instead of the default `bold` value, which would be the equivalent of `font-weight: 700`.

    .my-component {
      font-weight: 500;
    }

The `.my-component` class sets `font-weight` to `500` instead. To make the `<strong>` elements inside `.my-component` also `font-weight: 500` add:

    .my-component strong {
      font-weight: inherit;
    }

Now, the `<strong>` elements inside `.my-component` will have a `font-weight` of `500`.

You could explicitly set this value, but if you use `inherit` and the CSS of `.my-component` changes in the future, you can guarantee that your `<strong>` will automatically stay up to date with it.

### The `initial` keyword <a href="#the-initial-keyword" class="w-headline-link">#</a>

Inheritance can cause problems with your elements and `initial` provides you with a powerful reset option.

You learned earlier that every property has a default value in CSS. The `initial` keyword sets a property back to that initial, default value.

    aside strong {
      font-weight: initial;
    }

This snippet will remove the bold weight from all `<strong>` elements inside an `<aside>` element and instead, make them normal weight, which is the initial value.

### The `unset` keyword <a href="#the-unset-keyword" class="w-headline-link">#</a>

The `unset` property behaves differently if a property is inheritable or not. If a property is inheritable, the `unset` keyword will be the same as `inherit`. If the property is not inheritable, the `unset` keyword is equal to `initial`.

Remembering which CSS properties are inheritable can be hard, `unset` can be helpful in that context. For example, `color` is inheritable, but `margin` isn't, so you can write this:

    /* Global color styles for paragraph in authored CSS */
    p {
      margin-top: 2em;
      color: goldenrod;
    }

    /* The p needs to be reset in asides, so you can use unset */
    aside p {
      margin: unset;
      color: unset;
    }

Now, the `margin` is removed and `color` reverts back to being the inherited computed value.

You can use the `unset` value with the `all` property, too. Going back to the above example, what happens if the global `p` styles get an additional few properties? Only the rule that was set for `margin` and `color` will apply.

    /* Global color styles for paragraph in authored CSS */
    p {
      margin-top: 2em;
        color: goldenrod;
       padding: 2em;
       border: 1px solid;
    }

    /* Not all properties are accounted for anymore */
    aside p {
     margin: unset;
      color: unset;
    }

If you change the `aside p` rule to `all: unset` instead, it doesn't matter what global styles are applied to `p` in the future, they will always be unset.

    aside p {
      margin: unset;
      color: unset;
       all: unset;
    }

Test your knowledge of inheritance

Which of the following properties are inheritable?

<span data-role="option">`animation`</span> <span data-role="option">`font-size`</span> <span data-role="option">`color`</span> <span data-role="option">`text-align`</span> <span data-role="option">`line-height`</span>

Animations do not pass down to children.

🎉

🎉

🎉

🎉

Which value behaves like `inherit` unless there is nothing to inherit and then behaves like `initial`?

<span data-role="option">`reset`</span> <span data-role="option">`unset`</span> <span data-role="option">`superset`</span>

not a valid value, try again!

🎉

not a valid value, try again!

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [MDN reference on computed values](https://developer.mozilla.org/en-US/docs/Web/CSS/computed_value)
-   [An article on how inheritance can be useful in modular front-ends](https://www.smashingmagazine.com/2016/11/css-inheritance-cascade-global-scope-new-old-worst-best-friends/)

<a href="/learn/css/specificity/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">004</span>

Specificity

<a href="/learn/css/color/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">006</span>

Color

There are several different ways to specify color in CSS. In this module we take a look at the most commonly used color values.

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
