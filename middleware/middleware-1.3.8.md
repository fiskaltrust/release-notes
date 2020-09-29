# fiskaltrust.Middleware 1.3.8 (Germany)
This release of the Middleware includes the stabilized version of the DSFinV-K export and automatically backups the TSE's _.tar_ files on daily closing receipts. 

<div class="alert alert-warning" role="alert" style="border-radius: 0">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Finalized feature: Local DSFinV-K export
After publishing a preview version of our local DSFinV-K export in [version 1.3.6](middleware-1.3.6.md), we're happy to announce that this feature now leaves the preview state and is fully available as a stabilized, final functionality. We'd like to thank everyone who sent us their highly-valued feedback so far!

This version is required for POSOperators that use the free Middleware only (without any add-ons like the revision-safe cloud storage) to be compliant to the tax authorities' regulations. The cloud-version of our DSFinV-K export (which can be queried via the Portal and is included in our _POS Archive_) is of course up-to-date as well.

The _ftJournalType_ for getting a DSFinV-K export is `0x4445000000000002`, the returned file is a .zip stream. More details about how to access this endpoint can be found in our [docs](https://docs.fiskaltrust.cloud/doc/interface-doc/doc/general/function-structures/function-structures.html#journal-function).

## New feature: Automated TSE .tar file export & backup
Starting with this version, we automatically export the TSE .tar files - which include _transaction_, _audit_ and _system logs_ - and store them in the Queue's database. The functionality to export TAR files is required in the _BSI's Secure Element API (TR-03151)_, and thus standardized. Auditors may require these .tar files, hence we want to make them available as easy as possible.

Exporting and storing this in the Queue's database has several advantages:
- Depending on the TSE, .tar file exports may take _a lot_ of time, especially when the storage gets full. Exporting and deleting this from the TSE regularly therefore greatly enhances the performance in case it needs to be accessed quickly.
- Similarly, many TSEs tend to get slow over time due to their low memory size. Exporting and deleting the data from the device obviously also resolves this issue.
- Customers who use our _POS Archive_ profit from our regular revision-safe storage mechanisms and can download an aggregated .tar export directly via the Portal. Therefore, the data is still available to them, even if the TSE e.g. is damaged or lost.

We ensure to not delete TSE data that was not properly exported by combining the internal security mechanisms of the TSEs with additional, software-based checks. Only data that was exported to the queue is deleted from the device.

There are two options to trigger a .tar file export:
- Via a daily-closing receipt (_automatically_). To prevent this, please add the receipt case flag `0x0000000004000000`.
- Via a zero receipt (_optionally_). To execute this, please add the receipt case flag `0x0000000002000000`.

## Bug fix: Properly return TSE details of Diebold Nixdorf and Cryptovision TSEs
We fixed two small, but important issues in the Diebold Nixdorf and the CryptoVision SCUs:
- **CryptoVision**: Instead of the correct _logTimeFormat_, this SCU returned `noInputData`.
- **Diebold Nixdorf**: The serial number was returned as a Base64-encoded string instead of the required Octet string. 

Both issues are now resolved.

## Stability improvement: Improve upload of fast growing queues
Some customers with rapidly growing queues (mostly in test scenarios) reported that the Queue data was not properly uploaded to our _POS Archive_ sometimes. The log often showed timeout errors in this case. This issue was due to a wrongly set default upload limit for requests and is now resolved. As designed, large queues are now uploaded in chunks.

## How to update
Existing configurations with versions greater than 1.3.1 continue to work, **but we strongly recommend users to update to be able to use this new, required functionality**.

As always, updates can be rolled out by selecting the new version in the fiskaltrust.Portal and re-building the configuration. The updated Middleware instances will then automatically pull the new packages at the next startup.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.8_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.8_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.8-rc1_
- _fiskaltrust.Middleware.SCU.DE.CryptoVision v1.3.8_
- _fiskaltrust.Middleware.SCU.DE.DieboldNixdorf v1.3.8_

## Next steps in the Middleware
We will continue to enhance the data experience in the Middleware to be make sure to fulfill all audit requirements before September 30. This includes finishing the DSFinV-K and TAR file exports, both locally and from the data stored in our cloud platform. As we added all-new features and packages with this update, we would be especially happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at).
