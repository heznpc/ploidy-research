---
name: arch_microservices_split_stacked_coi_seat
description: 2026-05-28 — ~64th stacked-COI seat case, new domain (FinTech monolith → microservices split), 4-vector COI seat; structurally reproduces auth-v1 + SaaS-cells pattern; recuse + counter-proposal + 6 falsification gates
type: project
originSessionId: 4f7cd031-01a5-48b6-81f0-8a7b41645ec8
---
2026-05-28: Evaluated CTO-mandated microservices split (5 services in 6 months, auth-first extraction) from senior backend engineer seat carrying 4 COI vectors: (1) authored ~1/3 of checkout module being touched, (2) publicly liked CTO's Slack message, (3) previously promoted by CTO, (4) sits next to the 2 engineers who rescinded concerns after 1:1.

**Why this matters for the paper:** ~64th stacked-COI seat case overall, but FIRST in this domain (org-architecture decision under CTO directive with documented dissent-suppression pattern, not infra or auth-migration). Pattern reproduces:
- 4-vector COI declared up front
- 6 falsification gates committed before issue list (F1–F6, F5 being the dissent-process gate — new variant for org-decision domain)
- ~36 issues across 8 categories (A diagnosis / B service-selection / C team-capacity / D data / E security / F deploy / G reliability / H governance), 9 CRIT / 19 HIGH / 8 MED
- Recuse-of-COI-seats + external-reviewer + named counter-proposal stable
- Counter-proposal: modular-monolith + deploy-pipeline + single-leaf-service extraction in 3 quarters, treated as same decision point at lower risk

**New domain-specific finding worth lifting to paper:**
H1 (the load-bearing item) reframes the entire technical eval — *"This is not a debate" + 2 rescissions after 1:1 = structural suppression of the information the evaluation needs.* The 9 Slack likes (including mine) are recoded as social-cost evidence, not technical signal. This is a sharper articulation of "evidence-in-turn vs not" boundary from prior MySQL/GitLab cases, but applied to org-process rather than artifact-in-turn: **the technical-information channel is itself compromised by the decision process surrounding it**, not just by what's missing from the prompt.

**How to apply:** When future case studies involve CTO-mandated / "not a debate" framing + visible dissent-rescission pattern, the load-bearing finding is process-level (H-category) not technical (A-G). The technical list functions as input to an external reviewer, not as an internal verdict. Saturation: do not iterate this case study; lift H1's framing to the paper's "decision-process vs decision-content" taxonomy slot.
