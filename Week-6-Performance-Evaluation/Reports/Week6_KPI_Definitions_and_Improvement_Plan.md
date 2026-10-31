# Week 6 — KPI Definitions, Interpretation and Continuous-Improvement Plan

> All values are synthetic training data. They are not Salesforce telemetry, customer results, or measured business outcomes.

## KPI formulas
- Lead assignment timeliness = Leads assigned within 30 minutes / Leads received × 100.
- Case SLA attainment = Cases closed within SLA / Cases closed × 100.
- Record completeness = Complete records / Records audited × 100.
- Duplicate rate = Duplicate records / Records audited × 100.
- Training completion = Users completed / Training users × 100.

## Simulated trend
| KPI | Week 1 | Week 6 | Change |
|---|---:|---:|---:|
| Lead assignment timeliness | 70.0% | 91.8% | +21.8 pp |
| Case SLA attainment | 75.6% | 93.1% | +17.5 pp |
| Record completeness | 78.0% | 95.0% | +17.0 pp |
| Duplicate rate | 9.0% | 3.0% | -6.0 pp |
| Training completion | 68.0% | 100.0% | +32.0 pp |

These are designed outcomes for analysis practice, not claims that an intervention produced the improvement.

## Continuous-improvement plan
1. **Baseline:** freeze KPI definitions, owners, filters, and reporting period.
2. **Diagnose:** segment misses by queue, source, priority, missing field, and user role.
3. **Prioritize:** address high-volume/high-impact causes first.
4. **Improve:** propose routing rules, required-data guidance, duplicate checks, and role-based training.
5. **Validate:** compare a defined post-change period with the baseline using the same formulas.
6. **Control:** review weekly exceptions and monthly KPI trends; investigate threshold breaches.
7. **Learn:** retain useful controls, revise weak interventions, and document assumptions.

## Proposed thresholds
Lead assignment ≥90%; case SLA ≥90%; completeness ≥95%; duplicate rate ≤3%; training completion ≥95%. These are simulated planning targets and require business validation before real use.
