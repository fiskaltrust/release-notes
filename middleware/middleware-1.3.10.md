# fiskaltrust.Middleware 1.3.10 (Germany)
_October 28, 2020_

We're happy to announce that starting from this version, we provide SCUs for all currently certified TSEs, as well as SCUs for two major cloud TSEs that are currently in certification (fiskaly and A-Trust). While some of those are still only available on the sandbox, we consider them production-ready and are working closely with our partners to push them to production as soon as possible.

In addition to this, we resolved several important stability issues in version 1.3.10, which should result in an overall greatly increased reliability, especially when working with Swissbit SCUs. Also, we fixed an important issue in our SQLite implementation that lead to data not being 100% correctly read from the database (although no data was lost, as everything was written correctly).

**We highly recommend updating to this version on POS Systems that use SQLite Queues to resolve this issue.**

<div class="alert alert-warning" role="alert" style="border-radius: 0">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## New SCU: DeutscheFiskal (Sandbox)
The _Deutsche Fiskal cloud TSE_ is the first cloud-based approach that got certified by the BSI recently. Naturally, we wanted to provide support for this solution as soon as possible, and are happy to announce that the Middleware can now be configured to use it equally to other TSEs.

Additionally, we decided to reduce the configuration amount on the side of our partners and support the automatic download and setup of the FCC (_Fiscal Cloud Connector_, the web service that must be running on site) - if required, it's also possible to bypass this functionality and manually install this service.

While this TSE is running smoothly in our tests so far, there are some limitations, both technically and due to the business model:
- The DeutscheFiskal TSE was only certified for Windows 10 so far. Although the producer is working on additional certifications for other OS, it can meanwhile officially only be operated on Windows 10 machines.
- Due to the pricing model (pricing is calculated per client, not per TSE), our usual rollout scenarios are limited. We are working on updating our [documentation](https://docs.fiskaltrust.cloud/doc/productdescription-de-doc/for-posdealers/02-pre-sales/rollout-scenarios.html) to reflect these limitations.

## New SCU: Epson (Sandbox)
Previously to this version, our Epson SCU was still based on our interface 1.3.0 and hence incompatible to newer Queues (with version >= 1.3.1). While updating this SCU to the latest interface version, we greatly improved the stability and especially the compatibility, which now works with USB devices, printers, and Epson TSE servers.

We are working closely together with our partners to evaluate this SCU and will push it to production as soon as we gathered enough feedback to be confident that everything is working as expected in real-world scenarios.

## Stability improvement: Fixed concurrency issues in Swissbit SCU
We fixed a concurrency issue in our Swissbit SCU that lead to failed receipts and a switch to the failover-mode in some cases. While not many POS implementations were affected by this, the issue was occurring frequently for some customers, and was therefore now fixed.

## Stability improvement: Better error messages when sending wrong foreign currency requests
We improved the error messages that are returned by the Middleware in case a request that contains foreign currencies was missing some required fields in `ftReceiptCaseData`, which should simplify the implementation of these cases.

## Bug fix: A decimal value is cut while reading receipt journals in SQLite
Due to an issue in our SQLite implementation, we were missing precision in the `ftReceiptTotal` field while _reading_ receipt journals. Writing data was **not** affected, as all values were stored correctly. Additionally, this value is **not** used internally (i.e. for chaining, ...).

This issue was now resolved.

## Bug fix: Using float types for MySQL entities
While fixing the previous issue, we noticed a similar problem in our new MySQL queue. This was now resolved, and precision is now read correctly here as well.

## Bug fix: Exclude "Other processes"/"Andere Vorgänge" from cashpoint closing module in DSFinV-K export
Both during our internal tests and due to customer feedback, we noticed that the cashpoint closing module ("Kassenabschlussmodul") in the DSFinV-K contained too many entries, leading to wrong turnovers (e.g. if a receipt sequence contained the same items in _info-order_ and _POS receipt_ requests). This issue was now resolved, as the cashpoint closing module should only contain data from bons of the type _Beleg_.

## Bug fix: Wrong parameter sent to journal endpoint while uploading 
Due to an issue in the Middleware component that is responsible for uploading receipt data to our cloud systems, we queried more data than necessary from the Middleware before the upload, resulting in overall reduced performance and sometimes timeout issues while performing these uploads.

This issue is now resolved, the new package will automatically be included on a configuration rebuild.

## How to update
Existing configurations with versions greater than 1.3.1 continue to work, **but we strongly recommend users to update, as this new version should vastly improve the Middleware's reliability**.

As always, updates can be rolled out by selecting the new version in the fiskaltrust.Portal and re-building the configuration. The updated Middleware instances will then automatically pull the new packages at the next startup.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Launcher v1.3.10_
- _fiskaltrust.Middleware.Queue.EF v1.3.10_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.10_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.10-rc1_
- _fiskaltrust.Middleware.SCU.DE.Swissbit v1.3.10_
- _fiskaltrust.Middleware.Helper.Helipad v1.3.10_
- _fiskaltrust.Middleware.SCU.DE.Epson v1.3.10-rc1_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.10-rc1_

## Next steps in the Middleware
We will continue to improve the stability of our Middleware in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
