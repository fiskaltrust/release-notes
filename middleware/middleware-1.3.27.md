---
slug: /release-notes/middleware/1.3.27
title: Version 1.3.27
---

# fiskaltrust.Middleware 1.3.27 (Germany)
_December 20, 2021_

In this version of the Middleware, we updated the FCC used in the `SwissbitCloud` and `DeutscheFiskal` SCUs to protect against [Log4Shell](https://en.wikipedia.org/wiki/Log4Shell) exploits.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Improvement: FCC Update
We've update the FCC to version v3.2.4 which protects the FCC application against the Log4Shell exploits CVE-2021-44228 and CVE-2021-45046.

:::caution

Please update all `SwissbitCloud` and `DeutscheFiskal` SCUs to this version as soon as possible.

:::

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.27_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.27_

## Next steps in the Middleware
We will focus on development of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source and a first proof-of-concept can be found in the `proof-of-concept` branch of the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
