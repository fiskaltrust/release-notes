---
slug: /release-notes/middleware/1.3.35
title: Version 1.3.35
---

# fiskaltrust.Middleware 1.3.35 (Germany)
_July 05, 2022_

In this version of the Middleware, we've increased the resilience of our implementation of the Fiskal Cloud Connector in the _Swissbit Cloud_ and _Deutsche Fiskal_ SCUs and improved the compatibility and stability of our TAR and DSFinV-K exports.

:::caution

Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.

:::

## Feature: Removal of cspSystemTime property for Swissbit Cloud & Deutsche Fiskal
In previous versions, we've used auto-generated models for communicating with the Fiskal Cloud Connector, that included properties that we did not use in our implementation of the _SwissbitCloud_ and _DeutscheFiskal_ TSEs. In some rare cases, properties marked as "mandatory" were not returned by the FCC, which led to exceptions. We've removed all non-needed properties in our FCC model classes to increase the stability.

## Feature:  DSFinV-K export fallback in case of empty "ITemCaseName"
If the field ZAHLART is empty because of an empty ITemCaseName in ftReceiptCaseData, we automated that it would be filled with the payitem descrption. This will enable auditors to distinguish between the different payment types.

## Feature: SwissbitCloud support in Bring your own Data Center
Our _Bring your own Data Center_ solution is now working with a FCC container to be compatible with _SwissbitCloud_ and _DeutscheFiskal_ TSEs.

## Bug fix: TAR export failed
We´ve resolved an issue where headers could not be parsed resulting in failing TAR export. 

## Bug fix: Check contente equality failed for EF queue
We´ve fixed an issue whene running an export on a ef queue the tar files were not deleted.

## Documentation: Signaturecloud single pod manual
We've created a guide for running the launcher on Docker. It is a step-by-step guide on how to run the launcher on Docker, mainly focusing on running a signle container instance.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.34_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.34_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.34_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.34_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.34_
- _fiskaltrust.Middleware.SCU.DE.Cryptovision v1.3.34_

## Next steps in the Middleware
We will focus on developing of the next version of the fiskaltrust.Launcher in the next sprints.
This version will be developed open-source, and our first public prototype can be found in the public repository https://github.com/fiskaltrust/middleware-launcher.

As always, we're happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud) or directly via issues in our GitHub repositories.
