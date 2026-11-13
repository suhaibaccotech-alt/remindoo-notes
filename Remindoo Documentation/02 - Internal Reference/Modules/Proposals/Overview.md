# Proposals — Overview (internal)

**Purpose:** Functional notes on **Proposals** and the Document Builder for the team.

## Routes
- Builder: `/documents-builder`. New proposal wizard: `/proposals/create-new`. "Edit Proposal" on a draft loads that draft but under the same Create New Proposal title and URL (whether saving duplicates it is unknown, 12 Nov).

## Document Builder (reworked build, on preprod from 6 Nov 2026)
- Element settings moved from a right-hand panel to a **top bar**; the element carries Edit, Required and Delete. Undo with Ctrl+Z.
- 11 elements, added by click: Text Block, Heading, Image, Signature, Initials, Text Field, Date Picker, Checkbox (removal in progress, SCRUM-1259), Radio Buttons, Pricing Table, Packages. Content flows onto following pages. Drag-to-reorder isn't verified.
- Text Block and Heading open an editor modal from Edit (not automatically on add).
- **Required fields:** Save is blocked without a Signature and a Pricing Table or Packages. The save warning lists what's missing with Add buttons (SCRUM-531).
- **Page properties:** size A4 / US Letter / US Legal / A3, orientation, global font size, padding (Default 38px, Narrow 23px, Custom), Font & background (Page Font applies to every element, SCRUM-1255; background colour or image with Size, Position, Repeat, Opacity, Colour Overlay). New documents default to A4 · Portrait.
- **Page ⋯ menu:** Page properties, Duplicate page, Move up (disabled on page 1), Move down, Delete page.
- **Header & Footer:** text on every page; header background image with Image Fit.
- **Variables:** System and Pricing groups.
- **Templates picker:** 17 templates in Document Testing Tenant 2. Picking one replaces the open document without confirmation (SCRUM-1422).
- **Import PDF** (PDF only, 20 MB limit): Keep design, edit text / Editable text only (tables not imported) / Keep exact look (page images, placed inside the page padding). Replace or Append. Uploaded and imported images go to the dev image bucket.
- **Drafts:** an unsaved document is kept locally and offered back ("Unsaved changes found… Restore it?"); Discard drops it (SCRUM-529, SCRUM-1258). There's no browser warning on refresh.
- **Save:** "Template Created", then the Library (Preview, Edit). The document name is only saved by the main Save (SCRUM-532).

## Pricing table and packages
- New pricing tables have a "Fee" column; existing templates keep "Fee/Month" (not migrated, SCRUM-1252). Column headings are editable inline and in Pricing-Table Properties → Table Columns (Col 1–4). The product cell is editable inline.
- Optional products: "Optional" badge, tooltip "The client can untick this product when signing"; each product tracks optional and selected.
- Package name rules: required, max 50 characters, no word over 25, no duplicates within a group. The selected package and the monthly/yearly choice are shared between pages. Packages are populated from the proposal ("No packages available" in a bare template).
- Signature and date boxes use flow placement (they move below growing content). £ is the default currency symbol.

## Proposals list and sending
- The wizard offers "Create for existing Lead" (SCRUM-1250). The resend screen labels addresses "Recipients" (SCRUM-1256).
- Auto-invoice on signature: switch in Global Settings → Other Settings (SCRUM-1071, SCRUM-1506). Not verified end to end.
- **Not verified by QA:** sending, the client signing view, the submission preview (selected package, unticked optional products), PDF download. These need the emailed signing link.

## Proposal wizard (walk-through, 13 Nov 2026)
- `/proposals/create-new?tab=lead-information` → `?tab=pricing` → `?tab=send-email`.
- Lead Information: "Toggle lead mode" switch (existing / new lead), LOE Template (searchable), Proposal Name (prefilled with the template name), Existing Lead Name, Email (prefilled from the lead, + to add), phone, optional Additional Info of Leads. **Next creates the draft** ("Draft proposal created successfully").
- Pricing: Products / Packages pickers. The product picker lists categories with counts (they mirror client types), product cards with Standard Price and Grand Total, an Added Items basket and "Add n product". Table columns: Product Name, Frequency, Fee, QTY, Total Fee, Yearly Fee; Subtotal, Discount (Fixed or %), Total Exc. VAT, VAT % (20/15/10/0), Total Inc. VAT. "Products updated on proposal". Document Builder button.
- Send Email: "Saving your letter of engagement in the background… send will unlock when the document is ready." Tokens: ::Lead Name::, ::Lead Phone Number::, ::Company Number::, ::Proposal Name::, ::Signing Link::, ::Signed PDF::, ::Tenant Name::. Preview Email, Send Email to Lead. The builder renders beside it with "Proposal Loaded (Total: £…)".
- Not walked: sending and the client signing page.

## Send and signing page (Tenant 1, 13 Nov 2026)
- Existing Lead Name only lists unconverted leads. The lead's email was **not** prefilled for "Email Test 4" (it was for a lead in the other tenant); it had to be typed and added with +.
- Range-priced product: "Configure bracket and variables for <frequency>" with Range, Select Bracket (checkbox per bracket), Variables with options and quantity, "Total Price of this product", Add Product. Validation: "Please select a bracket for Monthly." The basket shows "Bracket Applied: <bracket>".
- Send Email step: From shows the connected mailbox; default subject "Proposal for Engagement"; Send is disabled until the letter of engagement has saved. Preview resolves ::Signing Link:: to `https://preprod-crm.remindoo.co/shared/<8-character id>`.
- After Send Email to Lead there's no visible confirmation; the app redirects to `/proposals`, where the row is Sent with Sent Date set.
- **Signing page** (`/shared/<id>`, opens without sign-in): header with the document title, "Shared Document Portfolio", page count, **DECLINE** and **FINISH & SUBMIT**; the document pages with the pricing table (product, "Breakdown (Details)" listing bracket and variable lines, fee per frequency, QTY, totals, discount, VAT); signature box with Draw / Type / Upload / Clear.
- The header title is the **template's** name ("NEW DOCUMENT"), not the proposal's name.
- The page count read "21 pages" for this template (same "Page 1 of 21" oddity noted on 9 Nov).
- Not done: Finish & Submit, Decline, the signed PDF, and the auto-created invoice.

**Status:** First draft (12 Nov 2026); wizard, send and signing page walked through 13 Nov 2026. Open bugs are in [Known Issues & Limitations](../../Known%20Issues%20&%20Limitations.md).
