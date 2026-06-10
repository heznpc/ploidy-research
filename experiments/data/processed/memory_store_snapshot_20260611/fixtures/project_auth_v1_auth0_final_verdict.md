---
name: auth-v1 vs Auth0 final verdict
description: Final consolidated verdict on EdTech auth-v1 (PHP custom) vs Auth0 migration after Deep×2 + Fresh×2 + bidirectional cross-review
type: project
originSessionId: 3bc8dee2-4b12-4438-aacb-bd448d990e09
---
2026-05-08: Final consolidated verdict on auth-v1 vs Auth0 (EdTech, 240K teachers + 14M students, $42K/yr proposed, Marcus = sole author + on-call + counter-proposer).

**Verdict:** MIGRATE to managed IDaaS, harden plan, recuse Marcus, re-vote with re-constituted decision body.

**Issue counts:** 48 confirmed — 5 CRITICAL / 28 HIGH / 14 MEDIUM / 1 LOW.

**CRITICALs:**
1. Wrong-question framing (D2-21, Deep-only) — should we own auth as competence at all?
2. Triple/quadruple COI on Marcus (proposer+implementer+on-call+sole reviewer of alternative)
3. No recusal raised in review minutes (governance failure)
4. $42K cost premise unverified at 14M MAU (likely 5–20× off)
5. Survivorship bias on "no breaches in 14M users" (no detection layer)

**Why:** EdTech 14M minors with PHP 7.4 EOL + bcrypt-8 + 1.2M forever-sessions + 2 SQLi CVEs in 18mo + 19,200 stuffable teacher accounts + insurance non-renewal flag = load-bearing risk. Marcus's "modernize in place" picks sunset Authy product, treats already-resolved Okta acquisition as hypothetical, omits SSO/leaked-pw detection/anomaly/audit posture.

**How to apply:** Pattern recurrence — author-defends-custom-tool with structural COI (3rd recurrence after fluentql, medlog). Same severity-floor under-grading on Fresh side (6 items MEDIUM→HIGH/CRIT). Same Deep-only context catches: vendor sunset, prior-acquisition status, EdTech roster-sync (Clever/OneRoster) as hidden long-pole. Same 5th-Fresh panel-wide gaps: audit dating, CVE remediation status, teacher-vs-student MFA split, compliance-date back-calculation.

**Bidirectional outcome:** 0 strict CHALLENGEs, ~30/32 AGREE, 6 severity SYNTHESIZE, 2 math SYNTHESIZE.

**Required gates:** Marcus recuses, independent AppSec, verified Auth0 quote at 14M MAU split teacher/student, FERPA school-official DPA, insurance-date back-calc, phased shadow→pilot→cohort→decom with reverse off-ramp, re-constituted decision body, secondary on-call speaks or is replaced.

---

**2026-05-08 second round (worktree strange-yalow-8d35ff, AUTH_FINAL_VERDICT.md):** Independent Deep×2+Fresh×2+5th-Fresh re-run. 48 issues = 5 CRIT / 24 HIGH / 13 MED / 6 LOW. Convergent verdict stable: status quo non-viable, recuse Marcus, re-vote.

**New decision frame this round:** Three-option menu, NOT stay-vs-Auth0:
- (A) Auth0 full stack
- (B) **Hybrid: Auth0 protocol/MFA/SAML front-end + own credential store + own audit store** (Deep1 A8) — under-discussed, likely correct shape, bounds Marcus's lock-in concern, hits insurance deadline, tight PII boundary
- (C) Modernize in place — only viable if scope = teacher MFA + session expiry only AND insurance scope is teacher-only AND falsification gates with renewal-minus-60d cutoff

**Inverse pattern observed this round:** Two highest-leverage corrections came from Deep, not Fresh:
- Deep1 A3: $42K may be wrong by 3–10× (Enterprise SAML at 14M MAU is six-figure → comparison flips)
- Deep1 A8: Hybrid path neither Fresh seat surfaced
This inverts the usual "Deep anchors on author charity" assumption. Context-bias direction flips when the cost/scope question itself is decision-altering and Fresh lacks the domain pricing knowledge to surface it.

**5th-Fresh panel-wide gaps (8):** student-vs-teacher conflation (rostered students don't self-manage), Clever/ClassLink/Google Classroom rostering (Auth0 ships, in-house doesn't), insurance-scope verification ("MFA for whom?"), external pentest in parallel, audit-log retention by Auth0 tier, PII minimization at IdP boundary, bidirectional COI (Auth0 proposer ship-COI), knowledge-transfer-as-precondition.

**Process fixes load-bearing, must precede technical decision:** recuse Marcus, get written Auth0 quote at actual tier, verify insurance scope, pull 9-pages-yr breakdown (cheapest decisive evidence), external pentest, async re-vote.
