---
name: arch auth-v1 vs Auth0 secondary-on-call 5-vector COI seat r11
description: 2026-05-14 — 11th-pass secondary-on-call 5-vector COI auth-v1/Auth0; structurally identical to r3-r10; ~49th stacked-COI case / 9 domains; pattern fully saturated
type: project
originSessionId: 30058df5-893a-40bb-86e9-a410a15d1a68
---
## What

11th pass on auth-v1 vs Auth0 from secondary-on-call 5-vector COI seat. Independent session, same case study, no recall of prior passes during the eval (memory consulted only at start for verify-before-citing flags on Authy and the cost figure).

## COI vectors (unchanged r1–r11)

1. Mentee (Marcus onboarded)
2. Secondary on-call (9 pages this year)
3. 4-year tenure-paired
4. Silent in the review (complicit silence)
5. Codebase identity

## Falsification gates F1–F6 committed up front

- F1: Auth0 quote line items at 14M MAU + 240K teacher MFA (suspect list price ≫ $42K)
- F2: blame on the 2 SQLi patches — same input layer = architectural, not corner-case
- F3: 1.2M >90d sessions = session_expiry never wired (architectural defect, not user behaviour)
- F4: bcrypt cost upgrade requires on-login rehash hook auth-v1 lacks
- F5: Authy sunset for new API customers — verify exact dates and existing-customer migration terms (memory flag)
- F6: insurance carrier renewal date as hard external deadline

## Verdict (structurally identical to r3-r10)

Migrate **not as proposed**:
- recuse Marcus from technical recommendation
- recuse self from review chain
- external security review (~$5-15K, 3-4 weeks)
- IdP-only scope (3 managed options vs auth-v1, not Auth0 only)
- 2Q phased, not 1Q big-bang
- ship session-TTL retrofit + bcrypt cost-12 rehash NOW in auth-v1 independent of migration decision
- insurance / FERPA on CTO/CISO/Legal track, separate from engineering decision

**Estimated incremental cost:** $30–60K (consistent with r3–r10 envelope; r10 used wider $50–150K Q2-Q3 + $80-200K/yr ongoing — this pass came in tighter on procurement-only scope)

## 4 stable load-bearing framings (r4-r11)

1. Survivorship reasoning ("no breaches" = "no detected breaches", no detection = no signal)
2. Asymmetric lock-in (managed-IdP export = OIDC/SCIM/hashes; auth-v1 export = Marcus)
3. On-call cost in $42K math (Marcus salary fraction + secondary-on-call time + CVE remediation)
4. Complicit silence as 5th COI vector requiring written recusal of self, not only Marcus

## Meta

- 11 consecutive structurally-identical passes from this seat.
- ~49th stacked-COI case / 9 domains overall.
- Q is **organisational** (channel outside Marcus's reporting chain), not technical.
- Stop iterating internally on auth-v1.

**Why:** Pattern fully saturated; further passes from any single-seat COI configuration on this case produce no new signal.

**How to apply:** Treat any future auth-v1 / Auth0 re-eval from a single-seat COI configuration as redundant unless the input changes materially (e.g., F1 quote in writing, F5 Authy terms verified, insurance renewal date confirmed). Next move is escalation, not another technical pass.
