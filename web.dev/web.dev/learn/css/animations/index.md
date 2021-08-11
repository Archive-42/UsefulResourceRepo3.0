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

-   <a href="#what-is-a-keyframe" class="toc__anchor">What is a keyframe?</a>
    -   <a href="#@keyframes" class="toc__anchor">@keyframes</a>
-   <a href="#the-animation-properties" class="toc__anchor">The animation properties</a>
    -   <a href="#animation-duration" class="toc__anchor">animation-duration</a>
    -   <a href="#animation-timing-function" class="toc__anchor">animation-timing-function</a>
    -   <a href="#animation-iteration-count" class="toc__anchor">animation-iteration-count</a>
    -   <a href="#animation-direction" class="toc__anchor">animation-direction</a>
    -   <a href="#animation-delay" class="toc__anchor">animation-delay</a>
    -   <a href="#animation-play-state" class="toc__anchor">animation-play-state</a>
    -   <a href="#animation-fill-mode" class="toc__anchor">animation-fill-mode</a>
    -   <a href="#the-animation-shorthand" class="toc__anchor">The animation shorthand</a>
-   <a href="#considerations-when-working-with-animation" class="toc__anchor">Considerations when working with animation</a>

021

Animations
==========

Animation is a great way to highlight interactive elements, and add interest and fun to your designs. In this module find out how to add and control animation effects with CSS.

On this page

-   <a href="#what-is-a-keyframe" class="toc__anchor">What is a keyframe?</a>
    -   <a href="#@keyframes" class="toc__anchor">@keyframes</a>
-   <a href="#the-animation-properties" class="toc__anchor">The animation properties</a>
    -   <a href="#animation-duration" class="toc__anchor">animation-duration</a>
    -   <a href="#animation-timing-function" class="toc__anchor">animation-timing-function</a>
    -   <a href="#animation-iteration-count" class="toc__anchor">animation-iteration-count</a>
    -   <a href="#animation-direction" class="toc__anchor">animation-direction</a>
    -   <a href="#animation-delay" class="toc__anchor">animation-delay</a>
    -   <a href="#animation-play-state" class="toc__anchor">animation-play-state</a>
    -   <a href="#animation-fill-mode" class="toc__anchor">animation-fill-mode</a>
    -   <a href="#the-animation-shorthand" class="toc__anchor">The animation shorthand</a>
-   <a href="#considerations-when-working-with-animation" class="toc__anchor">Considerations when working with animation</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 022: Animation

Sometimes you see little helpers on interfaces that when clicked, provide some helpful information about that particular section. These often have a pulsing animation to subtly let you know that the information is there and should be interacted with. How do you do this with CSS though?

In CSS, you can make this type of animation using CSS animations, which allow you to set an animation sequence, using keyframes. Animations can be simple, one state animations, or even complex, time-based sequences.

What is a keyframe? <a href="#what-is-a-keyframe" class="w-headline-link">#</a>
-------------------------------------------------------------------------------

In animation software, CSS, and most other tools that enable you to animate something, keyframes are the mechanism that you use to assign animation states to timestamps, along a timeline.

Let's use the "pulser" as a context for this. The entire animation runs for 1 second and runs over 2 states.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/pWCGpgzJqJNTBluK5u8S.svg" alt="The states of the pulser animation over the 1 second timeframe" width="800" height="340" />

There's a specific point where each of these animation states start and end. You map these out on the timeline with keyframes.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/wmKVq5GFj7cf6jfuLiT8.svg" alt="The same diagram as before, but this time, with keyframes" width="800" height="440" />

### `@keyframes` <a href="#@keyframes" class="w-headline-link">#</a>

Now you know what a keyframe is, that knowledge should help you understand how the CSS [`@keyframes`](https://developer.mozilla.org/en-US/docs/Web/CSS/@keyframes) rule works. Here is a basic rule with two states.

    @keyframes my-animation {
      from {
           transform: translateY(20px);
        }
        to {
         transform: translateY(0px);
     }
    }

The first part to note is the [custom ident](https://developer.mozilla.org/en-US/docs/Web/CSS/custom-ident) (custom identifier)—or in more human terms, the name of the keyframes rule. This rule's identifier is `my-animation`. The custom identifier works like a function name. Which, as you learned in the [functions module](/learn/css/functions), lets you reference the keyframes rule elsewhere in your CSS code.

A `<custom-ident>` is used in various places in CSS, and allows you to provide your own name for things. These identifiers are case-sensitive, and in some cases there are words that you can't use. For example, when naming lines in CSS Grid, you can't use the word `span`.

Inside the keyframes rule, `from` and `to` are keywords that represent `0%` and `100%`, which are the start of the animation and end. You could re-create the same rule like this:

    @keyframes my-animation {
       0% {
         transform: translateY(20px);
        }
        100% {
           transform: translateY(0px);
     }
    }

You can add as many positions as you like along the timeframe. Using the context of the "pulser" example, there are 2 states, which translate to 2 keyframes. This means you have 2 positions inside your keyframes rule to represent the changes for each of these keyframes.

    @keyframes pulse {
      0% {
        opacity: 0;
      }
      50% {
        transform: scale(1.4);
        opacity: 0.4;
      }
    }

The `animation` properties <a href="#the-animation-properties" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

To use your `@keyframes` in a CSS rule, define various animation properties *or*, use the [`animation`](https://developer.mozilla.org/en-US/docs/Web/CSS/animation) shorthand property.

### `animation-duration` <a href="#animation-duration" class="w-headline-link">#</a>

    .my-element {
     animation-duration: 10s;
    }

The [animation-duration](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-duration) property defines how long the `@keyframes` timeline should be. It should be a time value. It defaults to 0 seconds, which means the animation still runs, but it'll be too quick for you to see. You can't add negative time values.

### `animation-timing-function` <a href="#animation-timing-function" class="w-headline-link">#</a>

To help recreate natural motion in animation, you can use timing functions that calculate the speed of an animation at each point. Calculated values are often *curved*, making the animation run at variable speeds over the course of `animation-duration`, and if a value is calculated beyond that of the value defined in `@keyframes`, make the element appear to bounce.

There are several keywords available as presets in CSS, which are used as the value for [animation-timing-function](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-timing-function): `linear`, `ease`, `ease-in`, `ease-out`, `ease-in-out`.

    .my-element {
     animation-timing-function: ease-in-out;
    }

Values appear to curve with easing functions because easing is calculated using a **bézier curve**, which is used to model velocity. Each of the timing function keywords, such as `ease`, reference a pre-defined bézier curve. In CSS, you can define a bézier curve directly, using the `cubic-bezier()` function, which accepts four number values: `x1`, `y1`, `x2`, `y2`.

    .my-element {
      animation-timing-function: cubic-bezier(.42, 0, .58, 1);
    }

These values plot each part of the curve along the X and Y axis.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/AZr17k5ejTYsikAPiwTm.svg" alt="A bézier on a progression vs time chart" width="800" height="499" />

Understanding bézier curves is complicated and visual tools, such as [this generator by Lea Verou](https://cubic-bezier.com/) are very helpful.

#### The `steps` easing function <a href="#the-steps-easing-function" class="w-headline-link">#</a>

Sometimes you might want more granular control of your animation, and instead of moving along a curve, you want to move in intervals instead. The `steps()` easing function lets you break the timeline into defined, **equal intervals**.

    .my-element {
     animation-timing-function: steps(10, end);
    }

The first argument is how many steps. If steps are defined as 10 and there are 10 keyframes, each keyframe will play in sequence for the exact amount of time, with no transition between states. If there are not enough keyframes for the steps, steps between keyframes are added depending on the second argument.

The second argument is the direction. If it's set to `end`, which is the default, the steps finish at the end of your timeline. If it is set to `start`, the first step of your animation completes as soon as it starts, which means it ends one step earlier than `end`.

### `animation-iteration-count` <a href="#animation-iteration-count" class="w-headline-link">#</a>

    .my-element {
     animation-iteration-count: 10;
    }

The [animation-iteration-count](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-iteration-count) property defines how many times the `@keyframes` timeline should run. By default, this is 1, which means that when the animation reaches the end of your timeline, it will stop at the end. The number can't be a negative number.

You can use the `infinite` keyword which will loop your animation, which is how the "pulser" demo from the start of this lesson works.

### `animation-direction` <a href="#animation-direction" class="w-headline-link">#</a>

    .my-element {
      animation-direction: reverse;
    }

You can set which direction the timeline runs over your keyframes with [animation-direction](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-direction):

-   `normal`: the default value, which is forwards.
-   `reverse`: runs backwards over your timeline.
-   `alternate`: for each animation iteration, the timeline will run forwards or backwards in sequence.
-   `alternate-reverse`: the reverse of `alternate`.

### `animation-delay` <a href="#animation-delay" class="w-headline-link">#</a>

    .my-element {
     animation-delay: 5s;
    }

The [animation-delay](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-delay) property defines how long to wait before starting the animation. Like the `animation-duration` property, this accepts a time value.

Unlike the `animation-duration` property, you *can* define this as a negative value. If you set a negative value, the timeline in your `@keyframes` will start at that point. For example, if your animation is 10 seconds long and you set `animation-delay` to `-5s`, it will start from half-way along your timeline.

### `animation-play-state` <a href="#animation-play-state" class="w-headline-link">#</a>

    .my-element:hover {
       animation-play-state: paused;
    }

The [animation-play-state](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-play-state) property allows you to play and pause the animation. The default value is `running` and if you set it to `paused`, it will pause the animation.

### `animation-fill-mode` <a href="#animation-fill-mode" class="w-headline-link">#</a>

The [animation-fill-mode](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-fill-mode) property defines which values in your `@keyframes` timeline persist before the animation starts or after it ends. The default value is `none` which means when the animation is complete, the values in your timeline are discarded. Other options are:

-   `forwards`: The last keyframe will persist, based on the animation direction.
-   `backwards`: The first keyframe will persist, based on the animation direction.
-   `both`: follows the rules for both `forwards` and `backwards`.

### The `animation` shorthand <a href="#the-animation-shorthand" class="w-headline-link">#</a>

Instead of defining all the properties separately, you can define them in an `animation` shorthand, which lets you define the animation properties in the following order:

1.  `animation-name`
2.  `animation-duration`
3.  `animation-timing-function`
4.  `animation-delay`
5.  `animation-iteration-count`
6.  `animation-direction`
7.  `animation-fill-mode`
8.  `animation-play-state`

<!-- -->

    .my-element {
     animation: my-animation 10s ease-in-out 1s infinite forwards forwards running;
    }

Considerations when working with animation <a href="#considerations-when-working-with-animation" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------

Users can define in their operating system that they prefer to reduce motion experienced when they interact with applications and websites. This preference can be detected using the [prefers-reduced-motion](https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-reduced-motion) media query.

    @media (prefers-reduced-motion) {
      .my-autoplaying-animation {
        animation-play-state: paused;
      }
    }

This isn't necessarily a preference of no animation, but rather, a preference to reduce animations— [especially unexpected ones](/prefers-reduced-motion/). You can learn more about this preference and overall performance with [this animation guide](https://web.dev/animations/).

Test your knowledge of animations

The **name or custom identifier** of a `@keyframes` animation is case sensitive?

<span data-role="option">True</span> <span data-role="option">False</span>

🎉

CSS does not allow 2 animations to have the same name, but it does allow `SWOOP` and `swoop` to coexist.

The keywords `from` and `to` are the same as

<span data-role="option">`start` and `end`.</span> <span data-role="option">`0%` and `100%`.</span> <span data-role="option">`0` and `1`</span>

Try again!

`from` is the same as `0%` and `to` is the same as 100%.

Try again!

The `animation-timing-function` is also commonly known as

<span data-role="option">Dynamic timing</span> <span data-role="option">Delay</span> <span data-role="option">Easing</span>

Try again!

Try again!

🎉

What is the minimum number of keyframes required inside a `@keyframes` animation?

<span data-role="option">1</span> <span data-role="option">2</span> <span data-role="option">3</span> <span data-role="option">4</span>

The browser will take the current state of the element as a keyframe, so at minimum, 1 keyframe is required.

Try again!

Try again!

Try again!

<a href="/learn/css/gradients/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">020</span>

Gradients

<a href="/learn/css/filters/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">022</span>

Filters

Filters in CSS mean that you can apply effects you might only think possible in a graphics application. In this module, you can discover what is available.

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
