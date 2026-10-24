# Test Log — FlowDesk AI v1.0

| Test | Input / method | Expected result | Observed outcome | Assessment | Evidence |
|---|---|---|---|---|---|
| F01 | IT request | IT Support Queue, new record | IT record visible | Passed historically | EV-01 |
| F02 | Invalid category | Reject | Rejected in prior exercise | Passed historically; dedicated screenshot missing | Not packaged |
| F03 | HR request | HR Operations Queue | HR record created | Passed historically; dedicated screenshot missing | Not packaged |
| F04 | Operations request | Operations Support Queue | Operations record created | Passed historically; dedicated screenshot missing | Not packaged |
| F05 | Static-result SharePoint `InternalServerError` | Empty ID; business Failed | `requestid=''`, `executionstatus='Failed'` | Core test passed; no separate no-write screenshot | EV-02, redacted JSON |
| F06-A | Empty business impact | No create; Failed | Test UI rejected blank entry | **Not executed** | None |
| F06-B | All five fields complete | True validation; create; Success | Compose `true`, created ID 4, response Success | Passed | EV-03, redacted JSON |
| F06-C | Whitespace business impact | No create; Failed | Test UI rejected spaces | **Not executed** | None |
| G01 | Inspect permissions and membership | Document effective access | Site permission inheritance; owner reports one member | Assessed; multi-user effectiveness untested | EV-04 |
| G02 | Edit item 4 `New` to `In Progress` | Retain before/after versions | Versions 1.0 and 2.0, modifier, change shown | Passed | EV-05 |
| G03 | Inspect run for item 4 | Match create and response IDs | HTTP 201 ID 4; response HTTP 200 ID 4 | Core passed | EV-06 + redacted JSON |
| G04 | Submit identical request twice | Discover existing behavior | Both persisted as IDs 5 and 6 | **Gap confirmed** | EV-07 |

## Evidence interpretation

- Screenshots and redacted JSON support the specific documented observations only.
- F06 negative rejection has **not** been validated at the backend.
- A static-result test does not establish all production connector failure behavior.
- HTTP 200 on an agent response is a transport/action result, **not** a business-success indicator.
- Activity run history is not itself a documented persistent run-to-item correlation scheme.
- Do not claim production readiness, formal independent model validation, or actual enterprise risk acceptance.

See [evidence catalog](evidence/README.md).
