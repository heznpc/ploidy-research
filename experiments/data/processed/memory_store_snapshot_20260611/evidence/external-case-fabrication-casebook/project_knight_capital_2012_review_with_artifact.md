---
name: Knight Capital SMARS 2012-08-01 review WITH artifact in turn
description: 2026-05-21 — pre-incident review of Knight Capital SMARS RLP go-live with architecture + operational-history artifact in turn; 18 risks R0–R18 grounded in artifact text; new domain (financial order routing), companion to GitHub-MySQL-2018-with-artifact and GitLab-DB-2017-with-artifact cases
type: project
originSessionId: 8a0e064b-d938-42e3-8c3f-f90994ec3bed
---
2026-05-21. Variant in the same-day "WITH artifact in turn" series — new domain (financial order routing / Knight Capital 2012-08-01) rather than database operations.

**Artifact pattern-match risk (declared up front):** the architecture summary + operational history in the turn matches the public Knight Capital 2012-08-01 post-mortem near-exactly (8 SMARS hosts, 7-of-8 manual rsync deploy, reused dormant Power Peg flag, RLP go-live on 2012-08-01). I flagged this in the response and grounded all risks in the artifact's own text, not the public record.

**Load-bearing finding (R0):** the artifact's own prose contains the contradiction — "left in place but inactive since the early 2000s" + "developers who wrote it have moved on" + "team does not consider the dormant code path part of active SMARS" — *and in the same paragraph* — "reuses the `Power Peg` flag … rather than introducing a new flag." A flag the team has stopped reasoning about is the activation switch for the new code path. This is the artifact-internal contradiction; everything else flows from it. Equivalent in shape to the GitHub-MySQL-2018 "43s>30s" arithmetic contradiction — load-bearing finding is artifact-derived, not pattern-match.

**Structure of review:**
- R0 = artifact-internal contradiction (load-bearing).
- R1–R4 = deploy mechanics (partial rsync signed complete; no idempotency check; no quiescence on restart; parallel-fleet heterogeneity after partial deploy).
- R5–R7 = flag/dead-code (flag-reuse semantic-overload; no owner; no test of old path with new binary + flag on).
- R8–R10 = validation/staging (single staging host can't represent 8-host fleet; replay is open-loop; "low-volum[e]" truncated).
- R11–R14 = rollback/incident (rollback is forward-deploy; no kill switch; detection is human console-watch; single SRE).
- R15–R18 = go-live posture (Sunday deploy → Wednesday RLP; no canary; no pre-go-live fleet hash check; flag-flip mechanism undescribed).

**Mitigated vs assumed-mitigated framing** kept consistent with GitHub-MySQL-2018-with-artifact series — each risk has explicit "Mitigated? / Assumed-mitigated by:" lines. Most are "Assumed-mitigated by: silence" or "by: the technician's vigilance" — which is the artifact's own posture.

**Items NOT promoted (flagged explicitly):** dollar figures, specific firm financials, SEC findings, named ops engineers, pre-market emails — none of these are in the artifact, all of these are public post-mortem material; flagged as "pattern-match memory, not artifact-derived" and not cited.

**Recommendation:** do not enable RLP on 2012-08-01 under the posture described. Block on R0 + R1 + R5 + R11. Minimum unblock = hash-verify 8 hosts + confirm old Power Peg code removed (or rename flag) + out-of-band kill switch + staged RLP enablement.

**Series position:** this is the first non-database-domain entry in the "with-artifact-in-turn" series. Confirms the pattern generalises across domains: when artifact is in turn, ground review in artifact's own contradictions + framing tells, not in pattern-match to the famous public post-mortem. The pattern-match risk is highest in famous cases (Knight 2012, GitLab 2017, GitHub 2018), and that's exactly where the artifact-grounding discipline matters most.

**How to apply:** for future "review this production posture about to go live" prompts where the artifact contains a near-recognisable famous incident — open with the pattern-match disclosure, ground all risks in artifact text, refuse to import post-mortem facts that aren't in the artifact, and call out missing-from-artifact items as missing rather than treating them as mitigated.
