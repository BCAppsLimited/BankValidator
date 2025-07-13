---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Context Sensitive Help
description: Welcome brave explorer to the Bank Validator context sensitive help page. You most likely navigated to this page by clicking the help icon in Business Central (the one that looks like a question mark) and then clicking a link under the About apps on this page section. If the page you were looking at has a special topic dedicated to that page, you will have been taken straight to that topic heading when you clicked the link. If there is no dedicated help topic for the page you were on, you will have been shown the top of this page and will be reading this text, probably wondering why you are here, and what it was you were trying to do before you arrived.

# Author box
author:
    title:
    title_url: 
    external_url: 
    description: 

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Errors Explained
        url: /errors-explained
    next:
        content: End User License Agreement
        url: /eula
---

# AU Bank State Branches

The **AU Bank State Branches** page shows the BSB numbers that have been downloaded as source data for the Australian Bank Validation from the Australian Payments Network. The page serves no real purpose other than to let you see the data that is being used to validate your bank accounts.

# Bank Account Card

The **Bank Account Card** has been modified to show a **Bank Account Validation Result** field immediately after the **Bank Account No.** field on the **General** tab. If you do not see this field, it could be because you are in a Production environment and you do not have a license assigned or possibly the Bank Validator extension has not been activated. The value of this new field will show the results of attempting to validate the data in the **Bank Branch No.** and **Bank Account No.** fields. The validation is performed as soon as the page data is loaded and is re-validated whenever you edit the values in either the **Bank Branch No.** or **Bank Account No.** fields. You do not need to take action to perform the validation as this is handled automatically. The **Bank Account Validation Result** field is for information only and will not prevent any actions using the bank account record.

# Bank Validator Setup

Before you can use the Bank Validator app, you must select a **Default Validation Rule** (either *New Zealand Bank Validation* or *Australian Bank Validation*) and then set the **Active** field to on.

As the name suggests, all new bank accounts will be validated using the default validation rule. You can override the validation rule to be used for individual bank accounts if you wish.

You can think of this page as the control centre for bank account validation. You can use this page to get an overview of the state of bank accounts, manage the validation rule source data, and refresh the validation status of all accounts.

The **Bank Validator Setup** page has three sections:

- [Validation](#validation)
- [Validation Rule Source Data](#validation-rule-source-data)
- [Validation Results](#validation-results)

## Validation

![Image showing the validation group at the top of the Bank Validator Setup page.](/screenshots/contexthelp/BankValidatorSetupValidation.png)

The **Validation** group at the top of the page is where you select the **Default Validation Rule** and **Activate** the app. It also shows the date and time the **Validation Last Ran At**.

You will not be able to change the **Default Validation Rule** if the **Active** toggle is on.

Use the drop-down to select a **Default Validation Rule**. If your company is Australian, you should select *Australian Bank Validation*. If your company is New Zealand, you should select *New Zealand Bank Validation*. You must select a default validation rule other than *No Validation* to be able to continue.

Once you have selected your default validation rule, click the **Activate** toggle control. You will notice that the **Default Validation Rule** is greyed out and can no longer be changed.

## Validation Rule Source Data

![Image showing the validation rule source data subpage on the Bank Validator Setup page.](/screenshots/contexthelp/BankValidatorSetupValidationRuleSourceData.png)

This subpage includes a line for each source of data that is used as part of a validation rule. The fields are explained below.

| Field | Description |
|-|-|
| Validation Rule | Specifies the validation rule that this source data applies to. This is used to validate bank accounts against the rules defined in the system. |
| Resource Name | Specifies the name of the resource that this validation rule source data is associated with. |
| Table | Specifies the name of the table where the validation source data is stored. |
| Record Count | Specifies the number of records in the table for this validation rule source data. You can use the drilldown on this field to explore the underlying source data. |
| Last Checked At | Specifies the date and time when the validation rule source data was last checked for updates. |
| Last Imported At | Specifies the date and time when the validation rule source data was last imported. |
| Last Imported File Unique Identifier | Specifies the unique identifier of the file that was last imported for this validation rule source data. This could be a file name or an ETag. It is used to determine whether the system needs to pull down newer data from the data provider. |

You can use this part to drill-down into the validation source data records such as the [NZ Banks](#nz-banks), [NZ Bank Branches](#nz-bank-branches), or [AU Bank State Branches](#au-bank-state-branches) by clicking on the associated **Record Count** for each line.

## Validation Results

![Image showing the validation results on the Bank Validator Setup page.](/screenshots/contexthelp/BankValidatorSetupValidationResults.png)

The validation results are shown in the FactBox pane as a series of tiles or "cues". Each cue shows the number of bank accounts that have been validated grouped by a particular state. The cues and their meaning is shown below.

| Cue | Description |
|-|-|
| Valid Accounts | Specifies the number of bank accounts found during validation that are valid. |
| Valid Accounts with Duplicates | Specifies the number of bank accounts found during validation that are valid but have been used more than once in the system. |
| Invalid Accounts | Specifies the number of bank accounts found during validation that are invalid. |
| All Accounts | Specifies the number of bank accounts found during validation. |

Clicking on any cue will take you to the [Validated Bank Accounts](#validated-bank-accounts) list with a filter applied to only show the accounts that correspond to the cue.

# Customer Bank Account Card

The **Customer Bank Account Card** has been modified to show a **Bank Account Validation Result** field immediately after the **Bank Account No.** field on the **General** tab. If you do not see this field, it could be because you are in a Production environment and you do not have a license assigned. The value of this new field will show the results of attempting to validate the data in the **Bank Branch No.** and **Bank Account No.** fields. The validation is performed as soon as the page data is loaded and is re-validated whenever you edit the values in either the **Bank Branch No.** or **Bank Account No.** fields. You do not need to take action to perform the validation as this is handled automatically. The **Bank Account Validation Result** field is for information only and will not prevent any actions using the bank account record.

# Employee Card

The **Employee Card** has been modified to show a **Bank Account Validation Result** field immediately after the **Bank Account No.** field on the **Payments** tab. If you do not see this field, it could be because you are in a Production environment and you do not have a license assigned. The value of this new field will show the results of attempting to validate the data in the **Bank Branch No.** and **Bank Account No.** fields. The validation is performed as soon as the page data is loaded and is re-validated whenever you edit the values in either the **Bank Branch No.** or **Bank Account No.** fields. You do not need to take action to perform the validation as this is handled automatically. The **Bank Account Validation Result** field is for information only and will not prevent any actions using the bank account record.

# NZ Bank Branches

The **NZ Bank Branches** page shows all of the branches that have been imported from the PaymentsNZ Bank Branch Register file. The page serves no real purpose other than to let you see the data that is being used to validate your bank accounts.

# NZ Banks

The **NZ Banks** page shows all of the unique banks that have been imported from the PaymentsNZ Bank Branch Register file. Each bank also shows the validation algorithm that will be used to determine if the bank's check digit is correct. There is a drill down field showing a count of the number of branches associated with this bank. Use the drill down to show the related branches. 

# Payment Journal

The **Payment Journal** page has been modified to show a **Bank Account Validation Result** field immediately after the **Recipient Bank Account** field. If you do not see this field, it could be because you are in a Production environment and you do not have a license assigned. The value of this new field will show the results of attempting to validate the data in the **Bank Branch No.** and **Bank Account No.** fields from the related recipient bank account. The fields being validated will depend on the **Account Type** field as follows:

| Account Type       | Bank Account Validation Result Shows |
|--------------------|--------------------------------------|
| G/L Account        | No value shown. |
| Customer           | Validation of **Customer Bank Account** for Account No. and Recipient Bank Account. |
| Vendor             | Validation of **Vendor Bank Account** for Account No. and Recipient Bank Account. |
| Bank Account       | Validation of **Bank Account** for Account No. |
| Fixed Asset        | No value shown. |
| IC Partner         | No value shown. |
| Employee           | Validation of **Employee** for Account No. |
| Allocation Account | No value shown. |

# Vendor Bank Account Card

The **Vendor Bank Account Card** has been modified to show a **Bank Account Validation Result** field immediately after the **Bank Account No.** field on the **General** tab. If you do not see this field, it could be because you are in a Production environment and you do not have a license assigned. The value of this new field will show the results of attempting to validate the data in the **Bank Branch No.** and **Bank Account No.** fields. The validation is performed as soon as the page data is loaded and is re-validated whenever you edit the values in either the **Bank Branch No.** or **Bank Account No.** fields. You do not need to take action to perform the validation as this is handled automatically. The **Bank Account Validation Result** field is for information only and will not prevent any actions using the bank account record.

# Validate Bank Accounts

The **Validate Bank Accounts** processing job is a report with no layout that will allow you to filter on the tables that will be validated, namely:

- Bank Account
- Customer Bank Account
- Vendor Bank Account
- Employee

To allow you to skip validation for blocked customers or vendors, we have added a **Customer Blocked** and **Vendor Blocked** field which allows you to only validate customer or vendor bank accounts when the related customer or vendor matches the filter.

Prior to beginning the validation, the process will check the current validation source data files against the last imported files and, if there is a later file available, the new file will be imported to update the validation source data.

For each matching record found, the system will validate the combination of **Bank Branch No.** and **Bank Account No.** using the [validation rules](/BankValidator/validation-rules). Any records where both the **Bank Branch No.** and **Bank Account No.** fields are blank will be skipped, but other validation results will write a record showing the results of the validation to the **NZ Bank Account** table which you can review on the **NZ Bank Accounts** page. The process can be scheduled to run on a recurring basis and we recommend doing this in order to ensure the Bank Branch Register data is kept up to date. 

# Validated Bank Accounts

The **Validated Bank Accounts** page shows the list of results from the validation of bank account fields.

![Image showing the Validated Bank Accounts list page.](/screenshots/contexthelp/ValidatedBankAccounts.png)


| Field                     | Description |
|---------------------------|-------------|
| Used On | Identifies the table and key fields of the record that contains the back account. Click this field to navigate to relevant bank account card. |
| Validation Rule | Shows the validation rule that has been selected for validation for this particular bank account. When a new bank account is validated, it will always use the default validation rule, which is configured in the **Bank Validator Setup** page. Tha validation rule to use can be changed on the **Validated Bank Account Card** which can be accessed by clicking the contents of the **Bank Account Validation Result** field which is displayed on the page that contains the bank account being validated (i.e. the Bank Account Card, the Vendor Bank Account Card, the Customer Bank Account Card, or the Employee Card.) |
| Full Bank Account | The normalised full bank account number.[^1] |
| Status | The result of the validation. For an explanation of the values, see the section for the matching Result Status in the [Errors Explained](/BankValidator/errors-explained) topic. |
| Used Count | The count of records that are using the same bank account number. Any record that shows a value here that is greater than one is a duplicate. |
| Validity Last Checked | The date and time the validity of this bank account was last checked. |
| First Used | The date and time this bank account value was first used for the related **Used On** record. |
| History Count | The number of different accounts that have been used for the related **Used On** record. Use the drill-down on this field to show the historical records. |

From the previous image you can see that each bank account that has been validated (we do not show bank accounts where neither the **Bank Branch No.** nor the **Bank Account No.** fields were entered) is listed with a **Status** and a colour coding. The meaning of the colour coding is as follows:

| Style Name | Style | Meaning |
|-------|--------|---------|
| Subordinate | Grey | This is not the current bank account used on this record and shows historical values. Historical values are not shown on the main NZ Bank Accounts page but can be seen by drilling down on the **History Count** field. |
| Favourable | Bold + Green | The account is valid. |
| Ambiguous | Yellow | The account is valid but the Used Count is more than one, meaning the same bank account number has been used in multiple places. |
| Unfavourable | Bold + Italic + Red | The account is not valid. Use the **Status** field or navigate to the **Used On** record for more details. |

The **Bank Validator Setup** has some actions that can be used to update the status of all accounts or manually refresh the Bank Branch Register data and BSB Dictionary. These actions are described in the following sub-topics.

## Validate Action

This action will validate all accounts giving you an overview of how many accounts there are and whether they are valid or not. It will also attempt to update the validation source data by pulling the latest files from the data provider. Because of the update of source data feature, we recommend you schedule this process to run at least once a week to keep the validation source data up to date. See the [Schedule Validation](/BankValidator/install-guide/#schedule-validation) section in the configuration section of the install guide help topic.

Select the **Validate** action and you will be presented with the options page for the **Validate Bank Accounts** process.

![Image showing the options for the Validate Bank Accounts process.](/screenshots/install/ValidateBankAccountsProcess.png)

You can use this options page to filter on accounts to be validated (for example you can exclude blocked accounts), or to schedule the process to run on an automated basis.

Results of the validation will be stored and the FactBox cues will be updated to reflect the new totals.

We recommend scheduling this process to run once a day or once a week automatically and then manually opening the **Bank Validator Setup** page to check there are no invalid bank accounts in the system.


## Refresh Data Action

Select the **Refresh Data** action to trigger a check of the source data used for the validation process which includes the Bank Branch Register data provided by PaymentsNZ and the BSB Directory provided by the Australian Payments Network. The remote data sources will be compared with the copy of the data loaded into Business Central. Every time this process is run (either manually via this action or automatically as part of the **Validate** action), the file name or ETag is checked first and if we have already loaded the file with the same name, the system will do nothing. If the file provided by the data provider is different to the file we have previously loaded, the new file will be downloaded and imported.

The **Record Count** field on each of the data sources shows the result of the import. You can click the drill-down on the **Record Count** field to show the records that are used in the validation routines.  

## Restore Data Action

You should never need to select this option. The Bank Validator includes the latest PaymentsNZ Bank Branch Register and Australian Payments Network BSB Directory data which will be available as soon as the extension is installed. Select the **Restore Data** action to force the system to overwrite whatever validation source data is in the system with the data that came with the application.

# Validated Bank Account Card

The **Validated Bank Account Card** is launched by clicking the contents of the **Bank Account Validation Result** field on any of the following pages:

- Bank Account Card
- Customer Bank Account Card
- Vendor Bank Account Card
- Employee Card

![Image showing a validated bank account.](/screenshots/contexthelp/ValidatedBankAccount.png)

The main purpose of the page is to allow you to change the Validation Rule that should be used for this particular bank account.

It's also useful to see the full validation result message in a large text box.

---

[^1]: The combination of the **Bank Branch No.** and **Bank Account No.** fields where, for accounts that use the New Zealand Bank Validation rule, the formatting has been padded to have eight base account digits and four suffix digits resulting in BB-bbbb-AAAAAAAA-SSSS. For accounts using the Australian Bank Validation rule, no padding is applied to the data, even if it is valid.