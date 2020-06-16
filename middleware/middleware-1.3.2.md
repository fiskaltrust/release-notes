# fiskaltrust.Middleware 1.3.2 (Germany)
This release includes some stability improvements and bug fixes for the German middleware, and can be used in production scenarios. Additionally, a release candidate of the Diebold Nixdorf SCU is now available on the [sandbox](https://portal-sandbox.fiskaltrust.de).

No changes in the interface were made in this release.

<div class="alert alert-warning" role="alert" style="border-radius: 0">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## New features
- A first stable release candidate of the Diebold Nixdorf SCU implementation was published (as version `1.3.2-rc1`) to the sandbox. After extensive internal testing, we decided to release this version as RC1 to get customer feedback before publishing a final version. If you are interested in using Diebold Nixdorf TSEs in your products and need more information/notice any issues, please reach out to info@fiskaltrust.de. As always, we appreciate all forms of feedback.

## Stability improvements
- An issue was fixed that lead to a database locked error when requesting already sent receipts (e.g. for validation purposes) via the receipt case flag `0x0000800000000000` in rare cases.
- In addition to this, requested receipts were not properly ordered in case the request matched multiple ones. If this is the case, the Middleware now always returns the latest receipt.
- Due to a validation logic issue, empty ChargeItems or PayItems were not supported anymore in certain configurations and made the SCU switch to failure mode. This scenario mostly occurred when working with vouchers, and is now fixed.
- Logging at the application startup was greatly improved, which should simplify detecting errors for both customers and our customer care team.

## How to update
Existing configurations with 1.3.1 continue to work, but we recommend updating to this new version in case you are experiencing any issues that resemble the ones listed above. 

As always, updates can be rolled out by selecting the new version in the fiskaltrust.Portal and re-building the configuration. The updated Middleware instances will then automatically pull the new packages at the next startup.

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new packages).

- _fiskaltrust.Middleware.Queue.EF v1.3.2_
- _fiskaltrust.Middleware.Queue.SQLite v1.3.2_
- _fiskaltrust.Middleware.SCU.DieboldNixdorf v1.3.2-rc1_

## Next steps
As also announced in the previous release notes, we are working on improving our portal to create a better onboarding, development and middleware rollout experience. 