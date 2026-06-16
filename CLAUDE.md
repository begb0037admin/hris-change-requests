# CLAUDE.md — hris-change-requests
> AI bootstrap entry point. Read this first.
> Keep this file under 200 lines. Push details to linked docs.

## Identity
- **Project:** HRIS Change Requests
- **Purpose:** Draft Change Request documents from source material (emails, meeting notes) for Kevin Lelitte to upload to PeopleXD. PeopleXD owns the approval workflow — this repo produces accurate, fully-populated `.md` CR documents.
- **Owner:** Kevin Lelitte, Manager/Director HR Systems, University of Oxford
- **Status:** Active
- **Repo:** https://github.com/begb0037admin/hris-change-requests
- **Last updated:** 2026-06-16

## Bootstrap Order
1. This file (orientation)
2. Any existing files in `CRs/` for current context
3. `templates/change-request-template.md` for the blank template

Do NOT ask Kevin for a recap. Read the CRs folder to understand current state.

## Architecture
| Component | Description |
|---|---|
| `templates/change-request-template.md` | Blank 14-section CR template |
| `CRs/` | Completed CRs — one `.md` file per CR, named `CR-YYYY-MM-DD-[short-description].md` |

## PeopleXD Environments
Standard environment sequence for all change requests — always apply in this order:

| Environment | Code | Purpose |
|-------------|------|---------|
| UAT | UOXU | First non-production test environment |
| Sandpit & Training | UOXZ | Second non-production environment |
| Configuration | UOXC | Third non-production environment |
| Production | UOXP | Live — always last |

**Standard implementation sequence: UOXU → UOXZ → UOXC → UOXP**
Always verify in each environment before proceeding to the next. Never apply to UOXP before all three non-production environments are verified.

## Workflow
1. Kevin provides source material (emails, meeting notes, Granola transcripts)
2. Claude drafts the CR using the 14-section template
3. Kevin reviews and confirms — especially **Section 11 (Business Owner / Approver)**
4. Claude pushes the `.md` to `CRs/`
5. Kevin downloads and uploads to PeopleXD / OSM
6. Kevin replies to Asta Palmer (or relevant implementer) with the OSM reference number so they can pick up the task

## Hard Rules
- Never invent information — flag gaps explicitly with `[TBC]` or `[CONFIRM WITH KEVIN]`
- Always confirm Business Owner (Section 11) with Kevin before finalising
- One `.md` file per CR, pushed to `CRs/`
- Never commit credentials or email content verbatim if it contains personal data
- CR filenames: `CR-YYYY-MM-DD-[short-description].md` (kebab-case, lowercase)
- Always use the standard environment sequence: UOXU → UOXZ → UOXC → UOXP

## CR Naming Convention
`CR-2026-06-16-coreportal-admin-org-hierarchy-menu-options.md`
Date = date drafted. Short description = 3–5 words, kebab-case.
