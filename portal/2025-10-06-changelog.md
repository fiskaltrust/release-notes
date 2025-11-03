---
authors: platform
slug: portal/2025-41
tags: [Portal]
---

# Platform 2025-41

This release introduces Belgian market support and various platform enhancements.

## Belgian Portal Launch
<sub>Available since October 30, 2025</sub>

**Affected markets:** 🇧🇪

**Improved:** Added Belgian portal functionality, now available in sandbox environment for testing and validation. The portal includes all features requerd for management of the configuration, users and connections.

**Why it matters:** Expands platform reach to the Belgian market, enabling local customers to access fiskaltrust services with proper localization and regulatory compliance.

## CashBox Configuration Hidden Entity Fix
<sub>Available since October 1, 2025</sub>

**Affected markets:** ALL

**Fixed:** Resolved issue where hidden queues and signature creation units (SCUs) were still appearing in CashBox configuration. Hidden entities are now properly filtered out from selection lists, while previously selected hidden entities remain visible when already assigned to a CashBox.

**Why it matters:** Prevents confusion during CashBox configuration by ensuring only active, visible entities are available for selection, while maintaining functionality for existing configurations that use previously hidden entities.

## Helper Configuration Migration to React
<sub>Available since October 10, 2025</sub>

**Affected markets:** ALL

**Improved:** Migrated helper configuration to React implementation. The new React-based configuration supports all helper packages including balancer, REST API, POS API, helipad, and others. Enhanced cache management ensures changes made in CashBox pages are immediately visible without manual page reloads.

**Why it matters:** Provides a consistent, modern user experience across all configuration pages while improving performance and eliminating cache synchronization issues that previously required manual page refreshes.

## Exports stuck in pending state fix
<sub>Available since October 3, 2025</sub>

**Affected markets:** ALL

**Improved:** In certain scenarios it was happening that a Export got stuck in a pending state, even though it was already finished. This change fixes this behavior and users should now only see the in progress state for exports that are still running

<img width="1610" height="130" alt="image" src="https://github.com/user-attachments/assets/d5dee785-9bc3-4bf6-88d0-3af2056b7024" />

**Why it matters:** The in progress state lead to the blocking of downloads since we considered the export unfished. Fixing this issue resolves this and makes sure that users are always able to download the results in case of exports being finished.

