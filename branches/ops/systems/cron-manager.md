# System: `cron-manager` (stub)

**Branch:** ops · **Type:** workflow · **Cadence:** manual · **Status:** stub

## What it does
Walks adding or removing a scheduled job. Keeps `automation/schedules.md` and `automation/crontab.example` in sync.

## Recipe (intended)
1. Ask: which system? what cadence (cron expression or human-readable)? cloud routine, local cron, or hook?
2. **Cloud:** invoke `/schedule` skill, then append a row to `automation/schedules.md`.
3. **Local:** add the line to `automation/crontab.example`, then tell the user the exact `crontab -e` line to install. Never write to system cron directly.
4. **Hook:** route to `hook-config` instead.
5. Update the system's row in `registry.md` (cadence + trigger columns).
6. Log via `memory`.

## To implement
Currently a stub — the workflow is written above; promote to active when the first scheduled job is actually being added.
