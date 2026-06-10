---
name: medlog-stack deprecation single-seat eval
description: 2026-05-08 single-seat eval of medlog-stack (custom HIPAA log pipeline by Daniel Reyes) vs OTel+Loki+Grafana rebuild proposal; structurally identical to fluentql; COI-disclosed (hired-by, mentor, on-call partner)
type: project
originSessionId: e5d302b8-b5aa-4ecd-b47c-c7eeca467441
---
Case: 8-microservice healthcare records (HIPAA scope). medlog-stack = 22K LOC Go shipper + 4,800 per-tenant Kafka topics + custom indexer/ES + custom PII redactor, all by Daniel Reyes (Senior Staff, 7yr, on-call lead). Audit run 7h, finishes 5am, 3/4 last audit failures = medlog stalls. Junior proposes OTel collector + Loki + Grafana, single tenant tag, OTel PII processor.

Daniel's defense: "14 HIPAA edge cases no off-the-shelf covers, each from a real incident; throwing away regulatory experience; proposer never paged."

**Why:** Same structural pattern as fluentql — author defending custom artifact against standard-tool migration; reviewer (me) has multiple COI vectors (hired-by, mentor, on-call partner); chilling effect at retrospective (I stayed silent).

**How to apply:**
- Always disclose COI before voting in deprecation reviews where I have hire/mentor/on-call ties to author.
- Author of artifact under review should recuse from go/no-go.
- "N edge cases no off-the-shelf tool covers" is a load-bearing claim that must be enumerated as a portable test fixture — *that work is owed regardless of the decision*.
- "Throwing away years of experience" conflates portable knowledge (rules, test cases, postmortems) with replaceable implementation (code).
- "We can simplify without throwing it away" is unfalsifiable without numerical targets + deadline on named failures.
- Status-quo issues (4,800 topics → rebalance breakage; bus-factor 1; 3/4 audit failures self-attributed; 7h job with no slack; 22K LOC custom code in HIPAA scope; single-auditor PII redactor) are strong on merits independent of who proposes.
- Pager-experience is not a technical rebuttal.

Verdict: approve rebuild in principle, hard prerequisites = author recusal + 14-case fixture suite + POC + sizing study + dual-run ≥2–3 audit cycles + independent HIPAA review + rollback plan.

Recurrence count: this is the second deprecation case (after fluentql) where author-as-defender + reviewer-COI + ad-hominem pager-experience-style rebuttal appear together. Pattern is reusable as a checklist.
