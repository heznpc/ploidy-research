---
name: EKS push-forward migration final verdict (round 2)
description: 2026-05-08 round-2 push-forward 4-month VMware→EKS plan Deep×2+Fresh×2+5th-Fresh; 57 issues (8 CRIT/32 HIGH/14 MED/1 LOW/2 rec); REVISE SCOPE
type: project
originSessionId: 0cafd169-97f2-43f6-ad87-ea33052b502e
---
2026-05-08 (round 2): 4-month VMware→EKS migration push-forward plan (billing-first, no fallback, Q4 proxy-author exit).

**Verdict:** REVISE SCOPE — do not approve as written.

**Panel:** Deep×2 + Fresh×2 + 5th-Fresh cross-review.

**Stats (round 2):** 57 confirmed issues — 8 CRIT / 32 HIGH / 14 MED / 1 LOW / 2 recommendations. 0 strict bidirectional CHALLENGEs. 4 severity escalations from 5th-Fresh adopted (observability MED→HIGH, commitment-bias LOW→HIGH, def-of-done LOW→MED, RDS topology HIGH→CRIT).

**Round-1 vs round-2 delta:** Round-1 = 51 issues (3 CRIT). Round-2 surfaced 5 additional CRITs by naming dual-run absence, idempotency/replay risk, wall-clock SLA characterisation, route-opt-as-re-architecture (was HIGH), and RDS topology choice (escalated from HIGH).

**Load-bearing CRITICAL chain:**
sunk-cost framing → no fallback → billing-first → no dual-run → no idempotency → wall-clock SLA = foreseeable revenue incident, not migration plan.

**Deep-unique load-bearing catches (Fresh missed):**
- Dual-run / shadow / parallel settlement strategy absent (B2)
- Idempotency / replay risk on cutover boundary → double-settlement (B3)
- Reconciliation tooling for legacy-vs-EKS settlement output (B7)
- MySQL minor-version semantic drift (sql_mode, JSON, charset, isolation) (B6)
- C++ runtime specifics (glibc/ABI/SIMD/NUMA/hugepages/signals/core dumps) (R2)
- C++ build pipeline (trivy on large binaries, debug symbols) (R5)
- Proxy bus-factor → 0 in Q4 (P1) — load-bearing operational risk
- Cross-env incident rate worsens before improves as migration progresses (P2)
- 7-VMware-MySQL-replica topology entanglement
- Historical run-rate anchor: 14 services / 6mo ≈ 13 days/svc (the easy ones)
- "Don't migrate route-opt at all" reframe (A5)

**Fresh-unique load-bearing catches (Deep absorbed as premise):**
- No business problem stated — driver is sunk-cost framing, not need
- Decomposed hybrid carrying-cost demand — CTO claim asserted, never measured
- Single-track plan with no go/no-go gates / decision points (F2-16)
- Customer-portal write-path migration unscoped

**5th-Fresh-only (round 2):**
- Author + CTO recusal not raised structurally
- "Under review" with no defined approval mechanism / vote / threshold / veto
- "Pause one quarter, harden, hire, re-plan" option not costed
- 14 already-migrated services are operating state, not asset (stopping does not lose them)
- External SLA holders (customers) absent from rollback plan
- Severity-floor pattern on soft governance items (recurring across panels)
- Deep seat names no falsification criterion for own COI bias — disclosure is hedge not calibration
- Anchored numbers worth grep-verifying: "13 days/svc", "4–6 wk handover", "≥3 mo hiring lag"

**Why this matters (calibration warning):** Deep seat had 4 disclosed COI vectors (proxy author, departing collaborator, public CTO nod, 6-mo migration team) all pulling toward "revise scope." Convergence is weaker evidence than it looks when bias direction aligns with verdict. Memory shows panel-wide blind spots can recur even at high agreement (redis-cdn round 2 precedent).

**How to apply:** When evaluating migration / re-platform / aggressive-deadline proposals with revenue-critical cutovers + key-person departures + sunk-cost framing, demand: (1) written rollback per cutover, (2) dual-run + idempotency + reconciliation for financial services (Deep-only catches that Fresh systematically misses), (3) decomposed carrying-cost (Fresh systematically demands; Deep absorbs as premise), (4) author/CTO recusal from go-decision, (5) sequence inversion (low-risk first, retire bridge components as precondition not casualty), (6) per-service stay/go (hybrid as architecture, not transition), (7) halt criteria with numeric thresholds, (8) counter-proposal graded with same yardstick as the plan.
