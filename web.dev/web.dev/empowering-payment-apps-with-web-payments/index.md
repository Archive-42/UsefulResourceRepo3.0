## <a href="#empowering-payment-apps-with-web-payments" class="w-toc__header--link">Empowering payment apps with Web Payments</a>

- [What is Web Payments?](#what-is-web-payments)
- [Browser support](#browser-support)
- [The benefits of integrating Web Payments in a payment app](#the-benefits-of-integrating-web-payments-in-a-payment-app)
- [Better user experience](#better-user-experience)
- [Better developer experience](#better-developer-experience)
- [Stricter security](#stricter-security)
- [Comparing Web Payments to other approaches](#comparing-web-payments-to-other-approaches)
- [Integrating Web Payments in existing apps](#integrating-web-payments-in-existing-apps)
- [Platform-specific payment apps](#platform-specific-payment-apps)
- [Web based payment apps](#web-based-payment-apps)
- [How does merchant adoption work?](#how-does-merchant-adoption-work)
- [How much does it cost?](#how-much-does-it-cost)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Empowering payment apps with Web Payments

New web standards for frictionless payment experience on the web.

May 25, 2020 <span class="w-author__separator">•</span> Updated Jul 16, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/payments" class="w-post-signpost__link">Web Payments</a>

[<img src="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Eiji Kitamura" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/agektmr/)

<a href="/authors/agektmr/" class="w-author__name-link">Eiji Kitamura</a>

- <a href="https://twitter.com/agektmr" class="w-author__link">Twitter</a>
- <a href="https://github.com/agektmr" class="w-author__link">GitHub</a>
- <a href="https://blog.agektmr.com" class="w-author__link">Blog</a>

One of the key ecosystem drivers for the web are payments. With secure, seamless, and flexible payment systems, the web can become a sustainable and profitable platform. The Web Payments standards have the potential to be a key building block that will enable seamless integration of payment solutions into merchant checkout flows.

## What is Web Payments? <a href="#what-is-web-payments" class="w-headline-link">#</a>

Web Payments is a series of new standardized payment APIs available in modern browsers, including [Payment Request API](https://www.w3.org/TR/payment-request/), [Payment Handler API](https://www.w3.org/TR/payment-handler/) and [a few others](https://www.w3.org/Payments/WG/charter-201912.html#scope). These new browser primitives simplify online payments and enable payment apps to integrate with browsers easier than ever.

The standards are flexible; they work with various types of payment systems and are intended to work on any browser on any device, payment method, or payment service provider. This flexibility enables development simplicity, deployment consistency, and future compatibility with emerging payment technologies.

Research shows that [long checkout flows lead to cart abandonment](https://baymard.com/blog/checkout-flow-average-form-fields). With Web Payments, checkout flow is simplified to a few taps instead of manual entry of billing data for every purchase. See a demo below of how Google Pay leverages Web Payments to build a seamless flow. The same can be achieved by any other payment app:

Checkout flow with Google Pay and Web Payments..

1.  The customer goes to checkout and presses the **GPay** button.

2.  The Google Pay app launches _in front of the merchant website_.

3.  The customer confirms payment in the Google Pay app after examining the details.

4.  The merchant verifies the payment and the purchase is approved.

## Browser support <a href="#browser-support" class="w-headline-link">#</a>

Web Payments consists of a few different pieces of technologies and the support status depends on the browser.

<table><tbody><tr class="odd"><td></td><td>Chromium</td><td></td><td></td><td>Safari</td><td></td><td>Firefox</td></tr><tr class="even"><td></td><td>Desktop</td><td>Android</td><td>iOS</td><td>Desktop</td><td>Mobile</td><td></td></tr><tr class="odd"><td>Payment Request API</td><td>✔</td><td>✔</td><td></td><td>✔</td><td>✔</td><td>Under active development</td></tr><tr class="even"><td>Payment Handler API</td><td>✔</td><td>✔</td><td></td><td></td><td></td><td>Under active development</td></tr><tr class="odd"><td>iOS/Android payment app</td><td>✔</td><td>✔</td><td>*</td><td>✔**</td><td>✔**</td><td></td></tr></tbody></table>

\*Chrome is considering making built-in payment apps available on iOS.

\*\*Safari supports Apple Pay but no third party payment apps.

## The benefits of integrating Web Payments in a payment app <a href="#the-benefits-of-integrating-web-payments-in-a-payment-app" class="w-headline-link">#</a>

By integrating with Web Payments, payment apps can provide better user experience to customers, have better developer experience, and stricter security.

### Better user experience <a href="#better-user-experience" class="w-headline-link">#</a>

- **In-context payments:** Payments are made in [modals](https://material.io/components/sheets-bottom), in context of the merchant website, without redirects or pop-up windows.

- **Faster checkout**: Customers can save their payment details securely in their browser or a payment app, ready to be used on any supporting merchant site.

- **Streamlined purchase experience:** After completing (or aborting) the payment, the customer is on the merchant website exactly where they left off.

### Better developer experience <a href="#better-developer-experience" class="w-headline-link">#</a>

- **Easy integration:** Web Payments can be extended from an existing platform-specific payment app or a web-based payment app.

- **Low integration cost:** Merchants can integrate Web Payments with JavaScript and basic level server-side integration.

- **Standards:** The protocol and data format for exchanging information with merchants is standardized and doesn't require deep integration.

- **Dynamic price updates:** Merchants can dynamically change the shipping cost based on the shipping address selected in the payment app, without deep integration.

### Stricter security <a href="#stricter-security" class="w-headline-link">#</a>

- [Sideloading](https://en.wikipedia.org/wiki/Sideloading) prevention when invoking platform-specific payment apps.

- Designed with upcoming security and privacy paradigms in mind.

Using Web Payments also enables payment apps to bring any kind of payment method to the web such as e-money, cryptocurrency, bank transfers, and more. Web Payments is designed with sustainability in mind and doesn't put any restrictions on payment processing and payment methods.

## Comparing Web Payments to other approaches <a href="#comparing-web-payments-to-other-approaches" class="w-headline-link">#</a>

Consider the existing approaches to integrating payments on the web:

- **iframes:** Using JavaScript to inject the payment handler's website in an iframe and collect the customer's payment credential through a form.

- **Pop-ups:** Using JavaScript to open a pop-up window and collect the customer's payment credentials, either through a form or by having the customer authenticate and select a payment credential.

- **Redirects:** Merchant redirects the customer to a payment handler's website and lets the customer authenticate and select payment credentials. The redirect URL is communicated via a server.

- **OAuth:** Merchant lets the customer authenticate and authorize with a payment handler's identity via OAuth, select a payment method, shipping address etc through in-context iframe UI.

Here's how they compare to Web Payments:

<table><tbody><tr class="odd"><td></td><td>Web Payments</td><td>iframe</td><td>Popup</td><td>Redirect</td><td>OAuth</td></tr><tr class="even"><td>In-context payments</td><td>✔</td><td>✔</td><td></td><td>✔*</td><td>✔</td></tr><tr class="odd"><td>Dynamic price updates</td><td>✔</td><td></td><td></td><td></td><td>✔</td></tr><tr class="even"><td>Streamlined purchase experience</td><td>✔</td><td>✔</td><td></td><td></td><td>✔</td></tr><tr class="odd"><td>Platform-specific app integration</td><td>✔</td><td></td><td></td><td>✔</td><td></td></tr><tr class="even"><td>Low integration cost</td><td>✔</td><td>✔</td><td>✔</td><td>✔</td><td></td></tr><tr class="odd"><td>Standards</td><td>✔</td><td></td><td></td><td></td><td></td></tr></tbody></table>

\*Redirecting to a platform-specific payment app can be done in-context with the merchant website though redirecting to another website completely loses the context.

## Integrating Web Payments in existing apps <a href="#integrating-web-payments-in-existing-apps" class="w-headline-link">#</a>

You can integrate Web Payments in both platform-specific and web-based payment apps: if the platform-specific payment app is not installed, the web-based payment app can be used as a fallback. Customers and merchants can seamlessly send and receive payments through a payment method of their choice, depending on the environment.

### Platform-specific payment apps <a href="#platform-specific-payment-apps" class="w-headline-link">#</a>

- Ideal for payment apps that already have a large install base and want to give existing users a consistent experience on the web.

- Unlike [Android's "Intent" feature](https://developer.android.com/guide/components/intents-filters), Web Payments performs signature verification before running the payment app which makes malicious payment apps impossible to be sideloaded.

In the video above, Google Pay is a platform-specific payment app.

### Web based payment apps <a href="#web-based-payment-apps" class="w-headline-link">#</a>

- More future proof: typical payment app techniques like redirects or pop-ups are based on third party cookies [that may become obsolete](https://blog.chromium.org/2020/01/building-more-private-web-path-towards.html). While it's still hard to foresee the consequences, Web Payments look to the web with better privacy and a world without third party cookies.

- The web-based route is ideal for web services that have a large number of customers with their card on file.

Checkout flow with a web-based payment app.

## How does merchant adoption work? <a href="#how-does-merchant-adoption-work" class="w-headline-link">#</a>

For a payment app to be available on a merchant, the merchant needs to explicitly adopt it. Technically speaking, the merchant has to specify the payment app's identifier (payment method identifier) and use the Payment Request API with it.

We suggest that you provide good documentation in integration guides and SDKs or libraries to facilitate integration. For example, Google Pay provides [a developer's guide](https://developers.google.com/pay/api/web/overview).

Working with payment gateways is also a good option as they can help scale your outreach as well.

## How much does it cost? <a href="#how-much-does-it-cost" class="w-headline-link">#</a>

Web Payments is all about standard technology in the browser. Payment apps adopting it nor activating it on the browser won't charge them any fees by itself.

<a href="/tags/payments/" class="w-chip">Payments</a>

<span class="w-mr--sm">Last updated: Jul 16, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/payments/empowering-payment-apps-with-web-payments/index.md)

<a href="/blog" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
