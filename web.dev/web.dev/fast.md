# Fast load times

Techniques for improving site performance.

<img src="https://web-dev.imgix.net/image/jxu1OdD7LKOGIDU7jURMpSH2lyK2/fjFJRFnHXiem8yF0GGQ9.svg" alt="Collection cover image" class="w-masthead-path__image" width="330" height="220" />

## Overview

When you're building a modern web experience, it's important to measure, optimize, and monitor if you're to get fast and stay fast. Performance plays a significant role in the success of any online venture, as high performing sites engage and retain users better than poorly performing ones. Sites should focus on optimizing for user-centric happiness metrics. Tools like Lighthouse (baked into web.dev!) highlight these metrics and help you take the right steps toward improving your performance. To "stay fast", set and enforce performance budgets to help your team work within the constraints needed to continue loading fast and keeping users happy after your site has launched.

## Table of Contents

- <a href="#introduction" class="w-path-link">Introduction</a>
- <a href="#set-performance-budgets" class="w-path-link">Set performance budgets</a>
- <a href="#optimize-your-images" class="w-path-link">Optimize your images</a>
- <a href="#lazy-load-images-and-video" class="w-path-link">Lazy-load images and video</a>
- <a href="#optimize-your-javascript" class="w-path-link">Optimize your JavaScript</a>
- <a href="#optimize-your-resource-delivery" class="w-path-link">Optimize your resource delivery</a>
- <a href="#optimize-your-css" class="w-path-link">Optimize your CSS</a>
- <a href="#optimize-your-third-party-resources" class="w-path-link">Optimize your third-party resources</a>
- <a href="#optimize-webfonts" class="w-path-link">Optimize WebFonts</a>
- <a href="#optimize-for-network-quality" class="w-path-link">Optimize for network quality</a>
- <a href="#measure-performance-in-the-field" class="w-path-link">Measure performance in the field</a>
- <a href="#build-a-performance-culture" class="w-path-link">Build a performance culture</a>

---

## Introduction <a href="#introduction" class="w-headline-link">#</a>

- <a href="/why-speed-matters/" class="w-path-link">Why does speed matter?</a>
- <a href="/what-is-speed/" class="w-path-link">What is speed?</a>
- <a href="/how-to-measure-speed/" class="w-path-link">How to measure speed?</a>
- <a href="/how-to-stay-fast/" class="w-path-link">How to stay fast?</a>
- <a href="/rail/" class="w-path-link">Measure performance with the RAIL model</a>

## Set performance budgets <a href="#set-performance-budgets" class="w-headline-link">#</a>

- <a href="/performance-budgets-101/" class="w-path-link">Performance budgets 101</a>
- <a href="/your-first-performance-budget/" class="w-path-link">Your first performance budget</a>
- <a href="/incorporate-performance-budgets-into-your-build-tools/" class="w-path-link">Incorporate performance budgets into your build process</a>
- <a href="/use-lighthouse-for-performance-budgets/" class="w-path-link">Use Lighthouse for performance budgets</a>
- <a href="/using-bundlesize-with-travis-ci/" class="w-path-link">Using bundlesize with Travis CI</a>
- <a href="/using-lighthouse-bot-to-set-a-performance-budget/" class="w-path-link">Using Lighthouse Bot to set a performance budget</a>
- <a href="/lighthouse-ci/" class="w-path-link">Performance monitoring with Lighthouse CI</a>

## Optimize your images <a href="#optimize-your-images" class="w-headline-link">#</a>

- <a href="/choose-the-right-image-format/" class="w-path-link">Choose the right image format</a>
- <a href="/compress-images/" class="w-path-link">Choose the correct level of compression</a>
- <a href="/use-imagemin-to-compress-images/" class="w-path-link">Use Imagemin to compress images</a>
- <a href="/replace-gifs-with-videos/" class="w-path-link">Replace animated GIFs with video for faster page loads</a>
- <a href="/serve-responsive-images/" class="w-path-link">Serve responsive images</a>
- <a href="/serve-images-with-correct-dimensions/" class="w-path-link">Serve images with correct dimensions</a>
- <a href="/serve-images-webp/" class="w-path-link">Use WebP images</a>
- <a href="/image-cdns/" class="w-path-link">Use image CDNs to optimize images</a>

## Lazy-load images and video <a href="#lazy-load-images-and-video" class="w-headline-link">#</a>

- <a href="/lazy-loading/" class="w-path-link">Use lazy-loading to improve loading speed</a>
- <a href="/lazy-loading-images/" class="w-path-link">Lazy-loading images</a>
- <a href="/lazy-loading-video/" class="w-path-link">Lazy-loading video</a>
- <a href="/browser-level-image-lazy-loading/" class="w-path-link">Browser-level image lazy-loading for the web</a>
- <a href="/use-lazysizes-to-lazyload-images/" class="w-path-link">Use lazysizes to lazy-load images</a>

## Optimize your JavaScript <a href="#optimize-your-javascript" class="w-headline-link">#</a>

- <a href="/apply-instant-loading-with-prpl/" class="w-path-link">Apply instant loading with the PRPL pattern</a>
- <a href="/reduce-javascript-payloads-with-code-splitting/" class="w-path-link">Reduce JavaScript payloads with code splitting</a>
- <a href="/remove-unused-code/" class="w-path-link">Remove unused code</a>
- <a href="/reduce-network-payloads-using-text-compression/" class="w-path-link">Minify and compress network payloads</a>
- <a href="/serve-modern-code-to-modern-browsers/" class="w-path-link">Serve modern code to modern browsers for faster page loads</a>
- <a href="/publish-modern-javascript/" class="w-path-link">Publish, ship, and install modern JavaScript for faster applications</a>
- <a href="/commonjs-larger-bundles/" class="w-path-link">How CommonJS is making your bundles larger</a>

## Optimize your resource delivery <a href="#optimize-your-resource-delivery" class="w-headline-link">#</a>

- <a href="/content-delivery-networks/" class="w-path-link">Content delivery networks (CDNs)</a>
- <a href="/prioritize-resources/" class="w-path-link">Prioritize resources</a>
- <a href="/preload-critical-assets/" class="w-path-link">Preload critical assets to improve loading speed</a>
- <a href="/preconnect-and-dns-prefetch/" class="w-path-link">Establish network connections early to improve perceived page speed</a>
- <a href="/link-prefetch/" class="w-path-link">Prefetch resources to speed up future navigations</a>
- <a href="/fast-playback-with-preload/" class="w-path-link">Fast playback with audio and video preload</a>

## Optimize your CSS <a href="#optimize-your-css" class="w-headline-link">#</a>

- <a href="/defer-non-critical-css/" class="w-path-link">Defer non-critical CSS</a>
- <a href="/minify-css/" class="w-path-link">Minify CSS</a>
- <a href="/extract-critical-css/" class="w-path-link">Extract critical CSS</a>
- <a href="/optimize-css-background-images-with-media-queries/" class="w-path-link">Optimize CSS background images with media queries</a>

## Optimize your third-party resources <a href="#optimize-your-third-party-resources" class="w-headline-link">#</a>

- <a href="/third-party-javascript/" class="w-path-link">Third-party JavaScript performance</a>
- <a href="/identify-slow-third-party-javascript/" class="w-path-link">Identify slow third-party JavaScript</a>
- <a href="/efficiently-load-third-party-javascript/" class="w-path-link">Efficiently load third-party JavaScript</a>

## Optimize WebFonts <a href="#optimize-webfonts" class="w-headline-link">#</a>

- <a href="/avoid-invisible-text/" class="w-path-link">Avoid invisible text during font loading</a>
- <a href="/optimize-webfont-loading/" class="w-path-link">Optimize WebFont loading and rendering</a>
- <a href="/reduce-webfont-size/" class="w-path-link">Reduce WebFont Size</a>

## Optimize for network quality <a href="#optimize-for-network-quality" class="w-headline-link">#</a>

- <a href="/adaptive-serving-based-on-network-quality/" class="w-path-link">Adaptive serving based on network quality</a>

## Measure performance in the field <a href="#measure-performance-in-the-field" class="w-headline-link">#</a>

- <a href="/chrome-ux-report/" class="w-path-link">Using the Chrome UX Report to look at performance in the field</a>
- <a href="/chrome-ux-report-data-studio-dashboard/" class="w-path-link">Using the CrUX Dashboard on Data Studio</a>
- <a href="/chrome-ux-report-pagespeed-insights/" class="w-path-link">Using the Chrome UX Report on PageSpeed Insights</a>
- <a href="/chrome-ux-report-bigquery/" class="w-path-link">Using the Chrome UX Report on BigQuery</a>
- <a href="/chrome-ux-report-api/" class="w-path-link">Using the Chrome UX Report API</a>

## Build a performance culture <a href="#build-a-performance-culture" class="w-headline-link">#</a>

- <a href="/value-of-speed/" class="w-path-link">The value of speed</a>
- <a href="/how-can-performance-improve-conversion/" class="w-path-link">How can performance improve conversion?</a>
- <a href="/what-should-you-measure-to-improve-performance/" class="w-path-link">What should you measure to improve performance?</a>
- <a href="/how-to-report-metrics/" class="w-path-link">How to report metrics and build a performance culture</a>
- <a href="/fixing-website-speed-cross-functionally/" class="w-path-link">Fixing website speed cross-functionally</a>
- <a href="/site-speed-and-business-metrics/" class="w-path-link">Relating site speed and business metrics</a>

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
