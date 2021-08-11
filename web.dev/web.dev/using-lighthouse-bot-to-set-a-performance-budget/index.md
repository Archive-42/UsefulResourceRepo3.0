





<a href="#using-lighthouse-bot-to-set-a-performance-budget" class="w-toc__header--link">Using Lighthouse Bot to set a performance budget</a>
--------------------------------------------------------------------------------------------------------------------------------------------

-   [1. Setup](#1.-setup)
-   [2. Deploy to Firebase](#2.-deploy-to-firebase)
-   [Deploying to Firebase](#deploying-to-firebase)
-   [3. Setting up Travis](#3.-setting-up-travis)
-   [Once you have an account](#once-you-have-an-account)
-   [4. Automate Firebase deployment with Travis](#4.-automate-firebase-deployment-with-travis)
-   [Authorize Firebase](#authorize-firebase)
-   [Add deployment to your Travis setup](#add-deployment-to-your-travis-setup)
-   [5. Setting up Lighthouse Bot](#5.-setting-up-lighthouse-bot)
-   [Add Lighthouse Bot to your project](#add-lighthouse-bot-to-your-project)
-   [Add Lighthouse Bot to your Travis configuration](#add-lighthouse-bot-to-your-travis-configuration)
-   [Make a pull request to trigger Lighthouse Bot test on Travis](#make-a-pull-request-to-trigger-lighthouse-bot-test-on-travis)
-   [More Lighthouse options](#more-lighthouse-options)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Using Lighthouse Bot to set a performance budget
================================================

Jan 28, 2019

<span class="w-post-signpost__title">Appears in:</span> <a href="/fast" class="w-post-signpost__link">Fast load times</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

-   <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
-   <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

You've done hard work to get fast, now make sure you stay fast by automating performance testing with [Lighthouse Bot](https://github.com/ebidel/lighthousebot).

[Lighthouse](https://developers.google.com/web/tools/lighthouse) grades your app in 5 categories, and one of those is performance. While you could try to remember to monitor performance changes with [DevTools](https://developers.google.com/web/tools/lighthouse/#devtools) or [Lighthouse CLI](https://developers.google.com/web/tools/lighthouse/#cli) every time you edit your code, you don't have to do that. Tools can do the tedious stuff for you. [Travis CI](https://travis-ci.com/) is a great service that automatically runs tests for your app in the cloud every time you push new code.

Lighthouse Bot integrates with Travis CI, and its performance budget feature ensures that you won't accidentally downgrade performance without noticing. You can [configure your repository](https://help.github.com/articles/about-required-status-checks/) so that it won't allow merging pull-requests if the Lighthouse scores fall below the threshold you've set (e.g. &lt; 96/100).

<figure><img src="https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format" alt="Lighthouse Bot checks on GitHub." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/LIEdWOuIGubFE0JgBM5Y.png?auto=format&amp;w=1600 1600w" width="800" height="360" /><figcaption>Lighthouse Bot checks on GitHub.</figcaption></figure>Lighthouse Bot used to be called Lighthouse CI.

Although you can test performance on localhost, your site will often perform differently on live servers. To get a more realistic picture, it's best to deploy your site to a staging server. You can use any hosting service; this guide will take [Firebase hosting](https://firebase.google.com/docs/hosting/) for a spin.

1. Setup <a href="#1.-setup" class="w-headline-link">#</a>
----------------------------------------------------------

This simple app helps you sort three numbers.

[Clone the example from GitHub](https://github.com/GoogleChromeLabs/lighthouse-bot-starter), and make sure to add it as a repository on your GitHub account.

2. Deploy to Firebase <a href="#2.-deploy-to-firebase" class="w-headline-link">#</a>
------------------------------------------------------------------------------------

To get started, you'll need a Firebase account. Once you've taken care of that, [create a new project in the Firebase console](https://console.firebase.google.com/) by clicking "Add project":

<img src="https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format" sizes="(min-width: 517px) 517px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/SYTTK9CHxnTt1n7vONKU.png?auto=format&amp;w=1034 1034w" width="517" height="552" />

### Deploying to Firebase <a href="#deploying-to-firebase" class="w-headline-link">#</a>

You'll need [Firebase CLI](https://firebase.google.com/docs/cli/) to deploy the app. Even if you already have it installed, it's good practice to frequently update the CLI to the latest version with this command:

    npm install -g firebase-tools

To authorize the Firebase CLI, run:

    firebase login

Now initialize the project:

    firebase init

The console will ask you a series of questions during setup:

-   When prompted to select features, choose "Hosting."
-   For the default Firebase project, select the project that you've created in the Firebase console.
-   Type in "public" as your public directory.
-   Type "N" (no) to configuring as a single-page app.

This process creates a `firebase.json` configuration file in the root of your project directory.

Congrats, you're ready to deploy! Run:

    firebase deploy

In a split second, you'll have a live app.

3. Setting up Travis <a href="#3.-setting-up-travis" class="w-headline-link">#</a>
----------------------------------------------------------------------------------

You'll need to [register an account](https://travis-ci.com) on Travis and then activate GitHub Apps integration under the Settings section of your profile.

<img src="https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format" alt="GitHub Apps integration on Travis CI" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/fNGAjcYM5Rw3e43PExoD.png?auto=format&amp;w=1600 1600w" width="800" height="508" />

### Once you have an account <a href="#once-you-have-an-account" class="w-headline-link">#</a>

Go to Settings under your profile, hit the Sync account button, and make sure your project repo is listed on Travis.

<img src="https://web-dev.imgix.net/image/admin/dnXFBpBw4WvWbXQL1DQf.png?auto=format" sizes="(min-width: 160px) 160px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/dnXFBpBw4WvWbXQL1DQf.png?auto=format&amp;w=160 160w, https://web-dev.imgix.net/image/admin/dnXFBpBw4WvWbXQL1DQf.png?auto=format&amp;w=182 182w, https://web-dev.imgix.net/image/admin/dnXFBpBw4WvWbXQL1DQf.png?auto=format&amp;w=208 208w, https://web-dev.imgix.net/image/admin/dnXFBpBw4WvWbXQL1DQf.png?auto=format&amp;w=237 237w, https://web-dev.imgix.net/image/admin/dnXFBpBw4WvWbXQL1DQf.png?auto=format&amp;w=270 270w, https://web-dev.imgix.net/image/admin/dnXFBpBw4WvWbXQL1DQf.png?auto=format&amp;w=308 308w, https://web-dev.imgix.net/image/admin/dnXFBpBw4WvWbXQL1DQf.png?auto=format&amp;w=320 320w" width="160" height="54" />

To kick-off continuous integration, you need two things:

1.  To have a `.travis.yml` file in the root directory
2.  To trigger a build by doing a regular old git push

The `lighthouse-bot-starter` repo already has a `.travis.yml` YAML file:

    language: node_js
    node_js:
      - "8.1.3"
    install:
      - npm install
    before_script:
      - npm install -g firebase-tools
    script:
      - webpack

The YAML file tells Travis to install all the dependencies and build your app. Now it's your turn to **push the example app to your own GitHub repository**. If you haven't already, run the following command:

    git push origin main

Click on your repo under Settings in Travis to see your project's Travis dashboard. If everything is cool, you'll see your build go from yellow to green in a couple of minutes. 🎉

4. Automate Firebase deployment with Travis <a href="#4.-automate-firebase-deployment-with-travis" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------

In Step 2, you logged into your Firebase account and deployed the app from the command line with `firebase deploy`. In order for Travis to deploy your app to Firebase, you have to authorize it. How do you do that? With a Firebase token. 🗝️🔥

### Authorize Firebase <a href="#authorize-firebase" class="w-headline-link">#</a>

To generate the token run this command:

    firebase login:ci

It will open a new tab in a browser window so that Firebase can verify you. After that, look back at the console, and you'll see your freshly minted token. Copy it and go back to Travis.

In your project's Travis dashboard, go to **More options** &gt; **Settings** &gt; **Environment variables**.

<img src="https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format" class="w-screenshot" sizes="(min-width: 789px) 789px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/uU7MBc5NdBDZch3ZE3Zd.png?auto=format&amp;w=1578 1578w" width="789" height="233" />

Paste the token in the value field, name the variable `FIREBASE_TOKEN`, and add it.

### Add deployment to your Travis setup <a href="#add-deployment-to-your-travis-setup" class="w-headline-link">#</a>

You need the following lines to tell Travis to deploy the app after every successful build. Add them to the end of the `.travis.yml` file. 🔚

    after_success:
      - firebase deploy --token $FIREBASE_TOKEN --non-interactive

Push this change to GitHub and wait for your first automated deployment. If you take a look at your Travis log, it should soon say ✔️ Deploy complete!

Now whenever you make changes to your app, they will be automatically deployed to Firebase.

5. Setting up Lighthouse Bot <a href="#5.-setting-up-lighthouse-bot" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------

Friendly Lighthouse Bot updates you on your app's Lighthouse scores. It just needs an invitation to your repo.

On GitHub, go to your project's settings and **add "lighthousebot" as a collaborator** (Settings&gt;Collaborators):

<img src="https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format" alt="Lighthouse bot collaborator status" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/H2aLCOr36UDwm5Yk1k9r.png?auto=format&amp;w=1600 1600w" width="800" height="298" />

Approving these requests is a manual process so they don't always happen instantly. Before you start testing, make sure lighthousebot has approved its collaborator status. In the meantime, you also need to add another key to your project's environment variables on Travis. [Leave your email here](https://docs.google.com/forms/d/e/1FAIpQLSdIc3QNIMn7bBMgl2cfxmmo6wGBlUpdLGxjB_ml464t9eCg_A/viewform), and you'll get a Lighthouse Bot key in your inbox. 📬

On Travis, add this key as an environment variable and name it `LIGHTHOUSE_API_KEY`:

<img src="https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/admin/0XCrRSbUg1Sdca8k9xK9.jpg?auto=format&amp;w=1600 1600w" width="800" height="127" />

You can reuse this same key for other projects.

### Add Lighthouse Bot to your project <a href="#add-lighthouse-bot-to-your-project" class="w-headline-link">#</a>

Next, add Lighthouse Bot to your project by running:

    npm i --save-dev https://github.com/ebidel/lighthousebot

And add this bit to the `package.json`:

    "scripts": {
      "lh": "lighthousebot"
    }

### Add Lighthouse Bot to your Travis configuration <a href="#add-lighthouse-bot-to-your-travis-configuration" class="w-headline-link">#</a>

For the final trick, test the performance of the app after every pull request!

In `.travis.yml` add another step in after\_success:

    after_success:
      - firebase deploy --token $FIREBASE_TOKEN --non-interactive
      - npm run lh -- https://staging.example.com

It will run a Lighthouse audit on the given URL, so replace `https://staging.example.com` with the URL of your app (that's your-app-123.firebaseapp.com).

Set your standards high and tweak the setup so you don't accept any changes to the app that bring the performance score below 95:

    - npm run lh -- --perf=95 https://staging.example.com

### Make a pull request to trigger Lighthouse Bot test on Travis <a href="#make-a-pull-request-to-trigger-lighthouse-bot-test-on-travis" class="w-headline-link">#</a>

Lighthouse Bot will only test pull requests, so if you push to the main branch now, you'll just get "This script can only be run on Travis PR requests" in your Travis log.

To trigger the Lighthouse Bot test:

1.  Checkout a new branch
2.  Push it to Github
3.  Make a pull request

Hang tight on that pull request page and wait for Lighthouse Bot to sing! 🎤

<img src="https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format" alt="Passing Lighthouse scores" class="w-screenshot" sizes="(min-width: 586px) 586px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/admin/SmWHb70YqVfagXI3f03D.png?auto=format&amp;w=1172 1172w" width="586" height="329" /> <img src="https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format" alt="Passing Github checks" class="w-screenshot" sizes="(min-width: 462px) 462px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/admin/ZrPGH5OGEY5Y4e9ntUBK.png?auto=format&amp;w=924 924w" width="462" height="189" />

The performance score is great, the app is under budget, and the check has passed!

### More Lighthouse options <a href="#more-lighthouse-options" class="w-headline-link">#</a>

Remember how Lighthouse tests 5 different categories? You can enforce scores for any of those with Lighthouse Bot flags:

    --perf  # performance
    --pwa   # progressive web app score
    --a11y  # accessibility score
    --bp    # best practices score
    --seo   # SEO score

Example:

    npm run lh -- --perf=93 --seo=100 https://staging.example.com

This will fail the PR if the performance score drops below 93 **or** the SEO score drops below 100.

You can also choose not to get Lighthouse Bot's comments with the `--no-comment` option.

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Jan 28, 2019 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/using-lighthouse-bot-to-set-a-performance-budget/index.md)

<a href="/fast" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

-   ### Contribute

    -   <a href="https://github.com/GoogleChrome/web.dev/issues/new?assignees=&amp;labels=bug&amp;template=bug_report.md&amp;title=" class="w-footer__linkbox-link">File a bug</a>
    -   <a href="https://github.com/googlechrome/web.dev" class="w-footer__linkbox-link">View source</a>

-   ### Related content

    -   <a href="https://blog.chromium.org/" class="w-footer__linkbox-link">Chrome updates</a>
    -   <a href="https://developers.google.com/web/" class="w-footer__linkbox-link">Web Fundamentals</a>
    -   <a href="https://developers.google.com/web/showcase/" class="w-footer__linkbox-link">Case studies</a>
    -   <a href="https://devwebfeed.appspot.com/" class="w-footer__linkbox-link">DevWeb Content Firehose</a>
    -   <a href="/podcasts/" class="w-footer__linkbox-link">Podcasts</a>
    -   <a href="/shows/" class="w-footer__linkbox-link">Shows</a>

-   ### Connect

    -   <a href="https://www.twitter.com/ChromiumDev" class="w-footer__linkbox-link">Twitter</a>
    -   <a href="https://www.youtube.com/user/ChromeDevelopers" class="w-footer__linkbox-link">YouTube</a>

<a href="https://developers.google.com/" class="w-footer__utility-logo-link"><img src="/images/lockup-color.png" alt="Google Developers" class="w-footer__utility-logo" width="185" height="33" /></a>

-   <a href="https://developer.chrome.com/" class="w-footer__utility-link">Chrome</a>
-   <a href="https://firebase.google.com/" class="w-footer__utility-link">Firebase</a>
-   <a href="https://cloud.google.com/" class="w-footer__utility-link">Google Cloud Platform</a>
-   <a href="https://developers.google.com/products" class="w-footer__utility-link">All products</a>

<!-- -->

-   <a href="https://policies.google.com/" class="w-footer__utility-link">Terms &amp; Privacy</a>
-   <a href="/community-guidelines/" class="w-footer__utility-link">Community Guidelines</a>

Except as otherwise noted, the content of this page is licensed under the [Creative Commons Attribution 4.0 License](https://creativecommons.org/licenses/by/4.0/), and code samples are licensed under the [Apache 2.0 License](https://www.apache.org/licenses/LICENSE-2.0). For details, see the [Google Developers Site Policies](https://developers.google.com/terms/site-policies).
