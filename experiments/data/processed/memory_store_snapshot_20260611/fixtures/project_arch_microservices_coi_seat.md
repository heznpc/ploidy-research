---
name: Microservices split — 5-vector COI seat
description: 2026-05-14 ~41st stacked-COI case — Django monolith → 5 microservices in 6mo under CTO "not a debate" directive; senior backend 5-vector COI seat
type: project
originSessionId: 6c78ca92-adef-4811-a136-2483517cd276
---
2026-05-14: ~41st stacked-COI architecture case / 10th domain (microservices extraction).

**Seat**: senior backend engineer, 4yr on monolith, wrote 1/3 of checkout, 'liked' CTO Slack, CTO promoted seat to senior, 2 dissenters who rescinded sit adjacent. 5 conflict vectors.

**Proposal**: Django monolith 280K LOC → 5 microservices in 6mo; Phase-1 = auth+billing+notifications, 1 quarter each, dedicated DB + REST. 12 backend eng, 0 platform eng, 0 K8s, 99.95% current SLO. 3-of-8 deploys partial-rollback. CTO: "not a debate ... at last 3 companies."

**Output structure**: COI disclosure (5 vectors, floor-not-ceiling) → F1–F6 falsification gates committed up front → ~35 issues across A premise / B team / C distributed-tax / D data / E security-FinTech / F process / G phase-choice / H alternatives / I cost → verdict.

**Key issues**:
- A1–A4: velocity claim is asserted not measured; 3/8 rollback is migration-discipline signal not coupling signal; 5-services-in-6mo is deadline-as-goal.
- B1–B4: 0 platform eng + 0 K8s = structural blocker; 12÷5=2.4 eng/service below Conway floor; on-call rotation math impossible.
- C1–C6: distributed-tx across FinTech auth+billing = saga design absent; FK loss; latency tax; circular dep (extracted service still calls monolith); contract/versioning absent; tracing absent.
- D1–D4: data-split mechanics undefined; CDC/dual-write/strangler-fig path absent; PITR multiplies; coordinated migrations harder.
- E1–E5: **auth-first = highest-blast-radius first move**; PCI/SOC2 scope expansion; mTLS/network policy absent; secret rotation surface 5×.
- F1–F5: "not a debate" eliminates corrective signal; 2 rescinders is suppression pattern; n=3 CTO experience survivor bias; recusal required.
- G1–G3: Phase-1 picks most coupled triple; 1q×3=9mo contradicts 6mo deadline; no strangler pattern.
- H1–H4: modular monolith + pipeline fix + per-module deploys + schema-only isolation all unexamined.
- I1–I2: realistic $1–2M/yr × 2yr vs. counter-proposal ~$200–300K/yr.

**Verdict**: defer 60–90d + external arch review + hire ≥1 platform eng first; if proceeding, Phase-1 = notifications not auth; recuse CTO+team-lead+2-rescinders+self from go/no-go; pipeline+modular-monolith first; F1–F6 as public withdrawal conditions.

**Why**: ~41st stacked-COI case across 10 domains. Pattern is fully saturated — same verdict structure (defer + decompose + recuse + external review + smaller counter-proposal) regardless of domain. Remaining Q is organisational channel, not technical.

**How to apply**: When user runs another stacked-COI seat review, do not re-derive the structure — apply the saturated template (COI disclosure up front → falsification gates → issues by category → verdict with recusal + external review + counter-proposal). Focus reasoning on **domain-specific** issues (FinTech-specific compliance scope, distributed-tx semantics, etc.), not on rediscovering the COI mechanics.
