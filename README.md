## Claude Quick Load

Paste any URL below directly into Claude chat to load project context:

| File | Raw URL |
|---|---|
| `CLAUDE.md` | https://raw.githubusercontent.com/begb0037admin/hris-change-requests/main/CLAUDE.md |
| `HANDOVER.md` | https://raw.githubusercontent.com/begb0037admin/hris-change-requests/main/HANDOVER.md |

---

# HRIS Change Requests

Stores drafted Change Request (CR) documents for Kevin Lelitte to upload to PeopleXD. Claude drafts CRs from source material (emails, meeting notes); Kevin reviews and uploads.

**Owner:** Kevin Lelitte, HR Systems Manager/Director, University of Oxford
**Repo:** https://github.com/begb0037admin/hris-change-requests

## What's in the Repo

| Path | Purpose |
|---|---|
| `CLAUDE.md` | AI bootstrap — read first |
| `HANDOVER.md` | Current state and recent CRs |
| `templates/change-request-template.md` | Blank 14-section CR template |
| `CRs/` | Completed CRs — one `.md` per CR |

## CR Naming Convention

`CR-YYYY-MM-DD-[short-description].md` — e.g. `CR-2026-06-15-org-hierarchy-update.md`

## Workflow

1. Kevin provides source material → Claude drafts CR using the template
2. Kevin reviews (especially Section 11 — Business Owner/Approver)
3. Claude pushes `.md` to `CRs/`
4. Kevin downloads and uploads to PeopleXD
