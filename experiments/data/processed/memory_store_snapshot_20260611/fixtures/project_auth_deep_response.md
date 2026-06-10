---
name: auth-v1 vs Auth0 Deep×2→Fresh×2 cross-review
description: 2026-05-08 Deep cross-review of Fresh×2 on auth-v1 vs Auth0; 1 CHALLENGE (F1-5 SQLi severity), 6 SYNTHESIZE (severity escalations); Fresh-unique adoptions = FERPA DPA, Auth0 outage, force-reset cutover, rehash-on-login deadline, in-place=preserves-bus-factor framing; Deep-unique = K-12 threat model, identity PK in our DB, session-store invariants, revenue-side SAML, self-observation of suppressed dissent; convergent verdict = migrate, recuse Marcus
type: project
originSessionId: 0a27b9b7-346e-40e8-89fd-de7e2fdb38b9
---
# auth-v1 vs Auth0 — Deep×2 → Fresh×2 cross-review (2026-05-08)

4th recurrence of author-defends-custom-tool pattern (after medlog, fluentql, deprecate skill).

## Cross-review tally

- 0 strict CHALLENGE on direction (both sides converge on migrate)
- 1 severity CHALLENGE: F1-5 SQLi as MED is under-graded (auth-bypass class → CRIT)
- 6 severity-floor SYNTHESIZE: F2-4 (K-12 threat model), F2-6 (no detection capability), F2-7 (bus factor functionally 1), F2-10 (migration HIGH not MED — Deep was under-grading), F2-16/F1-17 (COI is governance HIGH not bias MED), F1-5 (SQLi)

## Fresh-unique adoptions (Deep missed)

- F2-11 FERPA DPA / sub-processor / district contract amendment — HIGH
- F2-13 Auth0 outage = total platform outage — MED, mitigate with cached-session graceful-degradation
- F2-14 "built by the same team that shipped two SQLi CVEs" — closing-line framing
- F1-12 1.2M long-lived sessions must be force-invalidated at cutover — HIGH
- F1-9 cost-factor cannot upgrade without plaintext → rehash-on-login + forced-reset deadline — HIGH
- F1-16 in-place modernization preserves bus factor — adopt as load-bearing headline

## Deep-unique items (Fresh missed)

- K-12-specific threat model: targeted teacher account takeover (ransomware/grade-changing)
- Identity PK stays in our DB, not Auth0's — concrete vendor-risk mitigation
- Force-reset for dormant accounts (complementary to F1-12 cutover-time force-reset)
- Session-store undocumented invariants surfaced by 9 on-call incidents (orphan sessions, account-merge mismatches)
- Revenue-side SAML blocker: districts requiring Google Workspace for Edu / Entra / Clever / ClassLink SSO
- Logout/revocation opacity for stolen-laptop scenario
- SOC2/ISO27001 attestations as B2G RFP-required
- Self-observation: attended review, didn't push back — social structure suppressed dissent (data, not personal note)

## Calibration pattern

- Fresh under-grades bus-factor + COI (no on-call data, no team history)
- Deep under-grades migration risk (habituated to status quo, would be the one paged)

## Load-bearing chain

CRIT cluster (status quo not safe): PHP 7.4 EOL + bcrypt-8 + immortal sessions + no MFA + 2 SQLi pattern
HIGH cluster (in-place doesn't fix it): bus factor + author COI + scope mismatch
Mandatory guardrails: FERPA DPA, force-reset at cutover, identity-PK-in-our-DB, dual-run, SAML phased rollout

## Recommendation

Migrate to Auth0. HIGH confidence. Recuse Marcus from build-vs-buy and re-decide above his level. Required: dual-run cutover, force-invalidate all sessions at cutover, rehash-on-login + forced-reset deadline for dormant, identity PK stays in our DB, FERPA DPA + district contract amendments, cached-session graceful-degradation for Auth0 outages.
