The goal this past Sprint was to work on the migration of the Outles page and the Queue page to React, as part of our effort to improve performance of roll-out relevant Portal sections.

### User Management

## Email confirmation

Very often customers were entering accidentally a misspelled email address and were thus unable to login. By adding a confirmation email so the user has to submit it for a second time. An error will be issued if the two entries don’t match 

Missing pic

## New React-based index page for Outlets

Users that are visiting the Outlet page, will now see the new version of it.
They will be able to quickly see all outlets, so they  can search them, configure them and also have access at the most important information.

Amongst the fields displaying in the main list are the following:

- OutletNumber
- Name
- Location Id
- Address
- CareFree subscription button (DE only)
   - Indicate active CareFree feature
   - Add carefree to basket
   - Extend carefree
- AKO subscription button (DE only)
   - Indicate active AKO feature
   - Add AKO to basket
   - Extend AKO
- Edit

Additionally, there is an extra section for the primary outlet and the fields for it.
The fields for importing, downloading and adding new outlets are also migrated.

Missing Pics

New React-based index page for Queue DE

In the new React-based index page for Queue in the German market, users will be able to quickly overview all queues, so that they can search them, configure them and also get the most important information. All previous UI/UX elements and functionalities are kept. 

Amongst the fields displaying in the main list are the following:
- Description 
- Localisation: CashBoxIdentification
- Active


The following actions are available:
- Journals
   - List Receiptjournals
   - List ActionJournals
- Export
-    Button to perform exports
   - Sandbox: Always enabled
   -Production: Only enabled if Queue has active PosArchive feature
- PosArchive Feature
    - The button should indicate if the PosArchive is available for this queue
- Action Buttons
   - Select SCU 
   - Configuration
   - Edit
   - Delete (Disabled with tooltip)
   
The following fields are shown in Details:
- Package Name
- Package Version
- URL 
- CashBox

Missing Pic
