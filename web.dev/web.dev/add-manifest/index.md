<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#add-a-web-app-manifest" class="w-toc__header--link">Add a web app manifest</a>

- [Create the manifest file](#create)
- [Key manifest properties](#manifest-properties)
- [Add the web app manifest to your pages](#link-manifest)
- [Test your manifest](#test-manifest)
- [Splash screens on mobile](#splash-screen)
- [Further reading](#further-reading)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Add a web app manifest

Nov 5, 2018 <span class="w-author__separator">•</span> Updated Jun 21, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/progressive-web-apps" class="w-post-signpost__link">Progressive Web Apps</a>

[<img src="https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Pete LePage" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/0g2WvpbGRGdVs0aAPc6ObG7gkud2/3rFbsLsMMk1VveHfBRSu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/petelepage/)

<a href="/authors/petelepage/" class="w-author__name-link">Pete LePage</a>

- <a href="https://twitter.com/petele" class="w-author__link">Twitter</a>
- <a href="https://github.com/petele" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@petele" class="w-author__link">Glitch</a>
- <a href="https://petelepage.com" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/mXjY3z3JmrispGtu9yn6.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="François Beaufort" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/mXjY3z3JmrispGtu9yn6.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/mXjY3z3JmrispGtu9yn6.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/mXjY3z3JmrispGtu9yn6.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/mXjY3z3JmrispGtu9yn6.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/mXjY3z3JmrispGtu9yn6.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/beaufortfrancois/)

<a href="/authors/beaufortfrancois/" class="w-author__name-link">François Beaufort</a>

- <a href="https://github.com/beaufortfrancois" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

- <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
- <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
- <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

The web app manifest is a JSON file that tells the browser about your Progressive Web App and how it should behave when installed on the user's desktop or mobile device. A typical manifest file includes the app name, the icons the app should use, and the URL that should be opened when the app is launched.

Manifest files are [supported](https://developer.mozilla.org/en-US/docs/Web/Manifest#Browser_compatibility) in Chrome, Edge, Firefox, UC Browser, Opera, and the Samsung browser. Safari has partial support.

## Create the manifest file <a href="#create" class="w-headline-link">#</a>

The manifest file can have any name, but is commonly named `manifest.json` and served from the root (your website's top-level directory). The specification suggests the extension should be `.webmanifest`, but browsers also support `.json` extensions, which is may be easier for developers to understand.

    {
      "short_name": "Weather",
      "name": "Weather: Do I need an umbrella?",
      "icons": [
        {
          "src": "/images/icons-192.png",
          "type": "image/png",
          "sizes": "192x192"
        },
        {
          "src": "/images/icons-512.png",
          "type": "image/png",
          "sizes": "512x512"
        }
      ],
      "start_url": "/?source=pwa",
      "background_color": "#3367D6",
      "display": "standalone",
      "scope": "/",
      "theme_color": "#3367D6",
      "shortcuts": [
        {
          "name": "How's weather today?",
          "short_name": "Today",
          "description": "View weather information for today",
          "url": "/today?source=pwa",
          "icons": [{ "src": "/images/today.png", "sizes": "192x192" }]
        },
        {
          "name": "How's weather tomorrow?",
          "short_name": "Tomorrow",
          "description": "View weather information for tomorrow",
          "url": "/tomorrow?source=pwa",
          "icons": [{ "src": "/images/tomorrow.png", "sizes": "192x192" }]
        }
      ],
      "description": "Weather forecast information",
      "screenshots": [
        {
          "src": "/images/screenshot1.png",
          "type": "image/png",
          "sizes": "540x720"
        },
        {
          "src": "/images/screenshot2.jpg",
          "type": "image/jpg",
          "sizes": "540x720"
        }
      ]
    }

### Key manifest properties <a href="#manifest-properties" class="w-headline-link">#</a>

#### `short_name` and/or `name` <a href="#name" class="w-headline-link">#</a>

You must provide at least the `short_name` or `name` property. If both are provided, `short_name` is used on the user's home screen, launcher, or other places where space may be limited. `name` is used when the app is installed.

#### `icons` <a href="#icons" class="w-headline-link">#</a>

When a user installs your PWA, you can define a set of icons for the browser to use on the home screen, app launcher, task switcher, splash screen, and so on.

The `icons` property is an array of image objects. Each object must include the `src`, a `sizes` property, and the `type` of image. To use [maskable icons](/maskable-icon/), sometimes referred to as adaptive icons on Android, you'll also need to add `"purpose": "any maskable"` to the `icon` property.

For Chrome, you must provide at least a 192x192 pixel icon, and a 512x512 pixel icon. If only those two icon sizes are provided, Chrome will automatically scale the icons to fit the device. If you'd prefer to scale your own icons, and adjust them for pixel-perfection, provide icons in increments of 48dp.

#### `start_url` <a href="#start-url" class="w-headline-link">#</a>

The `start_url` is required and tells the browser where your application should start when it is launched, and prevents the app from starting on whatever page the user was on when they added your app to their home screen.

Your `start_url` should direct the user straight into your app, rather than a product landing page. Think about what the user will want to do once they open your app, and place them there.

#### `background_color` <a href="#background-color" class="w-headline-link">#</a>

The `background_color` property is used on the splash screen when the application is first launched on mobile.

#### `display` <a href="#display" class="w-headline-link">#</a>

You can customize what browser UI is shown when your app is launched. For example, you can hide the address bar and browser chrome. Games can even be made to launch full screen.

<table><colgroup><col style="width: 50%" /><col style="width: 50%" /></colgroup><thead><tr class="header"><th><strong>Property</strong></th><th><strong>Use</strong></th></tr></thead><tbody><tr class="odd"><td><code>fullscreen</code></td><td>Opens the web application without any browser UI and takes up the entirety of the available display area.</td></tr><tr class="even"><td><code>standalone</code></td><td>Opens the web app to look and feel like a standalone app. The app runs in its own window, separate from the browser, and hides standard browser UI elements like the URL bar.<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/XdBsDeRZozIyXyiXA59n.png?auto=format&amp;w=1600 1600w" width="800" height="196" /></figure></td></tr><tr class="odd"><td><code>minimal-ui</code></td><td>This mode is similar to <code>standalone</code>, but provides the user a minimal set of UI elements for controlling navigation (such as back and reload).<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/trPwjcMio7tBKGBNoT9u.png?auto=format&amp;w=1600 1600w" width="800" height="196" /></figure></td></tr><tr class="even"><td><code>browser</code></td><td>A standard browser experience.</td></tr></tbody></table>

#### `display_override` <a href="#display-override" class="w-headline-link">#</a>

Web apps can choose how they are displayed by setting a `display` mode in their manifest as [explained above](#display). Browsers are _not_ required to support all display modes, but they _are_ required to support the [spec-defined fallback chain](https://w3c.github.io/manifest/#dfn-fallback-display-mode) (`"fullscreen"` → `"standalone"` → `"minimal-ui"` → `"browser"`). If they don't support a given mode, they fall back to the next display mode in the chain. This inflexible behavior can be problematic in rare cases, for example, a developer cannot request `"minimal-ui"` without being forced back into the `"browser"` display mode when `"minimal-ui"` is not supported. Another problem is that the current behavior makes it impossible to introduce new display modes in a backward compatible way, since explorations like tabbed application mode don't have a natural place in the fallback chain.

These problems are solved by the `display_override` property, which the browser considers _before_ the `display` property. Its value is a sequence of strings that are considered in the listed order, and the first supported display mode is applied. If none are supported, the browser falls back to evaluating the `display` field.

In the example below, the display mode fallback chain would be as follows. (The details of `"window-control-overlay"` are out-of-scope for this article.)

1.  `"window-control-overlay"` (First, look at `display_override`.)
2.  `"minimal-ui"`
3.  `"standalone"` (When `display_override` is exhausted, evaluate `display`.)
4.  `"minimal-ui"` (Finally, use the `display` fallback chain.)
5.  `"browser"`

<!-- -->

    {
      "display_override": ["window-control-overlay", "minimal-ui"],
      "display": "standalone",
    }

The browser will not consider `display_override` unless `display` is also present.

#### `scope` <a href="#scope" class="w-headline-link">#</a>

The `scope` defines the set of URLs that the browser considers to be within your app, and is used to decide when the user has left the app. The `scope` controls the URL structure that encompasses all the entry and exit points in your web app. Your `start_url` must reside within the `scope`.

**Caution**: If the user clicks a link in your app that navigates outside of the `scope`, the link will open and render within the existing PWA window. If you want the link to open in a browser tab, you must add `target="_blank"` to the `<a>` tag. On Android, links with `target="_blank"` will open in a [Chrome Custom Tab](https://developer.chrome.com/multidevice/android/customtabs).

A few other notes on `scope`:

- If you don't include a `scope` in your manifest, then the default implied `scope` is the directory that your web app manifest is served from.
- The `scope` attribute can be a relative path (`../`), or any higher level path (`/`) which would allow for an increase in coverage of navigations in your web app.
- The `start_url` must be in the scope.
- The `start_url` is relative to the path defined in the `scope` attribute.
- A `start_url` starting with `/` will always be the root of the origin.

#### `theme_color` <a href="#theme-color" class="w-headline-link">#</a>

The `theme_color` sets the color of the tool bar, and may be reflected in the app's preview in task switchers. The `theme_color` should match the `meta` theme color specified in your document head.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/8mkBdT3O0FZLo0PUppvv.png?auto=format&amp;w=1600 1600w" width="800" height="196" /></figure>As of Chromium 93 and Safari 15, you can adjust this color based on a media query with the `media` attribute of the `meta` theme color element. The first one that matches will be picked. For example, you could have one color for light mode and another one for dark mode. At the time of writing, you can't define those in your manifest. See [w3c/manifest\#975 GitHub issue](https://github.com/w3c/manifest/issues/975).

    <meta name="theme-color" media="(prefers-color-scheme: light)" content="white">
    <meta name="theme-color" media="(prefers-color-scheme: dark)"  content="black">

#### `shortcuts` <a href="#shortcuts" class="w-headline-link">#</a>

The `shortcuts` property is an array of [app shortcut](/app-shortcuts) objects whose goal is to provide quick access to key tasks within your app. Each member is a dictionary that contains at least a `name` and a `url`.

#### `description` <a href="#description" class="w-headline-link">#</a>

The `description` property describes the purpose of your app.

#### `screenshots` <a href="#screenshots" class="w-headline-link">#</a>

The `screenshots` property is an array of image objects, representing your app in common usage scenarios. Each object must include the `src`, a `sizes` property, and the `type` of image.

In Chrome, the image must respond to certain criteria:

- Width and height must be at least 320px and at most 3840px.
- The maximum dimension can't be more than 2.3 times as long as the minimum dimension.
- Screenshots must have the same aspect ratio.
- Only JPEG and PNG image formats are supported.

**Gotchas!**

The `description` and `screenshots` properties are currently used only in Chrome for Android when a user wants to install your app. The experimental flag `about://flags/#mobile-pwa-install-use-bottom-sheet` flag must be enabled in Chrome 90.

## Add the web app manifest to your pages <a href="#link-manifest" class="w-headline-link">#</a>

After creating the manifest, add a `<link>` tag to all the pages of your Progressive Web App. For example:

    <link rel="manifest" href="/manifest.json">

**Gotchas!**

The request for the manifest is made **without** credentials (even if it's on the same domain), thus if the manifest requires credentials, you must include `crossorigin="use-credentials"` in the manifest tag.

## Test your manifest <a href="#test-manifest" class="w-headline-link">#</a>

To verify your manifest is setup correctly, use the **Manifest** pane in the **Application** panel of Chrome DevTools.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FpIOY0Ak6FAA5xMuB9IT.png?auto=format&amp;w=1600 1600w" width="800" height="601" /></figure>This pane provides a human-readable version of many of your manifest's properties, and makes it easy to verify that all of the images are loading properly.

## Splash screens on mobile <a href="#splash-screen" class="w-headline-link">#</a>

When your app first launches on mobile, it can take a moment for the browser to spin up, and the initial content to begin rendering. Instead of showing a white screen that may look to the user like the app is stalled, the browser will show a splash screen until the first paint.

Chrome automatically creates the splash screen from the manifest properties, specifically:

- `name`
- `background_color`
- `icons`

The `background_color` should be the same color as the load page, to provide a smooth transition from the splash screen to your app.

Chrome will choose the icon that closely matches the device resolution for the device. Providing 192px and 512px icons is sufficient for most cases, but you can provide additional icons for pixel perfection.



## Further reading <a href="#further-reading" class="w-headline-link">#</a>

There are several additional properties that can be added to the web app manifest. Refer to the [MDN Web App Manifest documentation](https://developer.mozilla.org/en-US/docs/Web/Manifest) for more information. You can learn more about `display_override` in the [explainer](https://github.com/WICG/display-override/blob/master/explainer.md).

<a href="/tags/progressive-web-apps/" class="w-chip">Progressive Web Apps</a> <a href="/tags/web-app-manifest/" class="w-chip">Web App Manifest</a>

<span class="w-mr--sm">Last updated: Jun 21, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/progressive-web-apps/add-manifest/index.md)

<a href="/progressive-web-apps" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
