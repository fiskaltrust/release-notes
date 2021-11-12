---
slug: /release-notes/middleware/1.3.25
title: Version 1.3.25
---

# fiskaltrust.Middleware 1.3.25 (Germany)
_November 12, 2021_

In this version of the Middleware, we added the possibility to update the firmware of Swissbit TSEs. Additionally, some minor issues in the DSFinV-K were resolved and we improved logging for the Fiskal Cloud Connector.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Feature: Update of the Swissbit TSE firmware
We've implemented the functionality to automatically update the Swissbit TSE firmware. To enable this functionality set the _EnableFirmwareUpdate_ SCU config parameter to `true`.

:::danger

When enabled the update is performed at startup of the Middleware and can take up to 10 minutes. Do not shutdown the Middleware or disconnect the TSE during the update.

:::

## Bux Fix: SCU switch was failing due to unread Portal configuration in some cases
The Middleware was unable to read SCU switch configurations from the Portal in some rare cases, mostly when the Queue was put into failed mode while the configuration was being changed with a specific order and timing. This could lead to the following error message, altough the SCU switch was properly configured in the Portal:
> _The SCU switch must be initiated properly in the fiskaltrust.Portal before sending this receipt. See https://link.fiskaltrust.cloud/market-de/scu-switch for more details._

This issue has been resolved.

## Bux Fix: Amount and quantity were not converted correctly to DSFinV-K business cases in some edge cases
We've altered our DSFinV-K implementation, as the amount and quantity were not correctly transformed in some rare use-cases.
In some cases the payload was also incorrectoy calculated.

The issue should now be resolved, this change is backwards-compatible to existing data.

## DSFinV-K improvement: Populate `UST_BESCHR` field in `vat.csv` for different 0% tax classes
We now populate the `UST_BESCHR` field in the `vat.csv` file of the DSFinV-K Export for the different 0% tax classes to ease the tax autiding process.

## Stability improvement: Added warning messages for possibly wrong FccDirectories
If we detect a mismatch between the `FccDirectory` from the configuration and the FCC-Directory from the `run_fcc.bat` we log a warning message. This should simplify error detection when e.g. the service folder or the FCC directory is changed without adjusting the `run_fcc.bat`.

## Stability improvement: Reduced memory consumption of Helipad helper when uploads fail
Due to an issue in the HelipadHelper, memory consumption could increase unexpectedly in case the regular data uploads were failing to our services, e.g. due to an internet outage or server errors. This issue only occured to a small percentage of users and has been resolved. As the Helipad helper package is automatically added to CashBoxes, rebuilding configurations will automatically add the latest version without further actions required.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.25_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.25_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.25_
- _fiskaltrust.Middleware.SCU.DE.Swissbit v1.3.25_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.25_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.25_
- _fiskaltrust.Middleware.Helper.Helipad v1.3.25-rc2_

## Next steps in the Middleware
We will focus on development of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed opensource and a first proof-of-concept can be found in the `proof-of-concept` branch of the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
