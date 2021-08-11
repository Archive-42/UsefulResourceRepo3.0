<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#mini-app-open-source-projects" class="w-toc__header--link">Mini app open source projects</a>
------------------------------------------------------------------------------------------------------

-   [kbone](#kbone)
-   [kbone-ui](#kbone-ui)
-   [WeUI](#weui)
-   [Omi](#omi)
-   [Omiu](#omiu)
-   [WePY](#wepy)
-   [vConsole](#vconsole)
-   [weweb](#weweb)
-   [Acknowledgements](#acknowledgements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Mini app open source projects
=============================

Mar 3, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/mini-apps" class="w-post-signpost__link">Mini apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

-   <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
-   <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
-   <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

This post is part of an article collection where each article builds upon previous articles. If you just landed here, you may want to start reading from the [beginning](/mini-app-super-apps/).

kbone <a href="#kbone" class="w-headline-link">#</a>
----------------------------------------------------

The [kbone](https://wechat-miniprogram.github.io/kbone/docs/) project ([open source on GitHub](https://github.com/Tencent/kbone)) implements an adapter that simulates a browser environment in the adaptation layer, so that code written for the web can run without changes in a mini app. Several starter templates (among them [Vue](https://github.com/wechat-miniprogram/kbone-template-vue), [React](https://github.com/wechat-miniprogram/kbone-template-react), and [Preact](https://github.com/wechat-miniprogram/kbone-template-preact)) exist that make the onboarding experience for web developers coming from these frameworks easier.

A new project can be created with the `kbone-cli` tool. A wizard asks what framework to initiate the project with. The code snippet below shows the Preact demo. In the code snippet below, the `mp` command builds the mini app, the `web` command builds the web app, and `build` creates the production web app.

    npx kbone-cli init my-app
    cd my-app
    npm run mp
    npm run web
    npm run build

The code snippet below shows a simple counter component that then gets isomorphically rendered in a mini app and a web app. The overhead of the mini app is significant, purely judging from the DOM structure.

    import { h, Component } from "preact";
    import "./index.css";

    class Counter extends Component {
      state = { count: 1 };

      sub = () => {
        this.setState((prevState) => {
          return { count: --prevState.count };
        });
      };

      add = () => {
        this.setState((prevState) => {
          return { count: ++prevState.count };
        });
      };

      clickHandle = () => {
        if ("undefined" != typeof wx && wx.getSystemInfoSync) {
          wx.navigateTo({
            url: "../log/index?id=1",
          });
        } else {
          location.href = "log.html";
        }
      };

      render({}, { count }) {
        return (
          <div>
            <button onClick={this.sub}>-</button>
            <span>{count}</span>
            <button onClick={this.add}>+</button>
            <div onClick={this.clickHandle}>跳转</div>
          </div>
        );
      }
    }

    export default Counter;

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format" alt="The Preact kbone template demo app opened in WeChat DevTools. Note the complex DOM structure and how the plus and minus buttons are actually not &lt;button&gt; elements." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/DDreycxzclMP8IiUplyO.png?auto=format&amp;w=1600 1600w" width="800" height="664" /><figcaption>The Preact kbone template demo app opened in WeChat DevTools. Note the complex DOM structure and how the plus and minus buttons are actually not <code>&lt;button&gt;</code> elements.</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format" alt="The Preact kbone template demo app opened in the web browser. Note the DOM structure." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/rerYiCnwc92DP7pM7WPc.png?auto=format&amp;w=1600 1600w" width="800" height="496" /><figcaption>The Preact kbone template demo app opened in the web browser. Note the DOM structure.</figcaption></figure>kbone-ui <a href="#kbone-ui" class="w-headline-link">#</a>
----------------------------------------------------------

The [kbone-ui](https://wechat-miniprogram.github.io/kbone/docs/ui/intro/) project ([open source on GitHub](https://github.com/wechat-miniprogram/kbone-ui)) is a UI framework that facilitates both mini app development as well as Vue.js development with kbone. The kbone-ui components emulate the look and feel of [WeChat's built-in mini app components](https://developers.weixin.qq.com/miniprogram/dev/component/) (also see [Components](/mini-app-components/) above). A [demo](https://wechat-miniprogram.github.io/kboneui/ui/#/) that runs directly in the browser lets you explore the available components.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format" alt="The kbone-ui demo showing form-related components." sizes="(min-width: 320px) 320px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/wEA4Hr2JyVfKgdHnpb5o.png?auto=format&amp;w=640 640w" width="320" height="438" /><figcaption>The kbone-ui demo showing form-related components.</figcaption></figure>WeUI <a href="#weui" class="w-headline-link">#</a>
--------------------------------------------------

[WeUI](https://github.com/Tencent/weui) is a set of basic style libraries consistent with WeChat's default visual experience. The official WeChat design team has tailored designs for WeChat internal web pages and WeChat mini apps to make users' perception of use more uniform. It includes components such as `button`, `cell`, `dialog`, `progress`, `toast`, `article`, `actionsheet`, and `icon`. There are different versions of WeUI available like [weui-wxss](https://github.com/Tencent/weui-wxss/) for WeChat mini apps styled with WXSS (see [Styling](/mini-app-markup-styling-and-scripting/#styling) above), [weui.js](https://github.com/weui/weui.js/) for web apps, and [react-weui](https://github.com/weui/react-weui/) for WeChat React components.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format" alt="The WeUI demo app showing switches." sizes="(min-width: 450px) 450px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/V0xswCD3MJltrxALmy8n.png?auto=format&amp;w=900 900w" width="450" height="395" /><figcaption>The WeUI demo app showing switches.</figcaption></figure>Omi <a href="#omi" class="w-headline-link">#</a>
------------------------------------------------

[Omi](https://tencent.github.io/omi/) is a self-proclaimed frontend cross-frameworks framework ([open source on GitHub](https://github.com/Tencent/omi). It merges Web Components, JSX, Virtual DOM, functional style, observer or Proxy into one framework with tiny size and high performance. Its aim is to let developers write components once and use them everywhere, such as Omi, React, Preact, Vue.js, or Angular. Writing Omi components is very intuitive and free of almost all boilerplate.

    import { render, WeElement, define } from "omi";

    define("my-counter", class extends WeElement {
      data = {
        count: 1,
      };

      static css = `
        span{
            color: red;
        }`;

      sub = () => {
        this.data.count--;
        this.update();
      };

      add = () => {
        this.data.count++;
        this.update();
      };

      render() {
        return (
          <div>
            <button onClick={this.sub}>-</button>
            <span>{this.data.count}</span>
            <button onClick={this.add}>+</button>
          </div>
        );
      }
    });

    render(<my-counter />, "body");

Omiu <a href="#omiu" class="w-headline-link">#</a>
--------------------------------------------------

[Omiu](https://tencent.github.io/omi/components/docs/) is a cross framework UI component library ([open source on GitHub](https://github.com/Tencent/omi#omiu)) developed based on Omi, which outputs custom elements of standard web components.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format" alt="The Omiu demo app showing switches." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/eoNhik827CE4TfaT9ZaV.png?auto=format&amp;w=1600 1600w" width="800" height="939" /><figcaption>The Omiu demo app showing switches.</figcaption></figure>WePY <a href="#wepy" class="w-headline-link">#</a>
--------------------------------------------------

[WePY](https://wepyjs.github.io/wepy-docs/) is a framework that allows mini apps to support componentized development. Through pre-compilation, developers can choose their favorite development style to develop mini apps. The detailed optimization of the framework and the introduction of Promises and async functions all make the development of mini app projects easier and more efficient. At the same time, WePY is also a growing framework, which has largely absorbed some optimized frontend tools and framework design concepts and ideas, mostly from Vue.js.

    <style lang="less">
      @color: #4d926f;
      .num {
        color: @color;
      }
    </style>

    <template>
      <div class="container">
        <div class="num" @tap="num++">{{num}}</div>
        <custom-component></custom-component>
        <vendor-component></vendor-component>
        <div>{{text}}</div>
        <input v-model="text" />
      </div>
    </template>

    <config>
      { usingComponents: { customComponent: '@/components/customComponent', vendorComponent:
      'module:vendorComponent' } }
    </config>

    <script>
      import wepy from "@wepy/core";

      wepy.page({
        data: {
          num: 0,
          text: "Hello World",
        },
      });
    </script>

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format" alt="WePY &quot;getting started&quot; documentation." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ooxZuXzVY9aHXmha36vM.png?auto=format&amp;w=1600 1600w" width="800" height="505" /><figcaption>WePY "getting started" documentation.</figcaption></figure>vConsole <a href="#vconsole" class="w-headline-link">#</a>
----------------------------------------------------------

The [vConsole](https://github.com/Tencent/vConsole) project provides a lightweight, extendable frontend developer tool for mobile web pages. It offers a DevTools-like debugger that can be injected directly into web apps and mini apps. A [demo](http://wechatfe.github.io/vconsole/demo.html) showcases the opportunities. The vConsole includes tabs for logs, system, network, elements, and storage.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format" alt="vConsole demo app showing the elements explorer." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ow6FfaoI7fMCJDN1819t.png?auto=format&amp;w=1600 1600w" width="800" height="505" /><figcaption>vConsole demo app showing the elements explorer.</figcaption></figure>weweb <a href="#weweb" class="w-headline-link">#</a>
----------------------------------------------------

The [weweb](https://weidian-inc.github.io/hera/#/) project ([open source on GitHub](https://github.com/wdfe/weweb)) is the underlying frontend framework of the [Hera](https://weidian-inc.github.io/hera/#/) mini app framework that claims to be compatible with the syntax of WeChat mini apps, so you can write web applications in the way of mini apps. The documentation promises that if you already have a mini app, you can run it in the browser thanks to weweb. In my experiments, this did not work reliably for current mini apps, most probably because the project has not seen updates recently leading its compiler to miss changes in the WeChat platform.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format" alt="Hera mini app framework documentation showing the list of supported WeChat APIs." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/jU9Od9IDqFlmuYzAtirn.png?auto=format&amp;w=1600 1600w" width="800" height="505" /><figcaption>Hera mini app framework documentation showing the list of supported WeChat APIs.</figcaption></figure><figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format" alt="The weweb demo mini app compiled with weweb to run in the browser." sizes="(min-width: 300px) 300px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/C7ZpPrFE4geW0dylRpZ2.png?auto=format&amp;w=600 600w" width="300" height="429" /><figcaption>The weweb demo mini app compiled with weweb to run in the browser.</figcaption></figure>**Success**: In the next chapter, you will learn how to [program the mini app way](/mini-app-programming-way/).

Acknowledgements <a href="#acknowledgements" class="w-headline-link">#</a>
--------------------------------------------------------------------------

This article was reviewed by [Joe Medley](https://github.com/jpmedley), [Kayce Basques](https://github.com/kaycebasques), [Milica Mihajlija](https://github.com/mihajlija), [Alan Kent](https://github.com/alankent), and Keith Gu.

<a href="/tags/mini-apps/" class="w-chip">Mini apps</a>

<span class="w-mr--sm">Last updated: Mar 3, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/mini-apps/mini-app-open-source-projects/index.md)

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
