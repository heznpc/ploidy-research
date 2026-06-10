---
name: Auth0 migration eval — Marcus-colleague stacked-COI seat
description: 2026-05-14 single-seat eval of auth-v1 (custom PHP, Marcus Chen) vs Auth0 migration from 4-vector COI seat (4yr tenure + secondary on-call + onboarded by Marcus + silent in review); verdict = migrate, recuse Marcus from recommendation
type: project
originSessionId: cc07ae64-fd5c-4897-b7b8-9efcbcf57a7d
---
# Auth-v1 vs Auth0 — colleague seat (4-vector COI)

**Date:** 2026-05-14
**Seat:** Backend engineer, 4yr tenure, secondary on-call for auth-v1, onboarded by Marcus, attended review and stayed silent.
**COI vectors:** tenure overlap, operational dependency (pager skill depreciates if Auth0 lands), onboarding debt, observed-but-unspoken complicity.

## Case facts (pinned)
- 14M students, 240K teachers, EdTech
- auth-v1: PHP 7.4 (EOL Nov 2022), bcrypt cost 8, MySQL session store, no rotation, no MFA, 2 SQLi CVEs in 18mo
- 1.2M sessions >90d old, 8% teacher password reuse vs public breach sets
- Insurance carrier flagged no-MFA as non-compliance for next renewal
- Proposal: Auth0, $42K/yr (number likely wrong — real B2C @ 14M MAU likely $150–400K)
- Marcus pushback: "no breaches, CVEs are corner cases, Auth0 lock-in risk, modernize in place to PHP 8.3 + Authy MFA"

## Verdict: MIGRATE to managed IdP (Auth0 not locked — RFP Cognito/Entra/Okta CIC)

Load-bearing facts (any one is sufficient):
- C1: PHP 7.4 EOL, no upstream patches ~3.5yr
- C4: ~19K live credential-stuffing-vulnerable teacher accounts today
- C6: Insurance non-renewal is P0 business risk; carrier sets timeline, not us
- C7: Bus factor = 1 (Marcus sole author, I'm secondary but answered 9 pages = system is incident-prone and only he understands it)

## Why Marcus's plan fails on its own terms
- "Authy MFA" — Authy consumer app sunset 2024; real MFA build = WebAuthn + TOTP + recovery + enrollment + step-up + admin reset = months of senior work
- PHP 8.3 upgrade on custom auth code with recent SQLi = retest every auth path
- No SAML in his plan; SAML is revenue-blocking for district sales
- All of the above compete for the same single engineer's time

## Counter-proposal
1. Recuse Marcus from the *recommendation* vote (keep him on the *design* — his knowledge is highest-value input to migration sequencing). Recuse me too. Add one external security reviewer.
2. RFP managed-IdP layer; don't lock on Auth0 sight-unseen at $42K (number is wrong direction-of-magnitude).
3. Phase: SAML for districts (revenue) → teachers w/ MFA (insurance) → students (lazy bcrypt-rehash).
4. Two-engineer minimum on migration, one not Marcus (bus-factor mitigation).
5. Insurance carrier conversation drives the calendar.

## Process / pattern note
- Coercive review pattern: author-defends-system, dissent silent (including mine). Same pattern as the SaaS-cells and arch-split cases. Decision needs to be re-run without the author owning the vote.
- "Lock-in / what if prices rise" is asymmetric with the downside of a 14M-user breach (FERPA/COPPA/50-state notification/class action). Category error.
- "We keep ownership of our auth" is sunk-cost framing for non-auth-vendor company.

## Falsification gates (would flip verdict)
- Managed IdP TCO @ 14M MAU comes in materially worse than in-place modernisation TCO including hidden costs
- Clean in-place modernisation path with <1 quarter senior eng time AND independent security signoff
- Insurance carrier accepts MFA-on-PHP-with-credible-plan in lieu of managed IdP
