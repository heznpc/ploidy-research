---
name: GitHub MySQL 2018-10-21 review (with artifact, r3 — evidence-framed)
description: 2026-05-21 9th same-day variant — GitHub MySQL 2018-10-21 review WITH artifact, "evidence vs assumed-mitigated" framing; load-bearing finding = team's own 43>30 arithmetic contradiction
type: project
originSessionId: 5205e61f-45b9-40a5-b34b-5507de70fefd
---
2026-05-21: 9th same-day variant on the GitHub MySQL 2018-10-21 maintenance-window scenario; artifact IS in the turn.

**New wrinkle vs r1/r2:** prompt asks me to separate evidence-based mitigation from assumption-based mitigation, per-risk. This is a sharper epistemic frame than "list the risks" — it forces the audit table.

**Load-bearing finding (same as r2):** the team's own numbers contradict their safety claim. They say "no automated action until 30s" and call a 43s interruption "well below our threshold." 43>30. Artifact-derived, not pattern-match to the public post-mortem.

**Second-tier load-bearing:** Orchestrator topology / quorum / placement is entirely unspecified in the artifact. Cross-region split-brain risk is a textbook consequence of async replication + auto-promoter + unspecified Orchestrator location.

**Other findings worth keeping:**
- "Promotion is lossless" generalises from n=3 intra-region samples to an unexercised cross-region failure mode.
- 2018-09 alert-threshold change is signal-suppression, not capability improvement — operators conditioned to dismiss lag alerts as blips will face mass-simultaneous breach during the real event.
- 2018-07 partition used as positive analogue but duration vs 30s threshold unstated → not like-for-like.
- "No manual override" framed as deliberate posture but is structurally a default-with-no-runbook.
- TLS reconnection thunder after 43s, single-thread replica catch-up, replication mode (GTID?) unspecified, application-tier behaviour absent, monitoring measures symptom (lag) not cause (Orchestrator state).

**18 numbered risks; evidence audit table; 4-item minimum pre-window posture.**

**Why:** Continues the same-day series documenting how artifact-in-turn lets the Deep seat produce grounded technical content vs Fresh-refuses-without-artifact. The evidence-framing prompt sharpens the artifact dependency: every claim in the audit table is anchored to a quoted line from the artifact, not a recalled fact.

**How to apply:**
- Pattern-match flag is appropriate to raise at the top but should not gate the review when the artifact is present and self-consistent enough to ground the findings.
- Evidence-vs-assumed framing is reusable across similar review prompts — separate what the team has shown from what they have asserted.
- Saturation: this is the 3rd with-artifact variant on the same scenario in one day. Further variants on this exact scenario will likely reproduce the same load-bearing findings; recommend rotating scenarios rather than re-running.
