# Hooks — Event-Driven Triggers

Documents which Claude Code hooks are wired in `.claude/settings.json` and why. Source of truth is `.claude/settings.json` itself; this file is the human-readable mirror.

## Active hooks

| Event | Matcher | Command | Why |
|---|---|---|---|
| _Stop_ | _—_ | _append session-end timestamp to `archives/session-log.md`_ | _Cheap session telemetry; helps spot how often the OS gets used._ |

(The row above is an example. The shipped `.claude/settings.json` contains one minimal example hook — extend or remove as needed.)

## How to add a hook
Route through the `ops` branch's `hook-config` system. The recipe is in `branches/ops/systems/hook-config.md`.

## Safety
- No hook should ever run a destructive command silently. If a hook needs to delete or push, it should write to a queue file that the user reviews next session, not act directly.
- Hooks run in the user's shell with the user's permissions — treat any command in `.claude/settings.json` with the same caution as a crontab line.
