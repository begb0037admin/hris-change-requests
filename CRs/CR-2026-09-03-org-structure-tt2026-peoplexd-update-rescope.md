# Change Request — Trinity Term 2026 Organisational Structure Update in PeopleXD (Rescoped: Change Schedule rows 8–24 and 111–136)

**Date:** 2026-09-03
**Drafted by:** Kevin Lelitte
**Status:** Draft — rescope review required before submission

Companion to CR-2026-09-03-org-structure-tt2026-peoplexd-update. That document remains on file as the fuller record. This rescoped version narrows the change to the organisational-structure actions in the Change Schedule and is the version intended to be taken forward once the rescope review is complete. Where the two differ, the difference is deliberate and is marked below with [CONFIRM WITH KEVIN].

---

## 1. Details — What is changing?

This change request covers only the organisational-structure actions in Organisational Structure (Trinity Term 2026 FINAL PUBLISHED).xlsx, Change Schedule rows 8–24 and 111–136.

The Change Schedule is authoritative. The scope is:

- 17 department and management-unit schedule rows, of which rows 10 and 17 are HESA-code notes and not PeopleXD hierarchy build actions; and
- 26 subsidiary-company schedule rows.

The PERSUP11 Active Hierarchy report has already been saved as the pre-change baseline at 03 Change Register and Working Tool\Evidence\Pre-change\PERSUP11 Active Hierarchy 03SEP2026.xlsx. It records the before-state of the hierarchy; it does not replace the separate appointment/post check required before a move or retirement.

Department and management-unit actions. Each line gives the code, the PeopleXD action, and the scheduled Entity Name and Entity Full Name where they change:

- B9 — Rename. Entity Name: Tropical Medicine - CGHR (Oxford). Entity Full Name: Tropical Medicine - Centre for Global Health Research.
- A7 — Create new L3 department under 2B18. Entity Name: OVG. Entity Full Name: Oxford Vaccine Group.
- 8H40 — Create new L2 management unit. Entity Name: PAD. Entity Full Name: Public Affairs Directorate.
- KB — Re-parent to management unit 8H40 (from 8H20). Name unchanged.
- 8H20 — Rename management unit. Entity Name: VC and Registrar. Entity Full Name: Vice-Chancellor and Registrar's Office.
- L4 — Retire department.
- AU — Re-parent to management unit 4D14. Name unchanged.
- B8 — Create new L3 department under 2B27. Entity Name: CNCB. Entity Full Name: Centre for Neural Circuits and Behaviour.
- KY — Rename. Entity Name: LOD. Entity Full Name: Learning and Organisational Development.
- A1 — Rename. Entity Name: DCH Building Operations. Entity Full Name: Dorothy Crowfoot Hodgkin Building Operations.
- CC — Rename. Entity Name: Cross-RDM. Entity Full Name: Cross-RDM Professional Services.
- C1 — Rename. Entity Name: NDM Education. Entity Full Name: NDM Education.
- BH — Rename. Entity Name: NDM Operations. Entity Full Name: NDM Operations.
- 8HP0 — Rename management unit. Entity Name: Digital and information services. Entity Full Name: Digital and information services.
- E7 — Update Entity Full Name only. Entity Name remains Office of the CDIO. Entity Full Name becomes Chief Digital and Information Officer.

Schedule notes: row 10 records HESA code 101 for A7 and row 17 records HESA code 106 for B8. They are retained as source notes and are not hierarchy build actions in this change request.

Before creating B8, verify that the code is available in the target environment; the saved baseline is evidence for this pre-change check.

Before moving or retiring an item, run PERSUP11_Organisation Restructure and resolve any active appointments, unassigned posts or open unused vacancies in accordance with the hierarchy-maintenance guidance.

Subsidiary-company actions, applied under Level 2 entity 0D:

- Delete: V4 Instruct; VD Voltaire Foundation Limited; X3 OUC Investments Limited; X4 Oxford University Clinic LLP; V6 Oxford University (Beijing).
- Rename: V7 to Health Research Operations Kenya Limited; V5 to Oxford Advanced Research Centres Limited; X2 to Oxford Research South Africa Limited; VU to Oxford University Endowment Management Limited.
- Create: X0 Ecosystem Capital Limited; XL Endowment Estates Limited; XM OUPM Ltd; XP Oxuniprint Ltd; XQ Oxford GLAM Enterprises Limited; XR Oxford Research South Africa Limited (External Company Registration); XS Oxford University Development (North America), Inc; XT Oxford University Trading Limited; XU Oxuniprint Limited; XV Medical Sciences Commercial Services Limited; XW Proxemis Limited; XY TOF Corporate Trustee Limited; XZ University of Oxford China Office Limited; Y0 Yayasan Jalin Kemitraan Nusantara; Y1 Oxford University Clinical Research Unit Nepal; Y2 Oxford University (Suzhou) Science & Technology Co. Ltd.
- Then apply the separate subsequent schedule action that deletes XP as the duplicate company created in error. Preserve this create-then-delete sequence in the implementation evidence.

[CONFIRM WITH KEVIN] The companion CR on file records XP as not created (removed by PACS, reference retained in the change record only), and does not list XP Oxuniprint Ltd alongside XU Oxuniprint Limited. This rescoped version follows the Change Schedule's create-then-delete sequence instead. Confirm which is correct before submission.

Method: build in the agreed test environment using the Portal hierarchy-maintenance procedure.

---

## 2. Justification — Why is the change necessary?

PeopleXD's organisational hierarchy must match the published PACS Organisational Structure for Trinity Term 2026 so that posts, appointments, staff requests and downstream feeds are administered against the correct organisational units. The Trinity Term 2026 structure is published and effective; the corresponding PeopleXD hierarchy has not yet been updated.

---

## 3. Related Changes — Are there dependent changes?

[CONFIRM WITH KEVIN] This rescoped CR does not assert any dependencies. The companion CR on file references the Colleges & Halls workstream (CR-2026-06-15 / project DTP1092) as separate, and a Portal-enablement change (CR 20020472, COREPORTAL_ADMIN menu options) as a prerequisite for Portal-based hierarchy maintenance. Confirm whether either should be carried into this version before submission.

---

## 4. Impact on Dependent Services

The change updates organisational hierarchy configuration only. No integration, payroll calculation, salary data or personal data is changed.

Reporting or processes filtered by a department or management-unit code should be reviewed where a code has been renamed, re-parented or retired (B9, 8H20, KB, AU, C1, BH, 8HP0, E7, L4).

---

## 5. Impact — Downtime or at-risk period

No service outage is expected. The change adds, renames, re-parents and retires organisational-hierarchy records only. No existing staff records or live payroll data are altered. Work is done in the test environment first and promoted environment by environment with verification at each stage.

---

## 6. Impact — Effect of not applying the change

PeopleXD will retain stale names, parents and subsidiary-company records, and the new departments (A7 OVG, B8 CNCB) and the new management unit (8H40 PAD) cannot be used. Posts and appointments would continue to be created against an incorrect structure.

---

## 7. Risk Assessment

- B8 code collision. B8 must be confirmed available in the target environment before it is created; the saved PERSUP11 baseline is the evidence for this pre-change check.
- Moves and retirements with live records attached. Before moving or retiring an item (KB, AU, L4), run PERSUP11_Organisation Restructure and resolve any active appointments, unassigned posts or open unused vacancies first.
- Renamed or re-parented codes break downstream filters. Mitigated by the saved pre-change PERSUP11 baseline, the post-change PERSUP11 comparison, and the affected-reporting review in Section 4 and Section 10.
- XP create-then-delete sequence. The duplicate-in-error must be preserved as a recorded sequence in the implementation evidence, not silently omitted — see the Section 1 [CONFIRM WITH KEVIN].
- All changes are reversible at configuration-record level provided no posts or appointments have been created against a new or changed unit (see Section 14).

---

## 8. Testing — Who will test it and how?

Kevin Lelitte and Asta Palmer will:

1. Verify every in-scope value against Change Schedule rows 8–24 and 111–136.
2. Verify A7 under 2B18, B8 under 2B27, 8H40, KB under 8H40, AU under 4D14, retirement of L4, and E7's Entity Full Name.
3. Verify each subsidiary-company action, including the XP sequence.
4. Run the standard functional hierarchy checks in the test environment.
5. Re-run PERSUP11 Active Hierarchy and compare it with the saved pre-change baseline: new codes, names, parents, E7, L4 and subsidiary actions.
6. Save the post-change export alongside the baseline, plus implementation and test evidence, in the documented cycle location before promotion.

---

## 9. Implementation Plan

Step 1 — Confirm source values against the Change Schedule. Owner: Kevin Lelitte.

Step 2 — Verify B8 availability against the saved PERSUP11 baseline. Owner: Kevin Lelitte / Asta Palmer.

Step 3 — Apply the department and management-unit actions in the test environment via the Portal. Owner: Kevin Lelitte / Asta Palmer.

Step 4 — Apply the subsidiary-company actions in the test environment. Owner: Kevin Lelitte / Asta Palmer.

Step 5 — Test, compare PERSUP11 against the saved baseline, and save evidence. Owner: Kevin Lelitte / Asta Palmer.

Step 6 — Promote through the approved environments and verify each stage. Owner: Kevin Lelitte / Asta Palmer.

Step 7 — Complete production verification and sign-off. Owner: Kevin Lelitte.

---

## 10. Communications Plan

Give Michael O'Sullivan advance notice before the production change. Review affected reporting where a department or management-unit code has been renamed, re-parented or retired. No end-user-facing communication is required for the hierarchy change itself.

---

## 11. Business Owner / Approver

Marie Cooksey — Head of HR Systems.

---

## 12. Potential security impact

None. This CR changes organisational-hierarchy and subsidiary-company records only. No change to salary, payroll or personal-data access; existing HR access and Pay Group security continue to control record and salary visibility. No credentials or payroll-sensitive data are migrated.

---

## 13. How will the security impact be tested?

Confirm that hierarchy administration remains restricted to authorised (COREPORTAL_ADMIN) users and that no salary or payroll data is exposed through the renamed or newly created units. [CONFIRM WITH KEVIN] The source draft did not specify a security test; confirm this line is sufficient.

---

## 14. Back Out Plan

Provided no posts or appointments have been created against a changed unit:

1. Restore each department or management-unit name and parent from the saved PERSUP11 baseline; reinstate L4; remove A7, B8 and 8H40.
2. Reverse the subsidiary-company actions to their baseline values, preserving the recorded XP sequence.
3. Re-run PERSUP11 and compare it with the saved pre-change report.

If posts or appointments have been created against a changed unit, reassign or close them before reversing the hierarchy change.
