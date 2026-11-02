# Settings — Cross-Module Features

**Purpose:** Technical integration points between Settings and cross-cutting features owned elsewhere (e.g. E-Sign, HMRC): what data/APIs are shared, and links out to the full feature documentation in `Features/`.

## Service Templates

Service Templates are **defined** in Settings (see [Workflows.md](Workflows.md)), but the templates created here have no effect until applied:

- **Clients** — a Service Template is applied to a client profile to create an actual service instance (not yet documented).
- **Tasks** — the Task module generates the real task(s) from the applied service, applying the Internal/External Deadline logic configured in the template's Frequency Settings (not yet documented).

Full end-to-end picture: [Service Templates](../../Features/Service%20Templates.md).

**Status:** Partially written — Settings-side of Service Templates documented; Clients and Tasks sides pending.
