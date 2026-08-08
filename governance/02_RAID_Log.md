# RAID Log — Enterprise Chat Web App

## Risks
| ID | Risk | Likelihood | Impact | Mitigation |
|---|---|---|---|---|
| R1 | Uploaded source documents contain PII or sensitive commercial data that becomes retrievable by any user who can query the agent | Medium | High | Content Owner review gate before any file is attached to the vector index; no direct user uploads to production index |
| R2 | Agent falls back to Web Search (Grounding with Bing) when the index lacks coverage, returning ungrounded / off-brand answers (observed: agent quoted a different "Trailwalker" brand and EUR pricing) | High (observed in baseline test) | Medium | Restrict or disable Web Search tool in production; instruct agent via system prompt to state "not covered by internal docs" rather than search the open web |
| R3 | Token/query costs scale with adoption; no budget alert configured in this phase | Low (lab scale) | Medium | Add Azure Cost Management budget alert before any production rollout |
| R4 | Vector index becomes stale as product/policy docs change, causing the agent to confidently cite outdated information | Medium | High | Define index refresh cadence and ownership (see RACI); add "last indexed" freshness check to Quality Gate |

## Assumptions
| ID | Assumption |
|---|---|
| A1 | Source documents provided for indexing are the current, approved version at time of upload |
| A2 | Single-region deployment (documented region) is acceptable for this phase; no multi-region redundancy required |
| A3 | End users are internal employees only — no external/public access in this phase |

## Issues
| ID | Issue | Status |
|---|---|---|
| I1 | Baseline (ungrounded) test returned a wrong-brand, wrong-currency answer rather than an "I don't know" — confirms need for R2 mitigation before any production consideration | Logged; mitigation not yet implemented (lab scope) |

## Dependencies
| ID | Dependency |
|---|---|
| D1 | Availability of GPT-5-mini capacity in the selected Foundry region |
| D2 | Microsoft 365 Business License — required for full web app publish (currently blocking; Preview mode used instead) |
