# Document Sharing Portal — Cross-Module Features

**Purpose:** Technical integration points between **Document Sharing Portal** and cross-cutting features owned elsewhere (e.g. E-Sign, HMRC): what data/APIs are shared, and links out to the full feature documentation in `Features/`.

## Service Templates

Two Settings-configured points on a Service Template create content here automatically:

- **Folder automation** (on the Service Template itself) — creates a folder in the Document Sharing Portal when a service is created on a client from that template.
- **Document checklist** (on a Reminder Template) — a Reminder can send an email requesting documents from an external user; whatever they upload is placed into a specific folder here.

See [Service Templates](../../Features/Service%20Templates.md) and [Settings/Workflows.md](../Settings/Workflows.md).

**Status:** Partially written.
