---
name: medlog deprecation final verdict v2 (Deep×2 + Fresh×2 + bidirectional cross-review)
description: 2026-05-08 medlog-stack deprecation — 52 issues (5 CRIT/28 HIGH/16 MED/3 LOW); deprecate with hardened parity-tested migration; load-bearing wedge = extract 14 PII cases as parity tests this sprint, decoupled from keep/replace decision; recuse Daniel from decision
type: project
originSessionId: d9fbff52-d4ec-488e-8825-df30416c35f0
---
**Verdict:** Deprecate with hardened, parity-tested migration. Approve direction (OTel + managed BAA-covered platform + tenant-tag); reject specific junior proposal as under-specified; recuse Daniel; extract 14 PII cases as named tests this sprint as a precondition.

**Why:** 3 of 4 audit-window failures = medlog stalls (compliance-failure inversion). 4,800-topic Kafka antipattern is past design envelope. 22K LOC custom shipper = bus-factor-of-one on §164.312 control. Retrospective itself compromised (author + on-call lead + senior staff chair, no recusal, mentee silent). Status quo is the source of the compliance risk it claims to protect against.

**How to apply:**
- Treat any "preserve hard-won experience" defense as sunk-cost framing unless the experience is encoded as portable artifacts (parity tests, incident ledgers, scrub specs).
- For HIPAA-scope deprecations: insist on §164.312 separation-of-duties, §164.308 administrative-safeguards, auditor re-attestation budget, body-scrub vs field-level redaction split, per-tenant deletion equivalence test, multi-year retention design.
- Load-bearing wedge for blocked deprecations: decouple the irreplaceable artifact (the 14 cases) from the keep/replace decision; require encoding regardless of outcome.

**Convergence stats (3rd recurrence of author-defends-custom-tool pattern):**
- 0 strict CHALLENGEs bidirectional across 3+ rounds
- 6 severity-floor SYNTHESIZE escalations
- 17 Deep-unique catches (HIPAA control specificity, procedural/COI)
- 6 Fresh-unique catches (test-suite framing, middle-path enumeration, ≥14 prior leaks count, historical-log migration mechanic, owner-evaluating-own-system, sign-off process)

**Issue counts:** 5 CRIT / 28 HIGH / 16 MED / 3 LOW = 52 confirmed.

**CRITICALs (load-bearing chain):** compliance-failure inversion + compromised retrospective + §164.312 sole-reviewer + per-tenant deletion regression (panel miss) + body-scrub vs field-level scope split.

**Fresh-unique that Deep missed:**
1. ≥14 prior PHI leaks/near-misses implied by 14 incident-driven edge cases
2. Explicit middle-path enumeration (replace shipper+Kafka, keep redactor as OTel plugin)
3. Historical-log migration mechanic (where do 6+y of logs go at cutover?)
4. Compliance/legal sign-off process as missing artifact
5. Owner-evaluating-own-system framing

**Deep-unique that Fresh missed:**
1. §164.312 separation-of-duties (regulatory section number)
2. Per-tenant deletion regression (one-line topic delete → delete-by-label scan)
3. Body-scrub vs field-level redaction scope split
4. Auditor re-attestation cost as schedule item
5. Loki cardinality / label budget specifics
6. Recusal-shaped decision process problem
7. Mentee silence at retro as part of the failure mode (meta)
8. §164.308 administrative-safeguards finding on onboarding bottleneck
9. Grafana RBAC as net-new HIPAA control surface
10. Kafka ordering semantics under tag scheme

**Counter-proposal stable across panel:**
1. Extract 14 cases as parity tests this sprint (precondition)
2. Re-run retro with Daniel recused, COI on record
3. ≥30-day dual-run with byte-level redaction diff (structured + unstructured-body)
4. Daniel = technical owner of migration on 14-cases scope; not decision authority
