# Week 3 Technical One-Pager — Salesforce Integration Planning

## Integration principles
- Define a system of record for every business attribute before designing synchronization.
- Use supported APIs, approved authentication, least privilege and secret storage.
- Define canonical schemas, field mappings, validation, versioning and null handling.
- Use external IDs and idempotent processing to prevent duplicate side effects.
- Separate retryable technical failures from permanent business/data failures.
- Monitor latency, failures, backlog, API usage, data freshness and reconciliation.

## Proposed logical sequence
1. Salesforce event or scheduled extract is produced.
2. Middleware authenticates and validates the message.
3. Transformation maps fields to the target contract.
4. ERP or marketing platform processes the request.
5. Acknowledgement or error is recorded with a correlation ID.
6. Salesforce is updated where appropriate, or the message enters an exception queue.
7. Reconciliation compares expected and actual records.

## Security and operations checklist
- Confirm data classification and lawful purpose.
- Confirm marketing consent and suppression status before export.
- Use approved OAuth/identity patterns; never commit secrets.
- Encrypt traffic, restrict access, log administrative actions.
- Define retry limits, dead-letter handling, replay approval and ownership.
- Test duplicates, invalid data, timeouts, rate limits, schema changes and opt-outs.

**Boundary:** Proposed design for a fictional business. Not evidence of an integration configured, tested or deployed in a live Salesforce org.
