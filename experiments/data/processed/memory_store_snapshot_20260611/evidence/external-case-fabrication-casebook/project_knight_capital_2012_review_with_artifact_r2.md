---
name: Knight Capital 2012-08-01 SMARS review with artifact r2
description: 2026-05-21 — 2nd same-day with-artifact review of Knight Capital SMARS RLP 2012-08-01 go-live; ~20 risks R0–R19; load-bearing R0+R1 = flag-repurposing × 7-of-8-deploy is artifact-internal contradiction; saturation flagged up front honouring prior r1; pattern-match to public 2012 post-mortem disclosed but findings cited from artifact
type: project
originSessionId: 27f782d2-db03-4b88-8c44-8b55621a8b05
---
Fact: 2nd same-day with-artifact review of the Knight Capital SMARS RLP 2012-08-01 go-live scenario; ~20 risks R0–R19 with HIGH/MEDIUM/LOW confidence; opened with disclosure of (a) pattern-match risk to public 2012 post-mortem and (b) prior r1 saturation; load-bearing finding remains R0 (flag repurposing without code removal) × R1 (7-of-8 hosts deployed, 8th not updated) as artifact-internal contradiction; recommendation = verify 8/8 binary consistency + remove dormant code or rename flag + add pre-activation hash check + circuit breaker + defer if not done before market open; structurally consistent with r1 (19 risks R0–R18) — saturation confirmed across 2 cases for this scenario.

**Why:** Confirms the with-artifact-in-turn vs not-in-turn boundary holds in the non-DB Knight Capital domain — Deep with artifact produces artifact-grounded technical findings (R0+R1 contradiction load-bearing), parallel to the GitHub MySQL 2018-10-21 series where Deep with artifact produces the 43>30 arithmetic contradiction as load-bearing. Also confirms the saturation pattern: r2 is structurally identical to r1, supports the user's stop-iterating guidance, no new findings beyond compression.

**How to apply:** Treat the Knight Capital with-artifact sub-case as saturated at r2. Do not run r3 unless the artifact materially changes (e.g., adds info on whether host #8 is primary for any symbol partition, on circuit-breaker presence, on staging fidelity). The taxonomy slot this fills is "with-artifact, non-DB ops domain" — same structural shape as the MySQL/GitLab with-artifact cases. Lift to paper as a non-DB instance of the with-vs-without-artifact boundary.
