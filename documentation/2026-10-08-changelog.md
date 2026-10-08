---
title: "Documentation – Refunds and Voids, Error Handling, and Market Updates"
authors: documentation
slug: docs/refunds-voids-error-handling-market-updates
milestone: "n/a"
date: 2026-10-08
tags: [Documentation, PosCreators, PosDealers, POS System API, eInvoicing, InStore App, Austria, Belgium, Greece, Italy, Portugal]
---

# Documentation – Refunds and Voids, Error Handling, and Market Updates

This release focuses on improvements to the fiskaltrust documentation experience, including content updates, navigation enhancements, usability improvements, and maintenance activities.

<!-- truncate -->

## Added: Refunds, voids, discounts and error handling for all markets

Three new market-independent pages in the Compliance Middleware cash register integration:

- [Refunds and Voids](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/general/cash-register-integration/refunds-and-voids): how to void a receipt, refund it in full or in part, exchange goods and void single positions, using the `IsVoid` and `IsReturn`/`IsRefund` flags and `cbPreviousReceiptReference`. Covers referenced and unreferenced refunds and market-specific considerations.
- [Discounts and Extras](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/general/cash-register-integration/discounts-and-extras): how to record discounts and extras (surcharges) with the Discount flag of `ftChargeItemCase`, including percentage discounts, discounts on several positions or the whole receipt, discounts in refunds and voids, and how discounts differ from vouchers.
- [Error Handling](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/general/cash-register-integration/error-handling): how transport, HTTP and Middleware errors reach the POS system, how to evaluate `ftState` and error messages, and how the POS system should react.

**Why it matters:** PosCreators find the rules for corrections, price reductions and errors in one place for every market, with examples and links to the market-specific considerations.

## Added: Closing Receipts section

The cash register integration page has a new [Closing Receipts](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/general/cash-register-integration#closing-receipts) section. Daily, monthly and yearly closings are required independent of local regulations; shift closings only when the business works in shifts. The section describes the required order and how a due closing shows up in `ftState`.

**Why it matters:** PosCreators know which closings to integrate and how the Middleware signals that a closing is due.

## Added: POS System API Receipt Formats and Android IPC Transport

- [Receipt Formats](https://docs.fiskaltrust.eu/docs/poscreators/possystem-api/receipt-formats): how to retrieve an issued receipt in different formats with `GET /issue/{QueueId}/{QueueItemId}`, selected via the HTTP `Accept` header. Includes the available formats, rendering width and examples.
- [Android IPC Transport](https://docs.fiskaltrust.eu/docs/poscreators/possystem-api/android-ipc): how the launcher exposes the POS System API through Android IPC instead of a network request, with a bound service and with an activity intent.

**Why it matters:** Developers integrating the POS System API can retrieve rendered receipts in the format they need and call the API on Android without a network request.

## Added: eInvoicing buyer data and FatturaPA mapping

- [Buyer data (cbCustomer)](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/e-invoicing/cbcustomer): maps the `cbCustomer` fields to the buyer fields of EN 16931, including the fields for routing and buyer reference.
- [FatturaPA mapping (Italy)](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/italy/e-invoicing/fatturapa-mapping): how an Italian invoice receipt becomes a FatturaPA document (FPR12): which receipts get one, document types, the source of every FatturaPA element, the output and the validation rules.

**Why it matters:** PosCreators see which receipt data ends up in which eInvoice field and which validation rules a receipt has to pass before it is fiscalized.

## Added: Belgium Go-to-Market and Portugal Error Handling

- Belgium: [Go-to-Market](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/belgium/go-to-market) and [FAQ](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/belgium/go-to-market/faq) describe the parties in the Belgian registered cash register system (RCRS) and FDM setup, where the fiskaltrust.Middleware sits, what it provides, what remains with the PosCreator, and the onboarding steps.
- Portugal: [Error Handling](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/portugal/cash-register-integration/error-handling) lists the validation errors the Portuguese Middleware returns and how to fix a rejected request.

**Why it matters:** PosCreators entering Belgium get an overview of the setup and their responsibilities before they start; PosCreators in Portugal can resolve rejected requests on their own.

## Updated: Market documentation

- Austria: The [reference tables](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/austria/reference-tables) now include the v2 tables; the v0 tables and rksv.sign (retired product) were removed from the sidebar.
- Italy: the [data structures](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/italy/data-structures) page has a new [cbCustomer](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/italy/data-structures#customer-data-cbcustomer) subsection (sent as a serialized JSON string; the codice fiscale belongs in `CustomerTaxId`) and a new section on [how refunds and voids reference the original receipt](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/italy/data-structures#reference-to-the-original-receipt-in-refunds-and-voids).
- Greece: the [data structures](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/greece/data-structures) page documents the external MARK for refunds and voids of receipts from another device or system, and has a new [cbArea](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/greece/data-structures#cbarea) section (sent to myDATA as `tableAA`, max 50 characters).
- Portugal: the [Certification](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/portugal/certification) page has a new section [Receipt options, configuration, and extension points](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/portugal/certification#receipt-options-configuration-and-extension-points) for the certified document, and states that numbering series and starting numbers are set by fiskaltrust.

**Why it matters:** The market pages reflect the current behavior of the Middleware in each market.

## Updated: InStore App and PosDealer guides

- InStore App: [Available settings](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/instore-app/available-settings) updated for v1.3.2, including the `No printing` and `No payment` options, the Dummy Payment Provider and a SumUp section.
- [Registration](https://docs.fiskaltrust.eu/docs/posdealers/getting-started/registration): aligned with the new registration wizard in the fiskaltrust.Portal.
- [Desktop launchers](https://docs.fiskaltrust.eu/docs/posdealers/technical-operations/middleware/launchers/desktop#downloading-the-middleware-launcher): explicit steps to download a Middleware launcher from the fiskaltrust.Portal.
- [Network requirements](https://docs.fiskaltrust.eu/docs/posdealers/technical-operations/middleware/network-requirements): the Helipad helper uploads to `helipad.fiskaltrust.eu` and falls back to `helipad.fiskaltrust.cloud`.
- [DATEV MeinFiskal](https://docs.fiskaltrust.eu/docs/posdealers/buy-resell/products/3rd-party/datev-meinfiskal): updated onboarding process.

**Why it matters:** The guides match the current InStore App release, the current fiskaltrust.Portal and the current network endpoints.

## Improved: General data structures

The [data structures](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/general/data-structures) page has new sections:

- [cbCustomer](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/general/data-structures#cbcustomer), with links to the market-specific rules.
- [Object fields](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/general/data-structures#object-fields): fields such as `ftReceiptCaseData` are JSON objects; market-specific content goes in a sub-object keyed by the market code.
- [Currency](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/general/data-structures#currency) and [DecimalPrecisionMultiplier](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/general/data-structures#decimalprecisionmultiplier).

The [eInvoicing overview](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/e-invoicing/overview#invoices-and-invoice-types) has a new section *Invoices and invoice types* (B2C, B2B and B2G are set by `ftReceiptCase`) and states that eInvoicing is only available with a cloud CashBox. The POS System API migration guide now describes `ftReceiptCaseData` in v2 as a plain JSON object.

**Why it matters:** The shared data model is described once for all markets, and the market pages only document what differs.

## Improved: Navigation

- The PosCreators sidebar was restructured: the Middleware is grouped and the countries are listed at the top level.
- The [Austria Introduction](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/austria) is now the entry point for the Austrian section, with what is required for the Austrian market and links to the pages that cover each obligation.

**Why it matters:** Readers reach their market's pages faster and find each topic in one place.

## Improved: Discoverability with page tags

Every documentation page now has tags and a short description. The tags name the topic, product, market or regulation a page covers, for example `eInvoicing`, `InStore App`, `POS System API`, `KassenSichV` or `myDATA`. Each tag has its own page that lists all pages with that tag; the [tags overview](https://docs.fiskaltrust.eu/docs/tags) lists all tags.

**Why it matters:** Readers find all pages on a topic from one place, for example the [pages tagged eInvoicing](https://docs.fiskaltrust.eu/docs/tags/e-invoicing), across PosCreator and PosDealer sections and markets.

