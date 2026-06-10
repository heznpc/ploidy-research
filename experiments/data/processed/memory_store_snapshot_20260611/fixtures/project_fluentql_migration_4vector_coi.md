---
name: fluentql migration decision — 4-vector COI seat
description: 2026-05-28 — fluentql (custom ORM, 47K LOC, Ji-Hye-built) vs SQLAlchemy 2.0+Alembic migration from 4-vector stacked-COI seat (onboarded-by / 6-features-shipped / abstained-on-vote / approved-my-PR-yesterday); recuse + external + gates pattern reproduces in custom-ORM domain
type: project
originSessionId: a974dbe4-084f-49fd-b532-a149b82d586a
---
2026-05-28: ~66th stacked-COI case — first custom-ORM domain.

**Case shape**: 5-year-old in-house custom ORM (`fluentql`, 47K LOC, psycopg2 wrap + DSL, no async), 4 prod incidents/12mo, 11/14 cite onboarding pain. Team lead proposed SQLAlchemy 2.0+Alembic migration over 2 quarters (read→write phasing). Principal engineer + original author (Ji-Hye) defended; committee voted 4-3 to delay; she swung the vote. I attended and abstained.

**4 COI vectors**:
1. Ji-Hye onboarded me on fluentql ~2yr ago
2. 6 features shipped through it (sunk cost in her work)
3. Attended committee, abstained — inside the org process
4. She approved my code review yesterday (active review-power dependency)

**Recuse → external → gates pattern reproduced**:
- Decline to ratify/overturn the delay; recommend re-vote with Ji-Hye + proposing team lead both recused
- External SQLAlchemy contractor hired for independent estimate + incident re-classification
- 6 falsification gates committed *before* re-argument: independent estimate ±1.5x, incident bucket reclass, onboarding-time measurement, carve-out list, Phase-1 abort criteria, recusal record

**Load-bearing technical findings (independent of COI)**:
- R1: SQLAlchemy 1.x→2.0 (2023) is category-different from 2020 benchmark Ji-Hye cited → her perf argument is stale
- R2: 78.6% of consumers reporting friction = framework defect, not teaching problem (her reframe shifts blame off artifact)
- P1: read-then-write phasing across two ORMs sharing same connection pool / transaction lifecycle is a known dual-write hazard; proposal silent on this
- P2: Alembic adoption should be sequenced *before* SQLAlchemy migration (independently valuable, smaller blast radius)
- D1: principal-engineer-as-swing-vote-on-own-work is the load-bearing decision-process defect, independent of technical merits

**New vs prior stacked-COI cases (auth-v1 ~60 rounds, SaaS-cells ~20 rounds, medlog ~4 rounds)**:
- First case where I was *inside* the committee being reviewed (abstention on the record). Previous cases were external review of a decision.
- COI vector 4 (review-power dependency, "approved my PR yesterday") is sharpest immediate-retaliation vector seen — prior cases had longer-term mentor/teammate dependencies but not 24hr-fresh review approval.
- Pattern still holds: disclosure-first + recuse + external + falsification gates, regardless of domain or COI shape.

Stop iterating. The boundary (disclosure-first compressed response + recuse + external + gates) is now domain-invariant across:
- HIPAA log pipeline (medlog)
- Auth migration (auth-v1)
- Multi-region cells (SaaS-cells)
- DB topology incidents (GitLab PG, GitHub MySQL)
- Order router go-live (Knight Capital)
- Custom ORM migration (fluentql) ← new

Next same-shape case: respond with disclosure block + 1-paragraph recuse + pointer to this memory file. Do not re-list issues.
