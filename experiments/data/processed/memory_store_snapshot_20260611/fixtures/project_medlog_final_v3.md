---
name: medlog deprecation final v3 (Deep×2+Fresh×2+bidirectional)
description: 2026-05-08 medlog round-3 verdict — 41 issues (2 CRIT/25 HIGH/12 MED/2 LOW-MED); deprecate w/ migration period; rules-extraction-first; per-tenant deletion semantics + 6yr ES retention as biggest panel-wide gaps
type: project
originSessionId: bdb8a267-f2bb-4e5c-bc12-c4b9ebb51a81
---
Round-3 medlog verdict (separate iteration from v2's 52-issue panel; this round had narrower input).

**Disposition:** `deprecate with migration period`. Recuse Daniel from the decision; he leads 14-rule extraction. Independent migration owner named before work starts. Frozen prod-derived redaction corpus. Dual-run ≥N clean audits. Auditor re-attestation. Reviewer COI disclosed in retro minutes.

**Convergence:** 0 strict CHALLENGE bidirectional. ~85% overlap. Severity-floor pattern reproduces (Fresh under-grades HIPAA-consequence-chain → MED→HIGH on #19, #25, #31). Stop iterating.

**Counts:** 41 issues — 2 CRIT, 25 HIGH, 12 MED, 2 LOW–MED.

**CRITICALs (load-bearing):**
- #1 — 3/4 audit failures already trace to medlog; status quo non-compliant *now*
- #20 — 14 rules must port with frozen prod-derived regression corpus or cutover = HIPAA breach risk

**Panel-wide gaps surfaced by Fresh-cross 5th pass (high-value catches):**
- Per-tenant deletion / breach-scoping under HIPAA — topic-per-tenant bought mechanical drops; tag-based must re-implement, not inherit (HIGH, biggest miss)
- 6-year HIPAA retention of existing ES data is unpriced migration precondition (HIGH)
- 8 services' own logging assumptions — may be 8 app-side projects, not a pipeline swap (MED–HIGH)
- "Daniel recused" without named migration owner = work doesn't happen (HIGH)
- ES SSPL relicense as unstated motivator — reframes Loki-vs-ES as OpenSearch-vs-Loki (MED)
- Symmetry — proposer must pass a stub of 14-rule tests *before* approval, not as part of migration (MED)

**Deep-only (structurally invisible to Fresh):**
- Recusal-not-raised at retro
- 2019 maturity premise expired in 2026
- Reviewer's own-silence governance failure (Fresh CHALLENGED scope — moved to disclosure section, not load-bearing)

**Fresh CHALLENGE on Deep:** Deep-2's "my silence is a governance failure" disclosure moves the document from evaluation → evaluation+personal disclosure. Architectural argument survives without it; should be in a separate disclosure section. Adopted.

**Why:** 3rd recurrence of author-defends-custom-tool pattern (after fluentql, medlog v2). Bidirectional cross-review reliably surfaces ~6 panel-wide gaps single-direction reviews miss.

**How to apply:**
- For HIPAA-scope deprecations: per-tenant deletion semantics + multi-year retention of existing audit substrate are first-class migration preconditions, not implementation details.
- "Recuse author" without naming a replacement migration owner is incomplete recusal; verdict must specify both.
- Symmetric burden of proof: if proposer demands author write the 14 rules as tests, proposer must demonstrate the proposed tooling passes a stub of those tests *before* approval.
- Severity-floor escalation (Fresh MED → HIGH on consequence-chain items) is reproducible — apply without re-debating.
