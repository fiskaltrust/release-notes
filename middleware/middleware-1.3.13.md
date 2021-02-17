---
slug: /release-notes/middleware/1.3.13
title: Version 1.3.13
---

# fiskaltrust.Middleware 1.3.13 (Germany)
_January 22, 2021_

This version of the Middleware fixes two issues in the Launcher that affected users with specific configurations.

<div class="alert alert--warning" role="alert">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Bug fix: Memory leak when using very large Cashbox configurations
Due to an issue in the Launcher, loading very large configurations could lead to memory leaks, and thus ultimately to a crashing Launcher _at startup_. This issue only occurred when many packages Queues and SCU were used in a single Cashbox, and doesn't affect the runtime behavior after the startup phase.

The memory leak was removed, and the Launcher now consumes normal amounts of memory, no matter how many components are used in one Cashbox.

## Bug fix: Misleading warning message during installation
In case a specific order of parameters was used during the Windows Service installation of the Middleware, a warning was printed that stated that the installation was not successful. While this wasn't actually the case, the warning was highly misleading, and the behavior is now fixed.


## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

The latest Launcher version cannot be selected in the Portal, but is automatically included after a rebuild and manual re-download.

- _fiskaltrust.Launcher v1.3.13_

## Next steps in the Middleware
We will continue to improve the stability of our Middleware in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
