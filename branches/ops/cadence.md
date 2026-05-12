# Cadence — `ops`

| System | Cadence | Trigger | Notes |
|---|---|---|---|
| vault-cleanup | scheduled | cron:weekly | Sundays — only enabled when an active client opts in via overrides. |
| skill-builder | manual | on-demand | Fires when `/stretch` decides a new skill is the right artifact. |
| cron-manager | manual | on-demand | Fires when a new system needs a schedule. |
| hook-config | manual | on-demand | Fires when an event-driven trigger is needed. |
| sub-agent-spawn | manual | on-demand | Fires when a new branch is being added (rare — gate via `/stretch`). |
