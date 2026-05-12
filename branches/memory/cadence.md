# Cadence — `memory`

| System | Cadence | Trigger | Notes |
|---|---|---|---|
| ledger maintenance | manual | on-demand | Fires whenever another branch reports a decision worth logging. |
| archive trim | scheduled | cron:quarterly | First day of each quarter — sweep `context/` and `references/` for files untouched in 90+ days. |
