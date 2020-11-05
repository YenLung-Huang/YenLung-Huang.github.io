---
title: crm-leads
tags:
---

# Leads

Leads are especially useful if your company has two separate teams - one that handles lead generation and mass marketing and one that handles sales. The lead generation team can concentrate their work on the Leads tab, and the opportunity team can use the Account, Contact, and Opportunity tabs. ( - Salesforce)

* Salesforce
Track prospects apart from your contacts and opportunities with Salesforce lead records.
After you’ve qualified your lead records, convert them to contacts and create accounts for them (if you don’t already have the accounts in Salesforce).
And hopefully, create opportunities to bolster your pipeline.

* SuiteCRM
In SuiteCRM a Lead is an unqualified contact usually generated from some form of marketing related event, for example it could be a person that has filled out a form on your website or someone that you met at a trade show and you are not sure yet if they have buying authority.
Once a Lead is qualified and converted then it can be split into three parts; a Contact once you have established 'Who' it is, an Account when you know 'Where' they work and an Opportunity once it is known 'What' they might buy.


# Converting a Lead
Once enough information is gathered about a Lead, then the Lead can be progressed to the next Sales stage and the Lead can be converted into a Contact, Account and Opportunity. The way in which a Lead is converted depends on how the System Administrator has set up SuiteCRM. To convert a Lead with the default SuiteCRM setup you have to click on an individual Lead record to access the Detail View of the Lead and click on the arrow next to the Other button, then click on 'Convert Lead' from the drop-down menu shown in the image below:

# Leads FAQs
## What is a Lead? (Salesforce)
Leads are people who are interested in your product and service.
Converting leads to loyal customers will provide success within a business.
By managing your leads in a systematic and structured way, you can increase both the numbers of leads you generate and how many leads you convert

## What are the advantages of using leads? (Salesforce)
Using leads allows your company to maintain two separate lists - one for prospective customers and one for existing customers.
You can store your prospects as leads, and then once a lead becomes qualified, you can convert it to an account, contact, and, optionally, an opportunity.

## Can I capture leads from multiple web pages? (Salesforce)
Yes. Insert the generated HTML code into the web pages from which you want to capture leads. Whenever someone submits information on any of those web pages, a lead will be created.

## Can I convert existing accounts or contacts into leads? (Salesforce)
No. As an alternative, create an opportunity for the account or contact. If you prefer to use a lead, create a report containing the accounts or contacts you want to convert into leads, export them, and then import them as leads.

## How are lead fields mapped to other fields during conversion? (Salesforce)
When you convert a lead, data in standard lead fields is transferred into standard account, contact, and opportunity fields.
For custom lead fields, the data is mapped to custom account, contact, and opportunity fields as specified by your admin.

Any standard lead picklist fields that are blank inherit the default picklist value for accounts, contacts, and opportunities.
If you use record types, all records created during lead conversion adopt the default record type for the owner of the newly created account, contact, and opportunity.

## How can I tell which of my leads are new? (Salesforce)
When a lead is assigned to you, either manually transferred, imported, or generated from the web, the lead is marked as “Unread,” that is, it has a check mark in the Unread column on leads list views.
To view your new leads, select the My Unread Leads list view on the Leads tab.
When you view or edit an “Unread” lead, it is automatically marked as “Read.”

## What happens when I convert leads? (Salesforce)
When you convert leads, Salesforce creates accounts, contacts, and, opportunities using information from the leads you’re converting.
Salesforce moves any campaign members to the new contacts, and the leads become read-only records.
If existing accounts and contacts share the names specified on the leads, you can choose to update the existing accounts and contacts.
Salesforce adds information from the lead into empty fields; Salesforce does not overwrite existing account and contact data.

All open and closed activities from the leads are attached to the accounts, contacts, and opportunities, except for activities initiated from a High Velocity Sales cadence.
You can assign the owners of these new records, and schedule follow-up tasks.
When you assign new owners, only the open activities are assigned to the new owner.
If you have custom lead fields, that information can be inserted into custom account, contact, or opportunity fields.
Your admin can also set up your custom lead fields to populate custom account, contact, and opportunity fields automatically.
You can’t view converted leads, unless your admin has assigned you the "View and Edit Converted Leads" permission.
However, converted leads do appear in lead reports.
Salesforce updates the Last Modified Date and Last Modified By system fields on converted leads when picklist values included on converted leads are changed.

Once converted, a lead record is no longer searchable, unless your admin has assigned you the "View and Edit Converted Leads" permission.
The new account, contact, or opportunity record created from the converted lead is searchable.

## What status is assigned to web-generated leads? (Salesforce)
All new web leads are marked with a status equal to the “default status” that your administrator selects when editing the Lead Status picklist values.
In addition, web-generated leads are marked with the “Unread” flag; they have a check mark in the Unread column on the lead list views.
When a user views or edits a new web lead, the lead is automatically set to “Read.”
This way you can easily locate all new leads using the My Unread Leads list view.

## Who owns new web-generated leads? (Salesforce)
Your administrator can create a lead assignment rule to determine how web leads will be automatically assigned to different users or queues.
In addition, your administrator must customize the Lead Settings to specify a Default Lead Owner.
If the assignment rule fails to locate an owner, web leads are assigned to the default lead owner.
If you do not use assignment rules, all web leads are assigned to the default lead owner.

## Converting a Lead (SuiteCRM)
Once enough information is gathered about a Lead, then the Lead can be progressed to the next Sales stage and the Lead can be converted into a Contact, Account and Opportunity.
The way in which a Lead is converted depends on how the System Administrator has set up SuiteCRM.
To convert a Lead with the default SuiteCRM setup you have to click on an individual Lead record to access the Detail View of the Lead and click on the arrow next to the Other button, then click on 'Convert Lead' from the drop-down menu shown in the image below:
