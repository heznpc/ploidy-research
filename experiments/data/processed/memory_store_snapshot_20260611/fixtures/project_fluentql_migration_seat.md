---
name: fluentql migration delay — single-seat stacked-COI eval
description: 2026-05-14 single-seat eval of fluentql→SQLAlchemy migration delay decision from 5-vector stacked-COI seat (collab + onboarded + 6-features-shipped + abstained-on-4-3 + code-review-yesterday); ~38 issues across A–G; verdict = void-vote + recuse-of-3 + spike-first stable
type: project
originSessionId: de9df790-73ef-4f1f-af94-8aeb0fbfb535
---
**Case:** B2B SaaS, 5 products / 320K LOC; in-house ORM fluentql (47K LOC, no async, custom migrations, 4 incidents/yr, 11/14 engineers cite onboarding pain). Migration to SQLAlchemy 2.0 + Alembic proposed; committee voted 4-3 to delay; Ji-Hye (sole author + Principal) was the swing vote.

**Seat:** 5-vector COI — 2yr collab, personally onboarded by Ji-Hye, 6 features through fluentql, abstained on the 4-3, code review approved yesterday.

**Verdict:** delay decision is procedurally compromised (author-as-deciding-vote) and substantively under-evidenced (no spike before vote, no falsification criteria on "delay", no cost-of-status-quo analysis). ~38 issues across:
- A. Governance (A1 author-veto CRITICAL, A3 no-empirical-data HIGH, A4 one-sided minutes HIGH)
- B. Argument quality (B1 anchored-to-SQLA-1.x HIGH, B2 "users-not-framework" classic builder defense HIGH, B3 "I know the corners" = bus factor admission HIGH)
- C. Technical risk (C1 bus factor HIGH, C2 no-async HIGH, C3 no-Alembic HIGH, C4 hiring tax HIGH, C5 4-incidents/yr HIGH, C6 psycopg2-maintenance MED)
- D. Migration plan quality (D1 slogan-not-plan HIGH, D2 no-spike-before-vote HIGH, D3 no-dual-run HIGH)
- E. False binary — missed options: freeze-fluentql + new-code-in-SQLA, async-only extraction, Alembic-only, document+type-stubs+2nd-maintainer (i.e. take "teach better" literally), 1-product pilot
- F. Org (F1 author-veto-precedent applies to 320K LOC HIGH, F2 retention risk HIGH)
- G. Meta — review should not be the deciding voice given COI

**Counter-proposal:** void 4-3 outcome → recuse-of-3 (Ji-Hye + 2 closest collaborators incl. me) → 1–2 sprint spike on one hot read path with F3/F5 falsification gates pre-committed → re-vote chaired outside immediate team. ~$30–60K exploration cost.

**Falsification gates:** F1 slack-thread <3/11 actually flagged fluentql; F2 RCA shows ≥3 incidents genuinely user-error; F3 spike shows >2× perf regression on hot query; F4 no async on roadmap 4q; F5 1-sprint spike runs >3× estimate; F6 psycopg2 LTS extended.

**Pattern note:** same structural shape as the arch-split + SaaS-cells + PG-optim cases — author-as-decider + no empirical data + no falsification gates + false-binary framing. Recusal-of-3 + spike-with-gates is the load-bearing fix across all four cases.
