In the last Sprint, aside from working on the new React Order Page -among others, we made sure that React components can be used with translations from the translation API-, our main focus was to improve performance of the portal and the rollout experience.
 
### Features

#### User Management

##### Assigning a unique identifier to the CashBoxIdentification to ensure law compliance in Germany
A new checkbox was added to the Queue Create Page in Germany. Clicking on it lets users generate a unique CashboxIdentification based on the QueueId that’s about to be created.

##### New page for the overview of the signature creation units (DE market) 
As a part of the migration process of the portal to react-based components, a new page was integrated that offers a quick overview of the signature creation units for DE market, as well a search functionality and the option to configure them. Aside from previous functionalities that are still there, some additional points can be found:
 
- Outlet number is shown inside of the table
- Serial number is moved to expander
- Certification identification and number of the signatures are added to expander
 
![image.png](images/sprint-97/40999.png) 
 
##### Cleaning up of old service Helpers

As part of the migration of the Helpers page, old service helpers are removed from the German market, to ensure that components that are not available for usage in Portal are not displayed, thus avoiding confusion. These old Global Service 1.2 Helpers are not displayed in the German Portal (Sandbox & Production) anymore:
- Helpers page
- Cashbox edit by list page
- Cashbox edit by drag&drop page
 
##### Saving search in localstorage
As a part of the migration process of the CashBoxes pages, we worked on persisting the state of tableviews across sessions, so that PosDealers can find quicker the info they need to work with. So, now when a User types a searchterm and refreshes the page, the same searchterm is appearing. Additionally, if a user selects an order for the page, the same order will still appear after refreshing the page. Similarly, the same page will appear after refreshing the page when a user changes pagination.

##### Clear AccountSettings for localstorage based settings
By extending the existing account settings page to support clearing of the filters that are used on newly integrated react pages (cashbox page, SCU page, orders page), users can easily check the pages where they are using tablestates, so that they can clear them when necessary.
