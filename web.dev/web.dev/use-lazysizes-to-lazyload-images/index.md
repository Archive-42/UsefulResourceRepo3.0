## <a href="#use-lazysizes-to-lazy-load-images" class="w-toc__header--link">Use lazysizes to lazy-load images</a>

- [What is lazysizes?](#what-is-lazysizes)
- [Add lazysizes](#add-lazysizes)
- [Add the lazysizes script](#add-the-lazysizes-script)
- [Update &lt;img&gt; and/or &lt;picture&gt; tags](#update-lessimggreater-andor-lesspicturegreater-tags)
- [Verify](#verify)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Use lazysizes to lazy-load images

Nov 5, 2018 <span class="w-author__separator">•</span> Updated Apr 10, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

- <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
- <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
- <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

Browser-level lazy-loading is now available! Refer to the [Built-in lazy-loading for the web](/browser-level-image-lazy-loading/) article to learn how to use the `loading` attribute and leverage lazysizes as a fallback for browsers that do not yet support it.

**Lazy-loading** is the strategy of loading resources as they are needed, rather than in advance. This approach frees up resources during the initial page load and avoids loading assets that are never used.

Images that are offscreen during the initial pageload are ideal candidates for this technique. Best of all, [lazysizes](https://github.com/aFarkas/lazysizes) makes this a very simple strategy to implement.

## What is lazysizes? <a href="#what-is-lazysizes" class="w-headline-link">#</a>

[lazysizes](https://github.com/aFarkas/lazysizes) is the most popular library for lazy-loading images. It is a script that intelligently loads images as the user moves through the page and prioritizes images that the user will encounter soon.

## Add lazysizes <a href="#add-lazysizes" class="w-headline-link">#</a>

It is simple to add lazysizes:

- Add the lazysizes script to your pages.
- Choose the images you want to lazy-load.
- Update the `<img>` and/or `<picture>` tags for those images.

### Add the lazysizes script <a href="#add-the-lazysizes-script" class="w-headline-link">#</a>

Add the lazysizes [script](https://github.com/aFarkas/lazysizes/blob/gh-pages/lazysizes.min.js) to your pages:

    <script src="lazysizes.min.js" async></script>

### Update `<img>` and/or `<picture>` tags <a href="#update-lessimggreater-andor-lesspicturegreater-tags" class="w-headline-link">#</a>

**`<img>` tag instructions**

**Before:**

    <img src="flower.jpg" alt="">

**After:**

    <img data-src="flower.jpg" class="lazyload" alt="">

When you update the `<img>` tag you make two changes:

- **Add the `lazyload` class**: This indicates to lazysizes that the image should be lazy-loaded.
- **Change the `src` attribute to `data-src`**: When it is time to load the image, the lazysizes code sets the image `src` attribute using the value from the `data-src` attribute.

**`<picture>` tag instructions**

**Before:**

    <picture>
      <source type="image/webp" srcset="flower.webp">
      <source type="image/jpeg" srcset="flower.jpg">
      <img src="flower.jpg" alt="">
    </picture>

**After:**

    <picture>
      <source type="image/webp" data-srcset="flower.webp">
      <source type="image/jpeg" data-srcset="flower.jpg">
      <img data-src="flower.jpg" class="lazyload" alt="">
    </picture>

When you update the `<picture>` tag you make two changes:

- Add the `lazyload` class to the `<img>` tag.
- Change the `<source>` tag `srcset` attribute to `data-srcset`.

**Try it**! [Use lazysizes to only load images that are in the current viewport](/codelab-use-lazysizes-to-lazyload-images).

## Verify <a href="#verify" class="w-headline-link">#</a>

Open DevTools and scroll down the page to see these changes in action. As you scroll, you should see new network requests occur and `<img>` tag classes change from `lazyload` to `lazyloaded`.

Additionally, you can use Lighthouse to verify that you haven't forgotten to lazy-load any offscreen images. Run the Lighthouse Performance Audit (**Lighthouse &gt; Options &gt; Performance**) and look for the results of the **Defer offscreen images** audit.

<a href="/tags/performance/" class="w-chip">Performance</a> <a href="/tags/images/" class="w-chip">Images</a>

<span class="w-mr--sm">Last updated: Apr 10, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/use-lazysizes-to-lazyload-images/index.md)

## Codelabs

See it in action

Learn more and put this guide into action.

- <a href="/codelab-use-lazysizes-to-lazyload-images/" class="w-callout__link w-callout__link--codelab">Lazy load offscreen images with lazysizes</a>

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
