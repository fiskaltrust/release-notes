# fiskaltrust.Portal - Sprint 80
_August 31, 2020_

**Shop and production improvements**
TODO

## Features

### E-Commerce
- buying and producing digital products is now fully possible
- carefree + ako are buyable from the outlet page directly
- queue shows pos archive state
- shipping to outlets is implemented
- invoices show surrogation and outlet information
- move entitlements
- account specific price lists
- main outlet is now default in the german shop

### Data exports
- stability fixes when communicating with backend systems
- improved export creation form to properly validate form inputs

### Middleware Configuration
- new template variables: outlet_number + queue{0-9}_id_base64withoutspecialchars 
- required configuration (connection string) is now displayed in mysql config per default
- we fixed an issue in our backend systems that prevented the Austrian/French offline launcher from starting

### User Management
- in some cases, issues during registrations were not printed to the UI, which lead to confusion and issues later. all errors are now properly displayed
- we fixed an issue that could occur if a user deactivated the posdealer role while the auto invitation role was still active (they have to be disabled in the right order now)
- when the primary/first employee of an account was removed in the portal, it could lead to issues and a broken state. we hence disabled this option (please contact our support in cases were you need to remove/change the primary contact).

### Various
- we display the latest portal release notes in the lower left corner of the portal's homepage now

## Next steps
We will continue improving our e-commerce functionalities in the Portal in the upcoming sprints, both for the German and the French market. Additionally, we will continue to work on German features like the DSFinV-K export (both the cloud and the offline-version). Finally, we continuously work on improving the usability of our products, especially the Portal.

## Feedback
We would love to hear what you think about these features. To get in touch, please reach out to [info@fiskaltrust.at](mailto:info@fiskaltrust.at).
