---
title: "Role Restriction: Prevent PosOperator from Signing Additional Roles"
authors: platform
slug: portal/role-restriction-prevent-posoperator-from-signing-additional-roles
source: https://github.com/fiskaltrust/service-portal-ui/issues/260
milestone: "n/a"
date: 2026-05-06
tags: []
---

## Summary
We've made an important update to the role management in the fiskaltrust Service Portal. Now, if you are assigned only the PosOperator role, you won’t be able to sign into any other roles.
<!--truncate-->
## Why This Matters
This change helps ensure that users with the PosOperator role focus on their specific responsibilities without the confusion of managing multiple roles. It simplifies the role management process and enhances compliance with our long-term goal of role restrictions.

## What Changed
- Users with only the PosOperator role will see that all other role sign-on buttons are disabled.
- When hovering over any disabled role, a helpful tooltip will appear, explaining that you can't sign any other roles while the PosOperator role is active.
- Existing users with multiple roles, including PosOperator, will not experience any changes to their current access.

![pos-operator-role-restriction](images/pos-operator-role-restriction/pos-operator-role-restriction.png)

## Impact
This update primarily affects users who hold the PosOperator role exclusively. If you are one of these users, you will notice the new restrictions in place. If you have multiple roles, you can continue using them as before for now, so no immediate action is required on your side. However, our long-term goal is to separate these roles more clearly. Therefore, users who are both POS Dealers and POS Operators should plan to migrate their POS Operator activities to a separate account in the future.

