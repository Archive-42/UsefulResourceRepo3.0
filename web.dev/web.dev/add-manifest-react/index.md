





<img src="https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/pOjpReVK54kUJP6nZMwn.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#add-a-web-app-manifest-with-create-react-app" class="w-toc__header--link">Add a web app manifest with Create React App</a>

- [Why is this useful?](#why-is-this-useful)
- [Modify the default manifest](#modify-the-default-manifest)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Add a web app manifest with Create React App

A web app manifest is included into Create React App by default and allows anyone to install your React application on their device.

Apr 29, 2019 <span class="w-author__separator">•</span> Updated May 19, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

- <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
- <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
- <a href="https://houssein.me/" class="w-author__link">Blog</a>

If you don't know how web app manifest files work, refer to the [Add a web app manifest](/add-manifest) guide first.

Create React App (CRA) includes a web app manifest by default. Modifying this file will allow you to change how your application is displayed when installed on the user's device.

## <figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format" sizes="(min-width: 317px) 317px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yra3Y2jPf2tS5ELxJdAK.png?auto=format&amp;w=634 634w" width="317" height="640" /></figure>Why is this useful? <a href="#why-is-this-useful" class="w-headline-link">#</a>

Web app manifest files provide the capability to change how an installed application will look like on the user's desktop or mobile device. By modifying properties in the JSON file, you can modify a number of details in your application, including its:

- Name
- Description
- App icon
- Theme color

The [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/Manifest) covers all the properties that can be changed in detail.

## Modify the default manifest <a href="#modify-the-default-manifest" class="w-headline-link">#</a>

In CRA, a default manifest file, `/public/manifest.json` is included automatically when a new app is created:

    {
      "short_name": "React App",
      "name": "Create React App Sample",
      "icons": [
        {
          "src": "favicon.ico",
          "sizes": "64x64 32x32 24x24 16x16",
          "type": "image/x-icon"
        },
        {
          "src": "logo192.png",
          "type": "image/png",
          "sizes": "192x192"
        },
        {
          "src": "logo512.png",
          "type": "image/png",
          "sizes": "512x512"
        }
      ],
      "start_url": ".",
      "display": "standalone",
      "theme_color": "#000000",
      "background_color": "#ffffff"
    }

This allows anybody to install the application on their device and see some default details of the application. The HTML file, `public/index.html`, also includes a `<link>` element to load the manifest.

    <link rel="manifest" href="%PUBLIC_URL%/manifest.json" />

Here is an example of an application built with CRA that has a modified manifest file:

To find out if all the properties are working correctly in this example:

- To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).
- Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
- Click the **Application** tab.
- In the **Application** panel, click the **Manifest** tab.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format" alt="DevTool&#39;s Manifest tab shows the properties from the app manifest file." class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IpK9fr3O0zEX1GJXq9mw.png?auto=format&amp;w=1600 1600w" width="800" height="695" />

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

1.  If you're building a site that you think does not need to be installed on a device, remove the manifest and the `<link>` element in the HTML file that points to it.
2.  If you would like users to install the application on their device, modify the manifest file (or create one if you are not using CRA) with any properties that you like. The [MDN documentation](https://developer.mozilla.org/en-US/docs/Web/Manifest) explains all the required and optional attributes.

<span class="w-mr--sm">Last updated: May 19, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/add-manifest-react/index.md)

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
