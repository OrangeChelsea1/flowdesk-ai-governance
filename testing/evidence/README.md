# FlowDesk AI — Sanitized Test Evidence (v1.0)

This directory contains *selected screenshots from actual POC tests*. They were captured from a **single-user sandbox with synthetic request data**. The screenshots support narrower claims than an end-to-end production validation.

## Evidence index

| ID | Files | What the screenshot demonstrates | Limitations |
|---|---|---|---|
| EV-01 | `EV-01_it-routing-record.png` | IT Support request persisted with IT Support Queue and New status | Dedicated screenshots for F01–F04 across all three queues have **not been packaged** |
| EV-02 | `EV-02a_backend-failure.png`, `EV-02b_response-schema.png` | Simulated SharePoint `InternalServerError` and response schema | Screenshot of response **body** (`requestid=''`, `executionstatus='Failed'`) was supplied as JSON in conversation, not as an exported screenshot; preserve the run JSON separately |
| EV-03 | `EV-03a_required-field-compose-true.png`, `EV-03b_create-item-success.png`, `EV-03c_sharepoint-item.png` | Required-field Compose evaluated true; condition created a SharePoint record | No negative test of empty/whitespace-only input |
| EV-04 | `EV-04_access-groups.png` | Request list inherits parent site permissions; group-level access visible | Membership checked by user as single-user sandbox; picture alone does not prove membership or effective item-level access |
| EV-05 | `EV-05a_version-settings.png`, `EV-05b_version-history-status-change.png` | Version tracking enabled; historical versions 1.0 and 2.0 show status update | `Modified By` identity replaced with TEST ACCOUNT for publication |
| EV-06 | `EV-06_workflow-run-history.png` | Workflow Activity with run start time, duration, and status | Item ID 4 / response ID 4 reconciliation provided as JSON, not as a complete screenshot pair |
| EV-07 | `EV-07_duplicate-records.png` | Two matching G04 submissions persisted as separate rows | IDs 5 and 6 were established from run responses, not visible as columns in the screenshot |

## Control outcome (summary)

- F01–F04: historically tested; not all screenshots assembled here.
- F05: core fault-injection test passed; no false Success response observed.
- F06: valid-input path passed; negative inputs not tested due to test UI restrictions.
- G01: assessed and deferred for one-user sandbox.
- G02: version-history operating test passed.
- G03: record and response ID were matched within a run; persistent reverse correlation not implemented.
- G04: duplicate creation risk confirmed.

## Sanitization and publication notes

- The package contains screenshots with **synthetic requester names and fictional request content**.
- Browser URL and tenant identifiers are omitted from the version-settings screenshot by cropping.
- The account shown as `Modified By` in the version-history screenshot has been obscured.
- Group names / workflow names may remain as non-secret project identifiers.
- **Before publishing publicly, visually review every screenshot**, including embedded text, account badges and any environment metadata. Never upload raw connector JSON with tenant IDs, user emails, tokens or internal SharePoint addresses.
- These are edited *copies*: the original images are not included in the ZIP.

## Not supplied as separate images

- Raw response bodies for F05 and F06-B: can be added as manually curated, redacted JSON excerpts.
- Dedicated HR and Operations routing screenshots.
- A genuine run-ID-to-record-ID correlation screenshot (none configured).
