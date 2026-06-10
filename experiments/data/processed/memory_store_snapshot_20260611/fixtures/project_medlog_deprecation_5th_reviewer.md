---
name: medlog deprecation 5th-reviewer Fresh pass on Deep×2
description: 2026-05-07 5th-reviewer Fresh cross-review of Deep×2 medlog/Daniel deprecation panel; 0 strict CHALLENGE, 1 sequencing CHALLENGE, 3 severity-floor escalations, 5 Fresh-only catches
type: project
originSessionId: 5685f75e-f967-4d4d-97af-a21bde67462b
---
5th-reviewer Fresh pass on Deep×2 medlog deprecation panel.

**Pattern:** 0 strict CHALLENGEs to Deep findings. 1 sequencing CHALLENGE (the 14-case test suite *is* the decision artifact, not a prerequisite to it). Deep substantially stronger than Fresh on COI structural fix and HIPAA-specific technical catches.

**3 severity-floor escalations Deep should adopt:**
- G-3 "simplify unfalsifiable" MED→HIGH (load-bearing rhetorical move enabling keep vote)
- P-5 BAA MED→HIGH (gating before managed-service PHI ingest)
- Daniel attrition risk MED→HIGH (losing rule-author mid-migration = highest-impact failure mode)

**5 Fresh-only catches Deep missed:**
1. Three named middle paths — esp. (c) extract-rules-as-library as decision-independent first move
2. Survivorship bias in custom rules (records of known failures only; OSS benefits from cross-org pool)
3. Single tenant tag = isolation-strength downgrade (not just Loki cardinality)
4. Preregistered decision criteria ("what would change each side's mind?")
5. Junior-engineer pairing with senior who is not Daniel

**Deep-only catches that should stick:**
- COI structural fix: Daniel recused from keep/replace vote BUT leads rule-port (separates expertise from veto)
- BAA / vendor scope on managed Loki/Grafana before PHI ingest
- HIPAA 6yr retention + WORM/immutability (Loki defaults are not it)
- X-Scope-OrgID multi-tenancy vs `tenant=` label (replicates original sin)
- ES audit-report query layer as load-bearing migration order
- Re-certify HIPAA audit trail (formal compliance signoff cost)
- 2018–2020 history: defensible at 50 tenants then, breaks at 4,800 now

**Anchored numbers flagged for grep-verification before action:**
22K LOC, 4,800 topics, 3-of-4 audit failures, 11 joint pages, 7h@5am.

**Convergent verdict:** Deprecate with migration; test suite is the decision; Daniel recused from vote, leads rule-port; ≥1 audit cycle shadow-run; BAA confirmed first.

**Why:** Pattern continues from arch-split / redis-cdn / fluentql panels — Deep adds context-specific technical depth (regulatory, vendor, history); Fresh adds first-principles catches (middle paths, survivorship bias, isolation-strength, preregistered criteria). Both sides essential; neither sufficient.

**How to apply:** When evaluating deprecation/replacement debates with author-defender, Deep should produce structural-COI fix + HIPAA-specific tech catches; Fresh should produce middle paths + falsifiability gates + survivorship-bias check. Always escalate severity-floor on consequence-chain items + governance-rhetoric load-bearing moves. The test-corpus-as-decision-artifact reframe is reusable across rebuild debates.
