





<a href="#registering-a-web-based-payment-app" class="w-toc__header--link">Registering a web-based payment app</a>
------------------------------------------------------------------------------------------------------------------

-   [Browser support](#browser-support)
-   [Configuring a payment app with a web app manifest](#configuring-a-payment-app-with-a-web-app-manifest)
-   [Registering a service worker just-in-time (JIT)](#registering-a-service-worker-just-in-time-(jit))
-   [Configure a payment app with JavaScript](#configure-a-payment-app-with-javascript)
-   [Manually register a service worker](#manually-register-a-service-worker)
-   [Set a payment instrument](#set-a-payment-instrument)
-   [Enable delegations](#enable-delegations)
-   [Debugging a web-based payment app](#debugging-a-web-based-payment-app)
-   [Developing on a local server](#developing-on-a-local-server)
-   [Port forwarding a local server](#port-forwarding-a-local-server)
-   [Remote debugging a website on Android Chrome from desktop DevTools](#remote-debugging-a-website-on-android-chrome-from-desktop-devtools)
-   [Payment Handler event logging](#payment-handler-event-logging)
-   [Next steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Registering a web-based payment app
===================================

Learn how to configure a web-based payment app during registration.

Jul 17, 2020 <span class="w-author__separator">•</span> Updated Jul 20, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/payments" class="w-post-signpost__link">Web Payments</a>

[<img src="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Eiji Kitamura" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/agektmr/)

<a href="/authors/agektmr/" class="w-author__name-link">Eiji Kitamura</a>

-   <a href="https://twitter.com/agektmr" class="w-author__link">Twitter</a>
-   <a href="https://github.com/agektmr" class="w-author__link">GitHub</a>
-   <a href="https://blog.agektmr.com" class="w-author__link">Blog</a>

Web-based payment apps are [Progressive Web Apps (PWA)](/progressive-web-apps/) and run on top of [service workers](https://developer.mozilla.org/docs/Web/API/Service_Worker_API). The service worker in a payment app plays an important role as it captures payment requests from a merchant, launches the payment app, and mediates the communication with the merchant.

To configure a web-based payment app, you need to register available payment methods, delegation options, and a service worker. You can configure your web-based payment app declaratively with a web app manifest or imperatively with JavaScript.

Browser support <a href="#browser-support" class="w-headline-link">#</a>
------------------------------------------------------------------------

Web Payments consists of a few different pieces of technologies and the support status depends on the browser.

<table><tbody><tr class="odd"><td></td><td>Chromium</td><td></td><td></td><td>Safari</td><td></td><td>Firefox</td></tr><tr class="even"><td></td><td>Desktop</td><td>Android</td><td>iOS</td><td>Desktop</td><td>Mobile</td><td></td></tr><tr class="odd"><td>Payment Request API</td><td>✔</td><td>✔</td><td></td><td>✔</td><td>✔</td><td>Under active development</td></tr><tr class="even"><td>Payment Handler API</td><td>✔</td><td>✔</td><td></td><td></td><td></td><td>Under active development</td></tr><tr class="odd"><td>iOS/Android payment app</td><td>✔</td><td>✔</td><td>*</td><td>✔**</td><td>✔**</td><td></td></tr></tbody></table>

\*Chrome is considering making built-in payment apps available on iOS.

\*\*Safari supports Apple Pay but no third party payment apps.

Configuring a payment app with a web app manifest <a href="#configuring-a-payment-app-with-a-web-app-manifest" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------

To configure your web-based payment app declaratively, [serve a web app manifest](/setting-up-a-payment-method/#step-3:-serve-a-web-app-manifest).

The following properties in the web app manifest are relevant for web-based payment apps:

-   `name`
-   `icons`
-   `serviceworker`
    -   `src`
    -   `scope`
    -   `use_cache`
-   `payment`
    -   `supported_delegations`

Check out [Setting up a payment method](/setting-up-a-payment-method/#step-3:-serve-a-web-app-manifest) to make sure your payment method manifest points to your web app manifest properly.

### Registering a service worker just-in-time (JIT) <a href="#registering-a-service-worker-just-in-time-(jit)" class="w-headline-link">#</a>

**Key Term**: Service workers are usually registered using JavaScript, but they can also be automatically registered by the browser when the user chooses to pay with a web-based payment app on a merchant website. This is called *just-in-time (JIT) registration*.

The JIT registration requires only serving [the web app manifest](/setting-up-a-payment-method/#step-3:-serve-a-web-app-manifest) and no additional coding. If you've already configured your web app manifest and are serving it properly, you should be all set. The browser will handle the rest.

**Caution**: While a single payment method identifier can support multiple payment apps, JIT registration happens only when the payment method manifest points to a single payment app.

Configure a payment app with JavaScript <a href="#configure-a-payment-app-with-javascript" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------

Configuring a web-based payment app using JavaScript allows you to register multiple payment methods and manually unregister service workers.

### Manually register a service worker <a href="#manually-register-a-service-worker" class="w-headline-link">#</a>

A service worker is a JavaScript file you can register using [`navigator.serviceWorker.register()`](https://developer.mozilla.org/docs/Web/API/ServiceWorkerContainer/register). If you have a service worker file named `service-worker.js`, you can register it to the visitor's browser by running the following code:

\[payment handler\] payment app's landing page

    // Feature detection
    if ('serviceWorker' in navigator) {
      // Register a service worker
      navigator.serviceWorker.register(
        // A service worker JS file is separate
        'service-worker.js'
      );
      // PaymentManager requires the service worker to be active.
      // One simple method to activate a service worker is through
      // a `ready` promise.
      const registration = await navigator.serviceWorker.ready;
    …

**Success**: [Workbox](/workbox) is the recommended approach for adding service workers to websites because it automates a lot of boilerplate, makes it easier to follow best practices, and prevents subtle bugs that are common when using the low-level `ServiceWorker` API directly.

If you are new to the service worker, learn more at [Service Workers: an Introduction](https://developers.google.com/web/fundamentals/primers/service-workers).

### Set a payment instrument <a href="#set-a-payment-instrument" class="w-headline-link">#</a>

**Key Term**: Payment apps can support multiple ways for making a payment. For example, a customer can add multiple credit cards or e-wallets to a payment app. Each of them is a payment instrument.

Once the service worker is registered, [a service worker registration object](https://developer.mozilla.org/docs/Web/API/ServiceWorkerRegistration) is returned. Call [`registration.paymentManager.instrument.set()`](https://w3c.github.io/payment-handler/#paymentinstruments-interface) to set a payment instrument. It accepts two arguments, a string that represents the instrument key and a [`PaymentInstrument` object](https://w3c.github.io/payment-handler/#dom-paymentinstrument) that contains details about the instrument.

\[payment handler\] payment app's landing pages

    …
      // Feature detection
      if (!registration.paymentManager) return;


      await registration.paymentManager.instruments.set(
        // Payment instrument key
        'bobpay_card_1',
        // Payment instrument details
        {
          // This parameter will be ignored in Chrome
          name: 'Payment Handler Example',
          // This parameter will be used to match against
          // the PaymentRequest.
          method: 'https://bobpay.xyz/pay'
        }
      );

Arguments

Description

[`instrumentKey`](https://w3c.github.io/payment-handler/#paymentinstruments-interface) (required)

An arbitrary string used only to identify the instrument when you want to update it. It's not visible to customers and it's recommended you use an identifier from your payment app backend.

[`PaymentInstrument`](https://w3c.github.io/payment-handler/#paymentinstrument-dictionary)

Details of the payment instrument.

[`name`](https://developer.mozilla.org/docs/Web/Manifest/name) (required)

Sets a string as the instrument name. Required but ignored in Chrome.

[`icons`](https://developer.mozilla.org/docs/Web/Manifest/icons)

Sets an array of [`ImageObject`](https://w3c.github.io/payment-handler/#imageobject-dictionary)s that the Payment Request sheet will display. Ignored in Chrome.

`method`

A supported payment method identifier.

`capabilities`

Sets the [payment method specific parameters as an object](https://w3c.github.io/payment-handler/#capabilities-example). As of July 2020, basic-card is the only payment method that accepts capabilities.

Chrome ignores the `name` and `icons` properties. It respects the [web app manifest](/setting-up-a-payment-method/#step-3:-serve-a-web-app-manifest)'s respective properties instead, but other browsers may behave differently.

### Enable delegations <a href="#enable-delegations" class="w-headline-link">#</a>

Entering shipping address and contact information through a web form can be a cumbersome experience for customers. It can cause errors and lower conversion rate.

That's why the Payment Request API supports a feature to request shipping address and contact information. This provides multiple benefits:

-   Users can pick the right address with just a few taps.
-   The address is always returned in [the standardized format](https://w3c.github.io/payment-request/#paymentaddress-interface).
-   Submitting an incorrect address is less likely.

Payment apps can integrate this functionality to offer a more unified payment experience. This is called *delegation*.

Checkout flow with a web-based payment app.

Web-based payment apps can declare their support for delegation using the web app manifest's `payment.supported_delegations` field or through JavaScript.

To let the browser know that the payment app accepts a delegation, use [`PaymentManager.enableDelegations()`](https://w3c.github.io/payment-handler/#enabledelegations-method).

\[payment handler\] payment app's landing page

    …
     await registration.paymentManager.enableDelegations([
      'shippingAddress', 'payerName'
    ]);
    …

You can declare supported delegation options as an array of strings:

-   `shippingAddress`: The payment handler can provide a shipping address.
-   `payerName`: The payment handler can provide the payer's name.
-   `payerPhone`: The payment handler can provide the payer's phone number.
-   `payerEmail`: The payment handler can provide the payer's address.

Debugging a web-based payment app <a href="#debugging-a-web-based-payment-app" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------

When developing a web-based payment app frontend, you'll probably jump between merchant context and payment app context. The following debugging tips will help your developing experience on Chrome.

### Developing on a local server <a href="#developing-on-a-local-server" class="w-headline-link">#</a>

Which server do you use for development? Many developers tend to use localhost or a company-internal server environment which can be challenging because powerful features in the browser tend to require a secure environment (HTTPS) and a valid certificate. The Payment Request API and the Payment Handler API are no exception and localhosts or company-internal servers usually don't come with a valid certificate.

The good news is some browsers, including Chrome, exempt certificates for `http://localhost` by default. Also in Chrome, you can exempt the certificate requirement by launching a Chrome instance. For example, to exempt the requirement from `http://*.corp.company.com`, use the following flags:

-   [`--ignore-certificate-errors`](https://chromiumdash.appspot.com/commit/988b56b519836f3d3d94f145ba3554a0c0a7d0a8)
-   [`--unsafely-treat-insecure-origin-as-secure=http://*.corp.company.com`](https://chromiumdash.appspot.com/commit/77a7e1a65d14072149ec4420a0ab523586011d8a)

**macOS**

    /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --ignore-certificate-errors --unsafely-treat-insecure-origin-as-secure=http://*.corp.company.com

**Windows**

    chrome.exe --ignore-certificate-errors --unsafely-treat-insecure-origin-as-secure=http://*.corp.company.com

Learn more about running Chrome with a runtime flag at [Run Chromium with flags](https://www.chromium.org/developers/how-tos/run-chromium-with-flags).

### Port forwarding a local server <a href="#port-forwarding-a-local-server" class="w-headline-link">#</a>

You can port forward the local web server to an Android device using Chrome's DevTools and test how it works from a mobile browser. To learn how to do it, check out [Access Local Servers](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/local-server).

### Remote debugging a website on Android Chrome from desktop DevTools <a href="#remote-debugging-a-website-on-android-chrome-from-desktop-devtools" class="w-headline-link">#</a>

You can also debug Android Chrome on desktop DevTools. To learn how to do it, check out [Get Started with Remote Debugging Android Devices](https://developers.google.com/web/tools/chrome-devtools/remote-debugging).

### Payment Handler event logging <a href="#payment-handler-event-logging" class="w-headline-link">#</a>

[DevTools can display Payment Handler API events](https://developers.google.com/web/updates/2019/09/devtools#payments) for easier local development. Open DevTools on the merchant context and go to the "Payment Handler" section under the **Application** pane. Check "Show events from other domains" and click the "Record" button to start capturing events sent to the service worker that handles payments.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format" alt="Payment Handler event logging." class="w-screenshot w-screenshot--filled" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/FixX1Ld3y0Vgb4ZcSBGc.png?auto=format&amp;w=1600 1600w" width="800" height="585" /><figcaption>Payment Handler event logging.</figcaption></figure>Next steps <a href="#next-steps" class="w-headline-link">#</a>
--------------------------------------------------------------

You learned how to register a service worker, set payment instruments, and define delegation availability for a web-based payment app. The next step is to learn how the service worker can orchestrate a payment transaction at runtime.

-   [Orchestrating payment transactions with a service worker](/orchestrating-payment-transactions)

<a href="/tags/payments/" class="w-chip">Payments</a>

<span class="w-mr--sm">Last updated: Jul 20, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/payments/registering-a-web-based-payment-app/index.md)

<a href="/payments" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
