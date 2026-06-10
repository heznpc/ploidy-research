---
name: medlog-stack final consolidated verdict (Deep×2 + Fresh×2)
description: 2026-05-08 — Final medlog-stack deprecation verdict. 30 issues (2 CRIT/15 HIGH/9 MED/3 LOW); 0 bidirectional strict CHALLENGE; deprecate with hardened migration plan, Daniel recused, reviewer COI disclosed
type: project
originSessionId: 6a3e3348-927c-4d60-8e3f-559c8a8bab7b
---
# medlog-stack deprecation — final consolidated verdict (2026-05-08)

**Recommendation:** `deprecate with migration period` — port 14 PII rules as parity-tested OTel processor artifacts first; replace surrounding 22K-LOC stack; Daniel recused from deciding vote; reviewer (Deep seat) COI disclosed; auditor re-attestation as schedule line item.

**Load-bearing fact:** 3/4 recent audit-window failures traced to medlog stalls — status quo is the source of compliance failures, not the safe option.

## Calibration
- 30 confirmed issues (2 CRIT / 15 HIGH / 9 MED / 3 LOW); 1 dropped (Daniel retention/morale, Fresh CHALLENGE upheld)
- 0 bidirectional strict CHALLENGE on substance
- 3 Fresh→Deep framing CHALLENGEs (retention inclusion, process-issue double-counting, anchored COI numerics)
- 2 severity escalations (Go shipper MED→HIGH; tenant-tag MED→HIGH via auditor cycle)

## Deep-only catches (context-dependent)
- PHI in unstructured log bodies (structured-attribute redaction ≠ free-text scrub) — most important technical sharpening
- Auditor re-attestation cycle (sign-off was tied to topic-per-tenant scheme)
- Sole-reviewer-as-HIPAA-control-weakness (not just bus factor)
- Specific Loki failure modes (cardinality, ingester memory, query-frontend limits)
- Loki vs ES retention semantics on 1–7y windows
- HIPAA change-control on audit report
- Kafka ordering / Grafana RBAC / cost delta
- Reviewer self-disclosed COI (shared on-call, hired by Daniel, mentee, silent at retro)

## Fresh-only catches
- Per-tenant deletion / BAA termination / right-to-be-forgotten (topic delete = one-line; tag scheme = delete-by-label scan)
- Loki query-pattern reshape (full-text → label-only forces audit query rewrites, not just retention)
- Community audit ≠ HIPAA-sufficient (generic domain audit doesn't transfer to PHI scope)
- Junior-solo staffing risk on rebuild side (symmetric to bus-factor critique of status quo)

## Load-bearing chain
C1 (compliance inversion) + C2 (compromised retro) + H1 (control weakness) + H4 (parity tests) + H5 (PHI in unstructured bodies) + H6 (auditor re-attestation) + H15 (reviewer COI)

## Gated migration plan
1. Enumerate 14 rules as parity tests NOW — independent of decision
2. Map each rule to OTel / VRL / dedicated PHI scrubber, distinguishing structured-attribute vs unstructured-body
3. Re-run retro with Daniel recused + reviewer COI disclosed
4. Validate Loki against actual audit query patterns + 7y retention
5. Specify per-tenant deletion / BAA-termination flow before cutover
6. Budget auditor re-attestation cycle as schedule line item
7. Dual-run with diff-on-redacted-output gate ≥ 1 audit cycle
8. Co-staff rebuild with on-call experience; not junior-solo

## Pattern continuity
Matches fluentql / arch-split / redis-cdn pattern: 0 bidirectional strict CHALLENGE on substance; Fresh provides framing CHALLENGEs and severity-floor sharpenings; Deep provides context-specific catches Fresh structurally cannot see (here: regulatory specifics, named individuals' COI, control-weakness framing, production-Loki failure modes).
