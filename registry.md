# Registry — The Org Chart

The authoritative map of the OS. The conductor reads this on every session start to know who owns what. `/sweep` reads it to detect drift.

**Cadence values:** `manual` · `skill` · `scheduled` (local cron) · `cloud` (remote routine) · `hooked` (event) · `custom`

**Trigger values:** `on-demand` · `slash-command` · `cron:<expr>` · `schedule:<name>` · `hook:<event>` · `client-config`

| Branch | System | Type | Cadence | Trigger | Integrations | Status |
|---|---|---|---|---|---|---|
| memory | ledger maintenance | workflow | manual | on-demand | — | active |
| memory | archive trim | workflow | scheduled | cron:quarterly | — | planned |
| productivity | /launch | skill | manual | slash-command | — | active |
| productivity | /sweep | skill | scheduled | schedule:weekly | — | active |
| productivity | /stretch | skill | scheduled | schedule:weekly | — | active |
| ops | vault-cleanup | workflow | scheduled | cron:weekly | obsidian | stub |
| ops | skill-builder | workflow | manual | on-demand | — | stub |
| ops | cron-manager | workflow | manual | on-demand | — | stub |
| ops | hook-config | workflow | manual | on-demand | — | stub |
| ops | sub-agent-spawn | workflow | manual | on-demand | — | stub |

**Status legend:** `active` (working today) · `stub` (placeholder spec, no impl) · `planned` (committed, not started) · `retired` (kept for reference only).

Add or remove rows whenever a system is created, completed, or retired. The registry is the source of truth; everything else (CLAUDE.md, BRANCH.md files, schedules.md) is downstream.
