# Remindoo Documentation

This is the documentation for **Remindoo**, the CRM built for UK-based accounting firms to organize client information, manage accounts, assign tasks, and automate firm operations.

## How this documentation is organized

- **01 - User Guide/** — for accounting firm staff using Remindoo day to day. Organized by module, with a `Getting Started` page and a `Features/` folder for capabilities that span multiple modules (E-Sign, HMRC).
- **02 - Internal Reference/** — for the development/QA/support team. Mirrors the same module and feature structure, but covers the technical/functional implementation, architecture, and known issues.

Each module has its own folder under `Modules/` containing:
- `Overview.md` — what the module is and what it's for
- `Workflows.md` — step-by-step tasks / internal business logic
- `Cross-Module Features.md` — how features owned by other modules show up here
- One file per sub-feature confined to that module (e.g. `Didit.md` inside `Clients/`)

**Status:** This documentation is currently a skeleton. Content is being filled in module by module.
