





## <a href="#code-splitting-with-dynamic-imports-in-next.js" class="w-toc__header--link">Code splitting with dynamic imports in Next.js</a>

- [What will you learn?](#what-will-you-learn)
- [Route-based and component-based code splitting](#route-based-and-component-based-code-splitting)
- [Dynamic imports in action](#dynamic-imports-in-action)
- [Dynamic imports with custom loading indicator](#dynamic-imports-with-custom-loading-indicator)
- [Dynamic imports without SSR](#dynamic-imports-without-ssr)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Code splitting with dynamic imports in Next.js

How to speed up your Next.js app with code splitting and smart loading strategies.

Nov 8, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

- <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
- <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
- <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

## What will you learn? <a href="#what-will-you-learn" class="w-headline-link">#</a>

This post explains different types of [code splitting](/reduce-javascript-payloads-with-code-splitting/) and how to use dynamic imports to speed up your Next.js apps.

## Route-based and component-based code splitting <a href="#route-based-and-component-based-code-splitting" class="w-headline-link">#</a>

By default, Next.js splits your JavaScript into separate chunks for each route. When users load your application, Next.js only sends the code needed for the initial route. When users navigate around the application, they fetch the chunks associated with the other routes. Route-based code splitting minimizes the amount of script that needs to be parsed and compiled at once, which results in faster page load times.

While route-based code splitting is a good default, you can further optimize the loading process with code splitting on the component level. If you have large components in your app, it's a great idea to split them into separate chunks. That way, any large components that are not critical or only render on certain user interactions (like clicking a button) can be lazy-loaded.

Next.js supports [dynamic `import()`](https://v8.dev/features/dynamic-import), which allows you to import JavaScript modules (including React components) dynamically and load each import as a separate chunk. This gives you component-level code splitting and enables you to control resource loading so that users only download the code they need for the part of the site that they're viewing. In Next.js, these components are [server-side rendered (SSR)](https://developers.google.com/web/updates/2019/02/rendering-on-the-web) by default.

## Dynamic imports in action <a href="#dynamic-imports-in-action" class="w-headline-link">#</a>

This post includes several versions of a sample app that consists of a simple page with one button. When you click the button, you get to see a cute puppy. As you move through each version of the app, you'll see how dynamic imports are different from [static imports](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) and how to work with them.

In the first version of the app, the puppy lives in `components/Puppy.js`. To display the puppy on the page, the app imports the `Puppy` component in `index.js` with a static import statement:

    import Puppy from "../components/Puppy";

To see how Next.js bundles the app, inspect the network trace in DevTools:

1.  To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

2.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.

3.  Click the **Network** tab.

4.  Select the **Disable cache** checkbox.

5.  Reload the page.

When you load the page, all the necessary code, including the `Puppy.js` component, is bundled in `index.js`:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/6KWlTYFhoIEIGqnuMwlh.png?auto=format&amp;w=1600 1600w" width="800" height="665" /></figure>When you press the **Click me** button, only the request for the puppy JPEG is added to the **Network** tab:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7MkXVqnqfIbW74VV48kB.png?auto=format&amp;w=1600 1600w" width="800" height="665" /></figure>The downside of this approach is that even if users don't click the button to see the puppy, they have to load the `Puppy` component because it's included in `index.js`. In this little example that's not a big deal, but in real-world applications it's often a huge improvement to load large components only when necessary.

Now check out a second version of the app, in which the static import is replaced with a dynamic import. Next.js includes `next/dynamic`, which makes it possible to use dynamic imports for any components in Next:

    import Puppy from "../components/Puppy";
    import dynamic from "next/dynamic";

    // ...

    const Puppy = dynamic(import("../components/Puppy"));

Follow the steps from the first example to inspect the network trace.

When you first load the app, only `index.js` is downloaded. This time it's 0.5 KB smaller (it went down from 37.9 KB to 37.4 KB) because it doesn't include the code for the `Puppy` component:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/K7Ii3bxUkb37LrZjjWT1.png?auto=format&amp;w=1600 1600w" width="800" height="665" /></figure>The `Puppy` component is now in a separate chunk, `1.js`, which is loaded only when you press the button:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/1DfVDv5poQmwXwOKmnvd.png?auto=format&amp;w=1600 1600w" width="800" height="665" /></figure>By default, Next.js names these dynamic chunks *number*.js, where *number* starts from 1.

In real-world applications, components are often [much larger](https://bundlephobia.com/result?p=moment@2.24.0), and lazy-loading them can trim your initial JavaScript payload by hundreds of kilobytes.

## Dynamic imports with custom loading indicator <a href="#dynamic-imports-with-custom-loading-indicator" class="w-headline-link">#</a>

When you lazy-load resources, it's good practice to provide a loading indicator in case there are any delays. In Next.js, you can do that by providing an additional argument to the `dynamic()` function:

    const Puppy = dynamic(() => import("../components/Puppy"), {
      loading: () => <p>Loading...</p>
    });

To see the loading indictor in action, simulate slow network connection in DevTools:

1.  To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

2.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.

3.  Click the **Network** tab.

4.  Select the **Disable cache** checkbox.

5.  In the **Throttling** drop-down list, select **Fast 3G**.

6.  Press the **Click me** button.

Now when you click the button it takes a while to load the component and the app displays the "Loading…" message in the meantime.

## <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/tjlpmwolBVp1jh948Fln.png?auto=format&amp;w=1600 1600w" width="800" height="663" /></figure>Dynamic imports without SSR <a href="#dynamic-imports-without-ssr" class="w-headline-link">#</a>

If you need to render a component only on the client side (for example, a chat widget) you can do that by setting the `ssr` option to `false`:

    const Puppy = dynamic(() => import("../components/Puppy"), {
      ssr: false,
    });

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

With support for dynamic imports, Next.js gives you component-level code splitting, which can minimize your JavaScript payloads and improve application load time. All components are server-side rendered by default and you can disable this option whenever necessary.

<span class="w-mr--sm">Last updated: Nov 8, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/code-splitting-with-dynamic-imports-in-nextjs/index.md)

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
