# Handover — Pay Code 121 (PAYPAY25) HR Report Suite Fix
**Date:** 18 June 2026
**Handed over by:** Kevin Lelitte (session ending)
**Picked up by:** Next session — read this in full before doing anything

---

## Hard Rules for This Work

- Do not reference AI, Claude, or any automated tooling in any document, comment, or communication produced as part of this work.
- Do not attempt Microsoft Graph API — Oxford blocks it entirely.
- All documentation must read as if produced by Kevin Lelitte.

---

## Background — What This Is About

Pay code 121 (PAYPAY25) is missing from the SQL query pay code filter in three HR Report Suite `.RDL` files. This means staff on pay code 121 are not appearing in those reports. Tracy identified the issue; Michael confirmed it is a SQL omission (the pay code exists in PeopleXD but is not in the hard-coded list in the reports). The fix is needed before the current month's payroll run.

The three affected report files are:
- **PERDEP01 Full Data Set**
- **PERDEP01 Full Data Set with Allowances**
- **PERDEP20 Approved Allowance Changes**

Each file contains an embedded dataset called **DataSet1** with a SQL query that includes an explicit `IN()` list of allowance pay codes. Pay code 121 must be added in the correct numeric sequence within that list.

---

## Key People

| Person | Role |
|---|---|
| Kevin Lelitte | HR Systems Manager/Director — owns this change |
| Tracy | Validates reports in TEST and signs off before LIVE promotion |
| Michael | Confirmed the issue is a SQL omission, not an Access Group problem |
| Marie Cooksey | Head of HR Systems — Business Owner / Approver on the CR |

---

## Key Technical Facts

| Item | Detail |
|---|---|
| Report file type | `.RDL` — opened and edited in Visual Studio |
| Dataset to edit | `DataSet1` — the embedded dataset in each `.RDL` file |
| SQL change | Add `121` to the pay code `IN()` list in correct numeric sequence |
| Version bump | Version 9.0 → Version 10.0 in all three files |
| Report Summary header | Must be updated in each file: Version → 10.0, Last updated → JUN 2026, Change ID → OSM number (see below) |
| SQL dialect | TSQL (Transact-SQL) — these `.RDL` files use TSQL, not Oracle PL/SQL |
| Environment pipeline | DEV → TEST → QA → LIVE |
| Deploy order | TEST first → Tracy validates → then LIVE |
| Network drive | `I:\OUIT\CoreHR Reports` — all solution files are here |
| Remote access | CONNECT Remote Services (RADC) — `remotedesktop.connect.ox.ac.uk` |
| Remote app | HRIS Reporting - Visual Studio 2017 (purple icon) |
| Remote server | `CON-RDBROKER03.CONNECT.OX.AC.UK` |
| Credentials | Oxford SSO (Kevin's Oxford username and password) |

---

## What Has Been Completed This Session

### 1. Change Request drafted and pushed to GitHub

A formal Change Request document has been drafted and pushed to this repository:

**File:** `CRs/CR-2026-06-18-pay-code-121-hr-report-suite.md`

The CR is in the correct 14-section PeopleXD format (confirmed against a real Colleges & Halls CR used as a reference). It covers all required sections including testing, implementation plan, security impact, and back-out plan.

**The CR template has also been updated** (`templates/change-request-template.md`) to match this correct format for future use.

### 2. Change Request submitted to PeopleXD OSM — PENDING

The CR was copied from the repository and is ready to be submitted to PeopleXD OSM (the Oxford Service Management system). At the point this session ended, it had not yet been submitted. Kevin needs to submit it and obtain the **Change ID (OSM number)**.

- **OSM Category:** Report
- **OSM Justification/Type:** Bug Fix

Once the Change ID is received, it must be added to the Report Summary header in each of the three `.RDL` files (see implementation steps below).

### 3. CONNECT Remote Services — accessed and ready

Kevin successfully connected to CONNECT Remote Services and opened **HRIS Reporting - Visual Studio 2017**. Visual Studio loaded successfully. The session ended at this point — no files have been opened or edited yet.

---

## Current State — Exactly Where We Are

- CR document: drafted, in GitHub, **not yet submitted to OSM**
- OSM Change ID: **not yet obtained**
- Visual Studio: **loaded and ready** via CONNECT Remote Services
- Solution file: **not yet opened**
- `.RDL` files: **not yet edited**
- TEST deployment: **not done**
- Tracy validation: **not done**
- LIVE deployment: **not done**

---

## What To Do Next — Full Step-by-Step

Work through these steps in order. Do not skip ahead.

---

### Step A — Submit the CR to OSM and get the Change ID

Before touching any code, submit the CR to PeopleXD OSM if not already done.

1. Open PeopleXD OSM
2. Raise a new Change Request
3. Category: **Report** — Justification/Type: **Bug Fix**
4. Copy the content from `CRs/CR-2026-06-18-pay-code-121-hr-report-suite.md` into the relevant fields
5. Submit and note the **Change ID** (OSM number) — you will need this for the Report Summary headers

---

### Step B — Open Visual Studio and load the solution

1. Connect to CONNECT Remote Services at `remotedesktop.connect.ox.ac.uk`
2. Click **HRIS Reporting - Visual Studio 2017** (purple icon)
3. Log in with Oxford SSO credentials when prompted
4. Once Visual Studio loads, go to **File → Open → Project/Solution**
5. Navigate to `I:\OUIT\CoreHR Reports`
6. Open the solution file (`.sln`) for the **TEST** environment
7. In Solution Explorer (left panel), locate the three report files listed above

---

### Step C — Edit each `.RDL` file

Repeat this process for all three files: PERDEP01 Full Data Set, PERDEP01 Full Data Set with Allowances, PERDEP20 Approved Allowance Changes.

For each file:

**1. Open the file in Visual Studio**
- Double-click it in Solution Explorer

**2. Open DataSet1**
- In the report design surface, find the dataset called `DataSet1`
- Right-click → Edit Query (or similar) to view the SQL

**3. Find the pay code IN() list**
- Look for a `WHERE` clause containing something like:
  ```sql
  AND pay_code IN (100, 105, 115, 125, 130 ...)
  ```
  (Exact column name and values will differ — look for a list of numeric pay codes)

**4. Add 121 in the correct numeric sequence**
- Insert `121` in the correct position within the list (in ascending numeric order)
- Example: if the list reads `115, 125` then it should become `115, 121, 125`
- Do not alter any other part of the SQL

**5. Test in the Preview pane**
- Run a preview to confirm the report returns results and no SQL errors appear
- If there is a syntax error, check for missing commas or misplaced brackets

**6. Update the Report Summary header**
- The Report Summary is a comment block near the top of the DataSet1 SQL, looking like:
  ```
  -- Name:         PERDEP01 Full Data Set
  -- Tab name:     ...
  -- Version:      9.0
  -- Last updated: [date]
  -- Change ID:    [number]
  ```
- Update:
  - `Version` → `10.0`
  - `Last updated` → `JUN 2026`
  - `Change ID` → the OSM number obtained in Step A

**7. Save the file**

---

### Step D — Deploy to TEST

Once all three files are saved and previewed without errors:

1. Follow the standard HR Reporting release and deployment process to deploy the Version 10.0 files to the **TEST environment**
2. Refer to `HOW TO - Manage Reports - Release and Deployment.docx` on the SharePoint knowledge base if needed (path: HR Knowledge Base → How To Guides → Reporting)

---

### Step E — Tracy validates in TEST

Notify Tracy that Version 10.0 is available in TEST. She needs to confirm:
- Pay code 121 (PAYPAY25) appears in all three reports
- No existing pay codes are missing
- Report formatting is unchanged

Do not proceed to LIVE until Tracy confirms.

---

### Step F — Deploy to LIVE

Once Tracy has signed off TEST:

1. Open the **LIVE solution** in Visual Studio (also at `I:\OUIT\CoreHR Reports` — separate solution file)
2. Add the three Version 10.0 `.RDL` files from the TEST solution using **Add → Existing Item**
3. Deploy to LIVE
4. Move the files to the correct LIVE folder hierarchy
5. Remove/retire the Version 9.0 files
6. Ask Tracy to confirm LIVE output is correct

---

### Step G — Close out

1. Update `CRs/CR-2026-06-18-pay-code-121-hr-report-suite.md` — change Status from `Draft` to `Complete` and add the OSM number if not already in the file
2. Update this HANDOVER.md to reflect that the work is done
3. Notify Marie Cooksey if required under the CR

---

## Back-Out Plan (if something goes wrong)

The Version 9.0 `.RDL` files remain untouched in the TEST/QA solution throughout this process. If Version 10.0 causes a problem in LIVE:

1. Open the LIVE solution in Visual Studio
2. Add the Version 9.0 files from the TEST or QA solution using **Add → Existing Item**
3. Deploy Version 9.0 back to LIVE
4. Confirm with Tracy that LIVE has been restored
5. Raise a follow-up investigation before re-attempting the fix

Rollback takes approximately 15–30 minutes. No data is changed by this CR — rollback does not result in data loss.

---

## Reference — CR Document

Full CR is at: `CRs/CR-2026-06-18-pay-code-121-hr-report-suite.md`

Do not re-draft the CR. Do not create a duplicate. Use the existing file.
