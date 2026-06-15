# Change Request — Colleges & Halls Org Hierarchy & Payroll Company Set-Up (UOXU)

**Date:** 2026-06-15  
**Drafted by:** Claude Code / Kevin Lelitte  
**Status:** Draft

---

## 1. Details – What is changing?

Setting up a new non-payroll organisation structure in PeopleXD (UOXU) for Colleges & Halls. Components:

- **Company (Code 90):** “Non-Payroll Colleges & Halls” — copied from existing Colleges & Halls company; all payroll-registered fields (tax, calendar, revenue) left blank as this company will not run payroll
- **Pay Group (Code 90):** “ZZ Do Not Use Non-Pay” — duplicated from the existing non-employees pay group; linked to Company 90
- **Division:** 901 — Colleges & Halls — linked to Company 90
- **Subdivision (USER_CODE1):** ZSD901 — Colleges & Halls
- **Level 4 (USER_CODE2):** Z90101 — Colleges & Halls
- **Management Units:** Z901 (Colleges & Halls), Z902 (Permanent Private Halls)
- **Pay Admin by Code values:** to be loaded via the HR Reference data migration template (pipe-delimited format); avoids manual entry
- **Hierarchy linking:** all reference data to be linked in portal (not back office)
- **Access grants:** HR access and Pay Group 90 access to be granted to relevant users

> **Note:** Division Code configuration cannot be completed until the Company Code relationship is clarified — pending a configuration session with Conor (The Access Group). See Section 3.

---

## 2. Justification – Why is the change necessary?

Colleges & Halls staff need to be managed within PeopleXD UOXU (appointments, posts, hierarchy visibility) but are not on the University of Oxford payroll. The existing company structure does not accommodate this population. A separate non-payroll company and pay group are required to enable HR management of these staff without triggering payroll processing.

---

## 3. Related Changes – Are there dependent changes?

- **Division Code configuration** — blocked pending Conor’s (The Access Group) configuration session on Friday to clarify Company Code / Division Code relationship. Cannot be set up until that session completes.
- **Pay Admin by Code data migration** — separate upload step using HR Reference template; to follow company/pay group creation.
- **Post creation and staff assignment** — subsequent steps after hierarchy is built and access granted; out of scope of this CR.

---

## 4. Impact on Dependent Services – What is the impact on connected or downstream services or components?

- Post profiles for Colleges & Halls staff will become visible in portal once HR access is granted to Company 90
- **Pay Group access governs salary tab visibility:** users without explicit Pay Group 90 access will not see the salary tab for Colleges & Halls staff even if they have company-level HR access
- Any existing HR reports or processes scoped by company will need to be reviewed to include Company 90 if Colleges & Halls staff are to appear

---

## 5. Impact – Specify downtime or at-risk period

Minimal. This creates new records (company, pay group, reference data) with no existing staff or live payroll data attached. The existing University of Oxford payroll company is not affected.

---

## 6. Impact – Effect of not applying the change

Colleges & Halls staff cannot be managed in PeopleXD UOXU. No posts can be created for this population. HR visibility of this staff group is not available.

---

## 7. Risk Assessment – What are the risks to the services?

- **Pay group creation error (medium):** Pay Group 90 failed to appear after creation during the 12 June demo session. Root cause unresolved — The Access Group to investigate post-call. Risk mitigated by: issue was caught immediately; no staff were assigned; deletion is safe at this stage.
- **Data carry-over from copied company (low):** Mitigated by reviewing all sections of the copied company and removing non-applicable fields (revenue information, tax details cleared during session).
- **Access not granted (low):** If HR access or Pay Group access is not granted, created records become invisible to users. Mitigated by completing access grants as a mandatory step before handover.

---

## 8. Testing – Who will test it and how?

- **Kevin Lelitte / HR Systems** to verify: Company 90 appears in organisations list; Pay Group 90 appears in managed payroll; hierarchy links correctly in portal; HR and pay group access grants work as expected; salary tab visibility is correctly controlled by pay group access
- **The Access Group** to confirm Pay Group 90 creation issue resolved before final sign-off

---

## 9. Implementation Plan – Who will implement it and how?

| Step | Owner | Status |
|---|---|---|
| 1. The Access Group investigates and resolves Pay Group 90 creation error | The Access Group | [TODO — post 12 Jun call] |
| 2. The Access Group confirms Division Code / Company Code relationship | The Access Group / Kevin | [AWAITING — Friday config session] |
| 3. Load Pay Admin by Code values via data migration tool (HR Reference template) | Kevin Lelitte | [TODO] |
| 4. Build hierarchy linking in portal (not back office) | Kevin Lelitte | [TODO] |
| 5. Grant HR access to Company 90 for relevant users | Kevin Lelitte | [TODO] |
| 6. Grant Pay Group 90 access for relevant users | Kevin Lelitte | [TODO] |
| 7. Test and verify (see Section 8) | Kevin Lelitte | [TODO] |

---

## 10. Communications Plan – Who needs to know and how?

Michelle Williams (Comms) to be notified once the change is ready to go live, to manage any user-facing communications regarding Colleges & Halls staff visibility in PeopleXD.

---

## 11. Business Owner / Approver

Marie Cooksey — Head of HR Systems

---

## 12. What is the potential security impact of the change?

- Pay Group 90 access controls salary visibility for Colleges & Halls staff — must only be granted to authorised users
- No payroll-sensitive data or credentials are being migrated; this is a non-payroll company
- Access grants (HR access, pay group access) should be reviewed to ensure minimum necessary access

---

## 13. How will the security impact of the change be tested?

- Verify that a user **without** Pay Group 90 access cannot see the salary tab for Colleges & Halls staff
- Verify that a user **without** Company 90 HR access cannot see posts or appointments under that company

---

## 14. Back Out Plan – How will it be backed out in the event of the change failing?

At this stage (pre-staff-assignment), both new records can be safely deleted:

1. Delete Pay Group 90 first — safe while no staff are assigned (deletion is blocked once staff are associated)
2. Delete Company 90 from organisations list
3. Remove reference data (Division 901, ZSD901, Z90101, management units Z901/Z902) if not used elsewhere

> **Important:** Once staff are assigned to Pay Group 90 or Company 90, deletion is blocked. Back-out at that stage would require reassigning or removing all staff first.
