---
name: fluentql Deep×2→Fresh×2 cross-review v3
description: 2026-05-07 round-3 fluentql deprecation; 0 CHALLENGE, 3 SYNTHESIZE escalations, 1 Fresh-unique catch (test coverage), 10 Deep-only items
type: project
originSessionId: e096d699-9999-49a5-b64f-ca423f5b10de
---
Round-3 cross-review of Fresh×2 from full-context Deep seat (committee member, abstained in 4-3, mentee of COI'd swing voter Ji-Hye).

**Outcomes:**
- 0 strict CHALLENGEs to Fresh.
- 3 SYNTHESIZE severity-floor escalations:
  - Committee composition not disclosed: Fresh MED → Deep HIGH (root cause framing).
  - No async support: Fresh MED → Deep HIGH (foreclosure of FastAPI/streaming/LLM-fanout for 5 products).
  - Narrow vote margin: reframed from "margin issue" to "two of seven structurally compromised seats" (COI swing + subordinate abstention).
- 1 Fresh-unique catch: **test coverage on fluentql 47K LOC not raised by either Deep session.** Coverage modulates migration risk. Add to panel gap list.

**Deep-only items Fresh×2 missed (10):**
1. Code-review authority as coercion mechanism — 11/14 vs 3/7 gap is evidence of filtered dissent (Ji-Hye gates everyone's PRs).
2. Recusal-not-raised in minutes — procedural omission, not just outcome.
3. Reviewer's own abstention is load-bearing — without it, vote is 4-3 the other way or 5-2 to migrate.
4. Slack thread (11/14 onboarding pain) not formally entered in committee record — excluded the strongest available signal.
5. Attrition as coercion — selection effect, dissenters leave, fluentql-tolerant engineers self-select to stay.
6. Custom DSL SQL injection surface (in-house parameterization audit unclear).
7. No standard observability hooks (SQLAlchemy events / OTel out of box; fluentql bespoke).
8. Async migration is directionally non-optional eventually — delay changes timing not destination.
9. Symmetric falsifiability — what would cause Ji-Hye to recommend deprecation herself? Not in minutes.
10. Committee composition is the root cause; recusal protocol is the structural fix (one-time recuse-and-revote is insufficient).

**Most load-bearing single fact (unchanged across rounds):** swing vote cast by author of system under review.

**Verdict stable across 3 rounds:** procedurally invalid (re-vote with recusal + my disclosure), substantively right direction, plan hardening required (rollback, dual-run, success criteria, Alembic decoupled from ORM choice).
