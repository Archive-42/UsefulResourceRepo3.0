# Performance audits

Measure performance and find opportunities to speed up page loads.

<img src="https://web-dev.imgix.net/image/jxu1OdD7LKOGIDU7jURMpSH2lyK2/wpGZrgY08B0x6jbLnWPU.svg" alt="Collection cover image" class="w-masthead-path__image" width="330" height="220" />

## Overview

These checks ensure that your page is optimized for users to be able to see and interact with page content.

## Table of Contents

- <a href="#performance-audit-scoring" class="w-path-link">Performance audit scoring</a>
- <a href="#metrics" class="w-path-link">Metrics</a>
- <a href="#opportunities" class="w-path-link">Opportunities</a>
- <a href="#diagnostics" class="w-path-link">Diagnostics</a>

---

## Performance audit scoring <a href="#performance-audit-scoring" class="w-headline-link">#</a>

- <a href="/performance-scoring/" class="w-path-link">Lighthouse performance scoring</a>

## Metrics <a href="#metrics" class="w-headline-link">#</a>

- <a href="/first-contentful-paint/" class="w-path-link">First Contentful Paint</a>
- <a href="/first-meaningful-paint/" class="w-path-link">First Meaningful Paint</a>
- <a href="/speed-index/" class="w-path-link">Speed Index</a>
- <a href="/first-cpu-idle/" class="w-path-link">First CPU Idle</a>
- <a href="/interactive/" class="w-path-link">Time to Interactive</a>
- <a href="/lighthouse-max-potential-fid/" class="w-path-link">Max Potential First Input Delay</a>
- <a href="/lighthouse-total-blocking-time/" class="w-path-link">Total Blocking Time</a>
- <a href="/lighthouse-largest-contentful-paint/" class="w-path-link">Largest Contentful Paint</a>

## Opportunities <a href="#opportunities" class="w-headline-link">#</a>

- <a href="/render-blocking-resources/" class="w-path-link">Eliminate render-blocking resources</a>
- <a href="/uses-responsive-images/" class="w-path-link">Properly size images</a>
- <a href="/offscreen-images/" class="w-path-link">Defer offscreen images</a>
- <a href="/unminified-css/" class="w-path-link">Minify CSS</a>
- <a href="/unminified-javascript/" class="w-path-link">Minify JavaScript</a>
- <a href="/unused-css-rules/" class="w-path-link">Remove unused CSS</a>
- <a href="/uses-optimized-images/" class="w-path-link">Efficiently encode images</a>
- <a href="/uses-webp-images/" class="w-path-link">Serve images in modern formats</a>
- <a href="/uses-text-compression/" class="w-path-link">Enable text compression</a>
- <a href="/uses-rel-preconnect/" class="w-path-link">Preconnect to required origins</a>
- <a href="/time-to-first-byte/" class="w-path-link">Reduce server response times (TTFB)</a>
- <a href="/redirects/" class="w-path-link">Avoid multiple page redirects</a>
- <a href="/uses-rel-preload/" class="w-path-link">Preload key requests</a>
- <a href="/efficient-animated-content/" class="w-path-link">Use video formats for animated content</a>
- <a href="/third-party-summary/" class="w-path-link">Reduce the impact of third-party code</a>
- <a href="/non-composited-animations/" class="w-path-link">Avoid non-composited animations</a>
- <a href="/third-party-facades/" class="w-path-link">Lazy load third-party resources with facades</a>

## Diagnostics <a href="#diagnostics" class="w-headline-link">#</a>

- <a href="/total-byte-weight/" class="w-path-link">Avoid enormous network payloads</a>
- <a href="/uses-long-cache-ttl/" class="w-path-link">Serve static assets with an efficient cache policy</a>
- <a href="/dom-size/" class="w-path-link">Avoid an excessive DOM size</a>
- <a href="/critical-request-chains/" class="w-path-link">Avoid chaining critical requests</a>
- <a href="/user-timings/" class="w-path-link">User Timing marks and measures</a>
- <a href="/bootup-time/" class="w-path-link">Reduce JavaScript execution time</a>
- <a href="/mainthread-work-breakdown/" class="w-path-link">Minimize main thread work</a>
- <a href="/font-display/" class="w-path-link">Ensure text remains visible during webfont load</a>
- <a href="/resource-summary/" class="w-path-link">Keep request counts low and transfer sizes small</a>

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
