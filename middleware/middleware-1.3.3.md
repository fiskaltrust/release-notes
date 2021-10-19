---
slug: /release-notes/middleware/1.3.3
title: Version 1.3.3
---

# fiskaltrust.Middleware 1.3.3 (Germany)
_July 5, 2020_

**Starting with this release, the German Middleware is compatible with Linux, running on Mono**. Please also have a look at our [FAQs](https://docs.fiskaltrust.cloud/doc/faq/qna/market-de.html#can-i-run-the-fiskaltrust-middleware-on-linux-what-are-the-requirements-and-limitations-of-the-middleware-when-running-on-linux) to see all the requirements and specifics.

<div class="alert alert--warning" role="alert">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## New feature: Linux support
Linux compatibility already exists for the Austrian and the French Middleware, and was now also included for the German market. As we use Mono, an established runtime to execute .NET applications on Linux, we support all commonly used Linux distributions (like Ubuntu, Debian, CentOS and Fedora). 

The Linux Middleware can easily be downloaded from the Cashbox list in the portal by clicking the Linux download button.

Linux is currently supported for Entity Framework and SQLite queues, and fiskaly and Cryptovision SCUs (others will follow soon).

_As of writing this, Linux support is only rolled out to the sandbox, to gather some more feedback from key customers. We will deploy these new packages to production in the upcoming days._

## Stability improvements
- An issue was fixed that could lead to errors when sending a request without charge items and the DSFinV-K type _Bestellung-V1_ to the fiskaly SCU (e.g. via an info-order).
- The communication timeout between Queue and SCU can now be configured via the `-scutimeout=` switch (in seconds). This should only be used in rare scenarios where the default timeout of 75 seconds is not sufficient.
- When sending a daily-, monthly- or yearly-closing receipt without the _implicit_ ftReceiptCaseFlag, a wrong error message was returned stating that the "out-of-operations receipt cannot be used without the implicit flag". This was now resolved.
- The queue ID was shown as the cash register serial number/_Kassenseriennummer_ in the initial-operations-receipt, while POS receipts returned the ftCashboxIdentification as the value for this. To fulfill all legal requirements, we settled on the ftCashboxIdentification, which is now returned by all affected receipts.

## How to update
Existing configurations with versions greater than 1.3.1 continue to work, but we recommend updating to this new version in case you are experiencing any issues that resemble the ones listed above.

As always, updates can be rolled out by selecting the new version in the fiskaltrust.Portal and re-building the configuration. The updated Middleware instances will then automatically pull the new packages at the next startup.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.3_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.3_
- _fiskaltrust.Middleware.SCU.Cryptovision v1.3.3_
- _fiskaltrust.Middleware.SCU.Fiskaly v1.3.3-rc2_


## Next steps in the Middleware
We will continue improving the Linux experience and work on supporting more TSEs on this platform. In addition, our development team is continuously working on improving the stability of our Middleware, and would be very happy to hear any feedback or suggestions via feedback+middleware@fiskaltrust.cloud.
