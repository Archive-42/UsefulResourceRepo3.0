## <a href="#displays-images-with-incorrect-aspect-ratio" class="w-toc__header--link">Displays images with incorrect aspect ratio</a>

- [How the Lighthouse image aspect ratio audit fails](#how-the-lighthouse-image-aspect-ratio-audit-fails)
- [Ensure images display with the correct aspect ratio](#ensure-images-display-with-the-correct-aspect-ratio)
- [Use an image CDN](#use-an-image-cdn)
- [Check the CSS that affects the image's aspect ratio](#check-the-css-that-affects-the-image's-aspect-ratio)
- [Check the image's width and height attributes in the HTML](#check-the-image's-width-and-height-attributes-in-the-html)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Displays images with incorrect aspect ratio

May 2, 2019 <span class="w-author__separator">•</span> Updated Apr 29, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-best-practices" class="w-post-signpost__link">Best Practices audits</a>

If a rendered image has an [aspect ratio](<https://en.wikipedia.org/wiki/Aspect_ratio_(image)>) that's significantly different from the aspect ratio in its source file (the _natural_ aspect ratio), the rendered image may look distorted, possibly creating an unpleasant user experience.

## How the Lighthouse image aspect ratio audit fails <a href="#how-the-lighthouse-image-aspect-ratio-audit-fails" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) flags any image with a rendered dimension more than a few pixels different from the expected dimension when rendered at its natural ratio:

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/OSV0HmZeoy84Tf0Vrt9o.png?auto=format&amp;w=1600 1600w" width="800" height="198" /></figure>There are two common causes for an incorrect image aspect ratio:

- An image is set to explicit width and height values that differ from the source image's dimensions.
- An image is set to a width and height as a percentage of a variably-sized container.

Each Best Practices audit is weighted equally in the Lighthouse Best Practices Score. Learn more in [The Best Practices score](https://developers.google.com/web/tools/lighthouse/v3/scoring#best-practices).

## Ensure images display with the correct aspect ratio <a href="#ensure-images-display-with-the-correct-aspect-ratio" class="w-headline-link">#</a>

### Use an image CDN <a href="#use-an-image-cdn" class="w-headline-link">#</a>

An image CDN can make it easier to automate the process of creating different sized versions of your images. Check out [Use image CDNs to optimize images](/image-cdns/) for an overview and [How to install the Thumbor image CDN](/install-thumbor/) for a hands-on codelab.

### Check the CSS that affects the image's aspect ratio <a href="#check-the-css-that-affects-the-image&#39;s-aspect-ratio" class="w-headline-link">#</a>

If you're having trouble finding the CSS that's causing the incorrect aspect ratio, Chrome DevTools can show you the CSS declarations that affect a given image. See Google's [View only the CSS that's actually applied to an element](https://developers.google.com/web/tools/chrome-devtools/css/reference#computed) page for more information.

### Check the image's `width` and `height` attributes in the HTML <a href="#check-the-image&#39;s-width-and-height-attributes-in-the-html" class="w-headline-link">#</a>

When possible, it's good practice to specify each image's `width` and `height` attributes in your HTML so that the browser can allocate space for the image. This approach helps to ensure that content below the image doesn't shift once the image is loaded.

However, specifying image dimensions in HTML can be difficult if you're working with responsive images because there's no way to know the width and height until you know the viewport dimensions. Consider using the [CSS Aspect Ratio](https://www.npmjs.com/package/css-aspect-ratio) library or [aspect ratio boxes](https://css-tricks.com/aspect-ratio-boxes/) to help preserve aspect ratios for responsive images.

Finally, check out the [Serve images with correct dimensions](/serve-images-with-correct-dimensions) post to learn how to serve images that are the right size for each user's device.

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **Displays images with incorrect aspect ratio** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/image-aspect-ratio.js)
- [CSS Aspect Ratio](https://www.npmjs.com/package/css-aspect-ratio)
- [Aspect Ratio Boxes](https://css-tricks.com/aspect-ratio-boxes/)
- [Serve images with correct dimensions](/serve-images-with-correct-dimensions)

<span class="w-mr--sm">Last updated: Apr 29, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-best-practices/image-aspect-ratio/index.md)

<a href="/lighthouse-best-practices" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
