# Best Practices audits

Improve code health of your web page following these best practices

<img src="https://web-dev.imgix.net/image/jxu1OdD7LKOGIDU7jURMpSH2lyK2/WRBPLiZWj2BTEZIyRlqh.svg" alt="Collection cover image" class="w-masthead-path__image" width="330" height="220" />

## Overview

These checks highlight opportunities to improve the overall code health of your web app.

## Table of Contents

- <a href="#general-best-practices" class="w-path-link">General best practices</a>
- <a href="#make-your-page-fast" class="w-path-link">Make your page fast</a>
- <a href="#make-your-page-secure" class="w-path-link">Make your page secure</a>
- <a href="#create-a-good-user-experience" class="w-path-link">Create a good user experience</a>
- <a href="#avoid-deprecated-technologies" class="w-path-link">Avoid deprecated technologies</a>
- <a href="#diagnostic-audits" class="w-path-link">Diagnostic audits</a>

---

## General best practices <a href="#general-best-practices" class="w-headline-link">#</a>

- <a href="/doctype/" class="w-path-link">Page lacks the HTML doctype, thus triggering quirks mode</a>
- <a href="/errors-in-console/" class="w-path-link">Browser errors were logged to the console</a>
- <a href="/image-aspect-ratio/" class="w-path-link">Displays images with incorrect aspect ratio</a>

## Make your page fast <a href="#make-your-page-fast" class="w-headline-link">#</a>

- <a href="/uses-http2/" class="w-path-link">Does not use HTTP/2 for all of its resources</a>
- <a href="/no-document-write/" class="w-path-link">Uses document.write()</a>
- <a href="/uses-passive-event-listeners/" class="w-path-link">Use passive listeners to improve scrolling performance</a>

## Make your page secure <a href="#make-your-page-secure" class="w-headline-link">#</a>

- <a href="/is-on-https/" class="w-path-link">Does not use HTTPS</a>
- <a href="/external-anchors-use-rel-noopener/" class="w-path-link">Links to cross-origin destinations are unsafe</a>
- <a href="/no-vulnerable-libraries/" class="w-path-link">Includes front-end JavaScript libraries with known security vulnerabilities</a>
- <a href="/csp-xss/" class="w-path-link">Ensure CSP is effective against XSS attacks</a>

## Create a good user experience <a href="#create-a-good-user-experience" class="w-headline-link">#</a>

- <a href="/geolocation-on-start/" class="w-path-link">Requests the geolocation permission on page load</a>
- <a href="/notification-on-start/" class="w-path-link">Requests the notification permission on page load</a>
- <a href="/password-inputs-can-be-pasted-into/" class="w-path-link">Prevents users from pasting into password fields</a>

## Avoid deprecated technologies <a href="#avoid-deprecated-technologies" class="w-headline-link">#</a>

- <a href="/appcache-manifest/" class="w-path-link">Uses Application Cache</a>
- <a href="/deprecations/" class="w-path-link">Uses deprecated APIs</a>

## Diagnostic audits <a href="#diagnostic-audits" class="w-headline-link">#</a>

- <a href="/js-libraries/" class="w-path-link">Detected JavaScript libraries</a>

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
