---
name: auth-v1 panel response r4 (Deep r6/r7 thin)
description: 2026-05-15 ~60th stacked-COI case — 4th SEC+SRE+FIN panel per-point on auth-v1 Deep×2 r6/r7 (very thin, ~5 props each); 0 CHALLENGE; FERPA-not-HIPAA correction + Authy-which-product clarification + explicit-dollar-threshold on F3 gate; saturated
type: project
originSessionId: 1ac10086-1b8b-4a35-a30a-4d3a116a5c3c
---
2026-05-15. ~60th stacked-COI case in project dataset. 4th per-point panel response on auth-v1 vs Auth0.

**Input shape:** Deep×2 outputs were thin compression rounds (~5 propositions each, mostly procedural saturation acknowledgements), not fresh issue enumerations. Same seat composition as r1–r5.

**Panel composition:** SEC + SRE + FIN (3 lenses).

**Outcome:**
- 0 bidirectional CHALLENGE across all ~10 Deep propositions × 3 panel lenses.
- 100% AGREE on verdict (migrate), recusal-of-3, external review, Marcus-as-SME, Authy-EOL warning, saturation call.

**Panel-unique sharpenings this round:**
1. **FERPA-not-HIPAA correction (SEC):** Deep r7 said "external HIPAA/SOC2 consultant." Wrong regulatory regime — EdTech with 14M minors is FERPA + COPPA, not HIPAA. Pick EdTech-experienced consultant, not healthcare.
2. **Authy-which-product (SEC/SRE/FIN unanimous):** Authy Standalone Application = EOL Aug 2024; Twilio Verify API = current product. Marcus's counter-proposal must name which one before any comparison is possible. SDK, on-call surface, and pricing model all differ.
3. **F3 dollar threshold (FIN):** Cost-blowout falsification gate currently qualitative; should have explicit halt-and-rebaseline thresholds (e.g., $250K total / $X per MAU year-1).
4. **F4 implicit gate — Marcus unavailable (SRE):** Migration plan must survive Marcus-departs-week-1 scenario, not week-N. Bus-factor-of-1 (R1) is path-independent.
5. **Carrier sign-off ≠ residual-risk attestation (SEC):** Insurance signing off on the plan is a different attestation than signing off on migration-window risk (R11/R12). Two separate documents.
6. **External-review cost as governance line not project line (FIN):** $5–15K SEC + $5–15K SRE/IdP consultants should be capex'd as governance control, not folded into implementation budget.
7. **Exit plan as concrete data control (SRE):** Keep identity-of-record (email, district, role) in our DB to make Auth0 replaceable — concretises the abstract "exit plan."

**Saturation signal:** 3rd consecutive panel pass on auth-v1 with 0 CHALLENGE. Combined with ~7 single-seat COI rounds (r1–r7), this case is now at ~10 internal review rounds total. Pattern is at peak strength of the dataset.

**Recommendation:** stop iterating internally. Remaining action is organisational — calendar invite for external chair, not r8/r5-panel/etc.
