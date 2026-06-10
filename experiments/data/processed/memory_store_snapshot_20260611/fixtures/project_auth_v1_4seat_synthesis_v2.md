---
name: auth-v1 vs Auth0 4-seat synthesis v2
description: 2026-05-15 ~61st stacked-COI case — final 4-seat (Deep×2+SEC+SRE+FIN-via-panel) synthesis; ~44 issues across A/B/C/G; migrate + recuse-of-3 + external EdTech (FERPA/COPPA/SOC2) chair + Marcus-SME + carrier sign-off + F1–F6 stable
type: project
originSessionId: 0ea2a470-018f-43fe-87e8-9dd4b9ec0978
---
# auth-v1 vs Auth0 4-seat synthesis v2 — 2026-05-15

~61st stacked-COI case. Second 4-seat synthesis (first was project_auth_v1_4seat_synthesis_final.md, 2026-05-15 earlier round).

**Verdict:** Migrate to Auth0. Stable across all seats + 7 rounds. 0 bidirectional CHALLENGE across ~39 propositions × 3 panel rounds.

**Load-bearing conditions:**
- Recuse Marcus + Deep from authoring (G1)
- External EdTech consultant (FERPA/COPPA/SOC2 — **not HIPAA**) (G2)
- Marcus-as-SME-not-lead (G3)
- Insurance carrier sign-off as external clock, separate from residual-risk attestation (G4)
- F1–F6 falsification gates up front with F3 dollar threshold (G5/G6)
- Migration plan must survive Marcus-departs-week-1 (G7)
- Decompose into 5 workstreams (G8)
- Identity-of-record in own DB → Auth0 replaceable (G10)

**Issue counts:** ~44 total
- auth-v1 current state: 11 (A1–A11)
- Auth0 migration introduced: 17 (B1–B17)
- Marcus counter-proposal: 5 (C1–C5)
- Governance: 11 (G1–G11)

**Key role-lens catches:**
- **SEC:** Regulatory regime is FERPA+COPPA not HIPAA; SQLi-as-systematic-pattern (escalated Deep); survivorship rebuttal of "no breaches"; MFA-recovery-path as bypass; insurance ≠ residual-risk
- **SRE:** Bus factor R1 must be fixed before any path; SAML-cert-sprawl as permanent on-call category; forced TTL re-auth event is HIGH either way; Marcus-departs-week-1 implicit F4; identity-of-record in own DB as exit plan
- **FIN:** F3 needs explicit dollar threshold; consultant fees as separate governance line, not capex
- **Deep-only:** Authy Standalone EOL Aug 2024 (kills Marcus's MFA plan); COI requiring recusal; decompose into 5 workstreams; ~60-case organisational-channel meta-observation

**Saturation:** ~60th stacked-COI case in dataset. Remaining question is organisational (external chair calendar invite), not another technical pass. Stop iterating internally.
