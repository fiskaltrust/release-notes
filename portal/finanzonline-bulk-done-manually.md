---
title: "FinanzOnline Notifications: Set Several Entries to Done Manually at Once"
authors: market_at
slug: portal/finanzonline-bulk-done-manually
milestone: "n/a"
date: 2026-09-14
tags: [Portal, FinanzOnline]
---

## Summary

On the FinanzOnline notifications page you can now select several notifications or audits and set them all to done manually in one step, instead of opening a separate dialog for every single entry.

<!--truncate-->

## Why This Matters

The FinanzOnline notifications page lists the notifications and audits that fiskaltrust has sent, or attempted to send, on your behalf. Entries that failed, ran into an incident, or are still waiting remain in that list until someone records what happened to them. Where the work has already been handled directly in FinanzOnline, recording that outcome in the portal is the only step still missing.

Until now, that had to be done one entry at a time. Each row had its own action, each action opened its own dialog, and each dialog had to be filled in and confirmed separately. An account that moves its FinanzOnline handling into the portal with an existing history behind it had to repeat those steps for every entry in that history.

Now you can select the entries you want, state the result once, and have the portal apply it to all of them. The outcome recorded is the same, and so is its effect on your FinanzOnline history — you simply no longer repeat the process for each entry individually.

## What Changed

- Every list on the FinanzOnline notifications page now shows a checkbox next to each entry that can still be completed manually, along with a select-all checkbox above the list. Entries that are already finished cannot be selected, so a completed entry cannot be changed by accident.
- If you have searched or filtered the list first, select-all applies to the entries you can actually see — never to hidden ones. What you have selected is always what the action will change.
- Once something is selected, a button appears above the list showing the exact count, for example **Set 12 notifications to done manually** or **Set 12 audits to done manually**.
- The dialog asks only for the two details that make sense for a whole set: the **Result** to record and the **time** it happened. For notifications the result options are the familiar *Successfully executed*, *Failed*, *Ignore failed* and *Ignore duplicated*; for audits they are *Valid receipt*, *Invalid receipt*, *Ignore invalid or failed* and *Ignore duplicated*.
- While the entries are being processed you can follow the progress and stop the run at any time. Everything already processed keeps its new result, and everything not yet reached stays selected and untouched.
- If a single entry cannot be updated, the rest of the run carries on regardless. Only the entries that did not succeed remain selected afterwards, so confirming again retries just those.
- The per-entry action and its dialog are unchanged. If you would rather complete one entry at a time, exactly as before, nothing about that has changed.

## Impact

This applies to the **Austrian market only**, on the **Tools → FinanzOnline notifications** page, and is available to POS Operators who manage their own FinanzOnline reporting. It covers every list on that page: notifications, validations, the entries not yet processed, and the combined timeline.

There is nothing to set up, and none of your existing entries change until you choose to act on them. The result recorded for a set of entries is exactly the result the single-entry dialog would have recorded for each one, so your FinanzOnline history stays consistent whichever way you complete an entry.
