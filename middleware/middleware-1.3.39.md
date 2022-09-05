---
slug: /release-notes/middleware/1.3.39
title: Version 1.3.39
---

# fiskaltrust.Middleware 1.3.39 (Germany)
_September 05, 2022_

In this version of the Middleware, we've fixed an out of memory bug where an exeception was thrown during the TAR export.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Bug Fix FCC Out of memory
We've fixed a bug happening during the TAR export where the FCC threw an out of memory exception. We made it possible to configure the heap memory via a scu parameter fccHeapMemory and chosen heap memory size 256, 512 or 1024.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.36_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.36_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.37_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.38_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.38_


## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source, and our first public prototype can be found in the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
