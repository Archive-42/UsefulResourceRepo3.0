<img src="https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/CVkKShuaQw4CfZBg3Eub.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#virtualize-large-lists-with-react-window" class="w-toc__header--link">Virtualize large lists with react-window</a>

- [Why is this useful?](#why-is-this-useful)
- [react-window](#react-window)
- [When to use fixed size lists](#when-to-use-fixed-size-lists)
- [When to use variable sized lists](#when-to-use-variable-sized-lists)
- [Grids](#grids)
- [Lazy loading on scroll](#lazy-loading-on-scroll)
- [Overscanning](#overscanning)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Virtualize large lists with react-window

Super large tables and lists can slow down your site's performance signficantly. Virtualization can help!

Apr 29, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

- <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
- <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
- <a href="https://houssein.me/" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jason Miller" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/bPCYfhUgxdCpXhKAWc9X.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/developit/)

<a href="/authors/developit/" class="w-author__name-link">Jason Miller</a>

- <a href="https://twitter.com/_developit" class="w-author__link">Twitter</a>
- <a href="https://github.com/developit" class="w-author__link">GitHub</a>
- <a href="https://jasonformat.com" class="w-author__link">Blog</a>

[`react-window`](https://react-window.now.sh/#/examples/list/fixed-size) is a library that allows large lists to be rendered efficiently.

Here's an example of a list that contains 1000 rows being rendered with `react-window`. Try scrolling as fast you can.

## Why is this useful? <a href="#why-is-this-useful" class="w-headline-link">#</a>

There may be times where you need to display a large table or list that contains many rows. Loading every single item on such a list can affect performance significantly.

**List virtualization**, or "windowing", is the concept of only rendering what is visible to the user. The number of elements that are rendered at first is a very small subset of the entire list and the "window" of visible content _moves_ when the user continues to scroll. This improves both the rendering and scrolling performance of the list.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format" alt="Moving &quot;window&quot; of content in a virtualized list" class="w-screenshot" sizes="(min-width: 578px) 578px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aWscOPGSFKVAIkgnUplQ.jpg?auto=format&amp;w=1156 1156w" width="578" height="525" /><figcaption>Moving "window" of content in a virtualized list</figcaption></figure>DOM nodes that exit the "window" are recycled, or immediately replaced with newer elements as the user scrolls down the list. This keeps the number of all rendered elements specific to the size of the window.

## react-window <a href="#react-window" class="w-headline-link">#</a>

`react-window` is a small, third-party library that makes it easier to create virtualized lists in your application. It provides a number of base APIs that can be used for different types of lists and tables.

### When to use fixed size lists <a href="#when-to-use-fixed-size-lists" class="w-headline-link">#</a>

Use the `FixedSizeList` component if you have a long, one-dimensional list of equally sized items.

    import React from 'react';
    import { FixedSizeList } from 'react-window';

    const items = [...] // some list of items

    const Row = ({ index, style }) => (
      <div style={style}>
         {/* define the row component using items[index] */}
      </div>
    );

    const ListComponent = () => (
      <FixedSizeList
        height={500}
        width={500}
        itemSize={120}
        itemCount={items.length}
      >
        {Row}
      </FixedSizeList>
    );

    export default ListComponent;

- The `FixedSizeList` component accepts a `height`, `width` and `itemSize` prop to control the size of the items within the list.
- A function that renders the rows is passed as a child to `FixedSizeList`. Details about the particular item can be accessed with the `index` argument (`items[index]`).
- A `style` parameter is also passed in to the row rendering method that **must** be attached to the row element. List items are absolutely positioned with their height and width values assigned inline, and the `style` parameter is responsible for this.

**Caution**: Do not assign `height` and `width` properties to the list or the list item with an external CSS file. They would be ignored due to the fact that these style attributes are applied inline.

The Glitch example shown earlier in this article shows an example of a `FixedSizeList` component.

### When to use variable sized lists <a href="#when-to-use-variable-sized-lists" class="w-headline-link">#</a>

Use the `VariableSizeList` component to render a list of items that have different sizes. This component works in the same way as a fixed size list, but instead expects a function for the `itemSize` prop instead of a specific value.

    import React from 'react';
    import { VariableSizeList } from 'react-window';

    const items = [...] // some list of items

    const Row = ({ index, style }) => (
      <div style={style}>
         {/* define the row component using items[index] */}
      </div>
    );

    const getItemSize = index => {
      // return a size for items[index]
    }

    const ListComponent = () => (
      <VariableSizeList
        height={500}
        width={500}
        itemCount={items.length}
        itemSize={getItemSize}
      >
        {Row}
      </VariableSizeList>
    );

    export default ListComponent;

The following embed shows an example of this component.

The item size function passed to the `itemSize` prop randomizes the row heights in this example. In a real application however, there should be actual logic defining the sizes of each item. Ideally, these sizes should be calculated based on data or obtained from an API.

Both `FixedSizeList` and `VariableSizeList` components support horizontal lists by using a `layout="horizontal"` prop. Take a look at the [documentation](https://react-window.now.sh/#/examples/list/fixed-size) to see an example.

### Grids <a href="#grids" class="w-headline-link">#</a>

`react-window` also provides support for virtualizing multi-dimensional lists, or grids. In this context, the "window" of visible content changes as the user scrolls horizontally **and** vertically.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format" alt="Moving &quot;window&quot; of content in a virtualized grid is two-dimensional" class="w-screenshot" sizes="(min-width: 739px) 739px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1j2qoGW8bFzBNiOzaJKZ.jpg?auto=format&amp;w=1478 1478w" width="739" height="516" /><figcaption>Moving "window" of content in a virtualized grid is two-dimensional</figcaption></figure>Similarly, both `FixedSizeGrid` and `VariableSizeGrid` components can be used depending on whether the size of specific list items can vary.

- For `FixedSizeGrid`, the API is about the same but with the fact that heights, widths and item counts need to be represented for both columns and rows.
- For `VariableSizeGrid`, both the column widths and row heights can be changed by passing in functions instead of values to their respective props.

Take a look at the [documentation](https://react-window.now.sh/#/examples/grid/fixed-size) to see examples of virtualized grids.

Aside from providing the base components to create efficient lists and grids, `react-window` also provides other capabilities such as scrolling to a specific item or providing an indicator when the user is scrolling. The [documentation](https://react-window.now.sh/#/examples/list/scrolling-indicators) provides examples for this.

## Lazy loading on scroll <a href="#lazy-loading-on-scroll" class="w-headline-link">#</a>

Many websites improve performance by waiting to load and render items in a long list until the user has scrolled down. This technique, commonly referred to as "infinite loading", adds new DOM nodes into the list as the user scrolls past a certain threshold close to the end. Although this is better than loading all items on a list at once, it still ends up populating the DOM with thousands of row entries if the user has scrolled past that many. This can lead to an excessively large DOM size, which starts to impact performance by making style calculations and DOM mutations slower.

The following diagram might help summarize this:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format" alt="Difference in scrolling between a regular and virtualized list" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/dKuKVjP02xWxO9LPoOuc.jpg?auto=format&amp;w=1600 1600w" width="800" height="531" /><figcaption>Difference in scrolling between a regular and virtualized list</figcaption></figure>The best approach to solve this problem is continue to use a library like `react-window` to maintain a small "window" of elements on a page, but to also lazy load newer entries as the user scrolls down. A separate package, `react-window-infinite-loader`, makes this possible with `react-window`.

Consider the following piece of code which shows an example of state that is managed in a parent `App` component.

    import React, { Component } from 'react';

    import ListComponent from './ListComponent';

    class App extends Component {
      constructor(props) {
        super(props);
        this.state = {
          items: [], // instantiate initial list here
          moreItemsLoading: false,
          hasNextPage: true
        };

        this.loadMore = this.loadMore.bind(this);
      }

      loadMore() {
       // method to fetch newer entries for the list
      }

      render() {
        const { items, moreItemsLoading, hasNextPage } = this.state;

        return (
          <ListComponent
            items={items}
            moreItemsLoading={moreItemsLoading}
            loadMore={this.loadMore}
            hasNextPage={hasNextPage}
          />
        );
      }
    }

    export default App;

A `loadMore` method is passed into a child `ListComponent` that contains the infinite loader list. This is important because the infinite loader needs to fire a callback to load more items once the user has scrolled past a certain point.

Here's how the `ListComponent` that renders the list can look like:

    import React from 'react';
    import { FixedSizeList } from 'react-window';
    import InfiniteLoader from "react-window-infinite-loader";

    const ListComponent = ({ items, moreItemsLoading, loadMore, hasNextPage }) => {
      const Row = ({ index, style }) => (
         {/* define the row component using items[index] */}
      );

      const itemCount = hasNextPage ? items.length + 1 : items.length;

      return (
        <InfiniteLoader
          isItemLoaded={index => index < items.length}
          itemCount={itemCount}
          loadMoreItems={loadMore}
        >
          {({ onItemsRendered, ref }) => (
            <FixedSizeList
              height={500}
              width={500}
              itemCount={itemCount}
              itemSize={120}
              onItemsRendered={onItemsRendered}
              ref={ref}
            >
              {Row}
            </FixedSizeList>
          )}
      </InfiniteLoader>
      )
    };

    export default ListComponent;

In here, the `FixedSizeList` component is wrapped within the `InfiniteLoader`. The props assigned to the loader are:

- `isItemLoaded`: Method that checks whether a certain item has loaded
- `itemCount`: Number of items on the list (or expected)
- `loadMoreItems`: Callback that returns a promise that resolves to additional data for the list

A [render prop](https://reactjs.org/docs/render-props.html#using-props-other-than-render) is used to return a function that the list component uses in order to render. Both `onItemsRendered` and `ref` attributes are attributes that need to be passed in.

The following is an example of how infinite loading can work with a virtualized list.

Scrolling down the list might feel the same, but a request is now made to retrieve 10 users from a [random user API](https://randomuser.me/) every time you scroll close to the end of the list. This is all done while only rendering a single "window" of results at at a time.

By checking the `index` of a certain item, a different loading state can be shown for an item depending on whether a request has been made for newer entries and the item is still loading.

For example:

    const Row = ({ index, style }) => {
      const itemLoading = index === items.length;

      if (itemLoading) {
          // return loading state
      } else {
          // return item
      }
    };

## Overscanning <a href="#overscanning" class="w-headline-link">#</a>

Since items in a virtualized list only change when the user scrolls, blank space can briefly flash as newer entries are about to be displayed. You can try quickly scrolling any of the previous examples in this guide to notice this.

To improve the user experience of virtualized lists, `react-window` allows you to overscan items with the `overscanCount` property. This allows you to define how many items outside of the visible "window" to render at all times.

    <FixedSizeList
      //...
      overscanCount={4}
    >
      {...}
    </FixedSizeList>

`overscanCount` works for both the `FixedSizeList` and `VariableSizeList` components and has a default value of 1. Depending on how large a list is as well as the size of each item, overscanning more than just one entry can help prevent a noticeable flash of empty space when the user scrolls. However, overscanning too many entries can affect performance negatively. The whole point of using a virtualized list is to minimize the number of entries to what the user can see at any given moment, so try to keep the number of overscanned items as low as possible.

For `FixedSizeGrid` and `VariableSizeGrid`, use the `overscanColumnsCount` and `overscanRowsCount` properties to control the number of columns and rows to overscan respectively.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

If you are unsure where to begin virtualizing lists and tables in your application, follow these steps:

1.  Measure rendering and scrolling performance. This [article](https://addyosmani.com/blog/react-window/) shows how the [FPS meter](https://developers.google.com/web/tools/chrome-devtools/evaluate-performance/#analyze_frames_per_second) in Chrome DevTools can be used to explore how efficiently items are rendered on a list.
2.  Include `react-window` for any long lists or grids that are affecting performance.
3.  If there are certain features not supported in `react-window`, consider using [`react-virtualized`](https://github.com/bvaughn/react-virtualized) if you cannot add this functionality yourself.
4.  Wrap your virtualized list with `react-window-infinite-loader` if you need to lazy load items as the user scrolls.
5.  Use the `overscanCount` property for your lists and the `overscanColumnsCount` and `overscanRowsCount` properties for your grids to prevent a flash of empty content. Do not overscan too many entries as this will affect performance negatively.

<span class="w-mr--sm">Last updated: Apr 29, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/virtualize-long-lists-react-window/index.md)

<a href="/react" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
