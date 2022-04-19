---
slug: /release-notes/middleware/1.3.32
title: Version 1.3.32
---

# fiskaltrust.Middleware 1.3.32 (Germany)
_April 19, 2022_

In this version of the Middleware, we've improved the overall logging experience on Android by enabling cloud logging and adding a content provider to directly access log files even if the Middleware cannot be started.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Feature: Content Provider has been added to the Android application
A content provider has been added to the Middleware for Android, which should enable users to download log files even if the Middleware cannot be started. We've also extended our [Android samples](https://github.com/fiskaltrust/middleware-demo-android/blob/master/xamarin/MainActivity.cs#L206) to demonstrate the usage of this new feature.

## Feature: Application Insights has been activated for the Android Middleware
We've enabled Application Insights for the Android Middleware app, which enables us to offer cloud CashBox monitoring in the Portal for Android instances.

## Feature: Use fallback PosSystems in DSFinV-K
In case no PosSystems are set in the current master data configuration, the DSFinV-K export now falls back to all PosSystems connected to the operator's account. This will ensure that data used during implementation will be used if some fields in the cloud export are empty.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.SQLite v1.3.32_
- _fiskaltrust.Middleware.Queue.EF v1.3.32_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.32_

## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version is developed open-source and a first proof-of-concept can be found in the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
