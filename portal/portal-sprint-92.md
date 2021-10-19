---
slug: /release-notes/portal/sprint-92
title: Sprint 92 (February 1, 2021)
---

# fiskaltrust.Portal - Sprint 92
_February 1, 2021_

**Improving user experience in portal**

In this sprint we have focused on improving the permission selection and also worked on several improvements of different features.

## Features

### E-Commerce

#### Productdescription, image and name not showing up correctly.
In some cases we have been facing issues when customers added products to the cart and didn't see the correct descriptions, image and name of the added products. Nevertheless, the product was correctly added to the cart, but the visualization was wrong. We fixed this behavior und users should be able to see the correct description, image and name now.

### User Management

#### Enforce permission selection when employees are invited
One issue that has been poping up frequently is the fact that users are unable to login because of missing permissions. While this fix can be prevented by assigning the employee read permissions right after the employee has been created, this second manual step is unnecessary complicated. For this reason we slightly changed the UI to extend the add employee dialog by a permission selection so that users can immediately assign the necessary access rights. We also added a check to inform users about issues if no read right is assigned.

![enforce-permission](images/sprint-92/enforce-permission.png)

#### Unable to continue with password reset
Another issue that customers have frequently been facing was a wrong validation that we have fixed now. Since we do have different complexity criterias for passwords we are performing checks in the backend, but have not performed this check on the clientside. When users have used a password that didn´t meet the complexity criteria they got a error message and the button was disabled. We have fixed this behavior and users should see a errormessage if something is wrong with the password.

 ![password-clientside-validation](images/sprint-92/password-clientside-validation.png)

#### ResetPassword for errorpage shows austrian mail address
We got the information that some customers that had problems with the resetpassword functionality were seing the AT support mail address even though they are using the Portal-DE. This lead to some confusions and customers had been reaching out to the AT colleagues instead of the DE support. We changed the view to have a market speficic address showing up.

## Next steps
In the next weeks we will focus on improving the stability and usabiltiy of the portal.

## Feedback
We would love to hear what you think about these improvements and fixes. To get in touch, please reach out to [feedback+portal@fiskaltrust.cloud](mailto:feedback+portal@fiskaltrust.cloud).