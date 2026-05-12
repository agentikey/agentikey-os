# OPS Overrides — `<client-name>`

Which systems in the `ops` branch are active for this engagement. The conductor reads this whenever the active client is set.

| System | Enabled? | Notes |
|---|---|---|
| vault-cleanup | no | _e.g., "client has their own vault tooling — leave alone"_ |
| skill-builder | yes | _always-on if you build skills mid-engagement_ |
| cron-manager | yes | _ditto_ |
| hook-config | yes | _ditto_ |
| sub-agent-spawn | no | _new branches gated by /stretch, not per-client_ |

Add client-specific systems below by appending rows AND adding the system file under `branches/ops/systems/` (or a dedicated `clients/<slug>/systems/` folder if it's truly engagement-only).
