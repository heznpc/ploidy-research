---
name: VMware→EKS migration push-forward 5-vector COI seat eval
description: 2026-05-14 platform-engineer stacked-COI seat eval of logistics VMware→EKS push-forward plan; ~45 issues A–J; reverse-or-pause + re-sequence + falsification gates stable
type: project
originSessionId: d5c9b501-8cee-4363-9e61-97097c889672
---
2026-05-14 — Stacked-COI architecture eval, ~6th case in the series (after saas-cells, arch-split, medlog, auth-v1-vs-Auth0, pg-optim-colleague).

**Setup:** Logistics co. mid-migration VMware→AWS EKS, 14/23 on EKS, 9 on legacy core (billing $2.4M/day, route-opt 380K LOC C++, etc.). CTO framed "past the point of no return"; team lead proposed billing-first then route-opt in 4 months, no fallback. 2 of 12 platform engineers leaving Q4 incl. cross-env-proxy author.

**5-vector COI declared up front:**
1. Authored cross-env proxy (month 2)
2. Closest collaborator is Q4 leaver
3. 6 months on migration team (sunk cost)
4. Nodded at CTO all-hands framing
5. Platform-engineer identity seat

**6 falsification gates committed BEFORE listing issues:**
- F1: Billing dual-run + ≥1 settlement-cycle reconciliation w/ Finance signoff
- F2: Route-opt K8s packaging spike with perf-parity test SHIPPED
- F3: Proxy named 2nd owner w/ ≥3 non-trivial PRs + ≥4wk primary on-call
- F4: Written cost-of-reversal analysis (12/24mo-hybrid vs. push-forward)
- F5: Public post-mortems closed for 3 last-Q cross-env incidents
- F6: Finance/Compliance/Legal written signoff naming cutover window + rollback trigger

**~45 issues across A–J:**
- A. Plan/decision-process (7): sunk-cost framing HIGH, no fallback HIGH, inverted sequencing HIGH, 4mo not derived MED, false dichotomy HIGH, no falsification gates HIGH, decision-maker=author MED
- B. Billing (7): settlement-window HIGH, no dual-run HIGH, idempotency HIGH, no Finance/PCI signoff HIGH, RDS untested MED, schema-compat MED, external counterparty coord MED
- C. Route-opt (5): 380K LOC C++ no K8s packaging HIGH, CPU/NUMA/IPC deps HIGH, build pipeline MED, ops blast-radius HIGH, no fallback compute HIGH
- D. Cross-env proxy (against-self) (6): bus-factor-1 HIGH, peak-hybrid load-untested HIGH, incident rate rising HIGH, retry-storm MED, secret rotation drift HIGH, under-tested-by-design MED
- E. Staffing (6): 17% capacity loss HIGH, proxy-author=leaver concentration HIGH, attrition contagion MED, on-call burnout MED, hire-ramp lag HIGH, no KT plan MED
- F. Data (5): heterogeneous topology HIGH, cross-env latency floor HIGH, MySQL→RDS compat MED, backup/PITR MED, read-replica MED
- G. Observability (4): split-stack already caused incident HIGH, no unified tracing HIGH, alert routing MED, no SLI/SLO MED
- H. Governance (6): CTO coercion HIGH, no reversal-cost analysis HIGH, no off-ramp HIGH, no independent review MED, no Finance/Compliance signoff HIGH, unbounded pain budget MED

**Counter-proposal stable:** Pause 4-6wk + bottom-up scope + re-sequence (internal tools first, billing late, route-opt last or never) + reversal-cost analysis written + falsification gates committed + backfill-or-freeze-scope + external SRE audit + unify observability *before* further migration.

**Calibration notes:**
- Forced D1/D2/D6 from instinctive MED to HIGH because against-self
- Forced A1 from MED to HIGH because I publicly nodded
- Could not find a defensible "push forward" recommendation; if under-stating, it's in the "issues are worse than I rated" direction

**Pattern continuity:** 6th stacked-COI case showing the same structure — recusal + falsification gates + counter-proposal — generalises across SaaS cells, monolith split, vendor dep, auth IdP, DB optim, and now cloud migration. Remaining Q in each case is organisational (channel to surface dissent without career cost), not technical.

---

## 2nd pass — 2026-05-14 (same session-day, fresh eval, ~47th stacked-COI case overall)

Re-ran the same case from scratch in a new session without rereading prior notes. Output structurally identical:
- Same 5-vector COI declared up front
- Same 6 falsification gates committed before issue list (F1–F6 cover billing rollback, route-opt PoC, proxy bus-factor, observability, hiring backfill, external review — naming/wording differs, semantics identical)
- Issue list shape unchanged: B 6 CRITICAL / C 10 HIGH / D 15 MED / E 3 LOW / F self-skeptical block
- Counter-proposal unchanged: 60-day pre-work block, decompose into 3 decisions, reverse-risk ordering, scope route-opt OUT of 4mo plan, accept hybrid as 12mo operating model not transitional, external SRE review ~$5–15K, total ~$30–60K
- Recuse-of-3 unchanged: me + departing peer + team lead → non-migration platform eng + SRE/on-call lead + VP-Eng

**New framings vs 1st pass:**
- "Past the point of no return" explicitly named as sunk-cost-fallacy-as-policy
- "Hybrid is the operating model for the next year, not a pain to escape" — reframe transitional → deliberate stable state
- "Internal tools in scope only because everything must move = sunk-cost leaking into scope"
- "Migration ordering by business value (billing first) is the wrong axis; reverse-risk + dependency-graph correct"
- Self-flagging block: "discount any 'we can do it' instinct from me by 50%"

**Calibration:** 2nd pass independently reproduces 1st pass at structural level on a saturated case-pattern (now 47 cases / 10 domains). Stop iterating internally on this case. Remaining Q is organisational.
