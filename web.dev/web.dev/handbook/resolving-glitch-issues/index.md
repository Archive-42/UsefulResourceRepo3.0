<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

og/" class="gc-analytics-event header-default**link">Blog</a> <a href="/about/" class="gc-analytics-event header-default**link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

## <a href="#resolving-glitch-issues" class="w-toc__header--link">Resolving Glitch issues</a>

- [Project is suspended](#project-is-suspended)
- [Exceeding disk usage](#exceeding-disk-usage)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Resolving Glitch issues

Apr 27, 2020

[<img src="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Houssein Djirdeh" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/BibySYHD7JweNcHZCCOe.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/houssein/)

<a href="/authors/houssein/" class="w-author__name-link">Houssein Djirdeh</a>

- <a href="https://twitter.com/hdjirdeh" class="w-author__link">Twitter</a>
- <a href="https://github.com/housseindjirdeh" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@housseindjirdeh" class="w-author__link">Glitch</a>
- <a href="https://houssein.me/" class="w-author__link">Blog</a>

web.dev uses Glitch to embed web-based sample apps and development environments in its posts and codelabs. See the [Sample apps](/handbook/markup-sample-app) post for information about how to set up a Glitch.

This post will show you how to resolve some common Glitch issues.

Subscribing to Glitch and paying for Boosted Apps will automatically increase memory and disk space as well as improve your rate limits. That's an always an option if you run into any of the disk/memory issues mentioned in this post. [Learn more](https://glitch.happyfox.com/kb/article/73-boosted-apps-what-s-that/).

## Project is suspended <a href="#project-is-suspended" class="w-headline-link">#</a>

If you see a "Project has been suspended" message when opening a new project, contact support via their public forum or by emailing `support@glitch.com`. You should receive a reply soon with steps you can take to fix your project.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format" alt="Suspended-project" class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FZdKu2XfMTu9XNWaljfJ.png?auto=format&amp;w=1600 1600w" width="800" height="453" />

## Exceeding disk usage <a href="#exceeding-disk-usage" class="w-headline-link">#</a>

If you see an App Status warning with exceeded disk limits, you'll need to clear up some space before you can edit and use the project.

<img src="https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format" alt="Disk limit exceeded" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/iszxjOlALJHJnvo10kMl.png?auto=format&amp;w=1600 1600w" width="800" height="429" />

- Remove any unnecessary dependencies from `package.json`
- In the terminal, run `git gc` and `git prune` to remove unneeded files
- Run `du -hd1` to to see which directories are taking up disk space

<img src="https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format" alt="Directories disk usage" sizes="(min-width: 363px) 363px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/tsPeskkc1It3QeYkCJ5I.png?auto=format&amp;w=726 726w" width="363" height="433" />

If an unneeded directory is bloating up on every build and taking up disk space:

- Remove it (`rm -rf directory_name`)

- Consider adding a `prestart` script in `package.json` to ensure it gets deleted on every build

      "scripts": {
        "prestart": "rimraf directory_name",
        "start": "..."
      },

If the `.git` directory is taking up disk space:

- Run `git log --name-only --format="" | cat | sort | uniq -c | sort -nbr` to see which files are being committed to history (note: this will still include files previously committed even if they are now in `.gitignore`)

<img src="https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format" alt="Committed files" sizes="(min-width: 713px) 713px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/kghTObtD4BjdUV950To5.png?auto=format&amp;w=1426 1426w" width="713" height="89" />

- If you see any directories committed many times that shouldn't be, add them to `.gitignore`
- If you don't need `.git` history, remove the `.git` folder (`rm -rf .git`)

<span class="w-mr--sm">Last updated: Apr 27, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/handbook/resolving-glitch-issues/index.md)

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
