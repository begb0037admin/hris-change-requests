# Change Request — Retrospective Change Control for RECSUP20 Applicant Cority Interface File (Rebuild Ownership: Simon Burford)

**Date:** 2026-08-20
**Drafted by:** Kevin Lelitte
**Status:** Draft

---

## 1. Details — What is changing?

This CR retrospectively brings the report **RECSUP20_Applicant Cority Interface File_V1** under formal change control. No prior Change Request exists for this report — it has been in use without one.

**Report identity:** RECSUP20 Applicant Cority Interface File_V1 — a PeopleXD report that exports applicant data for import into Cority (the University's Health & Safety system).

**Current deployment status:** The report exists only in the **DEV/_Deployment** environment. It has never been promoted to QA or Production.

**Origin and authorship:** The report was built by **Grace Parsons**, who carried out the substantial majority of the analysis, build, and testing work. This is confirmed both by the email handover summary and independently by the document/workbook metadata on the source files (all held at `I:\ADMN\PS\HR Systems\Support\Analysis Team\Grace - Investigations\2025-03 Cority Applicant Data\`):

| File | Creator (metadata) | Created | Last modified |
|---|---|---|---|
| RECSUP20_Applicant Cority Interface File_V1.xlsx | Grace Parsons | 2025-03-05 | 2025-03-21 |
| Meeting Example RECSUP20...xlsx | Grace Parsons | 2025-03-07 | 2025-05-06 |
| May 2025\Report Example RECSUP20...xlsx | Grace Parsons | 2025-03-07 | 2025-05-06 |
| Round 2\RECSUP20...(5).xlsx | Grace Parsons | 2025-03-21 | 2025-03-21 |
| Testing Plan and Evidence - GP Cority Applicant Data.docx | Grace Parsons | 2025-03-06 | 2025-03-10 |

**[TBC — Grace Parsons' exact handover date is not stated in any source material or the email summary provided. The metadata above shows a build/activity window of March–May 2025 but this is not the same thing as a formal handover date. Confirm with Kevin/Grace if needed.]**

The report was subsequently picked up **informally** by James Salas and Lee Strudwick, with no formal change record created at that time. Lee Strudwick has since left the University and is not the focus of this CR. This CR is the first formal change-control record for this report.

This CR formally hands ownership of a full **rebuild** of this report to **Simon Burford**, per the Simon Burford / James Salas email thread (11–18 August 2026).

---

## 2. Justification — Why is the change necessary?

**Business purpose:** The report exports applicant data from PeopleXD to Cority, for use in Cority's Health & Safety / occupational health import processing.

**Justification for raising this CR now:**
- No change record has ever existed for a report that handles and exports personal applicant data (including date of birth) to an external system. This is a governance and audit gap that this CR closes.
- Ownership needs to be formally assigned to Simon Burford so the report has a named, accountable owner going forward.
- A number of known defects (Section 7) need to be tracked and resolved before there is any further reliance on this report, and before any promotion beyond DEV is considered.

---

## 3. Related Changes — Are there dependent changes?

None are evidenced in the source material reviewed (SQL, original interface text, testing plan, report examples, and the Simon Burford / James Salas email thread). **[If Simon Burford identifies any dependent changes during rebuild scoping — e.g. changes required on the Cority side to resolve the open support ticket in Section 7 — these should be raised as separate, linked CRs.]**

---

## 4. Impact on Dependent Services

The Cority H&S import process is dependent on this file. The known defects listed in Section 7 currently affect the reliability, completeness, and accuracy of that downstream import (e.g. malformed CSV headers, DOB formatting, and a possible column-mapping mismatch currently under investigation via an open Cority support ticket).

No other PeopleXD reports or downstream systems are evidenced as depending on this file.

---

## 5. Impact — Downtime or at-risk period

None. This CR does not deploy any change to a live environment. It formally documents the existing DEV-only state of the report and scopes a future rebuild. No promotion to QA or Production is being carried out under this CR.

---

## 6. Impact — Effect of not applying the change

If this CR is not raised, the report continues to exist without a formal change record or a named accountable owner, remains DEV-only with no documented path to QA/Production, and the known defects in Section 7 remain unresolved and untracked. Applicant data exports to Cority for H&S purposes remain unreliable, and the audit gap (a personal-data export process with no change history) remains open.

---

## 7. Risk Assessment

**Governance risk:** The absence of any prior change record for a report handling personal applicant data (name, DOB, address, email, phone number) exported to an external system is itself a risk. This CR closes that gap.

**Technical risk — known defects**, sourced from `Applicant Interface v1.sql`, the Simon Burford / James Salas email thread, and the open Cority support ticket:

1. **Unfinished SQL edit.** `Applicant Interface v1.sql` contains two blocks. The first (lines 1–49) is complete: `SELECT ... FROM rtbi_applicant_master INNER JOIN prbi_appointment_history ... INNER JOIN prbi_post_profile ... WHERE rtbi_applicant_master.applicant_status IN ('ACCP','OFFP','ACC','OFF','TSS','TSOA','TSOM') AND ... status_date >= sysdate-30`. Below it (line 54), an inline note reads *"new section to replace the other, replace and then retest."* A second block follows (lines 57–72) that switches both joins to `LEFT OUTER JOIN` on `prbi_appointment_history` and `prbi_post_profile`, and changes the status filter to `IN ('ACCP','OFFP','ACC','OFF','TSOA','TSOM')` — i.e. **`'TSS'` is dropped** from the list compared to the first block. Critically, this second block **has no `SELECT` clause at all** — it starts directly with `FROM`. It was never completed and, per the note left in the file, was never retested. **[CONFIRM WITH SIMON BURFORD — whether dropping status code 'TSS' was an intended business rule change or an in-progress edit that was abandoned; this needs to be resolved, not assumed, before the rebuild.]**
2. CSV export currently goes via an Excel conversion step, which causes header rows to split across multiple lines in the resulting CSV.
3. Quotation-mark handling around comma-containing fields is not working as expected on Cority's import side.
4. Date of Birth exports with a time component rather than `dd/mm/yyyy` only. This is corroborated by the underlying cell data in the live report examples (e.g. `RECSUP20_Applicant Cority Interface File_V1.xlsx`, `Round 2\...(5).xlsx`), where DOB values are stored as full datetimes (e.g. `1988-10-03 00:00:00`) rather than date-only values.
5. The report must guarantee all expected columns/headers are present even when no data exists. **[Discrepancy flagged, not resolved — the Simon Burford / James Salas email thread refers to "all 27 columns." Independently counting the live report header row (`RECSUP20_Applicant Cority Interface File_V1.xlsx`, row 6) shows 31 named column headers across 32 columns (one blank/merged cell), and the SQL `SELECT` list in `Applicant Interface v1.sql` returns 32 fields. CONFIRM WITH SIMON BURFORD / CORITY the exact expected column count and order before rebuild, rather than relying on either figure as authoritative.]**
6. Null-value handling is not yet explicitly configured. Options under consideration per the email thread: blank, `NULL`, `N/A`, or `-`.
7. UTF-8 encoding has not yet been confirmed against Cority's expected format.
8. A possible column-mapping mismatch is under investigation via an open Cority support ticket (ticket reference not provided in the source material — **[CONFIRM WITH KEVIN/SIMON BURFORD]**).

**Mitigation:** This CR does not promote the report; it formalises ownership and scopes the rebuild so each defect above can be addressed and retested in DEV before any promotion is considered (see Section 9 and the recommendation below).

---

## 8. Testing — Who will test it and how?

An existing `Testing Plan and Evidence - GP Cority Applicant Data.docx` (authored by Grace Parsons, created 2025-03-06, last modified 2025-03-10) exists at the same network location. Its content is limited — it records a small number of applicant numbers used in test runs and a note that, if a particular filtering approach is used, Occupational Health would need to be warned that backdated statuses may also be pulled through and may not be required. It does not evidence that Cority-side testing was completed.

Per Grace Parsons' handover, the following items were **outstanding at handover** and are not evidenced as having been completed since:
- Cority-side testing
- Duplication-checking training
- Automation of the pull/save process

**Going forward:** Simon Burford will define and execute a full test plan against the rebuilt report in DEV, covering each defect in Section 7, before any request to promote the report to QA. James Salas / the Cority support ticket contact should be involved in validating the Cority-side import behaviour specifically (quote-mark handling, column mapping, encoding).

---

## 9. Implementation Plan

Step 1 — Resolve the unfinished SQL edit in `Applicant Interface v1.sql` (lines 51–72): decide, with the business, whether status code `'TSS'` should be included or excluded from the applicant status filter, then either complete and retest the `LEFT OUTER JOIN` block (adding the missing `SELECT` clause) or formally revert to the working `INNER JOIN` block. Owner: Simon Burford.

Step 2 — Change the export method to export directly to CSV rather than via Excel conversion, to eliminate the multi-row header split. Owner: Simon Burford.

Step 3 — Fix quotation-mark handling around comma-containing fields so Cority's import parses them correctly. Owner: Simon Burford.

Step 4 — Correct the Date of Birth export format to `dd/mm/yyyy` only, removing the time component. Owner: Simon Burford.

Step 5 — Confirm the exact expected column count and order with Cority/the business (resolving the 27 vs. 31/32 discrepancy in Section 7, point 5), then guarantee all expected columns/headers are always present in the output, including when no data rows exist. Owner: Simon Burford.

Step 6 — Decide and implement a null-value handling convention (blank, `NULL`, `N/A`, or `-`). Owner: Simon Burford.

Step 7 — Confirm and implement UTF-8 encoding against Cority's expected format. Owner: Simon Burford.

Step 8 — Resolve the open Cority support ticket regarding the possible column-mapping mismatch, and reconcile findings into the rebuilt column mapping. Owner: Simon Burford / James Salas.

Step 9 — Retest the full report end-to-end in DEV against the outstanding items from Grace Parsons' handover (Cority-side testing, duplication checking, pull/save automation) and the defects above, before requesting promotion to QA. Owner: Simon Burford.

---

## 10. Communications Plan

James Salas (current informal contact and Cority support ticket liaison) should be notified once the SQL and column-mapping questions are resolved, so Cority-side validation can proceed. **[CONFIRM WITH KEVIN whether wider communication is needed — e.g. to Occupational Health/H&S stakeholders — this is not evidenced in the source material reviewed.]**

---

## 11. Business Owner / Approver

Marie Cooksey — Head of HR Systems.

---

## 12. Potential security impact

The report exports applicant personal data — including name, date of birth, home address, email address, and mobile phone number — to Cority, an external Health & Safety system. This CR itself does not introduce a new data flow or change existing access/permissions; it formalises change control over, and scopes a rebuild of, a report and export process that already exists and is already relied upon informally. **[CONFIRM WITH KEVIN/SIMON BURFORD whether any of the specific rebuild fixes — e.g. the DOB time-component correction, or the null-value handling decision — change what is technically exposed to Cority. Not evidenced either way in the source material.]**

---

## 13. How will the security impact be tested?

**[TBC — not evidenced in the source material beyond the existing Testing Plan and Evidence document and the open Cority support ticket, neither of which addresses security/data-exposure testing specifically. Simon Burford should define explicit security/data-exposure test steps — e.g. confirming only the intended fields are exported and that the Cority import target matches expectations — as part of the rebuild test plan in Section 8/9.]**

---

## 14. Back Out Plan

The report exists only in DEV/_Deployment and has never been promoted to QA or Production, so there is no live/Production dependency to roll back.

Step 1 — If rebuild changes made in DEV cause issues, revert the report/SQL definition to the last known working state — the original, complete `INNER JOIN` block (`Applicant Interface v1.sql`, lines 1–49) or an earlier saved version of the report. Owner: Simon Burford.

Step 2 — Confirm DEV output has been restored to the pre-rebuild working state. Owner: Simon Burford.

No Production data or live service is affected by this CR; rollback carries no data-loss risk.

---

## Recommendation

Once the rebuild (Section 9) is complete and retested against the defects in Section 7, this report should be formally promoted through QA — with sign-off from Simon Burford and, per Section 11, Marie Cooksey — before any further reliance is placed on it for live Cority H&S applicant data processing. It should not be treated as production-ready in its current DEV-only, unfixed state.
