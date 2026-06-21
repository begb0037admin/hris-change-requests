# AGENT_MODEL.md
# Runtime Operating Model

Version : 1.1
Status  : Ratified
Updated : 2026-06-18
Author  : Kevin Lelitte, HR Systems, University of Oxford

Governed by: CONSTITUTION.md
Scope      : All work repositories (begb0037admin)

---

## Preamble

This document defines the current implementation of the four-role
model established in CONSTITUTION.md Section 1.

If this document conflicts with CONSTITUTION.md, the constitution wins.

---

## Section 1 — Platform Context

**Work machine (Kevin):** Windows, begb0037 / AD-OAK
**Personal machine (Hope):** macOS — personal domain only

GitHub is the authoritative source of truth for all governed repositories.

---

## Section 2 — Role Assignments

**Seat A — Reasoning Seat → Claude Chat**
**Seat B — Human Seat → Kevin (work) / Hope (personal)**
**Seat C — Execution Seat → Claude Code**
**Seat D — Verification Seat → Chrome (browser)**

---

## Section 3 — Dispatch Protocol

🔵 RUN SCRIPT   → Seat B
🟡 COWORK BRIEF → Seat C
🔴 CHROME BRIEF → Seat D

---

## Section 4 — Session Discipline

1. No session closes without documentation updated.
2. After a sustained session, proactively offer a handover brief.

---

## Section 5 — Cross-Domain Model

**Kevin** — work domain. **Hope** — personal domain only.
**Failover chain (work):** Kevin → Hope

---

## Section 6 — Repository Scope

| Repository           | Status         |
|----------------------|----------------|
| clockify             | Active         |
| hris-dashboard       | Active         |
| hr-fa-knowledge-base | Active         |
| work-inbox           | Active         |
| meeting-records      | Active         |
| hr-projects          | Active         |
| command-centre       | Active         |
| ag-flexpoints        | Active         |
| hris-launcher        | Active         |
| hris-change-requests | Active         |
| aimm                 | Out of scope   |
| personal-finance     | Out of scope   |

---

## Version History

| Version | Date       | Change                   |
|---------|------------|--------------------------|
| 1.0     | 2026-06-06 | Initial ratification.    |
| 1.1     | 2026-06-18 | Scope updated.           |
