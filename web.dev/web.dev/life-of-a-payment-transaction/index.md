<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#life-of-a-payment-transaction" class="w-toc__header--link">Life of a payment transaction</a>
------------------------------------------------------------------------------------------------------

-   [Step 1: The merchant initiates a payment transaction](#step-1:-the-merchant-initiates-a-payment-transaction)
-   [Step 2: The merchant shows a payment button](#step-2:-the-merchant-shows-a-payment-button)
-   [Does the customer have the payment app available?](#does-the-customer-have-the-payment-app-available)
-   [Step 3: The customer presses the payment button](#show)
-   [Deferring the launch of the payment UI](#deferring-the-launch-of-the-payment-ui)
-   [Step 4: The browser launches the payment app](#launch)
-   [Step 5: How a merchant can update the transaction details depending on customer's actions](#step-5:-how-a-merchant-can-update-the-transaction-details-depending-on-customer's-actions)
-   [Payment method change event](#payment-method-change-event)
-   [Shipping address change event](#shipping-address-change-event)
-   [Shipping option change event](#shipping-option-change-event)
-   [Merchant validation event](#merchant-validation-event)
-   [Step 6: The merchant validates the payment and completes the transaction](#step-6:-the-merchant-validates-the-payment-and-completes-the-transaction)
-   [Processing and validating the payment](#processing-and-validating-the-payment)
-   [Completing or retrying the transaction](#completing-or-retrying-the-transaction)
-   [Next Steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Life of a payment transaction
=============================

Learn how merchants integrate payment apps and how payment transactions work  
with the Payment Request API.

May 25, 2020 <span class="w-author__separator">•</span> Updated Jul 17, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/payments" class="w-post-signpost__link">Web Payments</a>

[<img src="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Eiji Kitamura" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/agektmr/)

<a href="/authors/agektmr/" class="w-author__name-link">Eiji Kitamura</a>

-   <a href="https://twitter.com/agektmr" class="w-author__link">Twitter</a>
-   <a href="https://github.com/agektmr" class="w-author__link">GitHub</a>
-   <a href="https://blog.agektmr.com" class="w-author__link">Blog</a>

[<img src="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Milica Mihajlija" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/WkMOiDtaDgiAA2YkRZ5H.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/mihajlija/)

<a href="/authors/mihajlija/" class="w-author__name-link">Milica Mihajlija</a>

-   <a href="https://twitter.com/bibydigital" class="w-author__link">Twitter</a>
-   <a href="https://github.com/mihajlija" class="w-author__link">GitHub</a>
-   <a href="https://mihajlija.github.io/" class="w-author__link">Blog</a>

Web Payments APIs are dedicated payment features built into the browser for the first time. With Web Payments, merchant integration with payment apps becomes simpler while the customer experience gets streamlined and more secure.

To learn more about the benefits of using Web Payments check out [Empowering payment apps with Web Payments](/empowering-payment-apps-with-web-payments).

This article walks you through a payment transaction on a merchant website and helps you understand how payment app integration works.

The process involves 6 steps:

1.  The merchant initiates a payment transaction.

2.  The merchant shows a payment button.

3.  The customer presses the payment button.

    <img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/NQIh5tt5wsQFC5yKLCaU.svg" alt="A diagram of a cheese shop website with a BobPay (payment app) button." width="786" height="298" />

4.  The browser launches the payment app.

    <img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/IHztIcfJKeWDUIkugTkb.svg" alt="A diagram of the cheese shop website with BobPay app launched in a modal. The modal shows shipping options and total cost." width="671" height="366" />

5.  If the customer changes any details (such as shipping options or their address), the merchant updates the transaction details reflecting the change.

    <img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/BR9Od63aOdG9CaaD1z7K.svg" alt="A diagram showing the customer choosing a different shipping option in BobPay app modal. A second diagram showing the merchant updating the total cost displayed in BobPay." width="777" height="702" />

6.  After the customer confirms the purchase, the merchant validates the payment and completes the transaction.

    <img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/9Q6VqimbOxJ3ZXHvB8ry.svg" alt="A diagram showing the customer pressing the &quot;Pay&quot; button in BobPay, followed by a diagram of the cheese shop page showing &quot;Payment accepted&quot;." width="778" height="708" />

Step 1: The merchant initiates a payment transaction <a href="#step-1:-the-merchant-initiates-a-payment-transaction" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------------

When a customer decides to make a purchase, the merchant initiates the payment transaction by constructing a [`PaymentRequest`](https://developers.google.com/web/fundamentals/payments/basics/how-payment-request-api-works) object. This object includes important information about the transaction:

-   Acceptable payment methods and their data to process the transaction.
-   Details, such as the total price (required) and information about the items.
-   Options in which merchants can request shipping information such as a shipping address and a shipping option.
-   Merchants can also request the billing address, the payer's name, email, and phone number.
-   Merchants can also include optional [shipping type](https://developers.google.com/web/fundamentals/payments/merchant-guide/deep-dive-into-payment-request#changing_the_shipping_type) (`shipping`, `delivery`, or `pickup`) in the `PaymentRequest`. The payment app can use that as a hint to display the correct labels in its UI.

<!-- -->

    const request = new PaymentRequest([{
      supportedMethods: 'https://bobpay.xyz/pay',
      data: {
        transactionId: '****'
      }
    }], {
      displayItems: [{
        label: 'Anvil L/S Crew Neck - Grey M x1',
        amount: { currency: 'USD', value: '22.15' }
      }],
      total: {
        label: 'Total due',
        amount: { currency: 'USD', value : '22.15' }
      }
    }, {
      requestShipping: true,
      requestBillingAddress: true,
      requestPayerEmail: true,
      requestPayerPhone: true,
      requestPayerName: true,
      shippingType: 'delivery'
    });

Including a transaction ID
--------------------------

Some payment handlers may require the merchant to provide the transaction ID which they have issued in advance as part of the transaction information. A typical integration includes communication between the merchant's and the payment handler's server to reserve the total price. This prevents malicious customers from manipulating the price and cheating the merchant with a validation at the end of the transaction.

The merchant can pass a transaction ID as part of the [`PaymentMethodData`](https://www.w3.org/TR/payment-request/#dom-paymentmethoddata) object's `data` property.

Provided the transaction information, the browser goes through a discovery process of payment apps specified in the `PaymentRequest` based on the payment method identifiers. This way, the browser can determine the payment app to launch as soon as the merchant is ready to proceed with the transaction.

To learn how the discovery process works in detail check out [Setting up a payment method](/setting-up-a-payment-method#how-a-browser-discovers-a-payment-app).

Step 2: The merchant shows a payment button <a href="#step-2:-the-merchant-shows-a-payment-button" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------

Merchants can support many payment methods, but should only present the payment buttons for those that a customer can actually use. Showing a payment button that is unusable is poor user experience. If a merchant can predict that a payment method specified in the `PaymentRequest` object won't work for the customer, they can provide a fallback solution or not show that button at all.

Using a `PaymentRequest` instance, a merchant can query whether a customer has the payment app available.

### Does the customer have the payment app available? <a href="#does-the-customer-have-the-payment-app-available" class="w-headline-link">#</a>

The [`canMakePayment()`](https://developer.mozilla.org/docs/Web/API/PaymentRequest/canMakePayment) method of `PaymentRequest` returns `true` if a payment app is available on the customer's device. "Available" means that a payment app that supports the payment method is discovered, and that the platform-specific payment app is installed, or the web-based payment app is [ready to be registered](/setting-up-a-payment-method#jit-register).

    const canMakePayment = await request.canMakePayment();
    if (!canMakePayment) {
      // Fallback to other means of payment or hide the button.
    }

Step 3: The customer presses the payment button <a href="#show" class="w-headline-link">#</a>
---------------------------------------------------------------------------------------------

When the customer presses the payment button, the merchant calls the `show()` method of the `PaymentRequest` instance which immediately triggers the launch of the payment UI.

In case the final total price is set dynamically (for example, retrieved from a server), the merchant can defer the launch of the payment UI until the total is known.

### Deferring the launch of the payment UI <a href="#deferring-the-launch-of-the-payment-ui" class="w-headline-link">#</a>

Check out a demo of [deferring the payment UI](https://rsolomakhin.github.io/pr/wait/) until the final total price is determined.

To defer the payment UI, the merchant passes a promise to the `show()` method. The browser will show a loading indicator until the promise resolves and the transaction is ready to begin.

    const getTotalAmount = async () => {
      // Fetch the total amount from the server, etc.
    };

    try {
      const result = await request.show(getTotalAmount());
      // Process the result…
    } catch(e) {
      handleError(e);
    }

If there is no promise specified as an argument for `show()`, the browser will launch the payment UI immediately.

If the payment handler is designed to return a transaction ID upon setting the total price, the ID can be passed as part of the promise result.

Step 4: The browser launches the payment app <a href="#launch" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------

The browser can launch a platform-specific or a web-based payment app. (You can learn more about [how Chrome determines which payment app to launch](/setting-up-a-payment-method#how-chrome-determines-which-payment-app-to-launch).)

How the payment app is built is up to the developer for the most part, but the events emitted from and to the merchant, as well as the structure of the data passed along with those events, are standardized.

When the payment app is launched, it receives [the transaction information](https://w3c.github.io/payment-handler/#the-paymentrequestevent) passed to the `PaymentRequest` object in Step 1, which includes the following:

-   Payment method data
-   Total price
-   Payment options

The payment app uses the transaction information to label its UI.

Step 5: How a merchant can update the transaction details depending on customer's actions <a href="#step-5:-how-a-merchant-can-update-the-transaction-details-depending-on-customer&#39;s-actions" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

Customers have an option to change the transaction details such as payment method and shipping option in the payment app. While the customer makes changes, the merchant receives the change events and updates the transaction details.

There are four types of events a merchant can receive:

-   Payment method change event
-   Shipping address change event
-   Shipping option change event
-   Merchant validation event

### Payment method change event <a href="#payment-method-change-event" class="w-headline-link">#</a>

A payment app can support multiple payment methods and a merchant may offer a special discount depending on the customer's selection. To cover this use case, the payment method change event can inform the merchant of the new payment method so that they can update the total price with the discount and return it back to the payment app.

    request.addEventListener('paymentmethodchange', e => {
      e.updateWith({
        // Add discount etc.
      });
    });

### Shipping address change event <a href="#shipping-address-change-event" class="w-headline-link">#</a>

A payment app can optionally provide the customer's shipping address. This is convenient for customers because they don't have to manually enter any details into a form and they can store their shipping address in their prefered payment apps, rather than on multiple different merchant websites.

If a customer updates their shipping address in a payment app after the transaction has been initiated, a shipping address change event will be emitted to the merchant. This helps the merchant determine the shipping cost based on the new address, update the total price, and return it back to the payment app.

    request.addEventListener('shippingaddresschange', e => {
      e.updateWith({
        // Update the details
      });
    });

If the merchant can't ship to the updated address, they can provide an error message by adding an error parameter to the transaction details returned to the payment app.

Merchants don't receive customers' full shipping address until they've authorized the payment.

### Shipping option change event <a href="#shipping-option-change-event" class="w-headline-link">#</a>

A merchant can offer multiple shipping options to the customer and can delegate that choice to the payment app. The shipping options are displayed as a list of prices and service names the customer can select from. For example:

-   Standard shipping - Free
-   Express shipping - $5

When a customer updates the shipping option in a payment app, a shipping option change event will be emitted to the merchant. The merchant can then determine the shipping cost, update the total price, and return it back to the payment app.

    request.addEventListener('shippingoptionchange', e => {
      e.updateWith({
        // Update the details
      });
    });

The merchant can modify the shipping options dynamically based on the customer's shipping address as well. This is useful when a merchant wants to offer different sets of shipping options for domestic and international customers.

### Merchant validation event <a href="#merchant-validation-event" class="w-headline-link">#</a>

For additional security, a payment app can perform a merchant validation before proceeding to the payment flow. The design of the validation mechanism is up to the payment app, but the merchant validation event serves to inform the merchant of the URL they can use to validate themselves.

    request.addEventListener('merchantvalidation', e => {
      e.updateWith({
        // Use `e.validateURL` to validate
      });
    });

The support for the merchant validation event is limited to Apple Safari. Chromium-based browsers have not implemented this event as of May 2020.

Step 6: The merchant validates the payment and completes the transaction <a href="#step-6:-the-merchant-validates-the-payment-and-completes-the-transaction" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

When the customer successfully authorizes the payment, the `show()` method returns a promise that resolves to a [`PaymentResponse`](https://w3c.github.io/payment-request/#paymentresponse-interface). The `PaymentResponse` object includes the following information:

-   Payment result details
-   Shipping address
-   Shipping option
-   Contact information

At this point, the browser UI may still show a loading indicator meaning that the transaction is not completed yet.

If the payment app is terminated because of a payment failure or error, the promise returned from `show()` rejects, and the browser terminates the payment transaction.

### Processing and validating the payment <a href="#processing-and-validating-the-payment" class="w-headline-link">#</a>

The `details` in `PaymentResponse` is the payment credential object returned from the payment app. The merchant can use the credential to process or validate the payment. How this critical process works is up to the payment handler.

### Completing or retrying the transaction <a href="#completing-or-retrying-the-transaction" class="w-headline-link">#</a>

After the merchant determines whether the transaction has succeded or failed, they can either:

-   Call the `.complete()` method to complete the transaction and dismiss the loading indicator.
-   Let the customer retry by calling the `retry()` method.

<!-- -->

    async function doPaymentRequest() {
      try {
        const request = new PaymentRequest(methodData, details, options);
        const response = await request.show();
        await validateResponse(response);
      } catch (err) {
        // AbortError, SecurityError
        console.error(err);
      }
    }

    async function validateResponse(response) {
      try {
        const errors = await checkAllValuesAreGood(response);
        if (errors.length) {
          await response.retry(errors);
          return validateResponse(response);
        }
        await response.complete("success");
      } catch (err) {
        // Something went wrong…
        await response.complete("fail");
      }
    }
    // Must be called as a result of a click
    // or some explicit user action.
    doPaymentRequest();

Next Steps <a href="#next-steps" class="w-headline-link">#</a>
--------------------------------------------------------------

-   Learn how to declare a payment method identifier in detail in [Setting up a payment method](/setting-up-a-payment-method).
-   Learn how to build a platform-specific payment app in [Android payment apps developer's guide](/android-payment-apps-developers-guide).
-   Learn how to build a web-based payment app in [Web-based payment apps developer's guide](/web-based-payment-apps-overview).

<a href="/tags/payments/" class="w-chip">Payments</a>

<span class="w-mr--sm">Last updated: Jul 17, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/payments/life-of-a-payment-transaction/index.md)

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
