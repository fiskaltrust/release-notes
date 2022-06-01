---
slug: /release-notes/middleware/1.3.34
title: Version 1.3.34
---

# fiskaltrust.Middleware 1.3.34 (Germany)
_June 01, 2022_

In this version of the Middleware, we've updated the Fiskal Cloud Connector and the DSFINV-K export. Additionnally we fixed an issue that occured when switching from a SwissbitCloud SCU to another.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Updated third party dependencies: Swissbit Cloud & Deutsche Fiskal

We've updated our dependency to the Fiskal Cloud Connector (used by the Deutsche Fiskal and the Swissbit Cloud SCUs) to version 4.0.2. The Middleware's behavior was not changed by this update. Users can update to the latest FCC version by updating to version 1.3.34 of the DeutscheFiskal or SwissbitCloud SCU - the update will be automatically installed.

:::

## Feature: update DSFINV-K export to the 2.3

Our DSFinV-K 2.3 export is now officially certified by the Audicon. It has been released to the production Portal last week, and can therefore be used immediately by all customers with Carefree packages in Germany.

## Bug fix: Switch from a SwissbitCloud SCU to another was not possible so far
We implemented a functionality that enables to deregister the ERS number from a SCU to be able to re-register to another when performing a switch from a SwissbitCloud SCU to another.

## Feature: Removal of the  Parameter 'additionalData' form Cryptovision SCU

When validating our receipts created with a Cryptovision TSE, the validation failed because we were including a parameter called "additionalData" in our calls to the TSE. We removed this parameter to avoid these failures. More information can be found in our documentation in the Download area of the portal.

## Affected packages

Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.31_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.31_
- _fiskaltrust.Middleware.SCU.DE.Cryptovision v1.3.30_

## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source and a first proof-of-concept can be found in the `proof-of-concept` branch of the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
