---
slug: /release-notes/middleware/1.3.30
title: Version 1.3.30
---

# fiskaltrust.Middleware 1.3.30 (Germany)
_March 18, 2022_

In this version of the Middleware, we've added the possibility to declare a 'Master Queue' if there are multiple Queues connected to one TSE, in order to avoid long timeouts during daily closings and have one tar file export for all queues.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Feature: Possibility to enable a 'Master Queue' for TAR file export

When setting up the parameter `EnableTarFileExport`, there is a possibility to select one queue which will be responsible for the daily closing and Tar file export.
This can be achieved by setting the new parameter to `false` for the non-master Queues.

:::info

If multiple Queues use the same TSE the TAR file from the TSE will only end up in the POSArchive of the 'Master Queue' which triggered the export, given that queue has an active POSArchive subscription.

:::

## Bug Fix: CryptoVision execption about data fragmentation on transport layer

The source of the exception about data fragmentation on transport layer has been identified and corrected.

## Bug Fix: Cryptovision timeout when downloading TAR file

We fixed a bug happening during Tar files export with a TSE failed with a timeout error.
This bug only occurred when very large TAR files were exported, and only affected a small subset of users.

:::info

Please note that exports may take noticably longer in these cases, as the Middleware falls back to a slower export method. The duration of normally-sized exports is not increased.

:::


## Updated third party dependencies: Swissbit Cloud & Deutsche Fiskal

We've updated our dependency to the Fiskal Cloud Connector (used by the Deutsche Fiskal and the Swissbit Cloud SCUs) to version 3.2.5. This update enables our users to benefit from bug fixes and improvements the TSE vendors implemented in the new versions. 
The regular Middleware behavior was not changed by this update.

## Affected packages

Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.SQLite v1.3.30_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.30_
- _fiskaltrust.Middleware.Queue.EF v1.3.30_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.30_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.30_
- _fiskaltrust.Middleware.SCU.DE.CryptoVision v1.3.30_

## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source and a first proof-of-concept can be found in the `proof-of-concept` branch of the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
