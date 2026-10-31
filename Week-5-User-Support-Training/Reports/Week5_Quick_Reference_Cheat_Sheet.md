# Salesforce User Quick Reference — Week 5

## Before editing a record
1. Search for an existing record first.
2. Confirm identity and ownership.
3. Use verified information only.
4. Complete required fields without guessing.
5. Save and review the result.

## When something goes wrong
- Capture exact error text, timestamp/time zone and affected feature.
- Note business impact and steps to reproduce.
- Check only what your role permits.
- Do not repeatedly retry without understanding the error.
- Escalate permission, routing or configuration issues through the approved path.

## Common checks
| Issue | Check first | Safe action |
|---|---|---|
| Cannot edit | Access, role, field behavior | Escalate with exact error |
| Possible duplicate | Existing matches | Pause and request review |
| Wrong owner | Routing fields and process | Send for ownership review |
| Report mismatch | Filters, dates, status, owner scope | Record settings and compare sample |
| Case cannot close | Resolution details and status rules | Complete valid details or ask support |

## Security reminders
- Never share passwords or tokens.
- Never put secrets in case comments.
- Do not broaden access without approval.
- Do not export or change data outside your authorization.
- Use approved secure channels for restricted evidence.

## Escalation minimum
Issue + business impact + affected function + time/time zone + exact error + reproduction steps + expected vs observed + checks already completed.

**Fictional training guide. Validate all steps against the authorized Salesforce org before operational use.**
