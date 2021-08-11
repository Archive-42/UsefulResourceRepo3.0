## <a href="#route-prefetching-in-next.js" class="w-toc__header--link">Route prefetching in Next.js</a>

- [What will you learn?](#what-will-you-learn)
- [The &lt;Link&gt; component](#the-lesslinkgreater-component)
- [How automatic prefetching works](#how-automatic-prefetching-works)
- [Avoid unnecessary prefetching](#avoid-unnecessary-prefetching)
- [Prefetching with custom routing](#prefetching-with-custom-routing)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Route prefetching in Next.js

How Next.js speeds up navigations with route prefetching and how to customize it.

Nov 8, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

- <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
- <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
- <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

## What will you learn? <a href="#what-will-you-learn" class="w-headline-link">#</a>

In this post you'll learn how routing in Next.js works, how it's optimized for speed, and how to customize it to best fit your needs.

## The `<Link>` component <a href="#the-lesslinkgreater-component" class="w-headline-link">#</a>

In [Next.js](https://nextjs.org/), you don't need to set up routing manually. Next.js uses file-system-based routing, which lets you just create files and folders inside the `./pages/` directory:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format" class="w-screenshot" sizes="(min-width: 376px) 376px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7cwpyvEgBCIbkqrbsbL0.png?auto=format&amp;w=752 752w" width="376" height="348" /></figure>To link to different pages, use the [`<Link>`](https://nextjs.org/docs/api-reference/next/link) component, similarly to how you'd use the good old `<a>` element:

    <Link href="/margherita">
      <a>Margherita</a>
    </Link>

When you use the `<Link>` component for navigation, Next.js does a little bit more for you. Normally, a page is downloaded when you follow a link to it, but Next.js automatically prefetches the JavaScript needed to render the page.

When you load a page with a few links, odds are that by the time you follow a link, the component behind it has already been fetched. This improves application responsiveness by making navigations to new pages quicker.

In the example app below, the `index.js` page links to `margherita.js` with a `<Link>`:

Use Chrome DevTools to verify that `margherita.js` is prefetched:

1.  To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

2.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.

3.  Click the **Network** tab.

4.  Select the **Disable cache** checkbox.

5.  Reload the page.

When you load `index.js`, the **Network** tab shows that `margherita.js` is downloaded too:

<img src="https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format" alt="DevTools Network tab with margherita.js highlighted." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/ajJKWGvPidRa1nvqzXKL.png?auto=format&amp;w=1600 1600w" width="800" height="639" />

## How automatic prefetching works <a href="#how-automatic-prefetching-works" class="w-headline-link">#</a>

Next.js prefetches only links that appear in the viewport and uses the [Intersection Observer API](https://developer.mozilla.org/en-US/docs/Web/API/Intersection_Observer_API) to detect them. It also disables prefetching when the network connection is slow or when users have [`Save-Data`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Save-Data) turned on. Based on these checks, Next.js dynamically injects [`<link rel="preload">`](/preload-critical-assets/) tags to download components for subsequent navigations.

Next.js only _fetches_ the JavaScript; it doesn't execute it. That way, it's not downloading any additional content that the prefetched page might request until you visit the link.

**Caution**: Glitch examples are running in production mode because prefetching depends on the browsing conditions and it's enabled only in optimized production builds. To switch to development mode, check the `README.md` in Glitch examples.

Because `<link rel="preload">` requests resources with high priority, the browser expects them to be used right away, which triggers Console warnings. [Priority hints](https://developers.google.com/web/updates/2019/02/priority-hints) will soon become available in Chrome, which will allow Next.js to indicate lower priority for resources that are not needed immediately with `<link rel="preload" importance="low">`.

## Avoid unnecessary prefetching <a href="#avoid-unnecessary-prefetching" class="w-headline-link">#</a>

To avoid downloading unnecessary content, you can disable prefetching for rarely visited pages by setting the `prefetch` property on `<Link>` to `false`:

    <Link href="/pineapple-pizza" prefetch={false}>
      <a>Pineapple pizza</a>
    </Link>

In this second example app, the `index.js` page has a `<Link>` to `pineapple-pizza.js` with `prefetch` set to `false`:

To inspect the network activity, follow the steps from the first example. When you load `index.js`, the DevTools **Network** tab shows that `margherita.js` is downloaded, but `pineapple-pizza.js` is not:

<img src="https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format" alt="DevTools Network tab with margherita.js highlighted." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/8YTg0ym7vJbQm9oCVQYz.png?auto=format&amp;w=1600 1600w" width="800" height="639" />

## Prefetching with custom routing <a href="#prefetching-with-custom-routing" class="w-headline-link">#</a>

The `<Link>` component is suitable for most use cases, but you can also build your own component to do routing. Next.js makes this easy for you with the router API available in [`next/router`](https://nextjs.org/docs/api-reference/next/router#userouter). If you want to do something (for example, submit a form) before navigating to a new route, you can define that in your custom routing code.

When you use custom components for routing, you can add prefetching to them too. To implement prefetching in your routing code, use the `prefetch` method from `useRouter`.

Take a look at `components/MyLink.js` in this example app:

Prefetching is done inside the [`useEffect`](https://reactjs.org/docs/hooks-effect.html) hook. If the `prefetch` property on a `<MyLink>` is set to `true`, the route specified in the `href` property gets prefetched when that `<MyLink>` is rendered:

    useEffect(() => {
        if (prefetch) router.prefetch(href)
    });

When you click the link, the routing is done in `handleClick`. A message gets logged to the console, and the `push` method navigates to the new route specified in `href`:

    const handleClick = e => {
        e.preventDefault();
        console.log("Having fun with Next.js.");
        router.push(href);
    };

In this example app, the `index.js` page has a `<MyLink>` to `margherita.js` and `pineapple-pizza.js`. The `prefetch` property is set to `true` on `/margherita` and to `false` on `/pineapple-pizza`.

    <MyLink href="/margherita" title="Margherita" prefetch={true} />
    <MyLink href="/pineapple-pizza"  title="Pineapple pizza" prefetch={false} />

When you load `index.js`, the **Network** tab shows that `margherita.js` is downloaded and `pineapple-pizza.js` is not:

<img src="https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format" alt="DevTools Network tab with margherita.js highlighted." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/MWPy8nvBJCnzy4zGVRln.png?auto=format&amp;w=1600 1600w" width="800" height="639" />

When you click on either link, the **Console** logs "Having fun with Next.js." and navigates to the new route:

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format" alt="DevTools Console displaying the message &#39;Having fun with Next.js.&#39;" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/goiEqi3SIWJBUqsk7j6H.png?auto=format&amp;w=1600 1600w" width="800" height="690" />

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

When you use `<Link>`, Next.js automatically prefetches the JavaScript needed to render the linked page, which makes navigating to new pages faster. If you are using custom routing, you can use the Next.js router API to implement prefetching yourself. Avoid downloading content unnecessarily by disabling prefetching for rarely visited pages.

<span class="w-mr--sm">Last updated: Nov 8, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/route-prefetching-in-nextjs/index.md)

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
