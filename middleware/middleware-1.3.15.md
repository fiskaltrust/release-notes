---
slug: /release-notes/middleware/1.3.15
title: Version 1.3.15
---

# fiskaltrust.Middleware 1.3.15 (Germany)
_March 3, 2021_

This Middleware version contains a hotfix for Epson SCUs that fixes a potentially blocking issue when using the Middleware with an uninitialized TSE.

<div class="alert alert--warning" role="alert">Version 1.3 of the Middleware is meant for the German market only, customers in Austria and France should continue to use version 1.2. We will unify these experiences in an upcoming version.</div>

## Bug fix: New Epson TSEs cannot be initialized
Due to an issue in the Epson SCU, one of the following errors could occur while initializing a new TSE with the fiskaltrust.Middleware: 
- `TSE1_ERROR_WRONG_STATE_NEEDS_PUK_CHANGE`
- `TSE1_ERROR_CLIENT_NOT_REGISTERED`

We've resolved these issues, and the Epson SCU should now operate normally in scenarios where they occurred. We'd also like to thank our partners how helped us investigate this problem and verified the fix!

## Affected packages
Packages not listed here were not updated, as we decided to not increase the version of unchanged packages. All packages with versions greater or equal to 1.3.1 are compatible with each other (it is e.g. possible to use _fiskaltrust.Middleware.SCU.Swissbit.1.3.1_ with the new queue packages).

- _fiskaltrust.Middleware.SCU.DE.Epson v1.3.15_

## Next steps in the Middleware
We will continue to improve the stability of our Middleware in the next sprints. As always, we're happy to hear feedback and suggestions via [info@fiskaltrust.at](mailto:info@fiskaltrust.at) or directly via issues in our GitHub repositories.
