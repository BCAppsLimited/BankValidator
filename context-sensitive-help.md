---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Context Sensitive Help
description: Welcome brave explorer to the NZ Bank Account Validator context sensitive help page. You most likely navigated to this page by clicking the help icon in Business Central (the one that looks like a question mark) and then clicking a link under the About apps on this page section. If the page you were looking at has a special topic dedicated to that page, you will have been taken straight to that topic heading when you clicked the link. If there is no dedicated help topic for the page you were on, you will have been shown the top of this page and will be reading this text, probably wondering why you are here, and what it was you were trying to do before you arrived.

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
        content: The Algorithm
        url: /the-algorithm
    next:
        content: End User License Agreement
        url: /eula
---

# Bank Account Card

The **Bank Account Card** has been modified to show a **Bank Account Validation Result** field immediately after the **Bank Account No.** field on the **General** tab. If you do not see this field, it could be because you are in a Production environment and you do not have a license assigned. The value of this new field will show the results of attempting to validate the data in the **Bank Branch No.** and **Bank Account No.** fields. The validation is performed as soon as the page data is loaded and is re-validated whenever you edit the values in either the **Bank Branch No.** or **Bank Account No.** fields. You do not need to take action to perform the validation as this is handled automatically. The **Bank Account Validation Result** field is for information only and will not prevent any actions using the bank account record.

# Bank Account Validation Setup

There are no setup fields to configure on the **Bank Account Validation Setup** but you can think of this page as the control centre for bank account validation. You can use this page to get an overview of the state of bank accounts, manage the Bank Branch Register data, and refresh the validation status of all accounts.

To learn more about his page, see the [Bank Account Validation Setup section in Overview topic](/BankValidator/overview/#bank-account-validation-setup).

# Customer Bank Account Card

The **Customer Bank Account Card** has been modified to show a **Bank Account Validation Result** field immediately after the **Bank Account No.** field on the **General** tab. If you do not see this field, it could be because you are in a Production environment and you do not have a license assigned. The value of this new field will show the results of attempting to validate the data in the **Bank Branch No.** and **Bank Account No.** fields. The validation is performed as soon as the page data is loaded and is re-validated whenever you edit the values in either the **Bank Branch No.** or **Bank Account No.** fields. You do not need to take action to perform the validation as this is handled automatically. The **Bank Account Validation Result** field is for information only and will not prevent any actions using the bank account record.

# Employee Card

The **Employee Card** has been modified to show a **Bank Account Validation Result** field immediately after the **Bank Account No.** field on the **Payments** tab. If you do not see this field, it could be because you are in a Production environment and you do not have a license assigned. The value of this new field will show the results of attempting to validate the data in the **Bank Branch No.** and **Bank Account No.** fields. The validation is performed as soon as the page data is loaded and is re-validated whenever you edit the values in either the **Bank Branch No.** or **Bank Account No.** fields. You do not need to take action to perform the validation as this is handled automatically. The **Bank Account Validation Result** field is for information only and will not prevent any actions using the bank account record.

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

# NZ Bank Accounts

The **NZ Bank Accounts** page shows the list of results from the validation of bank account fields.

| Field                     | Description |
|---------------------------|-------------|
| Used On | Identifies the table and key fields of the record that contains the back account. Click this field to navigate to relevant bank account card. |
| Full Bank Account | The normalised full bank account number.[^1] |
| Status | The result of the validation. For an explanation of the values, see the section for the matching Result Status in the [Errors Explained](/BankValidator/errors-explained) topic. |
| Used Count | The count of records that are using the same bank account number. Any record that shows a value here that is greater than one is a duplicate. |
| Validity Last Checked | The date and time the validity of this bank account was last checked. |
| First Used | The date and time this bank account value was first used for the related **Used On** record. |
| History Count | The number of different accounts that have been used for the related **Used On** record. Use the drill-down on this field to show the historical records. |

# NZ Bank Branches

The **NZ Bank Branches** page shows all of the branches that have been imported from the PaymentsNZ Bank Branch Register file.

# NZ Banks

The **NZ Banks** page shows all of the unique banks that have been imported from the PaymentsNZ Bank Branch Register file.

# Validate NZ Bank Accounts

The **Validate NZ Bank Accounts** processing job is a report with no layout that will allow you to filter on the tables that will be validated, namely:

- Bank Account
- Customer Bank Account
- Vendor Bank Account
- Employee

To allow you to skip validation for blocked customers or vendors, we have added a **Customer Blocked** and **Vendor Blocked** field which allows you to only validate customer or vendor bank accounts when the related customer or vendor matches the filter.

Prior to beginning the validation, the process will check the current Bank Branch Register file against the last imported file and, if there is a later file available, the new file will be imported to update the **NZ Bank** and **NZ Bank Branch** tables that are used for validation.

For each matching record found, the system will validate the combination of **Bank Branch No.** and **Bank Account No.** using the [validation rules](/BankValidator/the-rules). Any records where both the **Bank Branch No.** and **Bank Account No.** fields are blank will be skipped, but other validation results will write a record showing the results of the validation to the **NZ Bank Account** table which you can review on the **NZ Bank Accounts** page. The process can be scheduled to run on a recurring basis and we recommend doing this in order to ensure the Bank Branch Register data is kept up to date. 

---

[^1]: The combination of the **Bank Branch No.** and **Bank Account No.** fields where the formatting has been padded to have eight base account digits and four suffix digits resulting in BB-bbbb-AAAAAAAA-SSSS.