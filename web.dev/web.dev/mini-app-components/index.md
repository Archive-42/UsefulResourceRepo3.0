<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#mini-app-components" class="w-toc__header--link">Mini app components</a>
----------------------------------------------------------------------------------

-   [Web components](#web-components)
-   [Components in mini apps](#components-in-mini-apps)
-   [Custom components](#custom-components)
-   [Acknowledgements](#acknowledgements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Mini app components
===================

Mar 3, 2021 <span class="w-author__separator">•</span> Updated Mar 17, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/mini-apps" class="w-post-signpost__link">Mini apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

-   <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
-   <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
-   <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

This post is part of an article collection where each article builds upon previous articles. If you just landed here, you may want to start reading from the [beginning](/mini-app-super-apps/).

Web components <a href="#web-components" class="w-headline-link">#</a>
----------------------------------------------------------------------

[Web components](https://developer.mozilla.org/en-US/docs/Web/Web_Components/) started with the promise of letting developers piece them together and build great apps on top of them. Examples of such atomic components are GitHub's [time-elements](https://github.com/github/time-elements), Stefan Judis' [web-vitals-element](https://github.com/stefanjudis/web-vitals-element), or, shameless plug, Google's [dark mode toggle](https://github.com/GoogleChromeLabs/dark-mode-toggle/). When it comes to complete design systems, however, I have observed that people prefer to rely on a coherent set of components from the same vendor. An incomplete list of examples includes SAP's [UI5 Web Components](https://sap.github.io/ui5-webcomponents/), the [Polymer Elements](https://www.webcomponents.org/author/PolymerElements), [Vaadin's elements](https://www.webcomponents.org/author/vaadin), Microsoft's [FAST](https://github.com/microsoft/fast), the [Material Web Components](https://github.com/material-components/material-components-web-components), arguably the [AMP components](https://amp.dev/documentation/components/), and many more. Due to a number of factors out of scope for this article, a lot of developers, however, have also flocked to frameworks like [React](https://reactjs.org/), [Vue.js](https://vuejs.org/), [Ember.js](https://emberjs.com/), etc. Rather than giving the developer the freedom to choose from any of these options (or, dependent on your viewpoint, *forcing* them to make a technology choice), super app providers universally supply a set of components that developers must use.

Components in mini apps <a href="#components-in-mini-apps" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------

You can think of these components like any of the component libraries mentioned above. To get an overview of the available components, you can browse [WeChat's component library](https://developers.weixin.qq.com/miniprogram/en/dev/component/), [ByteDance's components](https://microapp.bytedance.com/docs/zh-CN/mini-app/develop/component/all), [Alipay's components](https://opendocs.alipay.com/mini/component), [Baidu's](https://smartprogram.baidu.com/docs/develop/component/component/), and [Quick App components](https://doc.quickapp.cn/widgets/common-events.html).

Earlier [I showed](/mini-app-devtools/#custom-elements-under-the-hood) that while, for example, WeChat's `<image>` is a web component under the hood, not all of these components are technically web components. Some components, like `<map>` and `<video>`, are rendered as [OS-built-in components](https://developers.weixin.qq.com/ebook?action=get_post_info&docid=000caab39b88b06b00863ab085b80a) that get layered over the WebView. For the developer, this implementation detail is not revealed, they are programmed like any other component.

As always, the details vary, but the overall programming concepts are the same across all super app providers. An important concept is data binding, as shown before in [Markup languages](/mini-app-markup-styling-and-scripting/#markup-languages). Generally, components are grouped by function, so finding the right one for the job is easier. Below is an example from Alipay's categorization, which is similar to the component grouping of other vendors.

-   View containers
    -   `view`
    -   `swiper`
    -   `scroll-view`
    -   `cover-view`
    -   `cover-image`
    -   `movable-view`
    -   `movable-area`
-   Basic content
    -   `text`
    -   `icon`
    -   `progress`
    -   `rich-text`
-   Form components
    -   `button`
    -   `form`
    -   `label`
    -   `input`
    -   `textarea`
    -   `radio`
    -   `radio-group`
    -   `checkbox`
    -   `checkbox-group`
    -   `switch`
    -   `slider`
    -   `picker-view`
    -   `picker`
-   Navigation
    -   `navigator`
-   Media components
    -   `image`
    -   `video`
-   Canvas
    -   `canvas`
-   Map
    -   `map`
-   Open components
    -   `web-view`
    -   `lifestyle`
    -   `contact-button`
-   Accessibility
    -   `aria-component`

Below, you can see Alipay's [`<image>`](https://opendocs.alipay.com/mini/component/image) used in an `a:for` directive (see [List rendering](/mini-app-markup-styling-and-scripting/#list-rendering)) that loops over an image data array provided in `index.js`.

    /* index.js */
    Page({
      data: {
        array: [
          {
            mode: "scaleToFill",
            text: "scaleToFill",
          },
          {
            mode: "aspectFit",
            text: "aspectFit",
          },
        ],
        src: "https://images.example.com/sample.png",
      },
      imageError(e) {
        console.log("image", e.detail.errMsg);
      },
      onTap(e) {
        console.log("image tap", e);
      },
      imageLoad(e) {
        console.log("image", e);
      },
    });

    <!-- index.axml -->
    <view class="page">
      <view class="page-section" a:for="{{array}}" a:for-item="item">
        <view class="page-section-demo" onTap="onTap">
          <image
            class="image"
            mode="{{item.mode}}"
            onTap="onTap"
            onError="imageError"
            onLoad="imageLoad"
            src="{{src}}"
            lazy-load="true"
            default-source="https://images.example.com/loading.png"
          />
        </view>
      </view>
    </view>

Note the data binding of the `item.mode` to the `mode` attribute, the `src` to the `src` attribute, and the three event handlers `onTap`, `onError`, and `onLoad` to the functions of the same name. As shown [before](/mini-app-devtools/#custom-elements-under-the-hood), the `<image>` tag internally gets converted into a `<div>` with a placeholder of the image's final dimensions, optional lazy-loading, a default source, etc.

The available configuration options of the component are all listed in the [documentation](https://opendocs.alipay.com/mini/component/image). An embedded-in-the-docs [component preview with simulator](https://herbox-embed.alipay.com/s/doc-image?chInfo=openhome-doc&theme=light) makes the code immediately tangible.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format" alt="Alipay component documentation with embedded component preview." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/t2Y6WWsRhp6LjThxROUo.png?auto=format&amp;w=1600 1600w" width="800" height="510" /><figcaption>Alipay component documentation with embedded component preview.</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format" alt="Alipay component preview popped out into its own tab." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/xu2F51XL9Z0M3Z9n6n2O.png?auto=format&amp;w=1600 1600w" width="800" height="514" /><figcaption>Alipay component preview popped out into its own tab.</figcaption></figure>Each component also has a QR code that can be scanned with the Alipay app that opens the component example in a self-contained minimal example.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format" alt="Preview of the Alipay &lt;image&gt; component on a real device after following a QR code link from the docs." sizes="(min-width: 300px) 300px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/gaWqLG5GqeqqfbhWz8D1.png?auto=format&amp;w=600 600w" width="300" height="649" /><figcaption>Preview of the Alipay <code>&lt;image&gt;</code> component on a real device after following a <a href="https://qr.alipay.com/s6x01278ucjhjyknjd5ow53">QR code link</a> from the docs.</figcaption></figure>Developers can jump from the documentation straight into Alipay DevTools IDE by leveraging a proprietary URI scheme `antdevtool-tiny://`. This allows the documentation to link directly into a to-be-imported mini app project, so developers can get started with the component immediately.

Custom components <a href="#custom-components" class="w-headline-link">#</a>
----------------------------------------------------------------------------

Apart from using the vendor-provided components, developers can also create custom components. The concept exists for [WeChat](https://developers.weixin.qq.com/miniprogram/en/dev/framework/custom-component/), [ByteDance](https://microapp.bytedance.com/docs/zh-CN/mini-app/develop/guide/custom-component/custom-component), [Alipay](https://opendocs.alipay.com/mini/framework/component_configuration), and [Baidu](https://smartprogram.baidu.com/docs/develop/framework/custom-component/), as well as [Quick App](https://doc.quickapp.cn/tutorial/framework/parent-child-component-communication.html#%E7%BB%84%E4%BB%B6%E8%87%AA%E5%AE%9A%E4%B9%89). For example, a Baidu custom component consists of four files that must reside in the same folder: `custom.swan`, `custom.css`, `custom.js`, and `custom.json`.

The file `custom.json` denotes the folder contents as a custom component.

    {
      "component": true
    }

The file `custom.swan` contains the markup and `custom.css` the CSS.

    <view class="name" bindtap="tap">{{name}} {{age}}</view>

    .name {
      color: red;
    }

The file `custom.js` contains the logic. The component lifecycle functions are `attached()`, `detached()`, `created()`, and `ready()`. The component can additionally also react on [page lifecycle events](/mini-app-project-structure-lifecycle-and-bundling/#mini-app-lifecycle), namely `show()` and `hide()`.

    Component({
      properties: {
        name: {
          type: String,
          value: "swan",
        },
      },
      data: {
        age: 1,
      },
      methods: {
        tap: function () {},
      },
      lifetimes: {
        attached: function () {},
        detached: function () {},
        created: function () {},
        ready: function () {},
      },
      pageLifetimes: {
        show: function () {},
        hide: function () {},
      },
    });

The custom component can then be imported in `index.json`, the key of the import determines the name (here: `"custom"`) that the custom component can then be used with in `index.swan`.

    {
      "usingComponents": {
        "custom": "/components/custom/custom"
      }
    }

    <view>
      <custom name="swanapp"></custom>
    </view>

**Success**: Continue reading to learn about the [project structure, lifecycle, and bundling](/mini-app-project-structure-lifecycle-and-bundling/) of mini apps.

Acknowledgements <a href="#acknowledgements" class="w-headline-link">#</a>
--------------------------------------------------------------------------

This article was reviewed by [Joe Medley](https://github.com/jpmedley), [Kayce Basques](https://github.com/kaycebasques), [Milica Mihajlija](https://github.com/mihajlija), [Alan Kent](https://github.com/alankent), and Keith Gu.

<a href="/tags/mini-apps/" class="w-chip">Mini apps</a>

<span class="w-mr--sm">Last updated: Mar 17, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/mini-apps/mini-app-components/index.md)

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
