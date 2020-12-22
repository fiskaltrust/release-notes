# fiskaltrust.Middleware 1.3.12 (Germany)
_December 18, 2020_

This version of the Middleware fixes an important bug related to creating the signature payloads of _info-order_ receipts. **We hence strongly recommend all our users to update their versions of the Middleware in case they are using this receipt type.**

<div class="alert alert-warning" role="alert" style="border-radius: 0">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Bug fix: Signature payloads are incorrectly generated for info-order receipts
Due to an error in our business logic, the payload of _info-order_ receipts (i.e. receipts that ended up in a _Bestellung-V1_ bon) that was sent to the TSE was incorrectly created in some cases. This issue occurred when a _charge item_ quantity larger than `1` was used with this receipt type; instead of the expected price per item, the overall amount of the  _charge item_ was written into the payload. As this payload is signed by the TSE, the resulting signatures are incorrect as well in these cases. 

Other receipt types, especially types that create a _Kassenbeleg-V1_, were not affected. Therefore, the bookkeeping-relevant data can still be deduced from the signed receipts. As we create the DSFinV-K export from the receipts' raw data, these exports are also not affected by this issue and will still be created properly. 

Therefore, aside from updating the affected packages, no further steps should be required from a user perspective.

We'd like to apologize for the inconvenience created by this bug, and are currently introducing new tests and quality gates to prevent these kinds of issues in the future.

## Bug fix: Fail-transaction receipt could be used with implicit flow
Due to a missing check, the fail-transaction receipt could be used with the implicit flow in previous versions. As the implicit flow doesn't leave transactions open that could then be failed, we have modified the behavior of this case accordingly; hence, it's only possible to close transactions that were opened with an explicit start receipt with this case now.

- To close **single open transactions**, an **explicit** fail-transaction receipt needs to be used. The open transaction needs to be referenced via `cbReceiptReference`. In case this value is not provided or no open transaction exists, the Middleware will throw an exception and the call will fail.
- To close **multiple open transactions**, an **implicit** fail-transaction receipt needs to be sent. The transaction numbers that should be closed need to be passed via JSON in `ftReceiptCaseData`, using the array property `CurrentStartedTransactionNumbers` (e.g.: `ftReceiptCaseData: "{\"CurrentStartedTransactionNumbers\": [1, 2, 3]}"`). `cbReceiptReference` must be empty in this case, the Middleware will throw an exception and return an error otherwise.

We're aware of the fact that some customers have been using this case to fail parts of ongoing receipt sequences with the implicit flow. This, however, is unfortunately not correct according to the DSFinV-K, and that's why we now actively prevent this. 

If the receipt case was used to fail short processes (like e.g. reverting scanning items in retail scenarios), please keep in mind that the DSFinV-K doesn't require all scanned items to be sent to the TSE; it's just important to create a _"SonstigerVorgang"_ at the beginning to log the start timestamp of the business transaction. We hence recommend to only send an _info-internal_ receipt once at the beginning and one _POS receipt_ at the end of the process to fulfill these requirements. As no _info-orders_ are used in this sequence, it's not required to cancel anything in case of e.g. a duplicate scan.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

Due to the critical nature of this bug fix, we **strongly recommend** all users to update to the latest version.

- _fiskaltrust.Middleware.Queue.EF v1.3.12_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.12_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.12-rc1_

## Next steps in the Middleware
We will continue to improve the stability of our Middleware in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
