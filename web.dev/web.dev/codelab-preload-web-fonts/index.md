





# Preload web fonts to improve loading speed

Apr 23, 2018

[<img src="https://web-dev.imgix.net/image/admin/obrDCmQVA55Oc4bBX5ek.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Garima Mimani" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/obrDCmQVA55Oc4bBX5ek.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/obrDCmQVA55Oc4bBX5ek.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/obrDCmQVA55Oc4bBX5ek.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/obrDCmQVA55Oc4bBX5ek.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/obrDCmQVA55Oc4bBX5ek.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/gmimani/)

<a href="/authors/gmimani/" class="w-author__name-link">Garima Mimani</a>

- <a href="https://github.com/garimamimani" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@garimamimani" class="w-author__link">Glitch</a>

This codelab uses Chrome DevTools. [Download Chrome](https://www.google.com/chrome) if you don't already have it.

This codelab shows you how to preload web fonts using `rel="preload"` to remove any flash of unstyled text (FOUT).

## Measure <a href="#measure" class="w-headline-link">#</a>

First measure how the website performs before adding any optimizations.

1.  To preview the site, press **View App**. Then press **Fullscreen** ![fullscreen](/images/glitch/fullscreen.svg).
2.  Press `Control+Shift+J` (or `Command+Option+J` on Mac) to open DevTools.
3.  Click the **Lighthouse** tab.
4.  Make sure the **Performance** checkbox is selected in the _Categories_ list.
5.  Click the **Generate report** button.

The Lighthouse report that is generated will show you the fetching sequence of resources under **Maximum critical path latency**.

<img src="https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format" alt="Webfonts are present in the critical request chain." class="w-screenshot" sizes="(min-width: 704px) 704px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/eperh8ZUnjhsDlnJdNIG.png?auto=format&amp;w=1408 1408w" width="704" height="198" />

In the above audit the web fonts are part of the critical request chain and fetched last. The [**critical request chain**](/critical-request-chains) represents the order of resources that are prioritized and fetched by the browser. In this application, the web fonts (Pacfico and Pacifico-Bold) are defined using the [@font-face](https://developers.google.com/web/fundamentals/performance/optimizing-content-efficiency/webfont-optimization#defining_a_font_family_with_font-face) rule and are the last resource fetched by the browser in the critical request chain. Typically, webfonts are lazy loaded which means that they are not loaded until the critical resources are downloaded (CSS, JS).

Here is the sequence of the resources fetched in the application:

<img src="https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format" alt="Webfonts are lazy loaded." class="w-screenshot" sizes="(min-width: 583px) 583px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/9oBNjZORrBj6X8RVlr9t.png?auto=format&amp;w=1166 1166w" width="583" height="256" />

## Preloading Web fonts <a href="#preloading-web-fonts" class="w-headline-link">#</a>

In order to avoid FOUT, you can preload web fonts that are required immediately. Add the `Link` element for this application at the head of the document:

    <head>
     <!-- ... -->
     <link rel="preload" href="/assets/Pacifico-Bold.woff2" as="font" type="font/woff2" crossorigin>
    </head>

The `as="font" type="font/woff2"` attributes tell the browser to download this resource as a font and helps in prioritization of the re­source queue.

The `crossorigin` attribute indicates whether the resource should be fetched with a CORS request as the font may come from a different domain. Without this attribute, the preloaded font is ignored by the browser.

Since Pacifico-Bold is used in the page header, we added a preload tag to fetch it even sooner. It isn't important to preload the Pacifico.woff2 font because it styles the text that is below the fold.

Reload the application and run lighthouse again. Check the **Maximum critical path latency** section.

<img src="https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format" alt="Pacifico-Bold webfont is preloaded and removed from the cricical request chain" class="w-screenshot" sizes="(min-width: 645px) 645px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/lC85s7XSc8zEXgtwLsFu.png?auto=format&amp;w=1290 1290w" width="645" height="166" />

Notice how the `Pacifico-Bold.woff2` is removed from the critical request chain. It is fetched earlier in the application.

<img src="https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format" alt="Pacifico-Bold webfont is preloaded" class="w-screenshot" sizes="(min-width: 553px) 553px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/BrXidcKZfCbbUbkcSwas.png?auto=format&amp;w=1106 1106w" width="553" height="254" />

With preload, the browser knows that it needs to download this file earlier. It is important to note that if not used correctly, preload can harm performance by making unnecessary requests for resources that are not used.

<a href="/preload-critical-assets" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to article</a>

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
