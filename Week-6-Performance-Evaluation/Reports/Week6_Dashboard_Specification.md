# Week 6 — Simulated Performance Dashboard Specification

> Dashboard design only. No Salesforce dashboard was built or captured from a live org.

## KPI cards
Display lead assignment timeliness, case SLA attainment, record completeness, duplicate rate, and training completion with current-period value, target, and prior-period comparison.

## Charts
1. Line chart: weekly lead-assignment timeliness.
2. Line chart: weekly case SLA attainment.
3. Line chart: weekly record completeness and duplicate rate.
4. Column chart: training completion by week.
5. Exception table: KPI, target, actual, variance, owner, proposed action.

## Filters
Week/date range, lead source, case priority, queue/team, region, and training role where the source dataset supports the dimension.

## Interpretation rule
A green/positive trend in this simulated dataset demonstrates only how a dashboard could communicate change. It must not be described as realized operational improvement.
