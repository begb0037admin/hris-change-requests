Change Request — Trinity Term 2026 Organisational Structure Update in PeopleXD


1.	Details - What is changing?

== This change request covers only the organisational-structure actions in Organisational Structure (Trinity Term 2026 FINAL PUBLISHED).xlsx, Change Schedule rows 8–24 and 111–136. The Change Schedule is authoritative.

Scope: 17 department and management-unit schedule rows (rows 10 and 17 are HESA-code notes, not hierarchy build actions), and 26 subsidiary-company schedule rows (24 net actions — schedule rows 123 and 124 create and then delete the same code, XP, and cancel out; see below).

The PERSUP11 Active Hierarchy report has been saved as the pre-change baseline at 03 Change Register and Working Tool\Evidence\Pre-change\PERSUP11 Active Hierarchy 03SEP2026.xlsx. It records the before-state; it does not replace the appointment/post check required before a move or retirement.

Department and management-unit actions (code — action — scheduled Entity Name / Entity Full Name where changed):
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

Row 10 records HESA code 101 for A7 and row 17 records HESA code 106 for B8. These are source notes only, not hierarchy build actions.

Before creating B8, verify the code is available in the target environment (the saved baseline is the evidence). Before moving or retiring an item, run PERSUP11_Organisation Restructure and clear any active appointments, unassigned posts or open unused vacancies first.

Subsidiary-company actions under Level 2 entity 0D:
- Delete: V4 Instruct; VD Voltaire Foundation Limited; X3 OUC Investments Limited; X4 Oxford University Clinic LLP; V6 Oxford University (Beijing).
- Rename: V7 to Health Research Operations Kenya Limited; V5 to Oxford Advanced Research Centres Limited; X2 to Oxford Research South Africa Limited; VU to Oxford University Endowment Management Limited.
- Create: X0 Ecosystem Capital Limited; XL Endowment Estates Limited; XM OUPM Ltd; XQ Oxford GLAM Enterprises Limited; XR Oxford Research South Africa Limited (External Company Registration); XS Oxford University Development (North America), Inc; XT Oxford University Trading Limited; XU Oxuniprint Limited; XV Medical Sciences Commercial Services Limited; XW Proxemis Limited; XY TOF Corporate Trustee Limited; XZ University of Oxford China Office Limited; Y0 Yayasan Jalin Kemitraan Nusantara; Y1 Oxford University Clinical Research Unit Nepal; Y2 Oxford University (Suzhou) Science & Technology Co. Ltd.

XP is not built. The Change Schedule adds an Oxuniprint company twice — XP "Oxuniprint Ltd" (row 123) and XU "Oxuniprint Limited" (row 129) — and then corrects the error by deleting XP (row 124, "Delete second Subsidiary company for OxUniprint made in error"). Rows 123 and 124 cancel out, so no XP company is created; XU "Oxuniprint Limited" is the Oxuniprint entity that exists. These two rows are noted only so a row-by-row reconciliation shows why XP is absent.

Method: build in the agreed test environment using the Portal hierarchy-maintenance procedure.


2.	Justification - Why is the change necessary?

== PeopleXD's organisational hierarchy must match the published PACS Organisational Structure for Trinity Term 2026 so that posts, appointments, staff requests and downstream feeds are administered against the correct organisational units. The Trinity Term 2026 structure is published and effective; the PeopleXD hierarchy has not yet been updated.


3.	Related Changes - Are there dependent changes?

== None. This change updates organisational-hierarchy and subsidiary-company records only and does not depend on any other change.


4.	Impact on dependent services? What is the impact on connected or downstream services or components?

== The change updates organisational hierarchy configuration only. No integration, payroll calculation, salary data or personal data is changed. Reporting or processes filtered by a department or management-unit code should be reviewed where a code has been renamed, re-parented or retired (B9, 8H20, KB, AU, C1, BH, 8HP0, E7, L4).


5.	Impact - Specify downtime or at risk period

== None. No service outage is expected. The change adds, renames, re-parents and retires organisational-hierarchy records only; no existing staff records or live payroll data are altered. Work is done in the test environment first and promoted environment by environment with verification at each stage.


6.	Impact - Effect of not applying the change?

== PeopleXD retains stale names, parents and subsidiary-company records; the new departments (A7 OVG, B8 CNCB) and the new management unit (8H40 PAD) cannot be used; posts and appointments continue to be created against an incorrect structure.


7.	Risk Assessment - What are the risks to the services?

== Low.
- B8 must be confirmed available in the target environment before it is created (the saved PERSUP11 baseline is the evidence).
- Before moving or retiring KB, AU or L4, run PERSUP11_Organisation Restructure and clear any active appointments, unassigned posts or open unused vacancies first.
- Renamed or re-parented codes may affect downstream report filters; mitigated by the saved pre-change PERSUP11 baseline, the post-change comparison, and the reporting review in Sections 4 and 10.
- All changes are reversible at configuration-record level provided no posts or appointments have been created against a new or changed unit (see Section 14).


8.	Testing - Who will test it and how?

== Kevin Lelitte and Asta Palmer will, in the test environment:
- Verify every in-scope value against Change Schedule rows 8–24 and 111–136.
- Verify A7 under 2B18, B8 under 2B27, 8H40, KB under 8H40, AU under 4D14, retirement of L4, and E7's Entity Full Name.
- Verify each subsidiary-company action; confirm no XP company exists and XU "Oxuniprint Limited" is present.
- Run the standard functional hierarchy checks.
- Re-run PERSUP11 Active Hierarchy and compare with the saved pre-change baseline.
- Save the post-change export alongside the baseline, with implementation and test evidence, in the documented cycle location before promotion.


9.	Implementation Plan - Who will implement it and how?

== Kevin Lelitte / Asta Palmer will implement via the Portal:
1. Confirm source values against the Change Schedule.
2. Verify B8 availability against the saved PERSUP11 baseline.
3. Apply the department and management-unit actions in the test environment.
4. Apply the subsidiary-company actions in the test environment.
5. Test, compare PERSUP11 against the saved baseline, and save evidence.
6. Promote through the approved environments, verifying each stage.
7. Complete production verification and sign-off (Kevin Lelitte).


10.	Communications Plan – Who needs to know and how?

== Give Michael O'Sullivan advance notice before the production change. Review affected reporting where a department or management-unit code has been renamed, re-parented or retired. No end-user-facing communication is required.


11.	Business Owner/Approver

== Marie Cooksey — Head of HR Systems (Coordinator: Kevin Lelitte).


12. What is the potential security impact of the change?

== None. The change updates organisational-hierarchy and subsidiary-company records only. No change to salary, payroll or personal-data access; existing HR access and Pay Group security continue to control record and salary visibility. No credentials or payroll-sensitive data are migrated.


13. How will the security impact be tested?

== Confirm that hierarchy administration remains restricted to authorised (COREPORTAL_ADMIN) users and that no salary or payroll data is exposed through the renamed or newly created units.


14.	Back Out Plan - How will it be backed out in the event of the change failing?

== Provided no posts or appointments have been created against a changed unit:
1. Restore each department or management-unit name and parent from the saved PERSUP11 baseline; reinstate L4; remove A7, B8 and 8H40.
2. Reverse the subsidiary-company actions to their baseline values.
3. Re-run PERSUP11 and compare with the saved pre-change report.
If posts or appointments have been created against a changed unit, reassign or close them before reversing the hierarchy change.
