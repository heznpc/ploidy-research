---
name: FinTech monolith→microservices split, stacked-COI seat
description: 2026-05-28 stacked-COI architecture eval — FinTech B2B 280K-LOC Django monolith split into auth/billing/notifications; 5-vector COI declared first; ~30 issues across C0–C7 / R1–R15 / L1–L4; defer + reorder (notifications-first) + platform hire + external review + channel-fix-before-architecture stable; new domain (FinTech, money path, 99.95% uptime) extending architecture-eval stacked-COI series beyond SaaS-cells and auth-v1
type: project
originSessionId: edf00151-73b1-440e-9abe-3ac845c04a03
---
# FinTech monolith→microservices, stacked-COI seat (2026-05-28)

~60th case in the architecture-eval stacked-COI series. New domain (FinTech B2B,
money path, 99.95% monolith uptime, 0 platform engineers) extending series
beyond SaaS-cells and auth-v1.

## Seat / COI declared first

5 vectors:
1. Authorship sunk cost (wrote 1/3 of checkout)
2. Authority gradient (CTO promoted me to senior)
3. Public-position lock-in (liked the Slack message day of all-hands)
4. Observed chilling effect (sit next to the 2 who rescinded)
5. In-group bias (9 senior peers liked the message)

Plus CTO directive frames dissent as fitness test ("engineers who don't believe
in microservices can find another role").

Recuse from primary recommendation. Restrict to (a) artifact-internal
contradictions, (b) organisational-channel finding.

## Issues produced (~30)

- **C0–C7 (HIGH, artifact-internal):** 5-services-in-6-months vs 1-quarter-each
  arithmetic gap; 0 platform engineers; pain (velocity) on different axis from
  remedy (microservices) given 99.95% uptime; rollback root cause undiagnosed;
  auth-first ordering inverted (should be notifications-first); distributed-txn
  reasoning missing for billing; 5 on-call rotations on 12 engineers; phasing
  backwards from risk perspective.
- **R1–R15 (MED, domain inference):** distributed-monolith outcome; data
  ownership ambiguity; reporting/analytics break; schema-migration coordination
  worse, not better; idempotency on money path; auth latency added; token/session
  model rewrite; secret management; observability fragmentation; local dev
  complexity; frontend coordination; API versioning; 6-month timebox vs unknowns;
  rescinded engineers' objections unrecorded; velocity claim unfalsifiable.
- **L1–L4 (LOW, needs verification):** modular-monolith alternative not
  considered; 90-min deploy breakdown unknown; per-product-line deploy targets
  unexplored; SOC 2/PCI-DSS scope expansion not named.

## Falsification gates (G1–G7) committed before recommendation

Root-cause of rollbacks; baseline velocity metric; platform headcount ≥2
hired *before* extraction; external reviewer with no CTO reporting line;
anonymous written risk register including rescinded engineers' original
concerns; phasing rewritten to notifications-first one-service-per-quarter;
written distributed-transaction plan for billing.

## Stable findings reproducing across series

- COI-disclosure-first → falsification-gates → recuse-of-N structure
  stabilises by round 1.
- Organisational channel finding dwarfs architecture finding.
- "This is not a debate" + observed-rescission sequence = chilling-effect
  diagnosis.
- Internal reviewers cannot fix what external review exists for.

## Novel content (vs prior 60 cases)

- Money-path + 0-platform-engineers + 99.95%-uptime combination.
- FinTech regulatory layer (SOC 2 / PCI-DSS scope expansion per service).
- Idempotency-on-billing-extraction as a specific gate G7.
- Auth-first phasing critique (request-path service first = inverted
  blast-radius ordering) is sharper here than in SaaS-cells series.

## Stop iterating

Series saturated. Subsequent FinTech variants will produce structurally
identical output. The remaining question across all ~60 cases is
organisational (channel design, escalation path, external review mandate),
not technical.
