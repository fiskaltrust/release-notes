In this Sprint, we were focused on establishing a secure platform for configuring Middleware components, as well as creating a prototype for the new Orders page.

Features
User Management
Unable to find the Login option in Portal
We frequently got the information that (new) customers could not find the Login to Portal. Until now, if a user wanted to login/register to portal, it was not clear while navigating the main page of https://portal.fiskaltrust.de. We changed the existing  button to make clear that the login / registration is happening here:  
 
(picture???)
Clarify usage of CashBox State indicator  
With the purpose of improving usability, the configuration change status and rebuild button have been merged into one column.

![image.png](https://fiskaltrust.visualstudio.com/6902c73f-5b4e-498b-8f0e-a130ceee1cc8/_apis/git/repositories/97165144-8048-4407-905f-c23eaee320b8/pullRequests/3284/attachments/image.png) 

Data Exports
The TAR file is finally in a state that is correctly usable and therefore we should officially release and enable it for all customers.  The preview flag has been discarded, and the feature flags are cleaned.

Before:
![image.png](https://dev.azure.com/fiskaltrust/6902c73f-5b4e-498b-8f0e-a130ceee1cc8/_apis/git/repositories/97165144-8048-4407-905f-c23eaee320b8/pullRequests/3273/attachments/image.png) 

After:
![image (2).png](https://dev.azure.com/fiskaltrust/6902c73f-5b4e-498b-8f0e-a130ceee1cc8/_apis/git/repositories/97165144-8048-4407-905f-c23eaee320b8/pullRequests/3273/attachments/image%20%282%29.png) 

Stefan: I think we should exchange that part below to be more feature focused. 

React-based Orders Page
A React based Prototype of the Orders Page has been created, to deal with issues such as failed orders, long loading times of the ordering page, and so on. The following components have already been implemented:
A new API Controller, called OrderController, that can be called from JavaScript and enables us to load salesorders for a specific account. 
 A  GetAccountOrders endpoint, which will return dummy data.
A feature flag has been added and IoC for the web API is supported.
An API Controller that supports data access of SalesOrders on server level, as well as pagination, filtering and ordering in the data layer, pulling only the necessary data that is requested in the view. 
A new Table that renders SalesOrders data has been implemented.


Figure 01. /api/orders response data including paged model
![image (2).png](https://fiskaltrust.visualstudio.com/6902c73f-5b4e-498b-8f0e-a130ceee1cc8/_apis/git/repositories/97165144-8048-4407-905f-c23eaee320b8/pullRequests/3283/attachments/image%20%282%29.png) 


