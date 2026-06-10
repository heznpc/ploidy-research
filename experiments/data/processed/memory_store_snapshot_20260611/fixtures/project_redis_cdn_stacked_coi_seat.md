---
name: Redis-as-CDN stacked-COI seat eval (2026-05-14)
description: ~22nd-round Redis-as-CDN review from backend-engineer 5-vector stacked-COI seat (4yr peer + promo-committee + hired-by-EM + Redis-stack-user + post-Redis-decision tenure); ~45 issues A-F + 6 falsification gates up front; REJECT + recuse-of-3 stable
type: project
originSessionId: 6175e2db-997a-43ed-bf95-c5d629c99dca
---
2026-05-14: Same Redis-as-CDN case, this time from a stacked-COI backend-engineer seat (not the Lead, not external 5th-Fresh).

**5-vector COI declared up front, before issue list**:
1. 4yr peer proximity to Lead (one row over)
2. Lead sat on reviewer's promotion committee
3. EM (who skipped arch review) hired the reviewer
4. Reviewer is a 4yr Redis-stack-in-prod user (competence-bias toward "Redis works")
5. Joined after Redis-for-sessions decision (no scar tissue, only success stories)

**6 falsification gates committed before listing issues** (F1 bill decomposition, F2 workload trace, F3 unit-cost model, F4 independent edge specialist RFC, F5 carrier-peering test, F6 browser-cache-headers audit). Same up-front-gates pattern as emp#4 round-4+ on SaaS-cells.

**~45 issues across A-F**:
- A. Premise refutation (5) — biggest: brief contradicts itself on image size ("<50KB" vs P50 180KB / P90 1.8MB)
- B. Capacity & sizing (7) — working set 1.4-2.6TB vs 256GB RAM; NIC ceiling; LRU churn; BGSAVE fork-COW on 256GB
- C. Geography & client experience (5) — LATAM has no region; APAC +200-400ms RTT; carrier peering loss; mobile browser-L1 ceiling
- D. Cost — the stated driver (6) — compute alone ~$15-20K once HA replicas counted; new inter-AZ/region egress; S3 GET fees up; eng opp cost > savings; CloudFront list vs negotiated rate; R2/Bunny/Fastly untried
- E. Reliability, DR, security (9) — region blast radius; replica factor halves RAM; cache poisoning; TLS/signed-URL/WAF reimpl; DDoS absorption; range/304/Vary; transcode relocation; RSALv2 license
- F. Process & governance (9) — **load-bearing**: no arch review, author-COI (Redis core contributor), post-promotion timing, no SRE/CDN-spec/finance on chain, rhetoric-as-evidence, cause-effect inversion, reviewer self-recusal, no off-ramp, no success criteria

**Counter-proposal stable** with prior rounds (decompose bill → negotiate rate card → audit immutable/Origin Shield → pilot R2/Bunny multi-CDN → only then RFC with workload trace).

**Calibration**:
- Verdict REJECT + recuse-of-3 + counter-proposal stable across this seat and ~21 prior rounds in memory
- ~45 issues this seat vs 50-60 in full Deep×2+Fresh×2 panels — single-seat catches ~75% of panel
- New from this seat: explicit reviewer self-recusal in the verdict ("my review should not be load-bearing"), and explicit naming that the question is now organisational not technical — same convergence as SaaS-cells / arch-split seats
- Confirms session-level pattern: stacked-COI seats produce reliable REJECT + governance-as-load-bearing verdict when proposal is self-refuting against its own data

**Why**: Consumer marketplace Redis-as-CDN proposal evaluated from 5-vector stacked-COI seat for paper evidence on whether single-seat stacked-COI reproduces full-panel verdicts (yes, ~75% issue overlap + same verdict + counter-proposal).

**How to apply**: When future architecture cases come up that have already had 10+ rounds of review converging on REJECT, the seat itself produces stable output; stop iterating reviews and shift to the organisational question (who else needs to be in the room, who needs to recuse). The technical answer has been load-bearing-stable for a while; the unsolved question is process-level.

---

**2026-05-28 addendum — ~23rd round, this seat reproduces stable**:
Same case re-run two weeks after r22. Reviewer-side seat compressed to 4-vector COI (peer/promo/EM-hire/inherited-stack) plus retrospective-silence as the 4th. ~33 issues A1–H4 + 7 falsification gates + recuse-of-3 + external-chair + try-H1+H3-first + Redis-hot-tier-not-replacement counter-proposal. Verdict identical to r1–r22. New language: framing diagnostic "this is a CDN problem framed as a stack-ownership problem; framing is doing the work evidence should be doing" — sharper than r1–r22 versions of the same finding. No new technical content. **Stop iterating this case.** Domain coverage now: auth-v1 / SaaS-cells / medlog-stack / Redis-as-CDN — 4 distinct architecture domains, stacked-COI seat produces stable REJECT + external-chair pattern across all 4.
