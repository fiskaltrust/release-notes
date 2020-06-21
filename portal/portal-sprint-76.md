# fiskaltrust.Portal - Sprint 76
_June 22, 2020_

In the Sprint 76 update of the fiskaltrust.Portal, we are excited to announce that we have a completely new data export experience which not only should make selecting specific exports easier, but is also able to finish exports within a few minutes instead of several hours, even for very large queues.

In addition, we've added an automatic onboarding flow to the German sandbox environment. PosDealers are now able to onboard PosOperators without further manual actions on their side.

These major changes are (among others) described in more detail in the following sections.

## Features and stability improvements

### Data exports 

#### New data export experience
The export experience in the Portal - i.e. the functionality to write stored Middleware data like receipt requests and responses into different file types - was completely overhauled in this sprint. The previous implementation dated back to earlier days and overall far smaller queues, and did not fit the requirements of large customers anymore. In addition to this, we regularly received feedback that the user interface was not intuitive enough.

The key features of the new functionality are:
- Drastically improved performance, shrinking down the time for an export from hours to only minutes, even for very large queues. For example, an XML export of a queue with 800,000 receipts now takes only 15 minutes on average. Exporting smaller queues will usually be finished in 2-3 minutes.
- Increased reliability of the overall process. Especially for large queues, the old export tended to fail sometimes, requiring users to queue several exports until one succeeds. This was resolved, as we  observed very high success rates in our ongoing tests.
- An overall simpler architecture makes it far easier for the development to implement new export types (e.g. the French export, and the upcoming DSFinV-K export).
- A simpler user interface that focuses on the main requirements when requesting an export. Now, users can easily select the export and (if required) optional export targets.

![export-page](images/sprint-76/export-page.png)

#### Simplified upload target configuration
The previous drag-and-drop functionality for export targets was replaced by a simpler checkbox-based approach. While this slightly limits the customizability (previously, it was possible to specify multiple targets of the same type), our user tests show that the user experience is far easier to understand and use.

**Even if no target is specific, the data will still be stored on our servers and can be downloaded via the Portal anytime.**

When a target is selected, users can configure the required options:

![ftp-upload](images/sprint-76/ftp-upload.png)

#### CSV export
In addition to the _full XML export_, a CSV export was added that exports the full data schema of the Middleware into CSV files. Among others, this includes all receipt requests and responses that were processed, journals, and all internal data that is stored in the Middleware database.

#### FR export (Preview)
A preview version of the French export (_FR-DEX_) was added to the [French sandbox](https://portal-sandbox.fiskaltrust.fr). In accordance with the InfoCert certification requirements, it can be used to export Queue data into CSV files, split by the type of the receipt chain.

### Improved usability of receipt range slider
Previously, using the receipt range slider to configure exports often lead to issues when used with large queues. The performance of this component was greatly improved, and it should thus be far more stable now, even for very large export configurations.

### Additional information on parameters in journal.json
In addition to displaying it in the portal, we now include the receipt range of exports into the `journal.json`. This should make it easier to track exports after they were downloaded.

### E-Commerce

#### Separate template-products by market
In the past we have not separated the template-based-products for different markets. This led to the fact that we have shown all of these products in the shop. We have made some changes to being able to separate these products between the markets and now only products that are really available for the given market are shown.

### Middleware Configuration

#### Configuring Diebold Nixdorf SCU
Similar to the other SCUs, we added a Diebold Nixdorf specific configuration page now that should make configuring the Diebold Nixdorf SCU easier for the users.
<br/>
<br/>
![diebold-nixdorf-scu-configuration](images/sprint-76/diebold-scu-configuration.png)<br><br>

#### Bulk update functionality not working
When updating a Configuration in the Bulkupdate Interface a 500 error occurred. This issue was fixed and the functionality for updating middleware componenents and rebuilding the cashboxes automatically is back again.
<br/>
<br/>
![bulk-update-page](images/sprint-76/bulk-update-page.png)<br><br>


### User Management

#### Sandbox Feature - Auto-Onboarding of PosOperators (DE only)
We have been getting many questions on how to make the onboarding experience easier for PosDealers. Since most of the PosDealers are managing many customers with the ft-Portal it is sometimes hard to get everybody on board. In the past we already had the invitation process which created the accounts for the PosOperator and sent an invitation to the PosOperator that needed to be accepted. This often led to a lot of work and sometimes it made the onboarding experience very bad. 

With the latest changes that we have rolled out to our Sandbox environment customers now can test the new, fully automated onboarding process. To enable this feature you have to activate the new `Cash register dealer opt-in autoinvitation` feature as seen in the screenshot bellow.
<br/>
<br/>
![role-optin-activation](images/sprint-76/role-optin-activation.png)<br><br>

Because of the fact that this is a PosDealer-only feature you need to have the PosDealer role activated as well. The contract that is currently showing up is a placeholder contract and it will be replaced by an actual contract before going into production.

After that role has been activated you should see two new buttons in the PosOpeartors/Invitations view. 
<br/>
<br/>
![autoinvitation-posoperators](images/sprint-76/autoinvite-posoperators.png)<br><br>

Similar to the usual invitation feature you can either proceed for all pending invitations or just one by one. 

As soon as you have clicked one of the buttons the following steps are executed:

1. Creation of PosOperator Contact / User
1. Creation of PosOperator Account
1. Creation of Connection between PosOperator and PosDealer Accounts
1. Enable Full Permissions on PosOperator Account for PosDealer
1. Generate Random Password for PosOperator
1. Enable Connection between PosOperator and PosDealer Accounts
1. Create PosOperator contract and sign with the PosDealer´s Accountname
1. Save created PosOperator-Contract to the accountstorage of the PosOperator so that the PosOperator can access it via the portal
1. Save the opt-in-autoinvitation contract of the PosDealer to the accountstorage of the PosOperator (Prefix: posdealer-opt-in-autoinvitation_autoinvitation_{posDealerAccountId})
1. Enable PosOperator role for PosOperator
1. Send an Email to the PosOperator with the following documents:

- PosOperator Contract (signed by the PosDealer)
- PosDealer Opt-In Contract
- Additional files that can be added by the PosDealer during the invitation

After performing these steps the PosOperator Account is properly configured and can be used with the fiskaltrust Services. If the PosOperators want to login they will have to reset their password during the first login. To make this experience as easy as possible the email that the PosOperator gets contains a password reset link.

## Next steps
In the upcoming sprints, the development team will mostly focus on further improving the customer onboarding experience in the Portal.

In addition to this, we will continue to improve the _Export_ features in the portal and offer additional exports for DE.

## Feedback

We would love to hear what you think about these features. For getting in touch with us reach out to [info@fiskaltrust.at](mailto:info@fiskaltrust.at).