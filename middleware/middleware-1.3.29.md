

---
slug: /release-notes/middleware/1.3.29
title: Version 1.3.29
---

# fiskaltrust.Middleware 1.3.29 (Germany)
_March 8, 2022_

In this version of the Middleware, we now automatically clear up old tar files in the `fiskaltrust/service/Exports/` folder.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Feature: Automatically cleanup temporary files in the service folder

Temporary files in the `fiskaltrust/service/Exports/` folder are now automatically cleaned after they're no longer needed. Unneeded tmp files will also be cleaned up at startup.

There is a new queue configuration parameter `StoreTemporaryExportFiles` which can be set in the portal for all queues. The default is `false` and can be set to `true` to keep temporaty export files.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.SQLite v1.3.29_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.29_
- _fiskaltrust.Middleware.Queue.EF v1.3.29_

## Next steps in the Middleware
We will focus on reducing disk space used by the fiskaltrust.Middleware in the next sprints and continue development of the next version of the fiskaltrust.Launcher https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
