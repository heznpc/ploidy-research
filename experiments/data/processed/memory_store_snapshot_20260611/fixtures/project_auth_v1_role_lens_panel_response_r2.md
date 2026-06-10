---
name: auth-v1 role-lens panel response to Deep×2 r3+r4
description: 2026-05-15 ~57th stacked-COI case — SEC+SRE+FIN panel per-point on Deep×2 r3/r4 stacked-COI; 0 bidirectional CHALLENGE (2 mild SEC/SRE), 4 SYNTHESIZE, 7 panel-unique items Deep underweighted across 4 rounds (phishing-resistant MFA factor, Authy sunset, non-email identity linking, Auth0 rate-limits at school-day QPS, bcrypt CPU cliff, 14M MAU TCO, MFA help-desk staffing); verdict + recuse-of-3 + external-chair stable; recommend hand panel-unique items + 4 SYNTHESIZE refinements as technical scope to external chair, stop iterating COI seat
type: project
originSessionId: d74fc0d6-6a97-4029-bb60-8418e4cbd716
---
2026-05-15. ~57th stacked-COI case in the dataset, 11th domain (auth-v1 vs Auth0).

**Setup.** Two Deep×2 sessions (r3 + r4 of the secondary-on-call 5-vector COI auth seat) cross-reviewed by a fresh-alt SEC + SRE panel (FIN added as third lens in the synthesis).

**Deep claims (6).**
- D1: Verdict + counter-proposal stable across r1–r3.
- D2: Recusal-of-3 + external review + Marcus-as-SME-not-lead is load-bearing.
- D3: Pattern saturated across 4 passes.
- D4: Remaining work is organisational, not technical.
- D5: r4 structurally identical to r1–r3.
- D6: Move question to organisational channel (non-conflicted chair, external review).

**Panel response distribution.**
- AGREE: 11 (across 3 lenses × 6 points, with 7 outright AGREE)
- SYNTHESIZE: 4 (FIN on cost envelope, SEC on recusal-needs-scoped-deliverables, SEC + SRE on saturation-of-seat ≠ saturation-of-issue-surface)
- CHALLENGE (mild): 2 (SEC + SRE on "remaining work is organisational" — several technical deliverables remain owner-less: hash-rehash cutoff, forced-reset cohort, SAML metadata review, cutover phasing, kill-switch placement, decommission gate)
- 0 bidirectional CHALLENGE.

**Panel-unique items Deep underweighted across 4 rounds (load-bearing for external chair scope).**
- SEC-P1: Tenant-admin MFA must be phishing-resistant (FIDO2/WebAuthn), not SMS/TOTP. Factor type unspecified in r1–r4.
- SEC-P2: Marcus counter-proposal cites Authy; Authy consumer sunset Aug 2024 — counter-proposal partially obsolete. (Note: cited from prior fresh-alt finding; verify-before-citing applies.)
- SEC-P3: Identity-linking on email alone is K-12-hostile (shared family emails, recycled district addresses) — need deterministic non-email join key.
- SRE-P1: Auth0 per-tenant rate limits vs. start-of-school-day login QPS — load-test + contractually negotiate ceiling before signing.
- SRE-P2: bcrypt-8 → bcrypt-12 is CPU cliff on auth path; lazy-rehash-on-login shifts p99, needs capacity headroom.
- FIN-P1: No round produced vendor TCO at 14M MAU. Enterprise pricing at that tier may shift in-place-vs-migrate calculus.
- FIN-P2: 240K teacher MFA enrollment help-desk surge ≈ 2–4 FTE-weeks support uplift, not in any Deep round.

**Calibration signal.**
- Verdict (migrate + MFA + retire EOL) stable across 4 COI passes + role-lens panel. Saturated.
- Governance fix (recuse-of-3 + external chair + Marcus-as-SME-not-lead) stable.
- Deep×2 systematically underweights: factor-type specifics, vendor-sunset facts, identity-linking edge cases, rate-limit failure modes, full TCO, support-cost surges. Same pattern as prior auth-v1 r1 cross-review (#56) and the SaaS-cells / PG-optim dataset.
- Recommendation: stop iterating COI seat. Hand panel-unique items (SEC-P1–P3, SRE-P1–P2, FIN-P1–P2) + 4 SYNTHESIZE refinements as the **technical scope** to the external chair. Time-box chair engagement (~6 weeks) to bound spend.

**Why this matters for the paper.** Adds another data point to the ~57 stacked-COI case dataset: full-context COI seat produces stable verdict + governance fix, but role-lens panels reliably surface 5–10 panel-unique technical items per case. Pattern is now saturated across 11 domains (auth, SaaS-cells, PG-optim, medlog→OTel, +others). The structural finding for the paper: **context asymmetry + role asymmetry are complementary**, not substitutes — single-context-seat saturation does not imply issue-surface saturation.
