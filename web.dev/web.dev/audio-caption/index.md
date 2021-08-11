





## <a href="#lesscodegreaterandltaudioandgtlesscodegreater-elements-are-missing-a-lesscodegreaterandlttrackandgtlesscodegreater-element-with-lesscodegreaterkindandquotcaptionsandquotlesscodegreater" class="w-toc__header--link"><code>&lt;audio&gt;</code> elements are missing a <code>&lt;track&gt;</code> element with <code>[kind="captions"]</code></a>

- [How the Lighthouse audio track audit fails](#how-the-lighthouse-audio-track-audit-fails)
- [How to add an audio track](#how-to-add-an-audio-track)
- [Resources](#resources)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# `<audio>` elements are missing a `<track>` element with `[kind="captions"]`

May 2, 2019 <span class="w-author__separator">•</span> Updated Mar 25, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/lighthouse-accessibility" class="w-post-signpost__link">Accessibility audits</a>

This audit has been deprecated.

Captions make audio elements usable for deaf or hearing-impaired users, providing critical information such as who is talking, what they're saying, and other non-speech information.

## How the Lighthouse audio track audit fails <a href="#how-the-lighthouse-audio-track-audit-fails" class="w-headline-link">#</a>

Lighthouse flags `<audio>` elements that are missing `<track>` elements.

The Lighthouse Accessibility score is a weighted average of all the accessibility audits. See the [Lighthouse accessibility scoring](/accessibility-scoring) post for more information.

## How to add an audio track <a href="#how-to-add-an-audio-track" class="w-headline-link">#</a>

Add at least one `<track>` element to the `<audio>` element with attribute `kind="captions"`:

    <audio>
       <source src="favoriteSong.mp3" type="audio/mp3">
       <track src="captions_en.vtt" kind="captions" srclang="en" label="english_captions">
       <track src="captions_es.vtt" kind="captions" srclang="es" label="spanish_captions">
    </audio>

## Resources <a href="#resources" class="w-headline-link">#</a>

- [Source code for **`<audio>` elements are missing a `<track>` element with `[kind="captions"]`** audit](https://github.com/GoogleChrome/lighthouse/blob/master/lighthouse-core/audits/accessibility/audio-caption.js)
- [`<audio>`elements must have a captions `<track>` (Deque University)](https://dequeuniversity.com/rules/axe/3.3/audio-caption)

<span class="w-mr--sm">Last updated: Mar 25, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/lighthouse-accessibility/audio-caption/index.md)

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
