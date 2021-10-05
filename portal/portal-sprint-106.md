---
slug: /release-notes/portal/sprint-106
title: Sprint 106 (August 9, 2021)
---

# fiskaltrust.Portal - Sprint 106
_August 9, 2021_

## Features

### Middleware Configuration

- [Reworked Agencies Page](#reworked-agencies-page)
- [Highlighting Primary Contact on Employees Page](#highlighting-primary-contact-on-employees-page)
- [Employees Page Improvements](#employees-page-improvements)
- [PosOperator Page Improvements](#posoperator-page-improvements)

## Middleware Configuration

### Reworked Agencies Page

The Agencies  Page in Portal has been reworked and now the user experience has been greatly improved. All functionalities are kept but the user -aside from a significant improvement in the performance of the page- will also notice an improved experience when it comes to the following functionalities:
- Searching
- Sorting
- Pagination
- Add
- Edit
- Validation
- Routing

### Highlighting Primary Contact on Employees Page

The order of displaying data in the Employees Page table has been changed, and now, when Users navigate to the new employee's page, the primary contact will show up in the first row, as the “first” employee. 

![image](images/sprint-103/image.png)

### Employees Page Improvements

Until now, when trying to perform an update of the permissions for an employee, the switch is not refreshed and an error message is shown even though it was performed successfully. Now, this has been corrected and when users are updating permissions, the information about this update is immediately visible.
Aside from this, another improvement has been implemented in this Sprint:
So far, the wrong error message was being displayed when inviting employees, whenever there were issues with the given data. Now, the correct error message is displayed - based on data validation results,- whenever users cannot invite companies due to various data issues, meaning that the users are now properly informed on what exactly was the problem.

### PosOperator Page Improvements

The Posoperator page that can be found at https://portal-sandbox.fiskaltrust.de/PosOperator,  is showing up only for the roles of  Posoperator, Posdealer or Consultant. So, if the admin user’s role is not one of those, the page is showing up empty and there is no list for them. This has been reworked and now Admin users get a message that their role doesn’t contain POSOperator, POSDealer or Consultant and see POSOperator page Empty​.

## Next steps
In the next weeks we will focus on improving the PosOperators View.

## Feedback
We would love to hear what you think about these improvements and fixes. To get in touch, please reach out to [info@fiskaltrust.at](mailto:info@fiskaltrust.at).

© 2021 GitHub, Inc.
Terms
Privacy
Security
Status
Docs
Contact GitHub
Pricing
API
Training
Blog
About
