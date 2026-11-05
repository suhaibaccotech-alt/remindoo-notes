# Known Issues & Limitations

**Purpose:** A running list of known issues, limitations, and things to be aware of across the app. Newest first. Card keys link to Jira.

## Found in QA on preprod, 5 Nov 2026
| Area | Issue | Card |
| --- | --- | --- |
| Tasks | Due Amount and the task Invoices tab show only invoices linked to the task, not the client's outstanding balance | SCRUM-901 (failed QA) |
| Tasks | No latest-action dates under the task modal's action buttons; no Next Step or Next Page | SCRUM-1285 (failed QA) |
| Tasks | The "All" tab count leaves out Complete, Archived and Snooze | none yet |
| Tasks | Progress display "0hof 1h" is missing a space | none yet |
| Clients | Outstanding invoices modal leaves out partly paid invoices | proposed update to SCRUM-815 |
| Clients | No direct debit status in the outstanding invoices modal | SCRUM-1302 (not on preprod) |
| Invoices | Status disagrees with paid amount (Paid with balance remaining; Partial with £0 paid) | proposed |
| Email | /emails never loads when no mailbox is connected | proposed |
| Dashboard | Tabs open on last week; Capacity Planning cards disagree | proposed |
| Leads | Very long status names push the status tabs over three rows | proposed (Low) |
| Settings | Edit Own Profile shows "Employee not found" for the Test User account | question to Suhaib |
| App-wide | Profile pictures 404: the S3 URL is prefixed with the preprod domain | known since 2 Nov |
| Documents | Folder sizes show "-", so the storage total can't be checked against files | SCRUM-943 (question) |
| Proposals | Document Builder: the properties panel covers the page; AR's 4 Nov UI fixes aren't on preprod yet | AR's list |

## Test-tenant limitations (affect QA, not users)
- No connected mailbox, no HMRC authorisation, no 3CX, GoCardless shows "Coming soon". Cards needing these are tested by hand.
- Employees use yopmail addresses, so QA doesn't trigger anything that emails them.

**Status:** Started 5 Nov 2026.
