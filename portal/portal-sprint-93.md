---
slug: /release-notes/portal/sprint-93
title: Sprint 93 (February 15, 2021)
---

# fiskaltrust.Portal - Sprint 93
_February 15, 2021_

**Improving user experience in portal**

In this sprint we were focused fixing several issues and also trying to improve the usability.

## Features

### E-Commerce

#### Wrong Move Entitlements product is added to cart(DE market)
Previously, we were facing an issue while putting some products into the cart.
in some cases, when we put the Move Entitlements product into the cart,  the product was different from the one added to the shopping cart.
With this release, this should be fixed and products should be correctly added to the shopping cart.

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
We would love to hear what you think about these improvements and fixes. To get in touch, please reach out to [info@fiskaltrust.at](mailto:info@fiskaltrust.at).