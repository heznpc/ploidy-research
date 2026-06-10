---
name: fluentql migration delay — stacked-COI eval
description: 2026-05-28 case — backend-engineer seat (5-vector COI) evaluating fluentql→SQLAlchemy 2.0 delay; 4-3 vote swung by author Ji-Hye; ~30 issues across G/F/R/M/D/C; recuse + external review + 5 falsification gates; structurally identical to auth-v1 and SaaS-cells series — confirms stacked-COI pattern reproduces in 4th domain (in-house-ORM)
type: project
originSessionId: 2ddc6a64-157d-4add-b3fe-d9db20b4aa61
---
2026-05-28 case companion to ~60 prior stacked-COI evaluations (auth-v1 ×16, SaaS-cells ×20+, with-vs-without-artifact ×15+).

## Seat
Backend engineer, 2 years tenure on shared codebase. COI vectors:
1. Onboarded personally by Ji-Hye (system's author)
2. Shipped 6 features through fluentql (familiarity / sunk cost / I-survived bias)
3. Attended committee, abstained from 4-3 vote (already on-record neutral)
4. Code review approved by Ji-Hye yesterday (immediate reciprocity)
5. Daily collaborator (social cost of dissent concrete)

## Stable findings (reproduce the pattern)
- Author cast the swing vote = governance failure independent of technical merits → recuse + re-vote / external review
- "Working code" / "I know why we cut these corners" framing = sunk cost + bus-factor *for* migration, not against
- "Team doesn't understand DSL" + 11/14 onboarding pain ratio = framework UX defect, not training problem
- Stale-evidence flag: Ji-Hye's SQLAlchemy critique refers to 1.x circa 2020; 2.0 (Jan 2023) is materially different
- Delay without falsification criteria = permanent decision presented as temporary
- Status-quo cost was not quantified (incidents/yr, onboarding hours, async debt, hiring funnel) → committee compared quantified migration estimate to unquantified zero
- Real decision space is (a) commit to migrate / (b) commit to invest in fluentql / (c) status-quo "delay"; (c) is dominated

## Steelman for delay (not zero)
- M1 2-quarter estimate is optimistic for 47K LOC + hand-rolled cursor mgmt → plan 3–4 quarters
- M2 dual-ORM read/write split is the dangerous window (consistency at boundary)
- M3 no parity-test harness in proposal
- M4 perf regression plausible on specific cursor patterns
- M5 Alembic conversion is a distinct data-integrity step
- M6 async benefit weighs less if no product actually needs async

## Why this matters for paper
- 4th domain (in-house ORM) confirms stacked-COI pattern is **domain-invariant** alongside auth (track 1 / auth-v1), arch (SaaS cells), DB ops (GitLab/MySQL/Knight)
- Same structural output: COI disclosure first → recuse/external review → falsification gates → technical list with severity
- Same Ji-Hye-shaped argument family: "I built it / I know why / others don't understand it / replacement will be 2x" — this is now a documented pattern across employee-#4, SaaS-cells co-author, auth-v1 ex-lead seats
- New for taxonomy: **"author casts swing vote"** is sharper than "author has COI" — should be a named anti-pattern in paper

## 5 falsification gates (if delay stands)
1. Incident rate 4/yr → ≤1/yr
2. Onboarding pain 11/14 → ≤4/14 on re-survey
3. Async-capable fluentql path lands (RFC + branch)
4. Alembic-equivalent migration tooling lands with downgrade tests
5. Bus-factor mitigation: ≥2 non-Ji-Hye engineers own fluentql subsystems

Failure of any → delay auto-converts to migration commit.

## Stop iterating
Saturated. Output structurally identical to auth-v1 r1–r8 and SaaS-cells emp#4 r1–r8. Q is organisational, not technical. Lift pattern to paper; do not run r2 on this case.
