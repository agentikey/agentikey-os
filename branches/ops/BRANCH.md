# Branch: `ops`

## Role
The swappable OPS / CUSTOM slot. Holds systems specific to the current operational mode — typically a client engagement, but also internal-ops modes (e.g., "Q3 launch push"). What this branch contains changes when the active mode changes.

## Scope in
- Engagement-specific or mode-specific workflows that don't generalize across all of Osoto's work
- Operational glue: vault cleanup, skill scaffolding, cron/hook management, sub-agent spawning
- Anything that should be turned off when the engagement ends

## Scope out
- Anything reusable across engagements — promote it to a capability branch via `/stretch`.
- Persisting state — handed to `memory`.

## Active mode
Set in `context/profile.md` under `active_client:`. If no active client, this branch operates in "default" mode and only the always-applicable systems below are enabled.

## Owned systems
| System | Type | Cadence | One-line purpose |
|---|---|---|---|
| vault-cleanup | workflow | scheduled | Periodic tidy of the user's Obsidian (or equivalent) vault — staging → wiki, archive trim, duplicate detection. |
| skill-builder | workflow | manual | Wizard for scaffolding a new `.claude/skills/<name>/SKILL.md` and registering it. |
| cron-manager | workflow | manual | Walks adding/removing rows in `automation/schedules.md` and the matching `crontab.example` line. |
| hook-config | workflow | manual | Walks adding/removing entries in `.claude/settings.json` and documenting them in `automation/hooks.md`. |
| sub-agent-spawn | workflow | manual | Walks creating a new `.claude/agents/<name>.md` plus its `branches/<name>/` folder. |

Each system is currently a **stub** — a one-pager describing intent and the recipe. Promote to full implementations via `/stretch` as need arises.

## Integrations used
- `obsidian` (or whichever vault tool — listed in `tools.md` once wired)
- otherwise filesystem-only

## Handoffs
- **Calls:** `memory` (every decision/registration), `productivity` (when proposing a new skill, `/stretch` does the scoping).
- **Called by:** user directly, or per-client config in `clients/<slug>/ops-overrides.md`.

## Per-client overrides
The active client (from `context/profile.md`) determines which subset of the systems above is enabled. See `clients/_template/ops-overrides.md`.
