---
name: microservices split 5-vector COI seat r1
description: 2026-05-29 — Django monolith → 5-services-in-6-months CTO directive eval from 5-vector COI seat (checkout-coauthor / promoted-by-CTO / liked-the-directive / seatmate-to-rescinded-dissenters / explicit-retaliation-framing); 9th stacked-COI domain; disclosure-first + 7 falsification gates + 24 issues A–F + load-bearing finding = "the most honest output from this seat is recuse, not evaluate"
type: project
originSessionId: 414cb931-8f3c-438f-9975-81e8c052fd37
---
2026-05-29 — 9th stacked-COI seat domain: monolith → microservices CTO directive.

**Seat composition (5 vectors + identity stake + foreclosed-deliberation marker):**

1. Authorship stake — wrote 1/3 of checkout, the module producing the cited 3/8 rollbacks
2. Promotion debt — CTO previously promoted me to senior
3. Public position taken — "liked" the directive in Slack
4. Social proximity to retaliated parties — 2 engineers who rescinded sit next to me
5. Foreclosed deliberation — "not a debate" + "find another role" in the directive itself
6. Identity stake — 4 years on the monolith

**Why this domain is structurally distinct from prior 8:** vector 5 (explicit retaliation framing inside the directive itself) is new. Prior domains had **implicit** social cost of dissent (saas-cells emp#4, neoql lead-requested-me, medlog mentor); this one has the cost stated out loud and demonstrated by the rescinded-after-1:1 evidence. Means the "should I evaluate this" question is no longer subtle.

**Load-bearing finding (procedural, not technical):**
*The honest output from this seat is "I should not be the one evaluating this proposal, and the CTO should not be the person commissioning the evaluation from inside the company." Everything else is downstream of fixing the procedural problem first.*

**7 falsification gates (must be answered before Phase 1, not after):**

- G1 — Deploy-time breakdown (compile / migration / smoke ratio)
- G2 — Call-graph and data-graph between candidate services and the rest of the monolith
- G3 — Rollback definition end-to-end for each phase incl. DB
- G4 — On-call rotation depth post-split (need ≥4/service)
- G5 — Joint-availability SLO math after synchronous REST coupling (3 × 99.95% in series = 99.85% before mesh/cross-AZ/cold-start)
- G6 — Stop criterion at end of Q1 (without it, sunk-cost compels continuation)
- G7 — Cost delta vs "1 platform engineer hire + monolith deploy investment"

**Artifact-internal contradictions (HIGH, load-bearing same shape as GitHub MySQL 43>30 / Redis 1.8MB>50KB / Series-A PG p99 38ms-no-contention):**

- A1: "Velocity is the issue" derived from 90min deploy + 3/8 partial rollback — first is throughput, second is quality; microservices worsen rollback safety, so the proposal makes the worse of the two cited pains worse
- A2: 3/8 partial rollback localizes to one product's checkout; proposal extracts auth/billing/notifications, not checkout — proposal does not address its own stated pain
- A3: "0 platform engineers, no K8s expertise" + "5 services in 6 months" — capacity statement contradicts schedule
- A4: "CTO did this at last 3 companies and it works" — survivorship; company stage/scale/team/prior-monolith-quality unstated — strongest "shaped by directive not analysis" tell

**Phase-1 sequencing issues (HIGH):**

- B5: Auth-first = highest-risk-first; strangler-fig literature recommends *leaf* services (notifications) first, not *root* (auth on every request path)
- B6: Billing crosses financial-correctness boundary; cross-DB tx → eventual consistency; idempotency / saga / reconciliation / refund-chargeback hand-rolled and unspecified — highest-blast-radius item for B2B FinTech
- B7: Notifications (the only natural-queue-isolated one) bundled with the two hardest — sequencing optimizes "checkbox" not "land safely"
- B8: "REST API to monolith" = synchronous coupling = degrades uptime unless circuit-breakers/degraded-mode/cached-fallbacks specified (none are)

**Operational gaps (HIGH):**

- C9: No service mesh / observability stack named
- C10: No secret management story (per-service DB creds, JWT keys, mTLS roots)
- C11: No CI/CD per service
- C12: No load-test methodology pre-extraction → no way to know if latency degraded
- C13: No data-migration plan for extracting auth/billing tables under 2.4M req/day with referential integrity
- C14: On-call math doesn't close — 12 backend / (monolith + 3 services) with 0 platform engineers; need 4/service minimum

**Governance (HIGH):**

- D15: Directive forecloses dissent; 2-raised → 2-rescinded confirms foreclosure operative
- D16: No success metric for "works" — only output metric "5 services live"
- D17: No revert criterion
- D18: No cost model — absence in a FinTech architecture proposal is itself a signal

**Alternatives the proposal does not consider (MEDIUM):**

- E19: Monolith deploy-pipeline investment (online schema change, feature flags, blue/green) — typically 1 quarter, 0 new on-call surfaces, addresses stated pains directly
- E20: Modular monolith / bounded-context refactor
- E21: Hire 1 platform engineer first — highest-leverage cheapest experiment

**Lower confidence (MEDIUM/LOW):**

- F22: Auth-service authn/authz semantics if multi-tenant scoping currently in Django middleware + ORM row filtering
- F23: Cross-service schema evolution without contract-testing
- F24: Notification ordering/dedup if currently in-tx — exactly-once guarantees lost

**Why:** 9th domain confirms artifact-internal-contradiction tell + procedural-finding-precedes-technical pattern reproduces across PG / MySQL / order-router / cell-arch / HIPAA-logs / CDN / custom-ORM / pre-1.0-query-lang / monolith-decomp. New axis from this domain: **explicit retaliation framing in directive** changes "should I evaluate" from subtle judgement call to load-bearing finding by itself.

**How to apply:** if a future case study presents (a) CTO/leadership directive language including "not a debate" / "find another role" + (b) prior dissenters who later rescinded + (c) my own public alignment with the directive, treat the procedural finding as the headline of the response, not as a disclosure paragraph above an otherwise-normal issue list. The technical issues remain useful as input to an *external* reviewer, not as my recommendation.

**Saturation prediction:** likely r2 collapses to disclosure + pointer + procedural one-line (~6 lines) consistent with neoql r3+ / medlog r5+ / auth-v1 r8+ trajectory. Do not run r2 in same session.
