# Proposals — Workflows

**Purpose:** Step-by-step instructions for common things you do in **Proposals**.

## Build a document template
1. Proposals → **Document Templates** → **Create New Template**. The Document Builder opens on a blank **A4 · Portrait** page.
2. Name the document in the top bar. The name is saved when you save the document.
3. Add elements: Text Block or Heading for wording, Image for a logo or picture, then the form fields the client fills in (Text Field, Date Picker, Checkbox, Radio Buttons, Initials).
4. Add a **Signature**, and a **Pricing Table** or **Packages**. The document can't be saved without them; the **Required fields** panel shows what's still missing.
5. Click an element to change it: **Edit** for text, the top bar for size and alignment, **Required** to make the client complete it, **Delete** to remove it. Ctrl+Z undoes the last change.
6. Set the page up from **Page properties** (size, orientation, font size, padding, font and background) and add a **Header & Footer** if you want one on every page.
7. **Preview** to see the document as the client will.
8. **Save**. You'll see "Template Created" and the template appears in the **Library**, where you can preview or edit it.

## Start from a ready-made template
In the builder, click **Templates** and pick a design. **This replaces whatever is open in the builder, including its name, without asking**, so do it before you add your own content.

## Import a PDF
1. In the builder, click **Import PDF** and choose a PDF (other file types, including Word, aren't accepted).
2. Pick how to bring it in:
   - **Keep design, edit text**: the PDF's design becomes the page background with editable text on top.
   - **Editable text only**: headings and paragraphs come in as text. Tables aren't imported.
   - **Keep exact look**: each page comes in as an image.
3. Choose whether it replaces the current document or is added after it, then save. A new document takes the PDF's file name.

## Create a proposal
The wizard has three steps: **Lead Information**, **Pricing** and **Send Email**.

**Step 1: Lead Information**
1. Proposals → **New Proposal** (or **Create Proposal** on a lead).
2. Use the switch at the top to choose **Create for existing Lead** or **Create for new lead**. For a company, **Import from Companies House** can fill in the details.
3. Pick the **LOE Template** (the document template the proposal is built from). The **Proposal Name** is filled in from the template; change it to something you'll recognise.
4. For an existing lead, choose the **Existing Lead Name**. Its email is added for you; use **+** to add more addresses.
5. Optionally switch on **Additional Info of Leads** for lead type, company number, turnover, address and notes.
6. **Next**. The proposal is saved as a **Draft** at this point ("Draft proposal created successfully").

**Step 2: Pricing**
1. Click **Products** (or **Packages**). Pick a category on the left, then **Add** on each product you want. Products marked *Optional* can be unticked by the client when signing.
2. Check the **Added Items** and total, then confirm with **Add 1 product** (the button shows how many you've chosen).
3. Back on the pricing table you'll see each product's frequency, fee, quantity, total and yearly fee. Add a description, set a **Discount** (fixed or %), and choose the **VAT %** (20, 15, 10 or 0).
4. **Document Builder** opens the document itself if you want to change its wording or layout.
5. **Next**.

**Step 3: Send Email**
1. The letter of engagement is saved in the background; **Send** unlocks when it's ready. You'll see the document with the proposal's prices loaded.
2. Write the email: pick an **Email Template** or type the subject and body. Recipients come from step 1.
3. Use tokens such as ::Lead Name::, ::Proposal Name:: and **::Signing Link::** (the link the client signs with).
4. **Preview Email**, then **Send Email to Lead**.

You can leave at any step and come back; the proposal stays under **Draft**.

*The client's signing page isn't documented yet.*

## Resend a proposal
The resend screen lists the **Recipients** the proposal will go to before you send it again.

## Raise an invoice automatically when a proposal is signed
**Settings → Global Settings → Other Settings** has a switch that creates the invoice automatically once a client signs a proposal.

**Status:** First draft (12 Nov 2026), proposal wizard added 13 Nov 2026 from a preprod walk-through.

*Source: preprod QA run reports of 6–12 Nov 2026 (see `QA/Runs`), added 12 Nov 2026 without a fresh walk-through. The live app may lag preprod until the next release.*
