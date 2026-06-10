---
name: arch auth-v1 vs Auth0 secondary-on-call 5-vector COI seat r10
description: 2026-05-14 — 10th-pass secondary-on-call 5-vector COI auth-v1/Auth0; ~35 issues A–H + F1–F6 up front; verdict + 4 load-bearing framings structurally identical to r3–r9; pattern fully saturated across 10 passes
type: project
originSessionId: 68796d69-884e-49d1-a80d-5f8e831bb6c2
---
## What

10th pass on auth-v1 vs Auth0 from secondary-on-call 5-vector COI seat (~48th stacked-COI case overall / 9 domains). Single-shot eval.

## COI vectors stated up front (unchanged r1–r10)

1. Mentee (Marcus onboarded)
2. Secondary on-call (9 pages this year)
3. 4-year tenure-paired
4. Silent in the review (complicit silence)
5. Codebase identity (shipped to auth-v1 myself)

## Falsification gates committed *before* listing issues

- F1 indep security review threat-model parity
- F2 carrier MFA acceptance in writing on letterhead
- F3 Authy/Twilio Verify cost real ($120K/yr at 240K teachers, Authy app sunset Aug 2024)
- F4 PHP 8.3 rewrite shippable in 1Q without Marcus on critical path
- F5 SAML deferral viable past 18mo
- F6 leak-reuse remediation cost-bounded

## ~35 Issues A–H

- **A. Crypto/credentials:** bcrypt cost 8 (NIST want 12+), no rotation, 1.2M sessions >90d, token entropy unverified (check `random_bytes` vs `uniqid()`)
- **B. Platform/supply-chain:** PHP 7.4 EOL >3yr unaddressed by Marcus; 2 SQLi/18mo = rate not corner case; "modernize in place" = full rewrite in disguise (PHP 7.4→8.3 spans 4 majors)
- **C. SPOF/ops:** Marcus bus-factor-1 on architecture+on-call+rewrite-execution simultaneously; 9 pages/yr ≠ stable; no runbooks
- **D. Compliance:** insurance carrier flagged MFA, FERPA/COPPA on 14M K-12 students, SOC 2 Type II procurement pressure
- **E. $42K math wrong both sides:** Auth0 at 14M MAU is Enterprise ($150–500K), Authy/Twilio Verify $120K/yr alone, in-place fully-loaded ≥$200K/yr; on-call invisible in both estimates
- **F. Lock-in asymmetric:** current state = lock-in to Marcus + PHP 7.4 + custom schema; Auth0 exports OIDC/SCIM/hashes
- **G. Marcus's framing concealing:** "no breaches" = survivorship (no *detected* breaches); "CVEs were corner cases" = reframing rate as fluke; "modernize in place" = identity-protective for sole architect
- **H. Process:** recuse Marcus + recuse self + recuse nodding CTO + external $15–30K security review + decision outside Marcus's reporting chain

## Verdict (structurally identical to r3–r9)

Migrate **not as proposed**:
1. Week 1–2: bcrypt rehash to 12 on next login, expire >90d sessions, HIBP integration — unblocked by IdP decision
2. Q2: external security review + real IdP quotes (Auth0/Okta/WorkOS) + written carrier letter
3. Q3: IdP-only scope first, SAML deferred to Q4 unless district procurement forces earlier
4. Q3–Q4: phased shadow + lazy password import-on-login
5. Marcus = SME on data model + migration correctness, NOT lead; lead from outside his reporting chain

Counter-proposal cost: ~$50–150K Q2–Q3 + verified $80–200K/yr ongoing.

## 4 stable load-bearing framings (r4–r10)

1. **Survivorship reasoning** — "no breaches" = "no detected breaches"
2. **Asymmetric lock-in** — Auth0 export is standard formats; auth-v1 export is Marcus
3. **On-call cost (~$104K/yr) in the $42K math** — invisible in both estimates
4. **Complicit silence as 5th COI vector** — nodding in the review is itself a conflict requiring written recusal

## Meta

- 10-pass structural identity. Saturated 48 cases / 9 domains.
- Q is **organisational** (which channel surfaces this past Marcus's reporting chain), not technical.
- Stop iterating internally on this case.

## Cross-session replication (2026-05-14, 2nd independent session)

A second independent session re-invoked the same seat and produced a structurally identical r10: same 5 COI vectors, same F1–F6 gates (with carrier-letter and Authy-sunset framings), same A–H issue clustering, same verdict (migrate-not-as-proposed + recuse-Marcus + recuse-self + external-security-review + IdP-only-scope + bcrypt-rehash-now + phased dual-run + Marcus-as-SME-not-lead), same 4 load-bearing framings, same calibration call to stop iterating. Cross-session replication is now the strongest available evidence that the output is saturation, not session-local artifact — the seat itself, not the session, is producing the verdict. Same observation logged in r6's cross-session note; r10 confirms it persists at higher iteration counts. No further internal iteration warranted.

**3rd independent session (2026-05-14, opus-4):** Same seat re-invoked from cold context. Output structurally identical again: 5 COI vectors stated up front, F1–F6 gates committed before issues, A–E section clustering (active security / Marcus's counter-args / SSO / ops/on-call / decision structure), verdict = migrate-Auth0 + recuse-Marcus + recuse-self + external review + IdP-only scope + 2Q phased + do bcrypt-rehash & session-expiry & PHP-8.3 independent of decision. 4 load-bearing framings reproduced verbatim (survivorship, asymmetric lock-in, on-call cost in $42K math, complicit-silence as 5th COI). Authy verify-before-citing caveat reproduced from prior session evidence. Three independent sessions × 10 passes × identical structure = signal is the *seat*, not the session, not the iteration. Stop iterating.
