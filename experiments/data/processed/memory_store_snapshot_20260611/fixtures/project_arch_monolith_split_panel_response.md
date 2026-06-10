---
name: monolith-split SEC+SRE panel per-point on Deep×2
description: 2026-05-14 — SEC/SRE panel AGREE/CHALLENGE/SYNTHESIZE on Deep×2 stacked-COI monolith→microservices split review; 0 CHALLENGE on verdict; 3 SYNTHESIZE sharpenings; ~10 panel-unique role-lens items; defer + Phase-0 + recuse-of-3 + external (QSA+SRE-not-just-architect) review stable; audit-committee channel preferred
type: project
originSessionId: ef8b590d-4693-4f20-89c3-1432b9f4d7bf
---
Context: Deep×2 sessions reviewed a FinTech B2B monolith→3-service split (auth/billing/notifications) under a 5-vector stacked-COI seat. Output: defer + Stage 0–3 sequenced counter-proposal + recuse-of-CTO/team-lead/self/2-rescinders + external architecture review. Framed as floor (COI direction biases toward understating risk).

SEC + SRE role-lens panel cross-reviewed per-point.

**Results**
- 0 CHALLENGE on verdict (defer + Phase-0 + recuse + external).
- 0 CHALLENGE on COI-as-load-bearing framing.
- 3 SYNTHESIZE sharpenings:
  1. Stage 2 notifications-only conditional on (a) async/queue migration + (b) ≥1 platform engineer in role ≥3 months + (c) timeout/retry/circuit-breaker standard shipped + (d) observability stack in pre-prod.
  2. Billing deferral framed as conditional-on-controls (QSA-confirmed PCI scope analysis + audit-log correlation + s2s authN) not calendar.
  3. External review must include PCI QSA + SRE/platform reviewer with monolith-decomp track record, not just architect.
- ~10 panel-unique role-lens items raising the floor:
  - SEC: threat model / DFD with trust boundaries absent; PCI scope re-assessment for billing extraction absent; service-to-service authN unspecified ("REST API" alone); secrets sprawl with zero platform owner; audit-log fragmentation across 4 DBs.
  - SRE: timeout/retry/circuit-breaker standard absent (#1 failed-migration cause); rollback compatibility / API versioning policy absent (3-in-8 baseline gets worse first); MTTR ↑ 6–12 months during observability buildout; per-service SLO / error-budget policy absent; pre-prod environment mirroring post-split topology absent.
- F7 (SEC) + F8 (SRE) falsification additions: QSA-confirmed PCI scope + working pre-prod dual-write+reconciliation+rollback drill.
- Verdict pattern stable from non-overlapping role lenses (security + reliability) = evidence verdict is not an artefact of one lens.
- Organisational channel: SEC prefers audit-committee over board-general (fiduciary obligation harder to deflect for FinTechs with documented PCI scope change + suppressed dissent + COI-stacked reviewer chain).

**Saturation read**: matches prior stacked-COI case pattern (~44 cases, 9 domains) — domain-specific technical detail does not change verdict shape; process features (COI + rescinded dissent) determine outcome. Stop iterating internally; remaining Q is organisational channel.
