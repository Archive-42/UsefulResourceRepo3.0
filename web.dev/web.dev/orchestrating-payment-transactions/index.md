





<a href="#orchestrating-payment-transactions-with-a-service-worker" class="w-toc__header--link">Orchestrating payment transactions with a service worker</a>
------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [Receive a payment request event from the merchant](#receive-payment-request-event)
-   [Open the payment handler window to display the web-based payment app frontend](#open-payment-handler-window)
-   [Exchange information with the frontend](#exchange-information)
-   [Receive the ready signal from the frontend](#receive-ready-signal)
-   [Pass the transaction details to the frontend](#pass-details)
-   [Return the customer's payment credentials](#return-credentials)
-   [Cancel the payment transaction](#cancel-transaction)
-   [Sample code](#sample-code)
-   [Next steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Orchestrating payment transactions with a service worker
========================================================

How to adapt your web-based payment app to Web Payments and provide a better user experience for customers.

Aug 31, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/payments" class="w-post-signpost__link">Web Payments</a>

[<img src="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Eiji Kitamura" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/agektmr/)

<a href="/authors/agektmr/" class="w-author__name-link">Eiji Kitamura</a>

-   <a href="https://twitter.com/agektmr" class="w-author__link">Twitter</a>
-   <a href="https://github.com/agektmr" class="w-author__link">GitHub</a>
-   <a href="https://blog.agektmr.com" class="w-author__link">Blog</a>

Once [the payment app is registered](/registering-a-web-based-payment-app/), you are ready to accept payment requests from merchants. This post explains how to orchestrate a payment transaction from a service worker during runtime (i.e. when a window is displayed and the user is interacting with it).

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format" alt="Orchestrating payment transactions with a service worker" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/b0Pz24lmWMepSM6tboa1.png?auto=format&amp;w=1600 1600w" width="800" height="945" /><figcaption>Orchestrating payment transactions with a service worker</figcaption></figure>"Runtime payment parameter changes" refer to a set of events that allows the merchant and payment handler to exchange messages while the user is interacting with the payment handler. Learn more in [Handling optional payment information with a service worker](/handling-optional-payment-information).

Receive a payment request event from the merchant <a href="#receive-payment-request-event" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------

When a customer chooses to pay with your web-based payment app and [the merchant invokes `PaymentRequest.show()`](/life-of-a-payment-transaction/#), your service worker will receive a `paymentrequest` event. Add an event listener to the service worker to capture the event and prepare for the next action.

\[payment handler\] service-worker.js:

    …
    let payment_request_event;
    let resolver;
    let client;

    // `self` is the global object in service worker
    self.addEventListener('paymentrequest', async e => {
      if (payment_request_event) {
        // If there's an ongoing payment transaction, reject it.
        resolver.reject();
      }
      // Preserve the event for future use
      payment_request_event = e;
    …

**Caution**: Remember that a service worker is a single instance across different tabs and windows in the same browser. Global variables are shared across all tabs and windows.

The preserved `PaymentRequestEvent` contains important information about this transaction:

<table><thead><tr class="header"><th>Property name</th><th>Description</th></tr></thead><tbody><tr class="odd"><td><code>topOrigin</code></td><td>A string that indicates the origin of the top-level web page (usually the payee merchant). Use this to identify the merchant origin.</td></tr><tr class="even"><td><code>paymentRequestOrigin</code></td><td>A string that indicates the origin of the invoker. This can be the same as <code>topOrigin</code> when the merchant invokes the Payment Request API directly, but may be different if the API is invoked from within an iframe by a third party such as a payment gateway.</td></tr><tr class="odd"><td><code>paymentRequestId</code></td><td>The <code>id</code> property of the <code>PaymentDetailsInit</code> provided to the Payment Request API. If the merchant omits, the browser will provide an auto-generated ID.</td></tr><tr class="even"><td><code>methodData</code></td><td>The payment-method-specific data provided by the merchant as part of <code>PaymentMethodData</code>. Use this to determine the payment transaction details.</td></tr><tr class="odd"><td><code>total</code></td><td>The total amount provided by the merchant as part of <code>PaymentDetailsInit</code>. Use this to construct a UI to let the customer know the total amount to pay.</td></tr><tr class="even"><td><code>instrumentKey</code></td><td>The instrument key selected by the user. This reflects the <code>instrumentKey</code> you provided in advance. An empty string indicates that the user did not specify any instruments.</td></tr><tr class="odd"><td><code>paymentOptions</code></td><td>The <code>PaymentOptions</code> object provided to the Payment Request API by the merchant. Indicates whether the merchant is requesting shipping with <code>requestShipping</code>, the type of shipping with <code>shippingType</code>, billing address with <code>requestBillingAddress</code>, payer's email, name, phone respectively with <code>requestPayerEmail</code>, <code>requestPayerName</code>, <code>requestPayerPhone</code>. Use this to determine what information to include in the <code>PaymentHandlerResponse</code> on a payment authorization.</td></tr><tr class="even"><td><code>shippingOptions</code></td><td>The <code>shippingOptions</code> property of the <code>PaymentDetailsUpdate</code> provided to the Payment Request API. Use this to construct a UI to let the customer select a shipping option.</td></tr></tbody></table>

Open the payment handler window to display the web-based payment app frontend <a href="#open-payment-handler-window" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------------

When a `paymentrequest` event is received, the payment app can open a payment handler window by calling `PaymentRequestEvent.openWindow()`. The payment handler window will present the customers your payment app's interface where they can authenticate, choose shipping address and options, and authorize the payment. We'll cover how to write the frontend code in *Handling payments on the payment frontend* (coming soon).

Checkout flow with a web-based payment app.

Pass a preserved promise to `PaymentRequestEvent.respondWith()` so that you can resolve it with a payment result in the future.

\[payment handler\] service-worker.js:

    …
    self.addEventListener('paymentrequest', async e => {
    …
      // Retain a promise for future resolution
      // Polyfill for PromiseResolver is provided below.
      resolver = new PromiseResolver();

      // Pass a promise that resolves when payment is done.
      e.respondWith(resolver.promise);
      // Open the checkout page.
      try {
        // Open the window and preserve the client
        client = await e.openWindow(checkoutURL);
        if (!client) {
          // Reject if the window fails to open
          throw 'Failed to open window';
        }
      } catch (err) {
        // Reject the promise on failure
        resolver.reject(err);
      };
    });
    …

Use a convenient `PromiseResolver` polyfill to resolve a promise at arbitrary timing.

    class PromiseResolver {
      constructor() {
        this.promise_ = new Promise((resolve, reject) => {
          this.resolve_ = resolve;
          this.reject_ = reject;
        })
      }
      get promise() { return this.promise_ } 
      get resolve() { return this.resolve_ }
      get reject() { return this.reject_ }
    }

For security reasons, the frontend page opened in the payment handler window must have valid HTTPS certificates and no [mixed content](https://developers.google.com/web/fundamentals/security/prevent-mixed-content/what-is-mixed-content); otherwise the payment request will be cancelled by Chrome. Learn more at [Debugging a web-based payment app](/registering-a-web-based-payment-app/#debugging-a-web-based-payment-app).

Exchange information with the frontend <a href="#exchange-information" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------

The payment app's service worker can exchange messages with the payment app's frontend through `ServiceWorkerController.postMessage()`. To receive messages from the frontend, listen to `message` events.

\[payment handler\] service-worker.js:

    // Define a convenient `postMessage()` method
    const postMessage = (type, contents = {}) => {
      if (client) client.postMessage({ type, ...contents });
    }

### Receive the ready signal from the frontend <a href="#receive-ready-signal" class="w-headline-link">#</a>

Once the payment handler window is opened, the service worker should wait for a ready-state signal from the payment app frontend. The service worker can pass important information to the frontend when it is ready.

\[payment handler\] frontend:

    navigator.serviceWorker.controller.postMessage({
      type: 'WINDOW_IS_READY'
    });

\[payment handler\] service-worker.js:

    …
    // Received a message from the frontend
    self.addEventListener('message', async e => {
      let details;
      try {
        switch (e.data.type) {
          // `WINDOW_IS_READY` is a frontend's ready state signal
          case 'WINDOW_IS_READY':
            const { total, paymentOptions, shippingOptions } = payment_request_event;
    …

### Pass the transaction details to the frontend <a href="#pass-details" class="w-headline-link">#</a>

Now send the payment details back. In this case you're only sending the total of the payment request, but you can pass more details if you like.

\[payment handler\] service-worker.js:

    …
            // Pass the payment details to the frontend
            postMessage('PAYMENT_IS_READY', {
              total, paymentOptions, shippingOptions
            });
            break;
    …

\[payment handler\] frontend:

    let paymentOptions;
    let total;
    let shippingOptions;

    navigator.serviceWorker.addEventListener('message', async e => {
      switch (e.data.type) {
          case 'PAYMENT_IS_READY':
            ({ total, paymentOptions, shippingOptions } = e.data);
            // Update the UI
            renderHTML(total, paymentOptions, shippingOptions);
            break;
    …

Return the customer's payment credentials <a href="#return-credentials" class="w-headline-link">#</a>
-----------------------------------------------------------------------------------------------------

When the customer authorizes the payment, the frontend can send a post message to the service worker to proceed. You can resolve the promise passed to `PaymentRequestEvent.respondWith()` to send the result back to the merchant. Pass a [`PaymentHandlerResponse`](https://w3c.github.io/payment-handler/#dom-paymenthandlerresponse) object.

<table><thead><tr class="header"><th>Property name</th><th>Description</th></tr></thead><tbody><tr class="odd"><td><code>methodName</code></td><td>The payment method identifier used to make payment.</td></tr><tr class="even"><td><code>details</code></td><td>The payment method specific data that provides necessary information for the merchant to process payment. If <code>PaymentRequestEvent.paymentOptions.requestBillingAddress === true</code>, append the billing address as a <code>PaymentAddress</code> object as part of this.</td></tr><tr class="odd"><td><code>payerName</code></td><td>If <code>PaymentRequestEvent.paymentOptions.requestPayerName === true</code>, provide the payer's name.</td></tr><tr class="even"><td><code>payerEmail</code></td><td>If <code>PaymentRequestEvent.paymentOptions.requestPayerEmail === true</code>, provide the payer's email address.</td></tr><tr class="odd"><td><code>payerPhone</code></td><td>If <code>PaymentRequestEvent.paymentOptions.requestPayerPhone === true</code>, provide the payer's phone number.</td></tr><tr class="even"><td><code>shippingAddress</code></td><td>If <code>PaymentRequestEvent.paymentOptions.requestShipping === true</code>, provide the customer's shipping address with a <code>PaymentAddress</code> object.</td></tr><tr class="odd"><td><code>shippingOption</code></td><td>If <code>PaymentRequestEvent.paymentOptions.requestShipping</code>, provide the identifier of the customer's selected shipping option.</td></tr></tbody></table>

\[payment handler\] frontend:

      const paymentMethod = …
      const shippingOptionId = …
      const shippingAddress = …
      const contacts = …

      postMessage('PAYMENT_AUTHORIZED', {
        paymentMethod,              // Payment method identifier
        shippingOptionId,           // Shipping option id
        shippingAddress,            // shipping address object
        payerName: contacts.name,   // Payer name
        payerPhone: contacts.phone, // Payer Phone
        payerEmail: contacts.email, // Payer Email
      });

\[payment handler\] service-worker.js:

    …
    // Received a message from the frontend
    self.addEventListener('message', async e => {
      let details;
      try {
        switch (e.data.type) {
          …
          case 'PAYMENT_AUTHORIZED':
            // Resolve the payment request event promise
            // with a payment response object
            const response = {
              methodName: e.data.paymentMethod,
              details: { id: 'put payment credential here' },
            }
            let { paymentOptions } = payment_request_event;
            if (paymentOptions.requestBillingAddress) {
              response.details.billingAddress = e.data.methodData.billingAddress;
            }
            if (paymentOptions.requestShipping) {
              response.shippingAddress = e.data.shippingAddress;
              response.shippingOption = e.data.shippingOptionId;
            }
            if (paymentOptions.requestPayerEmail) {
              response.payerEmail = e.data.payerEmail;
            }
            if (paymentOptions.requestPayerName) {
              response.payerName = e.data.payerName;
            }
            if (paymentOptions.requestPayerPhone) {
              response.payerPhone = e.data.payerPhone;
            }
            resolver.resolve(response);
            // Don't forget to initialize.
            payment_request_event = null;
            break;
          …

Cancel the payment transaction <a href="#cancel-transaction" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------

To allow the customer to cancel the transaction, the frontend can send a post message to the service worker to do so. The service worker can then resolve the promise passed to `PaymentRequestEvent.respondWith()` with `null` to indicate to the merchant that the transaction has been cancelled.

\[payment handler\] frontend:

      postMessage('CANCEL_PAYMENT');

\[payment handler\] service-worker.js:

    …
    // Received a message from the frontend
    self.addEventListener('message', async e => {
      let details;
      try {
        switch (e.data.type) {
          …
          case 'CANCEL_PAYMENT':
            // Resolve the payment request event promise
            // with null
            resolver.resolve(null);
            // Don't forget to initialize.
            payment_request_event = null;
            break;
          …

Sample code <a href="#sample-code" class="w-headline-link">#</a>
----------------------------------------------------------------

All sample codes you saw in this document were excerpts from the following working sample app:

<https://paymenthandler-demo.glitch.me>

\[payment handler\] service worker

\[payment handler\] frontend

To try it out:

1.  Go to <https://paymentrequest-demo.glitch.me/>.
2.  Go to the bottom of the page.
3.  Press **Add a payment button**.
4.  Enter `https://paymenthandler-demo.glitch.me` to the **Payment Method Identifier** field.
5.  Press **Pay** button next to the field.

Next steps <a href="#next-steps" class="w-headline-link">#</a>
--------------------------------------------------------------

In this article, we learned how to orchestrate a payment transaction from a service worker. The next step is to learn how to add some more advanced features to the service worker.

-   [Handling optional payment information with a service worker](/handling-optional-payment-information)

<a href="/tags/payments/" class="w-chip">Payments</a> <a href="/tags/service-worker/" class="w-chip">Service Worker</a>

<span class="w-mr--sm">Last updated: Aug 31, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/payments/orchestrating-payment-transactions/index.md)

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
