# Project Charter — Enterprise Chat Web App (Microsoft Foundry)

## Project Name
Enterprise Knowledge Chat Agent — RAG-Grounded Deployment on Microsoft Foundry

## Sponsor / Delivery Lead
Jaswant Singh, AI Project Manager (PMP, AWS Certified AI Practitioner)

## Background
Employees currently rely on generic AI assistants or manual document search to answer product/policy questions. Generic LLM responses are inconsistent, occasionally wrong, and cannot be traced back to an approved source — creating both an accuracy risk and an audit gap.

## Business Objective
Deploy a conversational AI agent that answers employee questions **exclusively grounded in approved internal documentation**, with every answer traceable to a source file, so the business can trust and audit what the agent tells employees.

## Scope

**In scope**
- Microsoft Foundry project + agent provisioning (`chat-web-app01` / `enterprise-agent`)
- GPT-5-mini model deployment (Global Standard)
- File Search tool configuration against a dedicated vector index (`enterprise-index`)
- Baseline (ungrounded) vs. grounded response validation
- Agent Web Preview validation of the end-user experience

**Out of scope (this phase)**
- Production web app deployment (requires Microsoft 365 Business License — deferred)
- Teams / Microsoft 365 Copilot channel publishing
- Multi-agent workflows / routines (Preview features, not GA)
- Automated CI/CD for index refresh (manual process in this phase — see RAID)

## Success Criteria
| # | Criterion | Target |
|---|---|---|
| 1 | Grounded response accuracy | Agent answers product-specific questions using only indexed source docs |
| 2 | Citation presence | Every grounded answer includes a visible source file reference |
| 3 | Baseline delta documented | Ungrounded vs. grounded response captured as before/after evidence |
| 4 | Tool routing correctness | Agent prefers File Search over Web Search when the index has coverage |

## Key Stakeholders
| Role | Responsibility |
|---|---|
| AI Project Manager (delivery lead) | Scope, governance artifacts, quality gates |
| Content Owner (business) | Approves what enters the vector index |
| Security/Data Governance reviewer | Vets source docs for PII / sensitive data before indexing |

## Timeline
Single-session build and validation (~3 hours), consistent with lab cost/time envelope.

## Budget
Estimated $1–$3 in Azure consumption (GPT-5-mini token usage, File Search indexing, minimal storage) — no production spend committed in this phase.
