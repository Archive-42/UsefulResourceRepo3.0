## <a href="#lesscodegreaterandltvideoandgtlesscodegreater-elements-do-not-contain-a-lesscodegreaterandlttrackandgtlesscodegreater-element-with-lesscodegreaterkindandquotdescriptionandquotlesscodegreater" class="w-toc__header--link"><code>&lt;video&gt;</code> elements do not contain a <code>&lt;track&gt;</code> element with <code>[kind="description"]</code></a>

- [How the Lighthouse video description audit fails](#how-the-lighthouse-video-description-audit-fails)
- [How to add audio descriptions to video elements](#how-to-add-audio-descriptions-to-video-elements)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# `<video>` elements do not contain a `<track>` element with `[kind="description"]`

May 2, 2019 <span class="w-author__separator">•</span> Updated Sep 19, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

This audit has been deprecated and was removed in Lighthouse 7.0.

Audio descriptions provide relevant information for videos that dialogue cannot, such as facial expressions and scenes.

## How the Lighthouse video description audit fails <a href="#how-the-lighthouse-video-description-audit-fails" class="w-headline-link">#</a>

Lighthouse flags `<video>` elements that are missing a `<track>` element with the attribute `kind="descriptions"`.

The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to add audio descriptions to video elements <a href="#how-to-add-audio-descriptions-to-video-elements" class="w-headline-link">#</a>

Add at least one track element to the `video` element with attribute `kind="descriptions"`:

    <video width="300" height="200">
        <source src="marathonFinishLine.mp4" type="video/mp4">
        <track src="captions_en.vtt" kind="captions" srclang="en" label="english_captions">
        <track src="audio_desc_en.vtt" kind="descriptions" srclang="en" label="english_description">
        <track src="captions_es.vtt" kind="captions" srclang="es" label="spanish_captions">
        <track src="audio_desc_es.vtt" kind="descriptions" srclang="es" label="spanish_description">
    </video>

The example above includes both audio descriptions for visually impaired users and captions for hearing impaired users. Captions make video elements usable for deaf or hearing-impaired users. See also [`<video>` elements do not contain a `<track>` element with `[kind="captions"]`](/video-caption).

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **`<video>` elements do not contain a `<track>` element with `[kind="description"]`** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/video-description.js)
- [`<video>` elements must have an audio description `<track>` (Deque University)](https://dequeuniversity.com/rules/axe/3.3/video-description)

<span class="w-mr--sm">Last updated: Sep 19, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/video-description/index.md)

<a href="/lighthouse-accessibility" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
