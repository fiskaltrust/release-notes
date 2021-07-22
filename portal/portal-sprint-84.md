---
slug: /release-notes/portal/sprint-84
title: Sprint 84 (October 12, 2020)
---

# fiskaltrust.Portal - Sprint 84
_October 12, 2020_

**Usability improvements and bug fixes**

In this sprint, the Engineering team was mostly focusing on improving our Middleware by adding new SCUs and fixing some reported issues. Still, several usability improvements and bug fixes were implemented that should resolve some common issues our users experienced.

## Features

### E-Commerce

#### Fixed an issue that prevented purchasing products from the outlet page (DE)
The recently implemented check that should prevent customers from buying duplicate features for outlets broke the possibility to purchase outlet-based products directly from the outlet list. While it was still possible, this was of course an annoying issue, and therefore resolved.

### Middleware Configuration

#### Make POS-System version configurable (All markets)
To be fully compliant with the DSFinV-K, the master data module needs to contain the version of the POS-System. Hence, we added this field in the POS-System configuration dialogs.

In addition, we generally improved the performance of the POS-System functionality in the Portal.

<div class="alert alert--info" role="alert">POS-System data must be included in the DSFinV-K. To allow us to properly generate this, POS Creators need to add their POS-Systems to the fiskaltrust fiskaltrust.Portal in the respective configuration view, and POS dealers need to link to them. The data will automatically be available for for their linked operators reports then.</div>

#### Enable bulk updating for German SCUs (DE)
While bulk-updating Queues of connected accounts (which enables POS Dealers to update their operators in a simple way) was already possible, updating the SCUs was not yet supported in the German Portal. To fully make use of this feature, we updated this page to now show the SCUs as well. We therefore now have the same behavior as in our other markets.

#### VAT rates were rounded in the receipt journal list (All markets)
Users reported a bug about incorrectly rounded VAT rates in the receipt journal list view. As decimal VAT rates are not a thing in Austria, this issue wasn't noticed until now - nevertheless it's now fixed. 

In addition, customers hinted that the receipt total is also not displayed correctly in this list. This issue will be resolved in the upcoming sprint.

### User Management

#### Support email addresses that contain dots in the domain (All markets)
Another issue that was not noticed so far was the missing support for email addresses that contain a dot (`.`) in the domain, e.g. `user@sub.domain.de`. This was now fixed, users with this type of email address can now register (or be invited).

#### Fix UID check for companies outside of Germany (DE)
We noticed that our UID (Ust-ID) check for companies outside of Germany was not working in some scenarios. This issue is now resolved.

## Next steps
In the next sprints, we will focus on improving the Middleware, especially in terms of SCU stability, and are working on supporting additional TSEs (like the newly certified _Deutsche Fiskal TSE_). Aside from this, we will continue to improve the user experience in our Portal, mostly focused on an enhanced rollout experience.

## Feedback
We would love to hear what you think about these improvements and fixes. To get in touch, please reach out to [info@fiskaltrust.at](mailto:info@fiskaltrust.at).