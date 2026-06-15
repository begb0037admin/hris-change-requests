# Change Request — Colleges & Halls Org Hierarchy & Non-Payroll Company Set-Up (UOXU)

**Date:** 2026-06-15
**Drafted by:** Kevin Lelitte
**Status:** Draft

---

## 1. Details — What is changing?

A new non-payroll organisation structure will be created in PeopleXD (UOXU) for Colleges & Halls.

The change includes:

- Company 90 — Non-Payroll Colleges & Halls
- Pay Group 90 — ZZ Do Not Use Non-Pay
- Division 901 — Colleges & Halls
- USER_CODE1 (Subdivision) — ZSD901 — Colleges & Halls
- USER_CODE2 (Level 4) — Z90101 — Colleges & Halls
- Management Unit Z901 — Colleges & Halls
- Management Unit Z902 — Permanent Private Halls

Additional activities include loading Pay Admin by Code values using the HR Reference data migration template, linking hierarchy records within the portal, and granting HR access and Pay Group 90 access to authorised users.

Company 90 will be created from the existing Colleges & Halls company structure. Payroll-related fields, including tax, calendar and revenue settings, will remain blank as the company will not be used for payroll processing.

Division Code configuration remains dependent on confirmation of the Company Code / Division Code relationship by The Access Group.

---

## 2. Justification — Why is the change necessary?

Colleges & Halls staff require management within PeopleXD UOXU for organisational hierarchy, appointments and post management but are not paid through the University of Oxford payroll.

The current company structure does not support this population. A dedicated non-payroll company and pay group are therefore required to enable HR administration without introducing payroll processing requirements.

---

## 3. Related Changes — Are there dependent changes?

The following activities are dependent on this change:

- Confirmation of the Company Code / Division Code relationship by The Access Group.
- Loading of Pay Admin by Code values through the HR Reference data migration process.
- Creation of posts and assignment of staff following completion of the organisational hierarchy.

Post creation and staff assignment are outside the scope of this change request.

---

## 4. Impact on Dependent Services — What is the impact on connected or downstream services or components?

Once implemented, Colleges & Halls posts will be available within the organisational hierarchy and visible to authorised users.

Access to salary information will continue to be controlled through Pay Group security. Users without Pay Group 90 access will not be able to view salary information for Colleges & Halls staff, regardless of company-level HR access.

Any reporting or processes filtered by company may require review to ensure Company 90 is included where appropriate.

---

## 5. Impact — Specify downtime or at-risk period

No service outage is expected.

The change introduces new company, pay group and reference data records only. No existing staff records or live payroll data will be affected.

---

## 6. Impact — Effect of not applying the change

Colleges & Halls staff cannot be managed within PeopleXD UOXU.

Posts cannot be created for this population and HR visibility of Colleges & Halls staff will remain unavailable.

---

## 7. Risk Assessment — What are the risks to the services?

Pay Group 90 failed to appear following creation during the 12 June demonstration session. The root cause has not yet been identified and requires investigation by The Access Group.

No staff have been assigned to the pay group and the issue was identified immediately. Any incorrect configuration can be safely removed at this stage.

Configuration values may inadvertently be copied from the source company during creation of Company 90.

All copied configuration settings will be reviewed and non-applicable payroll-related values removed before implementation.

Users may be unable to view the new organisational structure if access is not configured correctly.

HR access and Pay Group access will be validated during testing prior to handover.

---

## 8. Potential Security Impact — What is it and how will it be tested?

Access to salary information will be controlled through Pay Group 90 security.

No payroll-sensitive data or credentials are being migrated.

Access permissions will be restricted to authorised users only.

Security testing will include:

- Verifying that users without Pay Group 90 access cannot view salary information.
- Verifying that users without Company 90 HR access cannot view Colleges & Halls posts or appointments.

---

## 9. Testing — Who will test it and how?

Kevin Lelitte / Simon Burford (HR Systems) will verify:

- Company 90 is available within the organisation structure.
- Pay Group 90 is available within Managed Payroll.
- Hierarchy records are linked correctly.
- HR access permissions function as expected.
- Pay Group access permissions function as expected.
- Salary tab visibility is controlled correctly through Pay Group security.

The Access Group will confirm resolution of the Pay Group 90 creation issue before final sign-off.

Backup Restore and Service Recovery testing are not required as this change introduces configuration records only and does not affect infrastructure, backup processes or recovery arrangements.

---

## 10. Implementation Plan — Who will implement it and how?

| Step | Owner | Status |
|---|---|---|
| 1. Investigate and resolve the Pay Group 90 creation issue | The Access Group | TODO |
| 2. Confirm the Company Code / Division Code relationship | The Access Group / Kevin Lelitte / Simon Burford | TODO |
| 3. Load Pay Admin by Code values using the HR Reference template | Kevin Lelitte / Simon Burford | TODO |
| 4. Build organisational hierarchy links within the portal | Kevin Lelitte / Simon Burford | TODO |
| 5. Grant HR access to authorised users | Kevin Lelitte / Simon Burford | TODO |
| 6. Grant Pay Group 90 access to authorised users | Kevin Lelitte / Simon Burford | TODO |
| 7. Complete testing and verification | Kevin Lelitte / Simon Burford | TODO |

---

## 11. Communications Plan — Who needs to know and how?

Michelle Williams (Comms) will be notified once the change is ready for implementation to coordinate any user-facing communications relating to Colleges & Halls staff visibility within PeopleXD.

---

## 12. Documentation — Does any documentation need to be updated?

Any internal administration documentation relating to organisational hierarchy management, company structures or security access may require updating following implementation.

The change does not affect the Service Relationship Model, Service Recovery Plan, Recovery Time Objective (RTO) or Recovery Point Objective (RPO).

---

## 13. Service Sponsor / Approver

Marie Cooksey — Head of HR Systems.

---

## 14. Back Out Plan — How will it be rolled back in the event of the change failing?

Provided no staff have been assigned, the change can be reversed by:

1. Deleting Pay Group 90.
2. Deleting Company 90.
3. Removing Division 901, USER_CODE1 ZSD901, USER_CODE2 Z90101 and Management Units Z901 and Z902.

Once staff have been assigned to Company 90 or Pay Group 90, those records must first be reassigned or removed before rollback can be completed.
