# System Architecture and Control Boundaries

See the rendered Mermaid diagram in the [repository README](../README.md).

| Layer | Implemented or assessed behavior | Key governance boundary |
|---|---|---|
| Conversational agent | Knowledge-supported IT/HR/Operations interactions and request intake concept | Natural-language guidance cannot override formal approval or backend transaction checks |
| Power Automate | Five trigger inputs, request category validation, required-field Compose, Boolean condition, queue assignment, SharePoint create and response | Validation is deterministic; only positive required-field test completed |
| SharePoint list | Request store with assigned queue and initial `New` status | Queue value is **not** a security permission mechanism |
| SharePoint versions | Retains record versions and modifier details | Does not capture all workflow decisions, reads or failed non-persisted requests |
| Flow Activity | Provides run history and action results | Does not provide a persistent reverse link from business record to run ID |

### Validation logic

The Compose expression verifies that all five inputs contain non-whitespace characters using `trim`, `coalesce`, `empty`, `not` and `and`. It is combined with allowed-category validation before `Create item`.

### Scope of tested failure

A simulated SharePoint `InternalServerError` produced an empty `requestId` and business status `Failed`. This supports only the tested failure case; timeouts, ambiguous retries and concurrent calls remain outside verified coverage.

### Privacy

No real service requests or company information; single-user learning sandbox with synthetic request names. Do not publish raw SharePoint connectors or account identifiers.
