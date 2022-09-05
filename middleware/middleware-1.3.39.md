---
slug: /release-notes/middleware/1.3.39
title: Version 1.3.39
---

# fiskaltrust.Middleware 1.3.39 (Germany)
_September 05, 2022_

In this version of the Middleware,we made it possible to run the German middleware on an ARM device, we've also fixed a bug concerning Fail-transactions not removing the failed start transactions on the FailedStartTransaction table in the database.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Feature: ARM support for the German middleware
We now offer support for customers using ARM devices and wish to implement our German middleware. These are the configuration working on ARM devices :
- SQLITE
- Swissbit hqrdware TSE
- SwissbitCloud TSE


## Bug Fix Explicit fail-transaction-receipt doesn't remove failed start transactions
We´ve solved a bug where in some cases the Fail-transaction receipt did not remove the failed start transactions from the FailedStartTransaction table in the database, resulting in an exception thrown.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.36_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.39_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.37_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.38_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.39_


## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source, and our first public prototype can be found in the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
