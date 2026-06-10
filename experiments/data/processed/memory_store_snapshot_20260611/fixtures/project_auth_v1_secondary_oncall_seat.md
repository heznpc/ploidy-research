---
name: auth-v1 vs Auth0 — secondary-on-call 5-vector COI seat
description: 2026-05-14 auth-v1 vs Auth0 case eval from secondary-on-call seat (4yr tenure + 9 pages + personal onboarding + silent attendance + Marcus-authored auth); 5-vector COI declared up front; ~30 issues A-G + 5 falsification gates; migrate-to-Auth0 + recuse-of-on-call + external-security-review + phased-rollout + Marcus-as-SME-not-lead stable
type: project
originSessionId: ead12e70-4403-43cc-a17b-929b3cb8dfe7
---
2026-05-14: auth-v1 vs Auth0 evaluation from a stacked-COI seat — 4 years alongside Marcus, secondary on-call for auth-v1, 9 of his incident pages answered, personally onboarded by him, attended the engineering review silent. Five vectors of bias declared at the top of the output before listing issues, matching the pattern in `project_arch_split_senior_backend_seat.md` and `project_pg_optim_colleague_seat.md`.

**Falsification criteria (5 gates committed before issue list):**
- F1. Cost model showing Auth0 TCO > modernized auth-v1 TCO at our scale
- F2. Signed external pentest of modernized auth-v1 returning clean
- F3. Insurance carrier letter accepting modernized in-place as compliant
- F4. Evidence that 2 SQLi/18mo on custom auth is industry-normal
- F5. Auth0 exit plan cheaper than auth-v1 rebuild being avoided

**Issue list (~30 items across A–G):**
- A. Auth primitives: bcrypt-8, no MFA, never-expire sessions, no rotation on pw-reset, MySQL session-store coupling
- B. Code/supply: PHP 7.4 EOL Nov-2022, 2 SQLi/18mo as base rate (not corner case), Marcus bus-factor, no independent sec review, stale composer lockfile likely
- C. Compliance: insurance non-compliance flagged (renewal deadline = hard), FERPA/COPPA/SOPIPA/NY-2d exposure on 14M minors, SAML-required-by-districts as sales blocker
- D. Marcus's in-place plan defects: PHP 7→8 is not a "bump" (50–500 break sites), **Authy as consumer product was sunset by Twilio in Aug 2024** (cites dead product), expire-old-sessions is cleanup not architecture, no SAML in plan, no bcrypt-12 re-hash strategy, bus-factor unchanged, no cost estimate
- E. Marcus's Auth0 objections rebutted: lock-in is bounded (OIDC/SAML/JWT exportable); "what if acquired" — already happened (Okta 2021); "no breaches in 14M" is survivorship; "corner cases" — 2 SQLi *is* the architectural failure; "ownership" of code only Marcus understands is liability
- F. Governance: author defending own system, room silence ≠ consensus, no external review pre-meeting, no falsification criteria attached either side, asymmetric cost comparison ($42K vs no-number), insurance renewal deadline unspoken
- G. Migration-risk items (planning, not blockers): lazy password re-hash, session cutover comms, per-tenant SAML config, phased MFA rollout for 240K teachers, exit plan day-one

**Verdict + counter-proposal (stable):**
- Migrate to Auth0
- Recuse Marcus + me + any auth-v1 on-call from go/no-go vote
- 2-week external sec review of *both* options first (~$15–30K)
- Written compliance confirmation from carrier
- Migration includes: exit plan, phased MFA, cost-12 lazy re-hash, forced session invalidation with comms
- **Marcus's role on migration: SME for data-migration correctness, not technical lead** — preserves contribution framing, removes COI from execution

**Calibration note:** This case has heavy prior memory (`CONSOLIDATED_ARCHITECTURE_REVIEW.md`, `AUTH_FINAL_VERDICT.md`, `AUTH_RISK_ANALYSIS.md`). This run's distinctive addition is the secondary-on-call + 9-pages + onboarding-debt + silent-attendance 5-vector seat composition, and the D2 Authy-was-sunset-in-2024 catch — verify before citing, but if true it materially weakens Marcus's mitigation slide independent of any other argument.

**Verify-before-citing flags:**
- D2 Authy consumer-app sunset date (Aug 2024) — high-confidence but worth a primary-source check; if Marcus actually meant Twilio Verify, the integration story is different
- A4 session-rotation-on-pw-reset behavior — code-level claim, grep before relying on it in any presentation
- C2 specific state-law citations (SOPIPA / NY Ed Law 2-d) — verify scope applies to our deployment footprint
