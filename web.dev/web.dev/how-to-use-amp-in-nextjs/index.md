<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

How to use AMP in Next.js
=========================

Nov 8, 2019

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

-   <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
-   <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
-   <a href="https://houssein.me/" class="w-author__link">Blog</a>

What will you learn? <a href="#what-will-you-learn" class="w-headline-link">#</a>
---------------------------------------------------------------------------------

This codelab lets you try out the two ways that you can use AMP in a Next.js app. Check out [How AMP can guarantee fastness in your Next.js app](/how-amp-can-guarantee-fastness-in-your-nextjs-app) to learn why you might want to add AMP support to your Next.js app.

### How to create Hybrid AMP pages <a href="#hybrid" class="w-headline-link">#</a>

**Caution**: The [AMP-only approach](#amponly) is the recommended path for using AMP with Next.js. The Hybrid AMP approach described in this section has a higher maintenance cost than the AMP-only approach because it requires you to maintain two versions of each page. You should only use the Hybrid approach if you're certain that the AMP-only approach won't work.

The **Hybrid AMP** approach creates an accompanying AMP version of any Next.js page. In the past the Hybrid approach was frequently used when there was an experience on the main version of your page that AMP couldn't support. The main version had the full experience while the AMP page had a slightly degraded experience. With the introduction of [amp-script](https://amp.dev/documentation/components/amp-script/) there's less of a need for the Hybrid approach, but we'll cover it here just in case you still need it.

There are multiple ways to configure how Next.js renders and serves pages. Using a `config` object allows you to modify these on a per-page basis. In order to serve a specific page as an AMP page, you need to export the `amp` property in the object:

    import React from 'react'

    export const config = { amp: 'hybrid' };

    const Home = () => (
      <p>This is the home page</p>
    );

    export default Home;

1.  Click **Remix to Edit** to make the project editable.

2.  To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

3.  Add `?amp=1` to the end of the URL. The page looks the same, but if you look in the Console you'll see that the AMP version of the page is being rendered.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ybkMSvzPYUoIpgU4eA1E.png?auto=format&amp;w=1600 1600w" width="800" height="376" /></figure>Since the page only has a single `<p>` tag, there's no visible difference between the main page and its AMP version.

#### How to conditionally serve AMP components <a href="#how-to-conditionally-serve-amp-components" class="w-headline-link">#</a>

AMP pages need to have their own set of valid components in place of many HTML elements. It's important to make sure that the AMP components are conditionally served only for the AMP page. Next.js provides a [hook](https://reactjs.org/docs/hooks-overview.html) called `useAmp` to allow you to conditionally serve different elements depending on which version of the page was requested.

1.  To view the source, press **View Source**.

2.  Edit `pages/index.js` so that it renders a different paragraph element to the page depending on whether the main version or the AMP version was requested:

        import React from 'react';
        import { useAmp } from 'next/amp';

        export const config = { amp: 'hybrid' };

        const Home = () => (
          useAmp() ? (
            <p>This is the <strong>AMP</strong> version of the home page</p>
          ) : (
            <p>This is the main version of the home page</p>
          )
        );

        export default Home;

3.  Load the main version of the page:

    <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/iXgDaiqLkqLY8kYoKSl7.png?auto=format&amp;w=1600 1600w" width="800" height="637" /></figure>4.  Add `?amp=1` to the end of the URL again to load the AMP version of the page:

    <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kWIKm1ADltg2B2444bLR.png?auto=format&amp;w=1600 1600w" width="800" height="637" /></figure>5.  Try rendering AMP's replacement of the image tag, `amp-img`:

        import React from 'react';
        import { useAmp } from 'next/amp';

        export const config = { amp: 'hybrid' };

        const imgSrc = 'https://placekitten.com/1000/1000';

        const Image = () => (
          useAmp() ? (
            <amp-img alt="A cute kitten"
              src={imgSrc}
              width="1000"
              height="1000"
              layout="responsive">
            </amp-img>
          ) : (
            <img alt="A cute kitten"
              src={imgSrc}
              width="1000"
              height="1000">
            </img>
          )
        );

        const Home = () => (
          <div>
            <Image />
          </div>
        );

        export default Home;

    `layout="responsive"` automatically renders a fully responsive image with an aspect ratio specified by width and height. Check out [Layout & media queries](https://amp.dev/documentation/guides-and-tutorials/develop/style_and_layout/control_layout/) to learn more about the supported layouts of AMP elements, and [amp-img](https://amp.dev/documentation/examples/components/amp-img/) to learn more about that element's optimizations.

6.  View the main version of the page again.

    <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/307bH0fcWyCUBhK47CUg.png?auto=format&amp;w=1600 1600w" width="800" height="637" /></figure>7.  View the AMP version of the page again.

    <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rTuu0WR9Rj6o07eLFFb4.png?auto=format&amp;w=1600 1600w" width="800" height="637" /></figure>

### How to create AMP-only pages <a href="#amponly" class="w-headline-link">#</a>

Next.js also supports AMP-only pages. With this approach, a single AMP page is served and rendered to users and search engines at all times.

1.  To render an AMP-only page, change the value of the `amp` property in the config object to `true`.

        import React from 'react'

        export const config = { amp: true };

        const Home = () => (
          <p>This is an AMP-only page</p>
        );

        export default Home;

<a href="/how-amp-can-guarantee-fastness-in-your-nextjs-app" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to article</a>

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
