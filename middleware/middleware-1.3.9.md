---
slug: /release-notes/middleware/1.3.9
title: Version 1.3.9
---

# fiskaltrust.Middleware 1.3.9 (Germany)
_October 6, 2020_

In this version, we published an important fix for the TSE _.tar_ file export, both in the Queue and the SCU packages. This resolves a critical issue where customers with pre-existing Queues were not able to properly execute daily-closing receipts anymore.

**We highly recommend updating to this version on POS Systems that use version 1.3.8 to resolve this issue.**

<div class="alert alert--warning" role="alert">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Bug fix: Resolve .tar file export issues during daily-closing receipt
Since the previous version (1.3.8), the Middleware automatically export the TSE's _.tar_ files during the daily-closing receipt. Unfortunately, due to a communication issue between Queue and SCU, this export was executed far slower than expected - which in some cases completely prevented the creation of a daily-closing receipt when TSEs already contained too many transactions. In other cases, the daily-closing receipt took an intolerable amount of time.

With this version, we drastically increased the communication speed when querying the _.tar_ export, which resolves this issue in our test scenarios. 

We also improved our internal device locking to prevented some race conditions some customers were experiencing, which could lead to issues both while signing receipts and especially while creating _.tar_ exports.

An email was sent out to POS Creators and POS Dealers to inform them about this cause. We'd like to use this opportunity to again apologize for any inconvenience this may caused our customers, and have introduced internal measures to avoid issues like this propagating to our production systems in the future.

## New SCU: ATrust (Sandbox)
After implementing the ATrust Cloud SCU we are making it available on the sandbox for early adopters. Since the ATrust TSE is not certified yet, it won't be available in production yet.

## How to update
Existing configurations with versions greater than 1.3.1 continue to work, **but we strongly recommend users to update to resolve this critical issue**.

**Version 1.3.8 should not be used anymore.**

As always, updates can be rolled out by selecting the new version in the fiskaltrust.Portal and re-building the configuration. The updated Middleware instances will then automatically pull the new packages at the next startup.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.9_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.9_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.9-rc1_
- _fiskaltrust.Middleware.SCU.DE.CryptoVision v1.3.9_
- _fiskaltrust.Middleware.SCU.DE.Swissbit v1.3.9_
- _fiskaltrust.Middleware.SCU.DE.DieboldNixdorf v1.3.9_
- _fiskaltrust.Middleware.SCU.DE.ATrust v1.3.9-rc1_

## Next steps in the Middleware
We will continue to improve the stability of our Middleware in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
