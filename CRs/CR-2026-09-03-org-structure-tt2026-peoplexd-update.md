# Change Request — Trinity Term 2026 Org Structure Update in PeopleXD (Organisational Hierarchy)

**Date:** 2026-09-03
**Drafted by:** Kevin Lelitte
**Status:** Draft

> Raised as an action from the 3 September 2026 "Organisational Structure Review (Trinity Term 2026)" meeting (K. Lelitte, M. O'Sullivan, A. Palmer, A. Kong, N. Kirwan). Intent recorded at that meeting: everything documented this time, built on the test server first, promoted environment by environment.
> **Scope confirmed by Kevin, 3 Sep 2026:** this CR covers the ~15 non-college department and subsidiary-company changes, the Merton correction (kept here as an explicit exception — see Section 1), and the associated Pay Administered By codes and baseline. The 43 Colleges & Societies L2→L3 integration stays separate, under CR-2026-06-15 / project DTP1092.

---

## 1. Details — What is changing?

The PeopleXD organisational hierarchy (UOXU first, then promoted) will be updated to match the PACS Organisational Structure published for Trinity Term 2026 (FINAL, effective dates to 19 August 2026). Source of truth: `Organisational Structure (Trinity Term 2026 FINAL PUBLISHED).xlsx`, Change Schedule tab, and Katherine Corr's 19 August 2026 PXD-specifics table (`RE: Org Structure Update`).

**Department / management-unit changes**

All name values below are taken verbatim from the FINAL PUBLISHED Change Schedule tab, which specifies **Entity Name** (short) and **Entity Full Name** separately — both fields are given, there is no outstanding choice.

| Entity | PXD action | Entity Name | Entity Full Name |
|---|---|---|---|
| B9 | Rename | Tropical Medicine - CGHR (Oxford) | Tropical Medicine - Centre for Global Health Research |
| A7 | Create new L3 Department under Paediatrics (2B18). Ignore the HESA-code schedule line | OVG | Oxford Vaccine Group |
| 8H40 | Create new L2 Management Unit | PAD | Public Affairs Directorate |
| KB | Move Department KB to new parent Management Unit 8H40 (from 8H20) | (unchanged) | (unchanged) |
| 8H20 | Rename Management Unit | VC and Registrar | Vice-Chancellor and Registrar's Office |
| L4 | Retire Department L4 "Development & External Affairs Directorate" | — | — |
| AU | Move "LaMB shared building services" from Management Unit 2B12 (Experimental Psychology) to 4D14 (Biology) | (unchanged) | (unchanged) |
| B8 | Create new L3 Department under Physiology, Anatomy & Genetics (2B27). Ignore the HESA-code schedule line | CNCB | Centre for Neural Circuits and Behaviour |
| KY | Rename | LOD | Learning and Organisational Development |
| A1 | Rename | DCH Building Operations | Dorothy Crowfoot Hodgkin Building Operations |
| CC | Rename | Cross-RDM | Cross-RDM Professional Services |
| C1 | Rename | NDM Education | NDM Education |
| BH | Rename | NDM Operations | NDM Operations |
| 8HP0 | Rename Management Unit | Digital and information services | Digital and information services |
| E7 | Rename — **Entity Name is unchanged ("Office of the CDIO"); only the Entity Full Name changes** from "Office of the Chief Digital Information Officer" to "Chief Digital and Information Officer". This is the only one of the 15 non-college items whose target value is not yet reflected in Org Structure Data (source change effective 12 Aug 2026). | Office of the CDIO (unchanged) | Chief Digital and Information Officer |

**Merton correction**

- Re-parent L3 code RP ("Merton College") from L2 0B13 (Lincoln) to L2 0B15 (Merton). Confirmed by PACS on 1 September 2026 as an error in the published structure; intended pairing is RM → 0B13 Lincoln, RP → 0B15 Merton.
- **Scope exception, confirmed by Kevin 3 Sep 2026:** although Merton/Lincoln sit inside the 43-college recode/re-create sequence (Change Schedule rows 49–54) otherwise tracked under CR-2026-06-15/DTP1092, this single re-parent is actioned under this CR — it is a correction to an existing error, not part of the colleges build. Owner: Kevin Lelitte.
- **[CONFIRM]** that PACS has reissued the published Organisational Structure file / report tabs cleanly before this is actioned.

**Subsidiary companies (Level 2, under 0D)**

- Delete (no longer operating): V4 Instruct; VD Voltaire Foundation Limited; X3 OUC Investments Limited; X4 Oxford University Clinic LLP; V6 Oxford University (Beijing).
- Rename to legal identity: V7 → Health Research Operations Kenya Limited; V5 → Oxford Advanced Research Centres Limited; X2 → Oxford Research South Africa Limited; VU → Oxford University Endowment Management Limited.
- Create: X0 Ecosystem Capital Limited; XL Endowment Estates Limited; XM OUPM Ltd; XQ Oxford GLAM Enterprises Limited; XR Oxford Research South Africa Limited (External Company Registration); XS Oxford University Development (North America), Inc; XT Oxford University Trading Limited; XU Oxuniprint Limited; XV Medical Sciences Commercial Services Limited; XW Proxemis Limited; XY TOF Corporate Trustee Limited; XZ University of Oxford China Office Limited; Y0 Yayasan Jalin Kemitraan Nusantara; Y1 Oxford University Clinical Research Unit Nepal; Y2 Oxford University (Suzhou) Science & Technology Co. Ltd.
- **Not created:** XP "Oxuniprint Ltd" — a duplicate of XU; removed by PACS, reference retained in the change record only.

**Reference data**

- Create Pay Administered By (USER5) reference-data codes for the new department codes A7 and B8: **A7DEP, A7DIV, B8DEP, B8DIV** (the standard two-code-per-department pattern per *HOW TO Manage the Org Hierarchy v4.0* §8). Create each as reference data and link each at the bottom level of the hierarchy. No separate approval required (confirmed by M. O'Sullivan, 3 Sep 2026 review). **[CONFIRM WITH KEVIN]** if any of the four is not required (e.g. a department that genuinely needs only DEP).
- Run and save the Active Hierarchy report (PERSUP11) **before** any change is made, as the pre-change baseline. Owner: Asta Palmer.

**Method:** all hierarchy maintenance is done via the Portal (not Back Office), consistent with the Back-Office-to-Portal migration and the COREPORTAL_ADMIN menu-option enablement (CR 20020472).

---

## 2. Justification — Why is the change necessary?

PeopleXD must stay in lockstep with the published PACS Organisational Structure so that posts, appointments, staff requests, HESA returns and downstream system feeds are administered against the correct organisational units. The Trinity Term 2026 changes are published and effective; the corresponding PeopleXD hierarchy has not yet been updated in the production environment. The 3 September 2026 review also identified that a previous cycle missed the Pay Administered By (USER5) build step for new department codes — this CR makes that step explicit so it is not missed again.

---

## 3. Related Changes — Are there dependent changes?

- **CR-2026-06-15** — Colleges & Halls org hierarchy and non-payroll company set-up (UOXU). The 43 Colleges & Societies L2→L3 integration (Option 2, agreed by Anne Mortimer 1 Sep 2026 — integrate L2 codes into management units, L4 renamed "colleges") is tracked there / under project **DTP1092 College Staff into PeopleXD**.
- **CR 20020472** — Enable 16 COREPORTAL_ADMIN menu options for Portal-based hierarchy maintenance. This is a prerequisite for the Portal work in this CR. **[CONFIRM status — weekly "Update Required" reminders were still being issued to 31 Aug 2026.]** A related change record, CR 20020477, was seen directly in Kevin's Outlook mailbox (Drew's live COM pull, 3 Sep) as a near-duplicate ITSM entry with its own RecId — it is not in any saved export and its relationship to 20020472 is not independently confirmed here; check both when following up.
- **FP 68261303** — Multi Company Setup with Access Group.
- Loading of the 40 REF2029 / Pay Administered By college codes is part of the colleges workstream (see command-centre task t005), not this CR.

---

## 4. Impact on Dependent Services — What is the impact on connected or downstream services or components?

- Once implemented, the updated units are visible in the organisational hierarchy to authorised users, and available for post and appointment management.
- Reporting or processes filtered by department code or management unit may need review where a code has been renamed, re-parented, or retired (B9, 8H20, KB, AU, C1, BH, 8HP0, E7, L4, RP).
- **HESA:** department code drives the Exemption Rules that determine which records enter the HESA Module (flagged by S. Rowles, 17 Aug 2026). The Exemption Rules should be reviewed against the current population once the changes are in place, and may need updating for the next return.
- **Data warehouse / H&S dashboard:** the org-structure mapping tables — including the H&S dashboard mapping maintained by D. Johnson and C. Sanders — may need updating (flagged by S. Burford, 17 Aug 2026).
- **H&S systems fed from Azure (Cority, DSE/Cardinus):** college records auto-created by the feed can duplicate manually created `UOX-DEP` entries; cleansing may be required. IRIS needs L3 University codes populated for Kellogg, Reuben and St Cross. These sit with the H&S systems owners, referenced here for awareness.
- No integration, payroll calculation, or salary-data access is changed by this CR.

---

## 5. Impact — Specify downtime or at-risk period

No service outage expected. The change adds, renames, re-parents and retires organisational-hierarchy and reference-data records only. No existing staff records or live payroll data are altered. Work is done in the test environment first and promoted environment by environment with verification at each stage. **Release route, confirmed by Kevin 3 Sep 2026:** UOXU (UAT) → UOXZ (Sandpit & Training) → UOXC (Configuration) → UOXP (Production) — the same route used for CR 20020472.

---

## 6. Impact — Effect of not applying the change

PeopleXD's organisational hierarchy remains out of step with the published PACS structure. New departments (A7 OVG, B8 CNCB) and the new management unit 8H40 (PAD) cannot be used; renamed and re-parented units carry stale names/parents; the Merton RP mis-parenting persists; retired unit L4 remains selectable; the E7 rename stays outstanding. Posts and appointments would continue to be created against an incorrect structure, and the Pay Administered By codes for the new departments would again be missed.

---

## 7. Risk Assessment — What are the risks to the services?

- **Wrong source version.** The published report tabs carried a Merton/Lincoln swap; the Change Schedule tab is authoritative. Mitigation: build only from the Change Schedule tab of FINAL PUBLISHED, and confirm PACS has reissued the published file cleanly before actioning the Merton re-parent.
- **Renamed/re-parented codes break downstream filters.** Mitigation: pre-change Active Hierarchy baseline (PERSUP11) captured and saved; post-change PERSUP11 compared; affected reports reviewed (Section 4).
- **Pay Administered By codes missed for A7 / B8.** Mitigation: called out as an explicit implementation step in this CR (Section 9).
- **B8 code collision.** B8 was historically a live costing code alongside BQ ("Human Anatomy & Genetics"); both dropped out of the live structure between Feb 2024 and Jan 2025. Whether BQ is still a live/available code needs checking against the Active Hierarchy report before B8 is created. **[CONFIRM — item for the Simon Burford / PACS follow-up.]**
- **Portal permissions not in place.** Dependent on CR 20020472. Mitigation: verify COREPORTAL_ADMIN menu options are enabled in the target environment before starting.
- All changes are reversible at the configuration-record level provided no posts/appointments have been created against a new or changed unit (see Section 14).

---

## 8. Potential Security Impact — What is it and how will it be tested?

No change to salary, payroll or personal-data access. This CR changes organisational-hierarchy and reference-data records only. Existing HR access and Pay Group security continue to control record and salary visibility. No credentials or payroll-sensitive data are migrated. Security testing: confirm that hierarchy administration remains restricted to COREPORTAL_ADMIN users and that no salary or payroll data is exposed through the renamed/created units.

---

## 9. Testing — Who will test it and how?

Kevin Lelitte / Asta Palmer (HR Systems) will, in each environment (release route per Section 5):

- Verify each renamed unit shows the agreed Entity Name **and** Entity Full Name exactly as in Section 1 (both fields).
- Verify A7 (under 2B18), B8 (under 2B27) and 8H40 exist with the correct parent.
- Verify KB sits under 8H40, AU sits under 4D14, RP sits under 0B15, and L4 is retired / not selectable.
- Verify each of **A7DEP, A7DIV, B8DEP, B8DIV** exists as USER5 reference data and is linked at the bottom level; capture the screenshot / report line as evidence per code.
- Verify the subsidiary-company deletes, renames and creations are reflected under 0D.
- Run the standard post-change checklist from *HOW TO Manage the Org Hierarchy v4.0*, Section 15 (create post / vacancy / staff request / casual worker appointment in test; search by department; view an employee's appointment; re-run PERSUP11) and compare PERSUP11 against the saved pre-change baseline.

Backup Restore and Service Recovery testing are not required — configuration records only, no infrastructure or recovery-arrangement impact.

---

## 10. Implementation Plan — Who will implement it and how?

| Step | Owner | Status |
|---|---|---|
| 1. Run and save the Active Hierarchy report (PERSUP11) as the pre-change baseline | Asta Palmer | TODO |
| 2. Confirm PACS has reissued the published Organisational Structure file / report tabs cleanly (Merton correction) | Kevin Lelitte / Katherine Corr | TODO |
| 3. Confirm CR 20020472 COREPORTAL_ADMIN menu options are enabled in the target environment | Kevin Lelitte / Asta Palmer | TODO |
| 4. Apply the department / management-unit changes and the Merton re-parent in UOXU via the Portal | Kevin Lelitte / Asta Palmer | TODO |
| 5. Apply the subsidiary-company deletes / renames / creations in UOXU | Kevin Lelitte / Asta Palmer | TODO |
| 6. Create USER5 codes A7DEP, A7DIV, B8DEP, B8DIV and link each at bottom level | Kevin Lelitte / Asta Palmer | TODO |
| 7. Test and verify the test environment (Section 9) | Kevin Lelitte / Asta Palmer | TODO |
| 8–9. Promote through the intermediate environments (route per Section 5), verify at each | Kevin Lelitte / Asta Palmer | TODO |
| 10. Promote to Production (UOXP), verify and sign off | Kevin Lelitte | TODO |
| 11. Send Katherine Corr an updated Department report from PXD for the PACS Dynamics mapping | Kevin Lelitte | TODO |

---

## 11. Communications Plan — Who needs to know and how?

- Advance notice to Michael O'Sullivan before the UOXP change, so recruitment (University-wide), payroll and grading-analyst permission updates can be prepared (action from the 3 Sep 2026 review).
- Notify the HESA lead (Sarah Rowles) and the data-warehouse / H&S dashboard owners (David Johnson, Christopher Sanders) so mapping tables and Exemption Rules can be reviewed.
- No end-user-facing communication required for the hierarchy change itself.

---

## 12. Documentation — Does any documentation need to be updated?

- *HOW TO Manage the Org Hierarchy v4.0* — update Section D to reflect Portal-first hierarchy linking (currently documents Back Office), and add a COREPORTAL_ADMIN / access-group procedure (currently absent). Tracked in the project Change Register (items 10, 11).
- File this cycle's artefacts to the network share under a `2026_27 Changes` folder and run the CoreHR cross-check template against live PeopleXD data (per *Managing the regular updates to the Org structure v2.0*). Tracked as Change Register item 13.
- The change does not affect the Service Relationship Model, Service Recovery Plan, RTO or RPO.

---

## 13. Service Sponsor / Approver

Marie Cooksey — Head of HR Systems. Confirmed by Kevin, 3 Sep 2026.

---

## 14. Back Out Plan — How will it be rolled back in the event of the change failing?

Provided no posts or appointments have been created against a new or changed unit:

1. Revert each renamed unit to its previous Entity Name and Entity Full Name; re-parent KB to 8H20, AU to 2B12, RP to 0B13; reinstate L4.
2. Delete the new units A7, B8 and 8H40, and delete each of the USER5 codes A7DEP, A7DIV, B8DEP, B8DIV and their bottom-level links.
3. Reverse the subsidiary-company changes: recreate V4, VD, X3, X4, V6; revert V7, V5, X2, VU names; delete X0, XL, XM, XQ, XR, XS, XT, XU, XV, XW, XY, XZ, Y0, Y1, Y2.
4. Restore from the saved pre-change Active Hierarchy (PERSUP11) baseline for comparison.

Once posts or appointments have been created against a new or changed unit, those must be reassigned or closed before that unit can be rolled back.
