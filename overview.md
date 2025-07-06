---
# Page settings
layout: default
keywords:
comments: true

# Hero section
title: Overview
description:  In this section you'll find basic information about the Bank Validator, what it does and how the validation works. Read this section to help you decide if this is the right extension for you.

# Author box
author:
    title: 
    title_url: 
    external_url: false
    description: 

# Micro navigation
micro_nav: true

# Page navigation
page_nav:
    prev:
        content: Home
        url: /
    next:
        content: Install Guide
        url: /install-guide
---

# What is Bank Validator?

OK, this is probably not going to come as a shock, but the Bank Validator is for validating bank account numbers. Specifically New Zealand and Australian bank account numbers. It adds an immediate visual feedback to every page that contains a **Bank Branch No.** and **Bank Account Number** field. Namely:

- **Bank Account Card**
- **Vendor Bank Account Card**
- **Customer Bank Account Card**
- **Employee Card**

In addition to the displays on the setup cards, the **Payment Journal** will show a warning if the bank account number used on the related account is not in a valid New Zealand or Australian bank account number format.

We don't alter the data and we don't stop you from using the bank account if it's not valid, however, the **Bank Account Validation Result** field that has been added to each of the previously listed pages shows a big bright friendly green tick if the entered number is valid according to the validation rule that has been selected.

![Image showing a valid bank account.](/screenshots/overview/ValidBankAccount.png)

Here's a bigger image of that field.

![Image showing a valid bank account enlarged.](/screenshots/overview/LargeValidBankAccount.png)

Imagine when you keyed in that bank account number you accidentally switched the first two characters of the base account number.

![Image showing an invalid bank account enlarged.](/screenshots/overview/LargeInvalidBankAccount.png)

Here you can immediately see there's a problem with the big red cross and an explanation of what's wrong. The full explanation of this particular error is:

❌ The Bank Account "01-0066-2134563-00" is not valid for Bank ID "01" and Branch "0066".

That's just one of the many possible validation errors. It's telling us that although "01" is a valid bank in New Zealand and "0066" is a valid branch for bank "01", the account number "2134563" does not have the correct check digit at the end which is most likely caused by miskeying the number into the entry field. You can find a complete list of error messages and their meaning in the [Errors Explained](/BankValidator/errors-explained) topic.

If your business uses Australian bank account numbers, you can set the **Default Validation Rule** on the **Bank Validation Setup** page to *Australian Bank Validation* which will ensure the BSB number entered is in a valid format and matches a list of known possible values. 

If you want to learn more about exactly how the validation is working, take a look at the [Bank Account Validation Rules](/BankValidator/the-rules), but in summary here's what we do:

## For the Kiwis

- Ensure the entered values in the **Bank Branch No.** and **Bank Account Number** fields, when combined together match the required formatting of a New Zealand bank account number
- Compare the bank id to a list of bank codes provided by PaymentsNZ
- Ensure the branch number exists for the bank using the same PaymentsNZ list
- Use the correct modulo checksum calculation for the bank to ensure the final digit of the base account number is correct for the other entered digits

## For the Aussies

- Ensure the entered values in the **Bank Branch No.** and **Bank Account Number** fields, when combined together match the required formatting of an Australian bank account number
- Compare the first seven characters of the bank account number (the BSB Number) to a list of codes provided by Australian Payments Network

<div class="callout callout--success">
<p><strong>Valid vs Verified</strong></p>
Whilst we can't guarantee the bank account number you have entered is correct, we can ensure it is valid. This will help to eliminate problems in data entry that can become very time consuming when the first indication of a problem is your bank payments get rejected.
</div>

# Bank Validation Setup

In addition to the immediate visual feedback, we provide an ability to get an overview of which accounts are used in the system and categorise them as:

- Valid Accounts
- Valid Accounts with Duplicates
- Invalid Accounts
- All Accounts

You can view this summary from the FactBox pane on the **Bank Account Validation Setup** page.

![Image showing an Bank Account Validation Setup page.](/screenshots/overview/BankAccountValidationSetup.png)

You can drill down on the tiles to show the details of the bank accounts which provides a quick and easy way to navigate to the card with the invalid bank account, allowing you to correct the mistake.

![Image showing NZ Bank Accounts page.](/screenshots/overview/NZBankAccounts.png)

From this image you can see that each bank account that has been validated (we do not show bank accounts where neither the **Bank Branch No.** nor the **Bank Account No.** fields were entered) is listed with a **Status** and a colour coding. The meaning of the colour coding is as follows:

| Style Name | Style | Meaning |
|-------|--------|---------|
| Subordinate | Grey | This is not the current bank account used on this record and shows historical values. Historical values are not shown on the main NZ Bank Accounts page but can be seen by drilling down on the **History Count** field. |
| Favourable | Bold + Green | The account is valid. |
| Ambiguous | Yellow | The account is valid but the Used Count is more than one, meaning the same bank account number has been used in multiple places. |
| Unfavourable | Bold + Italic + Red | The account is not valid. Use the **Status** field or navigate to the **Used On** record for more details. |

The **Bank Account Validation Setup** has some actions that can be used to update the status of all accounts or manually refresh the Bank Branch Register data. These actions are described in the following sub-topics.

## Validate Action

Select the **Validate** action and you will be presented with the options page for the **Validate NZ Bank Accounts** process.

![Image showing the options for the Validate NZ Bank Accounts process.](/screenshots/overview/ValidateNZBankAccountsProcess.png)

You can use this options page to filter on accounts to be validated (for example you can exclude blocked accounts), or to schedule the process to run on an automated basis.

The process will firstly ensure that the Bank Branch Register is up to date and then validate each of the tables that contains bank accounts. Results of the validation will be stored and the FactBox cues will be updated to reflect the new totals.

We recommend scheduling this process to run once a day or once a week automatically and then manually opening the **Bank Account Validation Setup** page to check there are no invalid bank accounts in the system.

## Refresh Data Action

Select the **Refresh Data** action to trigger a check of the Bank Branch Register data provided by PaymentsNZ compared with the copy of the data loaded into Business Central. Every time this process is run (either manually via this action or automatically as part of the **Validate** action), the file name is checked first and if we have already loaded the file with the same name, the system will do nothing. If the file provided by PaymentsNZ is different to the file we have previously loaded, the new file will be downloaded and imported.

## Restore Data Action

You should never need to select this option. The NZ Bank Account Validator includes the latest PaymentsNZ Bank Branch Register data which will be available as soon as the extension is installed. Select the **Restore Data** action to force the system to overwrite whatever Bank Branch Register data is in the system with the data that came with the application.

# How Much?

## Unlimited Free Trial in Sandbox

This extension is fully featured and completely free to use in a sandbox environment, so you can install the extension and try it out without paying a cent. Use it for as long as you like in your sandbox environments.

## Limited Free Trial in Production

It seems too good to be true, but if you decide to go ahead with our extension in your Production environment, you will get *another* free trial. You will need to purchase and assign licenses to your users, but you will not be charged for the first thirty days of use, and when your subscription does start to appear on your bill, you can cancel at any time. All licenses are managed through your Microsoft 365 Admin center and billed directly to you as part of your regular Microsoft Invoice (or can be bought using a credit card if you prefer).

NZ Bank Account Validator is available through [Microsoft's AppSource](https://appsource.microsoft.com/en-NZ/marketplace/apps?product=dynamics-365%3Bdynamics-365-business-central&page=1) and just in case you're not sure how to get started and install the product, checkout our [Install Guide](/BankValidator/install-guide).

