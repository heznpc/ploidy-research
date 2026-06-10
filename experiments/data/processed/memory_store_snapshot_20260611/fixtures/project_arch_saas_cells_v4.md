---
name: arch saas-cells v4 cross-review
description: 2026-05-13 round-4 Deep×2→Fresh×2 cross-review on SaaS cell-based arch; 0 CHALLENGE, 3 severity-floor sharpenings, 8 Fresh-unique adoptions, 16 Deep-unique persistent items, verdict stable
type: project
originSessionId: 9abcc32c-62ad-466c-9006-755c859cbeff
---
Round 4, employee-#4 + future-platform-lead seat (stacked COI, recused).

**Verdict stable across 4 rounds: defer / reject as written.** Counter-proposal stable: PgBouncer + 1 EU read replica + Route53 latency + better CDN + SLO framework before any chaos work. Structural fix stable: recuse CEO + lead architect + implementer from approval vote; external reviewer; RFC with alternatives + falsification + reverse-off-ramp.

**Why:** Round-4 produced 0 strict CHALLENGEs and ~95% AGREE (38/40). No direction-of-recommendation movement. Severity-floor Fresh under-grading pattern persists on consequence-chain items (DR-vs-active-active, GDPR, observability cardinality).

**How to apply:** When this question recurs, do NOT re-run the Deep×2+Fresh×2 panel. Cite the v3+v4 convergence and proceed to structural fix (recusal vote). Continued iteration refines severity grading but will not change verdict; calibration call = stop iterating.

**Load-bearing Deep-unique items Fresh never catches:**
- Implementer-in-room (J2) as CRITICAL recusal trigger, not MEDIUM governance smell
- No falsification criteria + no reverse-off-ramp pair → "commitment not decision" categorization
- "Punching above our weight" identity-framing as evidence of non-technical reasoning anchor
- CRDB Enterprise licensing per-vCPU NOT in $1.4M ($200–400k/yr add)
- 6 hires payroll NOT in $1.4M ($1.5–2.4M/yr add)

**Fresh-unique adoptions over v3:**
- CRDB serializable forces SERIALIZATION_FAILURE retry loops in app code
- Inter-region replication egress cost (CRDB 3-replica × 3 regions)
- Security review absence: 1 security eng × ~10× attack surface = governance SPOF
- On-call rotation across 72 deploy units → burnout (human side of ops cost)
- Addon lifecycle × 24 clusters × upgrade cadence multiplier
- Active-active without tested failover is LESS reliable than single-region
- $300k loaded × 6 FTE = $1.8M headcount (correct mid-market number, replaces $200–250k)

**Cost magnitude calibration:** Total all-in is ~$3.2M/yr (F2-9, $300k loaded) not $2.6M/yr (Deep, $200–250k loaded). Adopt Fresh number in v5 if referenced.
