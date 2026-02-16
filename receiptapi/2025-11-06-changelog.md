---
authors: receiptapi
slug: receipt-api/2025-11-06-changelog
tags: [Receipt Api, Experience, Europe]
---

# Bug: Wrong visualization of line amounts ([receipt-api/#52](https://github.com/fiskaltrust/service-receipt-api/issues/52))

Due to a visualization bug we have been showing a positive `Amount` even though cases where the `Amount` was sent negative. This behavior was due to the fact that the sign of the `Quantity` has been taken in consideration. This behavior has been corrected and the Receipt is now visualized based on the standard way how the Middleware handles signs.

# Bug: Wrong local receipt date ([receipt-api/#78](https://github.com/fiskaltrust/service-receipt-api/issues/78))

The `cbReceiptMoment` is always sent as UTC date. While we have displayed this directly in the Receipt view we did not convert it to the local time format. With this fix we have changed this behavior and the `cbReceiptMoment` that is displayed is converted to the timezone that the receipt was generated in.