---
name: arch_auth_v1_auth0_4session_synthesis
description: 2026-05-14 4-session synthesis of EdTech auth-v1 vs Auth0 from 5-vector COI seats; ~30 issues (4 CRIT/14 HIGH/11 MED/1 LOW); migrate + recuse-Marcus + verify-$42K + external-pentest unanimous load-bearing
type: project
originSessionId: 2e51c1b7-bc9f-4b6e-aa12-861c48a7ebc6
---
# 4-session synthesis — auth-v1 vs Auth0 (2026-05-14)

4 reviewers, identical 5-vector COI seat (mentee/secondary-on-call/tenure-paired/silent-in-review/codebase-identity), full context each. All 4 sessions: **migrate to Auth0** with Marcus + COI'd reviewer recused.

## Counts
- Total: ~30 confirmed issues
- Severity: 4 CRIT / 14 HIGH / 11 MED / 1 LOW
- Unanimous (4/4): 13 issues
- Load-bearing structural finding (4/4): author-as-decider COI is the deeper failure mode; technical case is the easy part

## Unanimous CRITICALs
- A1 PHP 7.4 EOL since Nov 2022 (~3.5yr unpatched runtime CVEs)
- A4 No MFA + insurance carrier non-renewal flag (business-continuity)
- D1 Marcus = author AND senior decider in own review (structural COI)
- D4 Recuse Marcus + COI'd reviewer; security lead + outside engineer owns call

## Unanimous HIGHs
A2 (bcrypt-8 + 8% leak overlap), A3 (1.2M stale sessions), A5 (2 SQLi/18mo base rate),
B1 (3 large parallel migrations not staffable in 1Q), B4 (negative-value ownership), B5 (bus factor),
C1 (Auth0 lock-in bounded), D2 (silent room anchored by tenure), F1 (verify $42K — likely $150-400K)

## Discipline note
Authy/Twilio sunset Aug 2024 claim downgraded from r1 unverified-asserted to MEDIUM verify-before-citing in r2 (matches arch_debate_fabrication_evidence pattern).

## Counter-proposal (stable across 4 sessions)
1. Recuse Marcus from vote, keep as migration tech lead
2. Recuse 5-vector-COI reviewer
3. 1Q timeline: lazy password migration → SAML top-20 districts → MFA staged → force-expire >30d sessions
4. Insurance carrier written confirmation by EOQ
5. External pentest before declaring done
6. IdP-only scoping in phase 1; pilot 1-2 districts; tested reverse off-ramp

## Calibration
6th stacked-COI 4-session synthesis after saas-cells / arch-split / medlog / auth-v1-author / auth-v1-secondary-oncall. Pattern consistent: COI disclosure + falsification gates + recusal recommendation + counter-proposal-with-conditions = stable artifact. Remaining question organisational not technical.
