# System: `hook-config` (stub)

**Branch:** ops · **Type:** workflow · **Cadence:** manual · **Status:** stub

## What it does
Adds, edits, or removes a Claude Code hook in `.claude/settings.json` and keeps `automation/hooks.md` in sync.

## Recipe (intended)
1. Ask: which event (`Stop`, `PreToolUse`, `PostToolUse`, etc.)? matcher? command to run?
2. Edit `.claude/settings.json` — add the entry under the right event key. Confirm the JSON is valid.
3. Document the hook in `automation/hooks.md`: name, event, what it does, why.
4. Log via `memory`.

## Safety
- Never silently overwrite an existing hook — ask first.
- Never add a hook that auto-runs destructive operations.

## To implement
Currently a stub. Promote when the first hook is being added.
