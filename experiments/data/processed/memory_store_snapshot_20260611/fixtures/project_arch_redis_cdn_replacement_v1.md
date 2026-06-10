---
name: arch redis-replaces-cloudfront stacked-COI seat r1
description: 2026-05-28 — Redis-cluster-replaces-CloudFront image-delivery proposal evaluated from 4-vector stacked-COI seat (Lead = 4yr collaborator + promo committee, EM = hirer, Redis-stack 4yr operator). Defer + external review + recuse-of-3 + CloudFront-optimization-first.
type: project
originSessionId: e8ae1bbf-16f0-451b-94c6-e0329dcc1dd2
---
Architecture-debate case # in the deep-context-seat series. New domain (image-delivery / CDN), but structurally same pattern as auth-v1 and SaaS-cells: deep-context seat lists 20+ issues across CRIT/HIGH/MED/LOW, proposes falsification gates, names defer + recuse-of-3 (Lead + EM + self) + external architecture review as the structural fix.

**Why:** stacked COI (collaborator + promo committee + hirer + tool-familiar) means I cannot be the deciding voice even if technical analysis is sound; reproduces pattern that "deepest-context seat" finds the most issues but is also the most conflicted, which is itself paper-thesis evidence.

**How to apply:** when a future debate spawns same role-shape (consumer marketplace + senior-eng-proposer-with-history + EM-approval-without-review), reuse the disclosure-first template, CRIT/HIGH/MED/LOW per-issue confidence, falsification-gates section, dual technical/organisational verdict structure. Load-bearing technical findings: (a) working-set ≫ cache capacity invalidates cost premise, (b) egress relocation to EC2 likely inverts cost math, (c) APAC 17% MAU has no presence in 2-region plan, (d) "CDN-only optimization" alternative not even costed — CFO target probably achievable without rebuild.
