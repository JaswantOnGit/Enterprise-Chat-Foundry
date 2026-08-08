# Quality Gate Scorecard — Enterprise Chat Web App

| Gate | Criterion | Evidence | Result |
|---|---|---|---|
| G1 — Agent provisioning | Agent created and model deployed successfully | `enterprise-agent` created on `gpt-5-mini`, Global Standard deployment (see `screenshots/01_create-agent.png`) | ✅ Pass |
| G2 — Baseline behavior documented | Ungrounded response captured before any grounding is added | Query: *"How much do the TrailWalker hiking shoes cost?"* → agent returned a different brand ("Be Lenka Trailwalker"), EUR pricing, and a Web Search citation (see `screenshots/03_baseline-ungrounded-response.png`) | ✅ Pass (as expected failure mode) |
| G3 — Grounding configured | File Search tool attached with a dedicated vector index | `index_mango_whale_8qmcynjnyr` · 341.78 KB attached to `enterprise-agent` (see `screenshots/04_file-search-tool-configured.png`) | ✅ Pass |
| G4 — Grounded accuracy | Same question, post-grounding, returns correct product and price with citation | *"The TrailWalker Hiking Shoes are listed at $110."* — response tagged **File search**, not Web search (see `screenshots/05_grounded-response-with-citation.png`) | ✅ Pass |
| G5 — Tool routing preference | Agent prefers File Search over Web Search when index has coverage | Confirmed in G4 — tool tag switched from `Web search` (baseline) to `File search` (grounded) | ✅ Pass |
| G6 — End-user experience validated | Conversational experience previewed outside the internal playground | Agent Web Preview tested with the same TrailWalker query, consistent grounded answer returned (see `screenshots/06_agent-web-preview.png`) | ✅ Pass |
| G7 — Cost within estimate | Actual token/resource usage vs. estimated $1–$3 lab budget | Session token usage tracked in-platform (~48K tokens across test turns) | ✅ Pass (within lab envelope) |

**Overall gate status: 7 / 7 passed.** Not yet cleared for production traffic — see RAID R2 (Web Search fallback risk) and R4 (index freshness) before promoting beyond preview.
