Checking to see if git is working now. 

Checking if sync works.

Did it the wrong way around but its working.


Here's the revised list, in Slack formatting so you can paste it straight in:

```
*Pushed to preprod for the Friday 6 November release*
*Whole App*
• Changelog editor: uploading a markdown file no longer replaces the existing content
*Dashboard*
• Tasks and Services tabs on the Dashboard
• Tasks tab: Current, History and Upcoming views, plus a new Outstanding work by team and stage chart
• Faster loading: the slowest dashboard queries went from over 20 seconds to under 1 second
*Leads*
• Fixed the Status and Source filters returning no results
*Tasks*
• New Tasks table with an Activities view
• The 10 missing columns and their filters added to the Tasks table
• Filters and saved filters
• Timer logs popup from the Progress column
• Send Now button in the task's Email Logs
• Latest action date shown under the task's action buttons
• Comments and messages are marked as read when the comments section is opened
• Personal task reminders now save
• Kanban view loads each status column separately
*Invoices*
• An invoice is created automatically when a proposal is signed
• Create an invoice from a task, or link existing invoices to it
• Sorting on the Invoices tables
• The Approve and Send email card now has the full set of invoice tokens
*Document Portal*
• Storage usage now shows correctly
*Email*
• Two-way email in Leads, Clients and Tasks
• Unread badge on the Communication tab in Leads, Clients and Tasks
• Preview button on email modals, showing the email filled in with the lead's, client's, task's, proposal's or invoice's details
*Integrations*
• 3CX calling from Leads, Clients and Tasks
• 3CX call details on client and lead timelines
```

Four items haven't been confirmed by testing yet:

- **Wider Preview line:** SCRUM-1366 is on preprod but hasn't been tested. On 2 Nov, Awais found no Preview button on the invoice and task reminder modals, so he should check the task, proposal and invoice modals before Friday.
- **Kanban lazy loading:** there's no Jira card for it. Only the fix for the kanban counts (SCRUM-1171) has been tested.
- **Send Now and latest action date:** both failed testing on 2 Nov, and I haven't seen a retest since.

I couldn't find Hammad's comment on Slack, so I worked from what you told me.