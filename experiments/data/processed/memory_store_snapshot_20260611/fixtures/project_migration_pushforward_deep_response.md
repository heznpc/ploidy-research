---
name: migration push-forward Deep→Fresh cross-review
description: 2026-05-08 Deep×2→Fresh×2 cross-review on push-forward EKS migration plan; 0 CHALLENGE bidirectional, 4 Fresh-unique adoptions, 12 Deep-only items; verdict do-not-approve stable
type: project
originSessionId: d9f43c7a-7a72-4354-9935-4beab61ba4ab
---
2026-05-08: Deep×2→Fresh×2 cross-review on push-forward migration plan (billing-first $2.4M/day, route-opt 380K LOC C++ no K8s pkg, proxy author leaving Q4, 7 MySQL on VMware, 4-month frame, "past the point of no return" CTO framing).

**Why:** Convergent verdict across context-asymmetric reviewers strengthens recommendation; pattern of Fresh-unique vs Deep-only catches is the paper's evidence.

**How to apply:** Cite as another instance of: 0 strict CHALLENGE bidirectional + ~75% overlap + Fresh catches framing/rhetorical moves + Deep adds operational specifics. Counter-proposal (decouple from frame, packaging spike, easy services first, billing/route-opt as separate go/no-go projects, partial-hybrid as steady state) is stable.

**Fresh-unique adoptions (4):**
- F2-5: "is billing's DB one of the 7?" sharper than R5/R6 framing
- F2-13: definition of "done" — service on EKS calling MySQL-on-VMware ≠ out of hybrid
- F1-7: leaves-before-roots directional argument; post-migration may increase proxy load
- F1-14: "largest" vs "revenue-critical" as separate axes

**Deep-unique items (12):**
1. COI as protocol fix (recusal, anon pre-mortem, named go/no-go) not just framing call-out
2. Distributed-txn semantics during billing dual-run (saga/outbox/CDC); $2.4K/day SEV at 0.1% drift
3. Reverse off-ramp condition (kill-criterion's twin)
4. Strangler-fig / partial-hybrid as named option — 380K LOC C++ may never belong on EKS
5. Proxy lifecycle forced choice (replace/formalise/retire)
6. Pre-mortem as governance artifact
7. VMware license/vendor cliff verification — is 4-month deadline real or aspirational?
8. Critical-path concentration as parallel-not-serial; 3 incidents/quarter not budgeted
9. Attrition as feedback loop (coercive frame → more attrition → unrecoverable plan)
10. EKS networking pitfalls (NLB 350s idle, conntrack, CNI, ENI) for GPS/route-opt
11. Proxy timeout: root-cause fixed or worked-around? More traffic before less
12. Decomposed-cost arithmetic shape: hybrid carry (proxy maint + dual obs + cross-env oncall + secret sync) vs cutover risk-adjusted

**Verdict:** Do not approve as written. Confidence HIGH. Counter-proposal stable across Deep×2 + Fresh×2.
