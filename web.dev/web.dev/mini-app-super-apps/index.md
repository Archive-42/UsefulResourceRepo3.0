





<a href="#mini-apps-and-super-apps" class="w-toc__header--link">Mini apps and super apps</a>
--------------------------------------------------------------------------------------------

-   [Welcome to mini apps](#welcome-to-mini-apps)
-   [What are super apps?](#what-are-super-apps)
-   [A few words about super app platforms](#a-few-words-about-super-app-platforms)
-   [Installing super apps](#installing-super-apps)
-   [Acknowledgements](#acknowledgements)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Mini apps and super apps
========================

Mar 3, 2021

<span class="w-post-signpost__title">Appears in:</span> <a href="/mini-apps" class="w-post-signpost__link">Mini apps</a>

[<img src="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Thomas Steiner" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/8PLpVmFef6mj72MVWeiN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/thomassteiner/)

<a href="/authors/thomassteiner/" class="w-author__name-link">Thomas Steiner</a>

-   <a href="https://twitter.com/tomayac" class="w-author__link">Twitter</a>
-   <a href="https://github.com/tomayac" class="w-author__link">GitHub</a>
-   <a href="https://glitch.com/@tomayac" class="w-author__link">Glitch</a>
-   <a href="https://blog.tomayac.com/" class="w-author__link">Blog</a>

Welcome to mini apps <a href="#welcome-to-mini-apps" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

When you look at applications on your phone, you probably have specific apps for specific tasks. You might have a banking app. You might have an app for buying public transit tickets. Likely you have an app for getting directions, and many more specialized apps. This post introduces you to the concept of a different kind of apps—mini apps—sometimes also called mini programs or applets. You will first learn about the background of various mini app platforms and their developer experience, and then focus on things the web can learn from mini apps. But before learning about mini apps, you first need to learn about super apps.

What are super apps? <a href="#what-are-super-apps" class="w-headline-link">#</a>
---------------------------------------------------------------------------------

Super apps serve as hosts to other apps that run within them: the so-called mini apps. Popular super apps are [WeChat](https://weixin.qq.com/) (微信) by Tencent, [Alipay](https://www.alipay.com/) (支付宝) by Ant Group (an affiliate company of the Chinese Alibaba Group), the app of the search engine [Baidu](https://baidu.com/) (百度), as well as ByteDance's [Douyin](https://www.douyin.com/) (抖音), which you might know as TikTok (蒂克托克). The first three are commonly also referred to as BAT, derived from **B**(aidu)**A**(libaba)**T**(encent). Super apps have taken the Chinese market by storm, which is why a lot of the examples in this article are Chinese.

<figure><img src="https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format" alt="The WeChat super app showing recently launched mini apps." sizes="(min-width: 300px) 300px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/8WbTDNrhLsU0El80frMBGE4eMCD3/UKmUgG231MtQ2nEo1P0K.PNG?auto=format&amp;w=600 600w" width="300" height="649" /><figcaption>The WeChat super app showing recently launched mini apps.</figcaption></figure>### A few words about super app platforms <a href="#a-few-words-about-super-app-platforms" class="w-headline-link">#</a>

WeChat aims to make itself a one-stop shop to meet almost any need users might have in their daily lives. Alipay builds its platforms on top of its payment system, focusing on retail and financial services, including credit, loan, insurance, installment, and local life services. Baidu strives to transform its search engine from solely connecting people, services, and information into information-as-a-service through mini programs for travel, retail, ads, payment, and more. Last but not least Douyin wants to boost itself as a hub for social e-commerce and transform to more of an entertainment and shopping platform.

### Installing super apps <a href="#installing-super-apps" class="w-headline-link">#</a>

Super apps are available on multiple operating systems. Note that the versions available in the official app stores may not always contain all features or be available in all locales. The links below point to links that work universally, but that may require loading from untrusted sources, so download and install the apps **at your own risk**. You typically need to create an account, which involves revealing your phone number. You might want to consider getting a burner phone. Be advised that many super apps only allow you to create a so-called overseas account, which does not have all features of a domestic account.

-   **WeChat:** [iOS](https://apps.apple.com/us/app/wechat/id414478124), [Android](https://weixin.qq.com/cgi-bin/readtemplate?uin=&stype=&promote=&fr=&lang=zh_CN&ADTAG=&check=false&t=weixin_download_method&sys=android&loc=weixin,android,web,0), [macOS](https://mac.weixin.qq.com/), [Windows](https://pc.weixin.qq.com/)
-   **Baidu:** [iOS](https://apps.apple.com/us/app/%E7%99%BE%E5%BA%A6/id382201985), [Android](https://play.google.com/store/apps/details?id=com.baidu.searchbox&hl=en)
-   **Alipay:** [iOS](https://itunes.apple.com/app/id333206289?mt=8), [Android](https://t.alipayobjects.com/L1/71/100/and/alipay_wap_main.apk)
-   **Douyin:** [iOS](https://itunes.apple.com/cn/app/%E6%8A%96%E9%9F%B3%E7%9F%AD%E8%A7%86%E9%A2%91/id1142110895?l=zh&ls=1&mt=8) (CN-only), [Android](http://s.toutiao.com/UsMYE/)

Since the user interface of many super apps is Chinese-only, use the [Google Translate app](https://translate.google.com/intl/en/about/#!#speak-with-the-world) in camera mode with a secondary phone (given you have one) to understand what is going on if you do not speak Chinese.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format" alt="Using Google Translate in camera mode to live-translate a Chinese mini app." sizes="(min-width: 300px) 300px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kSLjHjkFgscBC2j2d6j9.png?auto=format&amp;w=600 600w" width="300" height="520" /><figcaption>Using Google Translate in camera mode to live-translate a Chinese mini app.</figcaption></figure>**Success**: Read on to [learn more about mini apps](/mini-app-about/) in the next chapter.

Acknowledgements <a href="#acknowledgements" class="w-headline-link">#</a>
--------------------------------------------------------------------------

This article was reviewed by [Joe Medley](https://github.com/jpmedley), [Kayce Basques](https://github.com/kaycebasques), [Milica Mihajlija](https://github.com/mihajlija), [Alan Kent](https://github.com/alankent), and Keith Gu.

<a href="/tags/mini-apps/" class="w-chip">Mini apps</a>

<span class="w-mr--sm">Last updated: Mar 3, 2021 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/mini-apps/mini-app-super-apps/index.md)

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
