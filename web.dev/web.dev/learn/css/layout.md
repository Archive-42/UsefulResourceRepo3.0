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

- <a href="#layout:-a-brief-history" class="toc__anchor">Layout: a brief history</a>
- <a href="#layout:-the-present-and-future" class="toc__anchor">Layout: the present and future</a>
- <a href="#understanding-the-display-property" class="toc__anchor">Understanding the display property</a>
- <a href="#flexbox-and-grid" class="toc__anchor">Flexbox and Grid</a>
  - <a href="#flexbox" class="toc__anchor">Flexbox</a>
  - <a href="#grid" class="toc__anchor">Grid</a>
- <a href="#flow-layout" class="toc__anchor">Flow layout</a>
  - <a href="#inline-block" class="toc__anchor">Inline block</a>
  - <a href="#floats" class="toc__anchor">Floats</a>
  - <a href="#multicolumn-layout" class="toc__anchor">Multicolumn layout</a>
  - <a href="#positioning" class="toc__anchor">Positioning</a>
- <a href="#wrap-up" class="toc__anchor">Wrap-up</a>

008

# Layout

An overview of the various layout methods you have to choose from when building a component or page layout.

On this page

- <a href="#layout:-a-brief-history" class="toc__anchor">Layout: a brief history</a>
- <a href="#layout:-the-present-and-future" class="toc__anchor">Layout: the present and future</a>
- <a href="#understanding-the-display-property" class="toc__anchor">Understanding the display property</a>
- <a href="#flexbox-and-grid" class="toc__anchor">Flexbox and Grid</a>
  - <a href="#flexbox" class="toc__anchor">Flexbox</a>
  - <a href="#grid" class="toc__anchor">Grid</a>
- <a href="#flow-layout" class="toc__anchor">Flow layout</a>
  - <a href="#inline-block" class="toc__anchor">Inline block</a>
  - <a href="#floats" class="toc__anchor">Floats</a>
  - <a href="#multicolumn-layout" class="toc__anchor">Multicolumn layout</a>
  - <a href="#positioning" class="toc__anchor">Positioning</a>
- <a href="#wrap-up" class="toc__anchor">Wrap-up</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 009: Layout

Imagine you're working as a developer, and a designer colleague hands you a design for a brand new website. The design has all sorts of interesting layouts and compositions: two-dimensional layouts that are considerate of viewport width and height, as well as layouts that need to be fluid and flexible. How do you decide the best way to style these with CSS?

CSS provides us with various ways to solve layout problems, on a horizontal axis, vertical axis, or even both. Choosing the right layout method for a context can be hard, and often you may need more than one layout method to solve your problem. To help with this, in the following modules, you'll learn about the unique features of each CSS layout mechanism to inform those decisions.

## Layout: a brief history <a href="#layout:-a-brief-history" class="w-headline-link">#</a>

In the early days of the web, designs more complex than a simple document were laid out with `<table>` elements. Separating HTML from visual styles was made easier when CSS was widely adopted by browsers in the late '90s. CSS opened the door to developers being able to completely change the look and feel of a website without ever touching HTML. This new capability inspired projects such as [The CSS Zen Garden](http://www.csszengarden.com), which was created to demonstrate the power of CSS to encourage more developers to learn it.

CSS has evolved as our needs for web design and browser technology have evolved. You can read how CSS layout and our approach to layout has evolved over time in [this article by Rachel Andrew](https://24ways.org/2019/a-history-of-css-through-15-years-of-24-ways/).

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/vDDoFFoPVgJEuEaqcP4H.svg" alt="A timeline showing how CSS has evolved over the years, starting in 1996 up to 2021" width="760" height="270" />

## Layout: the present and future <a href="#layout:-the-present-and-future" class="w-headline-link">#</a>

Modern CSS has exceptionally powerful layout tooling. We have dedicated systems for layout and we're going to have a high-level look at what we have at our disposal, before digging into more detail of Flexbox and Grid in the next modules.

## Understanding the `display` property <a href="#understanding-the-display-property" class="w-headline-link">#</a>

The `display` property does two things. The first thing it does is determine if the box it is applied to acts as inline or block.

    .my-element {
      display: inline
    }

Inline elements behave like words in a sentence. They sit next to each other in the inline direction. Elements such as `<span>` and `<strong>`, which are typically used to style pieces of text within containing elements like a `<p>` (paragraph), are inline by default. They also preserve surrounding whitespace.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format" alt="A diagram showing all the different sizes of a box and where each sizing section starts and ends" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/GezxDZXkJgkMevkKg39M.png?auto=format&amp;w=1600 1600w" width="800" height="559" />

You can't set an explicit width and height on inline elements. Any block level margin and padding will be ignored by the surrounding elements.

    .my-element {
      display: block;
    }

Block elements don't sit alongside each other. They create a new line for themselves. Unless changed by other CSS code, a block element will expand to the size of the inline dimension, therefore spanning the full width in a horizontal writing mode. The margin on all sides of a block element will be respected.

    .my-element {
     display: flex;
    }

The `display` property also determines how an element's children should behave. For example, setting the `display` property to `display: flex` makes the box a block-level box, and also converts its children to flex items. This enables the flex properties that control alignment, ordering and flow.

## Flexbox and Grid <a href="#flexbox-and-grid" class="w-headline-link">#</a>

There are two main layout mechanisms that create layout rules for multiple elements, _[flexbox](/learn/css/flexbox)_ and _[grid](/learn/css/grid)_. They share similarities, but are designed to solve different layout problems.

We will be going into much more detail for both of these in future modules, but here is a high-level overview of what both are and what they are useful for.

### Flexbox <a href="#flexbox" class="w-headline-link">#</a>

    .my-element {
       display: flex;
    }

Flexbox is a layout mechanism for one-dimensional layouts. Layout across a single axis, either horizontally or vertically. By default, flexbox will align the element's children next to each other, in the inline direction, and stretch them in the block direction, so they're all the same height.

Items will stay on the same axis and not wrap when they run out of space. Instead they will try to squash onto the same line as each other. This behaviour can be changed using the `align-items`, `justify-content` and `flex-wrap` properties.

Flexbox also converts the child elements to be **flex items**, which means you can write rules on how they behave inside a flex container. You can change alignment, order and justification on an individual item. You can also change how it shrinks or grows using the `flex` property.

    .my-element div {
         flex: 1 0 auto;
    }

The `flex` property is a shorthand for `flex-grow`, `flex-shrink` and `flex-basis`. You can expand the above example like this:

    .my-element div {
     flex-grow: 1;
     flex-shrink: 0;
     flex-basis: auto;
    }

Developers provide these low-level rules to hint a browser how the layout should behave when it is challenged by content and viewport dimensions. This makes it a very useful mechanism for responsive web design.

### Grid <a href="#grid" class="w-headline-link">#</a>

    .my-element {
     display: grid;
    }

Grid is similar in a lot of ways to **flexbox**, but it is designed to control multi-axis layouts instead of single-axis layouts (vertical or horizontal space).

Grid enables you to write layout rules on an element that has `display: grid`, and introduces a few new primitives for layout styling, such as the `repeat()` and `minmax()` functions. One useful grid unit is the `fr` unit—which is a fraction of remaining space—you can build traditional 12 column grids, with a gap between each item, with 3 CSS properties:

    .my-element {
      display: grid;
      grid-template-columns: repeat(12, 1fr);
      gap: 1rem;
    }

This example above shows a single axis layout. Where flexbox mostly treats items as a group, grid gives you precise control over their placement in two dimensions. We could define that the first item in this grid takes up 2 rows and 3 columns:

    .my-element :first-child {
      grid-row: 1/3;
      grid-column: 1/4;
    }

The `grid-row` and `grid-column` properties instruct the first element in the grid to span to the start of the fourth column, from the first column, then span to the third row, from the first row.

## Flow layout <a href="#flow-layout" class="w-headline-link">#</a>

If not using grid or flexbox, your elements display in normal flow. There are a number of layout methods that you can use to adjust the behavior and position of items when in normal flow.

### Inline block <a href="#inline-block" class="w-headline-link">#</a>

Remember how surrounding elements don't respect block margin and padding on an inline element? With `inline-block` you _can_ cause that to happen.

    p span {
      display: inline-block;
    }

Using `inline-block` gives you a box that has some of the characteristics of a block-level element, but still flows inline with the text.

    p span {
     margin-top: 0.5rem;
    }

### Floats <a href="#floats" class="w-headline-link">#</a>

If you have an image that sits within a paragraph of text, wouldn't it be handy for that text to wrap around that image like you might see in a newspaper? You can do this with floats.

    img {
      float: left;
      margin-right: 1em;
    }

The `float` property instructs an element to "float" to the direction specified. The image in this example is instructed to float left, which then allows sibling elements to "wrap" around it. You can instruct an element to float `left`, `right` or `inherit`.

**Warning**: When you use `float`, keep in mind that any elements following the floated element may have their layout adjusted. To prevent this, you can clear the float, either by using `clear: both` on an element that follows your floated element _or_ with `display: flow-root` on the parent of your floated elements.

Find out more in the article [The end of the clearfix hack](https://rachelandrew.co.uk/archives/2017/01/24/the-end-of-the-clearfix-hack/).

### Multicolumn layout <a href="#multicolumn-layout" class="w-headline-link">#</a>

If you have a really long list of elements, such as a list of all of the countries of the world, it can result in _a lot_ of scrolling and time wasted for a user. It can also create excess whitespace on the page. With CSS multicolumn, you can split this into multiple columns to help with both of these issues.

    <h1>All countries</h1>
    <ul class="countries">
      <li>Argentina</li>
      <li>Aland Islands</li>
      <li>Albania</li>
      <li>Algeria</li>
      <li>American Samoa</li>
      <li>Andorra</li>
      …
    </ul>

    .countries {
        column-count: 2;
      column-gap: 1em;
    }

This automatically splits that long list into two columns and adds a gap between the two columns.

    .countries {
       width: 100%;
      column-width: 260px;
      column-gap: 1em;
    }

Instead of setting the number of columns that the content is split into, you can also define a minimum desired width, using `column-width`. As more space is made available in the viewport, more columns will automatically be created and as space is reduced, columns will also reduce. This is very useful in responsive web design contexts.

### Positioning <a href="#positioning" class="w-headline-link">#</a>

Last on this overview of layout mechanisms is positioning. The `position` property changes how an element behaves in the normal flow of the document, and how it relates to other elements. The available options are `relative`, `absolute`, `fixed` and `sticky` with the default value being `static`.

    .my-element {
      position: relative;
      top: 10px;
    }

This element is nudged 10px down based on its current position in the document, as it is positioned relative to itself. Adding `position: relative` to an element also makes it the containing block of any child elements with `position: absolute`. This means that its child will now be repositioned to this particular element, instead of the topmost relative parent, when it has an absolute position applied to it.

    .my-element {
      position: relative;
      width: 100px;
      height: 100px;
    }

    .another-element {
       position: absolute;
       bottom: 0;
        right: 0;
     width: 50px;
      height: 50px;
    }

When you set `position` to `absolute`, it breaks the element out of the current document flow. This means two things:

1.  You can position this element wherever you like, using `top`, `right`, `bottom` and `left` in its nearest relative parent.
2.  All of the content surrounding an absolute element reflows to fill the remaining space left by that element.

An element with a `position` value of `fixed` behaves in a similar way to `absolute`, with its parent being the root `<html>` element. Fixed position elements stay anchored from the top left based on the `top`, `right`, `bottom` and `left` values that you set.

You can achieve the anchored, fixed aspects of `fixed` and the more predictable document flow-honoring aspects of `relative` by using `sticky`. With this value, as the viewport scrolls past the element, it stays anchored to the `top`, `right`, `bottom` and `left` values that you set.

## Wrap-up <a href="#wrap-up" class="w-headline-link">#</a>

There's a lot of choice and flexibility with CSS layout. To dive further into the power of CSS [Flexbox](/learn/css/flexbox) and [Grid](/learn/css/grid), continue into the next few modules.

Test your knowledge of layout

What 2 things does the `display` property do?

<span data-role="option">Determines `inline` or `block` or `none`.</span> <span data-role="option">Determines the grid layout frame.</span> <span data-role="option">Determines how the children should behave.</span> <span data-role="option">Determines if the box should scroll.</span>

The layout engine needs to know if this box be full width or not and does it need a new line.

The display property can set display to grid but it doesn't have anything to do with a layout frame.

Flexbox and grid have opinions and new features for their children.

That's the `overflow` property.

To flow multiple paragraphs into columns, which CSS property is best for this task?

<span data-role="option">`display: grid`</span> <span data-role="option">`column-count`</span> <span data-role="option">`display: flex`</span> <span data-role="option">`float`</span>

While grid could put multiple paragraphs into columns, those columns would be their own columns, not flowing together from one to the next.

Paragraphs will flow from the end of one column into the start of the next, like a magazine or newspaper will do.

While flex could put multiple paragraphs into columns, those columns would be their own columns, not flowing together from one to the next like is needed.

Try again!

What does it mean if a block is out of flow?

<span data-role="option">It's stuck on the side of the river.</span> <span data-role="option">It's been given a `top` or `left` position value.</span> <span data-role="option">It's no longer positioned based on its siblings positions.</span>

Context is CSS here, not geography.

Having these properties alone do not pull a box out of flow.

A box with `position: absolute` for example, is now positioned with x and y coordinates based on the containing block, and not its order with other sibling elements.

Flexbox and Grid wrap their children by default?

<span data-role="option">True</span> <span data-role="option">False</span>

It must be opted into with `flex-wrap: wrap` or `repeat(auto-fit, 30ch)`.

Flexbox and Grid have special wrapping features that need additional styles to apply.

<a href="/learn/css/sizing/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">007</span>

Sizing Units

<a href="/learn/css/flexbox/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">009</span>

Flexbox

Flexbox is a layout mechanism designed for laying out groups of items in one dimension. Learn how to use it in this module.

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
