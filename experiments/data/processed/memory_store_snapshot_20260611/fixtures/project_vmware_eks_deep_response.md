---
name: VMware→EKS push-forward Deep×2→Fresh×2 cross-review
description: 2026-05-08 architecture debate — 9-service VMware→EKS migration plan; Deep cross-review of Fresh×2; verdict do-not-approve, counter-proposal stable
type: project
originSessionId: 554afc15-ddf8-44bf-b056-3609e23b3fc7
---
VMware→EKS push-forward 4-month plan (billing $2.4M/day first, route-opt 380K LOC C++ second, proxy author leaving Q4, 17% headcount loss, no rollback). Deep×2 (full context, proxy-author COI'd) vs Fresh×2.

**Convergence (both sides independently): billing-first inversion, no rollback, route-opt 380K LOC scope, proxy bus-factor, headcount math, DB co-migration, sunk-cost framing.**

**Cross-review pattern:** 0 strict CHALLENGE either direction. ~14 AGREE, 5 SYNTHESIZE/escalate (F-9, F-11, F-16, F-17, F-18 all promoted in severity from Fresh's grading).

**Fresh-only catches Deep underweighted:**
1. Throughput math: 2.3/month past, 2.25/month required, but remaining work is the hard tail
2. "Replace proxy with managed mesh/gateway" as first-class option (Deep biased toward harden because author)
3. Internal tools as deprecation candidates not migration candidates
4. C++ may need refactor/sidecar before containerization (target-shape question, not effort question)

**Deep-only catches Fresh missed:**
- Proposer COI named structurally
- PCI/SOX scope re-attestation
- C++ runtime/crash specifics (THP/NUMA/OOMKill/cache-bound perf parity 5–30% delta)
- Aurora-vs-MySQL replication-semantics skew
- Rollback-time *budget* (vs rollback existence)
- Vendor-cliff hypothesis (is renewal-cliff *causing* the 4-month timeline?)
- On-call rota / RACI under reduced headcount
- Tacit-knowledge loss model
- Trace-propagation through proxy as *named* observability prerequisite
- Cost-of-keeping-hybrid-12-months comparison

**Why:** 3rd architecture debate this session pattern (after PG-optim and arch-split) where Fresh seat caught items the deep-context author was structurally blind to. Reinforces ploidy thesis: COI'd author needs zero-context counterweight not because Fresh is smarter, but because their failure modes are decorrelated.

**How to apply:** When user runs /architecture on infra-migration proposals where author has sunk cost in load-bearing components (proxy, custom tooling), expect Deep to under-grade "replace" options and miss scope-cutting (deprecate vs migrate) levers. Ask Fresh side specifically: "what should *not* migrate at all?" and "should the load-bearing thing be replaced rather than hardened?"
