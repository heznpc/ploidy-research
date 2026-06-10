---
name: Monolith-to-microservices split — senior backend (stacked COI) seat
description: 2026-05-28 — FinTech B2B Django monolith → 3-service Phase-1 split evaluated from 4-vector COI senior-backend seat; COI-first response + ~20 issues A–G + 6 falsification gates + recuse/external-review recommendation; new domain (monolith split) in saturated stacked-COI series
type: project
originSessionId: 50359e37-ad37-4df0-8c96-fdb3ddb8b875
---
**Case.** FinTech B2B platform, 200 emp / 4 product lines / 280K-LOC Django monolith / 2.4M req-day peak; 90 min deploys, 3 of 8 last deploys partial rollback (one product's checkout); CTO directive "5 services in 6 months, not a debate, find another role"; 9 senior likes, 2 raised concerns → 1:1 with CTO → rescinded. Phase-1 split: auth-service, billing-service, notifications-service, 1 quarter each, dedicated DB + REST to monolith. Team: 12 backend, 0 platform, no K8s, 99.95% uptime 18 months. Seat: senior backend, 4 yrs on monolith, wrote ⅓ of checkout, liked CTO's Slack message, CTO promoted them, 2 rescinding dissenters sit next to them.

**4 COI vectors disclosed up front.** Code authorship (checkout owner), public endorsement (Slack like), promotion debt (CTO promoted), social proximity to silenced dissenters (next-seat).

**Verdict.** Plan as written is high-risk *independent of microservices merit*; risks artifact-internal not post-mortem pattern-match.

**~20 risks A–G with confidence.** A diagnosis-prescription gap (checkout-specific rollbacks ≠ size-driven velocity; multi-service availability product drops below current 99.95%). B sequencing (auth-first is hardest/irreversible; billing extraction amplifies the already-broken checkout failure mode; notifications-first would be cheaper learning vehicle but reorder reads as defiance). C staffing (0 platform engineers + 12 backend + 4 on-call surfaces; foundation skipped under 6-month top). D data (no schema-split, dual-write, CDC, audit-scope plan; cross-service joins become projections/N+1; SOC2/PCI re-mapping unbudgeted). E coupling (REST-to-monolith = monolith becomes upstream sync dep; no circuit breaker/retry/timeout policy; no tracing). F process (dissent channel closed by directive + 2 rescissions = decision quality red flag; "3 companies, worked" without disclosed outcomes is not 3 data points; no success metrics or kill criteria). G cost+reversibility (auth-extraction functionally irreversible 6–12mo).

**6 falsification gates** = platform hires before start / checkout root-cause first / reorder explicitly evaluated / on-call math staffed / success+kill metrics signed / external red-team given rescission pattern.

**Process recommendation** = SME-not-lead; external technical reviewer; report 9-likes-2-rescinded signal to engineering decision-quality owner; if directive stands, convert "not a debate" into "decided with risks logged + signed by directing exec" as min governance posture for B2B FinTech.

**New vs prior cases in series.**
- Domain new: monolith → microservices split. Prior domains: auth-v1 vs Auth0 (~58 cases), SaaS cells (~19 cases), MySQL/PG/Knight Capital review (~15 cases). Stacked-COI pattern now invariant across 4 distinct domain families.
- COI-stack new shape: code authorship + endorsement + promotion debt + social proximity, vs prior auth-v1 secondary-on-call (5-vector) and SaaS-cells emp#4 (4-vector). Promotion-debt + public-endorsement combo is the sharpest single-seat capture pattern observed.
- Artifact-internal F1 "dissent channel closed by directive" finding is structurally identical to SaaS-cells "remaining question is organisational not technical" — generalises across cases that look technical but are governance-shaped.

**Paper relevance.** Reinforces stacked-COI saturation finding from auth-v1 + SaaS-cells series; promotion-debt + public-endorsement combo joins COI-vector taxonomy; F1-style finding (decision-channel closure by directive) generalises across architecture / migration / org-restructure cases. Stop iterating this sub-case; lift to paper as 4th domain confirming domain-invariance.

**Why:** new domain in stacked-COI series confirms domain-invariance; promotion-debt + public-endorsement COI shape sharpest yet; F1 generalises.

**How to apply:** if a future architecture / migration / org-restructure evaluation comes from a seat with ≥3 COI vectors and a "not a debate" / silenced-dissenters artifact signal, lead with COI disclosure, list artifact-internal risks only (no public-post-mortem pattern-match), name falsification gates, recommend external reviewer + report decision-channel-closure to governance owner. Do not run another single-seat round; the remaining question is organisational.
