# CONSTITUTION.md
# The Operating Constitution

Version : 1.0
Status  : Ratified
Ratified: 2026-06-06
Author  : Kevin Lelitte, HR Systems, University of Oxford

---

## Preamble

This document defines the enduring principles under which all work
is conducted across all repositories and projects.

When this document conflicts with any other document, Section 6 governs.

---

## Section 1 — The Separation of Concerns

1. **The Reasoning Seat** — thinks, plans, designs, and routes.
2. **The Human Seat** — executes read-only operations. Human authority supersedes all in-flight decisions when invoked.
3. **The Execution Seat** — the sole authority for implementing approved changes.
4. **The Verification Seat** — confirms live behaviour. Read-only.

---

## Section 2 — Dispatch Quality

A dispatch must be complete enough that the receiving role requires no architectural decisions. One dispatch at a time.

---

## Section 3 — Implementation Authority

One role implements approved changes. Any other role's output is a handoff — not an implementation attempt.

---

## Section 4 — Rollback Before Change

Before any change, a restore point must be recorded. On failure, restore immediately.

---

## Section 5 — Documentation Permanence

Conversation is temporary. Documentation is permanent. No session closes without updated documentation.

---

## Section 6 — The Source of Truth Hierarchy

1. The operator's current AI preferences
2. This constitution
3. AGENT_MODEL.md
4. CLAUDE.md
5. STATUS.md / HANDOVER.md

---

## Section 7 — Amendment Process

Amendments require: documented reason, session note, version bump, propagation to all repositories.

---

## Section 8 — Universal Applicability

This constitution applies to every repository, project, and session.

---

## Version History

| Version | Date       | Change               |
|---------|------------|----------------------|
| 1.0     | 2026-06-06 | Initial ratification |
