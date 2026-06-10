---
name: auth-v1 → Auth0 migration final verdict
description: 2026-05-08 multi-round Deep×2+Fresh×2+5th-reviewer panel on auth-v1 vs Auth0; converged verdict = migrate, recuse all on-call rotation from vote, pull real quote, define student/COPPA flow before cutover
type: project
originSessionId: e912e05c-d3ca-40ac-a51b-c36e68369e4b
---
2026-05-08: auth-v1 (custom PHP 7.4, bcrypt-8, no MFA, 1.2M aged sessions, 2 SQLi/18mo, 14M users incl. minors, 240K teachers, insurance flagged non-compliance) vs Auth0 migration ($42K/yr headline, 1Q timeline). Multiple Ploidy rounds run.

**Verdict:** Migrate to Auth0. Recuse all auth-v1 on-call rotation from keep/replace vote (not just Marcus — secondary on-call sat silent = same failure at lower magnitude). Pull written Auth0 quote with correct SKU before commit. Marcus assigned migration tech lead.

**Latest round: 43 confirmed issues** (4 CRIT / 24 HIGH / 13 MED / 2 LOW). 0 strict substantive CHALLENGEs Deep↔Fresh; 2 anchored-number CHALLENGEs (PHP 8.3 EOL date off ~1yr; GPU bcrypt rates contradict 10⁴× between Deep sessions); 6 SYNTHESIZE escalations. Earlier round logged 53 issues, similar shape.

**Load-bearing chain (stable across rounds):**
- Insurance-renewal non-compliance flag = binding external deadline; in-place may be foreclosed on merit (Deep-only — Fresh can't see without project context)
- $42K headline implausible by ~10× at 14M MAU with SAML+MFA addons; entire cost comparison rests on unvalidated number
- Procedural: no member of auth-v1 on-call rotation should be deciding voice on keep/replace; structural recusal needed, not just author-recusal
- 2 SQLi/18mo in custom auth code = pattern, not corner case; author isn't objective evaluator
- 8% leaked-password reuse → ~19K stuffable teacher accounts; each with PII access for 30–150 students
- Fresh-unique: student auth path / COPPA-under-13 flow unspecified despite students = 98% of MAU
- Authy dead (Twilio Verify replacement); naming in 2026 = alternative wasn't researched

**Deep-only contributions:** insurance deadline as binding constraint, FERPA/COPPA/SOPIPA/NY Ed Law 2-d named by statute, PHP 7.4→8.3 BC breaks on auth code, shim/dual-run as auth-critical surface, "modernize in place" decomposed into 7 sub-projects, recurring EOL trap (PHP 8.3 EOL ~18mo out), Marcus-as-migration-tech-lead political fix.

**Fresh-only contributions:** student auth path (panel blind-spot), quantified credential-stuffing surface (~19K), egress plan as deliverable, vendor security amortization economic frame, B2B2C topology mismatch (Auth0 Organizations vs B2C SKU).

**5th-reviewer panel-wide gaps:** $42K never modeled (just flagged); false binary auth-v1-vs-Auth0 (no WorkOS/Cognito/Stytch/FusionAuth comparison); B2B2C topology; parental-consent ID-chain continuity; EOY batch deprovisioning; audit-log continuity for compliance investigations; carrying-cost of dual-stack (6–18mo realistic); reference-class forecasting absent (Khan/Quizlet/Duolingo post-mortems exist); rotation-wide recusal as structural fix.

**Counter-proposal stable across all rounds:**
1. Recuse all auth-v1 on-call rotation from keep/replace vote
2. Pull written Auth0 quote with correct SKU (Organizations + SAML + advanced MFA + log streaming) before commit
3. Migrate; assign Marcus as migration tech lead (knowledge transfers into cutover instead of competing with it)
4. Sequence: password users first (insurance-deadline gated), SAML district-by-district after
5. Lazy bcrypt rehash + forced reset for 8% leaked cohort
6. Treat shim/dual-run bridge as auth-critical, not glue
7. Define COPPA-aware student flow before cutover; preserve parental-consent ID chain
8. Reverse off-ramp + audit-log/ID continuity as deliverables
9. Ship immediate-action items (force-expire stale sessions, force-reset leaked passwords, rate-limit login) NOW — they're not blocked on the migration decision

**Pattern echoes (3rd+ recurrence):** structural-COI + author-defends-own-system (after fluentql, medlog). Same shape: builder votes on retention; secondary maintainer silent in room; "no breaches/incidents" framed as track record (survivorship bias). Stable structural fix = recuse rotation + dissent-prompt + ≥2-vendor bake-off.

**How to apply:** When reviewing managed-service migration proposals on tight timelines:
- Treat author-as-voter as load-bearing HIGH (not MEDIUM)
- Demand written vendor quote with correct SKU before commit; "suspiciously low" headlines are usually 5–10× off
- Decompose "modernize in place" into sub-projects; the phrase hides scope
- Anchored numbers (timeline, cost, EOL dates, GPU benchmarks) require source citations
- Force the panel to separate immediate-action items from the migrate/don't decision
- For EdTech specifically: COPPA consent-record continuity through cutover is a compliance blocker, not a nicety
- Watch for anchored Deep numbers without sourcing; preserve direction, hedge magnitude

**Calibration:** Stop iterating after 2–3 rounds when 0 substantive CHALLENGEs and recommendation stable. Next round won't add load-bearing findings. Invest the time in pulling the actual quote and writing the student-auth flow.
