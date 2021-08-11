<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#examples-of-high-performance-css-animations" class="w-toc__header--link">Examples of high-performance CSS animations</a>

- [Wizard loading animation](#wizard-loading-animation)
- [Inspect the animation with Chrome DevTools](#inspect-the-animation-with-chrome-devtools)
- [How it works](#how-it-works)
- [Pulsating Circle](#pulsating-circle)
- [Inspect the animation with Firefox DevTools](#inspect-the-animation-with-firefox-devtools)
- [Pure CSS 3D Sphere](#pure-css-3d-sphere)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Examples of high-performance CSS animations

Oct 23, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/animations" class="w-post-signpost__link">Animations</a>

[<img src="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Rachel Andrew" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/dUAN2DEXHRT6G6iPrIby.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/rachelandrew/)

<a href="/authors/rachelandrew/" class="w-author__name-link">Rachel Andrew</a>

- <a href="https://twitter.com/rachelandrew" class="w-author__link">Twitter</a>
- <a href="https://github.com/rachelandrew" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@rachelandrew" class="w-author__link">Glitch</a>
- <a href="https://rachelandrew.co.uk/" class="w-author__link">Blog</a>

In this post find out how some popular animations found on CodePen have been created. These animations all use the performant techniques discussed in other articles in this section.

See [Why are some animations slow?](/animations-overview/) to learn the theory behind these recommendations, and the [Animations Guide](/animations-guide) for practical tips.

## Wizard loading animation <a href="#wizard-loading-animation" class="w-headline-link">#</a>

[View Wizard loading animation on CodePen](https://codepen.io/Craaftx/full/ExyYRMK)

This loading animation is built entirely with CSS. The image plus all of the animation has been created in CSS and HTML, no images or JavaScript. To understand how it was created and how well it performs you can use Chrome DevTools.

### Inspect the animation with Chrome DevTools <a href="#inspect-the-animation-with-chrome-devtools" class="w-headline-link">#</a>

With the animation running, open the Performance tab in Chrome DevTools and record a few seconds of the animation. You should see in the Summary that the browser is not doing any Layout or Paint operations when running this animation.

<figure><img src="https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format" alt="The summary after profiling the wizard animation." sizes="(min-width: 724px) 724px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/r1h4gb24ZiYXAfI7Mskh.jpg?auto=format&amp;w=1448 1448w" width="724" height="416" /><figcaption>The summary after profiling the wizard animation.</figcaption></figure>To find out how this animation was achieved without causing layout and paint, inspect any of the moving elements in Chrome DevTools. You can use the **Animations Panel** to locate the various animated elements, clicking on any element will highlight it in the DOM.

<figure><img src="https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format" alt="Viewing and selecting items in the Chrome DevTools Animation Panel." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/sPoemcfld1jfUkSFhv3o.jpg?auto=format&amp;w=1600 1600w" width="800" height="349" /><figcaption>Viewing and selecting items in the Chrome DevTools Animation Panel.</figcaption></figure>For example select the triangle, and watch how the box of the element transforms during its journey into the air, as it spins, and then returns to the start position.

Video showing how we can track the path of the triangle in Chrome DevTools.

With the element still selected look at the Styles Panel. There you can see the CSS which draws the shape of the triangle, and the animation being used.

### How it works <a href="#how-it-works" class="w-headline-link">#</a>

The triangle is created by using the `::after` pseudo-element to add generated content, using borders to create the shape.

    .triangle {
        position: absolute;
        bottom: -62px;
        left: -10px;
        width: 110px;
        height: 110px;
        border-radius: 50%;
    }

    .triangle::after {
        content: "";
        position: absolute;
        top: 0;
        right: -10px;
        width: 0;
        height: 0;
        border-style: solid;
        border-width: 0 28px 48px 28px;
        border-color: transparent transparent #89beb3 transparent;
    }

You can find out more about making shapes with borders and generated content in [The Shapes of CSS](https://css-tricks.com/the-shapes-of-css/).

The animation is added with the following line of CSS,

    animation: path_triangle 10s ease-in-out infinite;

Staying in Chrome DevTools you can find the keyframes by scrolling down the Style Panel. There you will find that the animation is created by using `transform` to change the position of the element and rotate it. The `transform` property is one of the properties described in the [Animations Guide](/animations-guide), which does not cause the browser to do layout or paint operations (which are the main causes of slow animations).

    @keyframes path_triangle {
      0% {
        transform: translateY(0);
      }
      10% {
        transform: translateY(-172px) translatex(10px) rotate(-10deg);
      }
      55% {
        transform: translateY(-172px) translatex(10px) rotate(-365deg);
      }
      58% {
        transform: translateY(-172px) translatex(10px) rotate(-365deg);
      }
      63% {
        transform: rotate(-360deg);
      }
    }

Each of the different moving parts of this animation uses similar techniques. The result is a complex animation which runs smoothly.

## Pulsating Circle <a href="#pulsating-circle" class="w-headline-link">#</a>

[View Pulsating Circle on CodePen](https://codepen.io/peeke/full/BjxXZa)

This type of animation is sometimes used to draw attention to something on a page. To understand the animation you can use Firefox DevTools.

### Inspect the animation with Firefox DevTools <a href="#inspect-the-animation-with-firefox-devtools" class="w-headline-link">#</a>

With the animation running, open the Performance tab in Firefox DevTools and record a few seconds of the animation. Stop the recording, in the waterfall you should see that there are no entries for **Recalculate Style**. You now know that this animation does not cause style recalculation, and therefore layout and paint operations.

<figure><img src="https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format" alt="The Firefox DevTools Waterfall." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/68jWlrbNhgmS07vrXMCO.jpg?auto=format&amp;w=1600 1600w" width="800" height="354" /><figcaption>The Firefox DevTools Waterfall.</figcaption></figure>Staying in Firefox DevTools inspect the circle to see how this animation works. The `<div>` with a class of `pulsating-circle` marks the position of the circle, however it does not draw a circle itself.

    .pulsating-circle {
        position: absolute;
        left: 50%;
        top: 50%;
        transform: translateX(-50%) translateY(-50%);
        width: 30px;
        height: 30px;
    }

The visible circle and animations are achieved using the `::before` and `::after` pseudo-elements.

The `::before` element creates the opaque ring that extends outside of the white circle, using an animation called `pulse-ring`, which animates `transform: scale`, and `opacity`.

    .pulsating-circle::before {
        content: '';
        position: relative;
        display: block;
        width: 300%;
        height: 300%;
        box-sizing: border-box;
        margin-left: -100%;
        margin-top: -100%;
        border-radius: 45px;
        background-color: #01a4e9;
        animation: pulse-ring 1.25s cubic-bezier(0.215, 0.61, 0.355, 1) infinite;
    }

    @keyframes pulse-ring {
      0% {
        transform: scale(0.33);
      }
      80%, 100% {
        opacity: 0;
      }
    }

Another way to see which properties are being animated is to select the **Animations** panel in Firefox DevTools. You will then see a visualization of the animations being used, and the properties that are being animated.

With the ::before pseudo-element selected we can see which properties are animating.

The white circle itself is created and animated using the `::after` pseudo-element. The animation `pulse-dot` uses `transform: scale` to grow and shrink the dot during the animation.

    .pulsating-circle::after {
      content: '';
      position: absolute;
      left: 0;
      top: 0;
      display: block;
      width: 100%;
      height: 100%;
      background-color: white;
      border-radius: 15px;
      box-shadow: 0 0 8px rgba(0, 0, 0, 0.3);
      animation: pulse-dot 1.25s cubic-bezier(0.455, 0.03, 0.515, 0.955) -0.4s infinite;
    }

    @keyframes pulse-dot {
      0% {
        transform: scale(0.8);
      }
      50% {
        transform: scale(1);
      }
      100% {
        transform: scale(0.8);
      }
    }

An animation like this could be used in various places in your application, it's important that these small touches don't impact the overall performance of your app.

## Pure CSS 3D Sphere <a href="#pure-css-3d-sphere" class="w-headline-link">#</a>

[View Pure CSS 3D Sphere on CodePen](https://codepen.io/iamlark/full/jYzYJg)

This animation seems incredibly complicated, however it uses techniques that we have already seen in the previous examples. The complexity comes from animating a large number of elements.

Open Chrome DevTools and select one of the elements with a class of `plane`. The sphere is made up of a set of rotating planes and spokes.

The plane appears to be rotating.

The [DOM Search Tool](https://developers.google.com/web/tools/chrome-devtools/dom#search) in Chrome DevTools can make it easier to find an element that you want to inspect.

These planes and spokes are inside a wrapper `<div>`, and it is this element which is rotating using `transform: rotate3d`.

    .sphere-wrapper {
      transform-style: preserve-3d;
      width: 300px;
      height: 300px;
      position: relative;
      animation: rotate3d 10s linear infinite;
    }

    @keyframes rotate3d {
      0% {
        transform: rotate3d(1, 1, 1, 0deg);
      }
      25% {
        transform: rotate3d(1, 1, 1, 90deg);
      }
      50% {
        transform: rotate3d(1, 1, 1, 180deg);
      }
      75% {
        transform: rotate3d(1, 1, 1, 270deg);
      }
      100% {
        transform: rotate3d(1, 1, 1, 360deg);
      }
    }

The dots can be found nested inside the `plane` and `spoke` elements, they use an animation which uses transform to scale and translate them. This creates the pulsing effect.

The dot rotates with the sphere and pulses.

    .spoke-15 .dot,
    .spoke-21 .dot {
      animation: pulsate 0.5s infinite 0.83333333s alternate both;
      background-color: #55ffee;
    }

    @-webkit-keyframes pulsate {
      0% {
        transform: rotateX(90deg) scale(0.3) translateZ(20px);
      }
      100% {
        transform: rotateX(90deg) scale(1) translateZ(0px);
      }
    }

The work involved in creating this animation has been to get the timing right, to create the turning and pulsing effect. The animations themselves are quite straightforward, and use methods which perform very well.

You can see how this animation performs by opening Chrome DevTools and recording Performance while it is running. After the initial load, the animation is not triggering Layout or Paint, and runs smoothly.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

From these examples you can see how animating a few properties using performant methods can create some very cool animations. By defaulting to the performant methods described in the [Animations guide](/animations-guide) you can spend your time creating the effect you want, with fewer concerns about making the page slow.

<a href="/tags/animations/" class="w-chip">Animations</a> <a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Oct 23, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/animations/animations-examples/index.md)

<a href="/animations" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
