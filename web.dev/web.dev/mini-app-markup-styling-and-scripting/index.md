## <a href="#mini-app-markup-styling-and-scripting" class="w-toc__header--link">Mini app markup, styling, and scripting</a>

- [Markup languages](#markup-languages)
- [Data binding](#data-binding)
- [List rendering](#list-rendering)
- [Conditional rendering](#conditional-rendering)
- [Templates](#templates)
- [Styling](#styling)
- [Scripting](#scripting)
- [JavaScript bridge API](#javascript-bridge-api)
- [Acknowledgements](#acknowledgements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Mini app markup, styling, and scripting

Mar 3, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/mini-apps" class="w-post-signpost__link">Mini apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

- <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
- <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
- <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

This post is part of an article collection where each article builds upon previous articles. If you just landed here, you may want to start reading from the [beginning](/mini-app-super-apps/).

## Markup languages <a href="#markup-languages" class="w-headline-link">#</a>

As outlined before, rather than with plain HTML, mini apps are written with dialects of HTML. If you have ever dealt with [Vue.js](https://vuejs.org/) text interpolation and directives, you will feel immediately at home, but similar concepts existed way before that in XML Transformations ([XSLT](https://www.w3.org/TR/xslt-30/)). Below, you can see code samples from WeChat's [WXML](https://developers.weixin.qq.com/miniprogram/en/dev/framework/view/wxml/), but the concept is the same for all mini apps platforms, namely Alipay's [AXML](https://opendocs.alipay.com/mini/framework/axml), Baidu's [Swan Element](https://smartprogram.baidu.com/docs/develop/framework/dev/), ByteDance's [TTML](https://microapp.bytedance.com/docs/zh-CN/mini-app/develop/guide/mini-app-framework/view/ttml) (despite the DevTools calling it Bxml), and Quick App's [HTML](https://doc.quickapp.cn/tutorial/framework/for.html). Just like with Vue.js, the underlying mini app programming concept is the [model-view-viewmodel](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel) (MVVM).

### Data binding <a href="#data-binding" class="w-headline-link">#</a>

Data binding corresponds to Vue.js' [text interpolation](https://vuejs.org/v2/guide/syntax.html#Text).

    <!-- wxml -->
    <view>{{message}}</view>

    // page.js
    Page({
      data: {
        message: "Hello World!",
      },
    });

### List rendering <a href="#list-rendering" class="w-headline-link">#</a>

List rendering works like Vue.js [`v-for` directive](https://vuejs.org/v2/guide/list.html).

    <!-- wxml -->
    <view wx:for="{{array}}">{{item}}</view>

    // page.js
    Page({
      data: {
        array: [1, 2, 3, 4, 5],
      },
    });

### Conditional rendering <a href="#conditional-rendering" class="w-headline-link">#</a>

Conditional rendering works like Vue.js' [`v-if` directive](https://vuejs.org/v2/guide/conditional.html).

    <!-- wxml -->
    <view wx:if="{{view == 'one'}}">One</view>
    <view wx:elif="{{view == 'two'}}">Two</view>
    <view wx:else="{{view == 'three'}}">Three</view>

    // page.js
    Page({
      data: {
        view: "three",
      },
    });

### Templates <a href="#templates" class="w-headline-link">#</a>

Rather than requiring the imperative [cloning of the `content` of an HTML template](https://developer.mozilla.org/en-US/docs/Web/API/HTMLTemplateElement/content), WXML templates can be used declaratively via the `is` attribute that links to a template definition.

    <!-- wxml -->
    <template name="person">
      <view>
        First Name: {{firstName}}, Last Name: {{lastName}}
      </view>
    </template>

    <template is="person" data="{{...personA}}"></template>
    <template is="person" data="{{...personB}}"></template>
    <template is="person" data="{{...personC}}"></template>

    // page.js
    Page({
      data: {
        personA: { firstName: "Alice", lastName: "Foo" },
        personB: { firstName: "Bob", lastName: "Bar" },
        personC: { firstName: "Charly", lastName: "Baz" },
      },
    });

## Styling <a href="#styling" class="w-headline-link">#</a>

Styling happens with dialects of CSS. WeChat's is named [WXSS](https://developers.weixin.qq.com/miniprogram/en/dev/framework/quickstart/code.html#WXSS-Style). For Alipay, theirs is called [ACSS](https://opendocs.alipay.com/mini/framework/acss), Baidu's simply [CSS](https://smartprogram.baidu.com/docs/develop/framework/view_css/), and for ByteDance, their dialect is referred to as [TTSS](https://microapp.bytedance.com/docs/zh-CN/mini-app/develop/guide/mini-app-framework/view/ttss). What they have in common is that they extend CSS with responsive pixels. When writing regular CSS, developers need to convert all pixel units to adapt to different mobile device screens with different widths and pixel ratios. TTSS supports the `rpx` unit as its underlying layer, which means the mini app takes over the job from the developer and converts the units on their behalf, based on a specified screen width of `750rpx`. For example, on a Pixel 3a phone with a screen width of `393px` (and a device pixel ratio of `2.75`), responsive `200rpx` become `104px` on the real device when inspected with Chrome DevTools (393px / 750rpx \* 200rpx ≈ 104px). In Android, the same concept is called [density-independent pixel](https://developer.android.com/training/multiscreen/screendensities#TaskUseDP).

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format" alt="Inspecting the actual padding on a Pixel 3a device with Chrome DevTools." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/n26ptkMoSfiTDanfFh5F.png?auto=format&amp;w=1600 1600w" width="800" height="385" /><figcaption>Inspecting the actual padding on a Pixel 3a device with Chrome DevTools.</figcaption></figure>/* app.wxss */
    .container {
      height: 100%;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;
      padding: 200rpx 0; /* ← responsive pixels */
      box-sizing: border-box;
    }

Since components (see [later](/mini-app-components/)) do not use shadow DOM, styles declared on a page reach into all components. The common stylesheet file organization is to have one root stylesheet for global styles, and individual per-page stylesheets specific to each page of the mini app. Styles can be imported with an `@import` rule that behaves like the [`@import`](https://developer.mozilla.org/en-US/docs/Web/CSS/@import) CSS at-rule. Like in HTML, styles can also be declared inline, including dynamic text interpolation (see [before](/mini-app-markup-styling-and-scripting/#data-binding)).

    <view style="color:{{color}};" />

## Scripting <a href="#scripting" class="w-headline-link">#</a>

Mini apps support a "safe subset" of JavaScript that includes support for modules using varying syntaxes that remind of [CommonJS](http://www.commonjs.org/) or [RequireJS](https://requirejs.org/). JavaScript code cannot be executed via `eval()` and no functions can be created with `new Function()`. The scripting execution context is [V8](https://v8.dev/) or [JavaScriptCore](https://developer.apple.com/documentation/javascriptcore) on devices, and V8 or [NW.js](https://nwjs.io/) in the simulator. Coding with ES6 or newer syntax is usually possible, since the particular DevTools automatically transpile the code to ES5 if the build target is an operating system with an older WebView implementation (see [later](/mini-app-project-structure-lifecycle-and-bundling/#the-build-process)). The documentation of the super app providers explicitly mentions that their scripting languages are not to be confused with and are distinct from JavaScript. This statement, however, refers mostly just to the way modules work, that is, that they do not support standard [ES Modules](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Modules) yet.

As mentioned [before](/mini-app-markup-styling-and-scripting/#markup-languages), the mini app programming concept is the [model-view-viewmodel](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93viewmodel) (MVVM). The logic layer and the view layer run on different threads, which means the user interface does not get blocked by long-running operations. In web terms, you can think of scripts running in a [Web Worker](https://developer.mozilla.org/en-US/docs/Web/API/Web_Workers_API/Using_web_workers).

WeChat's scripting language is called [WXS](https://developers.weixin.qq.com/miniprogram/en/dev/reference/wxs/), Alipay's [SJS](https://opendocs.alipay.com/mini/framework/sjs), ByteDance's likewise [SJS](https://microapp.bytedance.com/docs/zh-CN/mini-app/develop/framework/sjs-syntax-reference/sjs-introduction/). Baidu speaks of [JS](https://smartprogram.baidu.com/docs/develop/framework/devjs/) when referencing theirs. These scripts need to be included using a special kind of tag, for example, `<wxs>` in WeChat. In contrast, Quick App uses regular `<script>` tags and the ES6 [JS](https://doc.quickapp.cn/framework/script.html) syntax.

    <wxs module="m1">
      var msg = "hello world";
      module.exports.message = msg;
    </wxs>

    <view>{{m1.message}}</view>

Modules can also be loaded via a `src` attribute, or imported via `require()`.

    // /pages/tools.wxs
    var foo = "'hello world' from tools.wxs";
    var bar = function (d) {
      return d;
    };
    module.exports = {
      FOO: foo,
      bar: bar,
    };
    module.exports.msg = "some msg";

    <!-- page/index/index.wxml -->
    <wxs src="./../tools.wxs" module="tools" />
    <view>{{tools.msg}}</view>
    <view>{{tools.bar(tools.FOO)}}</view>

    // /pages/logic.wxs
    var tools = require("./tools.wxs");

    console.log(tools.FOO);
    console.log(tools.bar("logic.wxs"));
    console.log(tools.msg);

### JavaScript bridge API <a href="#javascript-bridge-api" class="w-headline-link">#</a>

The JavaScript bridge that connects mini apps with the operating system makes it possible to use OS capabilities (see [Access to powerful features](/mini-app-about/#access-to-powerful-features). It also offers a number of convenience methods. For an overview, you can check out the different APIs of [WeChat](https://developers.weixin.qq.com/miniprogram/en/dev/api/), [Alipay](https://opendocs.alipay.com/mini/api), [Baidu](https://smartprogram.baidu.com/docs/develop/api/apilist/), [ByteDance](https://microapp.bytedance.com/docs/zh-CN/mini-app/develop/api/foundation/tt-can-i-use), and [Quick App](https://doc.quickapp.cn/features/).

Feature detection is straightforward, since all platforms provide a (literally called like this) `canIUse()` method whose name seems inspired by the website [caniuse.com](https://caniuse.com/). For example, ByteDance's [`tt.canIUse()`](https://microapp.bytedance.com/docs/zh-CN/mini-app/develop/api/foundation/tt-can-i-use) allows for support checks for APIs, methods, parameters, options, components, and attributes.

    // Testing if the `<swiper>` component is supported.
    tt.canIUse("swiper");
    // Testing if a particular field is supported.
    tt.canIUse("request.success.data");

**Success**: The next chapter introduces [mini app components](/mini-app-components/).

## Acknowledgements <a href="#acknowledgements" class="w-headline-link">#</a>

This article was reviewed by [Joe Medley](https://github.com/jpmedley), [Kayce Basques](https://github.com/kaycebasques), [Milica Mihajlija](https://github.com/mihajlija), [Alan Kent](https://github.com/alankent), and Keith Gu.

<a href="/tags/mini-apps/" class="w-chip">Mini apps</a>

<span class="w-mr--sm">Last updated: Mar 3, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/mini-apps/mini-app-markup-styling-and-scripting/index.md)

<a href="/mini-apps" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
