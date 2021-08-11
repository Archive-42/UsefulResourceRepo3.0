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

-   <a href="#content-and-sizing" class="toc__anchor">Content and sizing</a>
-   <a href="#the-areas-of-the-box-model" class="toc__anchor">The areas of the box model</a>
-   <a href="#a-useful-analogy" class="toc__anchor">A useful analogy</a>
-   <a href="#debugging-the-box-model" class="toc__anchor">Debugging the box model</a>
-   <a href="#controlling-the-box-model" class="toc__anchor">Controlling the box model</a>
-   <a href="#resources" class="toc__anchor">Resources</a>
    -   <a href="#user-agent-stylesheets" class="toc__anchor">User agent stylesheets</a>

001

Box Model
=========

Everything displayed by CSS is a box. Understanding how the CSS Box Model works is therefore a core foundation of CSS.

On this page

-   <a href="#content-and-sizing" class="toc__anchor">Content and sizing</a>
-   <a href="#the-areas-of-the-box-model" class="toc__anchor">The areas of the box model</a>
-   <a href="#a-useful-analogy" class="toc__anchor">A useful analogy</a>
-   <a href="#debugging-the-box-model" class="toc__anchor">Debugging the box model</a>
-   <a href="#controlling-the-box-model" class="toc__anchor">Controlling the box model</a>
-   <a href="#resources" class="toc__anchor">Resources</a>
    -   <a href="#user-agent-stylesheets" class="toc__anchor">User agent stylesheets</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 001: The Box Model

Say you have this bit of HTML:

    <p>I am a paragraph of text that has a few words in it.</p>

Then you write this CSS for it:

    p {
      width: 100px;
      height: 50px;
      padding: 20px;
      border: 1px solid;
    }

The content would break out of your element and it would be 142px wide, rather than 100px. Why is that? The box model is a core foundation of CSS and understanding how it works, how it is affected by other aspects of CSS and importantly, how you can control it will help you to write more predictable CSS.

A really important thing to remember when writing CSS, or working on the web as a whole, is that everything displayed by CSS is a box. Whether that's a box that uses `border-radius` to look like a circle, or even just some text: the key thing to remember is that it's all boxes.

Content and sizing <a href="#content-and-sizing" class="w-headline-link">#</a>
------------------------------------------------------------------------------

Boxes have different behavior based on their `display` value, their set dimensions, and the content that lives within them. This content could be even more boxes—generated by child elements—or plain text content. Either way, this content will affect the size of the box by default.

You can control this by using **extrinsic sizing**, or, you can continue to let the browser make decisions for you based on the content size, using **intrinsic sizing**.

Let's quickly look at the difference, using a demo to help us.

Notice that when the box is using extrinsic sizing, there's a limit of how much content you can add before it overflows out of the box's bounds. This makes the word, "awesome", overflow.

The demo has the words, "CSS is awesome" in a box with fixed dimensions and a thick border. The box has a width, so is extrinsically sized. It controls the sizing of its child content. The problem with this though, is that the word "awesome" is too large for the box, so it overflows outside of the parent box's **border box** (more on this later in the lesson). One way to prevent this overflow is to allow the box to be intrinsically sized by either unsetting the width, or in this case, setting the `width` to be `min-content`. The `min-content` keyword tells the box to only be as wide as the intrinsic minimum width of its content (the word "awesome"). This allows the box to fit around "CSS is awesome", perfectly.

Let's look at something more complex to see the impact of different sizing on real content:

Toggle intrinsic sizing on and off to see how you can gain more control with extrinsic sizing and let the content have more control with intrinsic sizing. To see the effect that intrinsic and extrinsic sizing has, add a few sentences of content to the card. When this element is using extrinsic sizing, there's a limit of how much content you can add before it overflows out of the element's bounds, but this isn't the case when intrinsic sizing is toggled on.

By default, this element has a set `width` and `height`—both `400px`. These dimensions give strict bounds to everything inside the element, which will be honored unless the content is too large for the box in which case visible overflow will happen. You can see this in action by changing the content of the caption, under the flower picture to something that exceeds the height of the box, which is a few lines of content.

**Key Term**: When content is too big for the box it is in, we call this overflow. You can manage how an element handles overflow content, using the `overflow` property.

When you switch to intrinsic sizing, you are letting the browser make decisions for you, based on the box's content size. It's much more difficult for there to be overflow with intrinsic sizing because our box will resize with its content, rather than try to size the content. It's important to remember that this is the default, flexible behavior of a browser. Though extrinsic sizing gives more control on the surface, intrinsic sizing provides the most flexibility, most of the time.

The areas of the box model <a href="#the-areas-of-the-box-model" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------

Boxes are made up of distinct box model areas that all do a specific job.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ECuEOJEGnudhXW5JEFih.svg" alt="The four main areas of the box model: content box, padding box, border box and margin box." width="800" height="547" /><figcaption>The four main areas of the box model: content box, padding box, border box and margin box.</figcaption></figure>You start with **content box**, which is the area that the content lives in. As you learned before: this content can control the size of its parent, so is usually the most variably sized area.

The **padding box** surrounds the content box and is the space created by the [`padding`](https://developer.mozilla.org/en-US/docs/Web/CSS/padding) property. Because padding is inside the box, the background of the box will be visible in the space that it creates. If our box has overflow rules set, such as `overflow: auto` or `overflow: scroll`, the scrollbars will occupy this space too.

The **border box** surrounds the padding box and its space is occupied by the `border` value. The border box is the bounds of your box and the **border edge** is the limit of what you can visually see. The [`border`](https://developer.mozilla.org/en-US/docs/Web/CSS/border) property is used to visually frame an element.

The final area, the **margin box**, is the space around your box, defined by the `margin` rule on your box. Properties such as [`outline`](https://developer.mozilla.org/en-US/docs/Web/CSS/outline) and [`box-shadow`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-shadow) occupy this space too because they are painted on top, so they don't affect the size of our box. You could have an `outline-width` of `200px` on our box and everything inside and including the border box would be exactly the same size.

A useful analogy <a href="#a-useful-analogy" class="w-headline-link">#</a>
--------------------------------------------------------------------------

The box model is complex to understand, so let's recap what you've learned with an analogy.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/FBaaJXdnuSkvOx1nB0CB.jpg?auto=format&amp;w=1600 1600w" width="800" height="562" /></figure>In this diagram, you have three photo frames, mounted to a wall, next to each other. The diagram has labels that associate elements of the frame with the box model.

To break this analogy down:

-   The content box is the artwork.
-   The padding box is the white matte, between the frame and the artwork.
-   The border box is the frame, providing a literal border for the artwork.
-   The margin box is the space between each frame.
-   The shadow occupies the same space as the margin box.

Debugging the box model <a href="#debugging-the-box-model" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

Browser DevTools provide a visualisation of a selected box's box model calculations, which can help you understand how the box model works and importantly, how it is affecting the website you're working on.

Go ahead and try this in your own browser:

1.  [Open DevTools](https://developers.google.com/web/tools/chrome-devtools/open)
2.  [Select an element](https://developers.google.com/web/tools/chrome-devtools/css/reference#select)
3.  Show the box model debugger

Controlling the box model <a href="#controlling-the-box-model" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

To understand how to control the box model, you first need to understand what happens in your browser.

Every browser applies a user agent stylesheet to HTML documents. The CSS used varies between each browser, but they provide sensible defaults to make content easier to read. They define how elements should look and behave if there's no CSS defined. It is in the user agent styles where a box's default `display` is set, too. For example, if we are in a normal flow, a `<div>` element's default `display` value is `block`, a `<li>` has a default `display` value of `list-item`, and a `<span>` has a default `display` value of `inline`.

An `inline` element has block margin, but other elements won't respect it. Use `inline-block`, and those elements will respect the block margin, while the element maintains most of the same behaviors it had as an `inline` element. A `block` item will, by default, fill the available **inline space**, whereas a `inline` and `inline-block` elements will only be as large as their content.

Alongside an understanding of how user agent styles affect each box, you also need to understand `box-sizing`, which tells our box how to calculate its box size. By default, all elements have the following user agent style: `box-sizing: content-box;`.

Having `content-box` as the value of `box-sizing` means that when you set dimensions, such as a `width` and `height`, they will be applied to the **content box**. If you then set `padding` and `border`, these values will be added to the content box's size.

    .my-box {
      width: 200px;
      border: 10px solid;
      padding: 20px;
    }

How wide do you think `.my-box` will be?

<span data-role="option">200px</span> <span data-role="option">260px</span>

Since the default value for box-sizing is content-box, padding and borders will be added to the width. `200px` would be correct if the box had `box-sizing: border-box`.

The default box sizing is content-box, which means padding and borders are added to the overall box.

The actual width of this box will be 260px. As the CSS uses the default `box-sizing: content-box`, the applied width is the width of the content, `padding` and `border` on both sides are added to that. So 200px for the content + 40px of padding + 20px of border makes a total visible width of 260px.

You *can* control this, though, by making the following modification to use the alternative box model, `border-box`:

    .my-box {
      box-sizing: border-box;
      width: 200px;
       border: 10px solid;
     padding: 20px;
    }

This alternative box model tells CSS to apply the `width` to the border box instead of the content box. This means that our `border` and `padding` get *pushed in*, and as a result, when you set `.my-box` to be `200px` wide: it actually renders at `200px` wide.

Check out how this works in the following interactive demo. Notice that when you toggle the `box-sizing` value it shows—via a blue background—which CSS is being applied *inside* our box.

    *,
    *::before,
    *::after {
      box-sizing: border-box;
    }

This CSS rule selects every element in the document and every `::before` and `::after` pseudo element and applies `box-sizing: border-box`. This means that every element will now have this alternative box model.

Because the alternative box model can be more predictable, developers often add this rule to resets and normalizers, [like this one](https://piccalil.li/blog/a-modern-css-reset).

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [Introduction to the box model](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)
-   [What are browser developer tools?](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_are_browser_developer_tools)

### User agent stylesheets <a href="#user-agent-stylesheets" class="w-headline-link">#</a>

-   [Chromium](https://chromium.googlesource.com/chromium/blink/+/master/Source/core/css/html.css)
-   [Firefox](https://searchfox.org/mozilla-central/source/layout/style/res/html.css)
-   [Webkit](https://trac.webkit.org/browser/trunk/Source/WebCore/css/html.css)

<a href="/learn/css/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">000</span>

Learn CSS

<a href="/learn/css/selectors/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">002</span>

Selectors

To apply CSS to an element you need to select it. CSS provides you with a number of different ways to do this, and you can explore them in this module.

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
