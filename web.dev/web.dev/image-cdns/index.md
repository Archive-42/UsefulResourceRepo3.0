

## <a href="#use-image-cdns-to-optimize-images" class="w-toc__header--link">Use image CDNs to optimize images</a>

- [Why use an image CDN?](#why-use-an-image-cdn)
- [What's an image CDN?](#what's-an-image-cdn)
- [How image CDNs use URLs to indicate optimization options](#how-image-cdns-use-urls-to-indicate-optimization-options)
- [Origin](#origin)
- [Image](#image)
- [Security key](#security-key)
- [Transformations](#transformations)
- [Types of Image CDNs](#types-of-image-cdns)
- [Self-managed image CDNs](#self-managed-image-cdns)
- [Third-party image CDNs](#third-party-image-cdns)
- [Choosing an image CDN](#choosing-an-image-cdn)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Use image CDNs to optimize images

Aug 14, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

- <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
- <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
- <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

## Why use an image CDN? <a href="#why-use-an-image-cdn" class="w-headline-link">#</a>

Image content delivery networks (CDNs) are excellent at optimizing images. Switching to an image CDN can yield a [40–80% savings](https://www.youtube.com/watch?v=YJGCZCaIZkQ&t=1010s) in image file size. In theory, it's possible to achieve the same results using only build scripts, but it's rare in practice.

## What's an image CDN? <a href="#what&#39;s-an-image-cdn" class="w-headline-link">#</a>

Image CDNs specialize in the transformation, optimization, and delivery of images. You can also think of them as APIs for accessing and manipulating the images used on your site. For images loaded from an image CDN, an image URL indicates not only which image to load, but also parameters like size, format, and quality. This makes it easy to create variations of an image for different use cases.

<figure><img src="https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format" alt="Examples of transformations image CDNs can perform based on parameters in image URLs." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/OIF2VcXp8P6O7tQvw53B.jpg?auto=format&amp;w=1600 1600w" width="800" height="408" /><figcaption>Examples of transformations image CDNs can perform based on parameters in image URLs.</figcaption></figure>Image CDNs are different from build-time image optimization scripts in that they create new versions of images as they're needed. As a result, CDNs are generally better suited to creating images that are heavily customized for each individual client than build scripts are.

## How image CDNs use URLs to indicate optimization options <a href="#how-image-cdns-use-urls-to-indicate-optimization-options" class="w-headline-link">#</a>

Image URLs used by image CDNs convey important information about an image and the transformations and optimizations that should be applied to it. URL formats will vary depending on image CDN, but at a high-level, they all have similar features. Let's walk through some of the most common features.

<figure><img src="https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/GA4udXeYUEjHSY4N0Qew.jpg?auto=format&amp;w=1600 1600w" width="800" height="127" /></figure>### Origin <a href="#origin" class="w-headline-link">#</a>

An image CDN can live on your own domain or the domain of your image CDN. Third-party image CDNs typically offer the option of using a custom domain for a fee. Using your own domain makes it easier to switch image CDNs at a later date because no URL changes will be needed.

The example above uses the image CDN's domain ("example-cdn.com") with a personalized subdomain, rather than a custom domain.

### Image <a href="#image" class="w-headline-link">#</a>

Image CDNs can usually be configured to automatically retrieve images from their existing locations when they're needed. This capability is often achieved by including the complete URL of the _existing image_ within the URL for the image generated by the image CDN. For example, you might see a URL that looks like this: `https://my-site.example-cdn.com/https://flowers.com/daisy.jpg/quality=auto`. This URL would retrieve and optimize the image that exists at `https://flowers.com/daisy.jpg`.

Another widely supported way of uploading images to an image CDN is to send them via an HTTP POST request to the image CDN's API.

### Security key <a href="#security-key" class="w-headline-link">#</a>

A security key prevents other people from creating new versions of your images. If this feature is enabled, each new version of an image requires a unique security key. If someone tries to change the parameters of the image URL but doesn't provide a valid security key, they won't be able to create a new version. Your image CDN will take care of the details of generating and tracking security keys for you.

### Transformations <a href="#transformations" class="w-headline-link">#</a>

Image CDNs offer tens, and in some cases hundreds, of different image transformations. These transformations are specified via the URL string, and there are no restrictions on using multiple transformations at the same time. In the context of web performance, the most important image transformations are size, pixel density, format, and compression. These transformations are the reason why switching to an image CDN typically results in a significant reduction in image size.

There tends to be an objectively best setting for performance transformations, so some image CDNs support an "auto" mode for these transformations. For example, instead of specifying that images be transformed to the WebP format, you could allow the CDN to automatically select and serve the optimal format. Signals that an image CDN can use to determine the best way to transform an image include:

- [Client hints](https://developers.google.com/web/updates/2015/09/automating-resource-selection-with-client-hints) (for example, viewport width, DPR, and image width)
- The [`Save-Data`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Save-Data) header
- The [User-Agent](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/User-Agent) request header
- The [Network Information API](https://developer.mozilla.org/en-US/docs/Web/API/Network_Information_API)

For example, the image CDN might serve JPEG XR to an Edge browser, WebP to a Chrome browser, and JPEG to a very old browser. Auto settings are popular because they allow you to take advantage of image CDNs' significant expertise in optimizing images without the need for code changes to adopt new technologies once they're supported by the image CDN.

## Types of Image CDNs <a href="#types-of-image-cdns" class="w-headline-link">#</a>

Image CDNs can be broken down into two categories: self-managed and third-party-managed.

### Self-managed image CDNs <a href="#self-managed-image-cdns" class="w-headline-link">#</a>

Self-managed CDNs can be a good choice for sites with engineering staff who are comfortable maintaining their own infrastructure.

[Thumbor](https://github.com/thumbor/thumbor) is the only self-managed image CDN available today. While it is open-source and free to use, it generally has fewer features than most commercial CDNs, and its documentation is somewhat limited. [Wikipedia](https://wikitech.wikimedia.org/wiki/Thumbor), [Square](https://medium.com/square-corner-blog/dynamic-images-with-thumbor-a430a1cfcd87), and [99designs](https://99designs.com/tech-blog/blog/2013/07/01/thumbnailing-with-thumbor/) are three sites that use Thumbor. See the [How to install the Thumbor image CDN](/install-thumbor) post for instructions on setting it up.

### Third-party image CDNs <a href="#third-party-image-cdns" class="w-headline-link">#</a>

Third-party image CDNs provide image CDNs as a service. Just as cloud providers provide servers and other infrastructure for a fee; image CDNs provide image optimization and delivery for a fee. Because third-party image CDNs maintain the underlying technology, getting started is fairly simple and can usually be accomplished in 10-15 minutes, although a complete migration for a large site might take far longer. Third-party image CDNs are typically priced based on usage tiers, with most image CDNs providing either a free tier or a free trial to give you an opportunity to try out their product.

## Choosing an image CDN <a href="#choosing-an-image-cdn" class="w-headline-link">#</a>

There are many good options for image CDNs. Some will have more features than others, but all of them will probably help you save bytes on your images and therefore load your pages faster. Besides feature sets, other factors to consider when choosing an image CDN are cost, support, documentation, and ease of setup or migration.

Trying them out yourself before making a decision can also be helpful. Below you can find codelabs with instructions on how to quickly get started with several image CDNs.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Aug 14, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/image-cdns/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/install-thumbor/" class="w-callout__link w-callout__link--codelab">How to install the Thumbor image CDN</a>

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
