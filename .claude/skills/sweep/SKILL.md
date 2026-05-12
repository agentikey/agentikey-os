---
name: sweep
description: Weekly health check for Agentikey Claude OS. Reads registry.md, CLAUDE.md, tools.md, and the branches/ tree, scores four dimensions (knowledge, tooling, capability, cadence) on a 0–25 scale each, and returns the top 3 gap-ranked fixes. Read-only except for writing a dated report to archives/sweeps/. Use weekly, or whenever the user says "audit the OS", "sweep", "is my OS working", or "find gaps".
---

# /sweep — OS Health Check

## Purpose
Surface structural drift before it compounds. Score what's in place, name the top three gaps, recommend the next move.

## Inputs (all read-only)
- `registry.md` — the org chart
- `CLAUDE.md` — conductor manual
- `tools.md` — integrations registry
- `branches/*/BRANCH.md` and `branches/*/cadence.md`
- `automation/schedules.md`
- `ledger.md` — for recency signal
- `clients/<active>/ops-overrides.md` if an active client is set

## The four dimensions

Each scored 0–25:

### Knowledge (0–25)
Is the durable layer populated and current?
- Are all 7 intake answers in `context/`? (5)
- Voice samples present and not stale? (5)
- Priorities updated within last 30 days? (5)
- `references/` has at least one entry per tool that has a non-trivial wiring? (5)
- `ledger.md` has activity within the last 14 days? (5)

### Tooling (0–25)
Are external tools registered and reachable?
- Every tool used by any branch appears in `tools.md`? (10)
- Every `tools.md` row has a non-`not-yet-connected` mechanism? (10)
- Every row's `last checked` is within 60 days? (5)

### Capability (0–25)
Are branches and systems coherent?
- Every branch listed in `CLAUDE.md` has a folder in `branches/` and an agent in `.claude/agents/`? (10)
- Every system in `registry.md` appears in its branch's `BRANCH.md` "Owned systems" table (and vice versa)? (10)
- No system is marked `stub` for more than 60 days without movement? (5)

### Cadence (0–25)
Is the OS being used?
- Every `scheduled`/`cloud` system in `registry.md` appears in `automation/schedules.md` with status `installed`? (10)
- Recent `archives/sweeps/` shows the last sweep was within 14 days? (5)
- Recent `archives/stretches/` shows the last stretch was within 14 days? (5)
- `ledger.md` shows at least 2 entries in the last 30 days? (5)

## Steps

1. Score each dimension. Show the math, not just the totals.
2. List specific deductions (e.g., "Tooling −10: 4 of 7 tools.md rows still `not-yet-connected`").
3. Rank the top 3 fixes by leverage: which one, if shipped this week, would raise the most points?
4. Write the full report to `archives/sweeps/YYYY-MM-DD.md`.
5. Print a 5-line summary to the user: scores, total /100, top fix.

## Outputs
- One report at `archives/sweeps/YYYY-MM-DD.md`
- Stdout summary
- Optional: a ledger entry only if the user accepts a top-fix as the week's `/stretch` target.

## What this skill does NOT do
- Doesn't modify anything except the report file.
- Doesn't propose new branches — that's `/stretch`.
- Doesn't email or notify — wrap with a hook or cron if you want that.
