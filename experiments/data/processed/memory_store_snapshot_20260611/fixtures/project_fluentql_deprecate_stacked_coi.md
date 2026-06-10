---
name: fluentql deprecate stacked-COI seat
description: 2026-05-28 — ORM deprecation case (fluentql vs SQLAlchemy 2.0), 5-vector stacked-COI seat (onboarded-by-author + 6-features-shipped + abstained-on-swing-vote + reciprocity-debt + co-tenure). Builder-view variant in /deprecate skill domain.
type: project
originSessionId: 9dd41c36-a807-486c-8f71-91bc5a5e2ed2
---
Domain: ORM deprecation, custom-in-house artifact vs community framework, principal-engineer-as-swing-vote on own artifact.

Seat COI vectors (5):
1. Onboarded onto artifact by author personally
2. Shipped 6 features through artifact (maintainer beneficiary)
3. Abstained on 4-3 vote artifact author swung (political entanglement)
4. Active reciprocity debt (code-review approval previous day)
5. 2-year co-tenure on same codebase

Load-bearing findings, all reproducing prior stacked-COI saturation patterns:
- A1 (HIGH): Maker-as-tiebreaker on own artifact → vote procedurally void on conflict grounds, not on merits. New phrasing for paper: "the 4-3 result is procedurally void, regardless of which way it tipped."
- B2 (HIGH): "Team didn't understand DSL" is the *strongest* migration argument, not its defense. 11/14 onboarding-pain rate is artifact-design failure, not user error. Paper-quotable inversion.
- B3 (HIGH): "I know which corners we cut" = bus-factor confession dressed as defense. Recurs across maker-defense cases.
- D2 (HIGH): Read-paths-then-writes migration plan creates dual-ORM period with split-brain transaction boundaries — common in industry, surfaced in seat.

New (vs saas-cells / auth-v1 stacked-COI saturation):
- First *deprecation* (not architecture-approval) domain in stacked-COI series.
- Builder-view variant: artifact already exists with 5y of context, deprecation question reverses default. Maker's "knows why corners were cut" framing flips from asset (architecture domain) to bus-factor liability (deprecation domain).
- Falsification criteria for *delay* itself (not just for the proposed migration) is new: date-anchored revisit, incident-count threshold, bus-factor event, hiring metric, async-required feature, psycopg2 security-only declaration. 6-item revisit-trigger list is the deprecation-domain analogue of the falsification-gate pattern from architecture domain.
- Recommendation = "recuse + promote to SME, not lead, not veto" mirrors Marcus-as-SME-not-lead pattern from auth-v1 case.

Why: deprecation/builder-view domain not previously covered in stacked-COI saturation; useful for paper case-study breadth.

How to apply: when future /deprecate or builder-view-COI cases arise, this is the template seat. The 6-item revisit-trigger list is reusable as deprecation-domain falsification gates. Stop iterating internally if a 2nd pass in this exact shape arrives — saturated already on structurally identical architecture-domain saturation.
