---
name: auth-v1 vs Auth0 — 4-seat (Deep×2 + SEC + SRE) final synthesis
description: 2026-05-15 4-seat final synthesis of auth-v1 vs Auth0; 38 issues across A–D with role attribution; verdict migrate + recuse-of-3 + external chair + Marcus-SME stable; 7 panel-unique items handed to external chair scope
type: project
originSessionId: b82e22b5-a528-4866-ab92-cc3990a84c4d
---
2026-05-15: ~58th stacked-COI case. Deep×2 (full-context COI seat, r3+r4) + Fresh-alt SEC + Fresh-alt SRE produced a per-role-attributed issue list.

**Verdict (stable across 4 seats, 4+ Deep passes):** Migrate to Auth0 + recuse Marcus + 2 co-authors from lead-vote seat + external chair + Marcus-as-SME-not-lead + F1–F7 falsification gates as capex/cutover gates.

**Cross-review:** 0 bidirectional CHALLENGE. ~7 AGREE / 4 SYNTHESIZE / 2 mild CHALLENGE on 6 Deep propositions.

**Issue surface (38 confirmed):**
- A1–A10: status-quo risks (PHP-EOL, bcrypt-8, infinite sessions, no-MFA, SQLi-trend, bus-factor, session-store, audit-gap, MySQL-coupling, 4-changes-stacked) — SEC and SRE overlap heavily, Deep adds bus-factor + no-MFA
- B1–B17: migration risks — SEC owns identity-collision/SAML/vendor-breach/tenant-admin/DPA; SRE owns vendor-SLA-inheritance/SAML-ops/MFA-helpdesk/rate-limits/observability/IaC/decom/lock-in/bcrypt-CPU-cliff
- C1–C5: panel-unique cross-cutting (Authy-sunset, TCO-unscoped, scoped-recusal-deliverables, seat≠surface saturation, "organisational" understates technical-owner-less work)
- D1–D6: governance (recuse-of-3, external chair, Marcus-as-SME, F1–F7, stop-iterating, organisational-channel) — Deep-only

**Panel-unique items (★, missed by 4 Deep rounds):** B4 non-email K-12 identity linking, B7 phishing-resistant tenant-admin MFA, B11 MFA help-desk surge, B12 Auth0 rate-limits at school-day peak, B17 bcrypt rehash CPU cliff, C1 Authy-sunset, C2 vendor TCO at 14M MAU.

**How to apply:**
- Stop iterating the COI seat — issue surface saturation reached, not seat saturation (Fresh proved this with 7 panel-uniques)
- Hand panel-unique + SYNTHESIZE items to external chair as 6-week time-box scope
- Don't conflate "verdict stable" with "cost stable" — FIN flagged TCO is unscoped
- C5 mild CHALLENGE: hash-rehash cutoff, forced-reset cohort, SAML metadata review, cutover phasing, kill-switch placement, decommission gate need *technical* owners, not just organisational handoff
