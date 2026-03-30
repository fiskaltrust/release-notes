---
title: "Test release notes automation"
source: https://github.com/fiskaltrust/service-portal-ui/issues/273
milestone: "n/a"
date: 2026-03-30
labels: []
---

## Summary
The editing process for PosOperator invitations has been upgraded to a new React form, enhancing user experience with inline validation and faster updates.

## Why This Matters
This change allows PosDealers to review and adjust invitation details more efficiently, eliminating the need for full page reloads and reducing friction when correcting data.

## What Changed
- Transitioned the PosOperator invitation editing from MVC to a React-based form.
- Implemented an `EditPosOperatorInvitationPage` that prepopulates dynamic company/user field groups.
- Updated navigation to the React edit route based on feature flag status.
- Ensured API parity by reusing the same endpoints for fetching and updating data.
- Added unit/integration tests for the new React edit component and API contract tests.

## Impact
PosDealers will benefit from a more streamlined editing process. No action is required from users; the transition to the new React form will occur automatically when the feature flag is enabled.
