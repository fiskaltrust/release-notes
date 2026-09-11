---
title: "Documentation – eInvoicing Guides for PosCreators"
authors: documentation
slug: docs/einvoicing-documentation
milestone: "n/a"
date: 2026-09-11
tags: [Documentation, eInvoicing, PosCreators, POS System API, Austria, Germany, France, Italy, Poland]
---

# Documentation – eInvoicing Guides for PosCreators

This release introduces new eInvoicing documentation for PosCreators: a market-agnostic guide to the shared integration model, plus country-specific guides for Austria, Germany, France, Italy, and Poland.

<!-- truncate -->

## Added: eInvoicing documentation for PosCreators

### eInvoicing overview – the shared integration model

Added a new [eInvoicing – Overview](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/e-invoicing/overview) page that explains how eInvoicing works across fiskaltrust markets from a PosCreator's perspective: the shared model built on the `/sign`, `/issue`, and `/journal` calls you already use, the fact that it is enabled by configuration rather than a new integration, the no-webhook (polled status) rule, shared prerequisites, and an availability-by-market table.

**Why it matters:** PosCreators get a single, integration-focused entry point that clarifies what stays the same across markets and what changes from one to the next, so teams can plan an eInvoicing rollout without re-learning the API for each country.

### Country-specific eInvoicing guides

Added **Overview** and **Setup & testing** pages for five markets, each covering that market's regulatory model, timeline, formats, and how to configure and validate the flow:

- **Austria** — B2G mandatory (B2B optional, early adoption) via Peppol or e-Rechnung.gv.at, formats ebInterface / Peppol BIS: [Overview](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/austria/e-invoicing/overview) · [Setup & testing](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/austria/e-invoicing/setup)
- **Germany** — B2B, post-audit, formats XRechnung / ZUGFeRD: [Overview](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/germany/e-invoicing/overview) · [Setup & testing](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/germany/e-invoicing/setup)
- **France** — B2B, decentralised via Plateforme Agréée (PDP), formats UBL / CII / Factur-X: [Overview](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/france/e-invoicing/overview) · [Setup & testing](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/france/e-invoicing/setup)
- **Italy** — B2G/B2B/B2C, centralised clearance via SDI, format FatturaPA: [Overview](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/italy/e-invoicing/overview) · [Setup & testing](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/italy/e-invoicing/setup)
- **Poland** — B2B, centralised clearance via KSeF, format KSeF FA(3): [Overview](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/poland/e-invoicing/overview) · [Setup & testing](https://docs.fiskaltrust.eu/docs/poscreators/middleware-doc/poland/e-invoicing/setup)

**Why it matters:** PosCreators get concrete, market-specific guidance — including which mandates are already live and which deadlines are coming — so they can configure the correct output format per country and prepare their integration ahead of time.
