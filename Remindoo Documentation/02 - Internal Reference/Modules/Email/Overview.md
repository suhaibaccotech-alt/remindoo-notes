# Email — Overview (internal)

- One shared compose window for Tasks ("Send Email to 1 task"), Leads ("Send Email to 1 lead", with Send from linked account or Create campaign) and Invoices ("Send Email to Client"). Each has Select Email Template, Recipients, Subject, BCC, a TinyMCE body, Attach files and Adjustable Tokens, plus **Preview Email** (yellow) beside **Send** (SCRUM-1366).
- Preview behaviour: tokens resolved from the record; an empty value renders blank; an unknown token stays as typed (e.g. ::Not A Token::); the payment link renders as a "Pay Invoice" button; the recipient is shown.
- Test tenant: "From: No connected accounts". **/emails never finishes loading** with no mailbox (spinner over 20 s, twice). Proposed card for Zain. This blocks QA of SCRUM-1205 and SCRUM-1206.
- Task Email Logs: one log's Subject column shows an email address (possibly the subject field holding the address).

**Status:** First draft (5 Nov 2026).
