---
name: arch eval auth-v1 vs Auth0 — secondary-on-call stacked-COI seat
description: 2026-05-14 single-seat auth-v1 vs Auth0 migration eval from 5-vector COI seat (4yr alongside Marcus + onboarded-by + secondary on-call + silent-in-review + bidirectional material interest); ~54 issues A–G with falsification gates up front; verdict = leave auth-v1, recuse-of-3, $30–60K external pentest + threat model first
type: project
originSessionId: ad9fe482-39c0-4331-89df-fd3fdd6ddd90
---
# Auth-v1 vs Auth0 — secondary-on-call stacked-COI single-seat eval

## Context

- Case: EdTech 14M students / 240K teachers; auth-v1 = custom PHP 7.4 by Marcus Chen (5yr tenure); proposed Auth0 migration at $42K/yr.
- Audit findings: 1.2M sessions >90d, 8% teachers leaked-password, insurance flagged no-MFA as policy non-compliance.
- Seat: 4yr alongside Marcus + onboarded by him + secondary on-call (9 pages/yr) + attended review silently + bidirectional material interest (on-call burden ↓ if migrate, expertise depreciates if migrate).

## Why save

First auth-vs-vendor architecture seat in memory; complements the SaaS-cells / arch-split / Redis-CDN series. Notable for **bidirectional material interest** — most prior seats had unidirectional COI (sunk-cost defending the build). Here both outcomes hurt the seat differently, which is a distinct flavor of COI worth flagging.

**Why:** Future auth/identity/vendor-vs-build decisions land in this same seat pattern; the bidirectional-COI framing should be reused. Also first seat where the proposer's plan was **factually wrong on a named API** (Authy app sunset Aug 2024) — a useful tell that "modernize in place" wasn't researched.

**How to apply:** When user asks for arch eval where they have stacked COI with the system author, lead with COI disclosure + falsification gates, then issue list, then recuse-of-N recommendation. Same template as `project_arch_saas_cells_emp4_round*` series.

## Falsification gates (committed up front)

1. F1 — pentest finds no credential-stuffing/session/SQLi exposure + PHP 7.4→8.3 <3 sprints → in-place viable
2. F2 — verified Auth0 quote at 14M MAU >$200K/yr → flips vendor choice not direction
3. F3 — insurance accepts in-place + MFA in writing → relaxes timeline
4. F4 — Marcus commits 60-day milestone (cost-12 bcrypt, idle TTL ≤30d, Twilio Verify, >50% MFA enrol) with tripwires → in-place gains evidence
5. F5 — district SAML audit shows <10 districts → shrinks SAML scope
6. F6 — find one engineering peer who'd vote against in-place out loud → falsifies coercive-structure claim

## Issues (~54 across A–G)

- **A. auth-v1 security posture (11 items)** — PHP 7.4 EOL, bcrypt-8 measurable weakness (~10K guesses/sec GPU vs ~1K at cost 12; 8% × 240K = 19.2K crackable), sessions never rotate, no MFA (K-12 dominant vector: PowerSchool 2024–25, Illuminate 2022), 2 SQLi CVEs/18mo = defect-density base rate alarm, cookie flags unverified, no login rate limiting, bus-factor=1, no threat model
- **B. Compliance (6 items)** — insurance non-renewal existential, FERPA reasonable-security, COPPA under-13, district RFP MFA+SSO table-stakes, HIBP rotation same-week regardless of vendor, no ATO monitoring
- **C. Marcus's in-place plan technical problems (11 items)** — **Authy sunset Aug 2024 (plan factually wrong)**, PHP 7.4→8.3 not "in place" (string-coercion, each(), libxml, gd, multi-quarter), staged 8.0→8.2→8.3 required, MFA scope understated (recovery codes, device binding, admin policy), session sweep ≠ idle/absolute TTL, bcrypt rehash only covers active users, SimpleSAMLphp signature-wrapping CVEs recur, WebAuthn/passkeys omitted, no falsifiable milestones, no total cost (Marcus loaded ~$300K × 2–3Q ≫ $42K/yr vendor)
- **D. Auth0-specific risks (6 items)** — lock-in bounded (export bcrypt hashes), Okta acquired 2021 (5yr stable pricing data > hypothetical), $42K quote at 14M MAU suspicious low (likely $100–300K), EU residency, outage blast radius, Okta-incident downstream risk
- **E. Migration execution (7 items)** — hash import doesn't fix cost factor, 1.2M session cutover = schedule for summer, SAML per-district = customer-success person-years, PHP integration surface (miss-one-route = bypass), COPPA child-friendly flow, SIEM log export scoping, rollback/dual-write plan
- **F. Process/governance (7 items)** — author = sole technical voice (self-eval ≠ review), 3 stacked-COI closest to decision, silence-as-data, no external security review, no falsification criteria, audit/insurance = external evidence status quo isn't holding, no credential-stuffing IR runbook
- **G. Both plans omit (6 items)** — same-week HIBP rotation, admin MFA non-negotiable, login anomaly detection, FERPA audit log + retention, account recovery flow, service-account/API-key handling

## Verdict

- **Direction:** leave auth-v1; status quo failing on (insurance + audit + leaked-password + EOL runtime + bus factor); in-place plan factually wrong on Authy + under-scopes PHP upgrade + omits SAML
- **Vendor:** Auth0 viable but $42K needs verification; WorkOS/Cognito/Keycloak in comparison; decision is "leave auth-v1" not "Auth0 specifically"
- **Recuse-of-3:** Marcus (author), me (4yr+onboarded+secondary on-call), CTO if sponsored original build
- **Counter-proposal:** ~$30–60K external pentest + threat model + same-week hardening (HIBP rotation, admin MFA, rate limit, idle TTL), then vendor selection with verified quotes
- **Confidence:** MEDIUM — technical case strong, COI also strong; my read should not be load-bearing

## Pattern notes for future seats

- Bidirectional material interest is a distinct COI flavor — flag it explicitly rather than collapsing to "sunk cost"
- Named-API factual errors in proposer's plan (Authy sunset) are a strong tell that the alternative wasn't researched; cite specifically
- "We keep ownership" framing hides upstream-dependency cost (here: SimpleSAMLphp) — name the hidden dependency
- Self-evaluation by author in single review = coercive-structure, same as SaaS-cells and arch-split series
