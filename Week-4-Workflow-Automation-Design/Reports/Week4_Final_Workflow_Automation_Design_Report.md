# Week 4 — Workflow Automation Design Report

**Portfolio:** Salesforce CRM Operations Learning Portfolio  
**Business scenario:** Cedarline Office Products (fictional)  
**Report type:** Functional design and simulated validation  
**Author:** Hrudhai Prem Kumar Patwari

> **Evidence and simulation disclosure:** Cedarline Office Products is a fictional training scenario. This report proposes Salesforce lead and case-routing automation. No live Salesforce org was accessed; no Flow, Workflow Rule, or Process Builder automation was configured, activated, executed, or deployed. The test cases are desk-based simulated scenarios with expected outcomes, not platform execution evidence. Benefits are expected, not measured.

## 1. Executive summary

This report designs a controlled approach to reduce manual lead distribution and case triage for the fictional Cedarline Office Products business. The proposal covers two operational processes: routing new leads to an appropriate sales queue and routing service cases according to severity. The design uses explicit decision criteria, exception paths, ownership controls, test scenarios, monitoring, and rollback planning.

The central recommendation is to use maintainable, record-triggered Salesforce Flow designs, subject to validation in an authorized sandbox and approval by process owners. Deterministic routing should handle records with complete and valid inputs. Missing or conflicting data should be sent for human review rather than assigned through an unreliable default.

## 2. Business background and problem statement

Cedarline is modelled as a growing office-products supplier with sales enquiries arriving through multiple channels and service cases requiring different levels of attention. In a manual process, a coordinator may need to inspect each lead's source, region, and company size before choosing a sales team. Service staff may also need to review case severity and manually determine the appropriate support queue.

Manual triage can create inconsistent ownership, delayed follow-up, avoidable reassignment, and weak visibility into exceptions. Automation can standardize routine decisions, but poorly designed automation can also amplify bad data or repeatedly overwrite legitimate ownership changes. The proposed solution therefore combines routing rules with validation, exception handling, monitoring, and human accountability.

## 3. Objectives and success measures

The design aims to:
- Apply consistent lead routing based on agreed business attributes.
- Route cases according to severity and the agreed support model.
- Prevent incomplete or invalid records from silently entering the wrong queue.
- Provide an auditable reason for exceptions and assignment failures.
- Make the logic understandable, testable, maintainable, and reversible.

If implemented in a real environment, success should be assessed using agreed measures such as percentage assigned within the target time, reassignment rate, exception rate, case SLA attainment, and number of automation faults. No baseline or realized improvement is claimed in this training report.

## 4. Scope, assumptions, and boundaries

### In scope
- Proposed lead routing by source, employee band, and region.
- Proposed case routing by severity.
- Missing-data and assignment-failure handling.
- Test design, operational controls, implementation sequence, and rollback.

### Out of scope
- Actual Salesforce configuration or deployment.
- Real customer, employee, or production data.
- Integration with external systems, telephony, email, or ERP.
- Claims about live queue membership, licenses, permissions, or org-specific field names.

### Assumptions requiring business confirmation
- Lead source, employee count/band, and region are available and governed fields.
- The business will define queue membership, regional coverage, and ownership responsibilities.
- Case severity values and escalation expectations are approved by the service owner.
- The Salesforce edition, licenses, security model, and automation limits support the final design.

## 5. Proposed solution architecture

The proposed design uses two independent record-triggered automation processes.

### 5.1 Lead assignment

**Trigger concept:** A new lead is created, or a defined set of routing fields changes while the lead remains eligible for automated assignment.

**Decision sequence:**
1. Check whether all required routing attributes are present and valid.
2. If required data is missing or invalid, route the record to a Data Quality Review queue.
3. If source is Partner, route to the Partner Sales queue.
4. Otherwise, evaluate the employee band:
   - Enterprise band: route to Enterprise Sales.
   - Small-business band: route to SMB Sales.
   - Unclassified or boundary values: route to Sales Operations Review until the business defines a rule.
5. Apply regional ownership only where a region-specific queue or assignment rule has been approved.
6. Record the routing outcome/reason in an approved field or audit mechanism, where appropriate.

The supplied test scenarios use illustrative values: 650 employees for an enterprise lead and 80 employees for an SMB lead. The exact employee thresholds and precedence rules must be confirmed by the business before implementation.

### 5.2 Case routing

**Trigger concept:** A new case is created, or severity changes and the case is eligible for rerouting under the agreed policy.

**Decision sequence:**
1. Validate that severity is populated with an allowed value.
2. If severity is missing or invalid, send the case to a Case Triage Review queue.
3. Critical severity: route to Priority Support and notify the designated manager/on-call role using an approved notification mechanism.
4. High severity: route to Tier 2 Support.
5. Normal severity: route to Tier 1 Support.
6. Preserve an audit trail of reassignment and escalation activity.

The business must define the operational meaning of each severity, coverage hours, response targets, and notification recipients. Severity should not be inferred solely from free-text descriptions without an approved classification process.

## 6. Decision table

| Object | Condition | Proposed destination | Handling |
|---|---|---|---|
| Lead | Required routing data missing/invalid | Data Quality Review | Human verification |
| Lead | Source = Partner | Partner Sales | Partner-specific ownership |
| Lead | Non-partner; employee band = Enterprise | Enterprise Sales | Enterprise sales handling |
| Lead | Non-partner; employee band = SMB | SMB Sales | SMB sales handling |
| Lead | Employee band/region cannot be classified | Sales Operations Review | Resolve rule or data gap |
| Case | Severity = Critical | Priority Support | Notify manager/on-call role |
| Case | Severity = High | Tier 2 Support | Specialist handling |
| Case | Severity = Normal | Tier 1 Support | Standard handling |
| Case | Severity missing/invalid | Case Triage Review | Human triage |
| Either | Assignment operation faults | Operations Review | Capture fault and investigate |

Where more than one condition could apply, precedence must be explicit. In this proposal, data validation occurs before routing, and Partner source takes precedence over employee band for leads. The business owner must approve this precedence.

## 7. Proposed Salesforce configuration approach

In an authorized sandbox, a Salesforce administrator could implement the design with record-triggered Flows and appropriate Decision, Assignment, Update Records, and fault-handling elements. Exact object fields, trigger timing, entry conditions, and queue IDs should be selected only after inspecting the target org's schema and governance standards.

Recommended build sequence:
1. Confirm the process owner, queue owners, membership, required fields, allowed values, and reassignment policy.
2. Document the routing decision table and obtain business sign-off.
3. Create a narrowly scoped record-triggered Flow for lead routing.
4. Create a separate record-triggered Flow for case routing to keep logic understandable and independently testable.
5. Add entry criteria to prevent unnecessary execution on unrelated updates.
6. Prevent repeated reassignment or recursion by checking current ownership, prior routing state, and whether the record is still eligible.
7. Configure fault paths and an operations-review mechanism.
8. Review access, notifications, field-level security, and audit requirements.
9. Test in a sandbox with synthetic records before approval and controlled activation.

A single complex Flow should not be used merely to reduce the number of automation assets. Separation by business process can improve ownership, troubleshooting, and change control.

## 8. Test plan and simulated results

The repository's `Week4_Automation_Test_Cases.csv` contains eight scenarios. The following table summarizes the desk-based expected outcomes.

| Test ID | Scenario | Expected result | Status |
|---|---|---|---|
| W4-T01 | Partner lead; South region | Partner Sales Queue | Simulated-Pass |
| W4-T02 | Web lead; 650 employees; South | Enterprise Sales Queue | Simulated-Pass |
| W4-T03 | Web lead; 80 employees; South | SMB Sales Queue | Simulated-Pass |
| W4-T04 | Web lead; region blank | Data Quality Queue | Simulated-Pass |
| W4-T05 | Critical case | Priority Support + manager notification | Simulated-Pass |
| W4-T06 | High case | Tier 2 Queue | Simulated-Pass |
| W4-T07 | Normal case | Tier 1 Queue | Simulated-Pass |
| W4-T08 | Simulated assignment error | Operations Review + admin notification | Simulated-Pass |

**Interpretation:** “Simulated-Pass” means the expected destination is consistent with the proposed decision logic during a desk-based walkthrough. It does not mean a Salesforce Flow was run or that a platform test passed.

Additional tests recommended before real deployment:
- Employee-count boundary values immediately below, at, and above each approved threshold.
- Unknown lead source, unsupported region, and blank employee count.
- Existing lead owner and manually locked/controlled ownership scenarios.
- Case severity changed after initial assignment.
- Repeated updates to verify no routing loop or unnecessary reassignment.
- Queue unavailable, insufficient access, and fault-path failure.
- Bulk record creation/update and governor-limit considerations.
- Notification failure and after-hours escalation.

## 9. Exception handling and operational controls

Automation should fail visibly and safely. Missing data should enter a review queue with a clear reason. An assignment fault should capture sufficient diagnostic context for authorized support staff without exposing secrets or unnecessary personal information.

Key controls:
- Least-privilege access to create, edit, activate, and deactivate automation.
- Named business and technical owners for each routing process.
- Version-controlled decision logic and documented change history.
- Approved queue membership and periodic access review.
- Fault paths, exception ownership, and a defined response process.
- Duplicate/recursion assessment and idempotent routing behavior.
- Test evidence and approval before production activation.
- Monitoring of assignment exceptions, unexpected reassignment, and automation errors.

Users should not be encouraged to bypass routing by editing ownership without following the agreed exception process.

## 10. Implementation, validation, and rollback

### Implementation stages
1. **Discovery:** Confirm business rules, data definitions, owners, queues, security, and service targets.
2. **Design approval:** Review decision tables, precedence, exception paths, and acceptance criteria.
3. **Sandbox build:** Configure the proposed Flows in a non-production environment.
4. **Validation:** Run positive, negative, boundary, bulk, security, and fault-path tests.
5. **User acceptance:** Obtain sales, service, and operations sign-off.
6. **Release approval:** Document change record, deployment window, support contacts, and rollback owner.
7. **Controlled activation:** Activate only after approvals and verify a monitored sample.
8. **Hypercare:** Review errors, misroutes, exceptions, and user feedback.

### Rollback plan
If material routing errors occur:
1. Pause or deactivate the new automation version according to the release procedure.
2. Restore the last approved version or previous routing process.
3. Identify records affected during the incident window.
4. Review and correct ownership using authorized procedures.
5. Confirm that normal lead and case handling has resumed.
6. Preserve error details, impact, corrective actions, and approval records.
7. Re-test the corrected design before a new release.

Rollback should be tested and documented before production activation; simply deactivating automation may not automatically restore record owners already changed.

## 11. Expected benefits and risks

**Expected benefits (not measured):**
- More consistent assignment for records with complete data.
- Less repetitive manual triage.
- Clearer handling of critical cases.
- Better visibility of incomplete records and routing faults.
- More repeatable testing and change governance.

**Risks and mitigations:**

| Risk | Mitigation |
|---|---|
| Incorrect or stale routing data | Validate required fields; route exceptions for review |
| Overly broad trigger conditions | Use narrow entry criteria and regression tests |
| Incorrect queue membership | Confirm queue owners and access before activation |
| Reassignment loops | Add eligibility checks and test repeated updates |
| Missed critical notification | Define monitored notification path and fallback |
| Uncontrolled rule changes | Require owner approval, versioning, and release records |

## 12. Limitations and next steps

This report is a functional design exercise, not a technical implementation record. The final build depends on Cedarline's approved data model, Salesforce configuration, licensing, queue structure, security model, and operational policies. No actual timing, productivity, SLA, or quality improvement has been measured.

The next step would be a requirements workshop with sales, service, operations, and Salesforce administration stakeholders. The output should be an approved field dictionary, queue/ownership matrix, severity definition, threshold policy, and acceptance-test plan.

## 13. Conclusion

A reliable automation design does more than assign records. It defines when automation should act, when it should stop, how exceptions are owned, how results are validated, and how the change can be reversed. The proposed Cedarline design provides a structured starting point for controlled lead and case routing, while keeping all implementation and outcome claims within the evidence available in this simulated portfolio.

## Appendix — Related repository artefacts

- [Lead assignment and case routing flow (Mermaid)](Lead_Assignment_and_Case_Routing_Flow.mmd)
- [Automation test cases (CSV)](Week4_Automation_Test_Cases.csv)
- [Implementation and rollback plan](Week4_Implementation_and_Rollback_Plan.md)
- [Original report (DOCX)](Week4_Workflow_Automation_Design.docx)

---
**Disclosure:** Fictional business; synthetic scenarios; proposed configuration only; no live Salesforce access, build, execution, or deployment.
