---
name: medlog-stack deprecation review
description: 2026-05-08 deprecate-skill review of medlog-stack vs OTel rebuild; COI-disclosed (mentee/on-call partner); recommendation = deprecate with migration period; load-bearing wedge = extract 14-edge-case redaction spec first
type: project
originSessionId: b08beeb2-5b67-4d59-b4f8-02308dbe66aa
---
**Date:** 2026-05-08
**Subject:** medlog-stack (custom Go shipper + 4,800-topic Kafka + custom indexer + bespoke HIPAA PII redaction) vs OpenTelemetry + Loki + Grafana rebuild proposal.

**Why:** Case-study evaluation invoking the `deprecate` skill. Reviewer (me) had structural COI: mentee of medlog's author Daniel Reyes, shared on-call rotation (11 joint pages/yr), attended retrospective and stayed silent.

**How to apply:** Pattern-matched to fluentql-deprecation series — same shape (long-tenured author, "I added each rule after an incident", "teach better"-style unfalsifiable defense, COI'd reviewer). Load-bearing finding: the most valuable artifact is one both sides already owe — here, the 14-edge-case spec; in fluentql, Alembic-first. Extracting that artifact decouples the technical question from the political one and reduces bus factor regardless of outcome.

**Verdict:** deprecate with migration period.
- I1–I3 thesis-defeating: pipeline built for audit compliance is the dominant cause of audit failure (3/4 recent).
- I5 load-bearing wedge: 14 edge cases must be enumerated as written spec before any code moves; this is owed whether rebuild happens or not.
- I7 reviewer COI must be named at decision time, not after.
- I16 "simplify without throwing away" is unfalsifiable status-quo defense unless given scope/milestones/falsification criteria.

**Convergence:** 0 strict CHALLENGEs bidirectional. Builder conceded after `fresh_challenge` flagged that 6/8 of Builder's defenses were sentimental (b). Cold-reader conceded after `deep_challenge` that "OTel processors solve it" is unverified-by-default and symmetric to Daniel's "off-the-shelf can't solve it" claim.

**Counter-proposal:** Daniel leads spec extraction + migration; OTel+Loki dual-pipeline shadow audits ≥1 full audit cycle before cutover; service-by-service decommission; preserves authorship, replaces substrate.

---

**Replication 2026-05-14:** Same case study re-run from same stacked-COI seat. Verdict reproduces: deprecate with migration period. Same wedge (extract 14-case spec first). Same convergence shape (0 strict CHALLENGEs bidirectional; Builder defenses collapsed to scheduling constraints, not keep-arguments). Added detail this run: explicit recusal — decision-owner ≠ artifact-author ≠ COI'd reviewer (me) — matching the structural recusal pattern from the SaaS-cells and arch-split panels. Without the Fresh pass, Deep seat was on track to recommend "give Daniel a quarter to simplify in place," converting K1/K3/K4 operational pathologies into "tradeoffs we accept." Session-evidence value: stable replication of the deprecate-skill outcome on the same artifact 6 days apart from the same COI seat.
