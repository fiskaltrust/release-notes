In this Sprint, we were focused on establishing a secure platform for configuring Middleware components, as well as creating a prototype for the new Orders page.

## Features

### User Management

#### Unable to find the Login option in Portal

We frequently got the information that (new) customers could not find the Login to Portal. Until now, if a user wanted to login/register to portal, it was not clear while navigating the main page of https://portal.fiskaltrust.de. We changed the existing  button to make clear that the login / registration is happening here:  
 
(picture???)

#### Clarify usage of CashBox State indicator  

With the purpose of improving usability, the configuration change status and rebuild button have been merged into one column.

![image.png](https://fiskaltrust.visualstudio.com/6902c73f-5b4e-498b-8f0e-a130ceee1cc8/_apis/git/repositories/97165144-8048-4407-905f-c23eaee320b8/pullRequests/3284/attachments/image.png) 

### Data Exports

The TAR file is finally in a state that is correctly usable and therefore we should officially release and enable it for all customers.  The preview flag has been discarded, and the feature flags are cleaned.

Before:
![before.png](https://github.com/fiskaltrust/release-notes/blob/user/opa/release_notes_94/portal/images/sprint-94/before.png)

After:
![after.png](https://github.com/fiskaltrust/release-notes/blob/user/opa/release_notes_94/portal/images/sprint-94/after.png) 


### Prototype of the new Orders Page

A Prototype of the new Orders Page has been created. In the past, issues such as failed orders, long loading times of the ordering page, TSEs not received at the checkout and so on, arose very frequently.  Various components of the new Orders Page have already been integrated to deal with the aforementioned issues, and more information will be shared, as more changes are implemented:






