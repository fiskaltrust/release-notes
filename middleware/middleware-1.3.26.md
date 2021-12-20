---
slug: /release-notes/middleware/1.3.26
title: Version 1.3.26
---

# fiskaltrust.Middleware 1.3.26 (Germany)
_December 9, 2021_

In this version of the Middleware, we introduced compatibility with the upcoming fiskaly v2 standalone product and implemented some fixes that should improve the runtime behavior of the Middleware, especially when using the CryptoVision TSE or in cases our users experienced memory or performance issues. Additionally, we've updated the Ambassador stack in _Bring your own Datacenter_ to support new Kubernetes versions. Please make sure to read the [Migration Guide](https://github.com/fiskaltrust/helm-charts/blob/master/bring-your-own-datacenter/MIGRATION.md#v1326) before updating.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Feature: Introduced compatibility with fiskaly v2 standalone product
As we'll make the fiskaly v2 standalone (or "single product") publicly available in our shop in the upcoming weeks, we enabled a convenience feature that will prevent accidental registration of multiple clients on a single TSE, which would lead to additional costs. This feature will only be activated if the TSE was bought as a standalone product; TSEs-as-a-Service and TSEs that are individually bought by the users themselves are not affected.

## Improvement: Bring you own Datacenter now supports Kubernetes v1.22+
We've upgraded BYODCs loadbalancer to the [Ambassador 2.0 stack](https://www.getambassador.io/docs/emissary/latest/about/changes-2.x/) which is now compatible with Kubernetes v1.22+.

:::danger

This update will lead to short downtime during the update process.
Please follow the [Migration Guide](https://github.com/fiskaltrust/helm-charts/blob/master/bring-your-own-datacenter/MIGRATION.md#v1326) when *updating* to this version of BYODC. 
Attempting the update without following the steps described there will destroy your BYODC installation.

:::

## Bug Fix: Proxy credentials are ignored during data upload on some systems
We've resolved an issue that caused the HelipadHelper (which is responsible for uploading receipt data to our systems) and the optional FileUploadHelper to ignore the proxy credentials set via the command line parameters of the Middleware Launcher. This issue did not occur on all system configurations and never occurred if a system proxy was set.

This issue has been resolved, proxy credentials are now correctly set. Unlike regular package updates, this change requires a re-download of the Launcher from the Portal. Users who are not experiencing upload problems related to proxy credentials don't have to update the Launcher.

## Stability improvement: Keep-alive polling for CryptoVision SCUs
Following a suggestions from CryptoVision, we've implemented the possibility to _poll_ CryptoVision TSEs to keep them alive. This should improve TSE instabilities for a small group of users where the USB power-saving mode of the operating system is disabled, but the TSE is still turned off by the OS. 

As this only affects a small subset of our users, this feature is turned off by default and can be enabled by setting the `KeepAliveIntervalInSeconds` of the SCU in the Portal. CryptoVision suggested to start testing with an interval of 5 - 10 seconds.


## Stability improvement: Helipad data upload helper performance and memory consumption
We've introduced several improvements in our Helipad helper package, which is responsible for uploading data to our cloud services. These improvements should reduce the memory and CPU consumption and the amount of transmitted data, while increasing the overall reliability of the upload. 

As the Helipad helper package is automatically added to CashBoxes, rebuilding configurations will automatically add the latest version without further actions required.


## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.SCU.DE.FiskalyCertified v1.3.26_
- _fiskaltrust.Middleware.SCU.DE.CryptoVision v1.3.26_
- _fiskaltrust.Middleware.Helper.Helipad v1.3.26_
- _fiskaltrust.Middleware.Helper.FileUpload v1.3.26_
- _fiskaltrust.Launcher v1.3.26_

## Next steps in the Middleware
We will focus on development of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source and a first proof-of-concept can be found in the `proof-of-concept` branch of the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.

## Merry Christmas
The PosCreator Experience team would like to take this opportunity to thank all our partners for their ongoing contributions to our products, and wish all of you Merry Christmas and happy holidays! 

![christmas-tree](https://imgs.xkcd.com/comics/tree.png)
