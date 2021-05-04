---
slug: /release-notes/middleware/1.3.19
title: Version 1.3.19
---

# fiskaltrust.Middleware 1.3.19 (Germany)
_May 4, 2021_

With this Middleware version, we added the possibility to switch the connected SCU for already started Queues. This change allows users of the Middleware to change the used TSE without having to create a new Queue. Additionally, we've included several important bug fixes in this update. 

<div class="alert alert--warning" role="alert">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Feature: Switch connected SCU without creating a new Queue


## Updated SCU: A-Trust

## Changed behavior: Fail-transaction-receipt executable in failed mode

## Changed behavior: Retrying on empty responses is now optional on CryptoVision

## Bug fix: Wrong TSE payload when transformed PayItems are used

## Bug fix: Improved time update precision in some SCUs

## Bug fix: Reading high number of started transactions fails on Diebold Nixdorf SCU

## Bug fix: Fixed wrong time format in DSFinV-K transaction table

## Bug fix: DSFinV-K threw exception when PayItem.Quantity was set to 0

## Bug fix: DSFinV-K cash payment table included wrong data

## Bug fix: Mono service could not be installed on some Linux versions

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.19-rc1 *_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.19-rc1 *_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.19-rc1 *_
- _fiskaltrust.Middleware.SCU.DE.CryptoVision v1.3.19_
- _fiskaltrust.Middleware.SCU.DE.DieboldNixdorf v1.3.19_
- _fiskaltrust.Middleware.SCU.DE.Epson v1.3.19_
- _fiskaltrust.Middleware.SCU.DE.Swissbit v1.3.19_
- _fiskaltrust.Launcher v1.3.19 **_

\* An RC version was released to be able to deliver the bug fixes quickly. After verifying the correct behavior together with our partners, the versions will be re-labeled to non-RC.

** Unlike regular package updates, this change requires a re-download of the Launcher from the Portal. The fiskaltrust.Launcher is currently not able to update itself.

## Next steps in the Middleware
We will continue to improve the stability of our Middleware in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
