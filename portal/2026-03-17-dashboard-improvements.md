---
authors: platform
slug: portal/partner-dashboard-overhaul
tags: [Portal, Partner Dashboard]
---

# Partner Dashboard overhaul — certificate tracking, smart filters, and receipt preview

The Partner Dashboard has been completely redesigned to give partners faster, more actionable insight into the health of their fleet. The headline addition is SCU certificate expiration tracking, but almost every part of the dashboard has been improved.

## SCU certificate expiration tracking

The dashboard now shows when each SCU's certificate expires (DE market). Expiration dates are color-coded — green when more than 3 months out, yellow within 3 months, and red when expired — so operators can plan renewals before they become an emergency. The exact expiry date and timezone are available in a tooltip, and the queue detail view surfaces this information as well.

## Redesigned data table

The previous dashboard table has been replaced with a new flexible table that introduces column sorting, pagination, a search bar with filter chips, and smooth loading animations. Rows are now color-coded by health status — green for healthy, yellow for warnings, red for errors — giving an immediate visual overview of the entire fleet.

All queues are now included regardless of state (active, out of operation, not active), with state filtering handled through the new toolbar dropdowns instead of pre-filtering the data.

## Smart filtering system

The old stat-card filters have been replaced with multiple dropdown filters in the table toolbar:

- **Issue filter** — No Receipts (48h), Missing Daily Closing, SCU failures, SCU expiring in next 3 months, TAR file issues, and more — each showing a count
- **Queue State filter** — In Operation, Out Of Operation, Not Active
- **CashBox Type filter** — Cloud vs. Local
- **Sorglos filter** — Premium status

Filters can also be typed directly in the search bar using prefixes like `type:cloud`, `state:active`, or `issue:noreceipt`, and appear as removable chips.

## In-app receipt preview

Clicking a receipt link now opens an in-app preview modal instead of navigating to an external URL. The modal embeds the digital receipt and optionally shows Request and Response tabs with the raw JSON data, making debugging faster without leaving the portal.

## SCU failure state visibility

A new column surfaces SSCD and USED failure states. Healthy SCUs show "OK" in green; failures show a red badge with the failure count. Hovering reveals detailed failure info including timestamps and queue item IDs.

## Queue Detail View

The detail view has been streamlined from a grid of metric cards to a clean list layout. It now includes the CashBox ID, POS System ID, and formatted receipt counters. DE-specific fields (certificate expiry, last TAR file, POS Archive status) are grouped in their own section. The "Last Failed Receipt" entry includes a button to open the receipt preview modal directly.

## Account surrogation links

Account names in the table are now clickable surrogation links, allowing partners to surrogate into a PosOperator's account directly from the dashboard.

## CSV export

The dashboard now includes a built-in CSV export that exports the currently filtered rows (not the full dataset). The export includes the new columns — SCU failure state, certificate expiry, and type information.

## Layout fix

Fixed an issue that caused an unnecessary scrollbar to appear on every page in the portal.

Available in the fiskaltrust Portal since March 17, 2026.
