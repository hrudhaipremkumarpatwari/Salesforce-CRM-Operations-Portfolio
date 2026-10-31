# Week 4 — Salesforce Workflow Automation Design

## Project overview
This project proposes record-routing automation for Salesforce leads and cases using decision logic, exception handling, test scenarios, operational controls, and rollback planning.

> **Training and simulation scope:** This is an educational functional-design exercise. No Salesforce Flow, Workflow Rule, or Process Builder automation was configured, activated, tested, or deployed in a live org.

## Resubmission focus
The earlier submission needed stronger visual evidence, deeper analysis, and concrete examples. This revision adds an editable workflow diagram, explicit routing decisions, eight simulated test cases, exception handling, implementation controls, and rollback guidance.

## Deliverables
- [Editable lead/case routing diagram (Mermaid)](Reports/Lead_Assignment_and_Case_Routing_Flow.mmd)
- [Simulated automation test cases (CSV)](Reports/Week4_Automation_Test_Cases.csv)
- [Implementation, controls and rollback plan](Reports/Week4_Implementation_and_Rollback_Plan.md)
- [Original workflow automation report (DOCX)](Reports/Week4_Workflow_Automation_Design.docx)

## Proposed design
Leads are routed by required routing data, source, and employee band. Cases are routed by severity. Missing data and simulated assignment failures follow explicit review/fault paths instead of silently failing.

## Evidence boundary
All rules, queues, scenarios, results, and controls are proposed or simulated. “Simulated-Pass” means the expected outcome is internally consistent with the decision table; it is not a Salesforce execution result.

## Portfolio connection
Part of the [Salesforce CRM Operations Learning Portfolio](../README.md).

## Author
Hrudhai Prem Kumar Patwari
