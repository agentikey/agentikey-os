# Schedules — Human-Readable Registry

Every recurring job, regardless of how it's triggered (cloud routine, local cron, or hook). Mirrors what's actually installed. Update this when you add or remove a schedule via `cron-manager` or `hook-config`.

| Name | System | Path | Cadence | Trigger detail | Status |
|---|---|---|---|---|---|
| _example_ | _/sweep_ | _.claude/skills/sweep_ | _weekly_ | _cron:0 9 * * 1 (Mon 9am local)_ | _planned_ |

**Status legend:** `installed` (live), `planned` (decided, not installed), `paused`, `retired`.

For each `cron:*` row, the matching crontab line should appear in `automation/crontab.example`. For each `hook:*` row, the matching settings.json entry should be documented in `automation/hooks.md`.
