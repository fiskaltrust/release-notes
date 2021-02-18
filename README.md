---
slug: /release-notes
title: Release notes
---

# fiskaltrust Release Notes
A repository containing release notes of our customer-facing products and services - namely the Middleware and the Portal.

These release notes will contain a sum-up of all customer-relevant changes that were made. Depending on the service, the severity of the change, and the affected markets, these changes may already be rolled out for some time when they are published here. 

If you're viewing this on GitHub, please navigate to https://docs.fiskaltrust.cloud for a more convenient view of this content and open the section of interest to the left. If you have any questions regarding the changes described here, please directly reach out to us via [info@fiskaltrust.de](mailto:info@fiskaltrust.de) / [info@fiskaltrust.at](mailto:info@fiskaltrust.at) / [info@fiskaltrust.fr](mailto:info@fiskaltrust.fr).

## February 17, 2021

### Middleware 1.3.14 (Germany)
This quality-of-life update for the Middleware fixes multiple bugs, introduces stability improvements, and should enhance the overall user experience of the Middleware.
Additionally, the MySQL Queue now officially left the RC status and is fully supported in production.

[Middleware 1.3.14 Release Notes](middleware/middleware-1.3.14.md)


## January 22, 2021

### Middleware 1.3.13 (Germany)
This version of the Middleware fixes two issues in the Launcher that affected users with specific configurations.

[Middleware 1.3.13 Release Notes](middleware/middleware-1.3.13.md)


## December 18, 2020

### Middleware 1.3.12
This version of the Middleware fixes an important bug related to creating the signature payloads of _info-order_ receipts.

[Middleware 1.3.12 Release Notes](middleware/middleware-1.3.12.md)


## December 12, 2020

### Middleware 1.3.11
With this version, we're happy to announce that the fiskaltrust Android Middleware is now publicly available in production! Additionally, we added support for the newly available Swissbit Cloud TSE, and introduced several important stability and performance improvements.

[Middleware 1.3.11 Release Notes](middleware/middleware-1.3.11.md)

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