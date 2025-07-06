---
# Page settings
layout: default
keywords:
comments: false

# Hero section
title: Errors Explained
description: We take you through each of the possible error messages that indicate an invalid bank account and how you should fix it. (hint - key it in correctly!)

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
        content: Context Sensitive Help
        url: /context-sensitive-help
---

# Validation Errors

This section contains a heading for each of the possible errors you might encounter when a bank account number fails to validate. The messages are in the order that the validations are performed.

Most of the messages will refer to parts of the entered bank account number as the part having the problem. The [Validation Rules](/BankValidator/the-rules) topic explains how the account number is made up of different parts. The names of the parts will be different for New Zealand or Australian bank accounts.

## New Zealand Bank Accounts

When referring to errors that occur when using the New Zealand Bank Validation, we will use the following syntax for the full bank account number:

The Full Bank Account Number should be in the format **BB**-**bbbb**-**AAAAAAA**-**SSS**, where 

- **BB** is the bank number (2 digits) 
- **bbbb** is the branch number (4 digits)
- **AAAAAAA** is the account number (7 or 8 digits) 
- **SSS** is the suffix (2 or 3 digits)

### The provided Bank Branch No. and Bank Account No. are not in the correct format.

Result Status = 'Improperly Formatted'.

The actual validation error message is quite long. Here it is in full:

<div class="callout callout--info">
    <p>The provided Bank Branch No. "BB-bbbb" and Bank Account No. "AAAAAAA-SSS" are not in the correct format.</p>
    <p></p>
    <p>The two fields are combined to make one single "Full Bank Account Number" which is "BB-bbbb-AAAAAAA-SSS".</p>
    <p>The Full Bank Account Number should be in the format BB-bbbb-AAAAAAA-SSS, where BB is the bank number (2 digits), bbbb is the branch number (4 digits), AAAAAAA is the account number (7 or 8 digits) and SSS is the suffix (2 or 3 digits).</p>
</div>

This means that the fields you entered could not be split up in to four separate components. 

If you like simplified examples, you should know the following are valid according to this test (although they will fail with other validation rules):

| Bank Branch No.      | Bank Account No.     | Full Bank Account No. |
|----------------------|----------------------|-----------------------|
| 12-1234              | 1234567-12           | 12-1234-1234567-12    |
| 12-1234              | 12345678-12          | 12-1234-12345678-12   |
| 12-1234              | 1234567-123          | 12-1234-1234567-123   |
| 12-1234              | 12345678-123         | 12-1234-12345678-123  |
| 12-1234-1234567-12   |                      | 12-1234-1234567-12    |
|                      | 12-1234-1234567-12   | 12-1234-1234567-12    |
| 12-1234-12345678-12  |                      | 12-1234-12345678-12   |
|                      | 12-1234-12345678-12  | 12-1234-12345678-12   |
| 12-1234-1234567-123  |                      | 12-1234-1234567-123   |
|                      | 12-1234-1234567-123  | 12-1234-1234567-123   |
| 12-1234-12345678-123 |                      | 12-1234-12345678-123  |
|                      | 12-1234-12345678-123 | 12-1234-12345678-123  |

Regular expressions are a convenient way to describe the formatting of an input field. This validation check ensures that the full bank account number (made by combining the **Bank Branch No.** and **Bank Account No.** together with a separating "-") matches the following regular expression:

^\d{2}-\d{4}-\d{7,8}-\d{2,3}$

Which has the following explanation:

```
^\d{2}-\d{4}-\d{7,8}-\d{2,3}$
```

| Token | Meaning |
|-------|---------|
| ^     | asserts position at start of a line |
| \d    | matches a digit (equivalent to [0-9]) |
| {2}   | matches the previous token exactly 2 times |
| \-    | matches the character - with index 4510 (2D16 or 558) literally (case sensitive) |
| \d    | matches a digit (equivalent to [0-9]) |
| {4}   | matches the previous token exactly 4 times |
| \-    | matches the character - with index 4510 (2D16 or 558) literally (case sensitive) |
| \d    | matches a digit (equivalent to [0-9]) |
| {7,8} | matches the previous token between 7 and 8 times, as many times as possible, giving back as needed (greedy) |
| \-    | matches the character - with index 4510 (2D16 or 558) literally (case sensitive) |
| \d    | matches a digit (equivalent to [0-9]) |
| {2,3} | matches the previous token between 2 and 3 times, as many times as possible, giving back as needed (greedy) |
| $     | asserts position at the end of a line |


### The Bank ID "BB" is not valid.

Result Status = 'Bank Id Invalid'.

The two digits you have entered for the bank id or bank number cannot be found in the list of NZ Banks that is extracted from the PaymentsNZ Bank Branch Register file. Use the page **NZ Banks** to see the list of banks that are allowed.

### The Bank Branch "bbbb" for Bank ID "BB" is not valid.
            
Result Status = 'Branch Number Invalid'.

The four digits you have entered for the branch number cannot be found in the list of NZ Bank Branches that is extracted from the PaymentsNZ Bank Branch Register file. Use the **NZ Bank Branches** page to see the list of bank branches that are allowed for any given bank.

### The Bank ID does not have a valid algorithm for the account base.

Result Status = 'Missing Algorithm'.

The actual validation error message is quite long. Here it is in full:

<div class="callout callout--info">
    <p>The Bank ID "BB" does not have a valid algorithm for the account base "AAAAAAA".</p>
</div>

Each of the various bank codes has an algorithm assigned that determines how the check digit should be calculated. This error occurs when the bank code exists as a bank in the list of NZ Banks but does not have an algorithm assigned. This message should not be possible without manipulating the data to create a new bank for which there is no validation algorithm.

The reason the account number is included in the validation message is that some banks will use algorithm A when the account number is within a certain range, and algorithm B otherwise. If you encounter this error, you should report it to us so we can investigate.

### The Bank Account is not valid for Bank ID and Branch.

Result Status = 'Algorithm Checksum Error'.

The actual validation error message is quite long. Here it is in full:

<div class="callout callout--info">
    <p>The Bank Account "BB-bbbb-AAAAAAA-SS" is not valid for Bank ID "BB" and Branch "bbbb".</p>
</div>

This is possibly the most common validation issue you will encounter. It means that the bank and branch are valid and the algorithm that the full bank account number is in the correct format. However, the algorithm that is used for this bank and account base provides a check digit that does not match the last digit of the account base.

### The modulo value for the algorithm is zero, which is invalid.

Result Status = 'Modulo is Zero'

This is an error you should  not see. It is an internal error that you cannot correct, but you should report to us so we can investigate.

### The weighting array does not have a value at position.

Result Status = 'Weighting Array Missing'.

This is also an internal error that you should never see. It means there is a bug in the algorithm and you should report this to use for further investigation.

## Australian Bank Accounts

When referring to errors that occur when using the Australian Bank Validation, we will use the following syntax for the full bank account number:

The Full Bank Account Number should be in the format **BBB**-**BBB**-**AAAAAAAAA**, where 

- **BBB-BBB** is the Bank State Branch (BSB) number (7 digits) 
- **AAAAAAAAA** is the account number (between 6 and 9 digits) 

### The provided BSB No. and Bank Account No. are not in the correct format.

Result Status = 'Improperly Formatted'.

The actual validation error message is quite long. Here it is in full:

 <div class="callout callout--info">
    <p>The provided BSB No. "BBB-BBB" and Bank Account No. "99999999" are not in the correct format.</p>
    <p></p>
    <p>The two fields are combined to make one single "Full Bank Account Number" which is "BBB-BBB-AAAAAAAAA".</p>
    <p>The Full Bank Account Number should be in the format BBB-BBB-AAAAAAAAA, where BBB-BBB is the Bank State Branch (BSB No.), AAAAAAAAA is the account number (between 6 and 9 digits).</p>
</div>

### The BSB "BBB-BBB" is not valid.

Result Status = 'Bank Id Invalid'.

The seven digits you have entered for the Band State Branch cannot be found in the list of BSBs that is extracted from the Australian Payments Network BSB Directory file. Use the page **AU Bank State Branches** to see the list of BSBs that are allowed.

## Bank Branch and Bank Account cannot both be empty.

The full bank account number is generated by taking the **Bank Branch No.** field and the **Bank Account No.** fields from the input page (such as the **Bank Account Card**, **Vendor Bank Account Card**, **Customer Bank Account Card**, or **Employee Card**) and concatenating the two fields into one long text element. If both the **Bank Branch No.** field and the **Bank Account No.** field contain values, they will be separated with a single "-" character.

If you leave both the **Bank Branch No.** field and the **Bank Account No.** field empty, then there is nothing for the algorithm to validate and you will see this message.

This message applies to both Australian and New Zealand validation rules.




