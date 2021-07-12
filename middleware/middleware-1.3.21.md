---
slug: /release-notes/middleware/1.3.21
title: Version 1.3.21
---

# fiskaltrust.Middleware 1.3.21 (Germany)
_July 13, 2021_

In this release, we've added the possibility to deactivate Queues and switch SCUs even in cases when the TSE is not reachable anymore. Additionally, we've further improved our DSFinV-K export after successfully receiving the [GoBD certification from Audicon](https://fiskaltrust.de/fiskaltrust-middleware-dsfinv-k-schnittstelle-jetzt-gobd-zertifiziert/), including using fallback master data, automatically resolving references over different days, and several stability improvements and fixes.

<div class="alert alert--warning" role="alert">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Feature: Deactivate Queues and switch SCUs when TSE is not accessible
After adding the possibility to switch SCUs (e.g. in case when users want to switch to a different TSE with the same Queue) in [version 1.3.19](middleware-1.3.19.md), we've further enhanced this feature to also work when the currently used TSE cannot be reached anymore. This can be useful in cases where a TSE was lost, broken or deactivated by mistake - or when the TSE's certificate expires in a few years.

The same functionality was also added to stop/out-of-operation receipts. **Please make sure to keep the Middleware running for at least 5 minutes after taking it out of service, so that the changes can be synced to the cloud (and appear in the Portal)**.

This feature is automatically active without requiring any implementation changes.

## Feature: Support fallback master data usage in DSFinV-K export
We've received the feedback from some of our users that the Middleware's and Portal's mechanisms to inject master data into the DSFinV-K export can be quite complex. Due to this, it could happen that the master data (e.g. company name, VAT ID, addresses, ...) were not properly added to the export sometimes. We've therefore updated this feature to enable the usage of _fallback data_ in case no actual master data is stored for the respective timeframe of the export. Additionally, we've improved our internal data flows to eliminate the vast majority of these cases for future deployments.

In case some parts of the master data tables of the DSFinV-K export are not properly populated, please follow these steps:
1. Make sure that the master data is correct in the PosOperator's Portal account
2. Update the Queue version to `>= 1.3.21`
3. Rebuild the Cashbox & restart the Middleware

## Feature: Automatically resolve DSFinV-K references over multiple days
Until now, the Middleware was only able to automatically resolve references (in `references.csv`) within a single day. While resolving references over multiple days was initially not planned, we were (rightly) informed that our documentation was very unclear about this topic, and several PosCreators assumed that we'd automatically resolve the references.

To improve the user experience of the Middleware and prevent requiring further implementation work, we've therefore implemented the following behavior:
- Receipts that have the same `cbReceiptReference` from previous days are automatically added to `references.csv`.
- Receipts that are referenced via `cbPreviousReceiptReference` are automatically added as well.

## Stability improvement: DSFinV-K export improvements
We've introduced several improvements into our DSFinV-K export, covering the following topics:
- On some machines, the DSFinV-K used the local system time instead UTC. We've changed this behavior to always using UTC.
- According to the DSFinV-K 2.2, values in the `STK_BR` column in `lines.csv` must not be negative (only `MENGE` can be). However, there are some cases in the Middleware's interface where it's required to send negative amounts - we've therefore updated the export to make sure these values are properly converted.
- The value of the `TERMINAL_SERIENNR` column in `slaves.csv` was changed to use the value of `cbTerminalId` (instead of the `CashboxIdentification`).
- The line endings of the files could differ between different OS; we now enforce the usage of `\r\n` to support all systems.

## Stability improvement: Generally improved error logging in SCUs
To be able to diagnose issues faster, we've added more extensive debug- and trace logging to our SCUs. Please make sure to [set the log verbosity](https://docs.fiskaltrust.cloud/docs/poscreators/middleware-doc/general/installation#launcher-configuration) either to `Debug` or `Trace` when collecting log files for our support. **When not actively diagnosing errors, the log verbosity should be set to "Information" to avoid rapidly growing log files.**

## Bug fix: Proxy settings were sometimes ignored when using Swissbit Cloud or Deutsche Fiskal TSEs
Due to an issue, the proxy settings made in _Swissbit Cloud_ and _Deutsche Fiskal_ were ignored in some cases. While the FCC could be initialized properly in these scenarios, it afterwards failed to start. After updating to 1.3.21, the affected Cashboxes should be startable without needing any further changes.

## Bug fix: High memory consumption and errors when uploading large datasets
We've fixed an issue where large datasets (e.g. large TAR files) could not be pushed to our cloud services, which lead to a memory leak in the library we use and ultimately to high memory consumption. If you are experiencing any memory issues, please consider performing this update.

The Helipad helper (the affected package) is automatically added to Cashboxes without requiring further actions. The latest version will be inserted when the Cashbox is rebuilt (no "manual" package updates in the Portal are required, therefore).

## Changed behavior: Strip ASN.1 header from public key in fiskaly TSEs
Unlike other TSE vendors, fiskaly doesn't only return the _public key_ in their service's responses, but wraps them into an ASN.1 header with additional metadata. As the format of the public key that needs to be printed onto the TSE is not specified by any legal standards, this behavior is technically okay - however, we've received feedback from our partners that auditors criticized this behavior during the first financial audits, or at least asked for more detailed explanations about the topic.

To simplify future audits, we've therefore altered our implementation to remove this ASN.1 structure and only return the actual content of the public key.

## Updated third party dependencies: Swissbit Cloud & Deutsche Fiskal
We've updated our dependency to the _Fiskal Cloud Connector_ (used by the _Deutsche Fiskal_ and the _Swissbit Cloud_ SCUs) to version 3.2.2. This update enables our users to benefit from bug fixes and improvements the TSE vendors implemented in the new versions. The regular Middleware behavior was not changed by this update.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.21_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.21_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.21_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.21_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.21_
- _fiskaltrust.Middleware.SCU.DE.CryptoVision v1.3.21_
- _fiskaltrust.Middleware.SCU.DE.Swissbit v1.3.21_
- _fiskaltrust.Middleware.SCU.DE.Fiskaly v1.3.21_
- _fiskaltrust.Middleware.Helper.Helipad v1.3.21_

## Next steps in the Middleware
As the upcoming, certified version of the fiskaly TSE will be released in a few days, we will make sure to properly test and then release our updated SCU as soon as possible afterwards. Additionally, we will provide templates for cash registers' process documentations (_Verfahrensdokumentationen_). As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
