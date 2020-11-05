---
title: crm-campaigns
tags:
---

# 01

# Campaigns

* Salesforce
Manage outbound marketing campaigns with direct mail programs, seminars, print ads, email, and other kinds of marketing collateral.
Organize campaigns into hierarchies for easy analysis to see what works best for increasing your company’s sales.
Salesforce makes it easy for you to quickly locate, manage, and report on campaigns.

The Type field on campaigns defines the general types of campaigns you run. Standard values include Advertising, Direct Mail, Email, Telemarketing, Banner Ads, Seminar/Conference, Public Relations, Partners, Referral Program, and Other.

* SuiteCRM
The Campaigns module in SuiteCRM can be a very powerful marketing and advertising tool for your organisation allowing you to create and track both email and non-email based (e.g. telesales or radio) marketing campaigns to prospective or existing customers.
With the tracking tools built into the Campaign module you can monitor the response you receive from your campaign in real time, allowing you to view the Return On Investment (ROI) and many other useful metrics.
This in turn helps you to plan your strategic marketing and advertising activities effectively by visualising which campaigns work and which do not.

# Multiple campaign
(https://community.suitecrm.com/t/multiple-campaign/69101)[https://community.suitecrm.com/t/multiple-campaign/69101]

```
1. Create a Target list, let’s call TL-1 , attach your contact to this TL-1
2. Create another Target List,let’s Call TL-2 , attach your contact to this TL-2.
3. Create a campaign, let’s call July-1, attach TL-1 to July-1
4. Crate another campaign, let’call July-2, Attach TL-2 to July-2.
```

Each campaign has one or more target lists.
That’s where you include the Contacts you want to reach.
And each contact can be in many Target lists, and the Target Lists can be reused across different campaigns, so that multiplicity you need is already there.

# fields

                                           | SuiteCRM        | SALESFORCE | SAP BYD | description
-------------------------------------------------------------------------------------------------
Active                                     | O (status)      | O          |         | Checkbox to mark whether the campaign is active or not.
Actual Cost                                | O               | O          |         | Amount of money spent to run the campaign.
Budgeted Cost                              | O               | O          |         | Amount of money budgeted for the campaign.
Campaign Currency                          | O               | O          |         | The default currency for currency amount fields in the campaign. Amounts display in the campaign currency and are also converted to the user’s personal currency. Available only for organizations that use multiple currencies.
Campaign Member Type                       | X               | O          |         | Record type for campaign members; determines the page layout of the members of the campaign.
Campaign Name                              | X               | O          |         | Identifying name for the campaign.
Campaign Owner                             | X               | O          |         | Assigned owner of the campaign.
Campaign Record Type                       | X               | O          |         | Record type for the campaign; determines the picklist values available for the campaign.
Converted Leads in Campaign                | X               | O          |         | Number of leads that were converted to accounts due to the marketing efforts in the campaign. Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. For more information on converting leads, see Convert Qualified Leads. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Created By                                 | O               | O          |         | User who created the campaign including creation date and time. (Read only)
Custom Links                               | X               | O          |         | Listing of custom links for campaigns as set up by your administrator.
Description                                | O               | O          |         | Description of the campaign. Up to 32KB of data are allowed in this field. Only the first 255 characters display in reports.
End Date                                   | O               | O          |         | Ending date for the campaign. Responses received after this date are still counted.
Expected Response (%)                      | X               | O          |         | Percentage of responses you expect to receive for the campaign.
Expected Revenue                           | O               | O          |         | Amount of money you expect to generate from the campaign.
Last Modified By                           | O               | O          |         | User who last changed the campaign fields, including modification date and time. This does not track changes made to any of the related list items on the campaign. (Read only)
Opportunities in Campaign                  | X               | O          |         | Calculated field for number of opportunities associated with the campaign. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Num Sent                                   | O               | O          |         | Number of individuals targeted by the campaign. For example, the number of emails sent.
Won Opportunities in Campaign              | X               | O          |         | Calculated field for number of closed/won opportunities associated with the campaign. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Parent Campaign                            | X               | O          |         | The campaign above the selected campaign in the campaign hierarchy.
Start Date                                 | O               | O          |         | Starting date for the campaign.
Status                                     | O               | O          |         | Status of the campaign, for example, Planned, In Progress. Entry is selected from a picklist of available values, which are set by an administrator. Each picklist value can have up to 40 characters.
Total Actual Cost in Hierarchy             | X               | O          |         | Calculated field for the total amount of money spent to run a campaign hierarchy. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Budgeted Cost in Hierarchy           | X               | O          |         | Calculated field for the total amount of money budgeted for a campaign hierarchy. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Contacts in Campaign                       | O (target list) | O          |         | Number of individuals on accounts that are associated with the campaign. Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Contacts in Hierarchy                | X               | O          |         | Calculated field for number of contacts associated with the campaign hierarchy. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Converted Leads in Hierarchy         | X               | O          |         | Calculated field for the total number of leads associated with the campaign hierarchy that were converted into accounts, contacts, and opportunities. Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Expected Revenue in Hierarchy        | X               | O          |         | Calculated field for the total amount of money you expect to generate from a campaign hierarchy. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Leads in Campaign                          | O (target list) | O          |         | Number of potential opportunities (leads) associated with the campaign. Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Leads in Hierarchy                   | X               | O          |         | Calculated field for the total number of leads associated with the campaign hierarchy. This number also includes converted leads. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Num Sent in Hierarchy                | X               | O          |         | Calculated field for the total number of individuals targeted by a campaign hierarchy, for example, the number of emails sent. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Opportunities in Hierarchy           | X               | O          |         | Calculated field for the total number of opportunities associated with the campaign hierarchy. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Responses in Campaign                      | O (only email)  | O          |         | Calculated field for the total number of contacts and unconverted leads that have a Member Status equivalent to “Responded” for the campaign. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Responses in Hierarchy               | X               | O          |         | Calculated field for number of contacts and unconverted leads that have a Member Status equivalent to “Responded” for the campaign hierarchy. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Value Opportunities in Campaign            | X               | O          |         | Calculated field for the amount of all opportunities associated with the campaign, including closed/won opportunities. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them.  For organizations using multiple currencies, opportunity amounts are converted to the campaign currency. If your currency does not match the campaign currency, the amount is converted to your currency and displays in parentheses.  For organizations using advanced currency management, opportunity amounts are converted to the campaign currency via dated exchange rates. If the campaign currency does not match your currency, the total of the opportunity amounts are converted using standard exchange rates, not dated exchange rates, and that amount displays in parentheses.  This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Value Opportunities in Hierarchy     | X               | O          |         | Calculated field for total amount of all opportunities associated with the campaign hierarchy, including closed/won opportunities. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them.  All campaigns in a hierarchy must use the same currency.  For organizations using multiple currencies, opportunity amounts are converted to the campaign currency. If your currency does not match the campaign currency, the amount is converted to your currency and displays in parentheses.  For organizations using advanced currency management, opportunity amounts are converted to the campaign currency via dated exchange rates. If the campaign currency does not match your currency, the total of the opportunity amounts are converted using standard exchange rates, not dated exchange rates, and that amount displays in parentheses.
Value Won Opportunities in Campaign        | X               | O          |         | Calculated field for amount of all closed/won opportunities associated with the campaign. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them.  For organizations using multiple currencies, opportunity amounts are converted to the campaign currency. If your currency does not match the campaign currency, the amount is converted to your currency.  For organizations using advanced currency management, opportunity amounts are converted to the campaign currency via dated exchange rates. If the campaign currency does not match your currency, the total of the opportunity amounts are converted using standard exchange rates, not dated exchange rates, and that amount displays in parentheses. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Value Won Opportunities in Hierarchy | X               | O          |         | Calculated field for amount of all closed/won opportunities associated with the campaign hierarchy. (Read only) Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them.  All campaigns in a hierarchy must use the same currency.  For organizations using multiple currencies, opportunity amounts are converted to the campaign currency. If your currency does not match the campaign currency, the amount is converted to your currency.  For organizations using advanced currency management, opportunity amounts are converted to the campaign currency via dated exchange rates. If the campaign currency does not match your currency, the total of the opportunity amounts are converted using standard exchange rates, not dated exchange rates, and that amount displays in parentheses. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Total Won Opportunities in Hierarchy       | X               | O          |         | Calculated field for the total number of won opportunities associated with the campaign hierarchy. Salesforce automatically calculates this amount using all associated records regardless of whether you have read access to them. This field cannot be referenced in formulas for workflow rules, validation rules, field updates, or approval processes, but it can be referenced in custom formula fields. Updates to this field do not trigger workflow rules.
Type                                       | O               | O          |         | Type of campaign, for example, Direct Mail or Referral Program. Entry is selected from a picklist of available values, which are set by an administrator. Each picklist value can have up to 40 characters.

# Question

1. Sales force member vs target lists
2. ROI Reports
How is Campaign influence different from ROI reports?
Campaign influence tracks pipeline and revenue for multiple campaigns, and ties all campaigns of a contact role to that opportunity for pipeline and ROI reporting. This is especially helpful for longer deal cycles when more than one campaign contributes to a closed deal or a converted lead.

# Campaign Tutorial:

## Defining Campaign Goals

### What are your campaign goals?

Campaigns usually have one of the following primary goals:
* Lead generation
Lead generation campaigns include direct mail, email blasts, web seminars, conferences, and trade shows.
These types of campaigns directly generate new prospects.
In Salesforce, you can easily track the effectiveness of each campaign in terms of the amount of new business generated.

* Brand building
Brand-building campaigns include print advertisements, billboards, and radio advertisements.
These types of campaigns may not generate direct responses, so the calculation of campaign ROI may not be as straightforward.

If you want to analyze your marketing budget by campaign goal, we recommend that you add a custom campaign picklist called Campaign Goal to track the primary goal of each campaign. This picklist should include values such as Brand building, Lead generation, and any other campaign goals your organization might have.


Salesforce has parent campaign to defined the different
