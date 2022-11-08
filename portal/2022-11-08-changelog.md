---
authors: posdealer
slug: portal/cashbox-bulk-update
tags: [Portal,BulkUpdate]
---

# Improve performance and UX of CashBox bulk update page

As we find this page beneficial to PosDealers, we made a couple of improvements in the last weeks:
- Update of the records are parallelized, and this will reduce your time of waiting to 5 times.
- Pagination - The summary page has pagination that will speed up rendering time, as now we are rendering 100 items per page
- Status - All CashBoxes will show their update status so you can be sure if a CashBox is updated. The column "Status" shows an icon; hovering over this provides you with additional information.
- Filtering - To be able to distinguish between item's current statuses clearly, we added the following options to filter out the data:
    - All CashBoxes - showing all items.
    - Updating - CashBox update is in progress.
    - Successfully updated - update is done successfully.
    - Failed to update - an update was not able to be performed.
- Download CSV - You can download all data in the table as a CSV file.
- Progress bar - As your updates are performed in chunks now, we are showing a progress bar at the bottom of the page. During the update, the bar is showing progress in percentage. After the update, the bar shows successful and failed operations by numbers. The bar will be colored yellow if updates fail; otherwise, the bar will be green with a success message.
