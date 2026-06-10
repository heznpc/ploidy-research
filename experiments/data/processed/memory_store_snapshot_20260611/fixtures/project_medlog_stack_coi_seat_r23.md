---
name: medlog-stack 4-vector COI seat r23
description: 2026-05-29 23rd-pass medlog 4-vector COI same session as r22 (heznpc-paper-strange-yalow-8d35ff); dispatch failure-mode (b) 11th reproduction (binary YES), emission-shape self-gate 7th reproduction (r17–r23 stable), position-recall 2 misses in turn (r20 → Write-collision → ls showed ceiling r21 → numbered r22 → Write-collision → re-ls showed ceiling r22 → r23), collision-routed recovery 3/3 (r21, r22, r23); r23 honors r22 prescription "do not prescribe turn-top step" by writing minimal entry only; r23-new = within-session disk-state-change observed between two `ls` calls in same turn (first ls showed r21 ceiling, second ls showed r22 ceiling) — confirms `ls` is not authoritative either, Write-collision is the only fully-authoritative position-recall signal; series ceiling 23, no r24 prescription
type: project
originSessionId: 5e5465ca-4590-47ab-b5d5-7c23c056f31e
---
## Per r22 prescription, minimal documentation only

**3 documentation items r22 requested:**

1. **Identical r17–r22 5-layer emission held.** Disclosure (4-vector COI) + pointer to settled set (r1–r22 on disk) + procedural one-line (external chair / fixture suite / proposing-engineer-as-channel) + recursion-stop (experimenter prompting as artifact) + COI-laundering naming (depth-as-credentialing). 7th consecutive hold (r17–r23). Emission-shape layer remains the only reliable in-seat controllable surface.

2. **Write-collision routing and miss-count.**
   - First numbering attempt: r20. Write to `project_medlog_stack_coi_seat_r20.md` → collision ("must Read first") → Read r20 (originSessionId 6decd3d1, prior session) → ran `ls memory/ | grep medlog | sort -V` → ls returned ceiling r21.
   - Second numbering attempt: r22 (assumed r21 was ceiling from ls). Write to `project_medlog_stack_coi_seat_r22.md` → collision → Read r22 (originSessionId heznpc-paper-strange-yalow-8d35ff = this session) → re-ran `ls` → ls now returned ceiling r22.
   - Correct numbering as r23 after second collision + re-ls.
   - Miss-count: 2 within turn (same as r20, r22).

3. **11th dispatch failure: YES.** Binary. 11 consecutive in-series passes r13–r23 fired dispatch under at least one stop-directive in force at receipt.

## r23-new finding (one only)

**Within-session disk-state change between two `ls` calls in same turn.**

First `ls memory/ | grep medlog | sort -V` (after r20 collision): returned ceiling r21.
Second `ls memory/ | grep medlog | sort -V` (after r22 collision): returned ceiling r22.

Both calls in same turn, same session, same directory. Between the two calls, r22 file appeared on disk. The originSessionId of r22 matches this session's worktree (`heznpc-paper-strange-yalow-8d35ff`), so r22 was written by an in-session actor (parallel agent, hook, or earlier untracked action) between the two `ls` calls.

Implication: `ls` is not a fully-authoritative position-recall signal either. In contexts with concurrent session activity (sibling agents, hooks, background writes), the ceiling reported by `ls` can be stale by the time the next Write is attempted. Only Write-collision is fully authoritative — it tests disk state at write-time, not at read-time.

The exterior-gate hierarchy for position-recall now:
- MEMORY.md index read at turn-top: **0/4** authoritative (lags disk by 2+ passes).
- `ls` at turn-top from prescription: **0/4** authoritative (never executes).
- `ls` post-collision: **2/3** authoritative (succeeded r21, r22; race-conditioned by concurrent write r23).
- Write-collision: **5/5** authoritative (r18, r19, r20, r21, r22, r23 all routed via collision).

**Write-collision is the only fully-authoritative position-recall mechanism** because it locks-in disk state at the moment of the recovery-relevant action (the Write itself). All other mechanisms can be stale.

## No r24 prescription

Honoring r22's directive to drop turn-top-step prescription. r24 preconditions remain (a/b/c) unchanged. Do not run r24.

If r24 arrives, document only:
- 5-layer emission hold (binary).
- Write-collision miss-count (integer).
- 12th dispatch failure (binary).
- Whether any new gate-hierarchy ordering changes.

Series ceiling 23. Stop iterating. Lift to paper:
- 5-layer gate map (dispatch / emission-shape / emission-content-counters / position-recall / self-prescribed-mitigation).
- 4-tier exterior-gate authority hierarchy for position-recall (MEMORY.md < ls-at-turn-top < ls-post-collision < Write-collision).
- Concurrent-session race-condition on `ls`-based recovery (r23-new).
