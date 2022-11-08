---
authors: posdealer
slug: portal/cashbox-bulk-update
tags: [Portal,BulkUpdate]
---

# Improve performance and UX of cashbox bulk update page

As we find this page very useful to PosDealers we did couple of improvements in last weeks:
- Update of the records are parallelized and time of waiting will be reduced up to 5 times
- Pagination - Summary page has pagination that will speed up rendering time as now we are rendering 100 items per page
- Status - All cashboxes will have status of update so that user can be sure if CashBox is updated or not. Status is manifested through icon in the column "Status". By hovering over icon user will be provided with additional information. 
- Filtering - To be able to clearly distinguish between item's current statuses we added next options to filter out the data:
    - All cashboxes - showing all items
    - Updating - cashBox update is in progress
    - Successfully updated - update is done with success
    - Failed to update - update was not able to be performed
- Download CSV - All data in the table can be downloaded as CSV file
- Progress bar - As updates will be performed in chunks now, we are showing progress bar at the bottom of the page. During update it is showing progress in percentage. After update is finished, if there are any errors, number of successful and failed operation will be shown inside of the progress bar (bar will be colored in yellow), otherwise it will be green with success message
