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

-   <a href="#the-parts-of-a-css-rule" class="toc__anchor">The parts of a CSS rule</a>
-   <a href="#simple-selectors" class="toc__anchor">Simple selectors</a>
    -   <a href="#universal-selector" class="toc__anchor">Universal selector</a>
    -   <a href="#type-selector" class="toc__anchor">Type selector</a>
    -   <a href="#class-selector" class="toc__anchor">Class selector</a>
    -   <a href="#id-selector" class="toc__anchor">ID selector</a>
    -   <a href="#attribute-selector" class="toc__anchor">Attribute selector</a>
    -   <a href="#grouping-selectors" class="toc__anchor">Grouping selectors</a>
-   <a href="#pseudo-classes-and-pseudo-elements" class="toc__anchor">Pseudo-classes and pseudo-elements</a>
    -   <a href="#pseudo-classes" class="toc__anchor">Pseudo-classes</a>
    -   <a href="#pseudo-element" class="toc__anchor">Pseudo-element</a>
-   <a href="#complex-selectors" class="toc__anchor">Complex selectors</a>
    -   <a href="#combinators" class="toc__anchor">Combinators</a>
    -   <a href="#compound-selectors" class="toc__anchor">Compound selectors</a>
-   <a href="#resources" class="toc__anchor">Resources</a>

002

Selectors
=========

To apply CSS to an element you need to select it. CSS provides you with a number of different ways to do this, and you can explore them in this module.

On this page

-   <a href="#the-parts-of-a-css-rule" class="toc__anchor">The parts of a CSS rule</a>
-   <a href="#simple-selectors" class="toc__anchor">Simple selectors</a>
    -   <a href="#universal-selector" class="toc__anchor">Universal selector</a>
    -   <a href="#type-selector" class="toc__anchor">Type selector</a>
    -   <a href="#class-selector" class="toc__anchor">Class selector</a>
    -   <a href="#id-selector" class="toc__anchor">ID selector</a>
    -   <a href="#attribute-selector" class="toc__anchor">Attribute selector</a>
    -   <a href="#grouping-selectors" class="toc__anchor">Grouping selectors</a>
-   <a href="#pseudo-classes-and-pseudo-elements" class="toc__anchor">Pseudo-classes and pseudo-elements</a>
    -   <a href="#pseudo-classes" class="toc__anchor">Pseudo-classes</a>
    -   <a href="#pseudo-element" class="toc__anchor">Pseudo-element</a>
-   <a href="#complex-selectors" class="toc__anchor">Complex selectors</a>
    -   <a href="#combinators" class="toc__anchor">Combinators</a>
    -   <a href="#compound-selectors" class="toc__anchor">Compound selectors</a>
-   <a href="#resources" class="toc__anchor">Resources</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 002: Selectors

If you've got some text that you only want to be larger and red if it's the first paragraph of an article, how do you do that?

    <article>
      <p>I want to be red and larger than the other text.</p>
      <p>I want to be normal sized and the default color.</p>
    </article>

You use a CSS selector to find that specific element and apply a CSS rule, like this.

    article p:first-of-type {
      color: red;
      font-size: 1.5em;
    }

CSS provides you with a lot of options to select elements and apply rules to them, ranging from very simple to very complex, to help solve situations like this.

The parts of a CSS rule <a href="#the-parts-of-a-css-rule" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

To understand how selectors work and their role in CSS, it's important to know the parts of a CSS rule. A CSS rule is a block of code, containing one or more selectors and one or more declarations.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/hFR4OOwyH5zWc5XUIcyu.svg" width="800" height="427" /></figure>In this CSS rule, the **selector** is `.my-css-rule` which finds all elements with a class of `my-css-rule` on the page. There are three declarations within the curly brackets. A declaration is a property and value pair which applies styles to the elements matched by the selectors. A CSS rule can have as many declarations and selectors as you like.

Simple selectors <a href="#simple-selectors" class="w-headline-link">#</a>
--------------------------------------------------------------------------

The most straightforward group of selectors target HTML elements plus classes, IDs, and other attributes which may be added to an HTML tag.

### Universal selector <a href="#universal-selector" class="w-headline-link">#</a>

A [universal selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors)—also known as a wildcard—matches any element.

    * {
      color: hotpink;
    }

This rule causes every HTML element on the page to have hotpink text.

### Type selector <a href="#type-selector" class="w-headline-link">#</a>

A [type selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Type_selectors) matches a HTML element directly.

    section {
      padding: 2em;
    }

This rule causes every `<section>` element to have `2em` of `padding` on all sides.

### Class selector <a href="#class-selector" class="w-headline-link">#</a>

A HTML element can have one or more items defined in their `class` attribute. The [class selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Class_selectors) matches any element that has that class applied to it.

    <div class="my-class"></div>
    <button class="my-class"></button>
    <p class="my-class"></p>

Any element that has the class applied to it will get colored red:

    .my-class {
      color: red;
    }

Notice how the `.` is only present in CSS and **not** the HTML. This is because the `.` character instructs the CSS language to match class attribute members. This is a common pattern in CSS, where a special character, or set of characters, is used to define selector types.

A HTML element that has a class of `.my-class` will still be matched to the above CSS rule, even if they have several other classes, like this:

    <div class="my-class another-class some-other-class"></div>

This is because CSS looks for a `class` attribute that *contains* the defined class, rather than matching that class exactly.

The value of a class attribute can be almost anything you want it to be. One thing that could trip you up, is that you can't start a class (or an ID) with a number, such as `.1element`. You can read more [in the specification](https://www.w3.org/TR/CSS21/syndata.html#characters).

### ID selector <a href="#id-selector" class="w-headline-link">#</a>

An HTML element with an `id` attribute should be the only element on a page with that ID value. You select elements with an [ID selector](https://developer.mozilla.org/en-US/docs/Web/CSS/ID_selectors) like this:

    #rad {
      border: 1px solid blue;
    }

This CSS would apply a blue border to the HTML element that has an `id` of `rad`, like this:

    <div id="rad"></div>

Similarly to the class selector `.`, use a `#` character to instruct CSS to look for an element that matches the `id` that follows it.

If the browser encounters more than one instance of an `id` it will still apply any CSS rules that match its selector. However, any element that has an `id` attribute is supposed to have a unique value for it, so unless you're writing very specific CSS for a single element, avoid applying styles with the `id` selector as it means you can't re-use those styles elsewhere.

### Attribute selector <a href="#attribute-selector" class="w-headline-link">#</a>

You can look for elements that have a certain HTML attribute, or have a certain value for an HTML attribute, using the [attribute selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors). Instruct CSS to look for attributes by wrapping the selector with square brackets (`[ ]`).

    [data-type='primary'] {
      color: red;
    }

This CSS looks for all elements that have an attribute of `data-type` with a value of `primary`, like this:

    <div data-type="primary"></div>

Instead of looking for a specific value of `data-type`, you can also look for elements with the attribute present, regardless of its value.

    [data-type] {
      color: red;
    }

    <div data-type="primary"></div>
    <div data-type="secondary"></div>

Both of these `<div>` elements will have red text.

You can use case-sensitive attribute selectors by adding an `s` operator to your attribute selector.

    [data-type='primary' s] {
      color: red;
    }

This means that if a HTML element had a `data-type` of `Primary`, instead of `primary`, it would not get red text. You can do the opposite—case insensitivity—by using an `i` operator.

Along with case operators, you have access to operators that match portions of strings inside attribute values.

    /* A href that contains “example.com” */
    [href*='example.com'] {
      color: red;
    }

    /* A href that starts with https */
    [href^='https'] {
      color: green;
    }

    /* A href that ends with .com */
    [href$='.com'] {
      color: blue;
    }

In this demo, the \`$\` operator in our attribute selector gets the filetype from the \`href\` attribute. This makes it possible to prefix the label—based on that filetype—using a pseudo-element.

### Grouping selectors <a href="#grouping-selectors" class="w-headline-link">#</a>

A selector doesn't have to match only a single element. You can group multiple selectors by separating them with commas:

    strong,
    em,
    .my-class,
    [lang] {
      color: red;
    }

This example extends the color change to both `<strong>` elements and `<em>` elements. It's also extended to a class named `.my-class`, and an element that has a `lang` attribute.

Test your knowledge of simple selectors

    * {}

What kind of simple selector is used in the above snippet?

<span data-role="option">attribute</span> <span data-role="option">ID</span> <span data-role="option">universal</span> <span data-role="option">class</span>

`[]` are used for **attribute** simple selectors.

`#` are used for **ID** simple selectors.

`*` is the **universal** simple selector.

`.` are used for **class** simple selectors.

    div {}

What kind of simple selector is used in the above snippet?

<span data-role="option">class</span> <span data-role="option">type</span> <span data-role="option">attribute</span> <span data-role="option">ID</span>

A `.` is used for **class** simple selectors.

An `element` name is used for **type** simple selectors.

Square brackets `[]` are used for **attribute** simple selectors.

A `#` is used for **ID** simple selectors.

Pseudo-classes and pseudo-elements <a href="#pseudo-classes-and-pseudo-elements" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------

CSS provides useful selector types that focus on specific platform state, like when an element is hovered, structures *inside* an element, or parts of an element.

### Pseudo-classes <a href="#pseudo-classes" class="w-headline-link">#</a>

HTML elements find themselves in various states, either because they are interacted with, or one of their child elements is in a certain state.

For example, an HTML element could be hovered with the mouse pointer by a user *or* a child element could also be hovered by the user. For those situations, use the `:hover` pseudo-class.

    /* Our link is hovered */
    a:hover {
      outline: 1px dotted green;
    }

    /* Sets all even paragraphs to have a different background */
    p:nth-child(even) {
      background: floralwhite;
    }

Find out more in the [pseudo-classes module](/learn/css/pseudo-classes).

### Pseudo-element <a href="#pseudo-element" class="w-headline-link">#</a>

Pseudo-elements differ from pseudo-classes because instead of responding to the platform state, they act as if they are inserting a new element with CSS. Pseudo-elements are also syntactically different from pseudo-classes, because instead of using a single colon (`:`), we use a double colon (`::`).

A double colon (`::`) is what distinguishes a pseudo-element from a pseudo-class, but because this distinction wasn't present in older versions of CSS specs, browsers support a single colon for the original pseudo-elements, such as `:before` and `:after` to help with backwards compatibility with older browsers, like IE8.

    .my-element::before {
      content: 'Prefix - ';
    }

As in the above demo where you prefixed a link's label with the type of file it was, you can use the `::before` pseudo-element to insert content **at the start of an element**, or the `::after` pseudo-element to insert content at the **end of an element**.

Pseudo-elements aren't limited to inserting content, though. You can also use them to target specific parts of an element. For example, suppose you have a list. Use `::marker` to style each bullet point (or number) in the list

    /* Your list will now either have red dots, or red numbers */
    li::marker {
      color: red;
    }

You can also use `::selection` to style the content that has been highlighted by a user.

    ::selection {
      background: black;
      color: white;
    }

Learn more in the [module on pseudo-elements](/learn/css/pseudo-elements).

Test your knowledge of pseudo selectors

Pseudo-element selectors use how many colons?

<span data-role="option">:</span> <span data-role="option">::</span> <span data-role="option">:::</span>

One `:` is used to target pseudo-classes.

Two `::` are used to target pseudo-elements.

This is invalid and targets nothing.

    p:hover {
      background: white;
      color: black;
    }

What kind of pseudo selector is used in the above snippet?

<span data-role="option">Pseudo-class</span> <span data-role="option">Pseudo-element</span>

One `:` is used to target pseudo-classes.

Two `::` are used to target pseudo-elements.

Complex selectors <a href="#complex-selectors" class="w-headline-link">#</a>
----------------------------------------------------------------------------

You have already seen a vast array of selectors, but sometimes, you will need more *fine-grained control* with your CSS. This is where complex selectors step in to help.

It's worth remembering at this point that although the following selectors give us more power, we can only **cascade downwards**, selecting child elements. We are not able to target upwards and select a parent element. We cover what the cascade is and how it works [in a later lesson](/learn/css/the-cascade).

### Combinators <a href="#combinators" class="w-headline-link">#</a>

A combinator is what sits between two selectors. For example, if the selector was `p > strong`, the combinator is the `>` character. The selectors which use these combinators help you select items based on their position in the document.

#### Descendant combinator <a href="#descendant-combinator" class="w-headline-link">#</a>

To understand descendant combinators, you need to first understand parent and child elements.

    <p>A paragraph of text with some <strong>bold text for emphasis</strong>.</p>

The parent element is the `<p>` which contains text. Inside that `<p>` element is a `<strong>` element, making its content bold. Because it is inside the `<p>`, it is a child element.

A descendant combinator allows us to target a child element. This uses a space (``) to instruct the browser to look for child elements:

    p strong {
      color: blue;
    }

This snippet selects all `<strong>` elements that are child elements of `<p>` elements only, making them blue recursively.

Because the descendant combinator is recursive, the padding added to each child element applies, resulting in a staggered effect.

This effect is better visualised in the above example, using the combinator selector, `.top div`. That CSS rule adds left padding to those `<div>` elements. Because the combinator is recursive, all `<div>` elements that are in `.top` will have that same padding applied to them.

Take a look at the HTML panel in this demo to see how the `.top` element has several `<div>` child elements which themselves, have `<div>` child elements.

#### Next sibling combinator <a href="#next-sibling-combinator" class="w-headline-link">#</a>

You can look for an element that immediately follows another element by using a `+` character in your selector.

To add space between stacked elements, use the next sibling combinator to add space *only* if an element is a **next sibling** of a child element of `.top`.

You could add margin to all child elements of `.top`, using the following selector:

    .top * {
      margin-top: 1em;
    }

The problem with this is that because you're selecting every child element of `.top`, this rule potentially creates extra, unnecessary space. The **next sibling combinator**, mixed with a **universal selector** enables you to not only control what elements get space, but also apply space to **any element**. This provides you with some long-term flexibility, regardless of what HTML elements appear in `.top`.

#### Subsequent- sibling combinator <a href="#subsequent-sibling-combinator" class="w-headline-link">#</a>

A subsequent combinator is very similar to a next sibling selector. Instead of a `+` character however, use a `~` character. How this differs is that an element just has to follow another element with the same parent, rather than being the next element with the same parent.

Use a subsequent selector along with a \`:checked\` pseudo class to create a pure CSS switch element.

This subsequent combinator provides a little less rigidity, which is useful in contexts like the above sample, where we change the color of a custom switch when its associated checkbox has the `:checked` state.

#### Child combinator <a href="#child-combinator" class="w-headline-link">#</a>

A child combinator (also known as direct descendant) allows you more control over the recursion that comes with combinator selectors. By using the `>` character, you limit the combinator selector to apply **only** to direct children.

Consider the previous, next sibling selector example. The space is added to each **next sibling**, but if one of those elements also has **next sibling elements** as children, it can result in undesirable, extra spacing.

To alleviate this problem, change the **next sibling selector** to incorporate a child combinator: `> * + *`. The rule will now **only** apply to direct children of `.top`.

### Compound selectors <a href="#compound-selectors" class="w-headline-link">#</a>

You can combine selectors to increase specificity and readability. For example, to target `<a>` elements, that also have a class of `.my-class`, write the following:

    a.my-class {
      color: red;
    }

This wouldn't apply a red color to all links and it would also only apply the red color to `.my-class` **if** it was on an `<a>` element. For more on this, see the [specificity module](/learn/css/specificity).

Test your knowledge of complex selectors

Which of the following symbols is **not** selector combinator?

<span data-role="option">&gt;</span> <span data-role="option">÷</span> <span data-role="option">+</span> <span data-role="option">\*</span> <span data-role="option">.</span>

The direct descendant combinator.

Invalid, not a CSS symbol.

The next sibling combinator.

This universal simple selector.

The class simple selector.

    section.awesome {
      border: 1px solid hotpink;
    }

The above selector is an example of a...

<span data-role="option">Combinator</span> <span data-role="option">Compound selector</span> <span data-role="option">Terminator</span>

A symbol used to combine selectors into a more specific one.

When 2 or more selectors are used together, without a combinator, in order to create a more specific selector.

Not a selector type, but sounds like one doesn't it? 🤖

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [CSS selectors reference](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Selectors)
-   [Interactive selectors game](https://flukeout.github.io/)
-   [Pseudo-class and pseudo-elements reference](https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/Pseudo-classes_and_pseudo-elements)
-   [A tool that translates CSS selectors into plain-english explainers](https://kittygiraudel.github.io/selectors-explained/)

<a href="/learn/css/box-model/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">001</span>

Box Model

<a href="/learn/css/the-cascade/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">003</span>

The cascade

Sometimes two or more competing CSS rules could apply to an element. In this module find out how the browser chooses which to use, and how to control this selection.

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
