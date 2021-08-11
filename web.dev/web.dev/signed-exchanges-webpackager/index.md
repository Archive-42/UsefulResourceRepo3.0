<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format" alt="Abstract photo" class="w-hero w-hero--cover" sizes="100vw" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/f7TRFlVQv5w58A2Cbpg7.jpg?auto=format&amp;w=1600 1600w" width="1600" height="480" />

## <a href="#how-to-set-up-signed-exchanges-using-web-packager" class="w-toc__header--link">How to set up Signed Exchanges using Web Packager</a>

- [Serve SXGs using a self-signed certificate](#serve-sxgs-using-a-self-signed-certificate)
- [Prerequisites](#prerequisites)
- [Generate a self-signed certificate](#generate-a-self-signed-certificate)
- [Setup the Web Packager server for testing](#setup-the-web-packager-server-for-testing)
- [Serve signed exchanges using a CanSignHttpExchanges certificate](#serve-signed-exchanges-using-a-cansignhttpexchanges-certificate)
- [Prerequisites](#prerequisites-3)

Share<a href="/newsletter/" class="gc-analytics-event w-actions__fab w-actions__fab--subscribe"><span>subscribe</span></a>

- <a href="/" class="gc-analytics-event w-breadcrumbs__link w-breadcrumbs__link--left-justify">Home</a>
- <a href="/blog" class="gc-analytics-event w-breadcrumbs__link">All articles</a>

# How to set up Signed Exchanges using Web Packager

Learn how to serve signed exchanges (SXGs) using Web Packager.

Feb 19, 2020

[<img src="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?auto=format&amp;fit=crop&amp;h=64&amp;w=64" alt="Katie Hempenius" class="w-author__image" sizes="(min-width: 64px) 64px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=1&amp;q=75, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=2&amp;q=50 2x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=3&amp;q=35 3x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=4&amp;q=23 4x, https://web-dev.imgix.net/image/admin/fZo7BJGec2MNRt6cWpeh.jpg?fit=crop&amp;h=64&amp;w=64&amp;auto=format&amp;dpr=5&amp;q=20 5x" width="64" height="64" />](/authors/katiehempenius/)

<a href="/authors/katiehempenius/" class="w-author__name-link">Katie Hempenius</a>

- <a href="https://twitter.com/katiehempenius" class="w-author__link">Twitter</a>
- <a href="https://github.com/khempenius" class="w-author__link">GitHub</a>
- <a href="https://glitch.com/@khempenius" class="w-author__link">Glitch</a>
- <a href="https://katiehempenius.com/" class="w-author__link">Blog</a>

A [signed exchange (SXG)](/signed-exchanges) is a delivery mechanism that makes it possible to authenticate the origin of a resource independently of how it was delivered. The following instructions explain how to set up Signed Exchanges using [Web Packager](https://github.com/google/webpackager). Instructions are included for both self-signed and `CanSignHttpExchanges` certificates.

## Serve SXGs using a self-signed certificate <a href="#serve-sxgs-using-a-self-signed-certificate" class="w-headline-link">#</a>

Using a self-signed certificate to serve SXGs is primarily used for demonstration and testing purposes. SXGs signed with a self-signed certificate will generate error messages in the browser when used outside of testing environments and should not be served to crawlers.

### Prerequisites <a href="#prerequisites" class="w-headline-link">#</a>

To follow these instructions you will need to have [openssl](https://github.com/openssl/openssl#build-and-install) and [Go](https://golang.org/doc/install) installed in your development environment.

### Generate a self-signed certificate <a href="#generate-a-self-signed-certificate" class="w-headline-link">#</a>

This section explains how to generate a self-signed certificate that can be used with signed exchanges.

#### Instructions <a href="#instructions" class="w-headline-link">#</a>

1.  Generate a private key.

        openssl ecparam -out priv.key -name prime256v1 -genkey

    The private key will be saved as a file named `priv.key`.

2.  Create a [certificate signing request](https://en.wikipedia.org/wiki/Certificate_signing_request) (CSR).

        openssl req -new -sha256 -key priv.key -out cert.csr -subj '/O=Web Packager Demo/CN=example.com'

    A certificate signing request is a block of encoded text that conveys the information necessary to request a certificate from a [certificate authority(CA)](https://en.wikipedia.org/wiki/Certificate_authority). Although you will not be requesting a certificate from a CA, it is still necessary to create a certificate signing request.

    The command above creates a certificate signing request for an organization named `Web Packager Demo` that has the [common name](https://knowledge.digicert.com/solution/SO7239.html) `example.com`. The common name should be the fully qualified domain name of the site that contains the content that you want to package as SXG.

    In a production SXG setup, this would be a site that you own. However, in a testing environment like the one described in these instructions, it can be any site.

3.  Create a certificate that has the `CanSignHttpExchanges` extension.

        openssl x509 -req -days 90 -in cert.csr -signkey priv.key -out cert.pem -extfile <(echo -e "1.3.6.1.4.1.11129.2.1.22 = ASN1:NULL\nsubjectAltName=DNS:example.com")

    This command uses the private key and the CSR created in steps 1 and 2 to create the certificate file `cert.pem`. The `-extfile` flag associates the certificate with the `CanSignHttpExchanges` certificate extension (`1.3.6.1.4.1.11129.2.1.22` is the [object identifier](https://access.redhat.com/documentation/en-us/red_hat_certificate_system/9/html/administration_guide/standard_x.509_v3_certificate_extensions) for the `CanSignHttpExchanges` extension). In addition, the `-extfile` flag also defines `example.com` as a [Subject Alternative Name](https://en.wikipedia.org/wiki/Subject_Alternative_Name).

    If you are curious about the contents of `cert.pem`, you can view them using the following command:

        openssl x509 -in cert.pem -noout -text

    You are done creating private keys and certificates. You will need the `priv.key` and `cert.pem` files in the next section.

### Setup the Web Packager server for testing <a href="#setup-the-web-packager-server-for-testing" class="w-headline-link">#</a>

#### Prerequisites <a href="#prerequisites-2" class="w-headline-link">#</a>

1.  Install [Web Packager](https://github.com/google/webpackager).

        git clone https://github.com/google/webpackager.git

2.  Build `webpkgserver`.

        cd webpackager/cmd/webpkgserver
        go build .

    `webpkgserver` is a specific binary within the Web Packager project.

3.  Verify that `webpkgserver` has been installed correctly.

        ./webpkgserver --help

    This command should return information about the usage of `webpkgserver`. If this does not work, a good first troubleshooting step is to verify that your [GOPATH](https://golang.org/doc/gopath_code.html#GOPATH) is configured correctly.

#### Instructions <a href="#instructions-2" class="w-headline-link">#</a>

1.  Navigate to the `webpkgserver` directory (you might already be in this directory).

        cd /path/to/cmd/webpkgserver

2.  Create a `webpkgsever.toml` file by copying the example.

        cp ./webpkgserver.example.toml ./webpkgserver.toml

    This file contains the configuration options for `webpkgserver`.

3.  Open `webpkgserver.toml` with an editor of your choice and make the following changes:

    - Change the line `#AllowTestCert = false` to `AllowTestCert = true`.
    - Change the line `PEMFile = 'path/to/your.pem'` to reflect the path to the PEM certificate, `cert.pem`, that you created. Do not change the line mentioning `TLS.PEMFile`—this is a different configuration option.
    - Change the line `KeyFile = 'priv.key'` to reflect the path of the private key, `priv.key`, that you created. Do not change the line mentioning `TLS.KeyFile`—this is a different configuration option.
    - Change the line `#CertURLBase = '/webpkg/cert'` to `CertURLBase = 'data:'`. `CertURLBase` indicates the serving location of the SXG certificate. This information is used to set the `cert-url` parameter in the [`Signature`](https://wicg.github.io/webpackage/draft-yasskin-http-origin-signed-responses.html#name-the-signature-header) header of the SXG. In production environments, `CertURLBase` is used like this: `CertURLBase = 'https://mysite.com/'`. However, for local testing, `CertURLBase = 'data:'` can be used to instruct `webpkgserver` to use a [data URL](https://developer.mozilla.org/en-US/docs/Web/HTTP/Basics_of_HTTP/Data_URIs) to inline the certificate in the `cert-url` field. For local testing, this is the most conveninent way to serve the SXG certificate.
    - Change the line `Domain = 'example.org'` to reflect the domain that you created a certificate for. If you have followed the instructions in this article verbatim, this should be changed to `example.com`. `webpkgserver` will only fetch content from the domain indicated by `webpkgserver.toml`. If you try to fetch pages from a different domain without updating `webpkgserver.toml`, the `webpkgserver` logs will show the error message `URL doesn't match the fetch targets`.

    **Optional**

    If you want to enable or disable [subresource preloading](https://github.com/WICG/webpackage/blob/master/explainers/signed-exchange-subresource-substitution.md), the following `webpkgserver.toml` configuration options are relevant:

    - To have `webpkgserver` insert directives for preloading stylesheet and script subresources as SXGs, change the line `#PreloadCSS = false` to `PreloadCSS = true`. In addition, change the line `#PreloadJS = false` to `PreloadJS = true`.

      As an alternative to using this configuration option, you can manually add `Link: rel="preload"` headers and `<link rel="preload">` tags to a page's HTML.

    - By default, `webpkgserver` replaces existing `<link rel="preload">` tags with the equivalent `<link>` tags necessary for fetching this content as SXG. In doing so, `webpkgserver` will set the [`allowed-alt-sxg`](https://github.com/WICG/webpackage/blob/main/explainers/signed-exchange-subresource-substitution.md#use-cases) and [`header-integrity`](https://github.com/WICG/webpackage/blob/main/explainers/signed-exchange-subresource-substitution.md#use-cases) directives as needed—HTML authors do not need to add these by hand. To override this behavior and keep existing non-SXG preloads, change `#KeepNonSXGPreloads (default = false)` to `KeepNonSXGPreloads = true`. Keep in mind that enabling this option may make the SXG ineligible for the Google SXG cache per these [requirements](https://github.com/google/webpackager/blob/master/docs/cache_requirements.md).

4.  Start `webpkgserver`.

        ./webpkgserver

    If the server has started successfully, you should see the following log messages:

        Listening at 127.0.0.1:8080
        Successfully retrieved valid OCSP.
        Writing to cache in /private/tmp/webpkg

    Your log messages may look slightly different. In particular, the directory that `webpkgserver` uses to cache certificates varies by operating system.

    If you do not see these messages, a good first troubleshooting step is to double-check `webpkgserver.toml`.

    If you update `webpkgserver.toml` you should restart `webpkgserver`.

5.  Launch Chrome using the following command:

        /Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome \
        --user-data-dir=/tmp/udd \
        --ignore-certificate-errors-spki-list=`openssl x509 -noout -pubkey -in cert.pem | openssl pkey -pubin -outform der | openssl dgst -sha256 -binary | base64`

    This command instructs Chrome to ignore the certificate errors associated with `cert.pem`. This makes it possible to test SXGs using a test certificate. If Chrome is launched without this command, inspecting the SXG in DevTools will display the error `Certificate verification error: ERR_CERT_INVALID`.

    **Note:**

    You may need to adjust this command to reflect the location of Chrome on your machine, as well as the location of `cert.pem`. If you've done this correctly, you should see a warning displayed below the address bar. The warning should be similar to this: `You are using an unsupported command-line flag: --ignore-certificate-errors-spki-list=9uxADcgc6/ho0mJLRMBcOjfBaN21k0sOInoMchr9CMY=.`

    If the warning does not include a hash string, you have not correctly indicated the location of the SXG certificate.

6.  Open the DevTools **Network** tab, then visit the following URL: `http://localhost:8080/priv/doc/https://example.com`.

    This makes a request to the `webpackager` instance running at `http://localhost:8080` for a SXG containing the contents of `https://example.com`. `/priv/doc/` is the default API endpoint used by `webpackager`.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format" alt="Screenshot of the DevTools Network tab showing a SXG and its certificate." sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/DPw05KcHLdWOgHYiDsgf.png?auto=format&amp;w=1600 1600w" width="800" height="236" />

The following resources are listed in the **Network** tab:

- A resource with the type `signed-exchange`. This is the SXG.
- A resource with the type `cert-chain+cbor`. This the SXG certificate. SXG certificates must use the `application/cert-chain+cbor` format.
- A resource with the type `document`. This is the content that has been delivered via SXG.

If you don't see these resources, try clearing the browser cache, then reloading `http://localhost:8080/priv/doc/https://example.com`.

Click on the **Preview** tab to see more information about the Signed Exchange and its signature.

<img src="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format" alt="Screenshot of the Preview tab showing a SXG" sizes="(min-width: 800px) 800px, calc(100vw - 48px)" srcset="https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=200 200w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=228 228w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=260 260w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=296 296w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=338 338w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=385 385w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=439 439w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=500 500w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=571 571w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=650 650w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=741 741w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=845 845w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=964 964w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=1098 1098w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=1252 1252w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=1428 1428w, https://web-dev.imgix.net/image/j2RDdG43oidUy6AL6LovThjeX9c2/x9hfT6ZJ8OuB4M1ImWic.png?auto=format&amp;w=1600 1600w" width="800" height="541" />

## Serve signed exchanges using a `CanSignHttpExchanges` certificate <a href="#serve-signed-exchanges-using-a-cansignhttpexchanges-certificate" class="w-headline-link">#</a>

The instructions in this section explain how to serve SXGs using a `CanSignHttpExchanges` certificate. Production use of SXGs requires a `CanSignHttpExchanges` certificate.

For the sake of brevity, these instructions are written with the assumption that you understand the concepts discussed in the [Setup Signed Exchanges using a self-signed certificate](/signed-exchanges-webpackager/#serve-sxgs-using-a-self-signed-certificate) section.

### Prerequisites <a href="#prerequisites-3" class="w-headline-link">#</a>

- You have a `CanSignHttpExchanges` certificate. This [page](https://github.com/google/webpackager/wiki/Certificate-Authorities) lists the CAs that offer this type of certificate.
- Although not a requirement, it is strongly recommended that you run `webpkgserver` behind an edge server. If you do not use an edge server, you will need to configure the `TLS.PEMFile` and `TLS.KeyFile` options in `webpkgserver.toml`. By default, `webpkgserver` runs over HTTP. However, SXG certificates must be served over HTTPS to be considered valid by the browser. Configuring `TLS.PEMFile` and `TLS.KeyFile` allows `webpkgserver` to use HTTPS and therefore serve the SXG certificate directly to the browser.

#### Instructions <a href="#instructions-3" class="w-headline-link">#</a>

1.  Create a PEM file by concatenating your site's SXG certificate followed by your site's CA certificate. More instructions on this can be found [here](https://www.digicert.com/kb/ssl-support/pem-ssl-creation.htm).

    [PEM](https://en.wikipedia.org/wiki/X.509#Certificate_filename_extensions) is a file format that is commonly used as a "container" for storing multiple certificates.

2.  Create a fresh `webpkgsever.toml` file by copying the example.

        cp ./webpkgserver.example.toml ./webpkgserver.toml

3.  Open `webpkgserver.toml` with the editor of your choice and make the following changes:

    - Change the line `PEMFile = cert.pem` to reflect the location of the PEM file containing your full certificate chain.
    - Change the line `KeyFile = 'priv.key'` to reflect the location of the private key corresponding to your PEM File.
    - Change the line `Domain = 'example.org'` to reflect your site.
    - (Optional) To have `webpkgserver` auto-renew the SXG certificate every 90 days, configure the options in the `[SXG.ACME]` section of `webpkgserver.toml`. This option only applies to sites with a DigiCert ACME account setup.

4.  Configure your edge server to forward traffic to the `webpkgserver` instance.

    There are two primary types of requests handled by `webpkgserver`: requests for SXGs (which are served by the `/priv/doc/` endpoint) and requests for the SXG certificate (which are served by the `/webpkg/cert/` endpoint). The URL rewriting rules for each of these request types varies slightly. For more information, see [Running behind front end edge server](https://github.com/google/webpackager/blob/master/cmd/webpkgserver/README.md#running-behind-front-end-edge-server).

    **Note:**

    By default, `webpkgserver` serves the SXG certificate at `/webpkg/cert/$CERT_HASH`—for example, `/webpkg/cert/-0QmE0gvoedn92gtwI3s7On9zPevJGm5pn2RYhpZxgY`. To generate `$CERT_HASH`, run the following command:

        openssl base64 -in cert.pem -d | openssl dgst -sha256 -binary | base64 | tr /+ _- | tr -d =

<a href="/tags/performance/" class="w-chip">Performance</a>

<span class="w-mr--sm">Last updated: Feb 19, 2020 </span>[Improve article](https://github.com/GoogleChrome/web.dev/blob/master/src/site/content/en/fast/signed-exchanges-webpackager/index.md)

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
