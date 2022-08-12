---
slug: /release-notes/middleware/1.3.38
title: Version 1.3.38
---

# fiskaltrust.Middleware 1.3.38 (Germany)
_August 12, 2022_

In this version of the Middleware, we've updated the Fiskal Cloud Connector (FCC) to version 4.0.3 after previous versions stopped working due to an expired code-signing certificate in the TSE (please see our [blog post](https://fiskaltrust.de/wichtige-information-swissbit-cloud-ausfall/) and the [Deutsche Fiskal status page](https://deutschefiskal.statuspage.io/incidents/vyd0z587c9xb) for more details).

:::danger

If you're using either a SwissbitCloud or DeutscheFiskal TSE, please update to this version immediately to restore the functionality of the TSE. According to the TSE vendors, the previous versions of the FCC will not work anymore, and the update is mandatory.

Middleware instances that are using previous versions will not stop working in case the implementation is correct, but switch to the _failure mode_ that temporary disables the TSE communication (which e.g. also happens when the internet is disconnected when using a cloud TSE, or an USB TSE is unplugged). The POS system needs to send a zero-receipt to restore the TSE communication after the update was performed.

:::

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Updated third party dependencies: Swissbit Cloud & Deutsche Fiskal
We've updated the FCC to version 4.0.3 that was released today by the TSE vendor to re-enable the TSE, which was not working anymore with previous FCC versions due to an expired certificate in the SMAERS component of the TSE.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.38_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.38_


## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source, and our first public prototype can be found in the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
