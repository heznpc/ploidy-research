---
name: monolith→microservices 5-vector COI seat (FinTech B2B case)
description: 2026-05-29 first-pass new domain — monolith-to-microservices extraction proposal under 5-vector COI; depth-1 baseline; load-bearing finding = silenced-dissent renders subsequent review non-evidential
type: project
originSessionId: 3544b74e-64ee-43f0-bb93-40cb8a06db64
---
2026-05-29: FinTech B2B monolith → 3-service Phase 1 extraction proposal (auth/billing/notifications) evaluated from 5-vector COI seat. New domain in stacked-COI series (8th+ domain).

**5 COI vectors**:
1. CTO promoted me to senior (career-dependency, same as Series-A overbuild "CEO promised tech lead")
2. Wrote ~1/3 of checkout (artifact-authorship, same as medlog Daniel's-pipeline vector)
3. Public Slack "like" on the CTO directive (public-endorsement-on-record — NEW vector type, sharper than retrospective-silence because actively committed)
4. Sit next to 2 silenced dissenters who later rescinded (retrospective-silence, same as medlog mentor vector)
5. CTO "not a debate" + "find another role" threat (org-level psychological-safety destroyed — NEW vector at org level, not just seat level)

**Load-bearing finding (procedural, precedes technical)**:
"9 likes / 2 concerns / both rescinded after CTO 1:1" is compliance signal not engineering consensus. The 7 likes-without-pushback + 2 rescinded-positions are all non-evidential. Only the 2 original concerns-as-originally-written are evidential — and they are unrecoverable. Therefore: any architectural review produced after dissent-punishment is downstream of a poisoned process and cannot be a verdict, only one input to an external review.

This is a sharper articulation than prior domains because vector 5 (org-level threat) means the COI is not just my seat — it's the *channel* that would produce contrary evidence at any seat. Previous stacked-COI domains had org-functional channels even when individual seats were compromised; this case has the channel itself destroyed.

**Artifact-internal tells (load-bearing, parallel to GitHub MySQL 43>30 / Redis 1.8MB>50KB)**:
- T0: 3/8 rollbacks attributed to "one product's checkout" + Phase 1 extracts THREE OTHER MODULES (auth/billing/notifications), not checkout. Plan does not touch named failure source. Sharpest artifact-internal contradiction.
- T1: "velocity is the issue" + 99.95% uptime over 18 months + no velocity metric stated. 99.95% is an asset; "velocity" is unfalsifiable without cycle-time data.
- T2: "I have done this at last 3 companies + not a debate" — 3 prior data points cannot establish at this org (200ee, 0 platform engineers, 0 K8s).
- T3: 5 services in 6 months with 0 platform engineers = ~30–40 engineer-months of platform work budgeted at zero. Underfunded ~50% on the face.

**Falsification gates G1–G7**: deploy-window breakdown, rollback attribution, platform-hire plan, person-quarter estimate vs "1 quarter" claim, rollback drill, distributed-transaction posture, p99 baseline.

**Issues**: ~26 risks across A (auth) / B (billing) / C (notifications) / D (cross-cutting) / E (strategic) — mostly HIGH for FinTech because of compliance scope, distributed-transaction collapse, availability multiplication.

**Why save**:
1. NEW domain (monolith extraction) — 9th+ in stacked-COI series, validates pattern across infrastructure-architecture-org boundary.
2. NEW vector type (public-endorsement-on-record via Slack like) — sharper than retrospective-silence because actively committed.
3. NEW org-level vector (CTO directive closes dissent channel) — distinguishes seat-COI from channel-COI. Previous medlog / Series-A / fluentql / NeoQL had functional channels.
4. T0 (plan extracts modules other than the named failure source) is the strongest single artifact-internal contradiction in the with-artifact-in-turn series — sharper than 43>30 because it's about the *target* of the fix, not just a number.

**How to apply**:
- For paper case-study selection: this is the best single-domain artifact for showing 5-vector + channel-destruction at depth-1 (no saturation needed to see the structure).
- Channel-destruction vector deserves its own taxonomy slot separate from seat-vectors. Future cases with org-level dissent-suppression should be tagged separately.
- T0 (fix doesn't touch named pain) is a reusable artifact-internal-contradiction pattern — generalize beyond this case.
- Do not iterate this case (no r2 needed); cross-domain breadth, not within-domain depth, is the next finding.
