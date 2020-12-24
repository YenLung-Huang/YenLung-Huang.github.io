---
title: crm-Accounts
tags:
- crm
---

# 03
# Acccounts

* SuiteCRM

Accounts in SuiteCRM will typically hold all information specific to a company that your organisation will have a relationship with. In real world terms an Account may be a business entity that is a qualified Sales Prospect, Customer, Supplier or Re-seller and can be used to track all interactions that take place between these entities and your organisation.

* SALESFORCE

Use accounts to store information about customers or individuals you do business with. There are two types of accounts. **Business accounts** store information about companies. **Person accounts** store information about individual people.

* SAP BYD

Corporate Account | private Account

# Comparison
Based on salesforce data

## Business account
A business account has the following fields, listed in alphabetical order.
Depending on your page layout and field-level security settings, some fields may not be visible or editable.

## fields comparison
                                                      | SuiteCRM        | SALESFORCE | SAP BYD        | description
------------------------------------------------------|-----------------|------------|----------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Account currency                                      | X               | O          |                | The default currency for all currency amount fields in the account. Amounts are displayed in the account currency and are also converted to the user’s personal currency. Available only in orgs using multiple currencies.
Account division                                      | X               | O          |                | Division to which the account belongs. Records related to the account, such as contacts and opportunities, automatically inherit the account’s division. Available only in orgs using divisions to segment data.
Account name                                          | O               | O          |                |
Account number                                        | X               | O          |                | Tracking or reference number for account. Up to 40 characters are allowed in this field.
Account owner                                         | X               | O          |                | Assigned owner of account. Not available in Personal Edition.
Account Record Type                                   | X               | O          |                | Name of the field that determines what picklist values are available for the record. Available in Professional, Enterprise, Unlimited, Performance, and Developer Editions.
Account Site                                          | X               | O          |                | Information about the account’s location, such as single location, Headquarters, or Branch. Up to 80 characters are allowed in this field.
Account Source                                        | X               | O          |                | The source of the account record. For example, Advertisement, Data.com, or Trade Show. The source is selected from a picklist of available values, which a Salesforce admin sets. Each picklist value can have up to 40 characters.
Annual Revenue                                        | O               | O          |                | Amount of annual reported revenue.
Billing City                                          | O               | O          |                |
Billing Country                                       | O               | O          |                |
Billing State/Province                                | O               | O          |                |
Billing Street                                        | O               | O          |                |
Billing Zip/Postal Code                               | O               | O          |                |
Clean Status                                          | X               | O          |                | The record’s clean status, as compared with Data.com. Oalues are Not Compared, In Sync, Reviewed, Different, Not Found, and Inactive. This field is available if you use Data.com Prospector or Data.com Clean.
Created By                                            | O               | O          |                | User who created the account, including creation date and time. (Read only)
Data.com Key                                          | X               | O          |                | The company’s ID in Data.com. When Salesforce records are compared with Data.com records (via manual cleaning or automated clean jobs), if Data.com finds a match, the two records are linked by this field’s numeric value.
D&B Company                                           | X               | O          |                | A link to the corresponding D&B Company record, which displays Dun & Bradstreet (D&B) fields for the account. Use the lookup if you want to associate a different D&B Company record with the account. This field is available only in orgs using Data.com Prospector or Data.com Clean.
Description                                           | O               | O          |                |
D-U-N-S Number                                        | X               | O          |                | The Data Universal Numbering System (D-U-N-S) number is a unique nine-digit number assigned to every business location in the D&B database that has a unique, separate, and distinct operation. D-U-N-S numbers are used by industries and organizations around the world as a global standard for business identification and tracking. This field is available if you use Data.com Prospector or Data.com Clean.
Employees                                             | O               | O          |                | Number of people employed by the account.
Evaluate this account against territory rules on save | X               | O          |                | When checked, causes account assignment rules to run when the account is edited and saved. When customizing the page layout for accounts, an administrator can control whether this checkbox displays and whether it is checked by default.
Exclude from territory assignment rules               | X               | O          |                | When checked, shields the account from being evaluated when account assignment rules are run, preventing it from being automatically assigned to territories. Also, if the account is already assigned to territories as a result of assignment rules, checking this box removes the account from those territories. This checkbox only affects rule-based account assignments and has no effect on manual account assignments.
Fax                                                   | O               | O          |                | Fax number.
Industry                                              | O               | O          |                | Primary business of account. Entry is selected from a picklist of available values, which a Salesforce admin sets. Each picklist value can have up to 40 characters.
Modified By                                           | O               | O          |                | User who last changed the account fields, including modification date and time. This field doesn’t track changes made to any of the related list items on the account. (Read only)
NAICS Code                                            | X               | O          |                | The six-digit North American Industry Classification System (NAICS) code is the standard used by business and government to classify business establishments into 20 industries, according to their economic activity for the purpose of collecting, analyzing, and publishing statistical data related to the U.S. business economy. This field is available if you use Data.com Prospector or Data.com Clean.
NAICS Description                                     | X               | O          |                | A brief description of an organization’s line of business, based on its NAICS code. This field is available if you use Data.com Prospector or Data.com Clean.
Ownership                                             | O               | O          |                | Ownership of company, for example, public or private. Entry is selected from a picklist of available values, which a Salesforce admin sets. Each picklist value can have up to 40 characters.
Parent Account                                        | O(Member of)    | O          |                | Parent company for companies that are subsidiaries of a larger company or organization. The parent account must be an existing account in Salesforce. You can enter the account name, or select (or optionally, create) the account using the lookup icon.
Partner Account                                       | X               | O          |                | Read-only field that indicates whether an account is a partner account.
Phone                                                 | O(Office Phone) | O          |                | Primary phone number of account.
Rating                                                | O               | O          |                | Categorization of how you rate this account, for example, Hot, Cold. Entry is selected from a picklist of available values, which a Salesforce admin sets. Each picklist value can have up to 40 characters.
Shipping City                                         | O               | O          |                | City portion of primary mailing or shipping address.
Shipping Country                                      | O               | O          |                | Country portion of primary mailing or shipping address. Entry is selected from a picklist of standard values or entered as text.
Shipping State/Province                               | O               | O          |                | State or province portion of primary mailing or shipping address. Entry is selected from a picklist of standard values or entered as text.
Shipping Street                                       | O               | O          |                | Primary mailing or shipping street address of account.
Shipping Zip/Postal Code                              | O               | O          |                | Zip or postal code portion of primary mailing or shipping address.
SIC Code                                              | O               | O          |                | Standard Industrial Classification code of the account’s main business categorization.
SIC Description                                       | X               | O          |                | A brief description of an organization’s line of business, based on its SIC code.
Territories                                           | X               | O          |                | The territories to which the account has been assigned.  For organizations that use Enterprise Territory Management, this field is not available. Enterprise Territory Management offers a related list called Assigned Territories that you can add to account page layouts.
Ticker Symbol                                         | X               | O          |                | The abbreviation used to identify publicly traded shares of a particular stock.
Tradestyle                                            | X               | O          |                | A name, different from its legal name, that a company can use for conducting business. Similar to “Doing business as” or “DBA”. This field is available if you use Data.com Prospector or Data.com Clean.
Type                                                  | O               | O          |                | Type of account, for example, Customer, Competitor, or Partner. Entry is selected from a picklist of available values, which a Salesforce admin sets. Each picklist value can have up to 40 characters.
Custom Links                                          | X               | O          |                | Listing of custom links for accounts as set up by your Salesforce admin.
Website                                               | O               | O          |                | URL of account’s website, for example, www.acme.com.
Year Started                                          | O               | O          |                | The year the company was established or the year when current ownership or management assumed control of the company. If the company establishment or ownership year is unavailable, then the year the Dun & Bradstreet record was created will be used. Dun & Bradstreet does not supply this data for branch locations.


## Person Account
- salesforce:
A person account has the following standard fields, listed in alphabetical order.
Depending on your page layout and field-level security settings, some fields may not be visible or editable.
Fields with a prefix “Person” or suffix “_pc” are contact fields that are supported for person accounts but not business accounts.

- suitecrm:
In sutiecrm the personal Account is joined by contact

                                                      | SuiteCRM           | SALESFORCE | SAP BYD | description
------------------------------------------------------|--------------------|------------|---------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Account Currency                                      | X                  | O          |         | The default currency for all currency amount fields in the account. Amounts are displayed in the account currency and are also converted to the user’s personal currency. Available only in orgs using multiple currencies.
Account Deivision                                     | X                  | O          |         | Division to which the account belongs. Records related to the account, such as contacts and opportunities, automatically inherit the account’s division. Available only in orgs using divisions to segment data.
Account Name                                          | O                  | O          |         | The name of the individual. In person accounts, the account name cannot be edited directly. Instead, Salesforce derives it by combining the First Name and Last Name fields in the appropriate order per the user's language setting. If Middle Name and Suffix fields have been enabled for the org, those fields are also included in the account name.
Account Name(Local)                                   | X                  | O          |         | The name of the account translated into the local language.
Account Number                                        | X                  | O          |         | Tracking or reference number for account.
Account Owner                                         | X                  | O          |         | Assigned owner of account. Not available in Personal Edition.
Account Record Type                                   | X                  | O          |         | Name of the field that determines what picklist values are available for the record. Available in Professional, Enterprise, Unlimited, Performance, and Developer Editions.
Account Site                                          | X                  | O          |         | Information about the account’s location, such as single location, Headquarters, or Branch.
Annual Revenue                                        | O                  | O          |         | Amount of annual reported revenue.
Assistant                                             | X                  | O          |         | The contact’s assistant.
Asst. Phone                                           | X                  | O          |         | The assistant’s phone number.
Billing City                                          | O                  | O          |         | City portion of billing address.
Billing Country                                       | O                  | O          |         | Country portion of billing address. Entry is selected from a picklist of standard values or entered as text.
Billing State/Province                                | O                  | O          |         | State or province portion of billing address. Entry is selected from a picklist of standard values or entered as text.
Billing Street                                        | O                  | O          |         | Street address used for billing.
Billing Zip/Postal Code                               | O                  | O          |         | Zip or postal code portion of billing address.
Birthdate                                             | O                  | O          |         | The contact’s birthday.
Created By                                            | O                  | O          |         | User who created the account, including creation date and time. (Read only)
Custom Links                                          | O                  | O          |         | Listing of custom links for accounts as set up by your Salesforce admin.
Department                                            | O                  | O          |         | The associated business or organizational unit.
Description                                           | O                  | O          |         | Description of account.
Do Not Call                                           | O                  | O          |         | Whether the contact wants to be contacted by phone.
Email                                                 | O                  | O          |         | The contact’s email address.
Email Opt Out                                         | O                  | O          |         | Whether the contact (person account) wants to receive email (false) or not (true).
Employees                                             | O                  | O          |         | Number of people employed by the account.
Evaluate this account against territory rules on save | X                  | O          |         | When checked, causes account assignment rules to run when the account is edited and saved. When customizing the page layout for accounts, an administrator can control whether this checkbox displays and whether it is checked by default.
Exclude from territory assignment rules               | X                  | O          |         | When checked, shields the account from being evaluated when account assignment rules are run, preventing it from being automatically assigned to territories. Also, if the account is already assigned to territories as a result of assignment rules, checking this box removes the account from those territories. This checkbox only affects rule-based account assignments and has no effect on manual account assignments.
Fax                                                   | O                  | O          |         | Fax number.
Fax Opt Out                                           | X                  | O          |         | Whether the contact wants to be included in broadcast faxes.
First Name                                            | O                  | O          |         | The first or given name of the individual.
Home Phone                                            | O                  | O          |         | The contact’s home phone number.
Industry                                              | O                  | O          |         | Primary business of account. Entry is selected from a picklist of available values, which a Salesforce admin sets.
Last Name                                             | O                  | O          |         | The surname or family name of the individual.
Lead Source                                           | O                  | O          |         | The record source: for example, Advertisement, Partner, or Web. The entry is selected from a picklist of available values, which the administrator sets.
Mailing City                                          | O(Primary Address) | O          |         | The city in the mailing address.
Mailing Country                                       | O(Primary Address) | O          |         | The mailing country for the address. Entry is selected from a picklist of standard values, or entered as text.
Mailing State/Province                                | O                  | O          |         | The mailing state or province for the address. Entry is selected from a picklist
Mailing Street                                        | O                  | O          |         | The street in the mailing address.
Mailing Zip/Postal Code                               | O                  | O          |         | The zip or postal code in the mailing address.
Middle Name                                           | X                  | O          |         | Middle name of the individual.
Mobile                                                | O                  | O          |         | The mailing state or province for the address. Entry is selected from a picklist
Modified By                                           | X                  | O          |         | User who last changed the account fields, including modification date and time.
Other City                                            | O                  | O          |         | The city in another address for the contact.
Other Country                                         | O                  | O          |         | Another country for the address. Entry is selected from a picklist of standard values, or entered as text.
Other Phone                                           | X                  | O          |         | Another phone number for the contact.
Other State/Province                                  | O                  | O          |         | Another state or province for the address. Entry is selected from a picklist of standard values, or entered as text.
Other Street                                          | O                  | O          |         | The street address in another address for the contact.
Other Zip/Postal Code                                 | O                  | O          |         | The zip or postal code in another address for the contact.
Ownership                                             | X                  | O          |         | Ownership of company, for example, public or private.
Phone                                                 | O                  | O          |         | Primary phone number of account.
Rating                                                | X                  | O          |         | Categorization of how you rate this account, for example, Hot, Cold. Entry is selected from a picklist of available values, which a Salesforce admin sets.
Salutation                                            | O                  | O          |         | The title for addressing the contact, for example, Mr., Ms., or Dr. The entry is selected from a picklist of available values, which the administrator sets.
Shipping City                                         | O                  | O          |         | City portion of primary mailing or shipping address.
Shipping Country                                      | O                  | O          |         | Country portion of primary mailing or shipping address. Entry is selected from a picklist of standard values or entered as text.
Shipping State/Province                               | O                  | O          |         | State or province portion of primary mailing or shipping address. Entry is selected from a picklist of standard values or entered as text.
Shipping Street                                       | O                  | O          |         | Primary mailing or shipping street address of account.
Shipping Zip/Postal Code                              | O                  | O          |         | Zip or postal code portion of primary mailing or shipping address.
SIC Code                                              | O                  | O          |         | Standard Industrial Classification code of the account’s main business categorization.
Suffix                                                | X                  | O          |         | Name suffix of the individual.
Territories                                           | X                  | O          |         | The territories to which the account has been assigned.
Title                                                 | O                  | O          |         | The contact’s position within the organization.
Type                                                  | X                  | O          |         | Type of account, for example, Customer, Competitor, or Partner. Entry is selected from a picklist of available values, which a Salesforce admin sets.
Website                                               | X                  | O          |         | URL of account’s website, for example, www.acme.com.

* Conclusion

1. Accounts have two type Business or individual person.
2. Account Fields, Accounts have business account fields and person account fields. (We can see it in suitecrm).
3. Considerations for Using Account Hierarchy

# Question?

* When leads become to account
