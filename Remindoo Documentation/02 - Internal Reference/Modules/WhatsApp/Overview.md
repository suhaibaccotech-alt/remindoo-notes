# WhatsApp – Internal Reference

Card: SCRUM-912 (Sami Asghar). Tested on preprod 5 Nov 2026 (AccoTech tenant, as Sami Test 1, Meta test number to a devops test handset). See [[QA/Runs/2026-11-05 WhatsApp]].

## Front end
- Inbox lives at `/emails?channel=whatsapp`. A chat is `&conversation=<id>`. The tab title still says "Emails | Remindoo".
- Settings: Global Settings → **WhatsApp** tab with sub-tabs **Numbers**, **Message templates**, **Quick replies**, **Retention**.

## Backend endpoints seen (preprod-be)
- `GET /api/whatsapp/conversations?page&pageSize`, `/conversations/counts`
- `GET /api/whatsapp/conversations/{id}`, `/messages?pageSize=50`, `/send-context` (window state and templates), `/assignees`, `/links`, `/notes`, `/read-receipt`
- `POST /api/whatsapp/conversations/{id}/mark-read`
- All need the app's auth headers (a plain fetch gets 401 "Missing required authentication headers").

## Settings (read-only check, 5 Nov)
- **Numbers:** one practice/test number connected. Meta caps a new number at 250 people per day. "Connect my number" adds the firm's own number. **Don't use it on preprod.**
- **Message templates:** 12 of 250. hello_world, test_new_2 (re-categorised by Meta to Marketing), jaspers_* approved; dsgfds draft; remindoo_* starter pack "In review". Per number, templates can be switched off (New chat said "4 templates are switched off on this number").
- **Quick replies:** shortcut (`/tt`), title, body; grouped A–Z; "Most recently used first". Tokens use `{{client_name}}` / `{{company_name}}` style. **The rest of the app uses `::Token::`.**
- **Retention:** 5–10 years, with CDD and consent clocks.

## Behaviour confirmed
- Consent gate: New chat needs an opt-in on the number. The opt-in stores source, date, wording version (UK v1) and note.
- Template send → ticks progress to Read. Inbound text and emoji arrive within seconds. Reactions show under the target message.
- Window: opens on inbound ("Open · 23h 59m"). When closed, composer is template-only.
- Star, Mark as unread, and the Unread/Starred counts work.
- Messages are written to the client timeline (Conversation feed and Activity) with "Open chat" deep links.

## Known issues (5 Nov 2026, proposed as cards for Sami)
1. Unfilled quick-reply tokens are sent raw (`{{company_name}}` reached the handset). The warning doesn't block sending. **High**
2. Inbound media (photo, PDF) stays on "downloading…". The UI never requests the file. **High**
3. Timeline: outgoing entries say "By <contact WhatsApp name>", not the staff sender. No message text. The contact uses the WhatsApp profile name rather than the client contact name.
4. Consent opt-in is not written to the client's Activity.
5. Link task lists every client's tasks. The Quick Task form opened from a chat has no client field.
6. No WhatsApp option in the client or task Conversation composers (card says Tasks and Clients integration).
7. Minor: the quick-reply panel stays open after send; a new chat takes about 5 s to appear and briefly shows "No approved templates".

## Testing rules
- Only send to the devops test handset (number kept off Jira and Command Center), with Suhaib holding the phone.
- Never add, connect or disconnect numbers, and never submit templates to Meta from preprod.
- QA client: "QA WhatsApp SCRUM-912" (Draft, no services). Chat #17.
