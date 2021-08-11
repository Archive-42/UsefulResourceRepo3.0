## <a href="#what-are-h5-and-quickapp" class="w-toc__header--link">What are H5 and QuickApp?</a>

- [What mini apps are not](#what-mini-apps-are-not)
- [H5](#h5)
- [Quick App](#quick-app)
- [Acknowledgements](#acknowledgements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# What are H5 and QuickApp?

Mar 3, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/mini-apps" class="w-post-signpost__link">Mini apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

- <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
- <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
- <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

This post is part of an article collection where each article builds upon previous articles. If you just landed here, you may want to start reading from the [beginning](/mini-app-super-apps/).

## What mini apps are not <a href="#what-mini-apps-are-not" class="w-headline-link">#</a>

Before I go into more detail on the developer experience of mini apps, I want to briefly mention and set apart two technologies that come up in the context of mini apps, H5 and Quick App.

## H5 <a href="#h5" class="w-headline-link">#</a>

H5 apps (or pages) are commonly seen as the predecessor of mini apps. What people mean by H5 is essentially a well-designed mobile web app (or page) that can be shared easily on chat applications. H5 is a reference to the HTML5 umbrella of technologies that includes responsive design, snappy CSS animations, multimedia content, etc. The Chinese Wikipedia actually [redirects](https://zh.wikipedia.org/wiki/H5) from H5 to HTML5. A good example of a representative H5 page experience is the [WeChat H5 boilerplate](https://panteng.github.io/wechat-h5-boilerplate/) project's demo.

## Quick App <a href="#quick-app" class="w-headline-link">#</a>

[Quick App](https://www.quickapp.cn/) is an industry alliance consisting of the following members:

- [vivo open platform](https://dev.vivo.com.cn/)
- [Huawei Developer Alliance](http://developer.huawei.com/cn/consumer)
- [OPPO open platform](https://open.oppomobile.com/)
- [Xiaomi Open Platform](https://dev.mi.com/console/app/newapp.html)
- [Lenovo Open Platform](http://open.lenovo.com/developer/)
- [Gionee Open Platform](http://devquickapp.gionee.com/)
- [Meizu Open Platform](http://open.flyme.cn/)
- [ZTE Developer Platform](https://dev.ztems.com/)
- [Nubian Open Platform](http://developer.nubia.com/developer/view/index.html)
- [OnePlus Open Platform](http://www.oneplus.cn/)
- [Hisense Open Platform](http://dev.hismarttv.com/)
- [China Mobile Terminal Corporation](https://www.chinamobileltd.com/tc/global/home.php)

While the technology of Quick App is comparable to "regular" mini apps (see [Building blocks and compatibility](/mini-app-about/#building-blocks-and-compatibility)), the discovery of Quick App is different. They are meant to be listed in stores, which come pre-installed on devices of the manufacturers in the alliance, but can also be shared by means of a deep link (see the [Quick App showcase](https://www.quickapp.cn/quickAppShow)). They do not run in the context of a super app, but launch as seemingly self-contained full screen applications that feel deeply integrated into device. What happens in the background is that they are opened in a full screen view rendered by the operating system that provides the JavaScript bridge.

**Success**: The next chapter covers the [developer experience of mini apps](/mini-app-devtools/).

## Acknowledgements <a href="#acknowledgements" class="w-headline-link">#</a>

This article was reviewed by [Joe Medley](https://github.com/jpmedley), [Kayce Basques](https://github.com/kaycebasques), [Milica Mihajlija](https://github.com/mihajlija), [Alan Kent](https://github.com/alankent), and Keith Gu.

<a href="/tags/mini-apps/" class="w-chip">Mini apps</a>

<span class="w-mr--sm">Last updated: Mar 3, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/mini-apps/mini-app-what-are-h5-and-quickapp/index.md)

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
