---
slug: /release-notes/middleware/1.3.33
title: Version 1.3.33
---

# fiskaltrust.Middleware 1.3.33 (Germany)
_April 26, 2022_

In this version of the Middleware, we've fixed an issue that could lead to failing requests when switching to another SCU. While the switch itself was successfully performed in these cases, the Middleware returned an error.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Bug fix: SCU switch was not possible in some cases
We've resolved an issue that lead to an error result when performing a SCU switch. While the switch itself was successfully performed in these cases, the Middleware returned an error instead of the anticipated result.

We highly recommend to update to this version before performing an SCU switch.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.SQLite v1.3.33_
- _fiskaltrust.Middleware.Queue.EF v1.3.33_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.33_

## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version is developed open-source and a first proof-of-concept can be found in the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to receive feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
