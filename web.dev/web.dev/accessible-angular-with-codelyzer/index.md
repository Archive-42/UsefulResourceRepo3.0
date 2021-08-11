





<img src="https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format" alt="Gondolas." class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/NxNmK1G1YjhB7tU6yVQa.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#audit-your-angular-app&#39;s-accessibility-with-codelyzer" class="w-toc__header--link">Audit your Angular app's accessibility with codelyzer</a>

- [Using codelyzer to detect inaccessible elements](#using-codelyzer-to-detect-inaccessible-elements)
- [Supplementing codelyzer](#supplementing-codelyzer)
- [Enforcing accessibility checks in your continuous integration](#enforcing-accessibility-checks-in-your-continuous-integration)
- [Conclusion](#conclusion)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Audit your Angular app's accessibility with codelyzer

Want to make your Angular site accessible for everyone? This is the right place!

Jul 3, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/angular" class="w-post-signpost__link">Angular</a>

[<img src="https://web-dev.imgix.net/image/admin/GFORxGF2V01nQ1p4lJ3E.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Zama Khan Mohammed" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/GFORxGF2V01nQ1p4lJ3E.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/GFORxGF2V01nQ1p4lJ3E.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/GFORxGF2V01nQ1p4lJ3E.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/GFORxGF2V01nQ1p4lJ3E.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/GFORxGF2V01nQ1p4lJ3E.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mohamedzamakhan/)

<a href="/authors/mohamedzamakhan/" class="w-author__name-link">Zama Khan Mohammed</a>

- <a href="https://twitter.com/mohamedzamakhan" class="w-author__link">Twitter</a>
- <a href="https://github.com/mohammedzamakhan" class="w-author__link">GitHub</a>
- <a href="https://blog.mgechev.com/" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Minko Gechev" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/OPpZ9x8KCVcxvqgdWXM5.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mgechev/)

<a href="/authors/mgechev/" class="w-author__name-link">Minko Gechev</a>

- <a href="https://twitter.com/mgechev" class="w-author__link">Twitter</a>
- <a href="https://github.com/mgechev" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@mgechev" class="w-author__link">Glitch</a>
- <a href="https://blog.mgechev.com/" class="w-author__link">Blog</a>

Making your app accessible means that all users, including those with special needs, can use it and understand the content. According to the [World Health Report](https://www.who.int/disabilities/world_report/2011/report.pdf), more than a billion people—about 15% of the world's population—have some form of disability. So [accessibility](/accessible) is a priority for any development project.

In this post you'll learn how to add [codelyzer's](https://github.com/mgechev/codelyzer) accessibility checks to the build process for an Angular app. This approach lets you catch accessibility bugs directly in your text editor as you code.

## Using codelyzer to detect inaccessible elements <a href="#using-codelyzer-to-detect-inaccessible-elements" class="w-headline-link">#</a>

[codelyzer](https://github.com/mgechev/codelyzer) is a tool that sits on top of [TSLint](https://palantir.github.io/tslint/) and checks whether Angular TypeScript projects follow a set of linting rules. Projects set up with the [Angular command line interface (CLI)](https://cli.angular.io/) include codelyzer by default.

codelyzer has over 50 rules for checking if an Angular application follows best practices. Of those, there are about 10 rules for enforcing accessibility criteria. To learn about the various accessibility checks provided by codelyzer and their rationales, see the [New Accessibility rules in Codelyzer](https://medium.com/ngconf/new-accessibility-rules-in-codelyzer-v5-0-0-85eec1d3e9bb) article.

Currently, all the accessibility rules are experimental and disabled by default. You can enable them by adding them to the TSLint configuration file (`tslint.json`):

    {
      "rulesDirectory": [
        "codelyzer"
      ],
      "rules": {
        ...,
        "template-accessibility-alt-text": true,
        "template-accessibility-elements-content": true,
        "template-accessibility-label-for": true,
        "template-accessibility-tabindex-no-positive": true,
        "template-accessibility-table-scope": true,
        "template-accessibility-valid-aria": true,
        "template-click-events-have-key-events": true,
        "template-mouse-events-have-key-events": true,
        "template-no-autofocus": true,
        "template-no-distracting-elements": true
      }
    }

TSLint works with all popular text editors and IDEs. To use it with VSCode, install the [TSLint plugin](https://marketplace.visualstudio.com/items?itemName=eg2.tslint). In WebStorm, TSLint is enabled by default. For other editors, check the TSLint [README](https://github.com/palantir/tslint#tslint).

With codelyzer's accessibility checks set up, you get a popup showing accessibility errors in TypeScript files or inline templates as you code:

<figure><img src="https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format" alt="A codelyzer popup showing a form element labeling error." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/XArrTmBXfijqQ8AteI76.png?auto=format&amp;w=1600 1600w" width="800" height="433" /><figcaption>A codelyzer popup showing a form element labeling error.</figcaption></figure>To perform linting over the entire project (including external templates), use the `ng lint` command:

<img src="https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format" alt="Linting with Angular CLI" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/sZdIj5CNklqppTk0UCf3.png?auto=format&amp;w=1600 1600w" width="800" height="342" />

## Supplementing codelyzer <a href="#supplementing-codelyzer" class="w-headline-link">#</a>

[Lighthouse](https://developers.google.com/web/tools/lighthouse/) is another tool you can use to enforce accessibility practices in your Angular application. The main difference between codelyzer and Lighthouse is when their checks get performed. Codelyzer statically analyzes the application at development time, without running it. This means that during development you can get direct feedback in your text editor or in the terminal. By contrast, Lighthouse actually runs your application and performs a bunch of checks using dynamic analysis.

Both tools can be useful parts of your development flow. Lighthouse has better coverage given the checks it performs, while codelyzer allows you to iterate faster by getting constant feedback in your text editor.

## Enforcing accessibility checks in your continuous integration <a href="#enforcing-accessibility-checks-in-your-continuous-integration" class="w-headline-link">#</a>

Introducing static accessibility checks in your continuous integration (CI) can be a great enhancement for your development flow. With codelyzer you can easily enforce certain accessibility rules or other practices by running `ng lint` on each code modification (for example for each new pull request).

This way, even before you proceed to code review, your CI can tell you if there are any accessibility violations.

## Conclusion <a href="#conclusion" class="w-headline-link">#</a>

To improve the accessibility of your Angular app:

1.  Enable the experimental accessibility rules in codelyzer.
2.  Perform accessibility linting over your entire project using the Angular CLI.
3.  Fix all the accessibility problems reported by codelyzer.
4.  Consider using Lighthouse for accessibility audits at runtime.

<a href="/tags/accessibility/" class="w-chip">Accessibility</a>

<span class="w-mr--sm">Last updated: Jul 3, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/angular/accessible-angular-with-codelyzer/index.md)

<a href="/angular" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
