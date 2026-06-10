---
name: Redis-fronted image CDN — 4-lens debate verdict
description: 2026-05-14 — Deep×2 + SEC + SRE + FIN debate on replacing CloudFront with self-hosted Redis for 8M images / 60M MAU; defer + recuse-of-3 + R2/CF-commit/AVIF stable
type: project
originSessionId: b297e4ed-eeec-4b87-b7f3-53ba9afc3061
---
2026-05-14: Redis-fronted-image-delivery architecture debate.

**Setup**: Proposal to replace CloudFront with self-hosted Redis (256GB/cluster × 2 regions us-east + eu-west) to save $48K/yr. 8M images, 60M MAU, 35% in LATAM+APAC. Approved by EM without architecture review.

**Verdict (stable across Deep×2 + SEC + SRE + FIN, 0 bidirectional CHALLENGE)**: **DEFER. Diagnose first. Recuse lead + EM-who-approved + Deep reviewer. External CDN/edge review mandatory.**

**Foundational premise error (Deep-unique)**: workload misread — plan assumed "<50KB" images; actual P50=180KB, P90=1.8MB. Cache undersized ~5× vs 2.4TB working set.

**Counter-proposal**: Cloudflare R2 (zero egress) + CloudFront commit pricing + Origin Shield + AVIF/responsive images attack byte volume directly without rewriting tier-0 path.

**Issue count**: ~40 confirmed
- 7 CRITICAL (signed-URL authz loss, GDPR transfer, HOL blocking, thundering herd, no rollback, egress recost, implicit CDN build)
- 17 HIGH
- 12 MEDIUM
- 1 LOW

**11 falsification gates** (Deep F1–F6, SEC F-SEC-1/2, SRE F-SRE-1/2, FIN F-FIN-1).

**Load-bearing organisational fix**: three independent role lenses → three independent governance channels (CISO via SOC2 / SRE lead via ops-readiness / CFO via TCO) that bypass the conflicted EM without personalising dissent. This is the structural answer to the "how to surface objection around an approving EM" question Deep flagged as the remaining open problem.

**Why**: Pattern matches ~9 prior stacked-COI architecture-review domains (SaaS cells, PG-optim, auth-v1, medlog→OTel); when technical signal saturates across rounds the remaining unresolved question is always organisational channel design, not more technical analysis.

**How to apply**: For future architecture reviews of similar shape (approving-EM + recused-reviewer + plausible-but-untried-alternatives), default to 4-lens panel (Deep + SEC + SRE + FIN) rather than more Deep rounds — additional role lenses surface ~8 panel-unique findings that Deep-only iteration does not produce. Falsification gates should be committed up front per lens, not post-hoc.
