# fiskaltrust.Middleware 1.3.6 (Germany)
This release adds the functionality to locally generate our preview version of the DSFinV-K export, and the new production-ready Diebold Nixdorf SCU. Additionally, we fixed several issues and added some smaller improvements, mostly related to special receipt responses.

<div class="alert alert-warning" role="alert" style="border-radius: 0">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## New feature: Local DSFinV-K export (Preview)
Starting with this version, Middleware users can download the DSFinV-K export not only from the Portal, but also directly from the Middleware's _Journal_ endpoint. This enables users that use the free Middleware only (without any add-ons like the revision-safe cloud storage) to be fully compliant to the tax authorities' regulations. 

The receipt case for getting a DSFinV-K export is `0x4445000000000002`, the returned file is a .zip stream. More details about how to access this endpoint can be found in our [docs](https://docs.fiskaltrust.cloud/doc/interface-doc/doc/general/function-structures/function-structures.html#journal-function).

Please note that this is a **preview version** of the DSFinV-K export, and still contains a few issues and minor limitations:
- Some VAT rates are currently not calculated correctly, e.g. in `lines_vat.csv`
- Depending on how vouchers are booked, they may not yet be properly written into the export.
- The KASSE_UST_ZUORDNUNG field is not yet filled.

We decided for releasing this preview versions despite the known limitations to both give POS Creators the opportunity to already implement everything, and also gather as much direct feedback as possible. We will focus on resolving the open points as soon as possible and will release a new version with a feature-complete export soon.

## New SCU: Diebold Nixdorf
After testing our Diebold Nixdorf SCU thoroughly on the sandbox and obtaining some customer feedback (also via Github - thanks to everyone who reached out), we released the Diebold Nixdorf SCU to production. It therefore can be used and configured via the Portal the exact same way as our other SCUs.

Combined with the possibility to order these TSEs via our Portal's shop, we hope to be able to support all customer demands who plan to work with this hardware now.

## New feature: More detailed responses for closing and out-of-operation receipts
We got some customer feedback about missing information in _daily-closing_ and _out-of-operation_ receipt responses, and therefore included some additional data to them:
- Responses to _daily-closing_ receipts now contain the upcounting `DailyClosingNumber` property in the JSON body of the `ftStateData` field. This makes it possible to reference this number e.g. in later receipts without the requirement to count the daily closings in the POS software itself.
- Equivalent to _initial-operation_ receipts, _out-of-operation_ receipts now properly create notifications in both the SignatureItems of the response and the Action Journal. While the German tax authorities still don't require this (this regulation was deferred), we're now prepared to properly handle these notifications as soon as they become mandatory.

## Stability improvement: Exception handling
We fixed two issues related to exception handling in this release. The first one was a [bug](https://github.com/fiskaltrust/middleware-interface-dotnet/issues/24) that we accidentally introduced in version 1.3.5 and made the Middleware freeze in certain cases when an exception occurred in the Queue, e.g. when the sent `ftCashBoxId` was not matching. 

The second issue was less critical, but annoying as it hid other errors. In some cases, customers who use gRPC did not receive real exception messages, but an exception that _The gRPC trailing metadata exceeded the allowed size_. The reason is that we append error details to this trailing metadata - an example of how to read this can be found in our [gRPC samples](https://github.com/fiskaltrust/middleware-demo-dotnet/blob/master/src/fiskaltrust.Middleware.Demo.Grpc/Demo.cs#L174). This issue is now resolved as well.
