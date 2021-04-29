In the last Sprint, our main focus was improving portal performance.
### Features

#### User Management

##### Assigning a unique identifier to the CashBoxIdentification to ensure law compliance in Germany
A new checkbox was added to the Queue Create Page in Germany. When users click on it, this autogenerates a unique CashboxIdentification, removing the fear of creating duplicates.

![CashBoxIdentification.png](images/sprint-97/CashBoxIdentification.png) 

##### New page for the overview of the signature creation units (DE market) 
A new page was integrated that offers a quick overview of the signature creation units for DE market, as well as search functionality and the option to configure the SCUs. Response times of the page are faster and the overall data overview is impoved. Aside from previous functionalities that are still there, some additional points can be found:
 
- Outlet number is shown inside of the table
- Serial number is moved to expander
- Certification identification and number of the signatures are added to expander
 
![image.png](images/sprint-97/40999.png) 
 
##### Cleaning up of old service Helpers
Old service helpers are removed from the German market, to ensure that components that are not available for usage in Portal are not displayed, thus avoiding confusion. These old Global Service 1.2 Helpers are not displayed in the German Portal (Sandbox & Production) anymore:
- Helpers page
- Cashbox edit by list page
- Cashbox edit by drag&drop page
 
##### Save search in localstorage
PosDealers can now find quicker the info they need to work with, when persisting the state of tableviews across sessions.  So, now when a User types a searchterm and refreshes the page, the same searchterm is appearing. Additionally, if a user selects an order for the page, the same order will still appear after refreshing the page. Similarly, the same page will appear after refreshing the page when a user changes pagination.

##### Clear AccountSettings for localstorage based settings
Now, account settings page is able to support clearing of the filters that are used on cashbox page, SCU page, orders page etc. Users can easily check the pages where they are using tablestates, so that they can clear them when necessary. Aside from that, everything works as before.

#### Remove numbers of status indicators for non-Admin users
To make sure that we make it easy for users to understand what is going on with status of the orders, we differentiate succeeded orders from failed orders without showing confusing information. This was achieved by removing the number status indicators for non-admin users.

