# Change Request — Retrospective Change Control for RECSUP20 Applicant Cority Interface File (Rebuild Ownership: Simon Burford)

**Date:** 2026-08-20
**Drafted by:** Kevin Lelitte
**Status:** Draft

---

## 1. Details — What is changing?

RECSUP20 Applicant Cority Interface File_V1 is being formally brought under change control. No prior CR exists for this report. It was built by Grace Parsons and exists only in DEV/_Deployment — it has never been promoted to QA or Production. Ownership of a rebuild is being formally assigned to Simon Burford.

---

## 2. Justification — Why is the change necessary?

The report exports applicant data from PeopleXD to Cority for Health & Safety import processing. It has never had a change record, and a number of known defects (Section 7) need to be tracked and owned before there is further reliance on it.

---

## 3. Related Changes — Are there dependent changes?

No.

---

## 4. Impact on Dependent Services

The Cority H&S import process depends on this file. Known defects (Section 7) currently affect the reliability of that import.

---

## 5. Impact — Downtime or at-risk period

None. This CR does not deploy to a live environment.

---

## 6. Impact — Effect of not applying the change

The report remains without a formal change record or named owner, and the known defects remain unresolved.

---

## 7. Risk Assessment

Known defects, sourced from `Applicant Interface v1.sql` and the Simon Burford / James Salas email thread:

- Unfinished SQL edit — a second, incomplete query block has no SELECT clause and was never finished or retested.
- CSV export currently goes via Excel, causing header rows to split across multiple lines.
- Quotation-mark handling around comma-containing fields is not working on Cority's import side.
- Date of Birth exports with a time component instead of dd/mm/yyyy.
- Expected column count to be confirmed with Cority — email thread states 27; live report/SQL currently show more. **[CONFIRM WITH SIMON BURFORD / CORITY]**
- Null-value handling not yet configured.
- UTF-8 encoding not yet confirmed against Cority's requirement.
- Possible column-mapping mismatch under investigation via an open Cority support ticket.

No risk to Production — the report is DEV-only.

---

## 8. What is the potential security impact of the change? How will the security impact be tested?

The report exports applicant personal data (name, DOB, address, email, phone) to Cority. This CR does not change existing access or data flows.

Security testing to be defined by Simon Burford as part of the rebuild test plan — confirming only the intended fields are exported and the Cority import target matches expectations.

---

## 9. Testing — Who will test it and how?

Simon Burford will define and run a full test plan in DEV against each defect above, before requesting promotion to QA. James Salas will validate the Cority-side import behaviour.

---

## 10. Implementation Plan — Who will implement it and how?

1. Resolve the unfinished SQL edit and retest. Owner: Simon Burford.
2. Fix CSV export, quote-mark handling, and DOB format. Owner: Simon Burford.
3. Confirm expected column count and null-value handling with the business/Cority. Owner: Simon Burford.
4. Confirm UTF-8 encoding and resolve the open Cority support ticket. Owner: Simon Burford / James Salas.
5. Retest in DEV before requesting promotion to QA. Owner: Simon Burford.

---

## 11. Communications Plan — Who needs to know and how?

James Salas will be informed once the rebuild is complete and ready for Cority-side validation.

---

## 12. Documentation — Does any documentation need to be updated?

Report documentation (SQL definition, column mapping, and format) will be updated to reflect the rebuild once complete. No impact on the Service Relationship Model or Service Recovery Plan (RTO/RPO).

---

## 13. Service Sponsor / Approver

Marie Cooksey — Head of HR Systems.

---

## 14. Back Out Plan — How will it be rolled back in the event of the change failing?

The report is DEV-only with no Production dependency. If rebuild changes cause issues, revert to the last known working SQL block. Owner: Simon Burford.
