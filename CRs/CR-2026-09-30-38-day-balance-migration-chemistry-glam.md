# Change Request — 38-Day Annual Leave Balance Migration: Chemistry (Pilot) and GLAM (First Tranche)

**Date:** 2026-09-30
**Drafted by:** Kevin Lelitte
**Status:** Draft

---

## 1. Details — What is changing?

Migrating department workgroups onto a 38-day annual leave balance in PeopleXD/WFM, department by department, in a controlled rollout rather than allowing departments to make balance changes independently.

- **Phase 1 — Chemistry (pilot):** 131 workgroups scheduled for balance update and rollover.
- **Phase 2 — GLAM:** first agreed tranche of 39 workgroups. Further GLAM workgroups depend on capacity after the Chemistry rollover completes.

**TBC** — exact workgroup list/codes for both Chemistry and GLAM, and the specific balance/workgroup configuration values to be applied in PeopleXD, to be confirmed by Kevin ahead of implementation. Requesting-department contacts for GLAM also TBC — Julie to confirm.

Target window: early October 2026 for the Chemistry pilot, following on from the 30 Sep 2026 roadmap deadline (HR Systems Roadmap item 208).

---

## 2. Justification — Why is the change necessary?

Chemistry and GLAM have requested migration to a 38-day annual leave balance. To keep this controlled and auditable, departments must not make balance changes independently — this CR is the mechanism for HR Systems to apply the change. Chemistry is being run first as the pilot to prove the approach before GLAM's larger rollout.

---

## 3. Related Changes — Are there dependent changes?

None recorded. Related roadmap tracking: HR Systems Roadmap item 208 ("Migrating departments onto 38 day balances"), led by Julie, team Kevin/Simon/Michael/Marie C.

---

## 4. Impact on Dependent Services

Annual leave balance and workgroup configuration only. TBC whether any leave-reporting or payroll-adjacent reports filter on the affected workgroups — to be confirmed during testing.

---

## 5. Impact — Downtime or at-risk period

None expected. Configuration-level workgroup/balance change; no system outage anticipated.

---

## 6. Impact — Effect of not applying the change

Chemistry and GLAM staff remain on their current (incorrect/unrequested) annual leave balance rather than the agreed 38-day entitlement, and departments may attempt to make the change independently outside of the controlled process.

---

## 7. Risk Assessment

Low, pending confirmation of exact workgroup scope.

- Incorrect workgroup selection could apply the balance change to the wrong group — mitigated by Julie confirming scope with each requesting department before Kevin applies configuration.
- GLAM's further tranches beyond the first 39 workgroups depend on post-rollover capacity from the Chemistry pilot — sequencing risk, not a technical risk.

---

## 8. Testing — Who will test it and how?

TBC — Kevin to confirm test approach with Michael. Expected: verify balance applied correctly for a sample of Chemistry workgroups post-rollover before proceeding to GLAM.

---

## 9. Implementation Plan

Step 1 — Julie contacts requesting departments (Chemistry, then GLAM) to confirm and explain scope. Owner: Julie.

Step 2 — Kevin updates balance/workgroup configuration for Chemistry's 131 workgroups. Owner: Kevin Lelitte.

Step 3 — Kevin discusses required configuration steps with Michael before GLAM proceeds. Owner: Kevin Lelitte.

Step 4 — Apply balance/workgroup configuration for GLAM's first tranche of 39 workgroups. Owner: Kevin Lelitte.

Step 5 — Confirm remaining GLAM workgroups and capacity for further tranches post-rollover. Owner: Julie / Kevin Lelitte.

---

## 10. Communications Plan

Julie to lead communication with Chemistry and GLAM as requesting departments, explaining scope ahead of each rollout. No wider end-user-facing communication identified — TBC if Michael requires anything further.

---

## 11. Business Owner / Approver

Marie Cooksey — Head of HR Systems.

---

## 12. Potential security impact

None anticipated. Change is limited to annual leave balance/workgroup configuration; no change to access, credentials, or salary/payroll data.

---

## 13. How will the security impact be tested?

TBC — confirm with Michael that no unintended access or reporting change results from the workgroup configuration update.

---

## 14. Back Out Plan

Step 1 — Revert affected workgroups' balance configuration to their pre-change value. Owner: Kevin Lelitte.

Step 2 — Confirm reversion with Julie and the affected department. Owner: Julie.
