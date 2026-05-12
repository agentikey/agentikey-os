# System: `sub-agent-spawn` (stub)

**Branch:** ops · **Type:** workflow · **Cadence:** manual · **Status:** stub

## What it does
Scaffolds a new branch — both the `branches/<name>/` folder and the matching `.claude/agents/<name>.md` subagent definition — so the conductor can immediately route to it.

## When to invoke
Only after `/stretch` has confirmed that a recurring category of work justifies a whole new branch. Adding a branch on speculation is an anti-pattern; this system gates against that by requiring a recent `ledger.md` entry from `/stretch` that named the branch.

## Recipe (intended)
1. Confirm the prerequisite ledger entry exists.
2. Ask: branch name, role sentence, scope in/out, initial owned systems (can be empty).
3. Copy `branches/_template/` → `branches/<name>/`, fill `BRANCH.md` and `cadence.md`.
4. Copy an existing `.claude/agents/*.md` → `.claude/agents/<name>.md`, edit frontmatter + system prompt.
5. Add the branch's rows to `registry.md`.
6. Append a `CLAUDE.md` summary table update if needed.
7. Log via `memory`.

## To implement
Currently a stub. Promote when adding the first capability branch (likely Research or Content, once a real workflow demands it).
