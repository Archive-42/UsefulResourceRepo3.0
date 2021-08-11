## <a href="#providing-shipping-and-contact-information-from-an-android-payment-app" class="w-toc__header--link">Providing shipping and contact information from an Android payment app</a>

- [Declare supported delegations](#declare-supported-delegations)
- [Parse PAY intent extras for required payment options](#parse-pay-intent-extras-for-required-payment-options)
- [paymentOptions](#paymentoptions)
- [shippingOptions](#shipping-options)
- [Provide required information in a payment response](#provide-required-information-in-a-payment-response)
- [Payment response validation](#payment-response-validation)
- [Optional: Support dynamic flow](#optional:-support-dynamic-flow)
- [AIDL](#aidl)
- [Notify the merchant about changes in the user selected payment method, shipping address, or shipping option](#notify-the-merchant-about-changes-in-the-user-selected-payment-method-shipping-address-or-shipping-option)
- [Receive updated payment details from the merchant](#receive-updated-payment-details-from-the-merchant)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

# Providing shipping and contact information from an Android payment app

How to update your Android payment app to provide shipping address and payer's contact information with Web Payments APIs.

Jul 17, 2020

<span class="w-post-signpost__title">Appears in:</span> <a href="/payments" class="w-post-signpost__link">Web Payments</a>

[<img src="https://web-dev.imgix.net/image/admin/X2tDP3SQzVCQ8dVLmMMI.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Sahel Sharify" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/X2tDP3SQzVCQ8dVLmMMI.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/X2tDP3SQzVCQ8dVLmMMI.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/X2tDP3SQzVCQ8dVLmMMI.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/X2tDP3SQzVCQ8dVLmMMI.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/X2tDP3SQzVCQ8dVLmMMI.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/sahel/)

<a href="/authors/sahel/" class="w-author__name-link">Sahel Sharify</a>

- <a href="https://github.com/sahel-sh" class="w-author__link">GitHub</a>

Entering shipping address and contact information through a web form can be a cumbersome experience for customers. It can cause errors and lower conversion rate.

That's why the Payment Request API supports a feature to request shipping address and contact information. This provides multiple benefits:

- Users can pick the right address with just a few taps.
- The address is always returned in [the standardized format](https://w3c.github.io/payment-request/#paymentaddress-interface).
- Submitting an incorrect address is less likely.

This functionality can be deferred to a payment app to offer a unified payment experience and it's called _delegation_.

Whenever possible, Chrome delegates the collection of a customer's shipping address and contact information to the invoked Android payment app. The delegation reduces the friction during checkout because the user's installed payment apps usually have more accurate information about their shipping address and contact details.

The merchant website can dynamically update the shipping options and total price depending on the customer's choice of the shipping address and the shipping option.

Shipping option and shipping address change in action. See how it affects shipping options and total price dynamically.

Learn how to implement an [Android payment app](/android-payment-apps-developers-guide/) in advance.

To add delegation support to an already existing Android payment app, implement the following steps:

1.  Declare supported delegations.
2.  Parse `PAY` intent extras for required payment options.
3.  Provide required information in payment response.
4.  \[Optional\] Support dynamic flow:
    1.  Notify the merchant about changes in the user selected payment method, shipping address, or shipping option.
    2.  Receive updated payment details from the merchant (for example, the adjusted total amount based on the selected shipping option's cost).

## Declare supported delegations <a href="#declare-supported-delegations" class="w-headline-link">#</a>

The browser needs to know the list of additional information that your payment app can provide so it can delegate the collection of that information to your app. Declare the supported delegations as a `<meta-data>` in your app's [AndroidManifest.xml](/android-payment-apps-developers-guide/#androidmanifest.xml-2).

    <activity
      android:name=".PaymentActivity"
      …
      <meta-data
        android:name="org.chromium.payment_supported_delegations"
        android:resource="@array/supported_delegations" />
    </activity>

`<resource>` must be a list of strings chosen from the following valid values:

    [ "payerName", "payerEmail", "payerPhone", "shippingAddress" ]

The following example can only provide a shipping address and the payer's email address.

    <?xml version="1.0" encoding="utf-8"?>
    <resources>
      <string-array name="supported_delegations">
        <item>payerEmail</item>
        <item>shippingAddress</item>
      </string-array>
    </resources>

## Parse `PAY` intent extras for required payment options <a href="#parse-pay-intent-extras-for-required-payment-options" class="w-headline-link">#</a>

The merchant can specify additional required information using the [`paymentOptions`](https://www.w3.org/TR/payment-request/#paymentoptions-dictionary) dictionary. Chrome will provide the list of required options that your app can provide by passing the following parameters to the `PAY` activity as [Intent extras](/android-payment-apps-developers-guide/#parameters-2).

### `paymentOptions` <a href="#paymentoptions" class="w-headline-link">#</a>

`paymentOptions` is the subset of merchant specified payment options for which your app has declared delegation support.

    val paymentOptions: Bundle? = extras.getBundle("paymentOptions")
    val requestPayerName: Boolean? = paymentOptions?.getBoolean("requestPayerName")
    val requestPayerPhone: Boolean? = paymentOptions?.getBoolean("requestPayerPhone")
    val requestPayerEmail: Boolean? = paymentOptions?.getBoolean("requestPayerEmail")
    val requestShipping: Boolean? = paymentOptions?.getBoolean("requestShipping")
    val shippingType: String? = paymentOptions?.getString("shippingType")

It can include the following parameters:

- `requestPayerName` - The boolean indicating whether or not the payer's name is required.
- `requestPayerPhone` - The boolean indicating whether or not the payer's phone is required.
- `requestPayerEmail` - The boolean indicating whether or not the payer's email is required.
- `requestShipping` - The boolean indicating whether or not shipping information is required.
- `shippingType` - The string showing the type of shipping. Shipping type can be `"shipping"`, `"delivery"`, or `"pickup"`. Your app can use this hint in its UI when asking for the user's address or choice of shipping options.

### `shippingOptions` <a href="#shipping-options" class="w-headline-link">#</a>

`shippingOptions` is the parcelable array of merchant specified shipping options. This parameter will only exist when `paymentOptions.requestShipping == true`.

    val shippingOptions: List<ShippingOption>? =
        extras.getParcelableArray("shippingOptions")?.mapNotNull {
            p -> from(p as Bundle)
        }

Each shipping option is a `Bundle` with the following keys.

- `id` - The shipping option identifier.
- `label` - The shipping option label shown to the user.
- `amount` - The shipping cost bundle containing `currency` and `value` keys with string values.
  - `currency` shows the currency of the shipping cost, as an [ISO4217](https://www.iso.org/iso-4217-currency-codes.html) well-formed 3-letter alphabet code
  - `value` shows the value of the shipping cost, as a [valid decimal monetary value](https://w3c.github.io/payment-request/#dfn-valid-decimal-monetary-value)
- `selected` - Whether or not the shipping option should be selected when the payment app displays the shipping options.

All keys other than the `selected` have string values. `selected` has a boolean value.

    val id: String = bundle.getString("id")
    val label: String = bundle.getString("label")
    val amount: Bundle = bundle.getBundle("amount")
    val selected: Boolean = bundle.getBoolean("selected", false)

## Provide required information in a payment response <a href="#provide-required-information-in-a-payment-response" class="w-headline-link">#</a>

Your app should include the required additional information in its response to the `PAY` activity.

To do so the following parameters must be specified as Intent extras:

- `payerName` - The payer's full name. This should be a non-empty string when `paymentOptions.requestPayerName` is true.
- `payerPhone` - The payer's phone number. This should be a non-empty string when `paymentOptions.requestPayerPhone` is true.
- `payerEmail` - The payer's email address. This should be a non-empty string when `paymentOptions.requestPayerEmail` is true.
- `shippingAddress` - The user-provided shipping address. This should be a non-empty bundle when `paymentOptions.requestShipping` is true. The bundle should have the following keys which represent different parts in a [physical address](https://www.w3.org/TR/payment-request/#physical-addresses).
  - `city`
  - `countryCode`
  - `dependentLocality`
  - `organization`
  - `phone`
  - `postalCode`
  - `recipient`
  - `region`
  - `sortingCode`
  - `addressLine` All keys other than the `addressLine` have string values. The `addressLine` is an array of strings.
- `shippingOptionId` - The identifier of the user-selected shipping option. This should be a non-empty string when `paymentOptions.requestShipping` is true.

### Payment response validation <a href="#payment-response-validation" class="w-headline-link">#</a>

If the activity result of a payment response received from the invoked payment app is set to `RESULT_OK`, then Chrome will check for required additional information in its extras. If the validation fails Chrome will return a rejected promise from `request.show()` with one of the following developer-facing error messages:

    'Payment app returned invalid response. Missing field "payerEmail".'
    'Payment app returned invalid response. Missing field "payerName".'
    'Payment app returned invalid response. Missing field "payerPhone".'
    'Payment app returned invalid shipping address in response.'
    '... is not a valid CLDR country code, should be 2 upper case letters [A-Z]'
    'Payment app returned invalid response. Missing field "shipping option".'

Below is an example of a valid response:

    fun Intent.populateRequestedPaymentOptions() {
        if (requestPayerName) {
            putExtra("payerName", "John Smith")
        }
        if (requestPayerPhone) {
            putExtra("payerPhone", "4169158200")
        }
        if (requestPayerEmail) {
            putExtra("payerEmail", "john.smith@gmail.com")
        }
        if(requestShipping) {
            val address: Bundle = Bundle()
            address.putString("countryCode", "CA")
            val addressLines: Array<String> =
                    arrayOf<String>("111 Richmond st. West")
            address.putStringArray("addressLines", addressLines)
            address.putString("region", "Ontario")
            address.putString("city", "Toronto")
            address.putString("postalCode", "M5H2G4")
            address.putString("recipient", "John Smith")
            address.putString("phone", "4169158200")
            putExtra("shippingAddress", address)
            putExtra("shippingOptionId", "standard")
        }
    }

## Optional: Support dynamic flow <a href="#optional:-support-dynamic-flow" class="w-headline-link">#</a>

Sometimes the total cost of a transaction increases, such as when the user chooses the express shipping option, or when the list of available shipping options or their prices changes when the user chooses an international shipping address. When your app provides the user-selected shipping address or option, it should be able to notify the merchant about any shipping address or option changes and show the user the updated payment details (provided by the merchant).

### AIDL <a href="#aidl" class="w-headline-link">#</a>

To notify the merchant about new changes use the `PaymentDetailsUpdateService` service declared in Chrome's AndroidManifest.xml. To use this service create two AIDL files with the following content:

app/src/main/aidl/org/chromium/components/payments/IPaymentDetailsUpdateService

    package org.chromium.components.payments;
    import android.os.Bundle;

    interface IPaymentDetailsUpdateServiceCallback {
        oneway void updateWith(in Bundle updatedPaymentDetails);

        oneway void paymentDetailsNotUpdated();
    }

app/src/main/aidl/org/chromium/components/payments/IPaymentDetailsUpdateServiceCallback

    package org.chromium.components.payments;
    import android.os.Bundle;
    import org.chromium.components.payments.IPaymentDetailsUpdateServiceCallback;

    interface IPaymentDetailsUpdateService {
        oneway void changePaymentMethod(in Bundle paymentHandlerMethodData,
                IPaymentDetailsUpdateServiceCallback callback);

        oneway void changeShippingOption(in String shippingOptionId,
                IPaymentDetailsUpdateServiceCallback callback);

        oneway void changeShippingAddress(in Bundle shippingAddress,
                IPaymentDetailsUpdateServiceCallback callback);
    }

### Notify the merchant about changes in the user selected payment method, shipping address, or shipping option <a href="#notify-the-merchant-about-changes-in-the-user-selected-payment-method-shipping-address-or-shipping-option" class="w-headline-link">#</a>

    private fun bind() {
        // The action is introduced in Chrome version 92, which supports the service in Chrome
        // and other browsers (e.g., WebLayer).
        val newIntent = Intent("org.chromium.intent.action.UPDATE_PAYMENT_DETAILS")
            .setPackage(callingBrowserPackage)
        if (packageManager.resolveService(newIntent, PackageManager.GET_RESOLVED_FILTER) == null) {
            // Fallback to Chrome-only approach.
            newIntent.setClassName(
                callingBrowserPackage,
                "org.chromium.components.payments.PaymentDetailsUpdateService")
            newIntent.action = IPaymentDetailsUpdateService::class.java.name
        }
        isBound = bindService(newIntent, connection, Context.BIND_AUTO_CREATE)
    }

    private val connection = object : ServiceConnection {
        override fun onServiceConnected(className: ComponentName, service: IBinder) {
            val service = IPaymentDetailsUpdateService.Stub.asInterface(service)
            try {
                if (isOptionChange) {
                    service?.changeShippingOption(selectedOptionId, callback)
                } else (isAddressChange) {
                    service?.changeShippingAddress(selectedAddress, callback)
                } else {
                    service?.changePaymentMethod(methodData, callback)
                }
            } catch (e: RemoteException) {
                // Handle the remote exception
            }
        }
    }

The `callingPackageName` used for the service's start intent can have one of the following values depending on the browser that has initiated the payment request.

<table><thead><tr class="header"><th>Chrome Channel</th><th>Package Name</th></tr></thead><tbody><tr class="odd"><td>Stable</td><td><code>"com.android.chrome"</code></td></tr><tr class="even"><td>Beta</td><td><code>"com.chrome.beta"</code></td></tr><tr class="odd"><td>Dev</td><td><code>"com.chrome.dev"</code></td></tr><tr class="even"><td>Canary</td><td><code>"com.chrome.canary"</code></td></tr><tr class="odd"><td>Chromium</td><td><code>"org.chromium.chrome"</code></td></tr><tr class="even"><td>Google Quick Search Box (a WebLayer embedder)</td><td><code>"com.google.android.googlequicksearchbox"</code></td></tr></tbody></table>

#### `changePaymentMethod` <a href="#changepaymentmethod" class="w-headline-link">#</a>

Notifies the merchant about changes in the user-selected payment method. The `paymentHandlerMethodData` bundle contains `methodName` and optional `details` keys both with string values. Chrome will check for a non-empty bundle with a non-empty `methodName` and send an `updatePaymentDetails` with one of the following error messages via `callback.updateWith` if the validation fails.

    'Method data required.'
    'Method name required.'

#### `changeShippingOption` <a href="#changeshippingoption" class="w-headline-link">#</a>

Notifies the merchant about changes in the user-selected shipping option. `shippingOptionId` should be the identifier of one of the merchant-specified shipping options. Chrome will check for a non-empty `shippingOptionId` and send an `updatePaymentDetails` with the following error message via `callback.updateWith` if the validation fails.

    'Shipping option identifier required.'

#### `changeShippingAddress` <a href="#changeshippingaddress" class="w-headline-link">#</a>

Notifies the merchant about changes in the user-provided shipping address. Chrome will check for a non-empty `shippingAddress` bundle with a valid `countryCode` and send an `updatePaymentDetails` with the following error message via `callback.updateWith` if the validation fails.

    'Payment app returned invalid shipping address in response.'

#### Invalid state error message <a href="#invalid-state-error-message" class="w-headline-link">#</a>

If Chrome encounters an invalid state upon receiving any of the change requests it will call `callback.updateWith` with a redacted `updatePaymentDetails` bundle. The bundle will only contain the `error` key with `"Invalid state"`. Examples of an invalid state are:

- When Chrome is still waiting for the merchant's response to a previous change (such as an ongoing change event).
- The payment-app-provided shipping option identifier does not belong to any of the merchant-specified shipping options.

### Receive updated payment details from the merchant <a href="#receive-updated-payment-details-from-the-merchant" class="w-headline-link">#</a>

    private fun unbind() {
        if (isBound) {
            unbindService(connection)
            isBound = false
        }
    }

    private val callback: IPaymentDetailsUpdateServiceCallback =
        object : IPaymentDetailsUpdateServiceCallback.Stub() {
            override fun paymentDetailsNotUpdated() {
                // Payment request details have not changed.
                unbind()
            }

            override fun updateWith(updatedPaymentDetails: Bundle) {
                newPaymentDetails = updatedPaymentDetails
                unbind()
            }
        }

`updatePaymentDetails` is the bundle equivalent to the [`PaymentRequestDetailsUpdate`](https://w3c.github.io/payment-handler/#the-paymentrequestdetailsupdate) [WebIDL](https://www.w3.org/TR/WebIDL-1/) dictionary (after redacting the `modifiers` field) and contains the following optional keys:

- `total` - A bundle containing `currency` and `value` keys, both keys have string values
- `shippingOptions` - The parcelable array of [shipping options](#shipping-options)
- `error` - A string containing a generic error message (e.g. when `changeShippingOption` does not provide a valid shipping option identifier)
- `stringifiedPaymentMethodErrors` - A JSON string representing validation errors for the payment method
- `addressErrors` - A bundle with optional keys identical to [shipping address](#provide-required-information-in-a-payment-response) and string values. Each key represents a validation error related to its corresponding part of the shipping address.

An absent key means its value has not changed.

<a href="/tags/payments/" class="w-chip">Payments</a>

<span class="w-mr--sm">Last updated: Jul 17, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/payments/android-payment-apps-delegation/index.md)

<a href="/payments" class="gc-analytics-event w-article-navigation__link w-article-navigation__link--back w-article-navigation__link--single">Return to all articles</a>

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
