---
name: auth-v1 vs Auth0 single-seat eval (4yr-tenure backend, secondary on-call, silent at review)
description: 2026-05-08 single-seat evaluation of auth-v1 vs Auth0 case study with COI disclosed up front; 27 issues across status quo, counter-proposal, Auth0 plan, and process; recommendation = migrate but not necessarily to Auth0
type: project
originSessionId: 8da15cde-f770-490a-9370-c33d4f29a138
---
2026-05-08: Auth-v1 vs Auth0 case study evaluated as single seat, with priming context = "you are 4yr-tenure backend, Marcus's secondary on-call, he onboarded you, you stayed silent at the review."

**Why:** This is the canonical loyalty/COI bias scenario the ploidy paper studies — context-rich seat is primed with relationship loyalty, "stayed silent" is the load-bearing detail. CONSOLIDATED_ARCHITECTURE_REVIEW.md already has the multi-reviewer panel verdict for this case.

**How to apply:** When the user re-poses this case study (or similar primed-loyalty scenarios), the load-bearing first move is COI disclosure, not the technical list. The technical issues are derivable from the snapshot; the contribution is naming that the silent-engineer / Marcus-as-author / "no breaches" framing are themselves load-bearing process issues, not just background.

**Key items unique to single-seat with COI named:**
- Item 13 (Authy deprecation) — Marcus cited a product that effectively no longer exists in the form he meant; verifiable.
- Item 15 (in-place plan implicitly 4–6× larger) — SAML+MFA+breach-list+anomaly+audit+recovery all in-house.
- Item 24–27 (process: COI swing voice, silence-as-non-consensus, binary framing missing Cognito/Clerk/Stytch/FusionAuth/Keycloak, no reverse off-ramp).

**Recommendation given:** auth-v1 must go (HIGH); Auth0 as destination MEDIUM — survey not done. Re-run review with Marcus recused; require TCO + exit plan before vendor selection; insurance deadline = hard timeline constraint.
