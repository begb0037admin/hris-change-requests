# Change Request — Org Hierarchy Migration: Enable 16 COREPORTAL_ADMIN Menu Options

**Date:** 2026-06-16
**Drafted by:** Kevin Lelitte
**Status:** Draft — pending Kevin review and OSM submission

---

## 1. Details — What is changing?

16 menu options will be enabled against the `COREPORTAL_ADMIN` menu profile in PeopleXD to grant access to maintain the organisational hierarchy in the Portal.

The menu options to be enabled are:

| Menu Option | Menu ID | System |
|-------------|---------|--------|
| Show Org Hierarchy | `MAIN_MENU.SHOW_HIERARCHY` | CorePortal (COCP) |
| Org | `MAIN_MENU.WS_ORG` | Web Services (WS) |
| Get hierarchy levels | `WS_ORG_MENU.GET_HIERARCHY_LEVELS_STRUCTURECODE` | Web Services (WS) |
| Get hierarchy businessunits | `WS_ORG_MENU.GET_HIERARCHY_BUSINESSUNITS` | Web Services (WS) |
| Get hierarchy items | `WS_ORG_MENU.GET_HIERARCHY_ITEMS_STRUCTURECODE_REFTYPE` | Web Services (WS) |
| Update hierarchy businessunits | `WS_ORG_MENU.PATCH_HIERARCHY_BUSINESSUNITS` | Web Services (WS) |
| Delete hierarchy businessunits | `WS_ORG_MENU.DELETE_HIERARCHY_BUSINESSUNITS` | Web Services (WS) |
| POST MANAGEMENT | `PEOPLE_MANAGEMENT_MENU.POST_MANAGEMENT` | People Management (CPPM) |
| POST MANAGEMENT PARAMETERS | `POST_MANAGEMENT_MENU.POST_MANAGEMENT_PARAMETERS` | People Management (CPPM) |
| POST APPOINTMENT MAINTENANCE | `POST_MANAGEMENT_MENU.POST_APPOINTMENT_MAINTENANCE` | People Management (CPPM) |
| POST PROFILE MAINTENANCE | `POST_MANAGEMENT_MENU.POST_PROFILE_MAINTENANCE` | People Management (CPPM) |
| Post Profile Sanction History | `POST_MANAGEMENT_MENU.POST_PROFILE_SANCTION_HISTORY` | People Management (CPPM) |
| POST RESTRUCTURING | `POST_MANAGEMENT_MENU.POST_RESTRUCTURING` | People Management (CPPM) |
| STRUCTURE SETUP | `POST_MANAGEMENT_MENU.STRUCTURE_SETUP` | People Management (CPPM) |
| TERMS AND CONDITIONS | `POST_MANAGEMENT_MENU.TERMS_AND_CONDITIONS` | People Management (CPPM) |
| VIEW POST APPOINTMENTS | `POST_MANAGEMENT_MENU.VIEW_POST_APPOINTMENTS` | People Management (CPPM) |

The change will be applied across all environments: DEV, TEST, QA, and LIVE.

Source: Asta Palmer, email 15 June 2026, attachment `COREPORTAL_ADMIN.xlsx`.

---

## 2. Justification — Why is the change necessary?

As part of the Back Office to Portal migration of organisational hierarchy management, the ability to view and maintain the org hierarchy must be accessible via the Portal. Helen (HR Systems) previously migrated the management of the organisational structure from Back Office into the Portal; however, the corresponding menu options were not enabled on the `COREPORTAL_ADMIN` profile at that time.

The 16 menu options are required to:
- Display and navigate the org hierarchy within the Portal (`Show Org Hierarchy`)
- Support the Web Services API calls that underpin Portal hierarchy operations
- Enable post management, post appointment maintenance, and related administration functions within People Management

This change is a dependency for the DTP1092 College Staff into PeopleXD project. Without these menu options enabled, the org hierarchy for Colleges & Halls cannot be administered via the Portal once the hierarchy structure has been built.

---

## 3. Related Changes — Are there dependent changes?

This change is directly linked to:

- **CR-2026-06-15-colleges-halls-org-hierarchy-setup** — Colleges & Halls org hierarchy and non-payroll company set-up in UOXU. That CR must be in progress or complete before the menu options will be meaningfully usable.
- **DTP1092 College Staff into PeopleXD** — the broader project this change supports.
- **FP 68261303 Multi Company Setup** — Access Group functional project covering the company and division code configuration.

---

## 4. Impact on Dependent Services — What is the impact on connected or downstream services?

Enabling these menu options makes existing Portal functionality accessible to `COREPORTAL_ADMIN` users. No new functionality is being introduced.

- Users with `COREPORTAL_ADMIN` access will gain the ability to view and maintain the org hierarchy, manage posts, and administer post appointments via the Portal.
- No integrations, reports, or downstream systems are affected by a menu profile change.
- Users without `COREPORTAL_ADMIN` access are unaffected.

---

## 5. Impact — Specify downtime or at-risk period

No service outage or at-risk period is expected. Menu profile configuration changes take effect immediately upon saving and do not require a system restart or scheduled maintenance window.

---

## 6. Impact — Effect of not applying the change

Without these menu options enabled, `COREPORTAL_ADMIN` users will be unable to:
- View or navigate the org hierarchy in the Portal
- Administer posts and post appointments via the Portal
- Support the Colleges & Halls hierarchy administration required by DTP1092

The org hierarchy migration from Back Office to Portal cannot proceed and the DTP1092 project will be blocked at the hierarchy administration stage.

---

## 7. Risk Assessment — What are the risks to the services?

| Risk | Likelihood | Severity | Mitigation |
|------|------------|----------|------------|
| Incorrect menu options enabled, granting unintended access | Low | Low | Options confirmed by Asta Palmer via comparison against the required profile (COREPORTAL_ADMIN.xlsx, 15 Jun 2026). Changes will be verified in each environment. |
| Menu options enabled in LIVE before testing in lower environments | Low | Medium | Implementation plan requires DEV → TEST → QA → LIVE sequence with verification at each stage. |
| Options enabled for wrong profile | Low | Low | Profile name (`COREPORTAL_ADMIN`) confirmed in source data. |

Overall risk is low. This is a menu profile configuration change only — no data, payroll records, or integrations are affected.

---

## 8. Testing — Who will test it and how?

Kevin Lelitte / Asta Palmer (HR Systems) will verify in each environment:

- `Show Org Hierarchy` is visible and navigable for a `COREPORTAL_ADMIN` user
- Post Management, Post Appointment Maintenance, and Post Profile Maintenance options are accessible
- Web Services org options are available as expected
- No unintended menu options have been added or removed
- Users without `COREPORTAL_ADMIN` access are unaffected

Reference: *PeopleXD People Management — Maintain the Organisational Hierarchy v1 (Mar 2024)*, HR FA Knowledge Base.

---

## 9. Implementation Plan — Who will implement it and how?

| Step | Action | Owner | Status |
|------|--------|-------|--------|
| 1 | Enable 16 menu options on `COREPORTAL_ADMIN` in DEV | Asta Palmer | TODO |
| 2 | Verify DEV — confirm all 16 options present and accessible | Kevin Lelitte / Asta Palmer | TODO |
| 3 | Enable 16 menu options on `COREPORTAL_ADMIN` in TEST | Asta Palmer | TODO |
| 4 | Verify TEST | Kevin Lelitte / Asta Palmer | TODO |
| 5 | Enable 16 menu options on `COREPORTAL_ADMIN` in QA | Asta Palmer | TODO |
| 6 | Verify QA | Kevin Lelitte / Asta Palmer | TODO |
| 7 | Enable 16 menu options on `COREPORTAL_ADMIN` in LIVE | Asta Palmer | TODO |
| 8 | Verify LIVE and sign off | Kevin Lelitte | TODO |

Asta Palmer has confirmed she normally receives an OSM task from the change request to complete this work. Kevin Lelitte to raise the OSM CR and assign the task to Asta once approved.

---

## 10. Communications Plan — Who needs to know and how?

This is an internal configuration change. No user-facing communications are required.

Simon Burford (HR Systems Analysis and Insights Manager) and Michael O’Sullivan are copied on the originating email and are aware of this change.

---

## 11. Business Owner / Approver

Marie Cooksey — Head of HR Systems.

---

## 12. What is the potential security impact of the change?

The change grants additional menu access to users already holding the `COREPORTAL_ADMIN` profile. No new users are being granted access; no salary, payroll, or personal data access is being changed.

The `COREPORTAL_ADMIN` profile is a controlled, administrator-level profile. Access to this profile is managed separately and is not affected by this CR.

---

## 13. How will the security impact of the change be tested?

- Confirm that only users with `COREPORTAL_ADMIN` access can see the newly enabled menu options
- Confirm that users on other profiles (e.g. standard employee self-service) cannot access the org hierarchy administration options
- Confirm that no salary or payroll data is exposed through the newly enabled menu options

---

## 14. Back Out Plan — How will it be backed out in the event of the change failing?

Rollback is straightforward: disable the 16 menu options on the `COREPORTAL_ADMIN` profile, restoring the profile to its prior state.

No data changes are made by this CR. Rollback can be completed immediately by Asta Palmer without any data loss or service impact.

| Step | Action | Owner |
|------|--------|-------|
| 1 | Disable the 16 menu options on `COREPORTAL_ADMIN` in the affected environment(s) | Asta Palmer |
| 2 | Verify the profile has been restored to its prior state | Kevin Lelitte |
