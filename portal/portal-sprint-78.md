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

#### Configuring Outlets for Middleware components

Since we do have the requirement of binding Queues and SCUs to specific outlets in Germany we added a setting for selecting the Outlet that the Queue/SCU should be created for. For Germany and France this setting is required. For Austria you don´t have to select an outlet for your Queue/SCU, but you can select it if you like to.

![queue-configuration-location](images/sprint-78/queue-configuration-location.png)<br><br>

When configuring helpers you CAN add an outlet, but it is not required. Especially for some specific helpers you sometimes don´t want to configure an outlet, so feel free to leave this empty.

![helper-configuration-location](images/sprint-78/helper-configuration-location.png)<br><br>

When creating / configuring CashBoxes you basically have two options. You can configure and outlet or you can leave the field empty. If the field is empty during the creation we take the next available outletnumber to make sure that we are not placing the queue onto an invalid outlet. If you later on want to configure the right outlet you can do this in the edit dialog.

We will continue improving this feature and add additional functionalities to make it easier to see in which outlet the selected component is running.

#### Failed to load more than 1000 ReceiptJournals 

In our monitoring we noticed that for some customers we do have failing requests when they try to request very large amounts of receiptjournal entries. The reason for this issue is a limitation of one of our backend systems. We fixed this by putting in a cap of 1000 receiptjournals that can be loaded.

####  FR -Fix for failing SignaturCreationFR creation if no proper outlet is configured

When you created a SignaturCreationFR with an outlet that has no properly configured businessnumber the creation ended in a 500 error. This is resolved now and in the case of no properly configured outlets you are prompted with an error message:

![fr-configuration-location-wrong](images/sprint-78/helper-configuration-location.png)<br><br>

In case you see this please make sure that your company configuration is valid and also that your outlets have correct location ids. 


#### DE - Hiding non working Helpers in German market

We have removed all helpers that have a version number lower than 1.3 in the german market to make sure that you don´t configure versions that will anyways not work. 

#### DE - Show error message when CashBox contains QueueDE without an assigned SCU

Our data showed that some of our customers are running into an issue when trying to start a CashBox with a Queue that has no SCU assigned. We extended this functionality with a check to make you aware of configuration problems. As soon as you click Rebuild Configuration you are prompted with an error messages that informs you about the wrong configuration. 

![cashbox-wrong-queuede](images/sprint-78/cashbox-wrong-queuede.png)<br><br>

#### DE - Filter ReceiptJournals and ActionJournals by Type

To make it easier for you to take a look at specific kinds of ReceiptJournals or ActionJournals we added a filter to the ReceiptJournal and ActionJournal page. You should be able to select one of the following Type of receipts:

- All receipts
- Zero receipts
- Initial operation receipts
- Out of operation receipts
- Monthly receipts
- Annual receipts

![de-receiptcases](images/sprint-78/de-receiptcases.png)<br><br>

#### List of queues performance improvement

While working on the outletmanagement feature we noticed that we are doing a lot of duplicate work while loading the queues that is not necessary. We changed a few things in the order that we call our backends and could see 8x-10x faster page loading time depending on how many queues you have configured. Especially accounts with many queues should see far better load timings. The gif bellow should give you a good overview on the difference.

![new-export-page-at](images/sprint-78/queue_list_performance.gif)<br><br>

### User Management

#### Outlet Management

One of the main features we have tried to improve is the Outlet Management. For this purpose we have made several changes that should make it easier to use, configure and adding outlets. In the next sections we will go into the details of the new functionalities.

##### Distinction between primary and additional outlets

We got the feedback that even if our old outletpage contained all necessary information it was sometimes hard to differentiate between the primary outlet (main address of the company) and the other outlets that you can add for each of your additional outlets. To make sure that you see the different categories of outlets seperately we have reworked the UI to have two main sections. One for the primary outlet and one for all your other outlets

![new-outlets-page](images/sprint-78/outlets-page.png)<br><br>

##### Searching / Pagination and exchanging fields that are shown in the table for outlets

Additionally to the separation between the outlet categories we reordered some fields and added a search box to let you search through your outlets which should help you find specific outlets very easily. The look and feel of the page is now similar to what we have for our Middleware configurations. Also we added pagination to make sure we are not displaying to much information at once.

![new-outlets-page-search](images/sprint-78/outlets-page-search.png)<br><br>

## Next steps
In the upcoming sprints, the development team will continue to improve the outlet management feature. One very frequently asked feature is the bulk import for many outlets. Additionally to that we will improve the shopping experience so that you are able to buy outlet based products.

## Feedback
We would love to hear what you think about these features. To get in touch, please reach out to [info@fiskaltrust.at](mailto:info@fiskaltrust.at).