# Production Readiness Gaps

This section intentionally documents **unresolved risks** rather than implying production readiness.

| Priority | Gap | Minimum exit criteria |
|---|---|---|
| P0 | Duplicate submission / ambiguous retries | Idempotency key for logical submission, datastore uniqueness, simultaneous retry tests |
| P0 | HR / IT / Operations permissions | Role-to-data access matrix and read/edit/delete tests under distinct accounts |
| P0 | Required-field negative scenarios | Observe backend refusing null, empty and whitespace input without creating a record |
| P1 | Timeout and partial failure | Explicit unknown outcome handling, retry policy, no double-write demonstration |
| P1 | End-to-end AI interaction | Scripted tests for collection of five fields, incomplete prompts and failure messaging |
| P1 | Durable correlation / monitoring | Run identifier stored or indexed per business item, alert and retention design |
| P2 | Operational KRIs | Definition and evidence for business failure rate, duplicate incident rate, response latency and unresolved request aging |

**Scope decision:** Implementing a full enterprise ticketing platform would be disproportionate to a portfolio POC. Documenting these gaps is a deliberate governance choice, not evidence that the controls were implemented.
