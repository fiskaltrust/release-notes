---
slug: /release-notes/middleware/1.3.7
title: Version 1.3.7
---

# fiskaltrust.Middleware 1.3.7 (Germany)
_September 21, 2020_

Version 1.3.7 contains an important fix for Entity Framework (EF) queues, which should resolve a recurring SQL concurrency exception that multiple customers experienced. 

While this only occurred for a small percentage of receipts, it was nevertheless a critical issue for affected customers - hence we decided to release version 1.3.7 earlier than expected. The feature and stability updates we announced in the last release notes will be included in version 1.3.8.

<div class="alert alert--warning" role="alert">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Stability improvement: Fixed concurrency error in EF queue
We fixed an error multiple customers were experiencing when using the EF queue (SQLite was not affected). In some cases, the component that backups receipt data to the fiskaltrust.Cloud (_HelipadHelper_) was blocking sign requests from being processed. With unlucky timing, this could lead to failed requests, and exceptions similar to this one:

`System.Data.SqlClient.SqlException: New transaction is not allowed because there are other threads running in the session.`

This issue is now resolved, and concurrent access is now possible (sign requests are still processed sequentially, of course).

## How to update
Existing configurations with versions greater than 1.3.1 continue to work, **but we strongly recommend users of the EF queue to update to prevent this issue**.

As always, updates can be rolled out by selecting the new version in the fiskaltrust.Portal and re-building the configuration. The updated Middleware instances will then automatically pull the new packages at the next startup.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.7_

## Next steps in the Middleware
We will continue to enhance the data experience in the Middleware to be make sure to fulfill all audit requirements before September 30. This includes finishing the DSFinV-K and TAR file exports, both locally and from the data stored in our cloud platform. As we added all-new features and packages with this update, we would be especially happy to hear feedback and suggestions via [feedback+middleware@fiskaltrust.cloud](mailto:feedback+middleware@fiskaltrust.cloud).
