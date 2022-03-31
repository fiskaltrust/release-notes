---
slug: /release-notes/middleware/1.3.31
title: Version 1.3.31
---

# fiskaltrust.Middleware 1.3.31 (Germany)
_March XX, 2022_

In this version of the Middleware, we've updated the Fiskal Cloud Connector (which is used by the _Swissbit Cloud_ and _Deutsche Fiskal_ SCUs). Additionally, we've resolved an issue in the Launcher that could lead to delayed processing of sign requests while journal requests were being executed concurrently.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Updated third party dependencies: Swissbit Cloud & Deutsche Fiskal
We've updated our dependency to the Fiskal Cloud Connector (used by the Deutsche Fiskal and the Swissbit Cloud SCUs) to version 4.0.1. The Middleware's behavior was not changed by this update. Users can update to the latest FCC version by updatin to version 1.3.31 of the _DeutscheFiskal_ or _SwissbitCloud_ SCU - the update will be automatically installed.

:::warning

Please note that FCC 4.0.1 is the first official FCC version running on the newest BSI certification. Due to BSI regulation, this version has to be installed not later than **July 31, 2022** due to the end of the certification for FCC 3.

:::

## Stability improvement: Delayd sign calls due to running journals
We've slightly changed the REST hosting implementation in the Launcher to make sure that calls to the _sign_ endpoint are always scheduled as quickly as possible, even if a call to the _journal_ endpoint is running at the same time. This change was made as the Helipad uploader (which uses the _journal_ endpoint) affected the sign performance for a small amount of installations. 

Please note that this change requires a rebuild of the CashBox and a re-download of the Launcher (i.e. the _fiskaltrust.exe_). If you're not affected by this issue, an update is not required.


## Affected packages

Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.31_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.31_
- _fiskaltrust.Launcher v1.3.31_
## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source and a first proof-of-concept can be found in the `proof-of-concept` branch of the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
