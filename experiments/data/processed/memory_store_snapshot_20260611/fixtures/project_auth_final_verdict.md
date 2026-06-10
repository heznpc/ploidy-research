---
name: auth-v1 vs Auth0 final consolidated verdict
description: 2026-05-08 — auth-v1 vs Auth0 Deep×2+Fresh×2 final synthesis; 35 issues (5 CRIT/16 HIGH/11 MED/3 LOW); MIGRATE; 4th recurrence author-defends-custom-tool
type: project
originSessionId: 96c75347-5fb9-4eea-8031-41777994be2d
---
# auth-v1 vs Auth0 — Final Verdict (Deep×2 + Fresh×2 + bidirectional cross)

**Decision:** MIGRATE to Auth0. Convergent across all 4 seats. 0 strict CHALLENGEs on substantive findings. 1 severity CHALLENGE (F1 SQLi MED→CRIT).

**Tally:** 35 issues — 5 CRIT / 16 HIGH / 11 MED / 3 LOW.

## Required guardrails (unanimous)
- Marcus recused from build-vs-buy decision
- FERPA + COPPA DPA / sub-processor review / district contract amendments
- Identity PK stays in our DB (not Auth0's)
- Dual-run cutover with day-1 outage fallback
- Force-reset deadline for dormant accounts (rehash-on-login insufficient)
- Force-invalidate 1.2M long-lived sessions at cutover
- Dual-stack SAML rollout for un-migrated districts

## Load-bearing findings (load-bearing chain)
- C1 (PHP EOL) + C2 (SQLi pattern) + C3 (no MFA + credential stuffing) + C4 (immortal sessions) + C5 (bcrypt-8) — status quo unsafe
- H1 (Marcus COI) + H2 (review failed to surface COI) — governance gap
- H4 (lock-in symmetry: auth-v1 = worse lock-in) — counter to Marcus's main argument
- H8 (SAML as revenue unblocker) — reframes Auth0 as sales-side win

## Deep-unique catches (context-required)
- H2 self-flag: attended review, didn't dissent — social structure suppressed COI
- H8 SAML revenue-side (district SSO requirements: Google Workspace for Edu, Entra, Clever, ClassLink)
- H15 K-12 targeted-takeover threat model (ransomware/grade-changing)
- M3 9 prior on-call incidents → undocumented session-store invariants
- M4 identity PK stays in our DB (concrete vendor-risk mitigation)
- M5 SOC2/ISO27001 as B2G RFP requirement
- M6 session revocation gap
- L3 habituation-as-severity-downgrade meta

## Fresh-unique catches (plan-as-stranger)
- H10 1.2M sessions must be force-invalidated at cutover (else vuln migrates)
- H12 FERPA/sub-processor/DPA migration plan work
- H13 COPPA as separate regime
- H16 stacked-independent-risks framing
- M7 Auth0 outage = steady-state platform dependency change
- M9 240K-teacher help desk during MFA rollout
- M11 custom session store as known antipattern

## Calibration patterns
- **Fresh under-grades** bus-factor + COI without on-call/team-history visibility
- **Deep under-grades** migration risk (habituation + would-be-paged) and dormant-account residual on rehash-on-login
- **F1 graded SQLi pattern as MED** — Deep CHALLENGE to CRIT (auth-bypass severity class)

## Pattern: 4th recurrence of author-defends-custom-tool
Prior: medlog (2026-05-08), fluentql (2026-05-07), deprecate skill (earlier). Same shape: original author + on-call owner argues for keeping artifact, COI not surfaced in review, "no breaches/incidents" used as evidence of safety. Fresh independently catches COI in every recurrence.

## How to apply
- For any future deprecation/replacement debate where the artifact's author is also the reviewer/owner: name COI explicitly up front, require recusal from build-vs-buy, weight "no incidents" as survivorship not evidence
- For K-12 / student-data systems: COPPA + FERPA are *separate* regimes; sub-processor disclosure to districts is a real plan item, not a footnote
- For managed-vs-custom auth decisions: lock-in symmetry argument (custom = bus-factor lock-in) is load-bearing and routinely under-weighted
