---
slug: /release-notes/middleware/1.3.24
title: Version 1.3.24
---

# fiskaltrust.Middleware 1.3.24 (Germany)
_October 15, 2021_

In this quality-of-life release of the Middleware, we resolved several issues that were occurring for segments of our users, and introduced multiple stability improvements to further improve the behavior of the Middleware during implementation and runtime.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Bug fix: FCC update failed when service folder is set to a different drive
Due to an issue in the recently added update process for the Fiskal Cloud Connector (the 3rd part dependency used by the _Swissbit Cloud_ and _Deutsche Fiskal_ SCUs), the FCC update was not successful when switching to SCU package version 1.3.23. FCC installations were not damaged by this failure, as it occurred before the actual update took place. The issue has been resolved, and the FCC will be properly updated when upgrading to SCU versions >= 1.3.24.

## Bug fix: Configuration upload failed when a Queue was put into a different Cashbox
When a Queue was put into a different Cashbox (e.g. when large Cashboxes are split up due to performance reasons), the Middleware mistook this change as a forbidden configuration update, which lead to blocked uploads of the configuration data (e.g. the Queue's status). Relevant receipt data was not affected by this and properly uploaded, but some convenience features in our Portal were blocked by this issue (e.g. viewing the Queue state). Due to our retry mechanisms, the configuration data will be uploaded as soon as the Queue version is updated and rolled out.

:::tip

Please note that installing an already running Cashbox on a different machine is not possible without further steps. The scenario described above only applies to situations where the Queue was put into another Cashbox that is then running on the _same_ machine.

:::

## Bug fix: TAR export via the API failed on some Linux distributions
We've received reports about an issue that lead to failing TAR exports on some Linux distributions due to a missing dependency. The issue has been resolved.

## Bug fix: Large numbers were incorrectly formatted in TSE process data
We've resolved an issue in the Middleware that could lead to incorrectly formatted TSE process data in some rare cases when the overall amount of a single receipt exceeded € 1000. Due to this error, a thousand separator was inserted, although this is not provided for in the DSFinV-K. 

## Bug fix: SCU switch was not working in BYODC installations
Due to an issue in our _Bring your own DataCenter_ solution, SCU switch operations could not be executed in some scenarios, leading to errors during the process. We've resolved this issue and further increased the systems stability to prevent similar errors in the future.

## Bug fix: FileUploadHelper failed to upload data on legacy OSs
We've resolved an issue where the FileUploadHelper used an outdated TLS version on legacy Operating Systems like Windows Server 2008, which lead to failing data uploads.

## Stability improvement: Added clear error messages for deleted fiskaly v2 test TSEs
Due to fiskaly's practice of deleting version 2 test TSEs weekly (each Sunday), many of our users who were not aware of this practice got confused by the fact that their Middleware test instances stopped working after each weekend. We've improved the log messages and errors the Middleware displays in this case to reduce the investigation effort to detect this issue for new users.

## Stability improvement: Improved Android lifecycle management
We've received note that some Android devices tend to kill the Middleware Launcher when running into low memory or battery scenarios. While this is a valid scenario for Android apps, our Middleware was unable to recover from this situation without a manual full restart of the service. 

We've improved the overall lifecycle handling of the underlying Android service, so that the App is now able to automatically recover when the service is killed by the Android OS. Additionally, we've added improved logging and simplified our service management to enhance the Developer experience when implementing and testing the Middleware on Android.

## Documentation: Improved process documentation for DSFinV-K exports
We've received and incorporated some feedback about the DSFinV-K process documentation templates added last month, including a clear changelog, details about timestamps, and several smaller terminology clarifications.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.24_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.24_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.24_
- _fiskaltrust.Middleware.SCU.DE.FiskalyCertified v1.3.24_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.24_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.24_
- _fiskaltrust.Middleware.Helper.FileUploadHelper v1.3.24-rc1_

## Next steps in the Middleware
We will focus on introducing several improvements in our data exports in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
