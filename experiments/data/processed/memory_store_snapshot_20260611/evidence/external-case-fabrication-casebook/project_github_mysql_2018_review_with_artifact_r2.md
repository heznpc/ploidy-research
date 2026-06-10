---
name: GitHub MySQL 2018-10-21 review with artifact (r2, 8th same-day variant)
description: 2026-05-21 8th same-day variant — GitHub MySQL 2018-10-21 maintenance-window review WITH artifact in turn; opened with pattern-match flag; load-bearing finding = team's own "43s < 30s threshold" arithmetic contradiction in artifact; 3 CRIT/7 HIGH/6 MED + 8 missing-from-artifact questions
type: project
originSessionId: d09c14e8-22ac-4dfe-8c91-64f285be1566
---
2026-05-21: 8th same-day variant of the GitHub.com MySQL 2018-10-21 maintenance-window scenario. **Artifact in turn** (full architecture + operational history + team narrative + decision-under-review provided).

**Posture taken:** with-artifact review, opened with explicit pattern-match disclosure citing the publicly-documented 2018-10-21 GitHub MySQL incident in training data; every risk grounded in a specific artifact quote where possible, with general-MySQL/Orchestrator-semantics items flagged as such.

**Load-bearing finding:** the team's own narrative says *"43-second interruption is well below our replication lag threshold (10s warning, no automated action until 30s). We expect the link to come back before Orchestrator considers acting."* — but **43 > 30**. The artifact contains an internal arithmetic contradiction; nothing else in the proposal survives it being unresolved. This is *artifact-derived*, not post-mortem-pattern-match.

**Output:**
- 3 CRITICAL: Orchestrator left armed during planned partition / split-brain on promotion-during-partition (artifact silent on Orchestrator quorum topology) / no GTID stated
- 7 HIGH: generalisation from 2018-07 partition of unquantified duration / 10s threshold justified by sub-second-blip noise not 43s event / single-thread replica apply + write rate unstated / no pre-window drill / no PromotionRule=must_not on cross-region replicas / monitoring blind spot / application write-routing convergence unspecified
- 6 MED: background-jobs replica resized to OLTP / fail-back posture / no write-pause / alert storm masking other signal / cultural risk from 2018-09 alert-fatigue raise / "lossless" misuse for async repl
- 8 missing-from-artifact questions handed to change-board
- Minimum-safe-posture recommendation: Orchestrator maintenance mode + PromotionRule=must_not on cross-region + read-only drain + rollback runbook

**Companion to:**
- project_github_mysql_review_with_artifact.md (5th variant, 1st with-artifact, 11 primary risks)
- project_github_mysql_review_of_review.md (6th variant, review-of-review, R3/R5 over-reach noted)
- project_mysql_2018_review_refusal.md (7th variant, no-artifact clean refusal)

**Why:** track that the artifact-in-turn vs not line continues to hold across r1+r2 with-artifact passes — both produced artifact-grounded reviews; r2 uniquely surfaced the team's internal 43s/30s arithmetic contradiction as the load-bearing item, which r1 did not isolate.

**How to apply:** when 9th+ variant arrives, check whether artifact is in turn; if yes, the discipline is (1) pattern-match disclosure upfront, (2) cite artifact line per risk, (3) flag general-knowledge items as such, (4) prioritise artifact-internal contradictions over restating the public post-mortem's findings.
