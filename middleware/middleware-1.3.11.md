# fiskaltrust.Middleware 1.3.11 (Germany)
_October 28, 2020_

With this version, we're happy to announce that the fiskaltrust Android Middleware is now publicly available in production! Additionally, we added support for the newly available Swissbit Cloud TSE, and introduced several important stability and performance improvements to our SCUs.

<div class="alert alert-warning" role="alert" style="border-radius: 0">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## New SCU: SwissbitCloud (Sandbox)
To increase our portfolio of supported cloud TSEs, we added a new SCU package that enables our Middleware users to include the newly available Swissbit Cloud TSE. 

Like the _DeutscheFiskal_ SCU, this new package automatically downloads and initializes the Fiscal Cloud Connector (the backend web service that is required to operate this TSE). If required, it's also possible to bypass this functionality and manually install this service by passing the `FccDirectory` parameter.

While this TSE is running smoothly in our tests so far, there are some limitations, both technically and due to the vendor's business model:
- The SwissbitCloud TSE was only certified for Windows 10 and Ubuntu 20.04 so far. Although the producer is working on additional certifications for other OSs, it can meanwhile officially only be operated on these systems. We're in continuous communication with Swissbit and will notify our users as soon as there are only news about this topic.
- Due to the pricing model (pricing is calculated per client, not per TSE), our usual rollout scenarios are limited. We are working on updating our [documentation](https://docs.fiskaltrust.cloud/doc/productdescription-de-doc/for-posdealers/02-pre-sales/rollout-scenarios.html) to reflect these limitations.

Finally, we'd like to emphasize that currently the Swissbit Cloud TSE is the fastest of all the TSEs we have tested, _including_ hardware devices.

## Stability improvements for hardware TSEs
In this version, we implemented various changes in our hardware SCU packages that should greatly improve the overall stability when working with **Swissbit, CryptoVision or Epson** TSEs. 

We especially focused on the stability of log exports and recurring operations like the self-tests and time updates, which should now also occur less often (and therefore reduce the number of consumed signatures).

## Performance improvements for hardware TSEs
While introducing the stability improvements mentioned above, we also worked hard to increase the performance of the **Swissbit, CryptoVision and Epson** TSEs. This is mostly reflecting in the performance of the log file exports, which - depending on the TSE - should now consume up to 50% less time.

## New feature: Opt-out of telemetry collection in online mode
The fiskaltrust Middleware collects usage and especially error telemetry, using Microsoft Application Insights. Previously, it was only possible to opt-out of the telemetry collection by using the Middleware in the offline mode, which comes with several disadvantages (e.g. no data upload). 

We therefore introduced a new Launcher parameter that completely deactivates all logging to Application Insights, `--telemetry-optout`.

Please keep in mind that using this will prevent us from actively reacting to issues in the respective customer installations, as we will be completely dependent on receiving inquiries and log files in those case. Also, the new _Metrics_ section in the Portal will not be available in that case.

## New feature: Bring your own datacenter proxy config
[_Bring your own Datatencer_](https://github.com/fiskaltrust/product-de-bring-your-own-datacenter) now has proxy configuration options.

## Bug fix: Uploading data was sometimes failing for large queues
We resolved an issue that lead to sometimes failing uploads to our cloud services for large queues, as the boundaries previously uploaded data was not always included properly. No data was lost due to this issue, and everything will be properly uploaded after a CashBox rebuild (which also updates the automatically added HelipadHelper).

We also fixed a related issue that sometimes completely prevented uploading data when running on Linux.

## Bug fix: The order of installation parameters is important
We noticed and resolved an issue that lead to errors when using the fiskaltrust Launcher with specific orders of parameters.

## Bug fix: Z_NUMBER is not always calculated correctly 
We resolved an issue that could lead to wrong Z_NUMBERS if the `from` and `to` parameters where specified when generating DSFinV-K exports.

## Bug fix: Exports via our client packages contained trailing \0 
We updated our Http and Soap client packages to resolve an issues that could led to trailing `\0` when requesting e.g. a DSFinV-K or a TAR export via the `Journal` endpoint. 

No data was lost in these cases, but the trailing characters had to be removed to make the files properly readable with default programs like WinRAR, which is now not the case anymore.

## How to update
Existing configurations with versions greater than 1.3.1 continue to work, **but we strongly recommend users of Hardware TSEs to update, as this new version should vastly improve the Middleware's reliability**.

As always, updates can be rolled out by selecting the new version in the fiskaltrust.Portal and re-building the configuration. The updated Middleware instances will then automatically pull the new packages at the next startup.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Launcher v1.3.11_
- _fiskaltrust.Middleware.Queue.EF v1.3.11_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.11_
- _fiskaltrust.Middleware.Queue.MySQL v1.3.11-rc2_
- _fiskaltrust.Middleware.SCU.DE.Swissbit v1.3.11_
- _fiskaltrust.Middleware.SCU.DE.CryptoVision v1.3.11_
- _fiskaltrust.Middleware.SCU.DE.Epson v1.3.11_
- _fiskaltrust.Middleware.SCU.DE.DeutscheFiskal v1.3.11_
- _fiskaltrust.Middleware.SCU.DE.SwissbitCloud v1.3.11_
- _fiskaltrust.Middleware.Helper.Helipad v1.3.11_
- _fiskaltrust.Middleware.Interface.Client.Http v1.3.11_
- _fiskaltrust.Middleware.Interface.Client.Soap v1.3.11_

## Next steps in the Middleware
We will continue to improve the stability of our Middleware in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
