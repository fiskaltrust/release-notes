---
slug: /release-notes/middleware/1.3.40
title: Version 1.3.40
---

# fiskaltrust.Middleware 1.3.40 (Germany)
_September 26, 2022_

In this version of the Middleware, we have added a SCU parameter to configure the Heap memory of the FCC, we also have added a timeout command for Entity Framework queue to perform a migration, we have modified the DSFINV-K export to exclude non pos-receipts, we have created some modi for the TAR-Export and we have fixed bugs regarding failing TAR-Export using a Fiskaly SCU and a bug concerning the indexes creation.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Feature: Heap memory is now configurable for DeutscheFiskal and SwissbitCloud SCUs
We made it possible to configure the heap memory thanks to an optional SCU parameter called `SetFccHeapMemory` with the following values 256, 512, 1024 for DeutscheFiskal and SwissbitCloud SCUs.
### Affected packages:
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.40_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.40_

## Feature: Excluding non pos-receipts in DSFINV-K export
We have modified the DSFINV-K export so that non pos-receipts (e.g. zero receipt, daily or monthly closing receipt...) are not part of it, anymore. It should create lighter databases and save memory and CPU cycle.
### Affected packages:
- _fiskaltrust.Middleware.Queue.EF v1.3.40_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.40_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.40

## Feature: EF timeout command configurable for migration
We have made possible to configure the timeout duration for EF queue to perform a migration. In some cases when performing a migration for a big EF queue the default timeout was not long enough leading to some errors.
### Affected packages:
- _fiskaltrust.Middleware.Queue.EF v1.3.40_

## Feature: TAR export modi for the queue
We have added several TAR export modi for the queue for the TAR-File export during the daily closing to avoid a growth of the database due to open transactions. We noticed that more and more database size were increasing leading to issues in terms of perfomance and data upload.To solve this issue we implemented a queue parameter allowing to configure different modi for the TAR-File export:
- all, this modi enables the automatic TAR-File export from the TSE on the queue
- none, this modi disables the automatic TAR-File export
- erased, this modi works in a way that TAR-files are only exported and saved when they can be deleted from the TSE. 
### Affected packages:
- _fiskaltrust.Middleware.Queue.EF v1.3.40_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.40_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.40

## Bug Fix: Fiskaly TAR export failure 
We´ve solved a bug where in some cases either a bad gateaway or a timeout error message was thrown when performing a TAR export while using a Fiskaly SCU, to avoid this, we added an automatic retry.
### Affected packages:
- _fiskaltrust.Middleware.SCU.DE.Fiskaly v1.3.40_

## Bug Fix: Index creation when they do not exist 
We´ve fixed a bug where an error message was thrown when updating the middleware version because the indexes already existed. We modified the index creation so that it only happens if the indexes do not exist. 
### Affected packages:
- _fiskaltrust.Middleware.Queue.SQLite v1.3.40

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.40_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.40_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.40
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.40_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.40_
- _fiskaltrust.Middleware.SCU.DE.Fiskaly v1.3.40_

## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source, and our first public prototype can be found in the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
