# fiskaltrust.Middleware 1.3.10 (Germany)

**We highly recommend updating to this version on POS Systems that uses SQLite Queues to resolve this issue.**

<div class="alert alert-warning" role="alert" style="border-radius: 0">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Bug fix: Wrong parameter sent to journal endpoint while uploading 

## Bug fix:  float types for MySQL entities

## Bug fix: Using float types for MySQL entities

## Bug fix: Exclude BonTypes from local DSFinV-K export

## Stability improvement: Fixed concurrency issues in Swissbit SCU

## New SCU: Epson (Sandbox)

## New SCU: DeutscheFiskal (Sandbox)

## How to update
Existing configurations with versions greater than 1.3.1 continue to work, **but we strongly recommend users to update to resolve this critical issue**.

As always, updates can be rolled out by selecting the new version in the fiskaltrust.Portal and re-building the configuration. The updated Middleware instances will then automatically pull the new packages at the next startup.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Launcher v1.3.10_
- _fiskaltrust.Middleware.Queue.EF v1.3.10_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.10_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.10-rc1_
- _fiskaltrust.Middleware.SCU.DE.Swissbit v1.3.10_
- _fiskaltrust.Middleware.Helper.Helipad v1.3.10_
- _fiskaltrust.Middleware.SCU.DE.Epson v1.3.10-rc1_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.10-rc1_

## Next steps in the Middleware
We will continue to improve the stability of our Middleware in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
