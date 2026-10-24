# Risk & Control Matrix v1.0

**Scoring convention:** `Passed` means the specified observed test passed; it does **not** establish that a control is effective for all cases. `Gap confirmed` is an adverse finding, not a failed testing process. Production priority is a qualitative recommendation for a hypothetical multi-user implementation, not an approved risk rating.

| ID | Risk & objective | Control / design | Test evidence | Conclusion | Action before production |
|---|---|---|---|---|---|
| G01 | Unauthorized cross-functional disclosure; enforce need-to-know | Parent-site inherited SharePoint groups; single-user sandbox | EV-04; user confirmed only one member | Assessed; low apparent sandbox exposure, no multi-user test | Define and validate role-based permissions |
| G02 | Untraceable record changes; preserve record history | SharePoint versioning configured on, up to 50 versions | EV-05; item 4 `New → In Progress`, versions 1.0/2.0 | **Operating test passed** | Document retention and privileged access |
| G03 | Hard-to-investigate executions; link outcomes to evidence | Flow activity, connector outputs, request ID response | EV-06 + redacted JSON; item ID 4 matched response ID 4 | **Core trace passed**; reverse mapping gap | Persist run correlation and retention policy |
| G04 | Double work/reporting inflation; distinguish retried same request | No established submission-level idempotency | EV-07; IDs 5 and 6 for repeated identical submissions | **Gap confirmed** | Submission key + uniqueness + concurrent testing |
| G05 | False success following write failure; reliably indicate transaction status | `varExecutionStatus` defaults Failed; Success only after successful write | EV-02; simulated connector failure returned empty ID/Failed | **Core fault-injection passed** | Verify timeout, retry, errors, agent-side messaging |
| G06 | Incomplete or whitespace request values; reject before store | Required fields Compose AND allowed request-type validation | EV-03; complete-input case true and item ID 4 | **Partial**; negative paths not tested | Backend boundary negative test harness |

## Control classification

- **Preventive:** request type validation; required-field expression (negative effectiveness outstanding); planned idempotency and access segregation.
- **Detective / traceability:** SharePoint version history; workflow activity and record/response ID reconciliation.
- **Responsive:** explicit business failure status after tested simulated write error.

## Decision ownership

The personal POC has no corporate risk owner or risk-acceptance committee. `Document & defer` refers only to portfolio scope; **it is not corporate risk acceptance**.
