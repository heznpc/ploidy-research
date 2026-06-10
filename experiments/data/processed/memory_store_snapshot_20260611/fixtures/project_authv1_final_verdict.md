---
name: auth-v1 → Auth0 final consolidated verdict
description: 2026-05-08 Deep×2 + Fresh×2 + bidirectional cross-review on auth-v1 deprecation; 50 issues (4 CRIT/28 HIGH/14 MED/4 LOW); 4th recurrence author-defends-own-tool COI
type: project
originSessionId: 39fee114-9241-40e5-b91a-052c7bebb8f8
---
**Verdict: MIGRATE to Auth0 (or equivalent managed IdP).** Both Deep sessions and both Fresh sessions independently converged. 0 strict CHALLENGEs bidirectional, 8 SYNTHESIZE.

**Why:** Status quo has multiple CRIT/HIGH issues (PHP 7.4 EOL, bcrypt-8, no rotation, no MFA, 2 SQLi/18mo, insurance deadline). "Modernize in place" leaves SQLi pattern, bus-factor, and SSO unaddressed; references deprecated Authy. Author of system being deprecated (Marcus) was the loudest pushback voice with no recusal declared.

**How to apply:** This is the 4th recurrence of the author-defends-own-tool COI pattern (fluentql → medlog → ARCHITECTURE_RISK → auth-v1). Recusal-from-decision-but-consultant-on-cutover is the load-bearing governance fix. When the proposer/defender of either path is the original author, surface this first, before technical scoring.

**Load-bearing chain:**
- C1 (no-recusal) + H25 (reviewer silence) + H27 (role split) → re-vote required
- H1+H2+H3+H4+H5 (EOL + weak hash + no rotation + no MFA + SQLi pattern) → status quo not safe
- H15+H16+H22 ($42K wrong, FERPA gate missing, SAML coord underestimated) → Auth0 plan needs re-costing

**Counter-proposal (stable):**
1. Marcus recuses from decision; tech consultant only
2. Re-cost ($150K–$300K realistic, not $42K)
3. FERPA/COPPA DPA gate before contract
4. 2–3 quarter dual-run, not 1 quarter cutover
5. Pre-defined rollback triggers
6. External security review of cutover + residual auth-v1
7. Mandatory auth abstraction layer (swap to Cognito/WorkOS/Keycloak)
8. Threat model doc + falsification criteria both paths
9. Success criterion = decommission auth-v1 (incl. M2M/admin paths), not Auth0 adoption

**Items needing verification:** Authy Aug-2024 deprecation date, Auth0 pricing at 14M MAU, "9 pages" PD logs, Auth0 default-tenant FERPA compliance, 8% leaked-password-reuse timestamp.

**Fresh-unique catches Deep missed:**
- F-A: "14M" ambiguous (registered/MAU/students/teachers) — pricing/COPPA/SAML scope hinges
- F-D: separate Marcus's decision-role from operational-role (Deep over-corrected to pure recusal)
- F-F: symmetric COI scrutiny on Auth0 *proposer* (vendor/resume incentives)
- F-H: formal gap-matrix (status quo × in-place × Auth0) for auditable comparison
- M11: contract instruments (export, price-cap, acquisition-change) enumerated pre-sig

**Deep-unique catches Fresh missed:**
- C3: Authy deprecated Aug 2024 (Marcus's MFA proposal references discontinued product)
- C4: no threat model / no falsification criteria on either path
- H10: PHP 8.3 upgrade itself 6–12 weeks during which security posture unchanged
- H11: code-ownership ≠ security-ownership decomposition
- H13: Auth0-price-hike vs breach reversibility asymmetry
- H14: API/M2M auth scope unaddressed
- H15: $42K mis-priced (realistic $150K–$300K)
- H25: reviewer's own silence as chilling-effect data
- M9: 2-week 1-district POC counter-proposal

**Total: 50 issues** (4 CRIT / 28 HIGH / 14 MED / 4 LOW). Calibration: stop iterating, panel is converged.
