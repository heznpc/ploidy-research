---
name: medlog-stack deprecation Deep×2+Fresh×2 verdict
description: 2026-05-08 — 49-issue verdict on HIPAA medlog-stack rebuild; recommendation = Daniel-recuse + 4-way decomposition + parity test suite + harden migration; load-bearing chain S4+DD1+DD4+P8+G1+G2+G8
type: project
originSessionId: 3b3fd7ac-c539-4025-9d50-78e099866dad
---
Final verdict on Daniel's medlog-stack defense vs. junior engineer's OTel/Loki rebuild proposal.

**49 confirmed issues:** 4 CRIT / 33 HIGH / 10 MED / 2 LOW.

**CRITICAL (4):**
- S4: 7h pipeline / 1h margin / 3-of-4 audit-window failures = ~99% empirical HIPAA SLA (5th-Fresh escalated from HIGH)
- P8: WORM/immutable audit sink for HIPAA 164.312(b) — Loki doesn't provide natively (5th-Fresh escalated; only Deep2 raised)
- G1: Daniel recuses from go/no-go vote (unanimous, load-bearing structural fix)
- G2: 4-way decomposition — Kafka topics / shipper / indexer = replace; redactor = extract & port (load-bearing structural fix)

**Load-bearing chain:** S4 + DD1 (14 cases enumerable) + DD4 (redactor ≠ whole stack) + P8 + G1 + G2 + G8 (Daniel designs parity suite, doesn't vote).

**Convergence:** 0 strict bidirectional CHALLENGEs on substantive findings; ~80% overlap; 4 SYNTHESIZE escalations; both Deep reviewers correctly disclosed COI (hired by Daniel, joint on-call, silent in retro).

**Deep-only catches** (12+): reactive-only redactor as liability not strength (Deep2), Loki cardinality recreates topic problem (Deep2), WORM sink (Deep2), reverse off-ramp (D1+D2), carrying-cost ledger (D1), authority asymmetry as argument structure (D1+D2), 4-way decomposition framing.

**Fresh-unique sharpenings** (5+): retrospective verdict already exists (F2), test suite extraction is valuable in *either* path (F1), conflation of redactor with whole stack named clearly (F1+F2).

**5th-Fresh panel gaps:** historical ES data 6yr retention migration, vendor branch (Grafana Cloud vs self-hosted), audit-report downstream consumers, DR/regional failure, operational ownership of new system (if Daniel still runs collectors, bus factor unchanged), falsification criteria for cutover.

**5th-Fresh CHALLENGEs:** "junior" framing inherited uncritically; "14" is Daniel-anchored unverified count; Deep2's 14-case examples are inferred not given; "open-source audited" critique over-amplified.

**Recommendation pattern matches earlier deprecation reviews** (fluentql, arch-split): proposer/builder COI requires recusal; defense conflates *experience* (portable) with *implementation* (replaceable); status quo not safe just because familiar.
