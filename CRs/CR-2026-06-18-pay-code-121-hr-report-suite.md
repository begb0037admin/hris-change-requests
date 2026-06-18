# Change Request — Add Pay Code 121 (PAYPAY25) to HR Report Suite SQL

**Date:** 2026-06-18
**Drafted by:** Kevin Lelitte
**Status:** Draft

---

## 1. Details — What is changing?

Pay code 121 (PAYPAY25) will be added to the SQL query pay code filter in three .RDL report files within the HR Reporting suite.

The affected files are:

- PERDEP01 Full Data Set
- PERDEP01 Full Data Set with Allowances
- PERDEP20 Approved Allowance Changes

Each file contains an embedded dataset (DataSet1) with a SQL query that includes an explicit list of allowance pay codes. Pay code 121 is currently absent from this list and will be added in the correct sequential position.

All three files will be incremented from Version 9.0 to Version 10.0. Report Summary headers (Name, Tab name, Version, Last updated, Change ID) will be updated in each file.

The change will be applied in the HR Reporting TEST environment first, validated by Tracy, then promoted to HR Reporting LIVE.

---

## 2. Justification — Why is the change necessary?

Pay code 121 (PAYPAY25) is not appearing in the HR report suite output. This was identified and reported by Tracy and confirmed by Michael as a SQL omission rather than an Access Group configuration issue. The pay code exists in PeopleXD but is excluded from the hard-coded pay code list in the affected reports.

The fix is required ahead of the current month's payroll run.

---

## 3. Related Changes — Are there dependent changes?

None. This is a standalone SQL change to three .RDL files. No changes to data sources, shared datasets, parameters, or the HR Reporting environment configuration are required.

---

## 4. Impact on dependent services — What is the impact on connected or downstream services or components?

Once deployed to LIVE, pay code 121 data will appear in PERDEP01 Full Data Set, PERDEP01 Full Data Set with Allowances, and PERDEP20 Approved Allowance Changes for any user running those reports.

No other reports or downstream systems are expected to be affected. Any additional reports that filter on pay codes should be reviewed in future to confirm pay code 121 is included where appropriate.

---

## 5. Impact — Specify downtime or at-risk period

No service outage is expected.

The existing Version 9.0 reports will remain live and accessible throughout. Version 10.0 files will be deployed to the LIVE environment's staging folder and will only become publicly accessible once moved to the correct folder hierarchy following successful testing.

---

## 6. Impact — Effect of not applying the change

Pay code 121 (PAYPAY25) will continue to be excluded from the HR report suite output. Staff on this pay code will not appear in PERDEP01 or PERDEP20 reports, resulting in inaccurate headcount and allowance data. This will affect the accuracy of payroll reporting for the current month.

---

## 7. Risk Assessment — What are the risks to the services?

The change is limited to adding a single value to a hard-coded list within three SQL queries. The risk of unintended side effects is low.

The primary risk is that the SQL edit introduces a syntax error. This will be identified immediately during the Preview pane test in Visual Studio before deployment. The change will not be deployed if the Preview pane does not return correct results.

A second risk is that additional report suites beyond the three identified also contain pay code filters that exclude 121. Tracy's testing will cover the known reports; any further omissions should be flagged as a separate change request.

---

## 8. What is the potential security impact of the change? How will the security impact be tested?

This change adds a pay code value to existing SQL queries. It does not alter data source connections, user permissions, pay group security, or access controls.

Staff on pay code 121 will become visible in reports to any user who already has access to PERDEP01 and PERDEP20. This is the intended outcome. No new access permissions are being granted.

Security testing will include:

- Verifying that existing report access controls remain unchanged post-deployment.
- Verifying that no additional users have gained access to reports as a result of the change.

---

## 9. Testing (Functional / Non-Functional) — Who will test it and how? Does Backup Restore / Service Recovery need to be re-tested?

Tracy will test the change in the HR Reporting TEST environment once Version 10.0 has been deployed there.

Tracy will verify:

- Pay code 121 (PAYPAY25) appears in the output of PERDEP01 Full Data Set.
- Pay code 121 appears in the output of PERDEP01 Full Data Set with Allowances.
- Pay code 121 appears in the output of PERDEP20 Approved Allowance Changes.
- No existing pay codes are missing from the output.
- Report formatting is unchanged.

Promotion to LIVE will only proceed once Tracy has confirmed all criteria are met.

Backup Restore and Service Recovery testing are not required as this change modifies SQL query code only and does not affect infrastructure, backup processes or recovery arrangements.

---

## 10. Implementation Plan — Who will implement it and how?

1. Kevin Lelitte will open the HR Reporting TEST solution in Visual Studio.

2. Kevin Lelitte will copy PERDEP01 Full Data Set to Version 10.0, add pay code 121 to DataSet1, and update the Report Summary header.

3. Kevin Lelitte will copy PERDEP01 Full Data Set with Allowances to Version 10.0, add pay code 121 to DataSet1, and update the Report Summary header.

4. Kevin Lelitte will copy PERDEP20 Approved Allowance Changes to Version 10.0, add pay code 121 to DataSet1, and update the Report Summary header.

5. Kevin Lelitte will enter credentials and deploy all three Version 10.0 files to HR Reporting TEST.

6. Tracy will validate the output in the TEST environment.

7. Kevin Lelitte will open the HR Reporting LIVE solution, add the Version 10.0 files from TEST, and deploy to LIVE.

8. Kevin Lelitte will move the deployed files to the correct LIVE folder hierarchy and delete Version 9.0.

9. Tracy and Kevin Lelitte will confirm the LIVE output is correct.

---

## 11. Communications Plan — Who needs to know and how?

No user-facing communication is required. The change corrects an omission in existing reports; users will see pay code 121 data appear as expected.

Tracy should be notified once Version 10.0 is available in TEST so she can schedule her validation check.

---

## 12. Does any documentation need to be updated? Will it affect the Service Relationship Model or Service Recovery Plan (RTO/RPO)?

The Report Summary header within each affected .RDL file will be updated as part of this change. No external documentation updates are required.

The change does not affect the Service Relationship Model, Service Recovery Plan, Recovery Time Objective (RTO) or Recovery Point Objective (RPO).

---

## 13. Service Sponsor / Approver — Who needs to approve this change?

Marie Cooksey — Head of HR Systems.

---

## 14. Back Out Plan — How will it be rolled back in the event of the change failing?

The Version 9.0 .RDL files remain in the HR Reporting QA solution and in the TEST environment throughout the process. If Version 10.0 fails in LIVE:

1. Open the HR Reporting LIVE solution in Visual Studio.

2. Add the Version 9.0 file(s) from the TEST or QA solution using Add > Existing Item.

3. Deploy the Version 9.0 file(s) to LIVE.

4. Move the restored file(s) to the correct folder hierarchy in LIVE.

5. Delete the Version 10.0 file(s).

Rollback can be completed within approximately 15-30 minutes.
