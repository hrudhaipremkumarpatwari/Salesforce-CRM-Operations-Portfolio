> **Version 2 — enhanced practical edition.** This is a separate revision; Version 1 remains unchanged. Prepared 2026-11-01.

# Week 6 — Performance Evaluation and Continuous-Improvement Report (Version 2)

**Portfolio:** Salesforce CRM Operations Learning Portfolio  
**Business scenario:** Cedarline Office Products (fictional)  
**Report type:** KPI framework, synthetic trend analysis, dashboard design, and improvement plan  
**Author:** Hrudhai Prem Kumar Patwari

> **Evidence and simulation disclosure:** All records and KPI values in this report are synthetic training data. They are not Salesforce telemetry, actual business results, customer outcomes, or evidence of a live implementation. No live Salesforce org or dashboard was accessed or configured. Week 6 evaluator comments/scores were not supplied; this report therefore addresses the stated performance-evaluation requirements without inventing evaluator feedback.

## 1. Executive summary

This report evaluates a six-week fictional CRM operations dataset for Cedarline Office Products. It defines five operational KPIs covering lead assignment, case service levels, record completeness, duplicate records, and user training. Transparent formulas are applied to the supplied synthetic dataset, and the Week 1 and Week 6 values are compared.

The simulated dataset shows improving percentages across all five selected measures. These trends are useful for demonstrating KPI calculation, dashboard communication, and continuous-improvement thinking. They must not be interpreted as proof that a real intervention caused improvement. A real evaluation would require an agreed baseline, verified Salesforce reports, consistent definitions, controlled filters, and process-owner review.

## 2. Business context and evaluation objectives

The fictional Cedarline scenario uses CRM to coordinate sales enquiries, customer service cases, and operational data quality. Performance evaluation should help process owners understand whether records are routed promptly, service cases meet defined commitments, CRM data is usable, duplicate creation is controlled, and users complete required learning.

Objectives:
- Define measurable KPIs with clear numerators and denominators.
- Calculate each KPI consistently across six periods.
- Compare the first and final periods and interpret the direction of change.
- Specify a dashboard that supports operational review.
- Recommend a continuous-improvement cycle with ownership and controls.
- Document assumptions and limitations so synthetic analysis is not mistaken for production evidence.

## 3. KPI framework and formulas

| KPI | Formula | Desired direction | Proposed owner |
|---|---|---|---|
| Lead assignment timeliness | Leads assigned within 30 minutes ÷ Leads received × 100 | Higher | Sales Operations |
| Case SLA attainment | Cases closed within SLA ÷ Cases closed × 100 | Higher | Service Operations |
| Record completeness | Complete records ÷ Records audited × 100 | Higher | CRM Data Steward |
| Duplicate rate | Duplicate records ÷ Records audited × 100 | Lower | CRM Data Steward |
| Training completion | Users completed ÷ Training users × 100 | Higher | Training Lead |

**Definition controls:**
- “Within 30 minutes” must use a defined timestamp pair, time zone, business calendar, and treatment of records created outside business hours.
- Case SLA attainment should use the agreed SLA clock and case population. The supplied dataset uses cases closed in each week as the denominator.
- Completeness requires a documented list of mandatory fields and a consistent audit method.
- Duplicate rate is expressed against records audited in this dataset. A real organization may instead choose duplicate records ÷ total records reviewed or a confirmed duplicate-pair measure; the definition must remain consistent.
- Training completion is completed learners ÷ assigned learners for the same cohort and reporting period.

## 4. Dataset overview

The source file is `Week6_Simulated_KPI_Dataset.csv`. It contains six weekly rows and the following count fields:

- Leads received and leads assigned within 30 minutes.
- Cases closed and cases closed within SLA.
- Records audited, complete records, and duplicate records.
- Training users and training completions.

The dataset is intentionally small and synthetic. It is designed to exercise percentage calculations and trend interpretation, not to reproduce a real CRM data extract.

## 5. KPI calculations and results

### 5.1 Week 1 and Week 6 comparison

| KPI | Week 1 calculation | Week 1 | Week 6 calculation | Week 6 | Change |
|---|---|---:|---|---:|---:|
| Lead assignment timeliness | 84 ÷ 120 × 100 | 70.0% | 145 ÷ 158 × 100 | 91.8% | +21.8 pp |
| Case SLA attainment | 68 ÷ 90 × 100 | 75.6% | 108 ÷ 116 × 100 | 93.1% | +17.5 pp |
| Record completeness | 78 ÷ 100 × 100 | 78.0% | 95 ÷ 100 × 100 | 95.0% | +17.0 pp |
| Duplicate rate | 9 ÷ 100 × 100 | 9.0% | 3 ÷ 100 × 100 | 3.0% | -6.0 pp |
| Training completion | 17 ÷ 25 × 100 | 68.0% | 25 ÷ 25 × 100 | 100.0% | +32.0 pp |

*pp = percentage points. Percentage-point change is the difference between two percentages, not the relative percentage increase.*

### 5.2 Six-week trend table

| Week | Lead assignment | Case SLA | Completeness | Duplicate rate | Training completion |
|---:|---:|---:|---:|---:|---:|
| 1 | 70.0% | 75.6% | 78.0% | 9.0% | 68.0% |
| 2 | 75.0% | 79.8% | 82.0% | 8.0% | 76.0% |
| 3 | 80.0% | 83.7% | 86.0% | 6.0% | 84.0% |
| 4 | 85.2% | 87.6% | 90.0% | 5.0% | 92.0% |
| 5 | 88.0% | 90.0% | 93.0% | 4.0% | 96.0% |
| 6 | 91.8% | 93.1% | 95.0% | 3.0% | 100.0% |

### 5.3 Interpretation

**Lead assignment timeliness:** The synthetic percentage rises from 70.0% to 91.8%. Lead volume also increases from 120 to 158 per week, while timely assignments increase from 84 to 145. In a real environment, the owner should segment results by lead source, region, queue, business hours, and missing routing data to identify where delays occur.

**Case SLA attainment:** The synthetic result rises from 75.6% to 93.1%. The number of cases closed also rises from 90 to 116. A real analysis should segment by severity, queue, case age, reopen status, and SLA pause rules so that changes in case mix do not distort interpretation.

**Record completeness:** Completeness increases from 78.0% to 95.0%, with 100 records audited each week. A real data-quality review should confirm which fields are mandatory, whether the sample is representative, and whether records are scored consistently.

**Duplicate rate:** The rate falls from 9.0% to 3.0%. A real review should distinguish confirmed duplicates from possible matches and document the matching criteria. A low rate is not meaningful if duplicate detection is incomplete.

**Training completion:** Completion rises from 68.0% to 100.0% of a cohort of 25. A real training evaluation should also measure knowledge retention and task accuracy, not attendance or completion alone.

**Overall:** All five simulated trends move in the desired direction. Because the dataset contains no intervention dates, control group, or operational context, it cannot establish causation. The correct conclusion is that the dataset demonstrates how an improvement trend could be reported, not that automation or training caused the trend.

## 6. Proposed dashboard design

The companion file `Week6_Dashboard_Specification.md` provides the dashboard layout.

### KPI cards
Show current-period value, agreed target, prior-period comparison, and a clear status definition for:
- Lead assignment timeliness.
- Case SLA attainment.
- Record completeness.
- Duplicate rate.
- Training completion.

### Charts
1. Weekly line chart for lead assignment timeliness.
2. Weekly line chart for case SLA attainment.
3. Weekly line chart for record completeness and duplicate rate, using clearly labelled scales.
4. Weekly column chart for training completion.
5. Exception table listing KPI, target, actual, variance, owner, and proposed action.

### Filters and drill-downs
Where source data supports them, include reporting period, lead source, region, case priority/severity, queue/team, and training role. Do not show a filter that is not backed by the available data. The supplied synthetic dataset does not include all these dimensions, so the filters are dashboard design recommendations rather than implemented capabilities.

### Dashboard governance
Define metric owners, refresh cadence, data access, filter defaults, and the treatment of missing values. A dashboard should show the reporting period and last refresh time. Users should be able to trace KPI values back to a documented report definition.

## 7. Proposed targets and threshold handling

The project uses the following illustrative planning thresholds:

| KPI | Proposed threshold |
|---|---:|
| Lead assignment timeliness | ≥90% |
| Case SLA attainment | ≥90% |
| Record completeness | ≥95% |
| Duplicate rate | ≤3% |
| Training completion | ≥95% |

These are training assumptions, not industry benchmarks or approved Cedarline service commitments. Business owners must validate targets against customer expectations, capacity, policy, and baseline performance.

A threshold breach should trigger investigation rather than automatic blame. Review data freshness, denominator changes, case mix, business calendars, queue staffing, and process exceptions before deciding on corrective action.

## 8. Continuous-improvement plan

Use a structured Plan–Do–Check–Act cycle:

1. **Baseline:** Agree definitions, data sources, owners, time windows, filters, and baseline period.
2. **Diagnose:** Segment missed targets by queue, lead source, region, case severity, missing fields, and user role where data is available.
3. **Prioritize:** Rank causes by business impact, frequency, and effort to resolve.
4. **Plan:** Select a limited intervention with a clear owner, expected effect, risks, and acceptance criteria.
5. **Do:** Pilot the change in an authorized non-production environment or controlled business process.
6. **Check:** Compare pre/post results using the same formulas and reporting rules; review sample records and exceptions.
7. **Act:** Standardize effective changes, revise ineffective changes, or stop interventions that create adverse outcomes.
8. **Control:** Review operational exceptions weekly and KPI trends monthly; maintain change history and process documentation.

### Example improvement actions

| KPI issue | Diagnostic questions | Proposed action | Validation |
|---|---|---|---|
| Late lead assignment | Which source/region/queue has the longest delay? Are fields missing? | Clarify routing ownership; review proposed automation and staffing | Compare assignment timestamps and exception rates |
| Missed case SLA | Which severity or queue drives misses? Are cases waiting for customer input? | Review escalation rules, queue coverage, and aging work | Compare SLA attainment and overdue backlog |
| Incomplete records | Which required fields are most often blank? Is guidance clear? | Improve field guidance and role-based training | Re-audit a consistent sample |
| Duplicate records | At what entry point do duplicates occur? Are search steps followed? | Improve search-before-create guidance and duplicate review | Track confirmed duplicate rate |
| Low training completion | Which roles or cohorts are behind? Is content accessible? | Provide targeted sessions and manager follow-up | Track completion plus knowledge-check scores |

## 9. Data quality and analytical limitations

The following limitations apply:
- Only six synthetic weekly observations are available.
- No record-level data, timestamps, queue dimensions, or case severity breakdown is supplied.
- The dataset has fixed audit and training cohort denominators, which simplifies comparison.
- The same record could potentially be represented in multiple weekly operational counts; no unique-record lineage is provided.
- There is no control group or intervention log.
- No seasonality, holidays, staffing changes, or business-hour calendar is represented.
- The case SLA denominator is cases closed, not all cases received or all open cases.
- The duplicate-rate denominator is records audited, not necessarily all records created.

For these reasons, the analysis is descriptive and illustrative. It should not be used to forecast real performance or to make personnel decisions.

## 10. Roles and review cadence

| Role | Responsibility | Suggested cadence |
|---|---|---|
| Sales Operations owner | Review lead assignment and exception trends | Weekly |
| Service Operations owner | Review SLA attainment and overdue cases | Weekly |
| CRM Data Steward | Review completeness and duplicate trends | Weekly/monthly |
| Training Lead | Review completion and knowledge gaps | Per cohort/monthly |
| CRM/Platform owner | Validate data definitions, dashboard access, and approved changes | Monthly/release-based |
| Business sponsor | Review outcomes, risks, and priorities | Monthly |

## 11. Recommendations and next steps

1. Obtain process-owner approval for KPI definitions and target thresholds.
2. Confirm source reports, field definitions, time zones, and reporting calendars in an authorized Salesforce environment.
3. Establish a representative baseline before introducing changes.
4. Build the dashboard only after validating the source reports and access model.
5. Assign owners to each KPI and exception category.
6. Pilot one improvement at a time and document the change.
7. Review unintended effects, such as faster routing but higher reassignment or improved completeness but increased user effort.
8. Retain evidence of data definitions, approvals, test results, and review decisions.

## 12. Conclusion

Performance evaluation is useful only when the measures are defined consistently, the source data is trustworthy, and the results lead to responsible action. The synthetic Cedarline dataset demonstrates calculations and trend reporting across five CRM operations KPIs. The proposed dashboard and improvement cycle provide a structured approach for a future authorized implementation, while the evidence disclosure prevents simulated values from being mistaken for real Salesforce performance.

## Appendix — Related repository artefacts

- [Synthetic six-week KPI dataset](Week6_Simulated_KPI_Dataset.csv)
- [KPI definitions and improvement plan](Week6_KPI_Definitions_and_Improvement_Plan.md)
- [Dashboard specification](Week6_Dashboard_Specification.md)
- [Original report (DOCX)](Week6_Performance_Evaluation_and_Improvement.docx)

---
**Disclosure:** Synthetic dataset and illustrative analysis only; no live Salesforce telemetry, dashboard, or implemented improvement is represented.



## Version 2 practical measurement and dashboard supplement

This supplement makes the KPI framework more operational by mapping each metric to a source-report design, validation checks, and a reproducible calculation. All values remain synthetic.

### A. KPI-to-source-report mapping

| KPI | Required source population | Required fields / dimensions | Calculation check | Common data risk |
|---|---|---|---|---|
| Lead assignment timeliness | Eligible leads created in the reporting week | Lead ID, CreatedDate, owner-assigned timestamp, source, region, queue, eligibility flag | Count eligible leads assigned within 30 elapsed minutes ÷ eligible leads | Timestamp timezone mismatch; excluding unassigned leads from denominator |
| Case SLA attainment | Cases closed in the reporting week under the selected SLA policy | Case ID, closed timestamp, SLA target, SLA met flag, severity, queue, pause status | Cases meeting SLA ÷ eligible closed cases | Mixing open and closed cases; inconsistent pause rules |
| Record completeness | Records included in a defined audit sample | Record ID, audit date, mandatory-field pass/fail, object type | Records passing all mandatory checks ÷ records audited | Changing mandatory-field list or sample method |
| Duplicate rate | Records audited under a documented matching policy | Record ID, confirmed-duplicate flag, match-rule ID, review status | Confirmed duplicate records ÷ records audited | Counting possible matches as confirmed duplicates |
| Training completion | Users assigned to the same training cohort | User/cohort ID, assigned status, completion status, completion date | Completed assigned users ÷ assigned users | Denominator changes mid-period; counting optional learners inconsistently |

**Important:** These are report requirements, not claims that the reports exist in a live Salesforce org. A Salesforce admin/reporting owner must map the logical fields to the actual org schema and confirm access.

### B. Reproducible calculations using the supplied synthetic data

Example Week 6 calculations:
- Lead assignment: 145 ÷ 158 × 100 = **91.8%**.
- Case SLA: 108 ÷ 116 × 100 = **93.1%**.
- Record completeness: 95 ÷ 100 × 100 = **95.0%**.
- Duplicate rate: 3 ÷ 100 × 100 = **3.0%**.
- Training completion: 25 ÷ 25 × 100 = **100.0%**.

Example spreadsheet formulas, assuming Week 6 is row 7 and columns follow the CSV header:
- Lead assignment: `=C7/B7`
- Case SLA: `=E7/D7`
- Completeness: `=G7/F7`
- Duplicate rate: `=H7/F7`
- Training completion: `=J7/I7`

Format each result as a percentage with one decimal place. Keep numerator and denominator visible beside the percentage so a reviewer can reproduce the result.

### C. Data validation and reconciliation checklist

Before publishing a real KPI:
1. Confirm the reporting week boundaries and time zone.
2. Confirm inclusion/exclusion rules and whether the denominator is eligible records, all records, or closed records.
3. Check for null timestamps, missing status values, duplicate IDs, and records outside the reporting window.
4. Reconcile the report row count to a second authorized source or sampled record list.
5. Recalculate the KPI independently from numerator and denominator counts.
6. Compare with the prior period using identical filters and definitions.
7. Document any data correction, backfill, or definition change.
8. Obtain metric-owner approval before publishing.

**Example reconciliation test:** If a weekly lead report shows 158 eligible leads but the underlying detail export contains 156 unique Lead IDs, do not publish 91.8% until the two-record difference is explained. Check duplicate rows, filters, time boundaries, and eligibility criteria first.

### D. Dashboard wireframe and visual rules

**Top row — KPI cards**
- Lead assignment within 30 minutes: 91.8% (synthetic Week 6).
- Case SLA attainment: 93.1% (synthetic Week 6).
- Record completeness: 95.0% (synthetic Week 6).
- Duplicate rate: 3.0% (synthetic Week 6).
- Training completion: 100.0% (synthetic Week 6).

Each card should show: current period, numerator/denominator, agreed target, prior-period change, owner, and last refresh timestamp. Do not show red/green status until the business has approved thresholds.

**Middle row — trend charts**
1. Line chart: weekly lead assignment timeliness.
2. Line chart: weekly case SLA attainment.
3. Two clearly labelled trend lines or separate charts: record completeness and duplicate rate. If using one shared axis, ensure the scale does not make one series unreadable.
4. Column chart: weekly training completion.

**Bottom row — operational exception table**
Columns: KPI, current result, target, variance, affected segment, owner, next action, due date. Drill-downs should be enabled only when the source report contains the relevant dimensions.

### E. Six-week dashboard data (derived from the synthetic source)

| Week | Lead assignment | Case SLA | Completeness | Duplicate rate | Training |
|---:|---:|---:|---:|---:|---:|
| 1 | 70.0% | 75.6% | 78.0% | 9.0% | 68.0% |
| 2 | 75.0% | 79.8% | 82.0% | 8.0% | 76.0% |
| 3 | 80.0% | 83.7% | 86.0% | 6.0% | 84.0% |
| 4 | 85.2% | 87.6% | 90.0% | 5.0% | 92.0% |
| 5 | 88.0% | 90.0% | 93.0% | 4.0% | 96.0% |
| 6 | 91.8% | 93.1% | 95.0% | 3.0% | 100.0% |

### F. Metric governance and change control

- Assign one accountable owner and one technical/report owner per KPI.
- Version metric definitions; record effective dates when formulas or populations change.
- Do not compare periods across a definition change without restating prior periods or clearly flagging the break.
- Publish the reporting window, refresh timestamp, filters, and known data-quality caveats.
- Review exceptions weekly; review definitions, targets, and trends monthly.
- Do not use these synthetic measures for employee performance decisions or operational forecasts.

**Version 2 boundary:** The additional report mapping, formulas, wireframe, and validation steps are proposed portfolio artefacts. The dashboard is not built, the source reports are not connected, and no live Salesforce metrics have been retrieved.
