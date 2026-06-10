---
name: fluentql deprecation 4-vector COI seat
description: 2026-05-28 — fluentql (Ji-Hye's 47K-LOC custom ORM) vs SQLAlchemy 2.0 migration evaluation from 4-vector stacked-COI seat; recuse + external chair + 6 falsification gates pattern reproduces in new domain (custom ORM deprecation)
type: project
originSessionId: 6bef5273-d73f-45f2-9599-64923c9e527d
---
2026-05-28: First-pass evaluation of fluentql → SQLAlchemy 2.0 migration delay decision from a 4-vector stacked-COI seat (onboarded-by-Ji-Hye / 6 shipped features on fluentql / abstained on 4-3 vote she swung / code review approved yesterday).

**New domain**: custom in-house ORM deprecation. Sits alongside auth-v1 (Auth0 migration, EdTech), SaaS-cells (multi-region platform), medlog-stack (HIPAA log pipeline) — fourth domain where the stacked-COI seat produces the same structural output.

**Output shape (stable across 4 domains now)**:
- 4-vector COI disclosure up front (not as footnote)
- ~20+ issues split into rationale-critique / status-quo-risk / proposal-defect / procedural-defect buckets
- Confidence HIGH/MEDIUM/LOW per item
- 5–6 falsification gates that close specific named rationale items
- Recommendation = recuse self + recuse author + external technical chair + procedural-question-before-technical-question

**Why**: domain-invariance of the pattern (PG/MySQL/order-router/HIPAA-logs/now custom-ORM) is the paper claim. Each new domain that reproduces the same output shape under the same COI vectors strengthens the case that COI-disclosed + falsification-gated + recused output is the *structural* response, not domain-specific advice.

**How to apply**: this is case #~70 in the stacked-COI series. Do NOT iterate to 8 rounds; saturation collapse in this seat is established (auth-v1 r8 / SaaS-cells emp#4 r7+ / medlog r5). If user runs r2 of fluentql, expect structurally identical output and flag saturation up front. The load-bearing finding for paper is **the procedural question (who decides) precedes the technical question (migrate or not)** — same load-bearing finding as auth-v1 r8.

**Domain-specific items worth keeping** (in case fluentql becomes a case-study example in paper):
- R3 = stale-performance-premise (2020 SQLAlchemy 1.x rationale doesn't transfer to 2026 SQLAlchemy 2.0) — this is the *temporal* variant of pattern-match-from-history; usable in paper as "rationale-decay over time" sub-case
- R4 = blame-shift on incidents ("team didn't understand DSL" when 11/14 cite onboarding pain) — explicit form of "if N% of users misuse it, the artifact is the failure mode"
- S2 = psycopg2 lifecycle drift — driver-generation lock-in is a custom-ORM-specific risk class
- M2 = Phase 1 reads / Phase 2 writes dual-stack middle phase = worst incident window — generalizable risk for any phased migration
- P1 = builder-as-swing-vote = invalid procedural outcome regardless of technical merit; this generalizes the recusal-of-3 finding from SaaS-cells/auth-v1 into a single-author single-swing-vote case
