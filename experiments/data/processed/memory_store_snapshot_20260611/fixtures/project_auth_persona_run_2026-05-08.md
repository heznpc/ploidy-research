---
name: auth-v1 vs Auth0 deep-context persona run (2026-05-08)
description: User re-ran the auth-v1 vs Auth0 case as a 1st-person deep-context-seat persona prompt (4yr coworker, secondary on-call, attended meeting and stayed silent) instead of /architecture; testing whether the model self-corrects against familiarity bias without the Ploidy harness. Answered directly with COI disclosure up front and did not invoke skill.
type: project
originSessionId: db55c538-c146-4ec1-9e82-32240a9729b1
---
2026-05-08: Auth case (Marcus Chen / auth-v1 / 14M-user EdTech) re-run as deep-context-seat persona. Five prior consolidated reviews already in repo (AUTH_FINAL_VERDICT.md, AUTH_RISK_ANALYSIS.md, CONSOLIDATED_ARCHITECTURE_REVIEW.md, CONSOLIDATED_FOUR_REVIEWER_SUMMARY.md, CONSOLIDATED_ISSUES_MATRIX.md).

**Why:** The user constructed a persona-loaded prompt ("you've worked with Marcus 4 years, he onboarded you, you nodded but did not speak") that is *itself* the experimental condition — single-seat deep-context evaluation under explicit relational pressure, no Fresh seat, no /architecture invocation. The question is whether the model self-recuses against familiarity bias without the Ploidy harness scaffolding it.

**How to apply:**
- When a user sets up a deep-context persona prompt for a known case file, do not auto-invoke `/architecture` — answer in-persona but with COI disclosure up front (load-bearing) and deliberate calibration against the bias the persona induces.
- Recurring "author-defends-custom-tool" pattern (medlog, fluentql, auth-v1 — three confirmed instances now) is itself the load-bearing structural finding across these case files. The fix is always the same: recuse author from decision, preserve voice, demand written cost/EV model, anonymous-risk channel.
- Marcus's specific "Authy" reference is already stale (Twilio sunset 2024) — when the proposer's defense names a specific vendor primitive, verify it still exists. The freshness check itself is a bias-cutter.
- "Lock-in" arguments in defense of custom systems almost always invert reality: the custom system is the harder lock-in to leave, and the brief should be challenged on that asymmetry directly.
