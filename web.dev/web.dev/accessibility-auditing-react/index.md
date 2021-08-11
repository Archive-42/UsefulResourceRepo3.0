<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<img src="https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format" alt="Hero Image" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/CYDdWUK4iah3Xe8yEfoR.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#accessibility-auditing-with-react-axe-and-eslint-plugin-jsx-a11y" class="w-toc__header--link">Accessibility auditing with react-axe and eslint-plugin-jsx-a11y</a>

- [Why is this useful?](#why-is-this-useful)
- [Use eslint-plugin-jsx-a11y](#use-eslint-plugin-jsx-a11y)
- [Use react-axe](#use-react-axe)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Accessibility auditing with react-axe and eslint-plugin-jsx-a11y

Your React site is not progressive if it's not accessible. Auditing during development can help you spot any issues.

Apr 29, 2019 <span class="w-author__separator">•</span> Updated Jul 16, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/react" class="w-post-signpost__link">React</a>

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

- <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
- <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
- <a href="https://houssein.me/" class="w-author__link">Blog</a>

If you would like to learn about the basic concepts behind accessibility in web pages, refer to the [What is accessibility](/what-is-accessibility) guide first.

[`react-axe`](https://github.com/dequelabs/react-axe) is a library that audits a React application and logs any accessibility issues to the Chrome DevTools console. It uses the open-source [axe](https://github.com/dequelabs/axe-core) testing library to flag any issues and their severity.

[`eslint-plugin-jsx-a11y`](https://github.com/evcohen/eslint-plugin-jsx-a11y) is an ESLint plugin that identifies and enforces a number of accessibility rules directly in your JSX. Using this in combination with a tool that tests the final rendered DOM, such as `react-axe`, can help you find and fix any accessibility concerns on your site.

## Why is this useful? <a href="#why-is-this-useful" class="w-headline-link">#</a>

It is crucial to build web sites that provide every user, regardless of their impairment or restriction, the capability to access its content. Using auditing libraries such as `react-axe` and `eslint-plugin-jsx-a11y` during the development of your React application will automatically surface any accessibility issues as they pop up.

## Use eslint-plugin-jsx-a11y <a href="#use-eslint-plugin-jsx-a11y" class="w-headline-link">#</a>

React already supports writing accessible HTML elements within JSX syntax. For example, you only need to use the `htmlFor` attribute instead of `for` to link a label to a specific form element within a React component.

    <input id="promo" type="checkbox">
    <label htmlFor="promo">Receive promotional offers?</label>

The [React accessibility documentation](https://reactjs.org/docs/accessibility.html) covers all the nuances of handling accessibility concerns within a React component. To make it easier to spot these issues during development, Create React App (CRA) includes the **`eslint-plugin-jsx-a11y`** plugin for ESLint by default.

To enable pre-configured linting provided by CRA:

1.  Install the appropriate [ESLint plugin](https://eslint.org/docs/user-guide/integrations#editors) for your code editor
2.  Add a `.eslintrc.json` file to your project

<!-- -->

    {
      "extends": "react-app"
    }

You can find more details about configuring your editor to support out-of-box linting in the [CRA documentation](https://facebook.github.io/create-react-app/docs/setting-up-your-editor).

Some common accessibility issues will now show up.

<img src="https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format" alt="Image accessibility warning in linter" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/n8Da1iOU3XCpu7avccaS.png?auto=format&amp;w=1600 1600w" width="800" height="500" />

To check for even more accessibility rules, modify the file to automatically include all the recommended rules by the plugin:

    {
      "extends": ["react-app", "plugin:jsx-a11y/recommended"]
    }

If you would like an even stricter subset of rules, switch to strict mode:

    {
      "extends": ["react-app", "plugin:jsx-a11y/strict"]
    }

<img src="https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format" alt="Label accessibility error in linter" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/LVsEpuH55MeHaY7RIpl3.png?auto=format&amp;w=1600 1600w" width="800" height="500" />

The project [documentation](https://github.com/evcohen/eslint-plugin-jsx-a11y#difference-between-recommended-and-strict-mode) provides information on the differences between recommended and strict mode.

## Use react-axe <a href="#use-react-axe" class="w-headline-link">#</a>

`eslint-plugin-jsx-a11y` can help you easily pinpoint any accessibility issues in your JSX, but it does not test any of the final HTML output. **`react-axe`** is a library that does exactly this by providing a React wrapper around the [`axe-core`](https://github.com/dequelabs/axe-core) testing tool by Deque Labs.

Install the library as a development dependency to begin:

    npm install --save-dev react-axe

You now only need to initialize the module in `index.js`:

    if (process.env.NODE_ENV !== 'production') {
      import('react-axe').then(axe => {
        axe.default(React, ReactDOM, 1000);
        ReactDOM.render(<App />, document.getElementById('root'));
      });
    } else {
      ReactDOM.render(<App />, document.getElementById('root'));
    }

A [dynamic import](https://developers.google.com/web/updates/2017/11/dynamic-import) is used here to only load the library when it is not in production mode before rendering and booting up the root `App` component. This ensures that it is not unnecessarily included in the final production bundle.

Now when you run the application during development, issues are surfaced directly to the Chrome DevTools console.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format" alt="React Axe in Chrome DevTools" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/7kiPTpXD47VBf83n6mqz.png?auto=format&amp;w=1600 1600w" width="800" height="430" />

A severity level is also assigned for each violation. These levels are:

- Minor
- Moderate
- Serious
- Critical

If you would like to include accessibility testing in your unit testing workflow, take a look at the [Jest and axe integration example](https://github.com/dequelabs/axe-core/tree/develop/doc/examples/jest_react) to understand how.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

1.  If you are building a site with React, include accessibility auditing into your workflow early to catch problems as you build your components.
2.  Use `eslint-plugin-jsx-a11y` to add accessibility checks into your linting workflow. CRA already comes with it included, but switch to either the recommended or strict mode.
3.  In addition to local development testing, include `react-axe` into your application to catch any issues on the final rendered DOM. Do not include it into your production bundle.

<span class="w-mr--sm">Last updated: Jul 16, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/react/accessibility-auditing-react/index.md)

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
