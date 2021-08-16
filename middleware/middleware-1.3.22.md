---
slug: /release-notes/middleware/1.3.22
title: Version 1.3.22
---

# fiskaltrust.Middleware 1.3.22 (Germany)
_August 16, 2021_

In this version of the Middleware, we have added support for the certified version 2 of the fiskaly Cloud TSE. Additionally, some minor issues in the DSFinV-K related to transformed PayItems were resolved, and we've introduced a mechanism to reduce the Middleware's memory consumption in some scenarios.

<div class="alert alert--warning" role="alert">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Feature: Support for the certified fiskaly Cloud TSE
The Middleware now supports version 2 of the fiskaly Cloud TSE. As this is the first certified version - which means that previously existing v1 installations need to migrate to v2 -, we've introduced a new package name to avoid confusion about which version is installed.

To use the fiskaly Cloud TSE v2, the new package `fiskaltrust.Middleware.SCU.DE.FiskalyCertified` must be used. This package does not support version 1 TSEs, which still can be used with the old `fiskaltrust.Middleware.SCU.DE.Fiskaly` package while preparing the migration.

:::tip

Due do legal regulations by fiskaly, existing TSEs can not be migrated to version 2, but new TSEs have to be created. Our objective is to make this switch as easy as possible, and we're in close contact with our partners and fiskaly to achieve this goal. A migration guide and some automation in the Portal will be released soon.

:::

## Stability improvement: Fiskaly v1 client update
We've updated the fiskaly client packages in our `fiskaltrust.Middleware.SCU.DE.Fiskaly` SCU, which should lead to increased stability and performance. While we strongly recommend switching to legally compliant v2 TSEs, we've introduced this (most likely last) update into our v2 SCU to hopefully reduce some instabilities our partners have been experiencing in the last weeks.

## Stability improvement: Automatically clean up memory after cloud uploads
As we're using .NET for our products, cleaning up memory manually is usually not required. However, some of our partners noticed increasing memory consumption by the Middleware, which (according to our investigations) are caused by fragmentation of the _Large Object Heap_ (LOH). Unlike other objects, the LOH is not compacted automatically ([only under specific circumstances](https://docs.microsoft.com/en-us/dotnet/standard/garbage-collection/large-object-heap#when-is-a-large-object-collected)). As some objects in the German Middleware tend to be large enough to end up in the LOH, this could lead to a fragmented LOH over time in some situations.

We've altered our HelipadUpload helper, which automatically runs each 5 minutes to upload data, to compact and collect the LOH after each upload. As this is an asynchronous process, the performance of the Middleware is not impacted by this change.

## Bug fix: Amount and quantity were not converted correctly to DSFinV-K business cases in some edge cases
We've altered our DSFinV-K implementation, as the amount and quantity was not correctly transformed from _PayItems_ in some rare use-cases. The issue should now be resolved, this change is backwards-compatible to existing data.

## Updated third party dependencies: Swissbit Cloud & Deutsche Fiskal
We've updated our dependency to the _Fiskal Cloud Connector_ (used by the _Deutsche Fiskal_ and the _Swissbit Cloud_ SCUs) to version 3.2.2. This update enables our users to benefit from bug fixes and improvements the TSE vendors implemented in the new versions. The regular Middleware behavior was not changed by this update.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.21_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.21_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.21_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.21_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.21_
- _fiskaltrust.Middleware.SCU.DE.CryptoVision v1.3.21_
- _fiskaltrust.Middleware.SCU.DE.Swissbit v1.3.21_
- _fiskaltrust.Middleware.SCU.DE.Fiskaly v1.3.21_
- _fiskaltrust.Middleware.Helper.Helipad v1.3.21_

## Next steps in the Middleware
As the upcoming, certified version of the fiskaly TSE will be released in a few days, we will make sure to properly test and then release our updated SCU as soon as possible afterwards. Additionally, we will provide templates for cash registers' process documentations (_Verfahrensdokumentationen_). As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
