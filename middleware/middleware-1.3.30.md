---
slug: /release-notes/middleware/1.3.30
title: Version 1.3.30
---

# fiskaltrust.Middleware 1.3.30 (Germany)
_March 17, 2022_

In this version of the Middleware, we've added the possibility to declare a 'Master Queue' if there are multiple Queues connected to one TSE, in order to avoid long timeouts during daily closings and have one tar file export for all queues.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Feature: Possibility to enable a 'Master Queue' for TAR file export

When setting up the parameter `EnableTarFileExport`, there is a possibility to select one queue which will be responsible for the daily closing and Tar file export.

## Bug Fix: CryptoVision execption about data fragmentation on transport layer

The source of the exception about data fragmentation on transport layer has been identified and corrected.

## Bug Fix: Cryptovision timeout when downloading TAR file

We fixed a bug happening during Tar files export with a TSE failed with a timeout error.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.SQLite v1.3.29_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.29_
- _fiskaltrust.Middleware.Queue.EF v1.3.28_

## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source and a first proof-of-concept can be found in the `proof-of-concept` branch of the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
