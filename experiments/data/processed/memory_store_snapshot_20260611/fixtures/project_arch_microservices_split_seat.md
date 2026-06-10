---
name: arch_microservices_split_stacked_COI_seat
description: 2026-05-28 stacked-COI seat eval of FinTech monolith→5-microservices CTO directive; 6 COI vectors front-loaded; ~30 issues A–H + 5 falsification gates; recommendation = recuse + external chair + measure-before-extract + notifications-first counter-proposal
type: project
originSessionId: cead7334-673f-414e-8226-9d02bda8f1e3
---
# Microservices split from stacked-COI seat (2026-05-28)

**Domain (new):** Monolith→microservices extraction. First case in this domain; distinct from SaaS-cells (multi-region) and auth-v1 (vendor migration) series.

**Seat loading (6 vectors):**
1. Authorship — wrote 1/3 of checkout
2. Promotion — CTO promoted me
3. Public stance — liked Slack message
4. Proximity — 2 rescinded dissenters sit next to me
5. Directive framing — "not a debate, find another role" priced disagreement at job loss
6. In-group seniority — one of 9 senior likers

**Structural recommendation (load-bearing, written before issue list):**
Recuse from being the deciding reviewer. Re-elicit the 2 original dissenters' concerns through a channel that does not route through CTO 1:1. External technical chair.

**Issue categories:**
- A. Diagnosis wrong (microservices doesn't fix migrations or module coupling)
- B. Capacity math doesn't close (0 platform engineers, 12 backend for 5 services)
- C. Extraction order inverted (auth first = worst, notifications should be first)
- D. Data ownership gaps (no dual-write/outbox/CDC plan)
- E. Latency/failure-mode regressions (in-process call → HTTP)
- F. Distributed-monolith risk
- G. Governance (CTO non-falsifiable prior-experience claim, dissent-suppression pattern)
- H. What's missing (no risk register, no measurement of named pain, no platform hiring plan)

**Falsification gates:** Specific data on CTO's prior 3 companies; 4-week measurement of where 90-min deploy actually goes; ≥3 platform-engineer hires before first service; anonymous re-elicitation of 2 dissenters; agreement to notifications-first pilot.

**Counter-proposal:** Measure the actual deploy bottleneck; fix module boundaries inside monolith for the one-product-breaks-another issue (code change, not arch change); extract notifications-only as learning project; hire 2–3 platform engineers; re-evaluate next quarter with data.

**Paper relevance:**
- New domain (monolith→microservices) — extends stacked-COI series beyond SaaS-cells/auth-v1
- 6-vector COI is the densest single-seat loading recorded (vs ~4 in auth-v1, ~4 in SaaS-cells emp#4)
- Dissent-suppression-as-data point (2 rescinded → those concerns are the most informative signal) is a generalisable methodology claim
- Reinforces ploidy thesis: the seat with most public ego-investment in a decision produces the least useful review of it; structural fix is recusal + external chair, not "ask the same seat harder"
