# Proposals — Overview

**Purpose:** What the **Proposals** module is for and what you can do with it.

Proposals lets you send leads and clients a priced proposal or engagement letter that they can sign online.

## The Proposals page
- Status tabs: All, Declined, Sent, Signed, Archived, Draft.
- **New Proposal**, **Document Templates**, Kanban view, filters.
- Columns: Proposal Name, Status, Lead name, Pricing, Created by, Sent by, Creation Date, Sent Date.

## Document Templates and the Document Builder
**Document Templates** lists your firm's templates. **Create New Template**, or the pencil icon on an existing one, opens the **Document Builder**.

*This describes the reworked builder on preprod (6 Nov 2026 onwards). The live app may still show the older layout with a properties panel on the right.*

- **Top bar**: document name, **Header & Footer**, **Templates** (start from a ready-made design), **Import PDF**, **Library**, **Variables**, **Preview** and **Save**.
- **Elements** you can add to the page:
  - *Text*: Text Block, Heading, Image
  - *Form*: Signature, Initials, Text Field, Date Picker, Checkbox, Radio Buttons
  - *Business*: Pricing Table, Packages
- **Selecting an element** shows its settings in a bar at the top of the page (there's no side panel), with **Edit**, **Required** and **Delete** on the element itself. Text Blocks and Headings open an edit window for their text and formatting.
- **Required fields**: a panel shows what the document still needs before it can be saved: a **Signature**, and a **Pricing Table** or **Packages**. If you press Save without them, the warning lists what's missing with an **Add** button for each.
- **Page properties**: size (A4, US Letter, US Legal, A3), orientation, font size for all text, padding (Default, Narrow or Custom), and **Font & background** (page font, background colour or image). A new document starts as **A4 · Portrait**.
- **Page "⋯" menu**: Page properties, Duplicate page, Move up, Move down, Delete page. Content that doesn't fit flows onto the next page.
- **Header & Footer**: text (and an optional header background image) repeated on every page.
- **Variables**: System and Pricing variables you can insert into text, filled in when the proposal is created.
- **Unsaved work is kept**: if you leave without saving, the builder offers "Unsaved changes found… Restore it?" next time you open the document. **Discard** drops the draft.

## Pricing tables and packages
- A new pricing table has a **Fee** column. Column headings can be renamed, in the table or in its settings.
- A product can be marked **Optional**: the client can untick it when signing.
- **Packages** let the client choose between options (with a monthly or yearly choice). A package name is required, up to 50 characters, and can't repeat within a group. Packages are filled in from the proposal, so an empty template shows "No packages available".
- The currency symbol is £ unless the currency is set otherwise.

See [Workflows](Workflows.md) for step-by-step guides.

**Status:** First draft (5 Nov 2026), Document Builder section rewritten 12 Nov 2026 from QA reports. Creating, sending and signing a proposal aren't documented yet.

*Source: observed on preprod (preprod-crm.remindoo.co) on 5 Nov 2026 during QA, and the QA run reports of 6–12 Nov 2026. The live app may lag preprod until the next release.*
