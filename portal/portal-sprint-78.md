# fiskaltrust.Portal - Sprint 78
_July 20, 2020_

**Outlet Management for Middleware components, New Export experience for AT**

In sprint 78, development was mostly focused on preparing for the additional challenges that come along with operating Middleware components in the german market. Since most components in germany are configured for just one outlet we extended the portal to being able to help with fulfilling this requirement.

## Features

### Data exports

#### Add the new Export view for AT
##### Export Creation

We added the new Export Creation View to the AT Market. This should give our Users a more simplified way to start exports.

The new Export Creation View uses our new Export system which should lower the times for getting an export from infinity to a few minutes depending on the size of the queue.

We also added a new Category of export to the page, called PosArchiveAT. This Export is a combination of the full export (XML) and the DEP export which will be used for finance audits. 

![new-export-page-at](images/sprint-78/new-export-at.png)<br><br>

#####  Export Retrivial
We also revamped the export page which can be found in the Tools section. This page should load very quickly and display all exports created with the new Export System. If you are missing a previously created export you can access them by clicking at the "Previous Exports" button.

![new-export-page-at](images/sprint-78/new-export-list-at.png)<br><br>

### E-Commerce

### Middleware Configuration

#### List of queues performance improvement

While working on the outletmanagement feature we noticed that we are doing a lot of duplicate work while loading the queues that is not necessary. We changed a few things in the order that we call our backends and could see 8x-10x faster page loading time depending on how many queues you have configured. Especially accounts with many queues should see far better load timings. The gif bellow should give you a good overview on the difference.

![new-export-page-at](images/sprint-78/queue_list_performance.gif)<br><br>

### User Management

#### Outlet Management


## Next steps
In the upcoming sprints, the development team will continue to improve the onboarding experience, data exports, and introduce some updates to our shop.

## Feedback
We would love to hear what you think about these features. To get in touch, please reach out to [info@fiskaltrust.at](mailto:info@fiskaltrust.at).