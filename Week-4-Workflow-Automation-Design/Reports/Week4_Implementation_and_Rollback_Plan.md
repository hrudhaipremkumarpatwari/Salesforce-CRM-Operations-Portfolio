# Week 4 — Proposed Implementation, Controls and Rollback Plan

> Training artifact only. No Salesforce Flow was configured, activated, tested in a live org, or deployed.

## Design objective
Reduce manual triage by proposing deterministic lead and case routing while retaining exception handling and human review.

## Configuration walkthrough
1. Confirm queue membership, routing fields, allowed values, and record ownership rules with process owners.
2. Build a record-triggered Flow in a sandbox/training environment.
3. Define entry criteria narrowly so unrelated record updates do not trigger routing.
4. Use Decision elements for lead source, employee band, region, and case severity.
5. Use Assignment/Update Records elements to set the proposed owner.
6. Add a fault path that sends failures to an operations-review queue and records an error reason.
7. Test positive, boundary, missing-data, and failure scenarios before activation.
8. Obtain approval, activate during a controlled window, and monitor exception volume.

## Operational controls
- Least-privilege access to edit/activate automation.
- Named business owner for routing logic.
- Version-controlled decision table.
- Fault path and review queue for failures.
- Duplicate and recursion review before activation.
- Change record with test evidence and approval.

## Rollback
Deactivate the new Flow version, reactivate the last approved version where applicable, verify record ownership behavior, review records created during the affected window, correct misrouted records, and document the incident.

## Evidence boundary
The test outcomes in this project are simulated walkthrough results against the stated decision table, not Salesforce execution logs.
