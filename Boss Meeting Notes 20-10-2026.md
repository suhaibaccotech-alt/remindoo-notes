# Leads Module
~~~
Find the loom in the dev@remindoo.co account per the date recorded, Give to AR
~~~
Will include the conversation tab by merging different tabs

## 2 Way Communication (Zain) (SCRUM-1334: https://accotech.atlassian.net/browse/SCRUM-1334)
Two way communication will allow the user to get emails back from the thread of an original email

Fix tokens shown in Leads


Follow the same system as GHL, show the threads outside instead of showing the thread inside of the modal, show an indicator that there are unread emails in the main table 

## Email Template Settings (Hammad)
Email Templates should show tokens based on the category selected in the email template section in settings


## Table Stuff 
Show differentiation between the sections of the applied filter, but also show more visibility for applied filters

Change the font color for the statuses to black, even if the background is colored

## Proposal Section
Ask the user if they want to edit an existing proposal or create a new one when clicking on create new proposal in the Lead Profile Proposals Section
Add new proposal button to Document Templates

## Email Template Dropdown
Add module tag for each email template

## Document Builder
More templates will be provided
Allow global change to font styling
Give image set as background for one page or all pages at once
Upload feature should be included
For white text, it should show a different colored background to make the text visible
Signature input should be handled even when initially placed on top for creating the input's instance
Document Builder should bring us back to Pricing page
Make sure that the signature input and the date input do not overlap

## Whole App
Make sure that green is associated with sending emails
All Automated Emails, sent from the app, should have the remindoo header and footer

## Timeline
It should have all of the options already selected when All is selected
Make sure that all of the changes discussed are completed by MB


# New Stuff
~~~
This has its own video. To be done later.
~~~
## New things on the horizon
Catch up fee feature
Add vertical progress bar on the right in the proposals section, and match lead information with CH
	Match Service dates with CH to make sure that the correct service template is used to calculate an accurate catch up for creating accounts or completing confirmation statements
	Show a breakdown of the past years' backlog tasks that have to be completed, with each year or period being selected for inclusion by the lead
	We should also log the exact date for joining to link with service to reduce onboarding workload
	Link LOE with service custom fields so that the information is completed before the client is created
	Also, create a form to get the unknown information from the lead/client
	Allow for flexible pricing to be setup using the invoices module for the LOE
	We need to be implement AML for Leads, this will need to be ported over to clients when lead is converted to client
	Create a status line that shows the different steps of a proposal
	Show pricing for the LOE email on center stage
	Show pricing for LOE in a side panel in the client view
	Augment Signature with Acceptance section
	Make token expiry dynamic
	Turn LOE signing into a onboarding process with AML built in, and then ask for missing information using the same link that was used for signing the LOE doc
	Create a progress profile to show proposal sitrep
	Also link with client portal.

# Tasks
~~~
Separate Vid, for Hammad and Zain
~~~
Progress column in tasks should have a popup (included in figma)
Segregate Client and Tasks permissions; self, team, and all
Add partner, and service manager columns
Move email sending button to email logs (already merging into conversations)
Show preview for token replacement when sending emails
Need to recheck 2 way email in tasks
Add missing 10 columns from old task table to the new table
Timeline icon cutoff from the top for the first entry
Show dates below the action buttons to show the latest date for the an action taken in the list inside the modal on the button click
Add next step button with the next page button
Change label to Send for Signature instead of Send Invite in E-Sign
Color code action buttons based on status, and show legend on pagination bar
Link Call logs with internal reminder for call requests; once a call reminder is sent, an action should be prompted to the user to follow up with a client by calling
Match tasks table design from previous table in terms of icons
Show outstanding invoices only
Show invoice payment information and method in Tasks (Later)
# Clients
~~~
Separate Vid for AR and Sami
~~~
Change the color of the icons in front of the client name based on what they represent, and based on their present status
Match E-Sign icon across Tasks and Clients
Show outstanding invoices only
Show colored tag to show that a client is green
Check Remindoo Ltd to see if the PAYE client auth request is working
Left align assignee columns
Invoices should have outstanding invoices and the wrong font sizing
Make sure that testing data is removed from production
Remove client fields for CH 
Sorting should apply to entire page (give option to apply to entire table too)
Check client auth
Make timeline event for LoC
Show button for sending Letter of Clearance even when the letter of clearance has already been sent
Allow user to add email and save to previous accountant
Create tokens for all client fields 
Green should represent completion and sent emails, not working right for AML button
For Self-Employed clients, allow client to be used for sending AML request to, do the same for client portal management
Show unread email indicator in client table
Show overdue tax liabilities with service custom fields
Show view for unauthorized clients
CH Statuses are all shown as red
Show invoice payment information and method in Clients (Later)
Red indicator is wrong for CH status if CH Status is fine
Show Client Name with Primary Contact Name as subtitle, if Contact converted to Client, then it should show the linked company's name as subtitle
Show direct debit status in invoice modal
Ensure duplicates are not created
Ensure empty clients are not created
Outside menu for HMRC is not working for Tax Liabilities or HMRC
	HMRC is not fetching data for authorization
	Tax Liabilities are not showing data in outside menu but showing correct authorization data
	HMRC Fields for VAT are not showing properly (allegedly, need to check against bubble)
Add confirmation for Paused Service
	Add timeline event for Paused Service
Add confirmation for reminder and email toggles
	Add timeline event for reminder and email toggles
Add detailed tooltip for contact AML tag
Client Card on Row Click AML entry should have green color
Make sure bulk deletion and sorting on AML table are added by MB


Prioritize the HMRC Checks for QA to check 
	Remindoo LTD Accounts

# Email Module
Old emails are showing, sync not working
Labels aren't working properly

# Invoice Module
Add logos for software
Remove colored edge on main cards
Show same frontend for Tokens
Pull templates from each software for sending invoices later

# Global Settings
Integrations tab
HMRC Design should be less contrasted; move the design around to make better use of negative space

# Lead Capture Form
Teleform as reference for Conditional Fields

# Workflow Builder
Workflow visual builder is garbage in terms of UX

# Client Custom Fields
Add button for visibility with save button
Add tooltip on hover on table columns
Add other fields from client schema

# Layout upper right menu
Add Signout button 
Allow proper changing of packages
Make balance font right with rest of the design system
~~~
This is the final vid
~~~

# Dashboard
Add AML metrics
Add HMRC Auth Metrics
Admin should be able to track clients and leads that are not authorized on HMRC, and do not have their identity verified on AML

# Changlog
Give APIs to Sir Waqas to connect changlog to a public view as previously mentioned
Request a Meeting Functionality - For support calls and demo meetings
Move to the right, align vertically

# Document Sharing Portal
Send Email to New Client that they have a folder in client portal
Associate Folders with Leads