---
name: stretch
description: Weekly leverage interview for Agentikey Claude OS. Surfaces 1–3 automation candidates from recent activity, picks ONE, scopes it (owner branch, autonomy level, cadence, artifact type), and ships a single artifact — a new skill, workflow doc, or script — plus a ledger entry. Designed to compound: one shipped artifact per week. Use weekly, or when the user says "what should I automate next", "find me leverage", or "let's level up".
---

# /stretch — Find and Ship One Automation

## Purpose
The OS grows by shipping exactly one artifact per cycle. This skill picks that one.

## Inputs
- Recent `archives/sweeps/` reports (last 30 days)
- `ledger.md` (last 30 days — what has the user been deciding about?)
- `context/priorities.md` (what matters now)
- The user's lived experience this week (asked directly)

## Steps

### Phase 1 — Surface candidates
Ask one open question: **"What did you do this week that you wish you hadn't had to do yourself?"**

From the answer + recent ledger entries + the latest sweep's top-3 fixes, list 1–3 candidates. Each candidate gets:
- One-line description
- Frequency (per day/week/month)
- Annoyance level (1–5)
- Constraint type: am I blocked by skill, time, or context?

If fewer than 1 candidate emerges, ask one more probing question and stop. Don't manufacture leverage that isn't there.

### Phase 2 — Pick one
Score each candidate: `(frequency × annoyance) / (estimated effort to automate)`. Highest score wins. Show the math; let the user override.

### Phase 3 — Scope
For the chosen candidate, decide:
- **Owner branch:** existing branch, or does this need a new one?
- **System type:** skill, workflow doc, or script?
- **Autonomy level:** L0 (manual checklist) → L1 (human-in-loop draft) → L2 (review-then-go) → L3 (fully autonomous on schedule) → L4 (self-modifying)
- **Cadence:** manual / scheduled / cloud / hooked
- **What is ONE artifact** that, shipped this week, makes the next iteration of the task 30%+ faster?

If the scope wants a new branch: confirm with the user, then route to `ops` → `sub-agent-spawn`. If a new skill: route to `ops` → `skill-builder`. If just a workflow doc: write it directly under `branches/<owner>/systems/<name>.md`.

### Phase 4 — Ship
Produce the artifact. One file. Don't gold-plate.

Then:
- Append a row to `registry.md`.
- Append to the owner branch's `BRANCH.md` "Owned systems" table.
- If the cadence is recurring, also append to `automation/schedules.md`.
- Log a ledger entry via `memory`: what was chosen, why it beat the alternatives, what the artifact is.

### Phase 5 — Report
Print a 4-line summary: what was chosen, what was shipped, where it lives, what the next iteration will look like.

## Output
Exactly one new file (the artifact) + registry/branch/schedule row updates + one ledger entry.

## Anti-patterns
- Shipping more than one artifact per run (kills compounding by spreading attention).
- Picking the most-glamorous candidate instead of the highest-leverage one.
- Inventing a new branch when an existing one would do.
- Skipping the ledger entry — that's how future sweeps know what changed.
