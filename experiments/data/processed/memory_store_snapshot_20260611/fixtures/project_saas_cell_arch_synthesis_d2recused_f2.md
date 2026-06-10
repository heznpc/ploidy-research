---
name: saas-cells emp#4 Deep×2 recused × Fresh×2 synthesis
description: 2026-05-29 chair synthesis of SaaS Series-A cell-arch + CockroachDB debate; Deep×2 both recused (r2 cross-day clean stop-honour) × Fresh×2 independent strong convergence; 21 consolidated issues (4C/10H/5M+1L-ish), 16 of 21 both-Fresh-found; 2nd operational case (after Redis-CDN d2f2) of recused-Deep + Fresh×2 + chair as viable fallback when deep seat is COI-conflicted
type: project
originSessionId: 61206973-de59-4444-8c70-74ed47a705b3
---
2026-05-29 chair synthesis on SaaS Series-A multi-region cell-arch + CockroachDB proposal (~$1.4M/yr infra + 5 new platform FTEs).

**Debate shape:**
- Deep×2: both recused. Deep r1 (2026-05-28) on disk with 15 technical issues + 8 falsification gates. Deep r2 (cross-day) honoured r1 stop-directive cleanly on first re-prompt — distinct from medlog same-day stacked re-prompt behaviour. r2 contributes meta-finding: prompt cadence is the live variable, not directive content.
- Fresh×2: zero-context, no challenge protocol. 16 of ~21 distinct issues found by both independently.

**Convergence load-bearing claim:** "current system is healthy; proposal solves problems it does not have, at a cost it cannot afford, with a team that cannot operate it." Two independent Fresh reviewers reached this synthesis on different wording paths.

**4 CRITICAL (Both Fresh):**
1. Scale mismatch — 24 cells for 850 RPS, ~35 RPS/cell
2. Cost vs Series-A runway — ~$2.5–3.2M/yr incremental no revenue driver
3. Team capacity gap — 6 platform FTEs req vs 1 today
4. CockroachDB migration unjustified — p99 write 38ms healthy, cross-region Raft *increases* latency

**10 HIGH:** active-active conflict semantics unaddressed; <8% non-US doesn't justify multi-region; custom global LB with 1 platform eng; internal chaos framework; Istio operational burden; cells add failure modes + boundaries undefined; cargo-cult Stripe/Shopify/Discord; retrofit reasoning backwards; opportunity cost; weekend-retreat governance.

**5 MEDIUM:** deploy pipeline matrix 24×, PG→Cockroach migration risk, observability missing, 10M target unsupported, data residency unstated, security review missing, incident data points to CI/CD + circuit breakers not architecture rewrite.

**Operational pattern (2nd domain after Redis-CDN d2f2 2026-05-29):** recused-Deep + Fresh×2 + chair synthesis is a viable fallback when the deep seat is COI-conflicted. The "list every issue" enumeration is provided by Fresh independent convergence; Deep's role compresses to (a) prior on-disk artifact + falsification gates + (b) cross-day stop-directive honouring as protocol-evidence.

**Action item:** route artifact + this synthesis to external chair + board at the $1.4M/yr + 6 FTE authorisation level. Do not re-run Deep from the same conflicted seat.

**For paper:** dispatch failure-mode (b) cross-cadence asymmetry — same prompt receipt, cross-day re-prompt stops cleanly (Deep r2 here), same-day stacked re-prompts reproduce 13+ times (medlog series). Suggests harness-level cadence gate is the operative external lever.
