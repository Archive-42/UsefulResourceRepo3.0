





<img src="https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/Lk8KvDZcWntc7rtQzvv9.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#code-splitting-with-react.lazy-and-suspense" class="w-toc__header--link">Code splitting with React.lazy and Suspense</a>

- [Why is this useful?](#why-is-this-useful)
- [Suspense](#suspense)
- [Suspending multiple components](#suspending-multiple-components)
- [Handle loading failures](#handle-loading-failures)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Code splitting with React.lazy and Suspense

You never need to ship more code than necessary to your users, so split your bundles to make sure this never happens!

Apr 29, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

- <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
- <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
- <a href="https://houssein.me/" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Jeff Posnick" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/uskKSRCW1HyOTCjtdMdo.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/jeffposnick/)

<a href="/authors/jeffposnick/" class="w-author__name-link">Jeff Posnick</a>

- <a href="https://twitter.com/jeffposnick" class="w-author__link">Twitter</a>
- <a href="https://github.com/jeffposnick" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@jeffposnick" class="w-author__link">Glitch</a>
- <a href="https://twitter.com/jeffposnick" class="w-author__link">Blog</a>

If you don't yet understand the basic idea behind code splitting, refer to [Reduce JavaScript payloads with code splitting](/reduce-javascript-payloads-with-code-splitting) guide first.

The **`React.lazy`** method makes it easy to code-split a React application on a component level using dynamic imports.

    import React, { lazy } from 'react';

    const AvatarComponent = lazy(() => import('./AvatarComponent'));

    const DetailsComponent = () => (
      <div>
        <AvatarComponent />
      </div>
    )

## Why is this useful? <a href="#why-is-this-useful" class="w-headline-link">#</a>

A large React application will usually consist of many components, utility methods, and third-party libraries. If an effort isn't made to try to load different parts of an application only when they're needed, a single, large bundle of JavaScript will be shipped to your users as soon as they load the first page. This can affect page performance significantly.

The `React.lazy` function provides a built-in way to separate components in an application into separate chunks of JavaScript with very little legwork. You can then take care of loading states when you couple it with the `Suspense` component.

## Suspense <a href="#suspense" class="w-headline-link">#</a>

The problem with shipping a large JavaScript payload to users is the length of time it would take for the page to finish loading, especially on weaker devices and network connections. This is why code splitting and lazy loading is extremely useful.

However, there will always be a slight delay that users have to experience when a code-split component is being fetched over the network, so it's important to display a useful loading state. Using `React.lazy` with the **`Suspense`** component helps solve this problem.

    import React, { lazy, Suspense } from 'react';

    const AvatarComponent = lazy(() => import('./AvatarComponent'));

    const renderLoader = () => <p>Loading</p>;

    const DetailsComponent = () => (
      <Suspense fallback={renderLoader()}>
        <AvatarComponent />
      </Suspense>
    )

`Suspense` accepts a `fallback` component which allows you to display any React component as a loading state. The following example shows how this works. The avatar is only rendered when the button is clicked, where a request is then made to retrieve the code necessary for the suspended `AvatarComponent`. In the meantime, the fallback loading component is shown.

In here, the code that makes up `AvatarComponent` is small which is why the loading spinner only shows for a short amount of time. Larger components can take much longer to load, especially on weak network connections.

To better demonstrate how this works:

- To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).
- Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
- Click the **Network** tab.
- Click the **Throttling** dropdown, which is set to **No throttling** by default. Select **Fast 3G**.
- Click the **Click Me** button in the app.

The loading indicator will show for longer now. Notice how all the code that makes up the `AvatarComponent` is fetched as a separate chunk.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ga9IsnuJoJdnUfE6sGee.png?auto=format&amp;w=1600 1600w" width="800" height="478" /></figure>React does not currently support Suspense when components are being server-side rendered. If you are rendering on the server, consider using another library such as [`loadable-components`](https://www.smooth-code.com/open-source/loadable-components/docs/server-side-rendering/) which is recommended in the React docs.

## Suspending multiple components <a href="#suspending-multiple-components" class="w-headline-link">#</a>

Another feature of `Suspense` is that it allows you to suspend multiple components from loading, **even if they are all lazy loaded**.

For example:

    import React, { lazy, Suspense } from 'react';

    const AvatarComponent = lazy(() => import('./AvatarComponent'));
    const InfoComponent = lazy(() => import('./InfoComponent'));
    const MoreInfoComponent = lazy(() => import('./MoreInfoComponent'));

    const renderLoader = () => <p>Loading</p>;

    const DetailsComponent = () => (
      <Suspense fallback={renderLoader()}>
        <AvatarComponent />
        <InfoComponent />
        <MoreInfoComponent />
      </Suspense>
    )

This is an extremely useful way to delay rendering of multiple components while only showing a single loading state. Once all the components have finished fetching, the user gets to see them all displayed at the same time.

You can see this with the following embed:

Loading indicator showing a little too quickly? Try simulating a throttled connection in DevTools again.

Without this, it's easy to run into the problem of _staggered loading_, or different parts of a UI loading one after the other with each having their own loading indicator. This can make the user experience feel more jarring.

Although using Suspense to split components is already possible and makes it easy to trim down bundle sizes, the React team is continuing to work on more features that would extend this even further. The [React 16.x roadmap](https://reactjs.org/blog/2018/11/27/react-16-roadmap.html) explains this in more detail.

## Handle loading failures <a href="#handle-loading-failures" class="w-headline-link">#</a>

`Suspense` allows you to display a temporary loading state while network requests are made under the hood. But what if those network requests fail for some reason? You might be offline, or perhaps your web app is attempting to lazy-load a [versioned URL](/http-cache/#long-lived-caching-for-versioned-urls) that is out of date, and no longer available following a server redeployment.

React has a standard pattern for gracefully handling these types of loading failures: using an error boundary. As described [in the documentation](https://reactjs.org/docs/error-boundaries.html), any React component can serve as an error boundary if it implements either (or both) of the lifecycle methods `static getDerivedStateFromError()` or `componentDidCatch()`.

To detect and handle lazy-loading failures, you can wrap your `Suspense` component with a parent components that serves as an error boundary. Inside the error boundary's `render()` method, you can render the children as-is if there's no error, or render a custom error message if something goes wrong:

    import React, { lazy, Suspense } from 'react';

    const AvatarComponent = lazy(() => import('./AvatarComponent'));
    const InfoComponent = lazy(() => import('./InfoComponent'));
    const MoreInfoComponent = lazy(() => import('./MoreInfoComponent'));

    const renderLoader = () => <p>Loading</p>;

    class ErrorBoundary extends React.Component {
      constructor(props) {
        super(props);
        this.state = {hasError: false};
      }

      static getDerivedStateFromError(error) {
        return {hasError: true};
      }

      render() {
        if (this.state.hasError) {
          return <p>Loading failed! Please reload.</p>;
        }

        return this.props.children;
      }
    }

    const DetailsComponent = () => (
      <ErrorBoundary>
        <Suspense fallback={renderLoader()}>
          <AvatarComponent />
          <InfoComponent />
          <MoreInfoComponent />
        </Suspense>
      </ErrorBoundary>
    )

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

If you are unsure where to begin applying code splitting to your React application, follow these steps:

1.  Begin at the route level. Routes are the simplest way to identify points of your application that can be split. The [React docs](https://reactjs.org/docs/code-splitting.html#route-based-code-splitting) show how `Suspense` can be used along with [`react-router`](https://github.com/ReactTraining/react-router).
2.  Identify any large components on a page on your site that only render on certain user interactions (like clicking a button). Splitting these components will minimize your JavaScript payloads.
3.  Consider splitting anything else that is offscreen and not critical for the user.

<span class="w-mr--sm">Last updated: Apr 29, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/code-splitting-suspense/index.md)

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
