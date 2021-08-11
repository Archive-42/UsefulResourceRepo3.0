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

-   <a href="#specificity-scoring" class="toc__anchor">Specificity scoring</a>
-   <a href="#scoring-each-selector-type" class="toc__anchor">Scoring each selector type</a>
    -   <a href="#universal-selector" class="toc__anchor">Universal selector</a>
    -   <a href="#element-or-pseudo-element-selector" class="toc__anchor">Element or pseudo-element selector</a>
    -   <a href="#class-pseudo-class-or-attribute-selector" class="toc__anchor">Class, pseudo-class, or attribute selector</a>
    -   <a href="#id-selector" class="toc__anchor">ID selector</a>
    -   <a href="#inline-style-attribute" class="toc__anchor">Inline style attribute</a>
    -   <a href="#!important-rule" class="toc__anchor">!important rule</a>
-   <a href="#specificity-in-context" class="toc__anchor">Specificity in context</a>
-   <a href="#visualizing-specificity" class="toc__anchor">Visualizing specificity</a>
-   <a href="#pragmatically-increasing-specificity" class="toc__anchor">Pragmatically increasing specificity</a>
-   <a href="#a-matching-specificity-score-sees-the-newest-instance-win" class="toc__anchor">A matching specificity score sees the newest instance win</a>
-   <a href="#resources" class="toc__anchor">Resources</a>

004

Specificity
===========

This module takes a deeper look at specificity, a key part of the cascade.

On this page

-   <a href="#specificity-scoring" class="toc__anchor">Specificity scoring</a>
-   <a href="#scoring-each-selector-type" class="toc__anchor">Scoring each selector type</a>
    -   <a href="#universal-selector" class="toc__anchor">Universal selector</a>
    -   <a href="#element-or-pseudo-element-selector" class="toc__anchor">Element or pseudo-element selector</a>
    -   <a href="#class-pseudo-class-or-attribute-selector" class="toc__anchor">Class, pseudo-class, or attribute selector</a>
    -   <a href="#id-selector" class="toc__anchor">ID selector</a>
    -   <a href="#inline-style-attribute" class="toc__anchor">Inline style attribute</a>
    -   <a href="#!important-rule" class="toc__anchor">!important rule</a>
-   <a href="#specificity-in-context" class="toc__anchor">Specificity in context</a>
-   <a href="#visualizing-specificity" class="toc__anchor">Visualizing specificity</a>
-   <a href="#pragmatically-increasing-specificity" class="toc__anchor">Pragmatically increasing specificity</a>
-   <a href="#a-matching-specificity-score-sees-the-newest-instance-win" class="toc__anchor">A matching specificity score sees the newest instance win</a>
-   <a href="#resources" class="toc__anchor">Resources</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 003: Specificity

Suppose that you're working with the following HTML and CSS:

    <button class="branding">Hello, Specificity!</button>

    button {
      color: red;
    }

    .branding {
      color: blue;
    }

There's two competing rules here. One will color the button red and the other will color it blue. Which rule gets applied to the element? Understanding the CSS specification's algorithm about specificity is the key to understanding how CSS decides between competing rules.

Specificity is one of the four distinct stages of the cascade, which was covered in the last module, on [the cascade](/learn/css/the-cascade/).

Specificity scoring <a href="#specificity-scoring" class="w-headline-link">#</a>
--------------------------------------------------------------------------------

Each selector rule gets a scoring. You can think of specificity as a total score and each selector type earns points towards that score. The selector with the highest score wins.

With specificity in a real project, the balancing act is making sure the CSS rules you expect to apply, actually *do apply,* while generally keeping scores low to prevent complexity. The score should only be as high as we need it to be, rather than aiming for the highest score possible. In the future, some genuinely more important CSS might need to be applied. If you go for the highest score, you'll make that job hard.

Scoring each selector type <a href="#scoring-each-selector-type" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------

Each selector type earns points. You add all of these points up to calculate a selector's overall specificity.

### Universal selector <a href="#universal-selector" class="w-headline-link">#</a>

A [universal selector](https://developer.mozilla.org/en-US/docs/Web/CSS/Universal_selectors) (`*`) has **no specificity** and gets **0 points**. This means that any rule with 1 or more points will override it

    * {
      color: red;
    }

### Element or pseudo-element selector <a href="#element-or-pseudo-element-selector" class="w-headline-link">#</a>

An [element](https://developer.mozilla.org/en-US/docs/Web/CSS/Type_selectors) (type) or [pseudo-element](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-elements) selector gets **1 point of specificity** .

#### Type selector <a href="#type-selector" class="w-headline-link">#</a>

    div {
      color: red;
    }

#### Pseudo-element selector <a href="#pseudo-element-selector" class="w-headline-link">#</a>

    ::selection {
      color: red;
    }

### Class, pseudo-class, or attribute selector <a href="#class-pseudo-class-or-attribute-selector" class="w-headline-link">#</a>

A [class](https://developer.mozilla.org/en-US/docs/Web/CSS/Class_selectors), [pseudo-class](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes) or [attribute](https://developer.mozilla.org/en-US/docs/Web/CSS/Attribute_selectors) selector gets **10 points of specificity**.

#### Class selector <a href="#class-selector" class="w-headline-link">#</a>

    .my-class {
      color: red;
    }

#### Pseudo-class selector <a href="#pseudo-class-selector" class="w-headline-link">#</a>

    :hover {
      color: red;
    }

#### Attribute selector <a href="#attribute-selector" class="w-headline-link">#</a>

    [href='#'] {
      color: red;
    }

The [`:not()`](https://developer.mozilla.org/en-US/docs/Web/CSS/:not) pseudo-class itself adds nothing to the specificity calculation. However, the selectors passed in as arguments do get added to the specificity calculation.

    div:not(.my-class) {
      color: red;
    }

This sample would have **11 points** of specificity because it has one type selector (`div`) and one class *inside* the `:not()`.

### ID selector <a href="#id-selector" class="w-headline-link">#</a>

An [ID](https://developer.mozilla.org/en-US/docs/Web/CSS/ID_selectors) selector gets **100 points of specificity**, as long as you use an ID selector (`#myID`) and not an attribute selector (`[id="myID"]`).

    #myID {
      color: red;
    }

### Inline style attribute <a href="#inline-style-attribute" class="w-headline-link">#</a>

CSS applied directly to the `style` attribute of the HTML element, gets a **specificity score of 1,000 points**. This means that in order to override it in CSS, you have to write an extremely specific selector.

    <div style="color: red"></div>

### `!important` rule <a href="#!important-rule" class="w-headline-link">#</a>

Lastly, an `!important` at the end of a CSS value gets a specificity score of **10,000 points**. This is the highest specificity that one individual item can get.

An `!important` rule is applied to a CSS property, so everything in the overall rule (selector and properties) does not get the same specificity score.

    .my-class {
      color: red !important; /* 10,000 points */
      background: white; /* 10 points */
    }

What is the specificity score of `a[href="#"]`?

<span data-role="option">1</span> <span data-role="option">5</span> <span data-role="option">11</span>

The `a` is worth 1 point, but the `[href="#"]` is worth 10 points.

Try again!

The `a` is worth 1 point and the `[href="#"]` is worth 10 points, making a total score of **11 points**.

Specificity in context <a href="#specificity-in-context" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------

The specificity of each selector that matches an element is added together. Consider this example HTML:

    <a class="my-class another-class" href="#">A link</a>

This link has two classes on it. Add the following CSS, and it gets **1 point of specificity**:

    a {
      color: red;
    }

Reference one of the classes in this rule, it now has **11 points of specificity**:

    a.my-class {
      color: green;
    }

Add the other class to the selector, it now has **21 points of specificity**:

    a.my-class.another-class {
      color: rebeccapurple;
    }

Add the `href` attribute to the selector, it now has **31 points of specificity**:

    a.my-class.another-class[href] {
      color: goldenrod;
    }

Finally,add a `:hover` pseudo-class to all of that, the selector ends up with **41 points of specificity**:

    a.my-class.another-class[href]:hover {
      color: lightgrey;
    }

Which of the following selectors is worth **21 points**?

<span data-role="option">`article > section`</span> <span data-role="option">`article.card.dark`</span> <span data-role="option">`article:hover a[href]`</span>

Elements are worth 1 point, there are 2 elements in the selector, making this worth **2 points**.

Elements are worth 1 point, classes are worth 10 points, and with 2 classes and 1 element, that makes this selector worth **21 points**.

Elements are worth 1 point, pseudo-classes and attributes are worth 10 points, there are 2 points for the elements, and 20 points for the attributes and classes, makes this selector worth **22 points**.

Visualizing specificity <a href="#visualizing-specificity" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

In diagrams and specificity calculators, the specificity is often visualized like this:

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/McrFhjqHXMznUzXbRuJ6.svg" alt="A diagram demonstrating most specific to least specific selectors" width="800" height="474" />

The left group is `id` selectors. The second group is class, attribute, and pseudo-class selectors. The final group is element and pseudo-element selectors.

For reference, the following selector is `0-4-1`:

    a.my-class.another-class[href]:hover {
      color: lightgrey;
    }

Which of the following selectors is `1-2-1`?

<span data-role="option">`section#specialty.dark`</span> <span data-role="option">`#specialty:hover li.dark`</span> <span data-role="option">`[data-state-rad].dark#specialty:hover`</span> <span data-role="option">`li#specialty section.dark`</span>

This selector is visualized as `1-1-1`.

🎉

This selector is visualized as `1-3-0`.

This selector is visualized as `1-1-2`.

Pragmatically increasing specificity <a href="#pragmatically-increasing-specificity" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------

Let's say we have some CSS that looks like this:

    .my-button {
      background: blue;
    }

    button[onclick] {
      background: grey;
    }

With HTML that looks like this:

    <button class="my-button" onclick="alert('hello')">Click me</button>

The button has a grey background, because the second selector earns **11 points of specificity** (`0-1-1`). This is because it has one type selector (`button`), which is **1 point** and an attribute selector (`[onclick]`), which is **10 points**.

The previous rule—`.my-button`—gets **10 points** (`0-1-0`), because it has one class selector.

If you want to give this rule a boost, repeat the class selector like this:

    .my-button.my-button {
      background: blue;
    }

    button[onclick] {
      background: grey;
    }

Now, the button will have a blue background, because the new selector gets a specificity score of **20 points** (`0-2-0`).

**Caution**: If you find that you are needing to boost specificity like this frequently, it may indicate that you are writing overly specific selectors. Consider whether you can refactor your CSS to reduce the specificity of other selectors to avoid this problem.

A matching specificity score sees the newest instance win <a href="#a-matching-specificity-score-sees-the-newest-instance-win" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------------------------------------

Let's stay with the button example for now and switch the CSS around to this:

    .my-button {
      background: blue;
    }

    [onclick] {
      background: grey;
    }

The button has a grey background, because **both selectors have an identical specificity score** (`0-1-0`).

If you switch the rules in the source order, the button would then be blue.

    [onclick] {
      background: grey;
    }

    .my-button {
      background: blue;
    }

This is the only instance where newer CSS wins. To do so it must match the specificity of another selector that targets the same element.

Resources <a href="#resources" class="w-headline-link">#</a>
------------------------------------------------------------

-   [CSS SpeciFISHity](http://specifishity.com)
-   [Specificity Calculator](https://specificity.keegan.st)
-   [MDN Specificity](https://developer.mozilla.org/en-US/docs/Web/CSS/Specificity)
-   [Specifics on CSS Specificity](https://css-tricks.com/specifics-on-css-specificity/)
-   [Another Specificity Calculator](https://polypane.app/css-specificity-calculator)

<a href="/learn/css/the-cascade/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">003</span>

The cascade

<a href="/learn/css/inheritance/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">005</span>

Inheritance

Some CSS properties inherit if you don't specify a value for them. Find out how this works, and how to use it to your advantage in this module.

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
