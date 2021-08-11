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

-   <a href="#interactive-states" class="toc__anchor">Interactive states</a>
    -   <a href="#:hover" class="toc__anchor">:hover</a>
    -   <a href="#:active" class="toc__anchor">:active</a>
    -   <a href="#:focus-:focus-within-and-:focus-visible" class="toc__anchor">:focus, :focus-within, and :focus-visible</a>
    -   <a href="#:target" class="toc__anchor">:target</a>
-   <a href="#historic-states" class="toc__anchor">Historic states</a>
    -   <a href="#:link" class="toc__anchor">:link</a>
-   <a href="#form-states" class="toc__anchor">Form states</a>
    -   <a href="#:disabled-and-:enabled" class="toc__anchor">:disabled and :enabled</a>
    -   <a href="#:checked-and-:indeterminate" class="toc__anchor">:checked and :indeterminate</a>
    -   <a href="#:placeholder-shown" class="toc__anchor">:placeholder-shown</a>
    -   <a href="#validation-states" class="toc__anchor">Validation states</a>
-   <a href="#selecting-elements-by-their-index-order-and-occurrence" class="toc__anchor">Selecting elements by their index, order and occurrence</a>
    -   <a href="#first-child-and-last-child" class="toc__anchor">first-child and last-child</a>
    -   <a href="#only-child" class="toc__anchor">only-child</a>
    -   <a href="#:first-of-type-and-:last-of-type" class="toc__anchor">:first-of-type and :last-of-type</a>
    -   <a href="#nth-child-and-nth-of-type" class="toc__anchor">nth-child and nth-of-type</a>
    -   <a href="#only-of-type" class="toc__anchor">only-of-type</a>
-   <a href="#finding-empty-elements" class="toc__anchor">Finding empty elements</a>
    -   <a href="#:empty" class="toc__anchor">:empty</a>
-   <a href="#finding-and-excluding-multiple-elements" class="toc__anchor">Finding and excluding multiple elements</a>
    -   <a href="#:is()" class="toc__anchor">:is()</a>
    -   <a href="#:not()" class="toc__anchor">:not()</a>

014

Pseudo-classes
==============

Pseudo-classes let you apply CSS based on state changes. This means that your design can react to user input such as an invalid email address.

On this page

-   <a href="#interactive-states" class="toc__anchor">Interactive states</a>
    -   <a href="#:hover" class="toc__anchor">:hover</a>
    -   <a href="#:active" class="toc__anchor">:active</a>
    -   <a href="#:focus-:focus-within-and-:focus-visible" class="toc__anchor">:focus, :focus-within, and :focus-visible</a>
    -   <a href="#:target" class="toc__anchor">:target</a>
-   <a href="#historic-states" class="toc__anchor">Historic states</a>
    -   <a href="#:link" class="toc__anchor">:link</a>
-   <a href="#form-states" class="toc__anchor">Form states</a>
    -   <a href="#:disabled-and-:enabled" class="toc__anchor">:disabled and :enabled</a>
    -   <a href="#:checked-and-:indeterminate" class="toc__anchor">:checked and :indeterminate</a>
    -   <a href="#:placeholder-shown" class="toc__anchor">:placeholder-shown</a>
    -   <a href="#validation-states" class="toc__anchor">Validation states</a>
-   <a href="#selecting-elements-by-their-index-order-and-occurrence" class="toc__anchor">Selecting elements by their index, order and occurrence</a>
    -   <a href="#first-child-and-last-child" class="toc__anchor">first-child and last-child</a>
    -   <a href="#only-child" class="toc__anchor">only-child</a>
    -   <a href="#:first-of-type-and-:last-of-type" class="toc__anchor">:first-of-type and :last-of-type</a>
    -   <a href="#nth-child-and-nth-of-type" class="toc__anchor">nth-child and nth-of-type</a>
    -   <a href="#only-of-type" class="toc__anchor">only-of-type</a>
-   <a href="#finding-empty-elements" class="toc__anchor">Finding empty elements</a>
    -   <a href="#:empty" class="toc__anchor">:empty</a>
-   <a href="#finding-and-excluding-multiple-elements" class="toc__anchor">Finding and excluding multiple elements</a>
    -   <a href="#:is()" class="toc__anchor">:is()</a>
    -   <a href="#:not()" class="toc__anchor">:not()</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 015: Pseudo-classes

Say you've got an email sign up form, and you want the email form field to have a red border if it contains an invalid email address. How do you do that? You can use an `:invalid` CSS pseudo-class, which is one of many browser-provided pseudo-classes.

A pseudo-class lets you apply styles based on state changes and external factors. This means that your design can react to user input such as an invalid email address. These are covered in the [selectors](/learn/css/selectors) module, and this module will take you through them in more detail.

Unlike pseudo-elements, which you can learn more about in the [previous module](/learn/css/pseudo-elements), pseudo-*classes* hook onto specific *states* that an element might be in, rather than generally style parts of that element.

Interactive states <a href="#interactive-states" class="w-headline-link">#</a>
------------------------------------------------------------------------------

The following pseudo-classes apply due to an interaction a user has with your page.

### `:hover` <a href="#:hover" class="w-headline-link">#</a>

If a user has a pointing device like a mouse or trackpad, and they place it over an element, you can hook on to that state with [`:hover`](https://developer.mozilla.org/en-US/docs/Web/CSS/:hover) to apply styles. This is a useful way to hint that an element can be interacted with.

### `:active` <a href="#:active" class="w-headline-link">#</a>

This state is triggered when an element is actively being interacted with— such as a click—before click is released. If a pointing device like a mouse is used, this state is when the click starts and hasn't yet been released.

### `:focus`, `:focus-within`, and `:focus-visible` <a href="#:focus-:focus-within-and-:focus-visible" class="w-headline-link">#</a>

If an element can receive focus—like a `<button>`— you can react to that state with the [`:focus`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus) pseudo-class.

You can also react if a child element of your element receives focus with [`:focus-within`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-within).

Focusable elements, like buttons, will show a focus ring when they are in focus—even when clicked. In this sort of situation, a developer will apply the following CSS:

    button:focus {
       outline: none;
    }

This CSS removes the default browser focus ring when an element receives focus, which presents an accessibility issue for users who navigate a web page with a keyboard. If there is no focus style, they won't be able to keep track of where focus currently is when using the tab key. With [`:focus-visible`](https://developer.mozilla.org/en-US/docs/Web/CSS/:focus-visible) you can present a focus style when an element receives focus via the keyboard, while also using the `outline: none` rule to prevent it when a pointer device interacts with it.

    button:focus {
      outline: none;
    }

    button:focus-visible {
       outline: 1px solid black;
    }

### `:target` <a href="#:target" class="w-headline-link">#</a>

The [`:target`](https://developer.mozilla.org/en-US/docs/Web/CSS/:target) pseudo-class selects an element that has an `id` matching a URL fragment. Say you have the following HTML:

    <article id="content">
      …
    </article>

You can attach styles to that element when the url contains `#content`.

    #content:target {
        background: yellow;
    }

This is useful for highlighting areas that might have been specifically linked to, such as the main content on a website, via a skip link.

Historic states <a href="#historic-states" class="w-headline-link">#</a>
------------------------------------------------------------------------

### `:link` <a href="#:link" class="w-headline-link">#</a>

The [`:link`](https://developer.mozilla.org/en-US/docs/Web/CSS/:link) pseudo-class can be applied to any `<a>` element that has a `href` value that **hasn't been** visited yet. `:visited`

You can style a link that's already been visited by the user using the [`:visited`](https://developer.mozilla.org/en-US/docs/Web/CSS/:visited) pseudo-class. This is the opposite state to `:link` but you have fewer CSS properties to use for [security reasons](https://developer.mozilla.org/en-US/docs/Web/CSS/Privacy_and_the_:visited_selector). You can only style `color`, `background-color`, `border-color`, `outline-color` and the color of SVG `fill` and `stroke`.

#### Order matters <a href="#order-matters" class="w-headline-link">#</a>

If you define a `:visited` style, it can be overridden by a link pseudo-class with at least equal specificity. Because of this, it's recommended that you use the LVHA rule for styling links with pseudo-classes in a particular order: `:link`, `:visited`, `:hover`, `:active`.

    a:link {}
    a:visited {}
    a:hover {}
    a:active {}

For security reasons, you can only change styles defined by a `:link` or unvisited state with the `:visited` pseudo-class, so making sure you define changeable styles first is important. Sticking to the LVHA rule will help with that.

Form states <a href="#form-states" class="w-headline-link">#</a>
----------------------------------------------------------------

The following pseudo-classes can select form elements, in the various states that these elements might be in during interaction with them.

### `:disabled` and `:enabled` <a href="#:disabled-and-:enabled" class="w-headline-link">#</a>

If a form element, such as a `<button>` is disabled by the browser, you can hook on to that state with the [`:disabled`](https://developer.mozilla.org/en-US/docs/Web/CSS/:disabled) pseudo-class. The [`:enabled`](https://developer.mozilla.org/en-US/docs/Web/CSS/:enabled) pseudo-class is available for the opposite state, though form elements are also `:enabled` by default, therefore you might not find yourself reaching for this pseudo-class.

### `:checked` and `:indeterminate` <a href="#:checked-and-:indeterminate" class="w-headline-link">#</a>

The [`:checked`](https://developer.mozilla.org/en-US/docs/Web/CSS/:checked) pseudo-class is available when a supporting form element, such as a checkbox or radio button is in a checked state.

The `:checked` state is a binary(true or false) state, but checkboxes do have an in-between state when they are neither checked or unchecked. This is known as the [`:indeterminate`](https://developer.mozilla.org/en-US/docs/Web/CSS/:indeterminate) state.

An example of this state is when you have a "select all" control that checks all checkboxes in a group. If the user was to then uncheck one of these checkboxes, the root checkbox would no longer represent "all" being checked, so should be put into an indeterminate state.

The `<progress>` element also has an indeterminate state that can be styled. A common use case is to give it a striped appearance to indicate it's unknown how much more is needed.

### `:placeholder-shown` <a href="#:placeholder-shown" class="w-headline-link">#</a>

If a form field has a `placeholder` attribute and **no value**, the [`:placeholder-shown`](https://developer.mozilla.org/en-US/docs/Web/CSS/:placeholder-shown) pseudo-class can be used to attach styles to that state. As soon as there is content in the field, whether it has a `placeholder` or not, this state will no longer apply.

### Validation states <a href="#validation-states" class="w-headline-link">#</a>

You can respond to HTML form validation with pseudo-classes such as [`:valid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:valid), [`:invalid`](https://developer.mozilla.org/en-US/docs/Web/CSS/:invalid) and [`:in-range`](https://developer.mozilla.org/en-US/docs/Web/CSS/:in-range). The `:valid` and `:invalid` pseudo-classes are useful for contexts such as an email field that has a `pattern` that needs to be matched, for it to be a valid field. This valid value state can be shown to the user, helping them understand they can safely move to the next field.

The `:in-range` pseudo-class is available if an input has a `min` and `max`, such as a numeric input *and* the value is within those bounds.

With HTML forms, you can determine that a field is required with the `required` attribute. The [`:required`](https://developer.mozilla.org/en-US/docs/Web/CSS/:required) pseudo-class will be available for required fields. Fields that are not required can be selected with the [`:optional`](https://developer.mozilla.org/en-US/docs/Web/CSS/:optional) pseudo-class.

It's not a good idea to rely solely on color to signify state changes— especially red and green—because colorblind and low-vision users can struggle to see a state change, or even miss it completely. A good idea is to use color to support state changes, along with text changes and icon changes to visually signify change

Selecting elements by their index, order and occurrence <a href="#selecting-elements-by-their-index-order-and-occurrence" class="w-headline-link">#</a>
-------------------------------------------------------------------------------------------------------------------------------------------------------

There is a group of pseudo-classes that select items based on where they are in the document.

### `first-child` and `last-child` <a href="#first-child-and-last-child" class="w-headline-link">#</a>

If you want to find the first or last item, you can use [`:first-child`](https://developer.mozilla.org/en-US/docs/Web/CSS/:first-child) and [`:last-child`](https://developer.mozilla.org/en-US/docs/Web/CSS/:last-child). These pseudo-classes will return either the first or last element in a group of sibling elements.

### `only-child` <a href="#only-child" class="w-headline-link">#</a>

You can also select elements that have no siblings, with the [`:only-child`](https://developer.mozilla.org/en-US/docs/Web/CSS/:only-child) pseudo-class.

### `:first-of-type` and `:last-of-type` <a href="#:first-of-type-and-:last-of-type" class="w-headline-link">#</a>

You can select the [`:first-of-type`](https://developer.mozilla.org/en-US/docs/Web/CSS/:first-of-type) and [`:last-of-type`](https://developer.mozilla.org/en-US/docs/Web/CSS/:last-of-type) which at first, look like they do the same thing as `:first-child` and `:last-child`, but consider this HTML:

    <div class="my-parent">
      <p>A paragraph</p>
        <div>A div</div>
      <div>Another div</div>
    </div>

And this CSS:

    .my-parent div:first-child {
       color: red;
    }

No elements would be colored red because the first child is a paragraph and not a div. The `:first-of-type` pseudo-class is useful in this context.

    .my-parent div:first-of-type {
        color: red;
    }

Even though the first `<div>` is the second child, it is still the first of type inside the `.my-parent` element, so with this rule, it will be colored red.

### `nth-child` and `nth-of-type` <a href="#nth-child-and-nth-of-type" class="w-headline-link">#</a>

You're not limited to first and last children and types either. The [`nth-child`](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-child) and [`nth-of-type`](https://developer.mozilla.org/en-US/docs/Web/CSS/:nth-of-type) pseudo-classes allow you to specify an element that is at a certain index. The indexing in CSS selectors starts at 1.

You can pass more than an index into these pseudo-classes too. If you wanted to select all even elements, you can use `nth-child(even)`.

You can also create more complex selectors that find items at regularly spaced intervals, using [the An+B microsyntax](https://www.w3.org/TR/css-syntax-3/#anb-microsyntax).

    li:nth-child(3n+3) {
       background: yellow;
    }

This selector selects every third item, starting at item 3. The `n` in this expression is the index, which starts at zero the 3 (`3n`) is how much you multiply that index by.

Let's say you have 7 `<li>` items. The first item that is selected is 3 because `3n+3` translates to `(3 * 0) + 3`. The next iteration would pick item 6 because `n` has now incremented to `1`, so `(3 * 1) + 3)`. This expression works for both `nth-child` and `nth-of-type`.

You can play around with this sort of selector on this [nth-child tester](https://css-tricks.com/examples/nth-child-tester/) or this [quantity selector tool](https://quantityqueries.com).

### `only-of-type` <a href="#only-of-type" class="w-headline-link">#</a>

Lastly, you can find the only element of a certain type in a group of siblings with [`:only-of-type`](https://developer.mozilla.org/en-US/docs/Web/CSS/:only-of-type). This is useful if you want to select lists with only one item, or if you want to find the only bold element in a paragraph.

Finding empty elements <a href="#finding-empty-elements" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------

It can sometimes be useful to identify completely empty elements, and there is a pseudo-class for that too.

### `:empty` <a href="#:empty" class="w-headline-link">#</a>

If an element has no children, the [`:empty`](https://developer.mozilla.org/en-US/docs/Web/CSS/:empty) pseudo-class applies to them. Children aren't just HTML elements or text nodes though: they can also be whitespace, which can be confusing when you're debugging the following HTML and wondering why it isn't working with `:empty`:

    <div>
    </div>

The reason is that there's some whitespace between the opening and closing `<div>`, so empty won't work.

The `:empty` pseudo-class can be useful if you have little control over the HTML and want to hide empty elements, such as a WYSIWYG content editor. Here, an editor has added a stray, empty paragraph.

    <article class="post">
     <p>Donec ullamcorper nulla non metus auctor fringilla.</p>
     <p></p>
     <p>Curabitur blandit tempus porttitor.</p>
    </article>

With `:empty`, you can find that and hide it.

    .post :empty {
      display: none;
    }

Finding and excluding multiple elements <a href="#finding-and-excluding-multiple-elements" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------

Some pseudo-classes help you to write more compact CSS.

### `:is()` <a href="#:is()" class="w-headline-link">#</a>

If you want to find all of the `h2`, `li` and `img` child elements in a `.post` element, you might think to write a selector list like this:

    .post h2,
    .post li,
    .post img {
     …
    }

With the [`:is()`](https://developer.mozilla.org/en-US/docs/Web/CSS/:is) pseudo-class, you can write a more compact version:

    .post :is(h2, li, img) {
       …
    }

The `:is` pseudo-class is not only more compact than a selector list but it is also more forgiving. In most cases, if there's an error or unsupported selector in a selector list, the entire selector list will no longer work. If there's an error in the passed selectors in an `:is` pseudo-class, it will ignore the invalid selector, but use those which are valid.

### `:not()` <a href="#:not()" class="w-headline-link">#</a>

You can also exclude items with the [`:not()`](https://developer.mozilla.org/en-US/docs/Web/CSS/:not) pseudo-class. For example, you can use it to style all links that don't have a `class` attribute.

    a:not([class]) {
        color: blue;
    }

A `:not` pseudo-class can also help you to improve accessibility. For example, an `<img>` must have an `alt`, even if its an empty value, so you could write a CSS rule that adds a thick red outline to invalid images:

    img:not([alt]) {
       outline: 10px red;
    }

Test your knowledge of pseudo classes

Pseudo-classes act as if a class has been dynamically applied to an element, while pseudo-elements act on an element itself.

<span data-role="option">True</span> <span data-role="option">False</span>

Watch for the use of a single or double `:` as a key distinguishing character in the selector

Pseudo-elements are for parts, Pseudo-classes are for state.

Which of the following are a *functional* pseudo-class?

<span data-role="option">`:is()`</span> <span data-role="option">`:target`</span> <span data-role="option">`:empty`</span> <span data-role="option">`:not()`</span>

🎉

Functional pseudo-classes have `()` after them, to indicate they accept paremeters.

Functional pseudo-classes have `()` after them, to indicate they accept paremeters.

🎉

Which of the following psuedo-classes are due to a user-interaction?

<span data-role="option">`:hover`</span> <span data-role="option">`:press`</span> <span data-role="option">`:squeeze`</span> <span data-role="option">`:target`</span> <span data-role="option">`:focus-within`</span>

🎉

Try again!

Try again!

🎉

🎉

Which of the following are `<form>` state pseudo classes?

<span data-role="option">`:enabled`</span> <span data-role="option">`:fresh`</span> <span data-role="option">`:indeterminate`</span> <span data-role="option">`:checked`</span> <span data-role="option">`:in-range`</span> <span data-role="option">`:loading`</span> <span data-role="option">`:valid`</span>

🎉

Try again!

🎉

🎉

🎉

Try again!

🎉

<a href="/learn/css/pseudo-elements/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">013</span>

Pseudo-elements

<a href="/learn/css/borders/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">015</span>

Borders

A border provides a frame for your boxes. In this module find out how to change the size, style and color of borders using CSS.

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
