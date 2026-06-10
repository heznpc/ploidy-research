---
name: auth-v1 vs Auth0 — secondary-on-call 5-vector COI seat, round 3
description: 2026-05-15 ~54th stacked-COI case / 10 domains — 3rd-pass auth-v1 vs Auth0 from secondary-on-call 5-vector COI seat; F1–F5 gates + ~30 issues A–G with HIGH/MED/LOW per item; migrate + recuse-Marcus + recuse-self + external pentest + Marcus-as-SME-not-lead stable; structurally identical to r1/r2
type: project
originSessionId: 3afa9407-d6c4-4f80-b48f-837b3c5d8872
---
2026-05-15: 3rd-pass auth-v1 vs Auth0 from the same 5-vector secondary-on-call seat (r1 = 2026-05-14, r2 = earlier 2026-05-15 session). Structurally identical to both priors on verdict and counter-proposal.

## Seat (unchanged)

5-vector COI: 4yr tenure overlap with Marcus / personally onboarded (mentorship debt) / secondary on-call for auth-v1 (operational dependency) / 9 of his pages answered in last 12mo / silent attendance at engineering review.

## Falsification gates (F1–F5, committed before issue list)

- F1. Independent TCO model: modernized auth-v1 < Auth0 over 3yr including security headcount.
- F2. Signed external pentest of modernized auth-v1 + written carrier acceptance of in-place.
- F3. ≥2 independent district CIOs confirm SAML not required for next renewal cycle.
- F4. Public base-rate evidence that 2 SQLi/18mo on 14M-user custom auth is industry-typical.
- F5. Auth0 exit cost (OIDC/SAML/JWT export to replacement IdP) > auth-v1 rebuild cost avoided.

## ~30 issues A–G (HIGH/MED/LOW per item, full list in conversation transcript)

- **A. crypto/session primitives**: bcrypt-8 (H), forever sessions (H), no MFA + 8% pwd-reuse (H), no rotation on reset (M, grep-confirm), MySQL-coupled session store (M)
- **B. code/supply**: PHP 7.4 EOL Nov 2022 (H), 2 SQLi/18mo = rate not corner case (H), bus-factor 1 = Marcus (H), no independent sec review ever (H), stale composer.lock likely (M)
- **C. compliance/commercial**: carrier non-compliance for next renewal = hard deadline (H), FERPA/COPPA/state-PII on 14M minors (H), SAML required as sales blocker (H), audit log likely missing (M)
- **D. Marcus's plan defects**: PHP 7→8.3 ≠ "bump" (H), Authy consumer-app sunset Aug 2024 (H — verify primary source; if Twilio Verify same lock-in objection applies), expire-sessions = cleanup not architecture (H), no bcrypt-12 re-hash strategy (H), no cost number = asymmetric comparison (H), bus-factor unchanged (H), no SAML in plan (H)
- **E. Marcus's Auth0 objections rebutted**: lock-in bounded by OIDC/SAML/JWT export (H); Okta acquired Auth0 in 2021 — hypothetical already occurred (H); "14M users no breaches" = survivorship (H); 2 SQLi *is* the architectural failure (H); ownership of code only one person understands = liability (H)
- **F. governance**: author defends own system (H), silence ≠ consensus (H, I'm evidence), no external review pre-meeting (H), no falsification criteria attached either side (H), carrier-renewal deadline unspoken in framing (H)
- **G. migration-execution (planning, not blockers)**: lazy bcrypt re-hash on login (M), forced session invalidation + 14M user comms (H), per-district SAML (M), phased MFA for 240K teachers (M), exit plan day one (H), dual-run cutover (M), data-migration correctness ← Marcus's genuine SME value (H)

## Verdict (stable r1 → r2 → r3)

Migrate to Auth0. Conditions:
1. Recuse Marcus + secondary-on-call cohort (incl. self) from go/no-go vote.
2. External security review of *both* options before vote (~$15–30K, 2wk).
3. Written carrier confirmation of compliance for chosen plan.
4. Auth0 exit plan documented day one (addresses E1 in writing not rhetorically).
5. Marcus's role on migration = data-migration SME, not technical lead.

## Distinctive vs r2

r3 added explicit "I'm evidence of F2" framing for silent-attendance vector (self-as-data-point, not just self-as-COI). No new technical findings.

## Calibration

Stop iterating internally on this seat composition. r1 + r2 + r3 are structurally identical on verdict, gates, and recusal-of-3 counter-proposal. Pattern saturated across ~54 stacked-COI cases / 10 domains. Remaining question is organisational channel (non-conflicted chair appointed external to Marcus's reporting line), not more analysis.

## Verify-before-citing (unchanged from r1)

- D2 Authy consumer-app sunset Aug 2024 — primary source check; if "Authy" in Marcus's slide actually means Twilio Verify, the dead-product framing weakens but the third-party-dependency objection still applies.
- A4 session-rotation-on-password-reset — code-level claim, grep before citing.
- C2 SOPIPA / NY Ed Law 2-d — verify scope against deployment footprint.
