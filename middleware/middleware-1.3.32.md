---
slug: /release-notes/middleware/1.3.32
title: Version 1.3.32
---

# fiskaltrust.Middleware 1.3.32 (Germany)
_April 19, 2022_

In this version of the Middleware, we activated the Appinsight for the Android middleware application in order to collect logs and have a monitoring in place.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Feature: Appinsights has been activated for the Android application

The Appinsight for the Android middleware application enables to collect logs and have a monitoring in place.

:::

## Feature: update of the queue and master data

In case the PosSystems are empty in DSFinV-K, we´ve added a fallback-masterdata. This will ensure that data used during implementation will be used if some fields in the cloud export are empty.

## Feature: Content Provider has been added to the Android application

A content provider has been added to the Android,  in order to give the POS Creator/Dealers the posibility to access the logs from the middleware Android installations, meaning remotely..

## Affected packages

Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.31_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.31_
- _fiskaltrust.Launcher v1.3.31_
## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source and a first proof-of-concept can be found in the `proof-of-concept` branch of the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.