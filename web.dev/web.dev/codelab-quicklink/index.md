





# Prefetching in create-react-app with Quicklink

Jun 8, 2020

[<img src="https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Addy Osmani" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/1L2RBhCLSnXjCnSlevaDjy3vba73/LJyNTOzyWbowv2mrlzPS.jpeg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/addyosmani/)

<a href="/authors/addyosmani/" class="w-author__name-link">Addy Osmani</a>

- <a href="https://twitter.com/addyosmani" class="w-author__link">Twitter</a>
- <a href="https://github.com/addyosmani" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Demian Renzulli" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/EuTrT82fyivFn16L0vD9.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/demianrenzulli/)

<a href="/authors/demianrenzulli/" class="w-author__name-link">Demian Renzulli</a>

- <a href="https://twitter.com/drenzulli" class="w-author__link">Twitter</a>
- <a href="https://github.com/demianrenzulli" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@demianrenzulli" class="w-author__link">Glitch</a>

[<img src="https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Anton Karlovskiy" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/IkUjDRwWBvgvkMuXmlad.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/antonkarlovskiy/)

<a href="/authors/antonkarlovskiy/" class="w-author__name-link">Anton Karlovskiy</a>

- <a href="https://twitter.com/antonkarlovskiy" class="w-author__link">Twitter</a>
- <a href="https://github.com/anton-karlovskiy" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@anton-karlovskiy" class="w-author__link">Glitch</a>

This codelab uses [Chrome DevTools](https://www.google.com/chrome/). Download Chrome if you don't already have it.

This codelab shows you how to implement the [Quicklink](/quicklink) library in a React SPA demo to demonstrate how prefetching speeds up subsequent navigations.

## Measure <a href="#measure" class="w-headline-link">#</a>

Before adding optimizations, it's always a good idea to first analyze the current state of the application.

- Click **Remix to Edit** to make the project editable.
- To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).

The website is a simple demo built with [create-react-app](https://reactjs.org/docs/create-a-new-react-app.html).

Complete the following instructions in the new tab that just opened:

1.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
2.  Click the **Network** tab.
3.  Select the **Disable cache** checkbox.
4.  In the [Throttling drop-down list](https://developers.google.com/web/tools/chrome-devtools/network/reference#throttling), select **Fast 3G** to simulate a slow connection type.
5.  Reload the app.
6.  Type `chunk` into the [Filter textbox](https://developers.google.com/web/tools/chrome-devtools/network/reference#filter-by-property) to hide any resources that do not include `chunk` in their name.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format" alt="Network panel showing the home page chunks." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DCl6nkEfsVukurm8gBsy.png?auto=format&amp;w=1600 1600w" width="800" height="194" />

The site uses [route-based code splitting](/reduce-javascript-payloads-with-code-splitting/), thanks to which only the necessary code is requested at the beginning.

1.  [Clear the network requests in DevTools](https://developers.google.com/web/tools/chrome-devtools/network/reference#clear).
2.  Within the app, click the **Blog** link to navigate to that page.

The JS and CSS chunks for the new route are loaded to render the page.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format" alt="Network panel showing the blog page chunks." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/23QuiFZwo7rouJaqmz9m.png?auto=format&amp;w=1600 1600w" width="800" height="119" />

Next, you'll implement Quicklink in this site, so that these chunks can be prefetched in the home page, making the navigation faster.

This allows you to combine the best of both techniques:

- Route-based code splitting tells the browser to only load the necessary chunks at a higher priority at page load time.
- Prefetching tells the browser to load the chunks for in-viewport links at the lowest priority, during the browser's idle time.

## Configure `webpack-route-manifest` <a href="#configure-webpack-route-manifest" class="w-headline-link">#</a>

The first step is to install and configure [webpack-route-manifest](https://github.com/lukeed/webpack-route-manifest), a webpack plugin that lets you generate a manifest file associating routes with their corresponding chunks.

Usually, you would need to install the library, but we've already done it for you. Here's the command that you would need to run:

    npm install webpack-route-manifest --save-dev

`config-overrides.js` is a file placed in your project root directory where you can override existing behaviour of the webpack configuration, without having to [eject the project](https://github.com/facebook/create-react-app/blob/master/packages/cra-template/template/README.md#npm-run-eject).

- To view the source, press **View Source**.

Open `config-overrides.js` for edit and add the `webpack-route-manifest` dependency at the beginning of the file:

    const path = require('path');
    const RouteManifest = require('webpack-route-manifest');

Next, configure the `webpack-route-manifest` plugin by adding the following code to the bottom of `config-overrides.js`:

    module.exports = function override(config) {
      config.resolve = {
        ...config.resolve,
        alias: {
          '@assets': `${path.resolve(__dirname, 'src/assets')}`,
          '@pages': `${path.resolve(__dirname, 'src/pages')}`,
          '@components': `${path.resolve(__dirname, 'src/components')}`,
        },
      };

      config.plugins.push(
        new RouteManifest({
          minify: true,
          filename: 'rmanifest.json',
          routes(str) {
            let out = str.replace('@pages', '').toLowerCase();
            if (out === '/article') return '/blog/:title';
            if (out === '/home') return '/';
            return out;
          },
        }),
      );

      return config;
    };

The new code does the following:

- `config.resolve` declares variables with the internal routes to pages, assets and components.
- `config.plugins.push()` creates a `RouteManifest` object and passes it the configuration so that the `rmanifest.json` file can be generated based on the site's routes and chunks.

The `manifest.json` file will be generated and made available at `https://site_url/rmanifest.json`.

## Configure quicklink <a href="#configure-quicklink" class="w-headline-link">#</a>

At this point you would need to install the Quicklink library in your project. For simplicity, we already added it to the project. Here's the command that you would need to run:

    npm install --save quicklink

Open `src/components/App/index.js` for edit.

First, import the Quicklink higher order component (HOC):

    import React, { lazy, Suspense } from 'react';
    import { Route } from 'react-router-dom';

    import Footer from '@components/Footer';
    import Hero from '@components/Hero';
    import style from './index.module.css';
    import { withQuicklink } from 'quicklink/dist/react/hoc.js';

    const Home = lazy(() => import(/* webpackChunkName: "home" */ '@pages/Home'));
    const About = lazy(() => import(/* webpackChunkName: "about" */ '@pages/About'));
    const Article = lazy(() => import(/* webpackChunkName: "article" */ '@pages/Article'));
    const Blog = lazy(() => import(/* webpackChunkName: "blog" */ '@pages/Blog'));

Next, create an `options` object after the `Blog` variable declaration, to use as an argument when calling `quicklink`:

    const options = {
      origins: []
    };

Finally, wrap each route with the `withQuicklink()` higher order component, passing it an `options` parameter and the target component for that route:

    const App = () => (
      <div className={style.app}>
        <Hero />
        <main className={style.wrapper}>
          <Suspense fallback={<div>Loading...</div>}>
            <Route path="/" exact component={withQuicklink(Home, options)} />
            <Route path="/blog" exact component={withQuicklink(Blog, options)} />
            <Route
              path="/blog/:title"
              component={withQuicklink(Article, options)}
            />
            <Route path="/about" exact component={withQuicklink(About, options)} />
          </Suspense>
        </main>
        <Footer />
      </div>
    );

The previous code instructs to prefetch chunks for the routes wrapped with `withQuicklink()`, when the link comes into the view.

If Glitch throws an error at this point about the lack of a dependency, try opening the Glitch Terminal (**Tools** &gt; **Terminal**), running `refresh` in the Terminal, then running `npm run build`.

## Measure again <a href="#measure-again" class="w-headline-link">#</a>

Repeat the first 6 steps from [Measure](#measure). Don't navigate to the blog page yet.

When the home page loads the chunks for that route are loaded. After that, Quicklink prefetches the route's chunks for the in-viewport links:

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format" alt="Network panel showing the home page prefetching chunks." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lClOmOYDx8Cg3RZakAu2.png?auto=format&amp;w=1600 1600w" width="800" height="286" />

These chunks are requested at the lowest priority and without blocking the page.

Next:

1.  Clear the Network log again.
2.  Disable the **Disable cache** checkbox.
3.  Click the **Blog** link to navigate to that page.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format" alt="Network panel showing the blog page with chunks picked up from cache." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/bJJYT3gDIWU9PeeXSdOE.png?auto=format&amp;w=1600 1600w" width="800" height="95" />

The **Size** column indicates that these chunks were retrieved from the "prefetch cache", instead of the network. Loading these chunks without a Quicklink took approximately **580ms**. Using the library it now takes **2ms**, which represents a **99% reduction**!

<a href="/quicklink" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to article</a>

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
