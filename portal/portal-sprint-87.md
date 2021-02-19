---
slug: /release-notes/portal/sprint-87
title: Sprint 87 (November 23, 2020)
---

# fiskaltrust.Portal - Sprint 87
_November 23, 2020_

**Improve Shopping experience**

The main focus of this sprint was to further enhance the Portal's Shopping experience, especially the selection of the outlet and the basic visualization of different categories of products. 

## Features

### Middleware Configuration

#### 404 error while loading packages during Updating a configuration
Some users were facing an issue that lead to a 404 when trying to reload packages in the UpdateConfiguration page. We have fixed this bug and now reloading packages should be possible without problems again.

### E-Commerce

#### Filtering based on category
One of the first steps that we are taking to improve the shopping experience is the possiblity to filter items based on different categories. This should give users the ability to quicker find the products that they are searching for.

#### Improving location selection
Another problem that we have noticed in the past is the fact that the current UI makes it very hard to keep track of the currently selected outlet. Additionally, we got the feedback that the Dropdown is not sufficient for most users and that more information would be helpful.

To improve this behavior we moved the outlet selection to the header and also made it sticky:

![OutletSelector_1.png](images/sprint-87/outlet-selector-1.PNG =800x) 

To make it easier to see which outlet you want to select we also overworked the Dropdown and are using a Modal dialog now.

![OutletSelector_2.png](images/sprint-87/outlet-selector-2.PNG =800x)

#### Storing outlet selection in usersession
While our users are performing a rollout they are usually purchasing multiple products and also move around pages. In the past we didn't store the outletselection, which required the user to select it again after each page reload. With these changes we now save the selected outlet in the user session and it is stored as long as the user is logged in.

### User Management

#### Username not changed after updating
Some users reached out to us, that they have issues while trying to update the username. This issue was caused by an internal systemchange and has been fixed with the latest release.

#### Improve errormessage when surrogating to accounts doesn't work
In the past we noticed that in cases where the PosDealer was missing Read Claims for the connected PosOperators it was very hard to see, why you haven't been able to surrogate. We extended the current approach by a better errormessage so that it is easier to see what went wrong.

![Screenshot_1.png](images/sprint-87/surrogation-error-message.png =800x)

## Next steps
In the next sprints, we will again focus on further improving the user experience in our Portal, mostly focused on an enhanced shopping experience.

## Feedback
We would love to hear what you think about these improvements and fixes. To get in touch, please reach out to [info@fiskaltrust.at](mailto:info@fiskaltrust.at).