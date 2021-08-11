<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#applying-the-mini-app-programming-principles-to-an-example-project" class="w-toc__header--link">Applying the mini app programming principles to an example project</a>
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [The app domain](#the-app-domain)
-   [HIIT Time example app](#hiit-time-example-app)
-   [App structure](#app-structure)
-   [Components-based lit-html markup](#components-based-lit-html-markup)
-   [Programming model](#programming-model)
-   [Styling](#styling)
-   [Screen wake lock](#screen-wake-lock)
-   [Testing the application](#testing-the-application)
-   [Acknowledgements](#acknowledgements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Applying the mini app programming principles to an example project
==================================================================

Mar 3, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/mini-apps" class="w-post-signpost__link">Mini apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

-   <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
-   <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
-   <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

This post is part of an article collection where each article builds upon previous articles. If you just landed here, you may want to start reading from the [beginning](/mini-app-super-apps/).

The app domain <a href="#the-app-domain" class="w-headline-link">#</a>
----------------------------------------------------------------------

To show the [mini app way of programming](/mini-app-programming-way/) applied to a web app, I needed a small but complete enough app idea. [High-intensity interval training](https://en.wikipedia.org/wiki/High-intensity_interval_training) (HIIT) is a cardiovascular exercise strategy of alternating sets of short periods of intense anaerobic exercise with less intense recovery periods. Many HIIT trainings use HIIT timers, for example, this [30 minute online session](https://www.youtube.com/watch?v=tXOZS3AKKOw) from [The Body Coach TV](https://www.youtube.com/user/thebodycoach1) YouTube channel.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format" alt="Active period." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tUl2jNm2bFqGBAFF5s63.png?auto=format&amp;w=1600 1600w" width="800" height="450" /><figcaption>Active period.</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format" alt="Resting period." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FMUgX3WJ4ZfQX38zHP75.png?auto=format&amp;w=1600 1600w" width="800" height="450" /><figcaption>Resting period.</figcaption></figure>

HIIT Time example app <a href="#hiit-time-example-app" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

For this chapter, I have built a basic example of such a HIIT timer application aptly named "HIIT Time" that lets the user define and manage various timers, always consisting of a high and a low intensity interval, and then select one of them for a training session. It is a responsive app with a navbar, a tabbar, and three pages:

-   **Workout:** The active page during a workout. It lets the user select one of the timers and features three progress rings: the number of sets, the active period, and the resting period.
-   **Timers:** Manages existing timers and lets the user create new ones.
-   **Preferences:** Allows toggling sound effects and speech output and selecting language and theme.

The following screenshots give an impression of the application.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9RYkQ17tlEy79NlAIFfP.svg" alt="HIIT Time &quot;Workout&quot; tab in portrait mode." width="800" height="450" /><figcaption>HIIT Time "Workout" tab in portrait mode.</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/SNHMWFvHtCYHEfC9SHPl.svg" alt="HIIT Time &quot;Workout&quot; tab in landscape mode." width="800" height="450" /><figcaption>HIIT Time "Workout" tab in landscape mode.</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/f7uqTk1PNMVaHob7FDzA.svg" alt="HIIT Time timer management." width="800" height="450" /><figcaption>HIIT Time timer management.</figcaption></figure>App structure <a href="#app-structure" class="w-headline-link">#</a>
--------------------------------------------------------------------

As outlined above, the app consists of a navbar, a tabbar, and three pages, arranged in a grid. Navbar and tabbar are realized as iframes with a `<div>` container in between them with three more iframes for the pages, out of which one is always visible and dependent on the active selection in the tabbar. A final iframe pointing to `about:blank` serves for dynamically created in-app pages, which are needed for modifying existing timers or creating new ones. I call this pattern multi-page single-page app (MPSPA).

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format" alt="The app consists of six iframes." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Rv14TNs1kU0bpW5kv5bq.png?auto=format&amp;w=1600 1600w" width="800" height="244" /><figcaption>The app consists of six iframes.</figcaption></figure>Components-based lit-html markup <a href="#components-based-lit-html-markup" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------

The structure of each page is realized as [lit-html](https://lit-html.polymer-project.org/) scaffold that gets dynamically evaluated at runtime. For a background on lit-html, it is an efficient, expressive, extensible HTML templating library for JavaScript. By using it directly in the HTML files, the mental programming model is directly output-oriented. As a programmer, you write a template of what the final output will look like, and lit-html then fills the gaps dynamically based on your data and hooks up the event listeners. The app makes use of third-party custom elements like [Shoelace](https://shoelace.style/)'s [`<sl-progress-ring>`](https://shoelace.style/components/progress-ring) or a self-implemented custom element called `<human-duration>`. Since custom elements have a declarative API (for example, the `percentage` attribute of the progress ring), they work well together with lit-html, as you can see in the listing below.

    <div>
      <button class="start" @click="${eventHandlers.start}" type="button">
        ${strings.START}
      </button>
      <button class="pause" @click="${eventHandlers.pause}" type="button">
        ${strings.PAUSE}
      </button>
      <button class="reset" @click="${eventHandlers.reset}" type="button">
        ${strings.RESET}
      </button>
    </div>

    <div class="progress-rings">
      <sl-progress-ring
        class="sets"
        percentage="${Math.floor(data.sets/data.activeTimer.sets*100)}"
      >
        <div class="progress-ring-caption">
          <span>${strings.SETS}</span>
          <span>${data.sets}</span>
        </div>
      </sl-progress-ring>
    </div>

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format" alt="Rendered section of the page corresponding to the mark-up above." sizes="(min-width: 300px) 300px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/Toz6JmkCQVt7WLscSnlP.png?auto=format&amp;w=600 600w" width="300" height="244" /><figcaption>Rendered section of the page corresponding to the mark-up above.</figcaption></figure>Programming model <a href="#programming-model" class="w-headline-link">#</a>
----------------------------------------------------------------------------

Each page has a corresponding `Page` class that fills the lit-html markup with life by providing implementations of the event handlers and providing the data for each page. This class also supports lifecycle methods like `onShow()`, `onHide()`, `onLoad()`, and `onUnload()`. Pages have access to a data store that serves for sharing optionally persisted per-page state and global state. All strings are centrally managed, so internationalization is built in. Routing is handled by the browser essentially for free, since all the app does is toggle iframe visibility and for dynamically created pages change the `src` attribute of the placeholder iframe. The example below shows the code for closing a dynamically created page.

    import Page from '../page.js';

    const page = new Page({
      eventHandlers: {
        back: (e) => {
          e.preventDefault();
          window.top.history.back();
        },
      },
    });

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format" alt="Navigation happens from iframe to iframe." sizes="(min-width: 500px) 500px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/y82LVHSxUVAehgQlDbsb.png?auto=format&amp;w=1000 1000w" width="500" height="272" /><figcaption>Navigation happens from iframe to iframe.</figcaption></figure>Styling <a href="#styling" class="w-headline-link">#</a>
--------------------------------------------------------

Styling of pages happens per-page in its own scoped CSS file. This means elements can usually just be directly addressed by their element names, since no clashes with other pages can occur. Global styles are added to each page, so central settings like the `font-family` or the `box-sizing` do not need to be declared repeatedly. This is also where the themes and dark mode options are defined. The listing below shows the rules for the Preferences page that lays out the various form elements on a grid.

    main {
      max-width: 600px;
    }

    form {
      display: grid;
      grid-template-columns: auto 1fr;
      grid-gap: 0.5rem;
      margin-block-end: 1rem;
    }

    label {
      text-align: end;
      grid-column: 1 / 2;
    }

    input,
    select {
      grid-column: 2 / 3;
    }

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format" alt="Every page is its own world. Styling happens directly with the element names." sizes="(min-width: 500px) 500px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/z3Op4O7OM5NQ1zz8Uah8.png?auto=format&amp;w=1000 1000w" width="500" height="312" /><figcaption>Every page is its own world. Styling happens directly with the element names.</figcaption></figure>Screen wake lock <a href="#screen-wake-lock" class="w-headline-link">#</a>
--------------------------------------------------------------------------

During a workout, the screen should not turn off. On browsers that support it, HIIT Time realizes this through a [screen wake lock](/wake-lock/). The snippet below shows how it is done.

    if ('wakeLock' in navigator) {
      const requestWakeLock = async () => {
        try {
          page.shared.wakeLock = await navigator.wakeLock.request('screen');
          page.shared.wakeLock.addEventListener('release', () => {
            // Nothing.
          });
        } catch (err) {
          console.error(`${err.name}, ${err.message}`);
        }
      };
      // Request a screen wake lock…
      await requestWakeLock();
      // …and re-request it when the page becomes visible.
      document.addEventListener('visibilitychange', async () => {
        if (
          page.shared.wakeLock !== null &&
          document.visibilityState === 'visible'
        ) {
          await requestWakeLock();
        }
      });
    }

Testing the application <a href="#testing-the-application" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

The HIIT Time application is available on [GitHub](https://github.com/tomayac/hiit-time). You can play with the [demo](https://tomayac.github.io/hiit-time/) in a new window, or right in the iframe embed below, which simulates a mobile device.

**Success**: The final chapter ends this collection on mini apps with a [conclusion](/mini-app-conclusion).

Acknowledgements <a href="#acknowledgements" class="w-headline-link">#</a>
--------------------------------------------------------------------------

This article was reviewed by [Joe Medley](https://github.com/jpmedley), [Kayce Basques](https://github.com/kaycebasques), [Milica Mihajlija](https://github.com/mihajlija), [Alan Kent](https://github.com/alankent), and Keith Gu.

<a href="/tags/mini-apps/" class="w-chip">Mini apps</a>

<span class="w-mr--sm">Last updated: Mar 3, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/mini-apps/mini-app-example-project/index.md)

<a href="/mini-apps" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
