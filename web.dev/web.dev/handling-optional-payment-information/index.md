<span class="w-tooltip w-tooltip--left">Open menu</span>

<a href="/" class="gc-analytics-event header-default__logo-link"><img src="/images/lockup.svg" alt="web.dev" class="header-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event header-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event header-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event header-default__link">Blog</a> <a href="/about/" class="gc-analytics-event header-default__link">About</a>

<span class="w-tooltip">Close</span>

<a href="/" class="gc-analytics-event"><img src="/images/lockup.svg" alt="web.dev" class="drawer-default__logo" width="125" height="30" /></a>

<a href="/learn/" class="gc-analytics-event drawer-default__link">Learn</a> <a href="/measure/" class="gc-analytics-event drawer-default__link">Measure</a> <a href="/blog/" class="gc-analytics-event drawer-default__link">Blog</a> <a href="/about/" class="gc-analytics-event drawer-default__link">About</a>

<a href="#handling-optional-payment-information-with-a-service-worker" class="w-toc__header--link">Handling optional payment information with a service worker</a>
------------------------------------------------------------------------------------------------------------------------------------------------------------------

-   [Inform the merchant of a payment method change](#payment-method-changes)
-   [Inform the merchant of a shipping address change](#shipping-address-changes)
-   [Inform the merchant of a shipping option change](#inform-the-merchant-of-a-shipping-option-change)
-   [Reflect the updated payment details](#reflect-the-updated-payment-details)
-   [Sample code](#sample-code)
-   [Next steps](#next-steps)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

Handling optional payment information with a service worker
===========================================================

How to adapt your web-based payment app to Web Payments and provide a better user experience for customers.

Aug 31, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/payments" class="w-post-signpost__link">Web Payments</a>

[<img src="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Eiji Kitamura" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/agektmr/)

<a href="/authors/agektmr/" class="w-author__name-link">Eiji Kitamura</a>

-   <a href="https://twitter.com/agektmr" class="w-author__link">Twitter</a>
-   <a href="https://github.com/agektmr" class="w-author__link">GitHub</a>
-   <a href="https://blog.agektmr.com" class="w-author__link">Blog</a>

Once [a web-based payment app receives a payment request and initiates a payment transaction](/orchestrating-payment-transactions), the service worker will act as the hub for communication between the merchant and the payment app. This post explains how a payment app can pass information about the payment method, shipping address, or contact information to the merchant using a service worker.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format" alt="Handling optional payment information with a service worker" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/kDteyNFNEVnJQyTPw5p8.png?auto=format&amp;w=1600 1600w" width="800" height="2335" /><figcaption>Handling optional payment information with a service worker</figcaption></figure>Inform the merchant of a payment method change <a href="#payment-method-changes" class="w-headline-link">#</a>
--------------------------------------------------------------------------------------------------------------

Payment apps can support multiple payment instruments with different payment methods.

Customer

Payment Method

Payment Instrument

A

Credit Card Issuer 1

`****1234`

Credit Card Issuer 1

`****4242`

Bank X

`******123`

B

Credit Card Issuer 2

`****5678`

Bank X

`******456`

For example, in the above table, Customer A's web-based wallet has two credit cards and one bank account registered. In this case, the app is handling three payment instruments (`****1234`, `****4242`, `******123`) and two payment methods (Credit Card Issuer 1 and Bank X). On a payment transaction, the payment app can let the customer pick one of the payment instruments and use it to pay for the merchant.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format" alt="Payment method picker UI" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/yZYmEL3y1e2cPaLNz34K.png?auto=format&amp;w=1600 1600w" width="800" height="1600" /><figcaption>Payment method picker UI</figcaption></figure>The payment app can let the merchant know which payment method the customer picked before sending the full payment response. This is useful when the merchant wants to run a discount campaign for a specific payment method brand, for example.

With the Payment Handler API, the payment app can send a "payment method change" event to the merchant via a service worker to notify the new payment method identifier. The service worker should invoke `PaymentRequestEvent.changePaymentMethod()` with the new payment method information.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format" alt="Inform the merchant of a payment method change" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/ogXzkcdinU3RNC9cMzN0.png?auto=format&amp;w=1600 1600w" width="800" height="659" /><figcaption>Inform the merchant of a payment method change</figcaption></figure>Payment apps can pass a `methodDetails` object as the optional second argument for `PaymentRequestEvent.changePaymentMethod()`. This object can contain arbitrary payment method details required for the merchant to process the change event.

**Warning**: Sharing detailed information about a customer with the merchant before the transaction is finalized is potentially a privacy risk. As a best practice, payment apps should omit unnecessary details as much as possible.

\[payment handler\] service-worker.js

    …
    // Received a message from the frontend
    self.addEventListener('message', async e => {
      let details;
      try {
        switch (e.data.type) {
          …
          case 'PAYMENT_METHOD_CHANGED':
            const newMethod = e.data.paymentMethod;
            const newDetails = e.data.methodDetails;
            // Redact or check that no sensitive information is passed in
            // `newDetails`.
            // Notify the merchant of the payment method change
            details =
              await payment_request_event.changePaymentMethod(newMethod, newDetails);
          …

When the merchant receives a `paymentmethodchange` event from the Payment Request API, they can update the payment details and respond with a [`PaymentDetailsUpdate`](https://w3c.github.io/payment-request/#paymentdetailsupdate-dictionary) object.

\[merchant\]

    request.addEventListener('paymentmethodchange', e => {
      if (e.methodName === 'another-pay') {
        // Apply $10 discount for example.
        const discount = {
          label: 'special discount',
          amount: {
            currency: 'USD',
            // The value being string complies the spec
            value: '-10.00'
          }
        };
        let total = 0;
        details.displayItems.push(discount);
        for (let item of details.displayItems) {
         total += parseFloat(item.amount.value);
        }
        // Convert the number back to string
        details.total.amount.value = total.toString();
      }
      // Pass a promise to `updateWith()` and send updated payment details
      e.updateWith(details);
    });

When the merchant responds, the promise that [`PaymentRequestEvent.changePaymentMethod()`](https://w3c.github.io/payment-handler/#dom-paymentrequestevent-changepaymentmethod) returned will resolve with a [`PaymentRequestDetailsUpdate`](https://w3c.github.io/payment-handler/#the-paymentrequestdetailsupdate) object.

\[payment handler\] service-worker.js

    …
            // Notify the merchant of the payment method change
            details = await payment_request_event.changePaymentMethod(newMethod, newDetails);
            // Provided the new payment details,
            // send a message back to the frontend to update the UI
            postMessage('UPDATE_REQUEST', details);
            break;
    …

Use the object to update the UI on the frontend. See [Reflect the updated payment details](#reflect-the-updated-payment-details).

Inform the merchant of a shipping address change <a href="#shipping-address-changes" class="w-headline-link">#</a>
------------------------------------------------------------------------------------------------------------------

Payment apps can provide the customer's shipping address to the merchant as part of the result of a payment transaction.

This is useful for merchants because they can delegate the address collection to payment apps. And, because the address data will be provided in [the standard data format](https://w3c.github.io/payment-request/#dom-addressinit), the merchant can expect to receive shipping addresses in consistent structure.

This is beneficial for customers as well because once they register their address information to their favorite payment app, they can reuse it in different shops.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format" alt="Shipping address picker UI" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/0ytdyaEC7tkPkBTv5rIu.png?auto=format&amp;w=1600 1600w" width="800" height="1600" /><figcaption>Shipping address picker UI</figcaption></figure>Payment apps can provide a UI to edit a shipping address or to select pre-registered address information for the customer on a payment transaction. When a shipping address is determined temporarily, the payment app can let the merchant know of the redacted address information. This provides merchants with multiple benefits:

-   A merchant can determine whether the customer meets the regional restriction to ship the item (for example, domestic only).
-   A merchant can change the list of shipping options based on the region of the shipping address (For example, international regular or express).
-   A merchant can apply the new shipping cost based on the address and update the total price.

With the Payment Handler API, the payment app can send a "shipping address change" event to the merchant from the service worker to notify the new shipping address. The service worker should invoke [`PaymentRequestEvent.changeShippingAddress()`](https://w3c.github.io/payment-handler/#dom-paymentrequestevent-changeshippingaddress) with the [new address object](https://www.w3.org/TR/payment-request/#dom-addressinit).

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format" alt="Inform the merchant of a shipping address change" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/aVv5d9OEcEjH1Z6nUQKb.png?auto=format&amp;w=1600 1600w" width="800" height="675" /><figcaption>Inform the merchant of a shipping address change</figcaption></figure>\[payment handler\] service-worker.js

    ...
    // Received a message from the frontend
    self.addEventListener('message', async e => {
      let details;
      try {
        switch (e.data.type) {
          …
          case 'SHIPPING_ADDRESS_CHANGED':
            const newAddress = e.data.shippingAddress;
            details =
              await payment_request_event.changeShippingAddress(newAddress);
          …

**Key Term**: **Redacted address**. Informing the full shipping address to the merchant in this case is not necessary and risks customers' privacy. The merchant only receives the parts of the address that they need to determine the shipping cost. Specifically, the browser will clear the `organization`, `phone`, `recipient`, `addressLine` fields from the payment app provided address before raising the `shippingaddresschange` event in the merchant's DOM.

The merchant will receive a `shippingaddresschange` event from the Payment Request API so they can respond with the updated [`PaymentDetailsUpdate`](https://w3c.github.io/payment-request/#paymentdetailsupdate-dictionary).

\[merchant\]

    request.addEventListener('shippingaddresschange', e => {
      // Read the updated shipping address and update the request.
      const addr = request.shippingAddress;
      const details = getPaymentDetailsFromShippingAddress(addr);
      // `updateWith()` sends back updated payment details
      e.updateWith(details);
    });

When the merchant responds, the promise [`PaymentRequestEvent.changeShippingAddress()`](https://w3c.github.io/payment-handler/#dom-paymentrequestevent-changeshippingaddress) returned will resolve with a [`PaymentRequestDetailsUpdate`](https://w3c.github.io/payment-handler/#the-paymentrequestdetailsupdate) object.

\[payment handler\] service-worker.js

    …
            // Notify the merchant of the shipping address change
            details = await payment_request_event.changeShippingAddress(newAddress);
            // Provided the new payment details,
            // send a message back to the frontend to update the UI
            postMessage('UPDATE_REQUEST', details);
            break;
    …

Use the object to update the UI on the frontend. See [Reflect the updated payment details](#reflect-the-updated-payment-details).

Inform the merchant of a shipping option change <a href="#inform-the-merchant-of-a-shipping-option-change" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------------------------------

Shipping options are delivery methods merchants use to ship purchased items to a customer. Typical shipping options include:

-   Free shipping
-   Express shipping
-   International shipping
-   Premium international shipping

Each comes with its own cost. Usually faster methods/options are more expensive.

Merchants using the Payment Request API can delegate this selection to a payment app. The payment app can use the information to construct a UI and let the customer pick a shipping option.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format" alt="Shipping option picker UI" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/VkHwTharTqX7oFK62RkA.png?auto=format&amp;w=1600 1600w" width="800" height="1600" /><figcaption>Shipping option picker UI</figcaption></figure>The list of shipping options specified in the merchant's Payment Request API is propagated to the payment app's service worker as a property of `PaymentRequestEvent`.

\[merchant\]

    const request = new PaymentRequest([{
      supportedMethods: 'https://bobpay.xyz/pay',
      data: { transactionId: '****' }
    }], {
      displayItems: [{
        label: 'Anvil L/S Crew Neck - Grey M x1',
        amount: { currency: 'USD', value: '22.15' }
      }],
      shippingOptions: [{
        id: 'standard',
        label: 'Standard',
        amount: { value: '0.00', currency: 'USD' },
        selected: true
      }, {
        id: 'express',
        label: 'Express',
        amount: { value: '5.00', currency: 'USD' }
      }],
      total: {
        label: 'Total due',
        amount: { currency: 'USD', value : '22.15' }
      }
    }, {  requestShipping: true });

The payment app can let the merchant know which shipping option the customer picked. This is important for both the merchant and the customer because changing the shipping option changes the total price as well. The merchant needs to be informed of the latest price for the payment verification later and the customer also needs to be aware of the change.

With the Payment Handler API, the payment app can send a "shipping option change" event to the merchant from the service worker. The service worker should invoke [`PaymentRequestEvent.changeShippingOption()`](https://w3c.github.io/payment-handler/#dom-paymentrequestevent-changeshippingoption) with the new shipping option ID.

<figure><img src="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format" alt="Inform the merchant of a shipping option change" class="w-screenshot" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/tcFciHGuF3MxnTr1y5ue01OGLBn2/mERzHqvPGrjKWu29m5q1.png?auto=format&amp;w=1600 1600w" width="800" height="667" /><figcaption>Inform the merchant of a shipping option change</figcaption></figure>\[payment handler\] service-worker.js

    …
    // Received a message from the frontend
    self.addEventListener('message', async e => {
      let details;
      try {
        switch (e.data.type) {
          …
          case 'SHIPPING_OPTION_CHANGED':
            const newOption = e.data.shippingOptionId;
            details =
              await payment_request_event.changeShippingOption(newOption);
          …

The merchant will receive a `shippingoptionchange` event from the Payment Request API. The merchant should use the information to update the total price and then respond with the updated [`PaymentDetailsUpdate`](https://w3c.github.io/payment-request/#paymentdetailsupdate-dictionary).

\[merchant\]

    request.addEventListener('shippingoptionchange', e => {
      // selected shipping option
      const shippingOption = request.shippingOption;
      const newTotal = {
        currency: 'USD',
        label: 'Total due',
        value: calculateNewTotal(shippingOption),
      };
      // `updateWith()` sends back updated payment details
      e.updateWith({ total: newTotal });
    });

When the merchant responds, the promise that [`PaymentRequestEvent.changeShippingOption()`](https://w3c.github.io/payment-handler/#dom-paymentrequestevent-changeshippingoption) returned will resolve with a [`PaymentRequestDetailsUpdate`](https://w3c.github.io/payment-handler/#the-paymentrequestdetailsupdate) object.

\[payment handler\] service-worker.js

    …
            // Notify the merchant of the shipping option change
            details = await payment_request_event.changeShippingOption(newOption);
            // Provided the new payment details,
            // send a message back to the frontend to update the UI
            postMessage('UPDATE_REQUEST', details);
            break;
    …

Use the object to update the UI on the frontend. See [Reflect the updated payment details](#reflect-the-updated-payment-details).

Reflect the updated payment details <a href="#reflect-the-updated-payment-details" class="w-headline-link">#</a>
----------------------------------------------------------------------------------------------------------------

Once the merchant finishes updating the payment details, the promises returned from `.changePaymentMethod()`, `.changeShippingAddress()` and `.changeShippingOption()` will resolve with a common [`PaymentRequestDetailsUpdate`](https://w3c.github.io/payment-handler/#the-paymentrequestdetailsupdate) object. The payment handler can use the result to reflect updated total price and shipping options to the UI.

The `PaymentRequestDetailsUpdate` object is passed from the merchant and it contains the exact information the merchant put in the `PaymentDetailsUpdate` object via the Payment Request API. The best way to ensure that merchants give you the information you expect is to provide good developer documentation, or provide a JavaScript library to control the information, or both.

Merchants may return errors for a few reasons:

-   The payment method is not acceptable.
-   The shipping address is outside of their supported regions.
-   The shipping address contains invalid information.
-   The shipping option is not selectable for the provided shipping address or some other reason.

Use the following properties to reflect the error status:

-   **`error`**: Human readable error string. This is the best string to display to customers.
-   **`shippingAddressErrors`**: [`AddressErrors`](https://www.w3.org/TR/payment-request/#dom-addresserrors) object that contains in-detail error string per address property. This is useful if you want to open a form that lets the customer edit their address and you need to point them directly to the invalid fields.
-   **`paymentMethodErrors`**: Payment-method-specific error object. You can ask merchants to provide a structured error like [`BasicCardErrors`](https://www.w3.org/TR/payment-method-basic-card/#dom-basiccarderrors) for basic-card, but the Web Payments spec authors recommend keeping it a simple string.

Sample code <a href="#sample-code" class="w-headline-link">#</a>
----------------------------------------------------------------

Most of sample codes you saw in this document were excerpts from the following working sample app:

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

In this article, we learned how to handle optional information on the service worker. The final step for building a web-based payment app is to learn how to build the frontend.

-   Handling payments on the payment frontend (coming soon)

<a href="/tags/payments/" class="w-chip">Payments</a> <a href="/tags/service-worker/" class="w-chip">Service Worker</a>

<span class="w-mr--sm">Last updated: Aug 31, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/payments/handling-optional-payment-information/index.md)

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
