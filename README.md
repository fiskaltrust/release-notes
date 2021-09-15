---
slug: /release-notes
title: Release notes
---

# fiskaltrust Release Notes
A repository containing release notes of our customer-facing products and services - namely the Middleware and the Portal.

These release notes will contain a sum-up of all customer-relevant changes that were made. Depending on the service, the severity of the change, and the affected markets, these changes may already be rolled out for some time when they are published here. 

If you're viewing this on GitHub, please navigate to https://docs.fiskaltrust.cloud for a more convenient view of this content and open the section of interest to the left. If you have any questions regarding the changes described here, please directly reach out to us via [info@fiskaltrust.de](mailto:info@fiskaltrust.de) / [info@fiskaltrust.at](mailto:info@fiskaltrust.at) / [info@fiskaltrust.fr](mailto:info@fiskaltrust.fr).

## September 15, 2021

### Middleware 1.3.23 (Germany)
In this version of the Middleware, we added the possibility to easily identify mandatory and optional signature items when printing receipts. Additionally, the Middleware is now able to automatically update the _Fiskal Cloud Connector_, and several bugs and stability issues have been resolved.

[Middleware 1.3.23 Release Notes](middleware/middleware-1.3.23.md)


## August 16, 2021

### Middleware 1.3.22 (Germany)
In this version of the Middleware, we have added support for the certified version 2 of the fiskaly Cloud TSE. Additionally, some minor issues in the DSFinV-K related to transformed PayItems were resolved, and we've introduced a mechanism to reduce the Middleware's memory consumption in some scenarios.

[Middleware 1.3.22 Release Notes](middleware/middleware-1.3.22.md)


## July 20, 2021

### Middleware 1.3.21 (Germany)
In this release, we've added the possibility to deactivate Queues and switch SCUs even in cases when the TSE is not reachable anymore. Additionally, we've further improved our DSFinV-K export after successfully receiving the [GoBD certification from Audicon](https://fiskaltrust.de/fiskaltrust-middleware-dsfinv-k-schnittstelle-jetzt-gobd-zertifiziert/), including using fallback master data, automatically resolving references over different days, and several stability improvements and fixes.

[Middleware 1.3.21 Release Notes](middleware/middleware-1.3.21.md)

## May 31, 2021

### Middleware 1.3.20 (Germany)
In this Middleware version, we've removed the _one-client-limitation_ of our Swissbit Cloud SCU in cases where it has been bought as a part of our Carefree package. This enables our partners to get the "fully unlimited" Carefree experience with this TSE-as-a-service, as only our fair use regulations are in place now. Additionally, we've updated third party dependencies, fixed some issues in our SCUs, and added requested features and stability improvements to the Middleware for Android.

[Middleware 1.3.20 Release Notes](middleware/middleware-1.3.20.md)

## May 31, 2021

### Portal
In this sprint, we have introduced several usability improvements including improving the overall performance.

[Portal Sprint 101 Release Notes](portal/portal-sprint-101.md)

## May 17, 2021

### Portal
In this sprint, we have introduced the ft-Knowledege base, that should provide users with informative articles on how to troubleshoot issues that they are facing in any of the fiskaltrust products.

[Portal Sprint 100 Release Notes](portal/portal-sprint-100.md)

## May 4, 2021

### Middleware 1.3.19 (Germany)
With this Middleware version, we added the possibility to switch the connected SCU for already started Queues. This change allows users of the Middleware to change the used TSE without having to create a new Queue. Additionally, we've included several important bug fixes in this update.

[Middleware 1.3.19 Release Notes](middleware/middleware-1.3.19.md)

## May 3, 2021

### Portal
In this sprint, we have introduced several usability improvements, especially when working with the AO148 generator, or the entitlements history page.

[Portal Sprint 99 Release Notes](portal/portal-sprint-99.md)

## April 19, 2021

### Portal
In this sprint, we have been focusing on creating a tool that should give users the ability to easily create AO 148 applications.

[Portal Sprint 98 Release Notes](portal/portal-sprint-98.md)

## April 5, 2021

### Portal
In this sprint, we have focused to improve overall usability and to make sure that users have the same capabilities to generate unique CashBoxIdentifications as they have when using ft-Helipad.

[Portal Sprint 97 Release Notes](portal/portal-sprint-97.md)

## March 26, 2021

### Middleware 1.3.18 (Germany)
This Middleware version contains bug fixes for issues that could occur when using _Swissbit Cloud_ or _Deutsche Fiskal_ TSEs behind a proxy server, a stability improvement for our _CryptoVision_ SCU to handle Windows' USB power saving mode, and a minor improvement for generating TSE order payloads.

[Middleware 1.3.18 Release Notes](middleware/middleware-1.3.18.md)


## March 22, 2021

### Portal
In this sprint, we have introduced the Rollout Management feature that should greatly improve the rollout experience for PosDealers. 

[Portal Sprint 96 Release Notes](portal/portal-sprint-96.md)

## March 18, 2021

## Middleware 1.3.17 (Germany)
This Middleware version contains a hotfix for Diebold Nixdorf SCUs that fixes a potentially blocking issue that could occur while reading the status of the TSE.

[Middleware 1.3.17 Release Notes](middleware/middleware-1.3.17.md)

## March 12, 2021

## Middleware 1.3.16 (Germany)
We're happy to announce that the fiskaly SCU is now available in our production systems (please see our [blog post](https://fiskaltrust.de/news/aktueller-status-zur-cloud-tse-202103/) for more details). Additionally, we've added a new signature that contains the TSE certification ID and (if required) information about the state of the certification and operational environment regulations. At least in the latter case, this needs to printed onto the receipt. Finally, this version contains some bug fixes and usability improvements for the Middleware.

[Middleware 1.3.16 Release Notes](middleware/middleware-1.3.16.md)

## March 8, 2021

### Portal
In this sprint we have been focusing to further improve the new orders page to being able to put it into public preview so that all of our users can use it.

[Portal Sprint 95 Release Notes](portal/portal-sprint-95.md)

## March 3, 2021

### Middleware 1.3.15 (Germany)
This Middleware version contains a hotfix for Epson SCUs that fixes a potentially blocking issue when using the Middleware with an uninitialized TSE.

[Middleware 1.3.15 Release Notes](middleware/middleware-1.3.15.md)

## March 1, 2021

### Portal
In this Sprint, we were focused on establishing a secure platform for configuring Middleware components, as well as creating a prototype for the new Orders page.

[Portal Sprint 94 Release Notes](portal/portal-sprint-94.md)

## February 17, 2021

### Middleware 1.3.14 (Germany)
This quality-of-life update for the Middleware fixes multiple bugs, introduces stability improvements, and should enhance the overall user experience of the Middleware.
Additionally, the MySQL Queue now officially left the RC status and is fully supported in production.

[Middleware 1.3.14 Release Notes](middleware/middleware-1.3.14.md)

## February 15, 2021

### Portal
In this sprint we have focused on improving the permission selection and also worked on several improvements of different features.

[Portal Sprint 93 Release Notes](portal/portal-sprint-93.md)

## February 1, 2021

### Portal
In this sprint we have focused on improving the permission selection and also worked on several improvements of different features.

[Portal Sprint 92 Release Notes](portal/portal-sprint-92.md)

## January 18, 2021

### Portal
In Sprint 91 most of the team was on vacation. Therefore we used the time to improve internal processes to having a baseline for future development.

[Portal Sprint 91 Release Notes](portal/portal-sprint-91.md)

## December 28, 2020

### Portal
In this sprint we have focused on improving the labeling of the different functionalitiets in the invitation view. Additionally, we have removed some not needed features that have led to confusions in the past.

[Portal Sprint 90 Release Notes](portal/portal-sprint-90.md)

## January 22, 2021

### Middleware 1.3.13 (Germany)
This version of the Middleware fixes two issues in the Launcher that affected users with specific configurations.

[Middleware 1.3.13 Release Notes](middleware/middleware-1.3.13.md)

## December 20, 2020

### Portal
In this sprint we have focused on implementing a long requested feature: Changing the primary contact of an account. Additionally, we have added some improvements to the overall user experience.

[Portal Sprint 89 Release Notes](portal/portal-sprint-89.md)

## December 18, 2020

### Middleware 1.3.12
This version of the Middleware fixes an important bug related to creating the signature payloads of _info-order_ receipts.

[Middleware 1.3.12 Release Notes](middleware/middleware-1.3.12.md)

## December 12, 2020

### Middleware 1.3.11
With this version, we're happy to announce that the fiskaltrust Android Middleware is now publicly available in production! Additionally, we added support for the newly available Swissbit Cloud TSE, and introduced several important stability and performance improvements.

[Middleware 1.3.11 Release Notes](middleware/middleware-1.3.11.md)

## December 7, 2020

### Portal
The main focus of this sprint was to further enhance the Portal's Shopping experience, especially the searching experience.


[Portal Sprint 88 Release Notes](portal/portal-sprint-88.md)

## November 23, 2020

### Portal
The main focus of this sprint was to further enhance the Portal's Shopping experience, especially the selection of the outlet and the basic visualization of different categories of products. 

[Portal Sprint 87 Release Notes](portal/portal-sprint-87.md)

## November 9, 2020

### Portal
The main focus of this sprint was to further enhance the Portal's UI and UX, especially for large-scale rollout scenarios and general POS Dealer activities. In addition, we worked on improving the Android Launcher, which can now be downloaded more easily and will soon be rolled out to Google Play.

[Portal Sprint 86 Release Notes](portal/portal-sprint-86.md)


## October 28, 2020

### Middleware 1.3.10
We're happy to announce that starting from this version, we provide SCUs for all currently certified TSEs, as well as SCUs for two major cloud TSEs that are currently in certification (fiskaly and A-Trust). While some of those are still only available on the sandbox, we consider them production-ready and are working closely with our partners to push them to production as soon as possible.

In addition to this, we resolved several important stability issues in version 1.3.10, which should result in an overall greatly increased reliability, especially when working with Swissbit SCUs. Also, we fixed an important issue in our SQLite implementation that lead to data not being 100% correctly read from the database (although no data was lost, as everything was written correctly).

[Middleware 1.3.10 Release Notes](middleware/middleware-1.3.10.md)


## October 26, 2020

### Portal
In this sprint, we worked in making the aggregated TAR export available in the Portal, which - together with the DSFinV-K export - enables our customers to get all audit-relevant data without requiring direct access to the POS System. Additionally, we greatly improved the subscription management, and are now displaying the expiration dates of TSEs.

[Portal Sprint 85 Release Notes](portal/portal-sprint-85.md)


## October 12, 2020

### Portal
In this sprint, the Engineering team was mostly focusing on improving our Middleware by adding new SCUs and fixing some reported issues. Still, several usability improvements and bug fixes were implemented that should resolve some common issues our users experienced.

[Portal Sprint 84 Release Notes](portal/portal-sprint-84.md)

## October 6, 2020

### Middleware 1.3.9
In this version, we published an important fix for the TSE _.tar_ file export, both in the Queue and the SCU packages. This resolves a critical issue where customers with pre-existing Queues were not able to properly execute daily-closing receipts anymore.

[Middleware 1.3.9 Release Notes](middleware/middleware-1.3.9.md)


## September 30, 2020

### Middleware 1.3.8
This release of the Middleware includes the stabilized version of the DSFinV-K export and automatically archives the TSE's _.tar_ files on daily closing receipts. 

[Middleware 1.3.8 Release Notes](middleware/middleware-1.3.8.md)

## September 28, 2020

### Portal
In this sprint, we focused on improving commonly used features in the Portal. This includes the registration process, the ordering and shipping workflows, and several smaller fixes to improve the overall user experience. Additionally, we enabled the auto-invitation flow and the CSV bulk operator import in production.

[Portal Sprint 83 Release Notes](portal/portal-sprint-83.md)


## September 21, 2020

### Middleware 1.3.7
Version 1.3.7 contains an important fix for Entity Framework (EF) queues, which should resolve a recurring SQL concurrency exception that multiple customers experienced. 

[Middleware 1.3.7 Release Notes](middleware/middleware-1.3.7.md)


## September 14, 2020

### Middleware 1.3.6
This release adds the functionality to locally generate our preview version of the DSFinV-K export, and the new production-ready Diebold Nixdorf SCU. Additionally, we fixed several issues and added some smaller improvements, mostly related to special receipt responses.

[Middleware 1.3.6 Release Notes](middleware/middleware-1.3.6.md)

### Portal
In this sprint, we focused on improving several features in portal. Additionally to a brand new editing experience for CashBox-Templates we also added a long requested feature to display the raw content of receipts to the receipts page. One thing that we also want to highlight is the Prod release of the FR Market.

[Portal Sprint 82 Release Notes](portal/portal-sprint-82.md)


## August 31, 2020

### Portal
In this sprint, we focused on streamlining the German e-commerce experience. This includes full support for ordering, producing and shipping digital and hardware products, enabling missing features in the entitlement based sale processes, and various UX improvements in the Portal that should greatly simplify common e-commerce related tasks.

[Portal Sprint 81 Release Notes](portal/portal-sprint-81.md)


## August 18, 2020

### Middleware 1.3.5
The Middleware 1.3.5 adds support for Android mobile devices, MySQL databases, and properly handles large amounts of parallel receipt requests.

[Middleware 1.3.5 Release Notes](middleware/middleware-1.3.5.md)

### Portal
In this sprint, we focused on releasing a first preview version of the _DSFinV-K_ export to the sandbox. Although this **preview version** is not production-ready, it already creates most of the required content and only misses some final polishing that we will perform in the upcoming weeks. In addition to this, we also added the possibility to download the new [Android Launcher for our Middleware](middleware/middleware-1.3.5.md), and introduced some small, but very helpful Quality of Life-updates.

[Portal Sprint 80 Release Notes](portal/portal-sprint-80.md)


## August 3, 2020

### Middleware 1.3.4
The Middleware 1.3.4 properly handles the DSFinV-K relevant master data and appends it to daily closing receipts, so that it can be easily used when querying an export. Aside from the changes made to support master data, we also introduced several stability improvements and fixed some bugs in this release and we updated our client packages to remove some inconsistencies between different communication protocols and Middleware versions.

[Middleware 1.3.4 Release Notes](middleware/middleware-1.3.4.md)

### Portal
Aside from further polishing the fiskaltrust.Portal's outlet feature, most development effort of this sprint was put into properly injecting DSFinV-K-relevant master data (e.g. account information, outlet data, etc.) into the middleware configuration so it can be processes by the [Middleware 1.3.4](middleware/middleware-1.3.4.md).

[Portal Sprint 79 Release Notes](portal/portal-sprint-79.md)
