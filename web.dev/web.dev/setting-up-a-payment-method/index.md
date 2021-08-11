<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#setting-up-a-payment-method" class="w-toc__header--link">Setting up a payment method</a>
--------------------------------------------------------------------------------------------------

-   [Browser support](#browser-support)
-   [How a browser discovers a payment app](#how-a-browser-discovers-a-payment-app)
-   [Step 1: Provide the payment method identifier](#step-1:-provide-the-payment-method-identifier)
-   [How merchants use the payment method identifier](#how-merchants-use-the-payment-method-identifier)
-   [Step 2: Serve the payment method manifest](#step-2:-serve-the-payment-method-manifest)
-   [Provide the payment method manifest](#provide-the-payment-method-manifest)
-   [Optionally route the browser to find the payment method manifest in another location](#optionally-route-the-browser-to-find-the-payment-method-manifest-in-another-location)
-   [Step 3: Serve a web app manifest](#step-3:-serve-a-web-app-manifest)
-   [How Chrome determines which payment app to launch](#how-chrome-determines-which-payment-app-to-launch)
-   [Launching the platform-specific payment app](#launching-the-platform-specific-payment-app)
-   [Launching the web-based payment app](#launching-the-web-based-payment-app)
-   [Understanding the special optimizations](#understanding-the-special-optimizations)
-   [How browsers can skip the Payment Request UI and launch a payment app directly](#how-browsers-can-skip-the-payment-request-ui-and-launch-a-payment-app-directly)
-   [When is a web-based payment app registered just-in-time (JIT)?](#jit-register)
-   [Next Steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Setting up a payment method
===========================

A payment transaction using Web Payments starts with the discovery of your  
payment app. Learn how to set up a payment method and get your payment app  
ready for merchants and customers to make payments.

May 25, 2020 <span class="w-author__separator">•</span> Updated Jul 17, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/payments" class="w-post-signpost__link">Web Payments</a>

[<img src="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Eiji Kitamura" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/agektmr/)

<a href="/authors/agektmr/" class="w-author__name-link">Eiji Kitamura</a>

-   <a href="https://twitter.com/agektmr" class="w-author__link">Twitter</a>
-   <a href="https://github.com/agektmr" class="w-author__link">GitHub</a>
-   <a href="https://blog.agektmr.com" class="w-author__link">Blog</a>

To be used with the Payment Request API, a payment app must be associated with a payment method identifier. Merchants that want to integrate with a payment app will use the payment method identifier to indicate that to the browser. This article discusses how payment app discovery works, and how to configure your payment app to be properly discovered and invoked by a browser.

If you are new to the concept of Web Payments or how a payment transaction works through payment apps, read the following articles first:

-   [Empowering payment apps with Web Payments](/empowering-payment-apps-with-web-payments)
-   [Life of a payment transaction](/life-of-a-payment-transaction)

Browser support <a href="#browser-support" class="w-headline-link">#</a>
------------------------------------------------------------------------

Web Payments consists of a few different pieces of technologies and the support status depends on the browser.

<table><tbody><tr class="odd"><td></td><td>Chromium</td><td></td><td></td><td>Safari</td><td></td><td>Firefox</td></tr><tr class="even"><td></td><td>Desktop</td><td>Android</td><td>iOS</td><td>Desktop</td><td>Mobile</td><td></td></tr><tr class="odd"><td>Payment Request API</td><td>✔</td><td>✔</td><td></td><td>✔</td><td>✔</td><td>Under active development</td></tr><tr class="even"><td>Payment Handler API</td><td>✔</td><td>✔</td><td></td><td></td><td></td><td>Under active development</td></tr><tr class="odd"><td>iOS/Android payment app</td><td>✔</td><td>✔</td><td>*</td><td>✔**</td><td>✔**</td><td></td></tr></tbody></table>

\*Chrome is considering making built-in payment apps available on iOS.

\*\*Safari supports Apple Pay but no third party payment apps.

How a browser discovers a payment app <a href="#how-a-browser-discovers-a-payment-app" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------

Every payment app needs to provide the following:

-   URL-based payment method identifier
-   Payment method manifest (except when the payment method identifier is provided by a third party)
-   Web app manifest

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kvLIMUysDNEG3IfPxKz6.png?auto=format&amp;w=1600 1600w" width="800" height="587" /></figure>The discovery process starts when a merchant initiates a transaction:

1.  The browser sends a request to the [payment method identifier](https://w3c.github.io/payment-method-manifest/) URL and fetches the [payment method manifest](https://w3c.github.io/payment-method-manifest/).
2.  The browser determines the [web app manifest](https://developer.mozilla.org/docs/Web/Manifest) URL from the payment method manifest and fetches the web app manifest.
3.  The browser determines whether to launch the OS payment app or the web-based payment app from the web app manifest.

The next sections explain in detail how to set up your own payment method so that browsers can discover it.

Step 1: Provide the payment method identifier <a href="#step-1:-provide-the-payment-method-identifier" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------------

A [payment method identifier](https://w3c.github.io/payment-method-id/#dfn-payment-method-identifiers) is a URL-based string. For example, Google Pay's identifier is `https://google.com/pay`. Payment app developers can pick any URL as a payment method identifier as long as they have control over it and can serve arbitrary content. In this article, we'll use [`https://bobpay.xyz/pay`](https://bobpay.xyz/pay) as the payment method identifier.

Payment apps can support third party payment methods as well.

### How merchants use the payment method identifier <a href="#how-merchants-use-the-payment-method-identifier" class="w-headline-link">#</a>

A `PaymentRequest` object is constructed with a list of [payment method identifiers](https://www.w3.org/TR/payment-method-id/) that identifies payment apps a merchant decides to accept. Payment method identifiers are set as a value for the `supportedMethods` property. For example:

\[merchant\] requests payment:

    const request = new PaymentRequest([{
      supportedMethods: 'https://bobpay.xyz/pay'
    }], {
      total: {
        label: 'total',
        amount: { value: '10', currency: 'USD' }
      }
    });

Redirects are allowed up to three times within the same-site for a payment method identifier in Chrome.

Step 2: Serve the payment method manifest <a href="#step-2:-serve-the-payment-method-manifest" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------

A [payment method manifest](https://w3c.github.io/payment-method-manifest/) is a JSON file that defines which payment app can use this payment method.

### Provide the payment method manifest <a href="#provide-the-payment-method-manifest" class="w-headline-link">#</a>

When a merchant initiates a payment transaction, [the browser sends an HTTP `GET` request to the payment method identifier URL](https://w3c.github.io/payment-method-manifest/#accessing). The server responds with the payment method manifest body.

A payment method manifest has two fields, `default_applications` and `supported_origins`.

Property name

Description

`default_applications` (required)

An array of URLs that points to web app manifests where the payment apps are hosted. (The URL can be a relative). This array is expected to reference the development manifest, production manifest, etc.

`supported_origins`

An array of URLs that points to origins that may host third-party payment apps implementing the same payment method. Note that a payment method can be implemented by multiple payment apps.

Payment method manifest fields

A payment method manifest file should look like this:

\[payment handler\] /payment-manifest.json:

    {
      "default_applications": ["https://bobpay.xyz/manifest.json"],
      "supported_origins": [
        "https://alicepay.friendsofalice.example"
      ]
    }

When the browser reads the `default_applications` field, it finds a list of links to [web app manifests](https://w3c.github.io/manifest/) of supported payment apps.

Chrome supports a single default payment app per single payment method as of Chrome 83.

### Optionally route the browser to find the payment method manifest in another location <a href="#optionally-route-the-browser-to-find-the-payment-method-manifest-in-another-location" class="w-headline-link">#</a>

The payment method identifier URL can optionally respond with a `Link` header that points to another URL where the browser can fetch the payment method manifest. This is useful when a payment method manifest is hosted at a different server or when the payment app is served by a third party.

<img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format" alt="How a browser discovers the payment app from a URL-based payment method identifier with redirects" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/5YDqz1ppLkjHd9HYgXYH.png?auto=format&amp;w=1600 1600w" width="800" height="698" />

Configure the payment method server to respond with a HTTP `Link` header with the `rel="payment-method-manifest"` attribute and the [payment method manifest](https://w3c.github.io/payment-method-manifest/) URL.

For example, if the manifest is at `https://bobpay.xyz/payment-manifest.json`, the response header would include:

    Link: <https://bobpay.xyz/payment-manifest.json>; rel="payment-method-manifest"

The URL can be a fully-qualified domain name or a relative path. Inspect `https://bobpay.xyz/pay/` for network traffic to see an example. You may use a `curl` command as well:

    curl --include https://bobpay.xyz/pay

Learn more about [payment method practices at W3C documentation](https://github.com/w3c/payment-request-info/wiki/PaymentMethodPractice).

Step 3: Serve a web app manifest <a href="#step-3:-serve-a-web-app-manifest" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------

A [web app manifest](https://developer.mozilla.org/en-US/docs/Web/Manifest) is used to define a web app as the name suggests. It's a widely used manifest file to [define a Progressive Web App (PWA)](/add-manifest/).

Typical web app manifest would look like this:

\[payment handler\] /manifest.json:

    {
      "name": "Pay with Bobpay",
      "short_name": "Bobpay",
      "description": "This is an example of the Payment Handler API.",
      "icons": [
        {
          "src": "images/manifest/icon-192x192.png",
          "sizes": "192x192",
          "type": "image/png"
        },
        {
          "src": "images/manifest/icon-512x512.png",
          "sizes": "512x512",
          "type": "image/png"
        }
      ],
      "serviceworker": {
        "src": "service-worker.js",
        "scope": "/",
        "use_cache": false
      },
      "payment": {
        "supported_delegations": [
          "shippingAddress",
          "payerName",
          "payerEmail",
          "payerPhone"
        ]
      },
      "start_url": "/",
      "display": "standalone",
      "theme_color": "#3f51b5",
      "background_color": "#3f51b5",
      "related_applications": [
        {
          "platform": "play",
          "id": "com.example.android.samplepay",
          "min_version": "1",
          "fingerprints": [
            {
              "type": "sha256_cert",
              "value": "4C:FC:14:C6:97:DE:66:4E:66:97:50:C0:24:CE:5F:27:00:92:EE:F3:7F:18:B3:DA:77:66:84:CD:9D:E9:D2:CB"
            }
          ]
        }
      ]
    }

The information described in a web app manifest is also used to define how a payment app appears in the Payment Request UI.

Property name

Description

`name` (required)

Used as the payment app name.

`icons` (required)

Used as the payment app icon. Only Chrome uses these icons; other browsers may use them as fallback icons if you don't specify them as part of the payment instrument.

`serviceworker`

Used to detect the service worker that runs as the web-based payment app.

`serviceworker.src`

The URL to download the service worker script from.

`serviceworker.scope`

A string representing a URL that defines a service worker's registration scope.

`serviceworker.use_cache`

The URL to download the service worker script from.

`related_applications`

Used to detect the app that acts as the OS-provided payment app. Find more details at [Android payment apps developer guide](/native-payment-apps-overview).

`prefer_related_applications`

Used to determine which payment app to launch when both an OS-provided payment app and a web-based payment app are available.

`payment.supported_delegations`

A string array used to determine the additional information that the payment app can provide. `shippingAddress`, `payerName`, `payerEmail`, and `payerPhone` are valid values.

Important web app manifest fields

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format" alt="Payment app label and icon." class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/lyP2t7T5R5bVzqh0LUTx.png?auto=format&amp;w=1600 1600w" width="800" height="237" /><figcaption>Payment app label and icon.</figcaption></figure>The web app manifest's `name` property is used as the payment app name, `icons` property is used as the payment app icon.

How Chrome determines which payment app to launch <a href="#how-chrome-determines-which-payment-app-to-launch" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------

### Launching the platform-specific payment app <a href="#launching-the-platform-specific-payment-app" class="w-headline-link">#</a>

To launch the platform-specific payment app, the following conditions must be met:

-   The `related_applications` field is specified in the web app manifest and:
    -   The installed app's package ID and signature match, while the minimum version (`min_version`) in the web app manifest is less than or equal to the version of the installed application.
-   The `prefer_related_applications` field is `true`.
-   The platform-specific payment app is installed and has:
    -   An intent filter of `org.chromium.action.PAY`.
    -   A payment method identifier specified as the value for the `org.chromium.default_payment_method_name` property.

Check out the [Android payment apps: developer's guide](/android-payment-apps-developers-guide/) for more details about how to set these up.

\[payment handler\] /manifest.json

    "prefer_related_applications": true,
    "related_applications": [{
      "platform": "play",
      "id": "xyz.bobpay.app",
      "min_version": "1",
      "fingerprints": [{
        "type": "sha256_cert",
        "value": "92:5A:39:05:C5:B9:EA:BC:71:48:5F:F2:05:0A:1E:57:5F:23:40:E9:E3:87:14:EC:6D:A2:04:21:E0:FD:3B:D1"
      }]
    }]

If the browser has determined that the platform-specific payment app is available, the discovery flow is terminated here. Otherwise it continues to the next step -- launching the web-based payment app.

### Launching the web-based payment app <a href="#launching-the-web-based-payment-app" class="w-headline-link">#</a>

The web-based payment app should be specified in the web app manifest's `serviceworker` field.

\[payment handler\] /manifest.json:

    "serviceworker": {
      "src": "payment-handler.js"
    }

The browser launches the web-based payment app by sending a `paymentrequest` event to the service worker. The service worker doesn't have to be registered in advance. [It can be registered just-in-time](#jit-register).

Understanding the special optimizations <a href="#understanding-the-special-optimizations" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------

### How browsers can skip the Payment Request UI and launch a payment app directly <a href="#how-browsers-can-skip-the-payment-request-ui-and-launch-a-payment-app-directly" class="w-headline-link">#</a>

In Chrome, when `show()` method of `PaymentRequest` is called, the Payment Request API displays a browser-provided UI called the "Payment Request UI". This UI allows users to choose a payment app, shipping options and delivery address, and payer's contact information. After pressing the **Continue** button in the Payment Request UI, the selected payment app is launched.

Payment Request UI intervenes before launching the payment app.

Showing the Payment Request UI before launching a payment app increases the number of steps needed for a user to fulfill a payment. To optimize the process, the browser can delegate fulfillment of that information to payment apps and launch a payment app directly without showing the Payment Request UI when `show()` is called.

Skip the Payment Request UI and launch the payment app directly.

To launch a payment app directly, the following conditions must be met:

-   `show()` is triggered with a user gesture (for example, a mouse click).
-   There is only a single payment app that:
    -   Supports the requested payment method identifier.
    -   Can fulfill all the delegated requirements (such as shipping address, payer's phone number, or payer's name).

Safari currently only supports Apple Pay so it always launches the app directly, skipping the Payment Request UI.

### When is a web-based payment app registered just-in-time (JIT)? <a href="#jit-register" class="w-headline-link">#</a>

Web-based payment apps can be launched without the user's explicit prior visit to the payment app website and registering the service worker. The service worker can be registered just-in-time when the user chooses to pay with the web-based payment app. There are two variations for the registration timing:

-   If the Payment Request UI is shown to the user, the app is registered just-in-time and launched when the user clicks **Continue**.
-   If the Payment Request UI is skipped, the payment app is registered just-in-time and launched directly. Skipping the Payment Request UI to launch a just-in-time registered app requires a user gesture, which prevents unexpected registration of cross-origin service workers.

While a single payment method identifier can support multiple payment apps, JIT-registration happens only when the payment method manifest points to a single payment app.

Next Steps <a href="#next-steps" class="w-headline-link">#</a>
--------------------------------------------------------------

Now that you have your payment app discoverable, learn how to develop a platform-specific payment app and a web-based payment app.

-   [Android payment apps: developer's guide](/android-payment-apps-developers-guide)
-   [Web based payment apps developer guide](/web-based-payment-apps-overview)

<a href="/tags/payments/" class="w-chip">Payments</a>

<span class="w-mr--sm">Last updated: Jul 17, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/payments/setting-up-a-payment-method/index.md)

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
