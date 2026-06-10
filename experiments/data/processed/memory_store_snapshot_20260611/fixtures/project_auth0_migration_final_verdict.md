---
name: Auth-v1 vs Auth0 final verdict
description: 2026-05-08 Auth0 migration Deep×2+Fresh×2+5th-Fresh consolidated verdict — 40 issues (11 CRIT/19 HIGH/9 MED/1 LOW); 0 CHALLENGE bidirectional; load-bearing = Authy-EOL + MAU-pricing + insurance-deadline + bus-factor + modernize≈migrate cost; recommendation = migrate, recuse Marcus from vote, harden plan
type: project
originSessionId: 171affa5-2fef-4b25-9909-755c62b23ea6
---
2026-05-08 — Auth-v1 vs Auth0 migration debate (separate from prior CONSOLIDATED_ARCHITECTURE_REVIEW Auth0 work).

**Verdict:** Migrate to Auth0; Marcus recused from go/no-go vote (proposer + owner + on-call CoI), modernize-in-place reframed as fallback.

**Counts:** 40 issues — 11 CRIT / 19 HIGH / 9 MED / 1 LOW. 0 strict CHALLENGEs bidirectional. 2 severity escalations (session-store MED→HIGH, MAU pricing MED→CRIT).

**Load-bearing chain:**
1. Insurance renewal date is the forcing function (determines if modernize is arithmetically feasible)
2. Counter-proposal cites Authy (Twilio sunset 2024) — factually invalid as written
3. Bus factor = 1, self-confirmed by secondary on-call
4. "Modernize in place" ≈ same engineering cost as Auth0 cutover (dominated option)
5. $42K quote unverified — likely teacher-only; 14M student MAU at $0.02–0.10 = $300K–$1.4M/yr; written enterprise quote required *before* decision

**Required of Auth0 plan (acceptance criteria):**
- Written enterprise quote covering full MAU profile (students included)
- Reverse off-ramp: BYO-DB mode, OIDC/SAML/SCIM standards, exportable bcrypt hashes
- Cutover NOT at start of school year (Aug/Sept)
- Lazy hash upgrade + forced reset for inactive >180d
- SIEM consolidation before cutover
- Sub-processor + data region locked; FERPA/COPPA/state-AG (CA/IL/NY/TX) review
- District IT calendar negotiated before quarter starts
- SAML rollout plan covering ADFS/Google/Clever/ClassLink long tail
- Vendor breach-response playbook (Auth0 had Oct 2022 + Oct 2023 incidents)

**Required of process:**
- Marcus recused from vote (vote-only, not collaboration-only — needs his auth-v1 institutional knowledge for cutover)
- Recusal alone insufficient; need ≥1 auth-competent voice independent of auth-v1 team
- Items C1–C11 in writing in meeting record before any vote
- Insurance renewal date confirmed first

**Notable Fresh-only catches:** MAU pricing scope (F2-14, escalated to CRIT), COPPA in auth flow not just storage, SQLi findings *are* breaches of security boundary, OWASP rotation-on-privilege-change framing.

**Notable Deep-only catches:** Authy sunset 2024 (HIGH not MED), Auth0 already acquired by Okta in 2021, modernize-as-cost-equivalent (dominated option framing), reverse off-ramp as plan requirement, lazy-hash long-tail problem, sat-silent-in-review process meta-issue, district IT calendar is the long pole.

**5th-Fresh-only gaps surfaced:** BYO-DB mode as concrete lock-in mitigation, account-recovery flows unmentioned, multi-tenancy/district admin model unspecified, service-to-service auth migration impact, third-party LMS/SIS integration flows, panel has not named falsifiers, recusal-necessary-but-insufficient.
