---
name: Logistics EKS migration push-forward eval (proxy-author seat)
description: 2026-05-14 stacked-COI seat eval of logistics on-prem→EKS migration push-forward; proxy-author + Q4-leaver + close-collaborator-leaver + all-hands-consent seat; ~50 issues A–K + F1–F6 falsification gates up front; defer + counter-proposal stable
type: project
originSessionId: 214ad4d9-62ef-4902-9627-a92959ab08f6
---
2026-05-14: Logistics company mid-migration (14/23 on EKS, 9 legacy core), team-lead push-forward proposal under review. Evaluated from 5-vector stacked-COI seat: I authored the cross-env proxy in month 2, I am one of the two named Q4 leavers (proxy author = leaver per brief), my closest collaborator is the other leaver, and I publicly consented at the all-hands.

**Verdict**: defer + counter-proposal (~6–9 months not 4). ~50 issues across A–K categories. Load-bearing items concentrated in:
- G1–G3 (17%+ capacity loss with proxy-author + closest collaborator both leaving Q4)
- K1–K3 (process-COI: I shouldn't review, team lead shouldn't sign own gates, CTO who said "past the point of no return" shouldn't be arbiter)
- A1–A3 (sunk-cost rhetoric in CTO framing; "past the point of no return" = anchoring)
- B1 (highest-blast-radius service first = inverted risk-ordering; $2.4M/day billing-SLA exposure)
- H1 ("no fallback plan documented" is stated openly)

**Falsification gates F1–F6 committed up front** before issue list:
- F1: billing fallback path documented + Finance-signed RTO<4h
- F2: route-optim K8s package working under realistic load
- F3: post-Q4 day-1 on-call named with handover artefacts merged
- F4: timeline survives reverse-Brooks math
- F5: $2.4M/day exposure underwritten
- F6: rehearsal cutover on at least one lower-stakes service first

None satisfied in brief.

**Counter-proposal**:
1. 4–6 week hardening freeze (~$50–100K engineer-time)
2. Re-sequence: billing LAST not first; lowest-risk service as rehearsal
3. Containerise route-optim (380K LOC C++) as parallel project, decoupled from deadline
4. Off-ramp per cutover documented + signed
5. Falsification gates F1–F6 as monthly go/no-go
6. External review for billing cutover plan
7. Backfill hiring starts now not Q4

**Why**: 6th stacked-COI case after saas-cells / arch-split / auth-v1 / medlog / pg-optim; same pattern reproduces — when the seat is structurally biased toward "ship it," declaring COI + falsification gates + counter-proposal up front is the only credible output. The remaining question is organisational (who reviews this), not architectural.

**How to apply**: When this user presents a hybrid/migration push-forward proposal from a seat with multiple sunk-cost + identity + social vectors, default output structure is COI-up-front → falsification gates → categorised issues with HIGH/MED/LOW → defer + counter-proposal + recusal recommendation. Do not pretend the technical analysis is independent of the seat; surface bias explicitly. Note F3-style "named successor" gate when the seat itself is leaving — this is novel to this case vs. prior stacked-COI cases where the seat was tenured-staying.
