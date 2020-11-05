---
title: crm-contacts
tags:
---

# Contacts

* Salesforce

Use contacts to store information about the people you do business with.
Contacts are usually associated with an account, but can also be associated with other records such as opportunities.  Contacts are even more useful when you enable Contacts to Multiple Accounts, add hierarchy information, and customize sharing settings.

* SutieCRM

In SuiteCRM a Contact is an individual who is typically associated with an Account (organisation) or Opportunity (qualified prospect).
For example if Techco is the Account, then John Smith, Sales Manager of Techco is the Contact.
This module holds all information relating to these individuals and also provides a vantage point for any history relating to a Contact record, for example if they were involved in a Meeting, raised a Case or sent an Email.

* SAP BYD

## fields comparison


                                        | SuiteCRM | SALESFORCE | SAP BYD | description
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Account Name                            | O        | O          |         | The account that the contact is linked to. Enter the account name, select the account from a list, or create an account. Private contacts don’t have an account.
Allow Customer Portal Self-Registration | X        | O          |         | If you allow access to a customer portal, when selected, allows contacts to self-register for it.
Assistant                               | X        | O          |         | The contact’s assistant. Maximum 40 characters.
Asst. Phone                             | X        | O          |         | The assistant’s phone number. Maximum 40 characters.
Birthdate                               | O        | O          |         | The contact’s birthday. Click the field, and then choose a date from the calendar.
Contact Currency                        | X        | O          |         | The default currency for all currency amount fields in the contact. Amounts are displayed in the contact currency and converted to the user’s personal currency. Available when multiple currencies are used.
Contact Division                        | X        | O          |         | The division that the contact belongs to. This value is inherited from the related account.  Available when divisions are used to segment data.
Contact Owner*                          | X        | O          |         | The contact’s assigned owner. Not available in Personal Edition.
Contact Record Type                     | X        | O          |         | The name of the field that determines what picklist values are available for the record. Available in Professional, Enterprise, Unlimited, Performance, and Developer Editions.
Created By                              | O        | O          |         | The user who created the contact. Includes creation date and time. Read only.
Custom Links                            | X        | O          |         | A list of custom links for contacts, as set up by your administrator.
Department                              | O        | O          |         | The associated business or organizational unit. Maximum 80 characters.
Description                             | O        | O          |         | The contact’s description. Maximum 32 KB of data. The first 255 characters appear in reports.
Email                                   | O        | O          |         | The contact’s email address. A valid email address is required. Maximum 80 characters.  Click the email address in this field to send an email using your personal email application. This action isn’t logged as an activity on the contact record.  If the Gmail Buttons and Links feature is enabled, click the Gmail link next to the field to send an email from your Gmail account.
Email Opt Out                           | O        | O          |         | Whether the contact wants to receive email (false) or not (true). If you use Data.com, the Email field value is hidden from search results and on the Contact Card, and it’s blank in .csv files that are created when you export records.
Fax                                     | O        | O          |         | The contact’s fax number. Maximum 40 characters.
First Name                              | O        | O          |         | The contact’s first name, as displayed on the contact edit page. Maximum 40 characters.
First Name (Local)                      | X        | O          |         | The contact’s first name, translated into the local language.
Home Phone                              | O        | O          |         | The contact’s home phone number. Maximum 40 characters.
Last Modified By                        | O        | O          |         | The user who last changed the contact fields, including modification date and time. This field doesn’t track changes that were made to any of the related list items on the contact. Read only.
Last Name                               | O        | O          |         | The contact’s last name as displayed on the contact edit page. Maximum 80 characters.
Last Name (Local)                       | X        | O          |         | The contact’s last name, translated into the local language.
Lead Source                             | O        | O          |         | The record source: for example, Advertisement, Partner, or Web. The entry is selected from a picklist of available values, which the administrator sets. Maximum 40 characters for each picklist value.
Mailing City                            | O        | O          |         | The city in the mailing address. Maximum 40 characters.
Mailing Country                         | O        | O          |         | The country in the mailing address. Maximum 80 characters.
Mailing State/Province                  | O        | O          |         | The state or province in the mailing address. Maximum 80 characters.
Mailing Street                          | O        | O          |         | The street in the mailing address. Maximum 255 characters.
Mailing Zip/Postal Code                 | O        | O          |         | The zip or postal code in the mailing address. Maximum 20 characters.
Middle Name                             | X        | O          |         | The contact’s middle name, as displayed on the contact edit page. Maximum 40 characters.  To enable this field, contact Salesforce Customer Support. Next, from Setup, enter User Interface in the Quick Find box, then select User Interface. Then select Enable Middle Names for Person Names.
Middle Name (Local)                     | X        | O          |         | The contact’s middle name, translated into the local language.  To enable this field, contact Salesforce Customer Support. Next, from Setup, enter User Interface in the Quick Find box, then select User Interface. Then select Enable Middle Names for Person Names.
Mobile                                  | O        | O          |         | The contact’s mobile phone number. Maximum 40 characters.
Name                                    | O        | O          |         | The contact’s combined first name, middle name, last name, and suffix, as displayed on the contact detail page.
Other City                              | O        | O          |         | The city in another address for the contact. Maximum 40 characters.
Other Country                           | O        | O          |         | The country in another address for the contact. The entry is selected from a picklist of standard values or entered as text. If the field is a text field, maximum 80 characters.
Other State/Province                    | O        | O          |         | The state or province in another address for the contact. The entry is selected from a picklist of standard values or entered as text. If the field is a text field, maximum 80 characters.
Other Street                            | O        | O          |         | The street address in another address for the contact. Maximum 255 characters.
Other Zip/Postal Code                   | O        | O          |         | The zip or postal code in another address for the contact. Maximum 20 characters.
Other Phone                             | O        | O          |         | Another phone number for the contact. Maximum 40 characters.
Phone                                   | O        | O          |         | The contact’s primary phone number. Maximum 40 characters.
Reports To                              | O        | O          |         | The name of the contact’s manager. Enter a contact name, or select a contact from the list.
Salutation                              | O        | O          |         | The title for addressing the contact, for example, Mr., Ms., or Dr. The entry is selected from a picklist of available values, which the administrator sets. Maximum 40 characters.
Suffix                                  | X        | O          |         | The suffix in the contact’s name, as displayed on the contact edit page. Maximum 40 characters.  To enable this field, contact Salesforce Customer Support. Next, from Setup, enter User Interface in the Quick Find box, then select User Interface. Then select Enable Middle Names for Person Names.
Title                                   | O        | O          |         | The contact’s position within the organization. Maximum 128 characters.
Username                                | O        | O          |         | For Self-Service contacts only. The Username defaults to the Email. Contacts enter their usernames when logging in to the Self-Service portal.
joomal_account_id                       | O        | X          |         | associate to joomla cms

## create contacts
* You can create a contact from several places in Salesforce.
        * Create a contact on an account’s detail page.
        * Import a contact from a mobile device using the Salesforce app.
        * Create a contact from the Contacts area. You should always associate an account to the new contact. If you don’t, the contact is private. Private contacts are accessible only to their owner and system administrators, which makes them hard to find and easy to forget.
* To create a contact that’s automatically associated with an account, create the contact from the account’s detail page.
* To track a contact’s relationship with more than one account, use the Related Accounts related list to add additional account-contact relationships By tracking all related accounts on a single contact record, you avoid creating duplicate contacts. Just make sure your admin has set up Contacts to Multiple Accounts.
* If your Salesforce org uses record types, you’re sometimes prompted to choose a Record Type when creating a contact. Different record types can have different fields and picklist values.
* If your Salesforce org uses divisions, the division of a new contact is automatically set to the division of the related account.

# Comparison
Based on salesforce data

# Conclusion
1. One Contacts to Multiple Accounts
