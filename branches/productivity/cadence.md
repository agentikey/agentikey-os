# Cadence — `productivity`

| System | Cadence | Trigger | Notes |
|---|---|---|---|
| /launch | manual | slash-command | One-time on a fresh install; idempotent on re-run. |
| /sweep | scheduled | schedule:weekly | Recommended: Monday morning. Run via `/schedule` skill (cloud routine) or local cron. |
| /stretch | scheduled | schedule:weekly | Recommended: Friday afternoon. Pair with the week's `/sweep` output. |
