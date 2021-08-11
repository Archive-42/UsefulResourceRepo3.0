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

-   <a href="#what-can-you-do-with-a-flex-layout" class="toc__anchor">What can you do with a flex layout?</a>
-   <a href="#the-main-axis-and-the-cross-axis" class="toc__anchor">The main axis and the cross axis</a>
-   <a href="#creating-a-flex-container" class="toc__anchor">Creating a flex container</a>
-   <a href="#controlling-the-direction-of-items" class="toc__anchor">Controlling the direction of items</a>
    -   <a href="#reversing-the-flow-of-items-and-accessibility" class="toc__anchor">Reversing the flow of items and accessibility</a>
    -   <a href="#writing-modes-and-direction" class="toc__anchor">Writing modes and direction</a>
-   <a href="#wrapping-flex-items" class="toc__anchor">Wrapping flex items</a>
    -   <a href="#the-flex-flow-shorthand" class="toc__anchor">The flex-flow shorthand</a>
-   <a href="#controlling-space-inside-flex-items" class="toc__anchor">Controlling space inside flex items</a>
    -   <a href="#allowing-items-to-grow-at-different-rates" class="toc__anchor">Allowing items to grow at different rates</a>
-   <a href="#reordering-flex-items" class="toc__anchor">Reordering flex items</a>
-   <a href="#flexbox-alignment-overview" class="toc__anchor">Flexbox alignment overview</a>
-   <a href="#distributing-space-on-the-main-axis" class="toc__anchor">Distributing space on the main axis</a>
    -   <a href="#with-flex-direction:-column" class="toc__anchor">With flex-direction: column</a>
-   <a href="#distributing-space-between-flex-lines" class="toc__anchor">Distributing space between flex lines</a>
    -   <a href="#the-place-content-shorthand" class="toc__anchor">The place-content shorthand</a>
-   <a href="#aligning-items-on-the-cross-axis" class="toc__anchor">Aligning items on the cross-axis</a>
-   <a href="#why-is-there-no-justify-self-in-flexbox" class="toc__anchor">Why is there no justify-self in flexbox?</a>
-   <a href="#how-to-center-an-item-vertically-and-horizontally" class="toc__anchor">How to center an item vertically and horizontally</a>
-   <a href="#resources" class="toc__anchor">Resources</a>

009

Flexbox
=======

Flexbox is a layout mechanism designed for laying out groups of items in one dimension. Learn how to use it in this module.

On this page

-   <a href="#what-can-you-do-with-a-flex-layout" class="toc__anchor">What can you do with a flex layout?</a>
-   <a href="#the-main-axis-and-the-cross-axis" class="toc__anchor">The main axis and the cross axis</a>
-   <a href="#creating-a-flex-container" class="toc__anchor">Creating a flex container</a>
-   <a href="#controlling-the-direction-of-items" class="toc__anchor">Controlling the direction of items</a>
    -   <a href="#reversing-the-flow-of-items-and-accessibility" class="toc__anchor">Reversing the flow of items and accessibility</a>
    -   <a href="#writing-modes-and-direction" class="toc__anchor">Writing modes and direction</a>
-   <a href="#wrapping-flex-items" class="toc__anchor">Wrapping flex items</a>
    -   <a href="#the-flex-flow-shorthand" class="toc__anchor">The flex-flow shorthand</a>
-   <a href="#controlling-space-inside-flex-items" class="toc__anchor">Controlling space inside flex items</a>
    -   <a href="#allowing-items-to-grow-at-different-rates" class="toc__anchor">Allowing items to grow at different rates</a>
-   <a href="#reordering-flex-items" class="toc__anchor">Reordering flex items</a>
-   <a href="#flexbox-alignment-overview" class="toc__anchor">Flexbox alignment overview</a>
-   <a href="#distributing-space-on-the-main-axis" class="toc__anchor">Distributing space on the main axis</a>
    -   <a href="#with-flex-direction:-column" class="toc__anchor">With flex-direction: column</a>
-   <a href="#distributing-space-between-flex-lines" class="toc__anchor">Distributing space between flex lines</a>
    -   <a href="#the-place-content-shorthand" class="toc__anchor">The place-content shorthand</a>
-   <a href="#aligning-items-on-the-cross-axis" class="toc__anchor">Aligning items on the cross-axis</a>
-   <a href="#why-is-there-no-justify-self-in-flexbox" class="toc__anchor">Why is there no justify-self in flexbox?</a>
-   <a href="#how-to-center-an-item-vertically-and-horizontally" class="toc__anchor">How to center an item vertically and horizontally</a>
-   <a href="#resources" class="toc__anchor">Resources</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 010: Flexbox

A design pattern that can be tricky in responsive design is a sidebar that sits inline with some content. Where there is viewport space, this pattern works great, but where space is condensed, that rigid layout can become problematic.

The Flexible Box Layout Model (flexbox) is a layout model designed for one-dimensional content. It excels at taking a bunch of items which have different sizes, and returning the best layout for those items.

This is the ideal layout model for this sidebar pattern. Flexbox not only helps lay the sidebar and content out inline, but where there's not enough space remaining, the sidebar will break onto a new line. Instead of setting rigid dimensions for the browser to follow, with flexbox, you can instead provide flexible boundaries to hint how the content could display.

What can you do with a flex layout? <a href="#what-can-you-do-with-a-flex-layout" class="w-headline-link">#</a>
---------------------------------------------------------------------------------------------------------------

Flex layouts have the following features, which you will be able to explore in this guide.

-   They can display as a row, or a column.
-   They respect the writing mode of the document.
-   They are single line by default, but can be asked to wrap onto multiple lines.
-   Items in the layout can be visually reordered, away from their order in the DOM.
-   Space can be distributed inside the items, so they become bigger and smaller according to the space available in their parent.
-   Space can be distributed around the items and flex lines in a wrapped layout, using the Box Alignment properties.
-   The items themselves can be aligned on the cross axis.

The main axis and the cross axis <a href="#the-main-axis-and-the-cross-axis" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------

The key to understanding flexbox is to understand the concept of a main axis and a cross axis. The main axis is the one set by your `flex-direction` property. If that is `row` your main axis is along the row, if it is `column` your main axis is along the column.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/xKtf0cHRw0xQyiyYuuyz.svg" width="800" height="320" /></figure>Flex items move as a group on the main axis. Remember: we've got a bunch of things and we are trying to get the best layout for them as a group.

The cross axis runs in the other direction to the main axis, so if `flex-direction` is `row` the cross axis runs along the column.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/5wCsZcBmK5L33LS7nOmP.svg" width="800" height="320" /></figure>You can do two things on the cross axis. You can move the items individually or as a group so they align against each other and the flex container. Also, if you have wrapped flex lines, you can treat those lines as a group in order to control how space is assigned to those lines. You will see how this all works in practice throughout this guide, for now just keep in mind that the main axis follows your `flex-direction`.

Creating a flex container <a href="#creating-a-flex-container" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

Let's see how flexbox behaves by taking a group of different sized items and using flexbox to lay them out.

    <div class="container" id="container">
      <div>One</div>
      <div>Item two</div>
      <div>The item we will refer to as three</div>
    </div>

To use flexbox you need to declare that you want to use a flex formatting context and not regular block and inline layout. Do this by changing the value of the `display` property to `flex`.

    .container {
      display: flex;
    }

As you learned in the [layout guide](/learn/css/layout) this will give you a block-level box, with flex item children. The flex items immediately start exhibiting some flexbox behavior, using their **initial values**.

All CSS properties have initial values which control how they behave "out of the box" when you haven't applied any CSS to change that initial behavior. The children of our flex container become flex items as soon as their parent gets `display: flex`, so these initial values mean that we start seeing some flexbox behavior.

The initial values mean that:

-   Items display as a row.
-   They do not wrap.
-   They do not grow to fill the container.
-   They line up at the start of the container.

Controlling the direction of items <a href="#controlling-the-direction-of-items" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------

Even though you haven't added a `flex-direction` property yet, the items display as a row because the initial value of `flex-direction` is `row`. If you want a row then you don't need to add the property. To change the direction, add the property and one of the four values:

-   `row`: the items lay out as a row.
-   `row-reverse:` the items lay out as a row from the end of the flex container.
-   `column`: the items lay out as a column.
-   `column-reverse` : the items lay out as a column from the end of the flex container.

You can try out all of the values using our group of items in the demo below.

### Reversing the flow of items and accessibility <a href="#reversing-the-flow-of-items-and-accessibility" class="w-headline-link">#</a>

You should be cautious when using any properties that reorder the visual display away from how things are ordered in the HTML document, as it can negatively impact accessibility. The `row-reverse` and `column-reverse` values are a good example of this. The reordering only happens for the visual order, not the logical order. This is important to understand as the logical order is the order that a screen reader will read out the content, and anyone navigating using the keyboard will follow.

You can see in the following video how in a reversed column layout, tabbing between links becomes disconnected as the keyboard navigation follows the DOM not the visual display.

Anything which can change the order of items in flexbox or grid can cause this problem. Therefore any reordering should include thorough testing to check that it will not make your site hard to use for some people.

For more information see:

-   [Content reordering](https://web.dev/content-reordering/)
-   [Flexbox and the keyboard navigation disconnect](https://tink.uk/flexbox-the-keyboard-navigation-disconnect/)

### Writing modes and direction <a href="#writing-modes-and-direction" class="w-headline-link">#</a>

Flex items lay out as a row by default. A row runs in the direction that sentences flow in your writing mode and script direction. This means that if you are working in Arabic, which has a right-to-left (rtl) script direction, the items will line up on the right. Tab order would also begin on the right as this is the way sentences are read in Arabic.

If you are working with a vertical writing mode, like some Japanese typefaces, then a row will run vertically, from top to bottom. Try changing the `flex-direction` in this demo which is using a vertical writing mode.

Therefore the way flex items behave by default is linked to the writing mode of the document. Most tutorials are written using English, or another horizontal, left to right writing mode. This would make it easy to assume that flex items line up **on the left**, and run **horizontally**.

With the main and cross axis plus the writing mode to consider, the fact that we talk about **start** and **end** rather than top, bottom, left, and right in flexbox might be easier to understand. Each axis has a start and an end. The start of the main axis is referred to as **main-start**. So our flex items initially line up from main-start. The end of that axis is **main-end**. The start of the cross axis is **cross-start** and the end **cross-end**.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/uSH4TxRv8KNQDTK7Vn8h.svg" alt="A labelled diagram of the above terms" width="800" height="382" />

Wrapping flex items <a href="#wrapping-flex-items" class="w-headline-link">#</a>
--------------------------------------------------------------------------------

The initial value of the `flex-wrap` property is `nowrap`. This means that if there is not enough space in the container the items will overflow.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format" alt="Once they hit min-content size flex items will start to overflow their container" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/VTUdLS9PeBziBvbOSc4q.jpg?auto=format&amp;w=1600 1600w" width="800" height="282" /><figcaption>Once they hit min-content size flex items will start to overflow their container</figcaption></figure>Items displaying using the initial values will shrink as small as they can, down to the `min-content` size before overflow happens.

To cause the items to wrap add `flex-wrap: wrap` to the flex container.

    .container {
      display: flex;
      flex-wrap: wrap;
    }

When a flex container wraps it creates multiple **flex lines**. In terms of space distribution, each line acts like a new flex container. Therefore if you are wrapping rows, it is not possible to get something in row 2 to line up with something above it in row 1. This is what is meant by flexbox being one-dimensional. You can control alignment in one axis, a row or a column, not both together as we can do in grid.

### The flex-flow shorthand <a href="#the-flex-flow-shorthand" class="w-headline-link">#</a>

You can set the `flex-direction` and `flex-wrap` properties using the shorthand `flex-flow`. For example, to set `flex-direction` to `column` and allow items to wrap:

    .container {
      display: flex;
      flex-flow: column wrap;
    }

Controlling space inside flex items <a href="#controlling-space-inside-flex-items" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------

Assuming our container has more space than is needed to display the items, the items line up at the start and do not grow to fill the space. They stop growing at their max-content size. This is because the initial value of the `flex-` properties is:

-   `flex-grow: 0`: items do not grow.
-   `flex-shrink: 1`: items can shrink smaller than their `flex-basis`.
-   `flex-basis: auto`: items have a base size of `auto`.

This can be represented by a keyword value of `flex: initial`. The `flex` shorthand property, or the longhands of `flex-grow`, `flex-shrink` and `flex-basis` are applied to the children of the flex container.

To cause the items to grow, while allowing large items to have more space than small ones use `flex:auto`. You can try this using the demo above. This sets the properties to:

-   `flex-grow: 1`: items can grow larger than their `flex-basis`.
-   `flex-shrink: 1`: items can shrink smaller than their `flex-basis`.
-   `flex-basis: auto`: items have a base size of `auto`.

Using `flex: auto` will mean that items end up different sizes, as the space that is shared between the items is shared out *after* each item is laid out as max-content size. So a large item will gain more space. To force all of the items to be a consistent size and ignore the size of the content change `flex:auto` to `flex: 1` in the demo.

This unpacks to:

-   `flex-grow: 1`: items can grow larger than their `flex-basis`.
-   `flex-shrink: 1`: items can shrink smaller than their `flex-basis`.
-   `flex-basis: 0`: items have a base size of `0`.

Using `flex: 1` says that all items have zero size, therefore all of the space in the flex container is available to be distributed. As all items have a `flex-grow` factor of `1` they all grow equally and the space is shared equally.

There is also a value of `flex: none`, which will give you inflexible flex items that do not grow or shrink. This might be useful if you are purely using flexbox to access the alignment properties but don't want any flexible behavior.

### Allowing items to grow at different rates <a href="#allowing-items-to-grow-at-different-rates" class="w-headline-link">#</a>

You don't have to give all items a `flex-grow` factor of `1`. You could give your flex items different `flex-grow` factors. In the demo below the first item has `flex: 1`, the second `flex: 2` and third `flex: 3`. As these items grow from `0` the available space in the flex container is shared into six. One part is given to the first item, two parts to the second, three parts to the third.

You can do the same thing from a `flex-basis` of `auto`, though you will need to specify the three values. The first value being `flex-grow`, the second `flex-shrink`, and the third `flex-basis`.

    .item1 {
      flex: 1 1 auto;
    }

    .item2 {
      flex: 2 1 auto;
    }

This is a less common use case as the reason to use a `flex-basis` of `auto` is to allow the browser to figure out space distribution. If you wanted to cause an item to grow a little more than the algorithm decides however it might be useful.

Reordering flex items <a href="#reordering-flex-items" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

Items in your flex container can be reordered using the `order` property. This property allows the ordering of items in **ordinal groups**. Items are laid out in the direction dictated by `flex-direction`, lowest values first. If more than one item has the same value it will be displayed with the other items with that value.

The example below demonstrates this ordering.

**Warning**: Using `order` has the same problems as the `row-reverse` and `column-reverse` values of `flex-direction`. It would be very easy to create a disconnected experience for some users. Do not use `order` because you are fixing things being out of order in the document. If the items logically should be in a different order, change your HTML!

Test your knowledge of flexbox

The default `flex-direction` is

<span data-role="option">`row`</span> <span data-role="option">`column`</span>

By default, flexbox will fit items into a row, lining them up at the start. With wrapping turned on, it will continue creating rows for children to flow within.

Setting flex-direction to column is a great way to stack elements, but it is not the default value.

By default, a flex container wraps children.

<span data-role="option">true</span> <span data-role="option">false</span>

Wrapping must be enabled.

Use `flex-wrap: wrap` with `display: flex` to wrap children

A flex child item appears squished, which flex property helps mitigate this?

<span data-role="option">`flex-grow`</span> <span data-role="option">`flex-shrink`</span> <span data-role="option">`flex-basis`</span>

This property describes if elements can grow beyond a basis size, not how it should behave under a basis.

Yes, this property describes how to handle sizing if the width is going below the basis.

This provides the starting point of sizing, but not how to handle sizing scenarios where width goes below basis, like in a squished scenario.

Flexbox alignment overview <a href="#flexbox-alignment-overview" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------

Flexbox brought with it a set of properties for aligning items and distributing space between items. These properties were so useful they have since been moved into their own specification, you'll encounter them in Grid Layout too. Here you can find out how they work when you are using flexbox.

The set of properties can be placed into two groups. Properties for space distribution, and properties for alignment. The properties which distribute space are:

-   `justify-content`: space distribution on the main axis.
-   `align-content`: space distribution on the cross axis.
-   `place-content`: a shorthand for setting both of the above properties.

The properties used for alignment in flexbox:

-   `align-self`: aligns a single item on the cross axis
-   `align-items`: aligns all of the items as a group on the cross axis

If you are working on the main axis then the properties begin with `justify-`. On the cross axis they begin with `align-`.

Distributing space on the main axis <a href="#distributing-space-on-the-main-axis" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------

With the HTML used earlier, the flex items laid out as a row, there is space on the main axis. The items are not big enough to completely fill the flex container. The items line up at the start of the flex container because the initial value of `justify-content` is `flex-start`. The items line up at the start and any extra space is at the end.

Add the `justify-content` property to the flex container, give it a value of `flex-end`, and the items line up at the end of the container and the spare space is placed at the start.

    .container {
      display: flex;
      justify-content: flex-end;
    }

You can also distribute the space between the items with `justify-content: space-between`.

Try some of the values in the demo, and [see MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content) for the full set of possible values.

For the `justify-content` property to do anything you have to have spare space in your container on the main axis. If your items fill the axis then there is no space to share out so the property won't do anything.

### With `flex-direction: column` <a href="#with-flex-direction:-column" class="w-headline-link">#</a>

If you have changed your `flex-direction` to `column` then `justify-content` will work on the column. To have spare space in your container when working as a column you need to give your container a `height` or `block-size`. Otherwise you won't have spare space to distribute.

Try the different values, this time with a flexbox column layout.

Distributing space between flex lines <a href="#distributing-space-between-flex-lines" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------

With a wrapped flex container you might have space to distribute on the cross axis. In this case you can use the `align-content` property with the same values as `justify-content`. Unlike `justify-content` which aligns items to `flex-start` by default, the initial value of `align-content` is `stretch`. Add the property `align-content` to the flex container to change that default behavior.

    .container {
      align-content: center;
    }

Try this out in the demo. The example has wrapped lines of flex items, and the container has a `block-size` in order that we have some spare space.

### The `place-content` shorthand <a href="#the-place-content-shorthand" class="w-headline-link">#</a>

To set both `justify-content` and `align-content` you can use `place-content` with one or two values. A single value will be used for both axes, if you specify both the first is used for `align-content` and the second for `justify-content`.

    .container {
      place-content: space-between;
      /* sets both to space-between */
    }

    .container {
      place-content: center flex-end;
      /* wrapped lines on the cross axis are centered,
      on the main axis items are aligned to the end of the flex container */
    }

Aligning items on the cross-axis <a href="#aligning-items-on-the-cross-axis" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------

On the cross axis you can also align your items within the flex line using `align-items` and `align-self`. The space available for this alignment will depend on the height of the flex container, or flex line in the case of a wrapped set of items.

The initial value of `align-self` is `stretch`, which is why flex items in a row stretch to the height of the tallest item by default. To change this, add the `align-self` property to any of your flex items.

    .container {
      display: flex;
    }

    .item1 {
      align-self: flex-start;
    }

Use any of the following values to align the item:

-   `flex-start`
-   `flex-end`
-   `center`
-   `stretch`
-   `baseline`

See [the full list of values on MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/align-self).

The next demo has a single line of flex items with `flex-direction: row`. The last item defines the height of the flex container. The first item has the `align-self` property with a value of `flex-start`. Try changing the value on that property to see how it moves within it's space on the cross axis.

The `align-self` property is applied to individual items. The `align-items` property can be applied to the flex container to set all of the individual `align-self` properties as a group.

    .container {
      display: flex;
      align-items: flex-start;
    }

In this next demo try changing the value of `align-items` to align all of the items on the cross axis as a group.

Why is there no justify-self in flexbox? <a href="#why-is-there-no-justify-self-in-flexbox" class="w-headline-link">#</a>
-------------------------------------------------------------------------------------------------------------------------

Flex items act as a group on the main axis. So there is no concept of splitting an individual item out of that group.

In grid layout the `justify-self` and `justify-items` properties work on the inline axis to do alignment of items on that axis within their grid area. Due to the way that flex layouts treat items as a group, these properties are not implemented in a flex context.

It is worth knowing that flexbox does work very nicely with auto margins. If you come across a need to split off one item from a group, or separate the group into two groups you can apply a margin to do this. In the example below the last item has a left margin of `auto`. The auto margin absorbs all space in the direction it is applied. This means that it pushes the item over to the right, thus splitting the groups.

How to center an item vertically and horizontally <a href="#how-to-center-an-item-vertically-and-horizontally" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------

The alignment properties can be used to center an item inside another box. The `justify-content` property aligns the item on the main axis, which is row. The `align-items` property on the cross axis.

    .container {
      width: 400px;
      height: 300px;
      display: flex;
      justify-content: center;
      align-items: center;
    }

In the future we may be able to do this alignment without needing to make the parent a flex container. The alignment properties are specified for block and inline layout. At present no browser has implemented these. However, switching into a flex formatting context gives you access to the properties. If you need to align something it's a great way to do it.

Test your knowledge of flexbox

    .container {
      display: flex;
      direction: ltr;
    }

To vertically align with flexbox, use

<span data-role="option">align keywords</span> <span data-role="option">justify keywords</span>

Nice

Sorry

    .container {
      display: flex;
      direction: ltr;
    }

To horizonally align with flexbox, use

<span data-role="option">align keywords</span> <span data-role="option">justify keywords</span>

Sorry

Nice

    .container {
      display: flex;
      direction: ltr;
    }

By default, flex items are aligned to `stretch`. If you want content size used for child items, which of the following styles would you use?

<span data-role="option">`justify-content: flex-start`</span> <span data-role="option">`align-content: start`</span> <span data-role="option">`height: auto`</span> <span data-role="option">`align-items: flex-start`</span>

The justify property is for horizontal alignment, not vertical.

`content` aligns flex lines, not child item alignment.

This will have no effect.

Yes, we want to vertically align them to the 'top' or start, which removes the default stretch value and instead uses the content height.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [MDN CSS Flexible Box Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Flexible_Box_Layout) includes a series of detailed guides with examples.
-   [CSS Tricks Guide to Flexbox](https://css-tricks.com/snippets/css/a-guide-to-flexbox/)
-   [What Happens When You Create a Flexbox Flex Container](https://www.smashingmagazine.com/2018/08/flexbox-display-flex-container/)
-   [Everything You Need To Know About Alignment In Flexbox](https://www.smashingmagazine.com/2018/08/flexbox-alignment/)
-   [How Big Is That Flexible Box?](https://www.smashingmagazine.com/2018/09/flexbox-sizing-flexible-box/)
-   [Use Cases For Flexbox](https://www.smashingmagazine.com/2018/10/flexbox-use-cases/)

<a href="/learn/css/layout/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">008</span>

Layout

<a href="/learn/css/grid/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">010</span>

Grid

CSS Grid Layout provides a two dimensional layout system, controlling layout in rows and columns. In this module discover everything grid has to offer.

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
