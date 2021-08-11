## <a href="#android-payment-app-developers-guide" class="w-toc__header--link">Android payment app developers guide</a>

- [Step 1: Let merchants discover your payment app](#step-1:-let-merchants-discover-your-payment-app)
- [Step 2: Let a merchant know if a customer has an enrolled instrument that is ready to pay](#step-2:-let-a-merchant-know-if-a-customer-has-an-enrolled-instrument-that-is-ready-to-pay)
- [AndroidManifest.xml](#androidmanifest.xml)
- [AIDL](#aidl)
- [Implementing IsReadyToPayService](#implementing-isreadytopayservice)
- [Parameters](#parameters)
- [Response](#response)
- [Permission](#permission)
- [Step 3: Let a customer make payment](#step-3:-let-a-customer-make-payment)
- [AndroidManifest.xml](#androidmanifest.xml-2)
- [Parameters](#parameters-2)
- [Response](#response-2)
- [Permission](#permission-2)
- [Step 4: Verify the caller's signing certificate](#step-4:-verify-the-caller's-signing-certificate)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# Android payment app developers guide

Learn how to adapt your Android payment app to work with Web Payments and provide a better user experience for customers.

May 25, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/payments" class="w-post-signpost__link">Web Payments</a>

[<img src="https://web-dev.imgix.net/image/admin/IjxUTn7SuYE9pHLSZteN.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Yuichi Araki" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/IjxUTn7SuYE9pHLSZteN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/IjxUTn7SuYE9pHLSZteN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/IjxUTn7SuYE9pHLSZteN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/IjxUTn7SuYE9pHLSZteN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/IjxUTn7SuYE9pHLSZteN.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/yaraki/)

<a href="/authors/yaraki/" class="w-author__name-link">Yuichi Araki</a>

- <a href="https://twitter.com/yuichi_araki" class="w-author__link">Twitter</a>
- <a href="https://github.com/yaraki" class="w-author__link">GitHub</a>

[<img src="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Eiji Kitamura" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/Mh9DRmQhjlroJM9JDqsu.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/agektmr/)

<a href="/authors/agektmr/" class="w-author__name-link">Eiji Kitamura</a>

- <a href="https://twitter.com/agektmr" class="w-author__link">Twitter</a>
- <a href="https://github.com/agektmr" class="w-author__link">GitHub</a>
- <a href="https://blog.agektmr.com" class="w-author__link">Blog</a>

The [Payment Request API](https://www.w3.org/TR/payment-request/) brings to the web a built-in browser-based interface that allows users to enter required payment information easier than ever before. The API can also invoke platform-specific payment apps.

Checkout flow with platform-specific Google Pay app that uses Web Payments.

Compared to using just Android Intents, Web Payments allow better integration with the browser, security, and user experience:

- The payment app is launched as a modal, in context of the merchant website.
- Implementation is supplemental to your existing payment app, enabling you to take advantage of your user base.
- The payment app's signature is checked to prevent [sideloading](https://en.wikipedia.org/wiki/Sideloading).
- Payment apps can support multiple payment methods.
- Any payment method, such as cryptocurrency, bank transfers, and more, can be integrated. Payment apps on Android devices can even integrate methods that require access to the hardware chip on the device.

To understand how merchants integrate with payment apps, check out [Life of a payment transaction](/life-of-a-payment-transaction/).

It takes four steps to implement Web Payments in an Android payment app:

1.  Let merchants discover your payment app.
2.  Let a merchant know if a customer has an enrolled instrument (such as credit card) that is ready to pay.
3.  Let a customer make payment.
4.  Verify the caller's signing certificate.

To see Web Payments in action, check out the [android-web-payment](https://github.com/GoogleChromeLabs/android-web-payment/) demo.

## Step 1: Let merchants discover your payment app <a href="#step-1:-let-merchants-discover-your-payment-app" class="w-headline-link">#</a>

In order for a merchant to use your payment app, they need to use the [Payment Request API](https://developer.mozilla.org/docs/Web/API/Payment_Request_API) and specify the payment method you support using the [payment method identifier](https://www.w3.org/TR/payment-method-id/).

If you have a payment method identifier that is unique to your payment app, you can set up your own [payment method manifest](https://w3c.github.io/payment-method-manifest/) so browsers can discover your app.

To learn how the discovery process works in detail and how to set up a new payment method check out [Setting up a payment method](/setting-up-a-payment-method).

## Step 2: Let a merchant know if a customer has an enrolled instrument that is ready to pay <a href="#step-2:-let-a-merchant-know-if-a-customer-has-an-enrolled-instrument-that-is-ready-to-pay" class="w-headline-link">#</a>

The merchant can call `hasEnrolledInstrument()` to [query whether the customer is able to make a payment](/life-of-a-payment-transaction#ready-to-pay). You can implement `IS_READY_TO_PAY` as an Android service to answer this query.

### `AndroidManifest.xml` <a href="#androidmanifest.xml" class="w-headline-link">#</a>

Declare your service with an intent filter with the action `org.chromium.intent.action.IS_READY_TO_PAY`.

    <service
      android:name=".SampleIsReadyToPayService"
      android:exported="true">
      <intent-filter>
        <action android:name="org.chromium.intent.action.IS_READY_TO_PAY" />
      </intent-filter>
    </service>

The `IS_READY_TO_PAY` service is optional. If there's no such intent handler in the payment app, then the web browser assumes that the app can always make payments.

### AIDL <a href="#aidl" class="w-headline-link">#</a>

The API for the `IS_READY_TO_PAY` service is defined in AIDL. Create two AIDL files with the following content:

app/src/main/aidl/org/chromium/IsReadyToPayServiceCallback.aidl

    package org.chromium;
    interface IsReadyToPayServiceCallback {
        oneway void handleIsReadyToPay(boolean isReadyToPay);
    }

app/src/main/aidl/org/chromium/IsReadyToPayService.aidl

    package org.chromium;
    import org.chromium.IsReadyToPayServiceCallback;

    interface IsReadyToPayService {
        oneway void isReadyToPay(IsReadyToPayServiceCallback callback);
    }

### Implementing `IsReadyToPayService` <a href="#implementing-isreadytopayservice" class="w-headline-link">#</a>

The simplest implementation of `IsReadyToPayService` is shown in the following example:

    class SampleIsReadyToPayService : Service() {
      private val binder = object : IsReadyToPayService.Stub() {
        override fun isReadyToPay(callback: IsReadyToPayServiceCallback?) {
          callback?.handleIsReadyToPay(true)
        }
      }

      override fun onBind(intent: Intent?): IBinder? {
        return binder
      }
    }

### Parameters <a href="#parameters" class="w-headline-link">#</a>

Pass the following parameters to `onBind` as Intent extras:

- `methodNames`
- `methodData`
- `topLevelOrigin`
- `topLevelCertificateChain`
- `topLevelCertificateChain`
- `paymentRequestOrigin`

<!-- -->

    override fun onBind(intent: Intent?): IBinder? {
      val extras: Bundle? = intent?.extras
      // …
    }

#### `methodNames` <a href="#methodnames" class="w-headline-link">#</a>

The names of the methods being queried. The elements are the keys in the `methodData` dictionary, and indicate the methods that the payment app supports.

    val methodNames: List<String>? = extras.getStringArrayList("methodNames")

#### `methodData` <a href="#methoddata" class="w-headline-link">#</a>

A mapping from each entry of `methodNames` to the [`methodData`](https://w3c.github.io/payment-request/#declaring-multiple-ways-of-paying).

    val methodData: Bundle? = extras.getBundle("methodData")

#### `topLevelOrigin` <a href="#toplevelorigin" class="w-headline-link">#</a>

The merchant's origin without the scheme (the scheme-less origin of the top-level browsing context). For example, `https://mystore.com/checkout` will be passed as `mystore.com`.

    val topLevelOrigin: String? = extras.getString("topLevelOrigin")

#### `topLevelCertificateChain` <a href="#toplevelcertificatechain" class="w-headline-link">#</a>

The merchant's certificate chain (the certificate chain of the top-level browsing context). Null for localhost and file on disk, which are both secure contexts without SSL certificates. The certificate chain is necessary because a payment app might have different trust requirements for websites.

    val topLevelCertificateChain: Array<Parcelable>? =
        extras.getParcelableArray("topLevelCertificateChain")

Each `Parcelable` is a `Bundle` with a `"certificate"` key and a byte array value.

    val list: List<ByteArray>? = topLevelCertificateChain?.mapNotNull { p ->
      (p as Bundle).getByteArray("certificate")
    }

#### `paymentRequestOrigin` <a href="#paymentrequestorigin" class="w-headline-link">#</a>

The schemeless origin of the iframe browsing context that invoked the `new PaymentRequest(methodData, details, options)` constructor in JavaScript. If the constructor was invoked from the top-level context, then the value of this parameter equals the value of `topLevelOrigin` parameter.

    val paymentRequestOrigin: String? = extras.getString("paymentRequestOrigin")

### Response <a href="#response" class="w-headline-link">#</a>

The service can send its response via `handleIsReadyToPay(Boolean)` method.

    callback?.handleIsReadyToPay(true)

### Permission <a href="#permission" class="w-headline-link">#</a>

You can use `Binder.getCallingUid()` to check who the caller is. Note that you have to do this in the `isReadyToPay` method, not in the `onBind` method.

    override fun isReadyToPay(callback: IsReadyToPayServiceCallback?) {
      try {
        val callingPackage = packageManager.getNameForUid(Binder.getCallingUid())
        // …

See [Verify the caller's signing certificate](#heading=h.czr8ye23zg2e) about how to verify that the calling package has the right signature.

## Step 3: Let a customer make payment <a href="#step-3:-let-a-customer-make-payment" class="w-headline-link">#</a>

The merchant calls `show()` to [launch the payment app](/life-of-a-payment-transaction#step-4:-the-browser-launches-the-payment-app) so the customer can make a payment. The payment app is invoked via an Android intent `PAY` with transaction information in the intent parameters.

The payment app responds with `methodName` and `details`, which are payment app specific and are opaque to the browser. The browser converts the `details` string into a JavaScript object for the merchant via JSON deserialization, but does not enforce any validity beyond that. The browser does not modify the `details`; that parameter's value is passed directly to the merchant.

### `AndroidManifest.xml` <a href="#androidmanifest.xml-2" class="w-headline-link">#</a>

The activity with the `PAY` intent filter should have a `<meta-data>` tag [that identifies the default payment method identifier for the app](/setting-up-a-payment-method).

To support multiple payment methods, add a `<meta-data>` tag with a `<string-array>` resource.

    <activity
      android:name=".PaymentActivity"
      android:theme="@style/Theme.SamplePay.Dialog">
      <intent-filter>
        <action android:name="org.chromium.intent.action.PAY" />
      </intent-filter>

      <meta-data
        android:name="org.chromium.default_payment_method_name"
        android:value="https://bobpay.xyz/pay" />
      <meta-data
        android:name="org.chromium.payment_method_names"
        android:resource="@array/method_names" />
    </activity>

The `resource` must be a list of strings, each of which must be a valid, absolute URL with an HTTPS scheme as shown here.

    <?xml version="1.0" encoding="utf-8"?>
    <resources>
        <string-array name="method_names">
            <item>https://alicepay.com/put/optional/path/here</item>
            <item>https://charliepay.com/put/optional/path/here</item>
        </string-array>
    </resources>

### Parameters <a href="#parameters-2" class="w-headline-link">#</a>

The following parameters are passed to the activity as Intent extras:

- `methodNames`
- `methodData`
- `topLevelOrigin`
- `topLevelCertificateChain`
- `paymentRequestOrigin`
- `total`
- `modifiers`
- `paymentRequestId`

<!-- -->

    val extras: Bundle? = intent?.extras

#### methodNames <a href="#methodnames-2" class="w-headline-link">#</a>

The names of the methods being used. The elements are the keys in the `methodData` dictionary. These are the methods that the payment app supports.

    val methodNames: List<String>? = extras.getStringArrayList("methodNames")

#### `methodData` <a href="#methoddata-2" class="w-headline-link">#</a>

A mapping from each of the `methodNames` to the [`methodData`](https://w3c.github.io/payment-request/#declaring-multiple-ways-of-paying).

    val methodData: Bundle? = extras.getBundle("methodData")

#### merchantName <a href="#merchantname" class="w-headline-link">#</a>

The contents of the `<title>` HTML tag of the merchant's checkout page (the browser's top-level browsing context).

    val merchantName: String? = extras.getString("merchantName")

#### `topLevelOrigin` <a href="#toplevelorigin-2" class="w-headline-link">#</a>

The merchant's origin without the scheme (The scheme-less origin of the top-level browsing context). For example, `https://mystore.com/checkout` is passed as `mystore.com`.

    val topLevelOrigin: String? = extras.getString("topLevelOrigin")

#### `topLevelCertificateChain` <a href="#toplevelcertificatechain-2" class="w-headline-link">#</a>

The merchant's certificate chain (The certificate chain of the top-level browsing context). Null for localhost and file on disk, which are both secure contexts without SSL certificates. Each `Parcelable` is a Bundle with a `certificate` key and a byte array value.

    val topLevelCertificateChain: Array<Parcelable>? =
        extras.getParcelableArray("topLevelCertificateChain")
    val list: List<ByteArray>? = topLevelCertificateChain?.mapNotNull { p ->
      (p as Bundle).getByteArray("certificate")
    }

#### `paymentRequestOrigin` <a href="#paymentrequestorigin-2" class="w-headline-link">#</a>

The scheme-less origin of the iframe browsing context that invoked the `new PaymentRequest(methodData, details, options)` constructor in JavaScript. If the constructor was invoked from the top-level context, then the value of this parameter equals the value of `topLevelOrigin` parameter.

    val paymentRequestOrigin: String? = extras.getString("paymentRequestOrigin")

#### `total` <a href="#total" class="w-headline-link">#</a>

The JSON string representing the total amount of the transaction.

    val total: String? = extras.getString("total")

Here's an example content of the string:

    {"currency":"USD","value":"25.00"}

#### `modifiers` <a href="#modifiers" class="w-headline-link">#</a>

The output of `JSON.stringify(details.modifiers)`, where `details.modifiers` contain only `supportedMethods` and `total`.

#### `paymentRequestId` <a href="#paymentrequestid" class="w-headline-link">#</a>

The `PaymentRequest.id` field that "push-payment" apps should associate with the transaction state. Merchant websites will use this field to query the "push-payment" apps for the state of transaction out of band.

    val paymentRequestId: String? = extras.getString("paymentRequestId")

### Response <a href="#response-2" class="w-headline-link">#</a>

The activity can send its response back through `setResult` with `RESULT_OK`.

    setResult(Activity.RESULT_OK, Intent().apply {
      putExtra("methodName", "https://bobpay.xyz/pay")
      putExtra("details", "{\"token\": \"put-some-data-here\"}")
    })
    finish()

You must specify two parameters as Intent extras:

- `methodName`: The name of the method being used.
- `details`: JSON string containing information necessary for the merchant to complete the transaction. If success is `true`, then `details` must be constructed in such a way that `JSON.parse(details)` will succeed.

You can pass `RESULT_CANCELED` if the transaction was not completed in the payment app, for example, if the user failed to type in the correct PIN code for their account in the payment app. The browser may let the user choose a different payment app.

    setResult(RESULT_CANCELED)
    finish()

If the activity result of a payment response received from the invoked payment app is set to `RESULT_OK`, then Chrome will check for non-empty `methodName` and `details` in its extras. If the validation fails Chrome will return a rejected promise from `request.show()` with one of the following developer facing error messages:

    'Payment app returned invalid response. Missing field "details".'
    'Payment app returned invalid response. Missing field "methodName".'

### Permission <a href="#permission-2" class="w-headline-link">#</a>

The activity can check the caller with its `getCallingPackage()` method.

    val caller: String? = callingPackage

The final step is to verify the caller's signing certificate to confirm that the calling package has the right signature.

## Step 4: Verify the caller's signing certificate <a href="#step-4:-verify-the-caller&#39;s-signing-certificate" class="w-headline-link">#</a>

You can check the caller's package name with `Binder.getCallingUid()` in `IS_READY_TO_PAY`, and with `Activity.getCallingPackage()` in `PAY`. In order to actually verify that the caller is the browser you have in mind, you should check its signing certificate and make sure that it matches with the correct value.

If you're targeting API level 28 and above and are integrating with a browser that has a single signing certificate, you can use `PackageManager.hasSigningCertificate()`.

    val packageName: String = … // The caller's package name
    val certificate: ByteArray = … // The correct signing certificate.
    val verified = packageManager.hasSigningCertificate(
      callingPackage,
      certificate,
      PackageManager.CERT_INPUT_SHA256
    )

`PackageManager.hasSigningCertificate()` is preferred for single certificate browsers, because it correctly handles certificate rotation. (Chrome has a single signing certificate.) Apps that have multiple signing certificates cannot rotate them.

If you need to support older API levels 27 and below, or if you need to handle browsers with multiple signing certificates, you can use `PackageManager.GET_SIGNATURES`.

    val packageName: String = … // The caller's package name
    val certificates: Set<ByteArray> = … // The correct set of signing certificates

    val packageInfo = getPackageInfo(packageName, PackageManager.GET_SIGNATURES)
    val sha256 = MessageDigest.getInstance("SHA-256")
    val signatures = packageInfo.signatures.map { sha256.digest(it.toByteArray()) }
    val verified = signatures.size == certificates.size &&
        signatures.all { s -> certificates.any { it.contentEquals(s) } }

<a href="/tags/payments/" class="w-chip">Payments</a>

<span class="w-mr--sm">Last updated: May 25, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/payments/android-payment-apps-developers-guide/index.md)

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
