# fiskaltrust Release Notes
A repository containing release notes of our customer-facing products and services. Right now, this affects the Middleware, Portal and Product Documentation.

- These release notes will contain a sum-up of all customer-relevant changes that were made. Depending on the service, the severity of the change, and the affected markets, these changes may already be rolled out for some time when they are published here. 
- Release notes will be published every two weeks.

Please navigate to https://docs.fiskaltrust.cloud for a more convenient view of this content and open the section of interest to the left. If you have any questions regarding the changes described here, please directly reach out to us via [info@fiskaltrust.de](mailto:info@fiskaltrust.de) / [info@fiskaltrust.at](mailto:info@fiskaltrust.at) / [info@fiskaltrust.fr](mailto:info@fiskaltrust.fr).

## August 17, 2020

### Documentation

We added an onboarding guide for poscreators to help them to get a high level overview about what fiskaltrust is doing and how to use our products. In addition to this, we explain how fiskaltrust is earning money by publishing our business model. Some FAQs have been updated and added in the FAQ repository.

[Documentation Release Notes](documentation/sprint-80.md) 

### Portal

Portal updates here

## August 3, 2020

### Middleware 1.3.4

The Middleware 1.3.4 properly handles the DSFinV-K relevant master data and appends it to daily closing receipts, so that it can be easily used when querying an export. Aside from the changes made to support master data, we also introduced several stability improvements and fixed some bugs in this release and we updated our client packages to remove some inconsistencies between different communication protocols and Middleware versions.

[Middleware Release Notes](middleware/middleware-1.3.4.md)

### Portal

Aside from further polishing the fiskaltrust.Portal's outlet feature, most development effort of this sprint was put into properly injecting DSFinV-K-relevant master data (e.g. account information, outlet data, etc.) into the middleware configuration so it can be processes by the [Middleware 1.3.4](middleware/middleware-1.3.4.md).

[Portal Release Notes](portal/portal-sprint-79.md)