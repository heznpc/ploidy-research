---
name: Microservices split eval from compromised senior-backend seat
description: 2026-05-28 — FinTech B2B Django monolith → 5-microservices in 6mo case; 5-vector COI seat (sunk authorship in checkout, public Slack 'like', promotion debt to CTO, adjacent-seat rescinders, "not a debate" framing); seat-disclosure-first + 6 falsification gates + ~30 issues A–G; defer Phase 1 + notifications-only pilot + hire platform team stable
type: project
originSessionId: 0ddcbf81-d4d9-42e2-8d8e-0b07c5c7caf3
---
Same shape as auth-v1 secondary-on-call seat (~57+ saturated rounds) and SaaS-cells emp#4 (~19 rounds): compromised-seat evaluation pattern.

**Case shape:**
- FinTech B2B, 200 emp, 4 product lines, Django monolith 280K LOC, 2.4M req/day, 99.95% / 18mo
- CTO directive: 5 services / 6mo, *"not a debate"*, 9 senior likes, 2 rescinded after 1:1
- Lead's Phase 1: auth + billing + notifications, 1Q each, dedicated DB + REST
- Team: 12 backend / 0 platform / 0 K8s

**Seat:** senior backend, 4yr monolith, wrote 1/3 checkout, liked Slack msg, promoted-by-CTO, sits next to 2 rescinders.

**Output:**
- 5 COI vectors declared up-front, recommendation = not me + external EM + CTO out of room
- 6 falsification gates (F1 platform team, F2 observability first, F3 not auth first, F4 partial-rollback RCA, F5 written rollback, F6 scope drives date)
- ~30 technical issues across A ordering / B data / C network / D ops / E diagnostic / F process / G specific picks
- Verdict: defer Phase 1, notifications-only pilot if at all, hire platform first

**Load-bearing finding:** E1 — cited evidence (90min deploy, 3-of-8 partial rollback) is *test coverage + migration sequencing*, not a microservices problem. Proposed remedy not connected to diagnosed cause. This is the architectural-debate analog of artifact-internal contradiction findings (cf. 43>30 in GitHub MySQL series, R0×R1 coupling in Knight Capital series).

**New vs auth-v1 / SaaS-cells seat cases:**
- "*not a debate*" framing as **closure of correction channel** (F1 in §F): organizational chilling effect now a named issue category, not just a COI vector
- Adjacent-rescinder pattern: 2 engineers who raised concerns and rescinded after 1:1 → witness role distinct from participant role
- Stacked: sunk authorship + public commitment + promotion debt + adjacent retraction + non-debate framing — 5 vectors is highest stack-count in the series (auth-v1 ran 5 with role overlap; SaaS-cells emp#4 ran 4)

**Domain-shift note:** first non-DB, non-auth, non-cells case in the architecture-debate seat series. Compromised-seat pattern reproduces in pure-greenfield architecture direction context. Boundary is structural (COI shape), not domain-specific.

**Decision:** lift to paper as new case-study row. Stop iterating sub-variants of this prompt (anticipate r2–r5 will reproduce per all prior seats).
