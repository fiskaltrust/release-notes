---
authors: platform
slug: portal/2025-41
tags: [Portal]
---

# Platform 2025-41

This release introduces Belgian market support and various platform enhancements.

<!-- truncate -->

## Belgian Portal Launch
<sub>Available since October 30, 2025</sub>

**Affected markets:** 🇧🇪

**Improved:** Added Belgian portal functionality, now available in sandbox and production environments for testing and validation. The portal includes all features required for management of the configuration, users and connections.

**Access Links:**
- Sandbox: [https://portal-sandbox.fiskaltrust.be](https://portal-sandbox.fiskaltrust.be)
- Production: [https://portal.fiskaltrust.be](https://portal.fiskaltrust.be)

**Interested in the Belgian market?** Contact our sales team to learn more about fiskaltrust services in Belgium.

**Why it matters:** Expands platform reach to the Belgian market, enabling local customers to access fiskaltrust services with proper localization and regulatory compliance.

## CashBox Configuration Hidden Entity Fix
<sub>Available since October 1, 2025</sub>

**Affected markets:** ALL

**Fixed:** Resolved issue where hidden queues and signature creation units (SCUs) were still appearing in CashBox configuration. Hidden entities are now properly filtered out from selection lists, while previously selected hidden entities remain visible when already assigned to a CashBox.

**Why it matters:** Makes CashBox setup much easier as only relevant items are shown as options to choose from.

## Helper Configuration Migration to React
<sub>Available since October 10, 2025</sub>

**Affected markets:** ALL

**Improved:** Migrated helper configuration to React implementation. The new React-based configuration supports all helper packages including balancer, REST API, POS API, helipad, and others. Enhanced cache management ensures changes made in CashBox pages are immediately visible without manual page reloads.

**Why it matters:** Provides a consistent, modern user experience across all configuration pages while improving performance and eliminating cache synchronization issues that previously required manual page refreshes.

## [Exports] Exports stuck in pending state fix (#1011)
<sub>Available since October 3, 2025</sub>

**Affected markets:** ALL

**Improved:** In certain scenarios it was happening that a Export got stuck in a pending state, even though it was already finished. This change fixes this behavior and users should now only see the in progress state for exports that are still running

<img width="1610" height="130" alt="image" src="https://github.com/user-attachments/assets/d5dee785-9bc3-4bf6-88d0-3af2056b7024" />

**Why it matters:** The in progress state lead to the blocking of downloads since we considered the export unfished. Fixing this issue resolves this and makes sure that users are always able to download the results in case of exports being finished.

## [Exports][DE] DFKA export does export VATId even if it is invalid (#1018)
<sub>Available since October 3, 2025</sub>

**Affected markets:** DE

A fix for the DFKA export has been rolled out that handles wrongly configured VAT Numbers more gracefully. There are certain scenarios where accounts are setup with a correct TaxId, but a invalid VATId. In the past we have always included both of these numbers into the DFKA export as soon as they have been set. With this change we hande invalid VAT numbers the same way as if it would not be configured and do not include them in the export. This allows accounts that have setup a correct TaxId to correctly validate the DFKA and as a result of that transfer to MeinFiskal.


