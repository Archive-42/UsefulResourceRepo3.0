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

- <a href="#overview" class="toc__anchor">Overview</a>
- <a href="#grid-terminology" class="toc__anchor">Grid terminology</a>
  - <a href="#grid-lines" class="toc__anchor">Grid lines</a>
  - <a href="#grid-tracks" class="toc__anchor">Grid tracks</a>
  - <a href="#grid-cell" class="toc__anchor">Grid cell</a>
  - <a href="#grid-area" class="toc__anchor">Grid area</a>
  - <a href="#gaps" class="toc__anchor">Gaps</a>
  - <a href="#grid-container" class="toc__anchor">Grid container</a>
  - <a href="#grid-item" class="toc__anchor">Grid item</a>
- <a href="#rows-and-columns" class="toc__anchor">Rows and columns</a>
  - <a href="#intrinsic-sizing-keywords" class="toc__anchor">Intrinsic sizing keywords</a>
  - <a href="#the-fr-unit" class="toc__anchor">The fr unit</a>
  - <a href="#the-minmax()-function" class="toc__anchor">The minmax() function</a>
  - <a href="#repeat()-notation" class="toc__anchor">repeat() notation</a>
  - <a href="#auto-fill-and-auto-fit" class="toc__anchor">auto-fill and auto-fit</a>
- <a href="#auto-placement" class="toc__anchor">Auto-placement</a>
  - <a href="#placing-items-in-columns" class="toc__anchor">Placing items in columns</a>
  - <a href="#spanning-tracks" class="toc__anchor">Spanning tracks</a>
  - <a href="#filling-gaps" class="toc__anchor">Filling gaps</a>
- <a href="#placing-items" class="toc__anchor">Placing items</a>
  - <a href="#stacking-items" class="toc__anchor">Stacking items</a>
  - <a href="#negative-line-numbers" class="toc__anchor">Negative line numbers</a>
- <a href="#named-grid-lines" class="toc__anchor">Named grid lines</a>
- <a href="#grid-template-areas" class="toc__anchor">Grid Template Areas</a>
- <a href="#shorthand-properties" class="toc__anchor">Shorthand properties</a>
  - <a href="#grid-template" class="toc__anchor">grid-template</a>
  - <a href="#grid-property" class="toc__anchor">grid property</a>
- <a href="#alignment" class="toc__anchor">Alignment</a>
  - <a href="#distributing-extra-space" class="toc__anchor">Distributing extra space</a>
  - <a href="#moving-content-around" class="toc__anchor">Moving content around</a>
- <a href="#resources" class="toc__anchor">Resources</a>

010

# Grid

CSS Grid Layout provides a two dimensional layout system, controlling layout in rows and columns. In this module discover everything grid has to offer.

On this page

- <a href="#overview" class="toc__anchor">Overview</a>
- <a href="#grid-terminology" class="toc__anchor">Grid terminology</a>
  - <a href="#grid-lines" class="toc__anchor">Grid lines</a>
  - <a href="#grid-tracks" class="toc__anchor">Grid tracks</a>
  - <a href="#grid-cell" class="toc__anchor">Grid cell</a>
  - <a href="#grid-area" class="toc__anchor">Grid area</a>
  - <a href="#gaps" class="toc__anchor">Gaps</a>
  - <a href="#grid-container" class="toc__anchor">Grid container</a>
  - <a href="#grid-item" class="toc__anchor">Grid item</a>
- <a href="#rows-and-columns" class="toc__anchor">Rows and columns</a>
  - <a href="#intrinsic-sizing-keywords" class="toc__anchor">Intrinsic sizing keywords</a>
  - <a href="#the-fr-unit" class="toc__anchor">The fr unit</a>
  - <a href="#the-minmax()-function" class="toc__anchor">The minmax() function</a>
  - <a href="#repeat()-notation" class="toc__anchor">repeat() notation</a>
  - <a href="#auto-fill-and-auto-fit" class="toc__anchor">auto-fill and auto-fit</a>
- <a href="#auto-placement" class="toc__anchor">Auto-placement</a>
  - <a href="#placing-items-in-columns" class="toc__anchor">Placing items in columns</a>
  - <a href="#spanning-tracks" class="toc__anchor">Spanning tracks</a>
  - <a href="#filling-gaps" class="toc__anchor">Filling gaps</a>
- <a href="#placing-items" class="toc__anchor">Placing items</a>
  - <a href="#stacking-items" class="toc__anchor">Stacking items</a>
  - <a href="#negative-line-numbers" class="toc__anchor">Negative line numbers</a>
- <a href="#named-grid-lines" class="toc__anchor">Named grid lines</a>
- <a href="#grid-template-areas" class="toc__anchor">Grid Template Areas</a>
- <a href="#shorthand-properties" class="toc__anchor">Shorthand properties</a>
  - <a href="#grid-template" class="toc__anchor">grid-template</a>
  - <a href="#grid-property" class="toc__anchor">grid property</a>
- <a href="#alignment" class="toc__anchor">Alignment</a>
  - <a href="#distributing-extra-space" class="toc__anchor">Distributing extra space</a>
  - <a href="#moving-content-around" class="toc__anchor">Moving content around</a>
- <a href="#resources" class="toc__anchor">Resources</a>

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="web-audio-fab__thumbnail" sizes="(min-width: 56px) 56px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=56 56w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=64 64w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=73 73w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=83 83w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=95 95w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=108 108w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=112 112w" width="56" height="56" />

<img src="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format" class="audio-player__thumbnail" sizes="(min-width: 80px) 80px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=80 80w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=91 91w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=104 104w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=119 119w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=135 135w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=154 154w, https://web-dev.imgix.net/image/foR0vJZKULb5AGJExlazy1xYDgI2/ECDb0qa4TB7yUsHwBic8.png?auto=format&amp;w=160 160w" width="80" height="80" />

The CSS Podcast - 011: Grid

A really common layout in web design is a header, sidebar, body and footer layout.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/tj7KmP72RKkffGQRswpA.svg" alt="A header with logo and navigation with a sidebar and content area that features an article" width="800" height="531" />

Over the years, there have been many methods to solve this layout, but with CSS grid, not only is it relatively straightforward, but you have lots of options. Grid is exceptionally useful at combining the control that extrinsic sizing provides with the flexibility of intrinsic sizing, which makes it ideal for this sort of layout. This is because grid is a layout method designed for two-dimensional content. That is, laying things out in rows and columns at the same time.

When creating a grid layout you define a grid with rows and columns. Then you place items onto that grid, or allow the browser to auto-place them into the cells you have created. There's a lot to grid, but with an overview of what is available you'll be making grid layouts in no time.

## Overview <a href="#overview" class="w-headline-link">#</a>

So what can you do with grid? Grid layouts have the following features. You'll learn about all of them in this guide.

1.  A grid can be defined with rows and columns. You can choose how to size these row and column tracks or they can react to the size of the content.
2.  Direct children of the grid container will be automatically placed onto this grid.
3.  Or, you can place the items in the precise location that you want.
4.  Lines and areas on the grid can be named to make placement easier.
5.  Spare space in the grid container can be distributed between the tracks.
6.  Grid items can be aligned within their area.

## Grid terminology <a href="#grid-terminology" class="w-headline-link">#</a>

Grid comes with a bunch of new terminology as it's the first time CSS has had a real layout system.

### Grid lines <a href="#grid-lines" class="w-headline-link">#</a>

A grid is made up of lines, which run horizontally and vertically. If your grid has three columns, it will have four column lines including the one after the last column.

Lines are numbered starting from 1, with the numbering following the writing mode and script direction of the component. This means that column line 1 will be on the left in a left-to-right language such as English, and on the right in a right-to-left language such as Arabic.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Sf8WXYmbhZkbhhPeqTrY.svg" alt="A diagram representation of grid lines" width="800" height="434" />

### Grid tracks <a href="#grid-tracks" class="w-headline-link">#</a>

A track is the space between two grid lines. A row track is between two row lines and a column track between two column lines. When we create our grid we create these tracks by assigning a size to them.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/7YkhnpgOQLrcaxjlKmlU.svg" alt="A diagram representation of a grid track" width="800" height="434" />

### Grid cell <a href="#grid-cell" class="w-headline-link">#</a>

A grid cell is the smallest space on a grid defined by the intersection of row and column tracks. It's just like a table cell or a cell in a spreadsheet. If you define a grid and don't place any of the items they will automatically be laid out one item into each defined grid cell.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/lpiPCpW6fy4BjFOL6j77.svg" alt="A diagram representation of a grid cell" width="800" height="434" />

### Grid area <a href="#grid-area" class="w-headline-link">#</a>

Several grid cells together. Grid areas are created by causing an item to span over multiple tracks.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/pGmMokRfoVbLNxf1VXrF.svg" alt="A diagram representation of a grid area" width="800" height="434" />

### Gaps <a href="#gaps" class="w-headline-link">#</a>

A gutter or alley between tracks. For sizing purposes these act like a regular track. You can't place content into a gap but you can span grid items across it.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/JNXSRH4j77loSB099E04.svg" alt="A diagram representation of a grid with gaps" width="800" height="434" />

### Grid container <a href="#grid-container" class="w-headline-link">#</a>

The HTML element which has `display: grid` applied, and therefore creates a new grid formatting context for the direct children.

    .container {
      display: grid;
    }

### Grid item <a href="#grid-item" class="w-headline-link">#</a>

A grid item is an item which is a direct child of the grid container.

    <div class="container">
      <div class="item"></div>
      <div class="item"></div>
      <div class="item"></div>
    </div>

## Rows and columns <a href="#rows-and-columns" class="w-headline-link">#</a>

To create a basic grid you can define a grid with three column tracks, two row tracks and a 10 pixel gap between the tracks as follows.

    .container {
        display: grid;
        grid-template-columns: 5em 100px 30%;
        grid-template-rows: 200px auto;
        gap: 10px;
    }

This grid demonstrates many of the things described in the terminology section. It has three column tracks. Each track uses a different length unit. It has two row tracks, one using a length unit and the other auto. When used as a track sizing auto can be thought of as being as big as the content. Tracks are auto sized by default.

If the element with a class of `.container` has child items, they will immediately lay out on this grid. You can see this in action in the demo below.

The Chrome Grid dev tools can help you to understand the various parts of the grid.

Open the [demo](https://codepen.io/web-dot-dev/full/NWdbrzr) in Chrome. Inspect the element with the grey background, which has an ID of `container`. Highlight the grid by selecting the grid badge in the DOM, next to the `.container` element. Inside the Layout tab, select **Display Line Numbers** in the dropdown to see the line numbers on your grid.

<figure><img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format" alt="A grid highlighted in Chrome DevTools showing line numbers, cells and tracks." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/YxpjWBUDsqQB2fr6rzU3.jpg?auto=format&amp;w=1600 1600w" width="800" height="449" /><figcaption>A grid highlighted in Chrome DevTools showing line numbers, cells and tracks.</figcaption></figure>### Intrinsic sizing keywords <a href="#intrinsic-sizing-keywords" class="w-headline-link">#</a>

In addition to the length and percentage dimensions as described in the section on [sizing units](/learn/css/sizing), grid tracks can use intrinsic sizing keywords. These keywords are defined in the Box Sizing specification and add additional methods of sizing boxes in CSS, not just grid tracks.

- `min-content`
- `max-content`
- `fit-content()`

The [`min-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/min-content) keyword will make a track as small as it can be without the track content overflowing. Changing the example grid layout to have three column tracks all at `min-content` size will mean they become as narrow as the longest word in the track.

The [`max-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/max-content) keyword has the opposite effect. The track will become as wide enough for all of the content to display in one long unbroken string. This might cause overflows as the string will not wrap.

The [`fit-content()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/fit-content()>) function acts like `max-content` at first. However, once the track reaches the size that you pass into the function, the content starts to wrap. So `fit-content(10em)` will create a track that is less than 10em, if the `max-content` size is less than 10em, but never larger than 10em.

In the next demo try out the different intrinsic sizing keywords by changing the sizing of the grid tracks.

You might spot in this demo that when auto is used the grid columns stretch to fill the container. Auto sized tracks will stretch by default if there is additional space in the grid container.

### The `fr` unit <a href="#the-fr-unit" class="w-headline-link">#</a>

We have existing length dimensions, percentages, and also these new keywords. There is also a special sizing method which only works in grid layout. This is the `fr` unit, a flexible length which describes a share of the available space in the grid container.

The `fr` unit works in a similar way to using `flex: auto` in flexbox. It distributes space after the items have been laid out. Therefore to have three columns which all get the same share of available space:

    .container {
      display: grid;
      grid-template-columns: 1fr 1fr 1fr;
    }

As the fr unit shares out available space, it can be combined with a fixed size gap or fixed size tracks. To have a component with a fixed size element and the second track taking up whatever space is left, you can use as a tracklisting of `grid-template-columns: 200px 1fr`.

Using different values for the fr unit will share the space in proportion. Larger values getting more of the spare space. In the demo below change the value of the third track.

### The `minmax()` function <a href="#the-minmax()-function" class="w-headline-link">#</a>

This function means that you can set a minimum and a maximum size for a track. This can be quite useful. If we take the example of the `fr` unit above which distributes remaining space, it could be written out using [`minmax()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/minmax()>) as `minmax(auto, 1fr)`. Grid looks at the intrinsic size of the content, then distributes available space after giving the content enough room. This means that you might not get tracks that each have an equal share of all space available in the grid container.

To force a track to take an equal share of the space in the grid container minus gaps use minmax. Replace `1fr` as a track size with `minmax(0, 1fr)`. This makes the minimum size of the track 0 and not the min-content size. Grid will then take all of the available size in the container, deduct the size needed for any gaps, and share the rest out according to your fr units.

### `repeat()` notation <a href="#repeat()-notation" class="w-headline-link">#</a>

If you want to create a 12 column track grid with equal columns, you could use the following CSS.

    .container {
        display: grid;
        grid-template-columns:
          minmax(0,1fr),
          minmax(0,1fr),
          minmax(0,1fr),
          minmax(0,1fr),
          minmax(0,1fr),
          minmax(0,1fr),
          minmax(0,1fr),
          minmax(0,1fr),
          minmax(0,1fr),
          minmax(0,1fr),
          minmax(0,1fr),
          minmax(0,1fr);
    }

Or, you could write it out using [`repeat()`](<https://developer.mozilla.org/en-US/docs/Web/CSS/repeat()>):

    .container {
        display: grid;
        grid-template-columns: repeat(12, minmax(0,1fr));
    }

The `repeat()` function can be used to repeat any section of your track listing. For example you can repeat a pattern of tracks. You can also have some regular tracks and a repeating section.

    .container {
        display: grid;
        grid-template-columns: 200px repeat(2, 1fr 2fr) 200px; /*creates 6 tracks*/
    }

### `auto-fill` and `auto-fit` <a href="#auto-fill-and-auto-fit" class="w-headline-link">#</a>

You can combine everything you have learned about track sizing, `minmax()`, and repeat, to create a useful pattern with grid layout. Perhaps you don't want to specify the number of column tracks, but instead want to create as many as will fit in your container.

You can achieve this with `repeat()` and the `auto-fill` or `auto-fit` keywords. In the demo below grid will create as many 200 pixel tracks as will fit in the container. Open the demo in a new window and see how the grid changes as you change the size of the viewport.

In the demo we get as many tracks as will fit. The tracks are not flexible however. You will get a gap on the end until there is enough space for another 200 pixel track. If you add the `minmax()` function, you can request as many tracks as will fit with a minimum size of 200 pixels and a maximum of 1fr. Grid then lays out the 200 pixel tracks and whatever space is leftover is distributed equally to them.

This creates a two-dimensional responsive layout with no need for any media queries.

There is a subtle difference between `auto-fill` and `auto-fit`. In the next demo play with a grid layout using the syntax explained above, but with only two grid items in the grid container. Using the `auto-fill` keyword you can see that empty tracks have been created. Change the keyword to `auto-fit` and the tracks collapse down to 0 size. This means that the flexible tracks now grow to consume the space.

The `auto-fill` and `auto-fit` keywords otherwise act in exactly the same way. There is no difference between them once the first track is filled.

## Auto-placement <a href="#auto-placement" class="w-headline-link">#</a>

You have already seen grid auto-placement at work in the demos so far. Items are placed on the grid one per cell in the order that they appear in the source. For many layouts this might be all you need. If you need more control then there are a couple of things you might like to do. The first is to tweak the auto-placement layout.

### Placing items in columns <a href="#placing-items-in-columns" class="w-headline-link">#</a>

The default behavior of grid layout is to place items along the rows. You can instead cause the items to place into columns using `grid-auto-flow: column`. You need to define row tracks otherwise the items will create intrinsic column tracks, and layout out all in one long row.

These values relate to the writing mode of the document. A row always runs in the direction a sentence runs in the writing mode of the document or component. In the next demo you can change mode the value of `grid-auto-flow` and the `writing-mode` property.

### Spanning tracks <a href="#spanning-tracks" class="w-headline-link">#</a>

You can cause some or all of the items in an auto-placed layout to span more than one track. Use the `span` keyword plus the number of lines to span as a value for `grid-column-end` or `grid-row-end`.

    .item {
        grid-column-end: span 2; /* will span two lines, therefore covering two tracks */
    }

As you have not specified a `grid-column-start`, this uses the initial value of `auto` and is placed according to the auto-placement rules. You can also specify the same thing using the shorthand `grid-column`:

    .item {
        grid-column: auto / span 2;
    }

### Filling gaps <a href="#filling-gaps" class="w-headline-link">#</a>

An auto-placed layout with some items spanning multiple tracks may result in a grid with some unfilled cells. The default behavior of grid layout with a fully auto-placed layout is to always progress forward. The items will be placed according to the order they are in the source, or any modification with the `order` property. If there is not enough space to fit an item, grid will leave a gap and move to the next track.

The next demo shows this behavior. The checkbox will apply the dense packing mode. This is enabled by giving `grid-auto-flow` a value of `dense`. With this value in place, grid will take items later in the layout and use them to fill gaps. This may mean that the display becomes disconnected from the logical order.

## Placing items <a href="#placing-items" class="w-headline-link">#</a>

You have a lot of functionality from CSS Grid already. Let's now take a look at how we position items on the grid we have created.

The first thing to remember is that CSS Grid Layout is based on a grid of numbered lines. The simplest way to place things onto the grid is to place them from one line to another. You'll discover other ways of placing items in this guide, but you always have access to those numbered lines.

The properties that you can use to place items by line number are:

- [`grid-column-start`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-start)
- [`grid-column-end`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column-end)
- [`grid-row-start`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-start)
- [`grid-row-end`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row-end)

They have shorthands which allow you to set both start and end lines at once:

- [`grid-column`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-column)
- [`grid-row`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-row)

To place your item set the start and end lines of the grid area that it should be placed into.

    .container {
        display: grid;
        grid-template-columns: repeat(4, 1fr);
        grid-template-rows: repeat(2, 200px 100px);
    }

    .item {
        grid-column-start: 1; /* start at column line 1 */
        grid-column-end: 4; /* end at column line 4 */
        grid-row-start: 2; /*start at row line 2 */
        grid-row-end: 4; /* end at row line 4 */
    }

Chrome DevTools can give you a visual guide to the lines in order to check where your item is placed.

The line numbering follows the writing mode and direction of the component. In the next demo change the writing mode or direction to see how the placement of the items stays consistent to the way that text flows.

### Stacking items <a href="#stacking-items" class="w-headline-link">#</a>

Using line-based positioning you can place items into the same cell of the grid. This means that you can stack items, or cause one item to partly overlap another. Items which come later in the source will be displayed on top of items that come earlier. You can change this stacking order using `z-index` just as with positioned items.

### Negative line numbers <a href="#negative-line-numbers" class="w-headline-link">#</a>

When you create a grid using `grid-template-rows` and `grid-template-columns` you create what is known as the **explicit grid**. This is a grid that you have defined and given size to the tracks.

Sometimes you will have items which display outside this explicit grid. For example, you might define column tracks and then add several rows of grid items without ever defining row tracks. The tracks would be auto sized by default. You also might place an item using `grid-column-end` that is outside of the explicit grid defined. In both of these cases grid will create tracks to make the layout work, and these tracks are referred to as the **implicit grid**.

Most of the time it will make no difference if you are working with an implicit or explicit grid. However, with line-based placement you may run into the main difference between the two.

Using negative line numbers you can place items from the end line of the explicit grid. This can be useful if you want an item to span from the first to the last column line. In that case you can use `grid-column: 1 / -1`. The item will stretch right across the explicit grid.

This only works for the explicit grid however. Take a layout of three rows of auto-placed items where you would like the very first item to span to the end line of the grid.

<img src="https://web-dev.imgix.net/image/VbAJIREinuYvovrBzzvEyZOpw5w1/Dt8yG376MqSyWJJ8KqPr.svg" alt="A sidebar with 8 sibling grid items" width="800" height="359" />

You might think that you can give that item `grid-row: 1 / -1`. In the demo below you can see that this doesn't work. The tracks are created in the implicit grid, there is no way to reach the end of the grid using `-1`.

#### Sizing implicit tracks <a href="#sizing-implicit-tracks" class="w-headline-link">#</a>

The tracks created in the implicit grid will be auto-sized by default. However if you want to control the sizing of the rows, use the [`grid-auto-rows`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-rows) property, and for columns [`grid-auto-columns`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-auto-columns).

To create all implicit rows at a minimum size of `10em` and a maximum size of `auto`:

    .container {
        display: grid;
        grid-auto-rows: minmax(10em, auto);
    }

To create implicit columns with a pattern of 100px and 200px wide tracks. In this case the first implicit column will be 100px, the second 200px, the third 100px, and so on.

    .container {
        display: grid;
        grid-auto-columns: 100px 200px;
    }

## Named grid lines <a href="#named-grid-lines" class="w-headline-link">#</a>

It can make it easier to place items into a layout if the lines have a name rather than a number. You can name any line on your grid by adding a name of your choosing between square brackets. Multiple names can be added, separated by a space inside the same brackets. Once you have named lines they can be used instead of the numbers.

    .container {
        display: grid;
        grid-template-columns:
          [main-start aside-start] 1fr
          [aside-end content-start] 2fr
          [content-end main-end]; /* a two column layout */
    }

    .sidebar {
        grid-column: aside-start / aside-end;
        /* placed between line 1 and 2*/
    }

    footer {
        grid-column: main-start / main-end;
        /* right across the layout from line 1 to line 3*/
    }

## Grid Template Areas <a href="#grid-template-areas" class="w-headline-link">#</a>

You can also name areas of the grid and place items onto those named areas. This is a lovely technique as it allows you to see what your component looks like right there in the CSS.

To start, give the direct children of your grid container a name using the [`grid-area`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-area) property:

    header {
        grid-area: header;
    }

    .sidebar {
        grid-area: sidebar;
    }

    .content {
        grid-area: content;
    }

    footer {
        grid-area: footer;
    }

The name can be anything you like other than the keywords `auto` and `span`. Once all of your items are named, use the [`grid-template-areas`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template-areas) property to define which grid cells each item will span. Each row is defined within quotes.

    .container {
        display: grid;
        grid-template-columns: repeat(4,1fr);
        grid-template-areas:
            "header header header header"
            "sidebar content content content"
            "sidebar footer footer footer";
    }

There are a few rules when using `grid-template-areas`.

- The value must be a complete grid with no empty cells.
- To span tracks repeat the name.
- The areas created by repeating the name must be rectangular and cannot be disconnected.

If you break any of the above rules the value is treated as invalid and thrown away.

To leave white space on the grid use a `.` or multiples with no white space between them. For example to leave the very first cell on the grid empty I could add a series of `.` characters:

    .container {
        display: grid;
        grid-template-columns: repeat(4,1fr);
        grid-template-areas:
            "....... header header header"
            "sidebar content content content"
            "sidebar footer footer footer";
    }

As your entire layout is defined in one place, it makes it straightforward to redefine the layout using media queries. In the next example I have created a two column layout which moves to three columns by redefining the value of `grid-template-columns` and `grid-template-areas`. Open the example in a new window to play with the viewport size and see the layout change.

You can also see how the `grid-template-areas` property relates to `writing-mode` and direction, as with other grid methods.

## Shorthand properties <a href="#shorthand-properties" class="w-headline-link">#</a>

There are two shorthand properties which allow you to set many of the grid properties in one go. These can look a little confusing until you break down exactly how they go together. Whether you want to use them or prefer to use longhands is up to you.

### `grid-template` <a href="#grid-template" class="w-headline-link">#</a>

The [`grid-template`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid-template) property is a shorthand for `grid-template-rows`, `grid-template-columns` and `grid-template-areas`. The rows are defined first, along with the value of `grid-template-areas`. Column sizing is added after a `/`.

    .container {
        display: grid;
        grid-template:
          "head head head" minmax(150px, auto)
          "sidebar content content" auto
          "sidebar footer footer" auto / 1fr 1fr 1fr;
    }

### `grid` property <a href="#grid-property" class="w-headline-link">#</a>

The [`grid`](https://developer.mozilla.org/en-US/docs/Web/CSS/grid) shorthand can be used in exactly the same way as the `grid-template` shorthand. When used in this way it will reset the other grid properties that it accepts to their initial values. The full set being:

- `grid-template-rows`
- `grid-template-columns`
- `grid-template-areas`
- `grid-auto-rows`
- `grid-auto-columns`
- `grid-auto-flow`

You can alternately use this shorthand to define how the implicit grid behaves, for example:

    .container {
        display: grid;
        grid: repeat(2, 80px) / auto-flow  120px;
    }

## Alignment <a href="#alignment" class="w-headline-link">#</a>

Grid layout uses the same alignment properties that you learned about in the guide to [flexbox](/learn/css/flexbox). In grid the properties which begin with `justify-` are always used on the inline axis, the direction in which sentences run in your writing mode.

The properties which begin with `align-` are used on the block axis, the direction in which blocks are laid out in your writing mode.

- [`justify-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-content) and [`align-content`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-content): distribute additional space in the grid container around or between tracks.
- [`justify-self`](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-self) and [`align-self`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-self): are applied to a grid item to move it around inside the grid area it is placed in.
- [`justify-items`](https://developer.mozilla.org/en-US/docs/Web/CSS/justify-items) and [`align-items`](https://developer.mozilla.org/en-US/docs/Web/CSS/align-items): are applied to the grid container to set all of the `justify-self` properties on the items.

### Distributing extra space <a href="#distributing-extra-space" class="w-headline-link">#</a>

In this demo the grid is larger than the space needed to lay out the fixed width tracks. This means we have space in both the inline and block dimensions of the grid. Try different values of `align-content` and `justify-content` to see how the tracks behave.

Note how the gaps become larger when using values such as `space-between`, and any grid item spanning two tracks also grows to absorb the additional space added to the gap.

As with flexbox, these properties will only work if there is additional space to distribute. If your grid tracks neatly fill the container then there will be no space to share out.

### Moving content around <a href="#moving-content-around" class="w-headline-link">#</a>

Items with a background color appear to completely fill the grid area they are placed in, because the initial value for `justify-self` and `align-self` is `stretch`.

If your item is an image, or something else with an intrinsic aspect ratio, the initial value will be `start` rather than `stretch` to avoid stretching things out of shape.

In the demo change the values of `justify-items` and `align-items` to see how this changes the layout. The grid area is not changing size, instead the items are being moved around inside the defined area.

Test your knowledge of grid

Which of the following are CSS grid terms?

<span data-role="option">lines</span> <span data-role="option">circles</span> <span data-role="option">cells</span> <span data-role="option">areas</span> <span data-role="option">trains</span> <span data-role="option">gaps</span> <span data-role="option">tracks</span>

The grid is divided by these horizontal and vertically running separators.

Sorry, no concepts of circles in CSS grid.

A single intersection of a row and a column creates a grid cell.

Multiple cells together.

Sorry, no concepts of trains in CSS grid.

The space between cells.

A single row or a column is a track in the grid.

    main {
      display: grid;
    }

What is the default layout direction of a grid?

<span data-role="option">Rows</span> <span data-role="option">Columns</span>

Without any columns defined, grid children lay out in the block direction as they normally would.

If `grid-auto-flow: column` was present, than a grid would layout as columns.

What is the difference between `auto-fit` and `auto-fill`?

<span data-role="option">`auto-fit` will stretch cells to fit the container, where `auto-fill` won't.</span> <span data-role="option">`auto-fit` will stretch a container to fit the children, where `auto-fill` makes the children fit to the container.</span>

`auto-fill` places as many items into the template as possible, without stretching. Fit **makes** them fit.

This is not how these properties behave.

What is `min-content`?

<span data-role="option">Same as 0%</span> <span data-role="option">The smallest letter</span> <span data-role="option">The longest word or image.</span>

0% is a relative value of the parent box, while `min-content` is relative to the words and images in the box.

While there is a smallest letter, letters are not what `min-content` is refering to.

In the phrase 'CSS is awesome', the word awesome would be the `min-content`.

What is `max-content`?

<span data-role="option">The longest sentence or biggest image.</span> <span data-role="option">The longest letter.</span> <span data-role="option">The longest word.</span>

This is the maximum size the content of the box is asking for or has specified. It's a sentence as it's widest or an image at it's widest.

While there is a longest letter, letters are not what `max-content` is refering to.

The longest word is `min-content`.

What is auto-placement?

<span data-role="option">When grid takes the child items and places them in the best order based on browser heuristics.</span> <span data-role="option">When grid child items have been given a `grid-area` and are placed on that cell.</span> <span data-role="option">When unassigned grid items are placed next in a layout template.</span>

No browser will change your content order, only your own styles will do that.

That's explicit placement not auto placement.

Grid items without an explicit area will be placed in the next available grid cell

## Resources <a href="#resources" class="w-headline-link">#</a>

This guide has given you an overview of the different parts of the grid layout specification. To find out more, take a look at the following resources.

- [MDN CSS Grid Layout](https://developer.mozilla.org/en-US/docs/Web/CSS/CSS_Grid_Layout)
- [A Complete Guide to Grid](https://css-tricks.com/snippets/css/complete-guide-grid/)
- [Creating a Grid Container](https://www.smashingmagazine.com/2020/01/understanding-css-grid-container/)
- [A comprehensive collection of grid learning material](https://gridbyexample.com/)

<a href="/learn/css/flexbox/" class="course-pagination-control"></a>

<span class="font-mono case-upper display-none md:display-inline">Prev</span> <span class="font-mono">009</span>

Flexbox

<a href="/learn/css/logical-properties/" class="course-pagination-control"></a>

<span class="font-mono case-upper">Next</span> <span class="font-mono">011</span>

Logical Properties

Logical, flow relative properties and values are linked to the flow of text, rather than the physical shape of the screen. Learn how to take advantage of this newer approach to CSS.

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
