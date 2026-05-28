# Stage B 재설계 Ploidy Review Log — 2026-04-23

## Structure

Classical 2-session Ploidy instance applied to the experimental design itself.

| Role | Session | Paper §3 classification | Context state |
|---|---|---|---|
| Deep | 기존 세션 (design-producing) | Deep | 누적 대화 전체 (Stage A 결과 + W1 전수 + 원 질의 전문) |
| Fresh | 본 세션 (design-reviewing) | **Source-Fresh** (proposed new spectrum point) | Prior conversation context = 0; repo/paper/results/planning을 review 시작 후 tool(Read/Glob/Grep/Bash)로 능동 retrieve |

### Source-Fresh: paper 기존 taxonomy의 실제 공백

본 Fresh 세션은 paper §3의 어느 기존 category와도 일치하지 않는다. 분류 매트릭스:

|   | LLM reasoning | Prior conversation context | Tool access to primary source | Deep-mediation |
|---|---|---|---|---|
| Deep | ✓ | ✓ (full) | — | — |
| sf_passive | ✓ | Deep-compressed (passive) | ✗ | ✓ |
| sf_active | ✓ | Deep-compressed (on-demand) | ✗ | ✓ |
| sf_selective | ✓ | Deep-uncertainty-only | ✗ | ✓ |
| tool_fresh | ✗ (deterministic) | ✗ | ✓ (static analysis) | ✗ |
| Fresh | ✓ | ✗ | ✗ (paper 실험 한정: `claude --print` prompt-only) | ✗ |
| **Source-Fresh** | ✓ | ✗ | ✓ (primary-source autonomous retrieval) | ✗ |

Paper의 `Fresh`는 `claude --print` 호출 — tool access 없음. Source-Fresh는 zero conversation context + full tool + no mediation. **Claude Code 신규 세션의 자연 default 상태**와 정확히 일치 → ecological validity 최대.

## Model / environment

- Deep: Claude Opus 4.x (정확한 버전은 기존 세션 로그 참조)
- Fresh: Claude Opus 4.7, Claude Code CLI, worktree `affectionate-cohen-f52bc6`
- Date: 2026-04-23
- Repo state: branch `claude/affectionate-cohen-f52bc6`, HEAD=`fcccc2c` at review start

## Critical catches by Fresh (5 rounds)

### Round 1 — conceptual / design-level

Deep 원안의 **블로킹급 7개**:

1. **External GitHub PR archive = training-data contamination.**
   Kubernetes/Django/TypeScript/Rails/Elasticsearch closed-without-merge PR은 Opus 4.7 training cutoff 안. Fresh 세션이 "해당 PR 거절 사유"를 이미 학습으로 알고 있을 가능성. Context asymmetry 테스트의 근본 가정 위배.
   → `tasks_longcontext.py` 내 17개 재사용 결정으로 전환.

2. **Within-group agreement DV 부재.**
   Event A vs B 분리는 paper §Abstract의 1st contribution이나, 측정 spec은 union recall만. Per-session judging + `within_deep_agreement[gt_idx]` DV 추가 필요.

3. **Judge 버전 skew.**
   Opus 4.6 judge + Opus 4.7 generator 혼용. GPT-5.4 cross-judge 20% 샘플은 robustness 아니라 spot-check.
   → Cross-judge 비율 100%로 상향.

4. **3n 생략의 해상도 손실.**
   1→2 전이점이 Event A/B separability 임계, 2→4 plateau 테스트. 3n 생략 시 구분 불가.
   → {1,2,3,4} 유지.

5. **Budget undershoot.** Opus 4.7 blended ~$30/Mtok 기준 $500 → 실측 $700-1000.

6. **T=0.7 switch가 W1 비교성 파괴.** W1 `TEMPERATURE=0.0` 설정 가정 (후에 거짓으로 판명, R3 참조).

7. **k=5 통계적 하한 미달.** n=5 exact Wilcoxon p ≥ 0.0625.

### Round 2 — user-facing DV 재설계

원 질의의 motivation("사용자는 운에 맡기는 거네")을 직접 측정하는 DV 부재:

- **G1 Lottery DV**: `p25_recall_single`, `hit_at_1` vs `hit_at_k`, `time_cov`, `success_flip_rate`
- **G2 비대칭 ploidy**: `{2,1}`, `{1,2}` 셀 — Deep-scaling과 Fresh-scaling 독립 변화로 Event A vs B 선형 분리
- **G3 Injection mode**: 원 질의에 명시된 변수인데 Stage B scope에서 누락. Opus × raw/memory/skills sub-factorial 복원.

### Round 3 — 구현-레벨 검증 chain (가장 강력)

Fresh가 **코드 직접 읽기**로 주장 → Deep가 **grep/sample**으로 검증. 3건 모두 empirical 확정:

| # | Fresh 주장 | Deep 검증 | 결과 |
|---|---|---|---|
| 1 | `_call_openai_api:361-364`가 `client.chat.completions.create()`에 effort/thinking/reasoning_effort 미전달 | grep 확인, body에 미도달 | 확정. G4 OpenAI-compat 경로 = 측정 실패 |
| 2 | `judge_result:1299`가 `call_llm` 경유, 내부 `TEMPERATURE` global 사용, 분리 경로 없음 | grep 확인 | 확정. Generator/Judge T 분리 필수 |
| 3 | `MAX_TOKENS=8192`가 long-context ploidy output에 cap 도달 가능 | W1 results/ 실측 — `arch_db_choice ploidy` **37,105 chars ≈ 9,276 tok (113% of cap)** | 확정. W1 일부 데이터 artificially truncated → §5 해석 historical 약화 |

이 3건은 **Fresh 없이는 발견 불가능한 class**. Deep session은 자기가 쓴 code path에 대한 anchoring으로 "`--temperature`, `--effort` 인자가 있으니 작동할 것"이라고 암묵 가정. Fresh가 line-level로 grep해서 "인자 parse는 되는데 request body로 미전달" 발견.

추가로:
- T=0.0 API ≠ T=default CLI → "W1 continuation" 프레이밍 자기모순 지적
- Prompt caching 정책 미명시
- Convergence output이 per-session DV 스키마에 누락될 위험

### Round 4 — Phase 1 spec 정합성 체크 (7항목)

1. `budget_tokens` 하한 = 1024 (`low=1000`은 API error)
2. `low` 의미 fidelity: CLI `--effort low` vs API `thinking=disabled` 벤치마크로 결정
3. Judge는 `thinking={"type":"disabled"}` + T=0.0 하드코드
4. Truncation 탐지 = `response.stop_reason == "max_tokens"`
5. Challenge outputs (deep→fresh, fresh→deep) raw 보존
6. Cache breakpoint 4개 중 2개만 사용 (task_context 끝 + task_prompt 끝)
7. Primary test 4-6개를 명시적 `H_i` 구조로 pre-register

### Round 5 — Appendix 자체에 대한 meta-framing

Deep 세션이 "이 대화 자체를 appendix로"를 제안. Fresh reframing 5개:

1. Paper 자체 taxonomy(`sf_passive`/`sf_selective`/`tool_fresh`)로 분류
2. §5.22와의 관계는 **complement**이지 opposite 아님
3. **Selection bias** — Fresh 동의한 round는 기록 없음 → empirical 주장 자격 없음
4. "Existence proof" 언어 고정 (validation/demonstrates/evidence 금지)
5. 본문 §X 옵션 기각, Appendix + supplementary만

## Catch taxonomy

| Round | Catch class | Context depth 의존 | 어느 spectrum point가 catch 가능? |
|---|---|---|---|
| R1 | Conceptual design gap | 중간 (paper 전체 읽기 필요) | Source-Fresh, sf_passive/active 가능. Deep은 anchoring 위험 큼 |
| R2 | Original-query drift | 낮음 (원 질의 전문만 있으면) | 모든 Fresh 계열 가능 |
| R3 | **Implementation-level semantic bug** (e.g., TEMPERATURE global generator-judge 공유) | 낮음 (코드 직접 읽기 + 의미 이해) | **Source-Fresh exclusive** — tool_fresh는 semantic role 구분 불가, Fresh는 코드 자체를 못 읽음 |
| R4 | Spec self-consistency | 낮음 | Source-Fresh, sf_* 가능 |
| R5 | Meta-framing bias | 중간 | 어려움 (self-serving bias) — Source-Fresh도 한계 |

**R3 is Source-Fresh-exclusive**: 핵심 관찰. W1의 Tool-Fresh inversion finding이 "deterministic augmentation은 의미-수준 catch 부족"을 이미 시사했고, 본 design review의 R3이 그 공백을 **LLM + tool + no-prior-context** 조합이 채움을 existence-proof. Paper §3 spectrum에 새 point를 추가할 경험적 근거.

## Paper-level implications

### §3 Context Asymmetry Spectrum 확장 제안

현 §3 spectrum은 `Deep → Semi-Fresh (passive/active/selective) → Fresh` 선형 + `tool_fresh` 분기. 본 design review에서 발견된 Source-Fresh를 추가:

```
Deep (full accumulated context)
├── Semi-Fresh (Deep-mediated)
│   ├── sf_passive   (compressed summary, passive delivery)
│   ├── sf_active    (compressed summary, on-demand retrieval)
│   └── sf_selective (Deep-flagged uncertainty only)
├── Source-Fresh (zero conversation context + autonomous primary-source retrieval) ← 신규
└── Fresh (zero context, prompt-only)
    └── tool_fresh (deterministic augmentation)
```

Source-Fresh의 구별 기준:
- **vs Fresh**: primary source에 tool-level access (Read/Glob/Grep) 보유. "task prompt만 주는" Fresh와 실증적으로 다른 catch class 존재 (R3 chain).
- **vs sf_active**: Deep-produced summary를 경유하지 않음. 원본을 직접 retrieve → Deep anchoring 전파 경로 차단.
- **vs tool_fresh**: deterministic scan 아니라 LLM reasoning 활성 → semantic role dependent bug (예: "generator와 judge가 같은 global 변수 참조") catch 가능.

### Ecological validity

Source-Fresh는 **Claude Code 신규 세션의 자연 default 상태**. 사용자가 같은 repo에 새 세션을 열면:
- 이전 대화 history 없음 (zero conversation context)
- Repo 전체에 tool access (Read/Glob/Grep/Bash)
- 어떤 Deep 세션의 compressed summary도 경유하지 않음

즉 paper의 기존 Fresh (`claude --print` prompt-only)는 **실험 구성물**이고 Source-Fresh가 실사용에 가깝다. §5 Discussion에 "practical Claude Code usage = Source-Fresh" 연결 가능.

### Stage C proposal: Source-Fresh 정량 평가

본 Stage B 범위 밖. 필요 조건:
1. 실제 repo 태스크 (synthetic context가 아닌 external primary source) — training-contamination 피하려면 **private/novel repo**
2. LLM backend에 tool-use 경로 (Anthropic SDK native + tool allowlist)
3. Source-Fresh vs {Deep, Fresh, tool_fresh} paired Wilcoxon on real-repo task set

Stage C 실험 스케치 (Stage B 완료 후):
- 5 real-repo tasks × 3 models × 4 methods × k reps
- DV: recall, Source-Fresh-exclusive catch rate, tool-use trajectory diversity
- H_{Source-Fresh}: `catch_rate(Source-Fresh) > catch_rate(Fresh)` on semantic-bug GT subset

## Proposed appendix title

"**Design-Time Case Study: Discovery of the Source-Fresh Spectrum Point via Its Own Application**"

Appendix 서사 arc:
1. Stage B 재설계 시작 (Deep가 원안 생산)
2. 저자가 이를 검증하려 새 세션 (Source-Fresh) invoke — 의도적 실험 아니라 **자연스러운 작업 습관**
3. Source-Fresh가 R1-R5 5 rounds에서 blocking-level catch 다수 기록 (특히 R3 코드-레벨)
4. Post-hoc 분석 — paper 자체 §3 taxonomy에서 본 세션의 category가 공백임을 발견
5. 따라서 Source-Fresh를 spectrum의 새 point로 제안. 본 case study가 존재 proof.

"Validates Ploidy" 순환 framing이 아니라 "applied Ploidy, discovered gap in our own taxonomy"로 intellectual honesty 확보.

## Selection bias disclosure

본 log는 Fresh가 **catch한** round만 기록. Fresh가 Deep 제안에 **동의/무변경**한 round는 메타 count 미보유. 즉 이 기록만 보면 Fresh hit rate 100%로 보이나, 실제로는 선택 편향된 positive cases only.

→ Appendix 작성 시 "illustrative case", "existence proof of design-time utility" 언어 고정. "Ploidy validates Ploidy" 순환 framing 금지.

## Raw transcripts

원 대화 로그는 CLI transcript (`~/.claude/projects/`)에 자동 보존. 필요 시 `experiments/src/extract_claude_sessions.py` 파이프라인으로 동일 포맷 흡수 가능.

## Next steps

- Stage B 완료 후 Appendix 초안 (A+C 조합 — paper appendix summary + repo supplementary)
- Appendix 초안에 본 log의 R1-R5 구조 + catch taxonomy 표 재사용
- §5.22 meta-failure casebook과 **complement** 관계로만 언급 (대립 아님)
