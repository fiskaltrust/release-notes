---
slug: /release-notes/middleware/1.3.16
title: Version 1.3.16
---

# fiskaltrust.Middleware 1.3.16 (Germany)
_March 12, 2021_

We're happy to announce that the fiskaly SCU is now available in our production systems (please see our [blog post](https://fiskaltrust.de/news/aktueller-status-zur-cloud-tse-202103/) for more details). Additionally, we've added a new signature that contains the TSE certification ID and (if required) information about the state of the certification and operational environment regulations. Finally, this version contains some bug fixes and usability improvements for the Middleware.

<div class="alert alert--warning" role="alert">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Production release: fiskaly SCU
In close collaboration with our partners, we've released the fiskaly SCU to production. To fulfill the legal requirements, we followed fiskaly's advice and added the informational phrase _"TSE in Evaluierung"_ ("TSE in evaluation") into the newly added certification identification signature item (see below). Please keep in mind that the fiskaly TSE is still in evaluation, and switching to the certified state will require an update of the SCU. Please refer to our [blog post about the state of cloud TSEs](https://fiskaltrust.de/news/aktueller-status-zur-cloud-tse-202103/) for more details.

## New signature item: Certification identification
We've added an additional signature item to the receipt response of POS receipts that contains the certification identification of the used TSE (e.g. `BSI-K-TR1234-5677`), and additionally contains a hint about the current state of the certification process or the operational environment. The _ftSignatureType_ of the newly added item is `0x4445000000000022`, more information can be found [here](https://docs.fiskaltrust.cloud/docs/poscreators/middleware-doc/germany/reference-tables/ftsignaturetype).

The signature item was added for all TSEs, including hardware devices. Currently, additional information is displayed for the three cloud SCUs that are available in our production systems:

| **SCU**                                      | **Certification identification**    |
|----------------------------------------------|-------------------------------------|
| fiskaltrust.Middleware.SCU.DE.Fiskaly        | BSI-K-TR-0403 [TSE in Evaluierung]  |
| fiskaltrust.Middleware.SCU.DE.SwissbitCloud  | BSI-K-TR-0456-2021 [USK ausgesetzt] |
| fiskaltrust.Middleware.SCU.DE.DeutscheFiskal | BSI-K-TR-0457-2021 [USK ausgesetzt] |

## Stability improvement: Fiskal Cloud Connector
We've updated our hosting of the _Fiskal Cloud Connector_ (FCC). This background service that is required by _Deutsche Fiskal_ and _Swissbit Cloud_ TSEs is automatically downloaded, initialized and started by our Middleware. However, we did not handle some initialization errors, leading to confusing errors for our users. We've changed the behavior so that the SCU now throws an exception and stops at startup time in case the FCC cannot initialized properly. If this happens, the error logs of the FCC are now printed into the console/our log file, allowing easier error diagnostics.

In addition, we've changed the default directory for the FCC installation from `%appdata%/fiskaltrust/FCC` to our regular service folder. As the Middleware now uses the package installation for both Deutsche Fiskal and Swissbit Cloud (introduced in [1.3.14](middleware-1.3.14.md)), binding instances to users is not required anymore. This  should make testing and installing the FCC with different/default service users easier. **Existing installations are not affected by this change and continue to work.**

## Compatibility improvement: Fiskal Cloud Connector on Linux
During the last two weeks, our partners informed us that the FCC could not be successfully installed on some Linux distributions without manually making some files executable. We have changed this behavior so that no manual action is needed anymore when setting up a _Swissbit Cloud_ or a _Deutsche Fiskal_ TSE on Linux.

## Bug fix: Deleting logs on fiskaly TSEs
To ensure equal functionality in all our TSE implementations, we've updated our fiskaly SCU to now mark logs that have been exported during a daily closing receipt as deleted. This resolves two issues:
- Previously, the fiskaly SCU always did a full export when daily-closing receipts were processed, and stored the results in the database. When a range-based `/Journal` export of those TAR files was called, the response could hence include more logs than requested. 
- Due to the full export, the duration of daily-closing receipts on fiskaly SCUs increased with each processed transaction, ultimately making the process very slow when many transactions were performed. 

Summarized, the fiskaly SCU now behaves as our other TSE implementations and only exports TAR logs that were generated since the last daily-closing receipt. However, there's one exception: similar to the behavior of the hardware TSEs in the case of open transactions, it's not possible to mark any transactions as deleted; the open transactions need to be closed first.

## Stability improvement: Add flag to ignore transaction mismatches at daily-closing receipts
In rare cases (e.g. due to power or network failures), TSE transactions could be marked as finished on the TSE, but the Middleware still kept them open in our internal database. As these "open" transactions must be closed before a daily-closing receipt can be executed, this effectively blocked the Middleware from performing this special receipt.

To resolve this problem, we've introduced the _ftReceiptCaseFlag_ `0x0000000020000000` (as described [here](https://docs.fiskaltrust.cloud/docs/poscreators/middleware-doc/germany/reference-tables/ftreceiptcase#ftreceiptcaseflag)). When this flag is sent with the daily-closing receipt, the Middleware will check if transactions that are marked open in our database are actually open in the TSE; if this is the case, a journal entry is made and the database is updated.

**Please note that this flag shouldn't be used per default, as it may hide power configuration issues or network problems that lead to incomplete DSFinV-K exports**. However, it may be useful in these cases to unblock users of cash registers in case this scenario occurred.

## Stability improvement: Middleware service startup
We've added a startup dependency to Windows' `HTTP` service to the service installation of the Middleware. This change should resolve rare cases where the Middleware and other Windows services seemed to block each other during startup, as it ensures that the HTTP service is started before the Middleware runs.

## Usability improvement: Error message when Visual Studio C++ Redistributable is not installed (Swissbit SCU)
In a previous version, we've introduced a more helpful warning message in case the Visual Studio C++ 2015 Redistributable isn't installed and the Swissbit SCU fails to start due to this dependency in Swissbit's library. However, the notification was not displayed on all systems, which now should be be the case anymore.

## Bug fix: Local DSFinV-K generation does not include the latest voiding/cancellation changes
We've fixed the known issue from Middleware 1.3.14, so that the DSFinV-K now properly displays the _BON_TYP_ and the _BON_STORNO_ according to the changes made in the previous version.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.16_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.16_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.16_
- _fiskaltrust.Middleware.SCU.DE.Fiskaly v1.3.16_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.16_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.16_
- _fiskaltrust.Middleware.SCU.DE.Swissbit v1.3.16_
- _fiskaltrust.Middleware.SCU.DE.DieboldNixdorf v1.3.16_
- _fiskaltrust.Launcher v1.3.16_

## Next steps in the Middleware
We will continue to improve the stability of our Middleware in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
