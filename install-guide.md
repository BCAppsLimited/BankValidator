---
# Page settings
layout: default
keywords:
comments: true

# Hero section
title: Install Guide
description:  In this section you'll find basic information about how to install the app and configure the licenses.  If you're a first time user, you should read this Install Guide first.

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
        content: Overview
        url: /overview
    next:
        content: Validation Rules
        url: /validation-rules
---

# Installation

## Unlimited Free Trial in a Sandbox

The best way to get started with Bank Validator is to install it in a Sandbox environment as this will allow you to use the app without restrictions without purchasing or assigning any licenses.

Open your Business Central Sandbox environment and use the Alt+Q keypress or click the Search icon in the toolbar to bring up the search dialog which says *Tell me what you want to do* at the top of box. Type *appsource* in the box and you will see an option for **Microsoft AppSource apps**.

![Image showing the search box with the text appsource entered.](/screenshots/install/SearchForAppSource.png)

Select the option to launch the **Microsoft AppSource apps** page. This page can take a while to load as it needs to read a list of available apps from the AppSource API. If you have not used this page before, you may see a prompt asking you to allow a connection to an external service.

![Image showing the request to allow a connection to an external service.](/screenshots/install/AllowRequestToService.png)

Ensure *Allow Always* is selected and click **OK**.

When the **Microsoft AppSource apps** page has opened, use the search box at the top of the page to search for a specific app.

![Image showing the Microsoft AppSource apps page with the search box activated](/screenshots/install/SearchForAnApp.png)

Type *Bank Validator* into the search box and you will see the app from publisher *BC Apps Limited* in the list of results.

Click on the contents of the **Name** field for the Bank Validator app and you will be shown the **App overview** page.

![Image showing the App overview page for the selected app.](/screenshots/install/AppOverview.png)

Click the **Install App** action button at the top of the page.

![Image showing the install extension prompt.](/screenshots/install/InstallExtension.png)

Click the **Install** button at the bottom of the dialog to continue with the install.

The **Installing app** dialog will launch to show you that the app installation is in progress.

![Image showing the installing app dialog.](/screenshots/install/InstallingApp.png)

After a short while, you will see the message that your app is installed and ready to use.

![Image showing the app is installed and ready to use message.](/screenshots/install/AppIsInstalled.png)

Congratulations! The app is now installed in your environment and you can go ahead and configure the extension for the first time use.

# Configuration

## Grant Permissions

If you have SUPER or SUPER (DATA) then you'll be able to run the configuration page without needing to set up additional permissions.

We have used implicit permissions throughout the application to ensure that if a user has access to the pages that show realtime validation of **Bank Branch No.** and **Bank Account No.** fields, they will not require additional configuration or permissions.

If you want to assign a permission set that has the rights to run the **Bank Validator Setup** page and other setup actions, you can use the **BC_BV_ADM** permission set.

Note that in a production environment, the **Bank Validation Result** field will only show if a user has a valid license assigned to their user account.

## Bank Validator Setup

Use the search option to find the **Bank Validator Setup** page.

![Image showing the search for the Bank Validator Setup page.](/screenshots/install/SearchForBankValidatorSetup.png)

Select the option to launch the **Bank Validator Setup** page. The page will look similar to the following image although the initial validation source data may differ from what is shown here.

![Image showing the Bank Validator Setup page.](/screenshots/install/BankValidatorSetup.png)

Use the drop-down to select a **Default Validation Rule**. If your company is Australian, you should select *Australian Bank Validation*. If your company is New Zealand, you should select *New Zealand Bank Validation*. You must select a default validation rule other than *No Validation* to be able to continue.

Once you have selected your default validation rule, click the **Activate** toggle control. You will notice that the **Default Validation Rule** is greyed out and can no longer be changed.

The configuration is complete and users will now see the **Bank Validation Result** field on every page that shows a bank account.

To learn more about the various fields and options on the **Bank Validator Setup** page, please read the [Bank Validator Setup](/BankValidator/context-sensitive-help/bank-validator-setup) section in the context-sensitive help topic.

## Run Validation

Although this is not a required step, you may want to run the validation process which will find all places that contain a **Bank Branch No.** and **Bank Account No.** and store the results of the validation. This will give you an overview of how many accounts there are and whether they are valid or not. It will also attempt to update the validation source data by pulling the latest files from the data provider. Because of the update of source data feature, we recommend you schedule this process to run at least once a week to keep the validation source data up to date.

Select the **Validate** action and you will be presented with the options page for the **Validate Bank Accounts** process.

![Image showing the options for the Validate Bank Accounts process.](/screenshots/install/ValidateBankAccountsProcess.png)

You can use this options page to filter on accounts to be validated (for example you can exclude blocked accounts), or to schedule the process to run on an automated basis.

Results of the validation will be stored and the FactBox cues will be updated to reflect the new totals.

We recommend scheduling this process to run once a day or once a week automatically and then manually opening the **Bank Validator Setup** page to check there are no invalid bank accounts in the system.

## Schedule Validation

As with most reports or processes in Business Central, you can schedule the process to run on a recurring schedule. After triggering the **Validate** action, select the **Schedule** button.

![Image showing the process scheduling dialog.](/screenshots/install/ScheduleValidation.png)

The previous image shows the settings for the report to run every Saturday at 3:00 a.m. with a recurring schedule of +1W (which means add one week to calculate the next start date). You could use +1D to run the report every night or +1M to run the report every month.

## Assign Licenses

If you didn't click the option from the previous step or you want to assign existing licenses, go to the [Microsoft 365 Admin Center](https://admin.microsoft.com/). Note that external users such as delegated admin agents, help desk agents, and admin partners will be assigned a free license automatically.

![Image showing the Microsoft 365 admin center licenses page.](/screenshots/gettingstarted/StreetAsGettingStartedAssignLicenses.png)

Click the link to open the Street As - Standard license assignment page. You should see the option to assign licenses to a user or to install the product.

![Image showing the Microsoft 365 admin center assign licenses page.](/screenshots/gettingstarted/StreetAsGettingStartedAssignLicensesAssign.png)

Click the **Assign licenses** link to proceed to the next step.

![Image showing the Microsoft 365 admin center assign licenses to users page.](/screenshots/gettingstarted/StreetAsGettingStartedAssignLicensesAssignUsers.png)

Type the name of the user you want to assign the license to in the search box and with the correct user selected, click the **Assign** button to compete the process. You will be returned to the previous page where you can will see which users have a license assigned. 

![Image showing the Microsoft 365 admin center assign licenses page after the licenses have been assigned.](/screenshots/gettingstarted/StreetAsGettingStartedAssignLicensesAfterAssign.png)

If you wish to purchase more licenses in future for this product, you can do so from within the Microsoft 365 admin center page without needing to visit AppSource. You can trigger the install of the app by clicking the **Install this product** link. The system will sign you in to Business Central and take you to the Extension Installation page.

## Install

![Image showing the Business Central Extension Installation page.](/screenshots/gettingstarted/StreetAsGettingStartedInstallWarning.png)

Click the **Install** button to begin the install. A helpful message showing that the installation is in progress will be displayed and that you can continue working will the extension is installed.

![Image showing the Business Central extension is installing message page.](/screenshots/gettingstarted/StreetAsGettingStartedInstalling.png)

After a short while (assuming you didn't go off and do something else), the system will show you a message telling you that the app is installed.

![Image showing the Business Central extension app is installed message page.](/screenshots/gettingstarted/StreetAsGettingStartedAppIsInstalled.png)

Congratulations! You have successfully installed the app. Let's go ahead and set it up.


---

[^1]: There are currently 66 pages with updated address fields. If you find a page that you would like to be included, please log an issue by clicking the LOG ISSUE link at the top right of this page (a github user account is required to log an issue).
[^2]: Use the Alt+Q key combination or click on the magnifying glass icon in the top bar to launch the "Tell me what you want to do" search box. The search feature is a little bit smart and you can usually get away with just typing the start of the words you are looking for. I usually just type "Street Setup" to quickly get to the setup screen.
[^3]: That's right, your first configuration task is going to see if you can correctly identify New Zealand in a list of countries.
[^4]: Use the Alt+Q key combination or click on the magnifying glass icon in the top bar to launch the "Tell me what you want to do" search box. The search feature is a little bit smart and you can usually get away with just typing the start of the words you are looking for.
[^5]: The biggest cost is the code-signing certificate. Then there's the domain name, the Microsoft 365 subscription, the template used to make the online help. Not to mention the time invested in building the app and keeping it up to date with the latest versions of Business Central. I feel a sales pitch coming on...  