# fiskaltrust Release Notes
A repository containing release notes of our customer-facing products and services. Right now, this affects the Middleware, Portal and Product Documentation.

- These release notes will contain a sum-up of all customer-relevant changes that were made. Depending on the service, the severity of the change, and the affected markets, these changes may already be rolled out for some time when they are published here. 
- Release notes will be published every two weeks.

Please navigate to https://docs.fiskaltrust.cloud for a more convenient view of this content and open the section of interest to the left. If you have any questions regarding the changes described here, please directly reach out to us via [info@fiskaltrust.de](mailto:info@fiskaltrust.de) / [info@fiskaltrust.at](mailto:info@fiskaltrust.at) / [info@fiskaltrust.fr](mailto:info@fiskaltrust.fr).

## September 01, 2020

### market-at

### market-de

#### Documentation

We published a [lead presentation for poscreators](https://docs.fiskaltrust.cloud/doc/productdescription-de-doc/for-poscreators/README.html#lead-pr%C3%A4sentation) which are interested into fiskaltrust compliance as a service solution. It is intended to provide an overview of the fiskaltrust solution and to show a possible way of integration into the POS System of the POS Creators. In addition to this, we added several new FAQ.

[Documentation Release Notes](documentation/market-de-sprint-81.md)

### market-fr

## August 18, 2020

### Middleware 1.3.5
The Middleware 1.3.5 adds support for Android mobile devices, MySQL databases, and properly handles large amounts of parallel receipt requests.

[Middleware 1.3.5 Release Notes](middleware/middleware-1.3.5.md)

### Portal
In this sprint, we focused on releasing a first preview version of the _DSFinV-K_ export to the sandbox. Although this **preview version** is not production-ready, it already creates most of the required content and only misses some final polishing that we will perform in the upcoming weeks. In addition to this, we also added the possibility to download the new [Android Launcher for our Middleware](middleware/middleware-1.3.5.md), and introduced some small, but very helpful Quality of Life-updates.

[Portal Sprint 80 Release Notes](portal/portal-sprint-80.md)

### Documentation
The product documentation is available on http://docs.fiskaltrust.cloud. We explain how fiskaltrust is earning money by publishing our business model. In addition to this, several improvements have been made at the product documentation. Some FAQs have been updated and added in the FAQ repository.

[Documentation Sprint 80 Release Notes](documentation/sprint-80.md) 

## August 3, 2020

### Middleware 1.3.4
The Middleware 1.3.4 properly handles the DSFinV-K relevant master data and appends it to daily closing receipts, so that it can be easily used when querying an export. Aside from the changes made to support master data, we also introduced several stability improvements and fixed some bugs in this release and we updated our client packages to remove some inconsistencies between different communication protocols and Middleware versions.

[Middleware 1.3.4 Release Notes](middleware/middleware-1.3.4.md)

### Portal
Aside from further polishing the fiskaltrust.Portal's outlet feature, most development effort of this sprint was put into properly injecting DSFinV-K-relevant master data (e.g. account information, outlet data, etc.) into the middleware configuration so it can be processes by the [Middleware 1.3.4](middleware/middleware-1.3.4.md).

[Portal Sprint 79 Release Notes](portal/portal-sprint-79.md)