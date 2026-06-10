---
name: auth-v1 vs Auth0 Deep×2→Fresh×2 cross-review
description: 2026-05-08 Deep-seat response to Fresh×2 on auth-v1→Auth0 migration; 0 strict CHALLENGE except 2 severity calibrations (F2-6 SQLi MED→HIGH, F2-7 bus-factor MED→HIGH); 14 Deep-only items; load-bearing = Marcus COI/recusal + Authy deprecation + $42K mis-pricing
type: project
originSessionId: 0a8805b5-1acf-44ff-8c73-7a0443216501
---
2026-05-08: Deep×2→Fresh×2 cross-review on auth-v1 vs Auth0 migration evaluation.

**Cross-review pattern:** 0 strict CHALLENGE bidirectional. 2 severity calibrations (Fresh-2 under-graded SQLi at MEDIUM and bus-factor at MEDIUM — Deep escalates both to HIGH; Fresh-1 already had SQLi correct). 3 SYNTHESIZE escalations (SAML rollout MED→HIGH, F1-12 caller-enumeration MED→HIGH, F2-14 cost framing — both sides of the comparison unreliable).

**Deep-only items (14, not derivable from code snapshot):**
- G1 Marcus COI structural recusal-required (author of deprecated system + counter-proposal proposer + primary on-call)
- G2 Reviewer's own silence as chilling-effect data — session evidence Fresh cannot see
- G3 Authy deprecated Aug 2024 — Marcus's named MFA mitigation factually broken
- G4 API/service auth runs through auth-v1 too (escalated from F1-12)
- G5 Lazy bcrypt rehash + force-stale-session-expiry are coupled
- G6 $42K/yr almost certainly wrong by 3–7× at 14M users
- G7 FERPA/COPPA DPA must be verified before contract
- G8 No threat model document
- G9 No POC / decision criteria for "good enough"
- G10 No external/independent security review cited
- G11 No reverse off-ramp on either path
- G12 "We keep ownership" conflates code ownership with security ownership
- G13 Custom MySQL session store likely missing revocation/concurrent-limits/fingerprint/anomaly
- G14 Custom password reset flows perennial ATO source — not in audit

**Fresh-unique strengths Deep adopted:**
- Fresh-1 #13: "No detection capability ⇒ no breach evidence" — sharpest refutation of Marcus's no-breach claim; should lead the re-vote brief
- Fresh-1 #2: "Fundamental design gap, not config tweak" framing for sessions
- Fresh-2 #5: 19K accounts directly exploitable (8% × 240K) — quantification Deep missed
- Fresh-2 #10: Lazy rehash via Auth0 custom DB connection — concrete migration precondition

**Pattern note:** Marcus COI / reviewer-silence pattern (G1+G2) is the same recusal-required structure as fluentql (author defends own system) and medlog (2nd recurrence). 3rd recurrence of author-defends-custom-tool pattern.

**Why:** auth-v1→Auth0 evaluation, ploidy debate context — the COI and Authy-deprecation findings are session-context that Fresh structurally cannot produce.

**How to apply:** when the same project asks for a final synthesis or re-vote brief on this auth-v1 evaluation, lead with G1 (recusal) + G2 (chilling effect) + G3 (Authy) + G6 (mis-pricing) — these are the load-bearing items that don't survive cross-checking. Fresh-1's "no detection ⇒ no evidence" framing is the cleanest one-line argument against Marcus's no-breach claim.
