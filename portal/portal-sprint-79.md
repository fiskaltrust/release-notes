# fiskaltrust.Portal - Sprint NUMBER
_August 3, 2020_

**DSFinV-K master data handling & outlet bulk imports**

Aside from further polishing the fiskaltrust.Portal's outlet feature, most development effort of this sprint was put into properly injecting DSFinV-K-relevant master data (e.g. account information, outlet data, etc.) into the middleware configuration so it can be processes by the [Middleware 1.3.4](../middleware/middleware-1.3.4.md). This enables us to finish the DSFinV-K export prototype in the next sprints.

## Features

### Data exports

#### Automatic updates on the export status page
To further improve the export experience, the status on the export page is now automatically updating for running exports. Thus, it's not required anymore to refresh the page when waiting for an export to finish. Aside from the changed status icon in the table, users will be notified with a toast notification, as shown in the picture below:

![export-page-refresh](images/sprint-79/export-page-refresh.jpg)

#### Compress export results
All output files of exports are now compressed to a zip file after each successful export. This should especially simplify processes when dealing with exports that create many files (like FR-DEX and DSFinV-K).

The only file that is not added to the archive is _journal.json_, which contains user-relevant events that happened during the export (e.g. details about a possibly broken receipt chain).

#### Improved XML export compatibility
In some cases, users were unable to open the output file of the XML export in Excel due to compatibility issues when using special characters like "<" in certain portions of the data. This issue was resolved.

### E-Commerce

#### Replace UID check error with warning
To fulfill legal requirements, the fiskaltrust.Portal displays an error message on the checkout page if master data values are detected to be invalid. Due to a limitation of the EU service that we use to validate company data, it's currently not possible to properly validate German VAT numbers. 

Hence, we now display a warning instead of an error message in the shop that gives the user the ability to manually check if the entered VAT number is correct before proceeding the checkout process.

![outlet-csv-import](images/sprint-79/shop-uid-warning.png)

**Please note that customers are still required to set their companies' VAT numbers in the master data section of the Portal.**

### Middleware Configuration

#### Agency management
The DSFinV-K specification requires the ability to handle agency businesses - a common example for this is selling toll stickers for the ASFINAG. In these cases, the company is selling something in the name of a third party company, which both has to be printed on the receipt and is written into the DSFinV-K export.

With the changes we made, it's now possible to handle these agencies within accounts. Added agencies will be assigned an ID that should be sent to the Middleware when performing agency business transactions (via ftChargeItemCaseData, [as described in the docs](https://docs.fiskaltrust.cloud/doc/interface-doc/doc/appendix-de-kassensichv/data-structures/data-structures.html#charge-items-entry)).

The Portal will then automatically inject this data into the configuration, as described [here](../middleware/middleware-1.3.4.md). This process will furthermore be described in more detail in the upcoming _procedural documentation_ for the DSFinV-K export.

![agencies](images/sprint-79/agencies.png)

#### Outlet CSV import
To simplify the outlet management for large customers, we added a new feature that allows importing outlets from CSV files. It's also possible to download a sample CSV that contains the required data schema.

![outlet-csv-import](images/sprint-79/outlet-csv-import.png)

After uploading the file, an additional page is shown that shows the to-be-imported data. Possible validation errors and their detailed description are also displayed on that page (if they occur). These validations e.g. include checks for duplicate outlet numbers, invalid characters, or schema mismatches.



### User Management

## Next steps
The next sprints will be mostly focused on further improving the shop experience by simplifying the current processes and streamlining the offered products. We are also working hard on improving the Middleware and preparing additional product runtimes for customers with cloud cash registers.

## Feedback
We would love to hear what you think about these features. To get in touch, please reach out to [info@fiskaltrust.at](mailto:info@fiskaltrust.at).