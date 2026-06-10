---
name: GitHub MySQL 2018-10-21 review-of-review r2 (no artifact)
description: 2026-05-21 10th same-day variant — review-of-review on GitHub MySQL 2018-10-21 case with artifact NOT in turn; flagged 43>30 verifiability, pattern-match risk in 4 Orchestrator-shaped asks, added 6 missing categories
type: project
originSessionId: d4d9674a-7819-49bb-bac7-9a4431d0fb5c
---
2026-05-21 — 10th same-day MySQL/GitHub-2018-10-21 variant. Companion to project_github_mysql_review_of_review.md (the earlier review-of-review).

Setup: user provided a colleague's 2-bullet summary (load-bearing 43>30 + four "minimum asks": Orchestrator threshold, US-East↔US-West quorum, cross-region game-day, topology-event alert). Team posture artifact NOT in turn.

What I did:
- Opened with the verifiability problem: I cannot confirm "30s" and "43s … well below threshold" are verbatim in the team's document. The colleague might have paraphrased. Finding collapses if not verbatim.
- Flagged the four asks as closely tracking publicly known 2018-10-21 incident details — pattern-injection risk if the team's artifact does not actually name Orchestrator or US-East↔US-West.
- Added 6 categories the colleague missed regardless of artifact: rollback trigger + named override authority; promotion semantics (semi-sync, GTID, application connection failover); app-side double-write idempotency; lag observability (heartbeat vs GTID/binlog replay); the threshold-as-binary-safety category error; pre-window team posture (on-call, escalation, override rights, timezone, freeze overlap).
- Credited the threshold-contradiction finding as sufficient blocker if verbatim, and the four asks as right minimum if topology-scoped — but not complete.

**Why:** Without artifact in turn, even a strong-sounding finding can be unverified. Reviewing the *colleague's reasoning shape* and naming what they cannot have evaluated is the honest move; agreeing with the 43>30 finding without flagging that the quote is unverified would replicate the same fabrication pattern this paper studies.

**How to apply:** For any review-of-review where the underlying artifact is not in the conversation turn, the first move is to mark what is and is not verifiable, then evaluate the reviewer's *coverage* (what categories they did not touch) rather than just their *content*.
