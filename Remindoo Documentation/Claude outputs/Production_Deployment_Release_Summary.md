**Production Deployment – Completed Features, Enhancements & Fixes**

*Production Release Summary*

**Muqaddas**

**1\.** HMRC – Expand Buttons: Expand buttons are now open by default.

**2\.** HMRC – XML and MTD Differentiation: Added design changes to clearly differentiate XML and MTD.

**3\.** HMRC – Colour Consistency: Updated the dark green colour for consistency across the HMRC screens.

**4\.** Tables – Freeze Header: Added a frozen header to every major table so column headings stay visible while scrolling.

**5\.** Service Dates: Service dates that are not linked to the client's services are now greyed out.

**6\.** Subtask Step Spacing: Fixed incorrect spacing between subtask steps.

**7\.** Employee List – Phone Number Validation: Added proper phone number validation in the Employee List.

**8\.** Edit Own Profile – Phone Number Validation: Added proper phone number validation in Edit Own Profile.

**9\.** Client Profile Header – UTR Label: Fixed the profile header showing "Company UTR" for self-employed clients.

**10\.** Tasks – Quick Task to Detailed Task: Fixed the issue where switching from Quick Task to Detailed Task wiped the entered information.

**11\.** Knowledge Base – In Review & FAQ Previews: Fixed the incorrect In Review count and paging, and FAQ previews no longer break acronyms when using Title Case.

**Abdur Rehman**

**1\.** Proposal – View Signed Proposal: Fixed the signature and date not being displayed when viewing a signed proposal.

**2\.** Proposal – Signed Proposal PDF: Fixed the signed proposal PDF downloaded from the proposal preview not showing the date.

**3\.** Reminders – Progress Status: Reminders are no longer sent after the progress status has changed.

**4\.** Clients – National Insurance Number: Fixed the National Insurance number field rejecting letters and spaces.

**5\.** Client Onboarding – National Insurance Number: Fixed the National Insurance number in the client onboarding flow accepting only numbers.

**6\.** Client Portal – Invitation Email: Fixed the invitation email showing the wrong company, client and sender.

**7\.** Clients – E-Sign: Fixed client portal documents sent for e-signature showing no input fields when the recipient is a public user.

**8\.** Proposals – Price Range Products: Fixed products with price ranges changing to £0 after being added to a proposal.

**9\.** Clients – VAT Service Reminder: Fixed the VAT service reminder for the September 2026 period not being received by clients.

**10\.** Clients – Bulk Delete: Fixed bulk delete not working in the Clients table.

**11\.** Proposals – Proposal Name: The proposal name can now be edited and no longer always copies the template name.

**12\.** Proposals – BCC Field: Fixed the BCC field being pre-filled with the lead's own email address.

**13\.** Proposals – Save Proposal: Fixed Save Proposal hanging on "Generating your PDF…".

**14\.** Clients – Client Virtualization: The Clients table now uses virtualization, and clients are retrieved through the Client API using the matching filters (converted from RPC to API).

**Aftab**

**1\.** Invoices – Outstanding Invoices Card: Fixed the Outstanding Invoices card showing 0.00 without a value.

**2\.** Invoices – Item Description: Fixed HTML code being displayed in the invoice item description.

**3\.** Invoices – Overdue Invoice Emails: Fixed overdue invoice emails containing localhost links.

**4\.** Tasks – Generated Task Names: Fixed generated task names keeping the unresolved ::Client Name:: token.

**5\.** Invoices – Reminder Emails: Fixed invoice reminder emails being sent twice.

**6\.** Invoices – Default VAT: Fixed new invoice lines defaulting to 5% VAT.

**7\.** Integrations – Xero Sync: Fixed Xero Invoices Syncing.

**Hammad**

**1\.** Email Attachments – File Size Limit: Increased the maximum file size per attachment from 4 MB to 10 MB across the entire application, with a 25 MB limit on total attachments per email.
