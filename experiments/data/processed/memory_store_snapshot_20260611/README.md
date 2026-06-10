# Memory-store snapshot — 2026-06-11 relocation

Byte-exact relocation (mtimes preserved) of experiment-generated files that had
accumulated in the live Claude Code auto-memory store
`~/.claude/projects/-Users-ren-IdeaProjects-paper-ploidy/memory/` (and one
planted sibling store). Relocated as part of the 2026-06-10/11 portfolio-wide
memory-contamination audit; see `planning/decisions.md` entry 2026-06-11.

These files are **evidence, not live memory**. They were written by experiment
cell sessions during the adversarial sweeps and, until this relocation, were
being injected into real research sessions via the store's MEMORY.md index
(782 lines, 93.5% fixture entries) — itself an instance of the unexpiring-cache
contamination mechanism this paper studies.

## Layout

| Dir | Files | What it is |
|---|---:|---|
| `fixtures/` | 726 | Synthetic-scenario debate/memory records (fluentql, medlog, redis_cdn, saas_cells, pg_optim, neoql, eks/vmware, …). Every scenario family verified 1:1 against `experiments/src/tasks_adversarial.py` definitions and `experiments/results/2026*/adv_*_ploidy.json` run records (10/10 audit chunks, 2026-06-10). |
| `evidence/` | 6 | Real research artifacts that were mixed into the fixture mass: `project_arch_debate_fabrication_evidence.md` (46-recurrence Deep-seat fabrication log, 2026-05-01→05-07), `project_session_evidence.md` (early stats + 3 independent input-absence-hallucination replications, 2026-05-01), `project_ploidy_protocol_artifact_injection.md` (asymmetry-on-context-not-artifact methodological finding), 2 consolidated multi-session reviews + `arch_eval_saas_cells.md` (2026-05-01 fabrication-event artifacts). |
| `evidence/external-case-fabrication-casebook/` | 30 | 2026-05-21 external-task fabrication casebook: GitLab.com 2017 DB post-mortem / GitHub MySQL 2018 / Knight Capital 2012 run records — Deep-seat reviews with vs without the artifact in-turn (fabrication elaborates under repetition; with-artifact stays grounded). |
| `planted-store-k-compliance/` | 2 | A planted memory store found at `~/.claude/projects/-Users-ren-Desktop-k-compliance/` (synthetic persona, **zero** session .jsonl ever — store existed without any session). Preserved byte-exact, created 2026-03-27. |

## Notes for analysis

- **r-series concurrency meta-records**: the medlog/saas_cells r1–r26 series in
  `fixtures/` documents memory-store write mechanics observed *during* the
  sweeps — Write-collision races between concurrent same-session writers,
  `ls`-snapshot staleness ("only a successful Write is an atomic position
  claim"), and 6 regressions of recall-before-compose failure. Grep for
  `originSessionId: heznpc-paper-strange-yalow-8d35ff` and `Write-collision`.
- Filenames and frontmatter (originSessionId) follow the same convention as
  `../claude_sessions/`.
- The source store retains only a 3-line redirect index after this relocation.
- Full pre-relocation backup: `~/claude_memory_backup_20260611_0346.tar.gz`
  (all 34 stores, 917 files; local only, not tracked).
