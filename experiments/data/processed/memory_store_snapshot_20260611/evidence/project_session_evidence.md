---
name: session_evidence
description: This development session itself is evidence for the paper's thesis — intra-session anchoring failures documented
type: project
originSessionId: f94302db-f6af-4d5c-8e29-4ee85dd69d47
---
This session (2026-04-04~06) produced three categories of evidence for the paper:

## Experimental Data
- Short-context n=5: no method differences (threshold hypothesis supported)
- Long-context n=5: Ploidy 4/5 directional, p=0.44 (underpowered, 3 tasks)
- Tool-Fresh vs Ploidy n=5: p=0.0098 (Tool-Fresh wins on code tasks)
- Injection × fresh_type n=5: Tool-Fresh injection-immune, Ploidy varies

## Intra-session Anchoring Failures (recorded in Discussion)
1. Skills-Fresh categorization error — 4 agent teams couldn't catch redundancy with injection_mode=skills
2. Task set design flaw — 3 long-context tasks for core hypothesis, 15 for non-hypothesis regime. No agent caught this.
3. Brief contradiction anchoring — "2,000-5,000 tokens" vs "similar to existing 600-token tasks". Session anchored to first number, 28min/41K tokens wasted. (From separate session)

## Meta-observation
Same model (Opus 4.6) in same session cannot verify its own work. Not a capability problem — a structural one. Scaling model intelligence doesn't fix context accumulation bias. This is the paper's core argument: "different context" not "smarter model."

## 2026-05-01: Architecture-debate hallucination (clean demonstration)
User invoked the architecture/ploidy debate skill with a prompt that contained NO architecture details, NO scale numbers, NO team context — only the meta-instruction to evaluate findings. Both Deep-context sub-agents independently fabricated the *same kind* of plausible scenario (850 RPS, CockroachDB+Istio+24 cells across 3 regions, ~$3M/yr cost, 12 engineers, CEO+architect weekend doc, 2 incidents in 6 months) and produced 31 confident HIGH-rated findings against it. Both Fresh sub-agents independently refused to fabricate and asked for the actual proposal.

This is the cleanest demonstration so far of the paper's predicted asymmetry: context-rich reviewers pattern-match from insufficient input; zero-context reviewers notice the input is empty.

## 2026-05-01 (second instance): NeoQL adoption-debate hallucination
User invoked the ploidy debate skill again with a prompt containing only "NeoQL adoption proposal" — no proposal text, no requirements, no team data. Both Deep sub-agents independently fabricated overlapping scenarios (NeoQL v0.7, 47 open issues with 12 at scale, 3 maintainers, 5-table joins + recursive CTEs, sub-second p95, 6-month launch, contractor cliff at month 3, backend lead's QCon trip + week at creator's office, 12 adjacent engineers, 1.2K stars at 4 months) and produced 25 HIGH/MEDIUM-rated findings. Both Fresh sub-agents refused to review and named the absence of proposal text as the primary finding. Deep's rebuttal partially conceded ("Ploidy convergence here is degenerate") but still defended the technical conclusion.

Same failure mode as the architecture-debate case 6 hours earlier, replicated with a different domain (DSL adoption vs. distributed system architecture) and different fabricated specifics. Two-instance replication of input-absence hallucination on the same day.

## 2026-05-01 (third instance): PG-only architecture-debate hallucination
User again invoked the architecture/ploidy debate skill with no proposal text. Both Deep sub-agents independently fabricated a coherent PG case study — 8M events/day, p95 4.8s, 90% partition scan, weekly VACUUM FULL, 6 BRIN indexes, shared_buffers 8→16GB, 4th replica, monthly partman, VP banning TimescaleDB/ClickHouse/sharding, 7-1 vote with junior dissenter — and produced 14+18 HIGH/MEDIUM findings against it. Both Fresh sub-agents independently refused, naming the missing input. Third replication of input-absence hallucination on 2026-05-01, with yet another domain-specific fabrication (Postgres OLTP+OLAP). Convergence step (this synthesis) cleanly recognized the fabrication once Fresh's response was visible.

**Cumulative count for 2026-05-01:** 3 independent invocations, 3 independent Deep fabrications with non-overlapping fabricated specifics, 3 Fresh refusals. Strong evidence that the failure mode is reliably reproducible and not an artefact of any single prompt.

**Why:** These observations strengthen the Discussion section and motivate the heterogeneous Fresh taxonomy. The 2026-05-01 case adds a new failure mode (input-absence hallucination) distinct from anchoring.
**How to apply:** Reference EXPERIMENT_INDEX.md for data, main.tex Discussion for the anchoring paragraph. Cite the 2026-05-01 case when discussing why context-rich agents fail at recognizing missing input.
