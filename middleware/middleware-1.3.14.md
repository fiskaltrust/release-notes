---
slug: /release-notes/middleware/1.3.14
title: Version 1.3.14
---

# fiskaltrust.Middleware 1.3.14 (Germany)
_February 17, 2021_

This quality-of-life update for the Middleware fixes multiple bugs, introduces stability improvements, and should enhance the overall user experience of the Middleware. Additionally, the MySQL Queue now officially left the RC status and is fully supported in production.

<div class="alert alert--warning" role="alert">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Production release: MySQL Queue
We've removed the _Release Candidate_ flag from our MySQL Queue, stating that it is now officially supported for production use cases. We'd like to thank all the partners who tested this package and provided highly valuable feedback.

## Changed behavior: Cancelling/Voiding receipts
We've updated the behavior of the Middleware to more precisely reflect the cancellation requirements described in the DSFinV-K. Previously, sending the _reverse/voided receipt_ ftRecreiptCaseFlag (`40000`) led to the BON_TYP `AVBelegStorno` - however, this type should not be used anymore in case a TSE is used (which probably applies to 99.9% of all cases). Therefore, we've changed the Middleware behavior: 
- Sending this flag now does not alter the type of the receipt anymore, i.e. a _Beleg_ stays what it is (and does not turn into a _AVBelegStorno_). 
- The flag is now only used for the `BON_STORNO` column while generating the DSFinV-K export.

**Known issue**: This change is not yet reflected in the local DSFinV-K export (which can be queried via the _Journal_ endpoint). However, the data is stored correctly, and a backwards-compatible export will be included in version 1.3.15.

## Changed behavior: DSFinV-K receipt referencing
We've updated our DSFinV-K generation logic to now include a broader variety of different receipt connections into the allocation groups (i.e. "Abrechnungskreis") part of the export. This file now includes one entry for each of the following connections:
- `cbPreviousReceiptReference`
- `cbReceiptReference`
- `cbArea`

This means that no matter which approach our partners use to connect receipts, the connections will now be made visible in the export. This behavior is backwards-compatible and generates correct exports for previously transmitted receipts as well.

## Stability improvement: DSFinV-K export with old data
While introducing the previous change, we generally improved the stability of our DSFinV-K export to be more compatible with older queues. This should fix several rare issues users were experiencing when querying exports (e.g. missing files).

## Bug fix: Wrong item delimiter sent to TSE for info-order receipts
When signing info-orders (which are treated as `Bestellung-V1` on the TSE) with more than one ChargeItem, the Middleware used a wrong item delimiter when generating the TSE payload - instead of `\r`, `\n` was used. As this is only a formal issue, the content of the data was still correctly signed.

This is now resolved, and the correct delimiter is used. Generating the DSFinV-K is not affected by this change.

## Bug fix: It was technically possible to operate a stopped Queue
Due to an issue in the Middleware, it was technically still possible to send receipts to a stopped Queue. However, since the TSE is usually deactivated in this case (if the respective flag is not used), this could lead to exceptions.

With this fix, the Queue now correctly responds with the _ftState_ `0x4445000000000001` after it was deactivated, and doesn't contact the SCU and therefore the TSE anymore.

## Bug fix: Launcher sometimes fails to start when operations take too long
Due to a default limitation in Windows services, services must not take more than 30 seconds to start, otherwise they'll be flagged as "not responding" by Windows. This issue infrequently happens with components that need to download 3rd party components during the first initialization (e.g. Swissbit Cloud/Deutsche Fiskal), which may take more than 30 seconds with slow internet connections.

This issue is now resolved, as the Launcher automatically requests more startup time starting from this version.

## Bug fix: Diebold Nixdorf SCU throws exception during self test
Due to unexpected behavior of Diebold Nixdorf TSEs with older firmware versions, the Middleware could run into issues when querying the TSE's current state details. As this operation is executed frequently during the self test of the TSE, this could lead to recurrent issues.

The Middleware was updated to be compatible with the respective firmware versions.

## Dependency update: Fiskal Cloud Connector v3 (Swissbit Cloud & Deutsche Fiskal)
On February 15, version 3.0 of the _Fiskal Cloud Connector_ was released. This 3rd party background service is required both by the Swissbit Cloud and the Deutsche Fiskal Cloud TSEs, as it contains their local SMAERS application (and is therefore part of the TSE). When using the respective SCUs with versions >= 1.3.14, version 3 is automatically installed and initialized.

Due to this change, Middleware instances using Swissbit Cloud SCUs now don't require Admin privileges anymore (unless e.g. an Admin port range is used, etc.). However, to automatically add the required Firewall exceptions, Admin privileges are still required. These Firewall exceptions can also be set manually, or - in user mode - via the respective popup. Please refer to our [documentation](https://docs.fiskaltrust.cloud/docs/product-description/germany/products-and-services/caas/features/basics/tse/swissbit-cloud) for more details.

<div class="alert alert--warning" role="alert">Due to regulatory reasons caused by the updated TR-03153 certifications of Swissbit Cloud and Deutsche Fiskal TSEs, it's <b>not possible to update existing installations that are currently using v2 FCCs</b>. This only affects a very small amount of our partners, whom we will directly contact in the next days. SCUs that were not rolled our yet are not affected by this problem and have been automatically updated to use the latest FCC version.</div>

## User experience improvement: Clear error message in case VC++ is not installed (Swissbit)
On some Windows version, the Swissbit Hardware TSE library (which is internally used by our Middleware) requires the installation of the _Visual Studio C++ Redistributable for Visual Studio 2015_. We've improved the error message that is thrown in case this dependency is not installed to give our partners the opportunity to more easily diagnose the issue, and also updated our [documentation](https://docs.fiskaltrust.cloud/docs/product-description/germany/products-and-services/caas/features/basics/tse/swissbit#troubleshooting).

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.14_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.14_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.14_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.14_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.14_
- _fiskaltrust.Middleware.SCU.DE.Swissbit v1.3.14_
- _fiskaltrust.Middleware.SCU.DE.DieboldNixdorf v1.3.14_
- _fiskaltrust.Middleware.SCU.DE.Fiskaly v1.3.14-rc1_
- _fiskaltrust.Launcher v1.3.14_

## Next steps in the Middleware
We will continue to improve the stability of our Middleware in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
