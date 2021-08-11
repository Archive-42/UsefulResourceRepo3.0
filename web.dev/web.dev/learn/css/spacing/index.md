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

- <a href="#html-spacing" class="toc__anchor">HTML spacing</a>
- <a href="#margin" class="toc__anchor">Margin</a>
  - <a href="#negative-margin" class="toc__anchor">Negative margin</a>
  - <a href="#margin-collapse" class="toc__anchor">Margin collapse</a>
- <a href="#padding" class="toc__anchor">Padding</a>
- <a href="#positioning" class="toc__anchor">Positioning</a>
- <a href="#grid-and-flexbox" class="toc__anchor">Grid and flexbox</a>
- <a href="#creating-consistent-spacing" class="toc__anchor">Creating consistent spacing</a>

012

# Spacing

Find out how to select the best method of spacing elements, taking into consideration the layout method you are using and component that you need to build.

On this page

- <a href="#html-spacing" class="toc__anchor">HTML spacing</a>
- <a href="#margin" class="toc__anchor">Margin</a>
  - <a href="#negative-margin" class="toc__anchor">Negative margin</a>
  - <a href="#margin-collapse" class="toc__anchor">Margin collapse</a>
- <a href="#padding" class="toc__anchor">Padding</a>
- <a href="#positioning" class="toc__anchor">Positioning</a>
- <a href="#grid-and-flexbox" class="toc__anchor">Grid and flexbox</a>
- <a href="#creating-consistent-spacing" class="toc__anchor">Creating consistent spacing</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 013: Spacing

Say you've got a collection of three boxes, stacked on top of each other and you want space between them. How many ways can you think of to do that in CSS?

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/jGjBqBRk3uCvXT7Tdjre.svg" alt="Three stacked boxes with a downward arrow" width="800" height="498" />

The `margin` property _might_ give you what you need, but it also might add additional spacing that you don't want. For example, how do you target just the space _in between_ each of those elements? Something like `gap` might be more appropriate in this case. There are many ways to adjust spacing within a UI, each with its own strengths and caveats.

## HTML spacing <a href="#html-spacing" class="w-headline-link">#</a>

HTML itself provides some methods to space elements. The `<br>` and `<hr>` elements allow you to space elements in the block direction, which if you are in a latin-based language, is top-to-bottom.

If you use a `<br>` element, it will create a line-break, just like if you were to press your enter key in a word processor.

The `<hr>` creates a horizontal line with space either-side, known as `margin`.

Along with using HTML elements, HTML _entities_ can create space. An HTML entity is a reserved string of characters that are replaced with character entities by the browser. For example, if you were to type `&ampcopy;` in your HTML file, it would be converted into a © character. The `&ampnbsp;` entity is converted into a non-breaking space character, which provides an inline space. Be careful though, because the non-breaking aspect of this character stitches the two elements together, which can result in odd behaviour.

Use HTML elements to add space only when the element helps with the understanding of the document. For example, an `<hr>` doesn't just add space, it creates a logical separation of two chunks of content. If you just want a line with space around it, adding a border with CSS might be more appropriate.

## Margin <a href="#margin" class="w-headline-link">#</a>

If you want to add space to the outside of an element, you use the `margin` property. Margin is like adding a cushion around your element. The `margin` property is shorthand for `margin-top`, `margin-right`, `margin-bottom` and `margin-left`.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/ECuEOJEGnudhXW5JEFih.svg" alt="A diagram of the four main areas of the box model." width="800" height="547" />

The `margin` shorthand applies properties in a particular order: top, right, bottom and left. You can remember these with trouble: TRouBLe.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/F8jtvl15CsAcs8Oaid2l.svg" alt="The word &#39;Trouble&#39; running downwards with T, R, B and L extending to Top, Right, Bottom and Left. A box with arrows showing the directions too." width="800" height="320" />

The `margin` shorthand can also be used with one, two, or three values. Adding a fourth value lets you set each individual side. These are applied as follows:

- One value will be applied to all sides. (`margin: 20px`).
- Two values: the first value will be applied to the top and bottom sides, and the second value will be applied to the left and right sides. (`margin: 20px 40px`)
- Three values: the first value is `top`, the second value is `left` **and** `right`, and the third value is `bottom`. (`margin: 20px 40px 30px`).

Margin can be defined with a length, percentage or auto value, such as `1em` or `20%`. If you use a percentage, the value will be calculated based on the width of your element's containing block.

This means that if your element's containing block has a width of `250px` and your element has a `margin` value of `20%`: each side of your element will have a computed margin of `50px`.

You can also use a value of `auto` for margin. For block level elements with a restricted size, an `auto` margin will take up available space in the direction that it is applied to. A good example is this one, from the [flexbox module](/learn/css/flexbox), where the items push away from each other.

Another good example of `auto` margin is a horizontally centered wrapper which has a max width. This sort of wrapper is often used to create a consistent center column on a website.

    .wrapper {
      max-width: 400px;
     margin: 0 auto;
    }

Here, margin is removed from the top and bottom (block) sides, and `auto` shares the space between the left and right (inline) sides.

In the previous module on [logical properties](/learn/css/logical-properties), you learned that instead of specifying `margin-top`, `margin-right`, `margin-bottom` and `margin-left`, you can use `margin-block-start`, `margin-inline-end`, `margin-block-end` and `margin-inline-start`.

### Negative margin <a href="#negative-margin" class="w-headline-link">#</a>

Negative values can also be used for margin. Instead of adding space between adjacent sibling elements, it will **reduce space** between them. This can result in overlapping elements, if you declare a negative value that's more than the available space.

### Margin collapse <a href="#margin-collapse" class="w-headline-link">#</a>

Margin collapse is a tricky concept, but it's something you'll run into very commonly when building interfaces. Say you have two elements: a heading and a paragraph that both have vertical margin on them:

    <article>
      <h1>My heading with teal margin</h1>
      <p>A paragraph of text that has blue margin on it, following the heading with margin.</p>
    </article>

    h1 {
     margin-bottom: 2rem;
    }

    p {
        margin-top: 3rem;
    }

At first glance, you would be forgiven for thinking that the paragraph will be spaced `5em` from the heading, because `2rem` and `3rem` combined calculate to `5rem`. Because **vertical margin collapses**, though, the space is actually `3rem`.

Margin collapse works by selecting the largest value of two adjoining elements with vertical margin set on the adjoining sides. The bottom of the `h1` meets the top of the `p`, so the largest value of the `h1`'s bottom margin and the `p`'s top margin is selected. If the `h1` were to have `3.5rem` of bottom margin, the space between them both would then be `3.5rem` because that is larger than `3rem`. Only block margins collapse, not inline (horizontal) margins.

This behavior is rooted back to when the web was mostly just documents. Collapsing margins help to set consistent spacing between elements without accidentally creating huge gaps between elements that also have margin defined.

Margin collapse also helps with empty elements. If you have a paragraph that has a top and bottom margin of `20px`, it will only create `20px` of space: not `40px`. If _anything_ is added to the inside of this element though, including `padding`, its margin will no longer collapse in itself and will be treated as any box with content.

If two elements stacked on top of each other both have 20px of top margin and 30px of bottom margin, how much space will there be between them?

<span data-role="option">10px</span> <span data-role="option">20px</span> <span data-role="option">30px</span> <span data-role="option">40px</span>

Try again!

Not quite

CSS will take the larger of the margin spaces between elements yep!

Try again!

#### Preventing margin collapse <a href="#preventing-margin-collapse" class="w-headline-link">#</a>

If you make an element absolutely positioned, using `position: absolute`, the margin will no longer collapse. The margin also won't collapse if you use the `float` property, too.

If you have an element with no margin between two elements with block margin, the margin won't collapse either, because the two elements with block margin are no longer adjacent siblings: they are just siblings.

In the [layout lesson](/learn/css/layout), you learned that flexbox and grid containers are very similar to block containers, but handle their child elements very differently. This is the case with margin collapse, too.

If we take the original example from the lesson and apply flexbox with column direction, the margins are combined, instead of collapsed. This can provide predictability with layout work, which is what flexbox and grid containers are designed for.

Margin and margin collapse can be tricky to understand, but understanding how they work, in detail, is very useful, so [this detailed explainer](https://www.smashingmagazine.com/2019/07/margins-in-css) is strongly recommended.

## Padding <a href="#padding" class="w-headline-link">#</a>

Instead of creating space on the outside of your box, like `margin` does, the `padding` property creates space on the **inside** of your box instead: like insulation.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format" alt="A box with arrows pointing inwards to show that padding lives inside a box" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/kClqXks3zC6Dio1c6f6v.png?auto=format&amp;w=1600 1600w" width="800" height="336" />

Depending on which box model you are using—which was covered back in the [box model lesson](/learn/css/box-model/) —`padding` can also affect the overall dimensions of the element too.

The `padding` property is shorthand for `padding-top`, `padding-right`, `padding-bottom` and `padding-left`. Just like `margin`, `padding` has logical properties, too: `padding-block-start`, `padding-inline-end`, `padding-block-end` and `padding-inline-start`.

## Positioning <a href="#positioning" class="w-headline-link">#</a>

Also covered in the [layout](/learn/css/layout/) module, if you set a value for `position` that is anything other than `static`, you can space elements with the `top`, `right`, `bottom` and `left` properties. There are some differences with how these directional values behave:

- An element with `position: relative` will maintain its place in the document flow, even when you set these values. They will be relative to your element's position too.
- An element with `position: absolute` will base the directional values from the relative parent's position.
- An element with `position: fixed` will base the directional values on the viewport.
- An element with `position: sticky` will only apply the directional values when it is in its docked/stuck state.

In the [logical properties](/learn/css/logical-properties) module, you learn about the `inset-block` and `inset-inline` properties, which allow you to set directional values that honor writing mode.

Both properties are shorthands combining the `start` and `end` values and as such accept either one value to be set for `start` and `end` or two individual values.

## Grid and flexbox <a href="#grid-and-flexbox" class="w-headline-link">#</a>

Lastly, in both grid and flexbox you can use the `gap` property to create space _between_ child elements. The `gap` property is shorthand for `row-gap` and `column-gap`, it accepts one or two values, which can be lengths or percentages. You can also use keywords such as `unset`, `initial` and `inherit`. If you define only one value, the same `gap` will be applied to both the rows and columns, but if you define both values, the first value is `row-gap` and the second value is `column-gap`.

With both flexbox and grid, you can also create space using their distribution and alignment capabilities, which we cover in the [grid module](/learn/css/grid) and [flexbox module](/learn/css/flexbox).

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/JNXSRH4j77loSB099E04.svg" alt="A diagram representation of a grid with gaps" width="800" height="434" />

## Creating consistent spacing <a href="#creating-consistent-spacing" class="w-headline-link">#</a>

It is a really good idea to choose a strategy and stick with it to help you create a consistent user interface that has good flow and rhythm. A good way to achieve this is use consistent measures for your spacing.

For example, you could commit to using `20px` as a consistent measure for all gaps between elements—known as gutters—so all layouts look and feel consistent. You could also decide to use `1em` as the vertical spacing between flow content, which would achieve consistent spacing based on the element's `font-size`. Whatever you choose, you should save these values as variables (or CSS custom properties) to tokenize those values and make the consistency a bit easier.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/8eun6aGNHPTr4kyOrYkc.svg" alt="Consistent spacing between elements, using either 20px for a layout or 1em for flow content" width="800" height="602" />

    :root {
      --gutter: 20px;
      --spacing: 1em;
    }

    h1 {
      margin-left: var(--gutter);
      margin-top: var(--spacing);
    }

Using custom properties like this allows you to define them once, then use them throughout your CSS. When they are updated, either locally within an element or globally, the values will pass down through the cascade and the updated values will be reflected.

Test your knowledge of spacing

It's safe to use HTML for spacing when...

<span data-role="option">It's only one.</span> <span data-role="option">No one will notice.</span> <span data-role="option">It's just for space.</span> <span data-role="option">It helps with the understanding of the document.</span>

Try again!

Try again!

Try again!

You got it!

To create space **inside** a box, use...

<span data-role="option">Margin</span> <span data-role="option">HTML</span> <span data-role="option">Gap</span> <span data-role="option">Padding</span>

Margin is for pushing outside of a box.

These are for spacing and dividing content.

Gap is for spacing between boxes.

Padding is for creating space inside of a box.

To create space **outside** a box, use...

<span data-role="option">Margin</span> <span data-role="option">HTML</span> <span data-role="option">Gap</span> <span data-role="option">Padding</span>

Margin is for pushing outside of a box.

These are for spacing and dividing content.

Gap is for spacing between boxes.

Padding is for creating space inside of a box.

To create space **between** boxes, use...

<span data-role="option">Margin</span> <span data-role="option">HTML</span> <span data-role="option">Gap</span> <span data-role="option">Padding</span>

Margin is for pushing outside of a box.

These are for spacing and dividing content.

Gap is for spacing between boxes.

Padding is for creating space inside of a box.

<a href="/learn/css/logical-properties/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">011</span>

Logical Properties

<a href="/learn/css/pseudo-elements/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">013</span>

Pseudo-elements

A pseudo-element is like adding or targeting an extra element without having to add more HTML. They have a variety of roles and you can learn about them in this module.

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
