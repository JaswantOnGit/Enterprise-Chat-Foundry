# UAT Checklist — Enterprise Chat Web App

## Test Case 1 — Baseline (Ungrounded) Behavior
- [x] Ask agent a product-specific question before any data grounding is configured
- [x] Confirm response is generic, incorrect, or references the wrong product/brand
- [x] Screenshot captured as evidence: `screenshots/03_baseline-ungrounded-response.png`

## Test Case 2 — File Search Tool Configuration
- [x] Attach File Search tool to the agent
- [x] Create a new vector index and upload approved source documents
- [x] Confirm all files show "Success" status after indexing
- [x] Screenshot captured: `screenshots/04_file-search-tool-configured.png`

## Test Case 3 — Grounded Response Accuracy
- [x] Re-ask the identical question used in Test Case 1
- [x] Confirm the answer now reflects the correct product and price
- [x] Confirm a source-file citation is visibly attached to the response
- [x] Confirm the tool tag on the response reads "File search," not "Web search"
- [x] Screenshot captured: `screenshots/05_grounded-response-with-citation.png`

## Test Case 4 — Agent Web Preview
- [x] Publish/preview the agent as an end-user-facing web app
- [x] Re-run the same query in the preview interface
- [x] Confirm response consistency with the playground-grounded answer
- [x] Screenshot captured: `screenshots/06_agent-web-preview.png`

## Sign-off
| Role | Name | Result |
|---|---|---|
| AI Project Manager | Jaswant Singh | ✅ Approved — all test cases passed |

**Known limitation carried forward (not blocking for lab/demo purposes):** Web Search remains enabled as a fallback tool. In a production rollout, this should be disabled or gated per RAID item R2 to prevent the agent from answering with unverified, non-indexed information.
