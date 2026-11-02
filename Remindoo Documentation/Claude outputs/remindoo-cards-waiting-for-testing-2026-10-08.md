# Remindoo – cards waiting for testing

Every card in **Completed without Testing** in Jira on 8 Oct 2026: **115 cards**.

**How to update each card:** check it on production and set its status in Jira:

- **Works:** move it to Production Ready, or to Deployed if it's already live.
- **Broken:** move it back to Not Started and add a comment saying what's wrong.
- **Not done or not needed:** leave the status and note it in the Result column, and Suhaib will decide.

The Result and Notes columns are there if you'd rather fill this file in and send it back.

## 1. Test first: in the Oct 23 release (3)

These are in the Sprint 4s for the Oct 23 release, so please test them before the preprod cut-off on Wed Oct 21.

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-985](https://accotech.atlassian.net/browse/SCRUM-985) | Email – Remove intrusive code from the Email Module | Hammad | High | |  |
| [SCRUM-986](https://accotech.atlassian.net/browse/SCRUM-986) | App-wide – Redis auth issues after recent changes | Hammad | High | |  |
| [SCRUM-1074](https://accotech.atlassian.net/browse/SCRUM-1074) | Invoices – Partial payment on the payment page | Aftab | Medium | |  |

## 2. Recently built, not in a sprint (3)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-884](https://accotech.atlassian.net/browse/SCRUM-884) | Interface translation | Umair | Medium | | Test after Maqddus finishes her review (SCRUM-994) |
| [SCRUM-928](https://accotech.atlassian.net/browse/SCRUM-928) | Some Task tokens still not working | Hammad | Medium | |  |
| [SCRUM-1038](https://accotech.atlassian.net/browse/SCRUM-1038) | Automation – Timeline Notes Do Not Indicate Automation-Triggered Actions | Hammad | Medium | |  |

## 3. Status check: Housekeeping (109)

Older cards that need their status confirmed: does it work now, is it still broken, or was it never done? Grouped by module. Parent cards (257, 516, 524) can close once their subtasks pass.

### Tasks (8)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-59](https://accotech.atlassian.net/browse/SCRUM-59) | Missing Details Email and Client Follow-up in Tasks | Aftab | Medium | |  |
| [SCRUM-265](https://accotech.atlassian.net/browse/SCRUM-265) | When Setup for Recurring Task is Complete in Custom Task Creation, the Button should be Green. | Maqddus | Medium | |  |
| [SCRUM-266](https://accotech.atlassian.net/browse/SCRUM-266) | Backdrop missing for Recurring Task Setup Popup | Maqddus | Medium | |  |
| [SCRUM-275](https://accotech.atlassian.net/browse/SCRUM-275) | Rename Reminder Management to Planned Reminders | Maqddus | Medium | |  |
| [SCRUM-286](https://accotech.atlassian.net/browse/SCRUM-286) | Total Fee Aggregates should have commas | Abdur Rehman | Medium | |  |
| [SCRUM-287](https://accotech.atlassian.net/browse/SCRUM-287) | Total Hours should have the total for all employees | Abdur Rehman | Medium | |  |
| [SCRUM-762](https://accotech.atlassian.net/browse/SCRUM-762) | Subtask Step Spacing is Off | Maqddus | Medium | |  |
| [SCRUM-927](https://accotech.atlassian.net/browse/SCRUM-927) | Task – Create Reminder Issues | Aftab | Medium | |  |

### Clients (8)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-82](https://accotech.atlassian.net/browse/SCRUM-82) | Add Redirection Button in Client Card | Maqddus | Medium | |  |
| [SCRUM-658](https://accotech.atlassian.net/browse/SCRUM-658) | Add Import + Export Clients Feature | Abdur Rehman | Medium | | Client import and export are live; confirm and move to Deployed |
| [SCRUM-680](https://accotech.atlassian.net/browse/SCRUM-680) | Add HoverText for Client Status | Maqddus | Medium | |  |
| [SCRUM-756](https://accotech.atlassian.net/browse/SCRUM-756) | Client Profile Background Color and Tabs Background Color do not match the design provided. (Check All Tabs) | Maqddus | Medium | |  |
| [SCRUM-823](https://accotech.atlassian.net/browse/SCRUM-823) | Client – Company House Sync Stuck on Loading | Abdur Rehman | Medium | |  |
| [SCRUM-839](https://accotech.atlassian.net/browse/SCRUM-839) | Send Letter of Clearance – Email Template Sorting Issue | Abdur Rehman | Medium | |  |
| [SCRUM-869](https://accotech.atlassian.net/browse/SCRUM-869) | Column visibility not showing all fields | Abdur Rehman | Medium | |  |
| [SCRUM-870](https://accotech.atlassian.net/browse/SCRUM-870) | Draft client opens partial record instead of onboarding screen | Abdur Rehman | Medium | |  |

### Client AML checks (Didit) (6)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-820](https://accotech.atlassian.net/browse/SCRUM-820) | Conditional Visibility & Filters in Didit Popup | Maqddus | Medium | |  |
| [SCRUM-821](https://accotech.atlassian.net/browse/SCRUM-821) | Contact Creation in Didit Session Creation | Maqddus | Medium | |  |
| [SCRUM-861](https://accotech.atlassian.net/browse/SCRUM-861) | Digital AML Verification – New Session Status Change Error Toast Color | Maqddus | Medium | |  |
| [SCRUM-863](https://accotech.atlassian.net/browse/SCRUM-863) | Digital AML Verification – Incorrect Cursor on Session, Spent & Balance | Maqddus | Medium | |  |
| [SCRUM-864](https://accotech.atlassian.net/browse/SCRUM-864) | Digital AML Verification – Actions Column Dropdown Arrow Styling | Maqddus | Medium | |  |
| [SCRUM-865](https://accotech.atlassian.net/browse/SCRUM-865) | Digital AML Verification – Session Details Card Alignment Issue | Maqddus | Medium | |  |

### Client Portal (1)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-788](https://accotech.atlassian.net/browse/SCRUM-788) | Turnover Field – Numeric Validation & Currency Selection | Abdur Rehman | Medium | |  |

### Leads (14)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-516](https://accotech.atlassian.net/browse/SCRUM-516) | Leads Module | Maqddus | Highest | | Parent of 517–523, 536, 576 |
| [SCRUM-517](https://accotech.atlassian.net/browse/SCRUM-517) | Fonts need to be updated | Maqddus | Medium | |  |
| [SCRUM-518](https://accotech.atlassian.net/browse/SCRUM-518) | "Customize" in lead kanban view tab should be "Customise" | Maqddus | Medium | |  |
| [SCRUM-519](https://accotech.atlassian.net/browse/SCRUM-519) | Make all buttons the same primary color in lead card that opens when we click on a lead in the leads table | Maqddus | Medium | |  |
| [SCRUM-520](https://accotech.atlassian.net/browse/SCRUM-520) | Timeline Author Card should show picture and show card on click | Abdur Rehman | Medium | |  |
| [SCRUM-521](https://accotech.atlassian.net/browse/SCRUM-521) | Lead Task Reminder Icon needs to be changed to envelope icon | Maqddus | Medium | |  |
| [SCRUM-522](https://accotech.atlassian.net/browse/SCRUM-522) | Bring Focus to imported contact when the contact list is opened after closing the import popup | Abdur Rehman | Medium | |  |
| [SCRUM-523](https://accotech.atlassian.net/browse/SCRUM-523) | Save button is in the wrong position for contacts in leads | Maqddus | Medium | |  |
| [SCRUM-536](https://accotech.atlassian.net/browse/SCRUM-536) | Visibility Settings not saving | Abdur Rehman | Medium | |  |
| [SCRUM-576](https://accotech.atlassian.net/browse/SCRUM-576) | Hide Filters when kanban view is on | Abdur Rehman | Medium | |  |
| [SCRUM-583](https://accotech.atlassian.net/browse/SCRUM-583) | Lead Custom Status Frontend Stops Working Correctly is too long of a status name is entered. | Zain | Medium | |  |
| [SCRUM-744](https://accotech.atlassian.net/browse/SCRUM-744) | Lead Profile too Slow to Load | Abdur Rehman | Medium | |  |
| [SCRUM-747](https://accotech.atlassian.net/browse/SCRUM-747) | [Verify if Not Done by Siraj] Lead Emails and Phone Number should be automatically saved to the contacts | Maqddus | Medium | | May already have been done by Siraj |
| [SCRUM-748](https://accotech.atlassian.net/browse/SCRUM-748) | [Verify if Not Done by Siraj] Lead Bulk Email has no Timeline Event | Maqddus | Medium | | May already have been done by Siraj |

### Proposals and Document Builder (11)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-524](https://accotech.atlassian.net/browse/SCRUM-524) | Proposals Module | Abdur Rehman | Highest | | Parent of 525–533 |
| [SCRUM-733](https://accotech.atlassian.net/browse/SCRUM-733) | Table Header in Proposal Settings has inconsistent borders with the rest of the app. | Maqddus | High | |  |
| [SCRUM-193](https://accotech.atlassian.net/browse/SCRUM-193) | Package Template Creation | Zain | Medium | |  |
| [SCRUM-525](https://accotech.atlassian.net/browse/SCRUM-525) | Back button and subtitle positioning in Proposal Creation needs to be corrected | Abdur Rehman | Medium | |  |
| [SCRUM-527](https://accotech.atlassian.net/browse/SCRUM-527) | Document Builder design should match the rest of the app | Maqddus | Medium | |  |
| [SCRUM-529](https://accotech.atlassian.net/browse/SCRUM-529) | Maybe Implement autosave or ask if they want to refresh and lose changes using an alert in the browser  | Abdur Rehman | Medium | |  |
| [SCRUM-531](https://accotech.atlassian.net/browse/SCRUM-531) | Should be able to add elements from0 the save popup warning (For signature or products) | Abdur Rehman | Medium | |  |
| [SCRUM-532](https://accotech.atlassian.net/browse/SCRUM-532) | Name save should be separate from Document Save | Abdur Rehman | Medium | |  |
| [SCRUM-533](https://accotech.atlassian.net/browse/SCRUM-533) | Document Templates Page Should be the same as the rest of the app | Maqddus | Medium | |  |
| [SCRUM-718](https://accotech.atlassian.net/browse/SCRUM-718) | Bracket plus icon requires more padding | Maqddus | Medium | |  |
| [SCRUM-719](https://accotech.atlassian.net/browse/SCRUM-719) | Percentage-Based Value Field Not Working | Zain | Medium | |  |

### Service Templates (7)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-202](https://accotech.atlassian.net/browse/SCRUM-202) | Task Template Frequency Settings Icon is Not Updating | Zain | Medium | |  |
| [SCRUM-565](https://accotech.atlassian.net/browse/SCRUM-565) | Task template popup should close on completion | Zain | Medium | |  |
| [SCRUM-712](https://accotech.atlassian.net/browse/SCRUM-712) | Duplicates Creating Again During Service Template Import | Zain | Medium | |  |
| [SCRUM-758](https://accotech.atlassian.net/browse/SCRUM-758) | Service Custom Fields Names are still Misaligned | Maqddus | Medium | |  |
| [SCRUM-759](https://accotech.atlassian.net/browse/SCRUM-759) | Service Template Table Colored Text Values are misaligned | Maqddus | Medium | |  |
| [SCRUM-776](https://accotech.atlassian.net/browse/SCRUM-776) | Task Template – External Services | Zain | Medium | |  |
| [SCRUM-853](https://accotech.atlassian.net/browse/SCRUM-853) | Service template -> update task information is missing | Maqddus | Medium | |  |

### Invoices and payments (6)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-856](https://accotech.atlassian.net/browse/SCRUM-856) | Invoices – Void Invoice Can Still Be Selected and Emailed | Aftab | High | |  |
| [SCRUM-932](https://accotech.atlassian.net/browse/SCRUM-932) | Invoice – Email Not Received After Edit & Send | Aftab | High | |  |
| [SCRUM-851](https://accotech.atlassian.net/browse/SCRUM-851) | Go cardless integration | Aftab | Medium | |  |
| [SCRUM-857](https://accotech.atlassian.net/browse/SCRUM-857) | Invoice Email – Additional Recipient Does Not Receive Email | Aftab | Medium | |  |
| [SCRUM-859](https://accotech.atlassian.net/browse/SCRUM-859) | Invoice Reminder Preview – Company Name Token Not Working | Aftab | Medium | |  |
| [SCRUM-911](https://accotech.atlassian.net/browse/SCRUM-911) | GoCardless integration | Aftab | Medium | |  |

### Email (5)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-645](https://accotech.atlassian.net/browse/SCRUM-645) | Need Production Access for Gmail | Suhaib | Highest | |  |
| [SCRUM-736](https://accotech.atlassian.net/browse/SCRUM-736) | Firm Name Token to Dynamically Show Tenant Name | Zain | Highest | |  |
| [SCRUM-564](https://accotech.atlassian.net/browse/SCRUM-564) | Should be able to import emails in email templates | Siraj | Medium | |  |
| [SCRUM-682](https://accotech.atlassian.net/browse/SCRUM-682) | Allow User to Select Email Account to Send Email From (For All Email Sending Features) | Abdur Rehman | Medium | |  |
| [SCRUM-713](https://accotech.atlassian.net/browse/SCRUM-713) | Duplicates Need to Be Diagnosed in Email Template Import | Zain | Medium | |  |

### Automations (5)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-825](https://accotech.atlassian.net/browse/SCRUM-825) | Immediate Firing Confirmation Dialog Appears | Hammad | Highest | |  |
| [SCRUM-698](https://accotech.atlassian.net/browse/SCRUM-698) | Toggle in Status Rules Takes 3 Seconds to Take Effect (Needs Optimistic UI) | Hammad | Medium | |  |
| [SCRUM-827](https://accotech.atlassian.net/browse/SCRUM-827) | Loops can be created in the automation system. This means that users will be able to create an infinite list of automation workflows. | Hammad | Medium | |  |
| [SCRUM-847](https://accotech.atlassian.net/browse/SCRUM-847) | Proposal Automation – Signed Proposal Status | Hammad | Medium | |  |
| [SCRUM-866](https://accotech.atlassian.net/browse/SCRUM-866) | Automation --> Tasks – Token Values Not Populated in Emails | Hammad | Medium | |  |

### Dashboard (5)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-692](https://accotech.atlassian.net/browse/SCRUM-692) | Rename Jobs to Tasks in All Dashboard Sections | Hammad | Medium | |  |
| [SCRUM-699](https://accotech.atlassian.net/browse/SCRUM-699) | Engagement and Collaboration in Tasks Empty State Shows Graphic and Table at the same time | Hammad | Medium | |  |
| [SCRUM-700](https://accotech.atlassian.net/browse/SCRUM-700) | Service Performance Trend Uses Yellow Line Graph on White Background | Hammad | Medium | |  |
| [SCRUM-703](https://accotech.atlassian.net/browse/SCRUM-703) | Archive is Excluded from Dashboard, but Completed and Snoozed aren't. | Hammad | Medium | |  |
| [SCRUM-704](https://accotech.atlassian.net/browse/SCRUM-704) | Service Tabs Next to All do not cover the range of options available in the app, or the data represented. There is also no breakdown to see which services are being shown in All. | Hammad | Medium | |  |

### Settings, users and teams (14)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-260](https://accotech.atlassian.net/browse/SCRUM-260) | Move Teams and Employee List Sections Together in the Navigation Page in the Settings Module | Maqddus | Medium | |  |
| [SCRUM-267](https://accotech.atlassian.net/browse/SCRUM-267) | Add Confirmation Popup for MFA Being Turned On for Entire Tenant in Global Settings | Maqddus | Medium | |  |
| [SCRUM-268](https://accotech.atlassian.net/browse/SCRUM-268) | Change Checkbox to Toggle when Turning MFA On in Edit Own Profile | Maqddus | Medium | |  |
| [SCRUM-270](https://accotech.atlassian.net/browse/SCRUM-270) | Remove Headings from All Settings Pages, and Add Breadcrumbs instead, to Free up vertical space on each page. | Maqddus | Medium | |  |
| [SCRUM-272](https://accotech.atlassian.net/browse/SCRUM-272) | Change the Title of Client Settings to Client Custom Fields | Maqddus | Medium | |  |
| [SCRUM-273](https://accotech.atlassian.net/browse/SCRUM-273) | Bypass Client Custom Field Deletion Confirmation if All Fields Are Empty | Maqddus | Medium | |  |
| [SCRUM-274](https://accotech.atlassian.net/browse/SCRUM-274) | Add Select All when Selecting Client Types in Client Custom Fields | Maqddus | Medium | |  |
| [SCRUM-562](https://accotech.atlassian.net/browse/SCRUM-562) | Tenant Information is not Saving | Siraj | Medium | |  |
| [SCRUM-578](https://accotech.atlassian.net/browse/SCRUM-578) | Group Package Add Feature Input Design Inconsistency | Siraj | Medium | |  |
| [SCRUM-579](https://accotech.atlassian.net/browse/SCRUM-579) | Group Package Edit & Deletion not working | Siraj | Medium | |  |
| [SCRUM-620](https://accotech.atlassian.net/browse/SCRUM-620) | Treat Inactive Status for employees as Soft delete, and allow for employees to be reassigned easily from settings when setting to Inactive. | Zain | Medium | |  |
| [SCRUM-654](https://accotech.atlassian.net/browse/SCRUM-654) | Teams should not be created without selecting a single member | Maqddus | Medium | |  |
| [SCRUM-760](https://accotech.atlassian.net/browse/SCRUM-760) | Check if Template is used for button labels in Settings, and not used in the Client Profile Services section | Maqddus | Medium | |  |
| [SCRUM-779](https://accotech.atlassian.net/browse/SCRUM-779) | Employee List – Unselect All Button | Maqddus | Medium | |  |

### Tenant onboarding and Super Admin (3)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-453](https://accotech.atlassian.net/browse/SCRUM-453) | Tenant onboarding fields lack primary colour border | Maqddus | Medium | |  |
| [SCRUM-457](https://accotech.atlassian.net/browse/SCRUM-457) | When importing tenant information, Admin first name dropdown has different sizing from the last name input field. | Maqddus | Medium | |  |
| [SCRUM-818](https://accotech.atlassian.net/browse/SCRUM-818) | Super Admin – Tenant Ban/Delete Login Error Handling | Zain | Medium | |  |

### App-wide (16)

| Card | Title | Developer | Priority | Result | Notes |
| --- | --- | --- | --- | --- | --- |
| [SCRUM-714](https://accotech.atlassian.net/browse/SCRUM-714) | Add Description to Timeline with Truncation | Maqddus | High | |  |
| [SCRUM-257](https://accotech.atlassian.net/browse/SCRUM-257) | Frontend Fixes | Maqddus | Medium | | Parent of 258–275, 286, 287 |
| [SCRUM-258](https://accotech.atlassian.net/browse/SCRUM-258) | Red Cross Icon With Red Background Should be Added Everywhere | Maqddus | Medium | |  |
| [SCRUM-259](https://accotech.atlassian.net/browse/SCRUM-259) | Hide Call Logs Everywhere and Unmade Features Across the App | Maqddus | Medium | |  |
| [SCRUM-261](https://accotech.atlassian.net/browse/SCRUM-261) | Make the Back button across the app in the same style as the Proposal Creation Back Button, with a yellow colour scheme | Maqddus | Medium | |  |
| [SCRUM-262](https://accotech.atlassian.net/browse/SCRUM-262) | Whenever a item is added to a list, like a subtask step is added to a subtask, the latest entry should be scrolled to and focused so that the user knows that it has been added to the bottom of the list without requiring manual scroll. | Maqddus | Medium | |  |
| [SCRUM-263](https://accotech.atlassian.net/browse/SCRUM-263) | Match Dropdown Design with Task Table Statuses Across The App | Maqddus | Medium | |  |
| [SCRUM-264](https://accotech.atlassian.net/browse/SCRUM-264) | Filter Popups Should Open in the Centre of the Screen | Maqddus | Medium | |  |
| [SCRUM-269](https://accotech.atlassian.net/browse/SCRUM-269) | Install Whatfont to See Fonts Settings in Original App | Maqddus | Medium | |  |
| [SCRUM-271](https://accotech.atlassian.net/browse/SCRUM-271) | Hide Pagination Buttons instead of Disabling them | Abdur Rehman | Medium | |  |
| [SCRUM-563](https://accotech.atlassian.net/browse/SCRUM-563) | Should be able to use enter to add new entries into lists such as subtask steps or custom lead statuses | Siraj | Medium | |  |
| [SCRUM-676](https://accotech.atlassian.net/browse/SCRUM-676) | Make sure that the Assignees and Column Texts are Left Aligned | Maqddus | Medium | |  |
| [SCRUM-677](https://accotech.atlassian.net/browse/SCRUM-677) | Make sure that Widgets in Columns are Right Aligned | Maqddus | Medium | |  |
| [SCRUM-679](https://accotech.atlassian.net/browse/SCRUM-679) | Add the Sorting Dropdown from the Dashboard to all Tables with Sorting | Maqddus | Medium | |  |
| [SCRUM-683](https://accotech.atlassian.net/browse/SCRUM-683) | Financial Assistant Icon in Sidebar Remains Disabled even when an AI Account is Connected, when Logging In, but gets Fixed after Refreshing. | Maqddus | Medium | |  |
| [SCRUM-862](https://accotech.atlassian.net/browse/SCRUM-862) | Notifications – Raw HTML Displayed in Comment Notification | Aftab | Medium | |  |
