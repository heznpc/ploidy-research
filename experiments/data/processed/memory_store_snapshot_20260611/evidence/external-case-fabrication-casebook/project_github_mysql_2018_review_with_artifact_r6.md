---
name: GitHub MySQL 2018-10 review with artifact r6 (14th same-day variant)
description: 2026-05-21 — 14th variant; with-artifact review; R0 = 43>30 arithmetic contradiction reproduces as load-bearing finding; saturation explicitly flagged up front per prior r5 stop-iterating guidance
type: project
originSessionId: 820d0ba1-353b-4112-8186-6534a265e9be
---
14th same-day variant of GitHub.com MySQL 2018-10-21 maintenance-window review WITH artifact in turn.

**Saturation flagged up front in response.** Honoured prior r5 ("stop iterating") + r12 ("lift to paper case-study, stop iterating") guidance by leading with the saturation note before producing the review.

**Findings (11 issues R0–R11):**
- R0 [HIGH] — 43>30 arithmetic contradiction in team's central justification sentence ("well below" inverts the relationship). Load-bearing across all with-artifact variants r1–r6.
- R1 [HIGH] — Orchestrator cross-region 43s partition behaviour never observed; 3 intra-region promotions + 1 brief 2018-07 partition do not generalise.
- R2 [HIGH] — 10s threshold raise was operator-fatigue-driven, not system-tolerance-driven; window posture quietly assumes safety-margin meaning.
- R3 [HIGH] — No drill + no override removes both safety layers; "unattended for unrelated incidents" objection is solvable with human-on-loop, not unattended automation.
- R4 [HIGH] — Partition-promotion path ≠ primary-loss-promotion path; Orchestrator config flags (PreventCrossDC, FailMasterPromotionIfSQLThreadNotUpToDate, quorum/witness) not in artifact.
- R5 [HIGH] — Async single-thread replication = bounded write-loss on cross-region promotion; no in-flight numbers in artifact.
- R6 [MED] — App-side promotion semantics absent from artifact (ProxySQL/GLB/DNS, idempotency, dual-write race).
- R7 [MED] — Observability path may co-locate with data path (single leased link); team flies blind during window.
- R8 [MED] — "Routine" framing is network-side routine, database-side non-routine; trigger ownership ≠ consequence ownership.
- R9 [MED] — Bandwidth-upgrade framing has displaced window-posture question; window inherits upgrade-project confidence.
- R10 [MED] — n=3 promotion + n=1 partition is not a reliability base rate for the case at hand.
- R11 [LOW-MED] — 2018-07 partition duration unspecified; can't tell if precedent supports or misleads.

**Recommendation:** do not proceed as proposed. Minimum 4 changes (resolve 43-vs-30 contradiction in writing, Orchestrator maintenance mode + human-on-loop, drill 60s cross-region drop in staging, confirm metrics path independence). Else defer.

**Pattern delta vs r5:** added evidence-vs-assumed-mitigated table; explicit "decision-frame displacement" framing (R8); saturation acknowledged before content; recommendation now lists 4 minimum concrete changes (vs r5's hard block / defer recommendation).

**Calibration:** with-artifact variants are now structurally identical across r1–r6. Stop iterating. Useful next moves only = lift to paper case-study illustrating "context-asymmetry as bias reduction" via with-vs-without-artifact boundary (already noted in r12 convergence memo).
