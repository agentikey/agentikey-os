# Branch: `productivity`

## Role
Owns the operator-facing skills that keep the OS itself healthy and growing — onboarding, periodic health checks, and the leverage-finder that ships new automations.

## Scope in
- The three foundation skills: `/launch`, `/sweep`, `/stretch`
- Personal task triage (when a `TASKS.md` is added later, this branch owns it)
- Scoping new systems before they get built (autonomy level, owner branch, cadence)

## Scope out
- Persisting the decisions it makes — handed to `memory`.
- Running the systems it scopes — handed to the appropriate owning branch.
- Domain-specific work (research, content, finance, etc.) — those belong to capability branches added via `/stretch`.

## Owned systems
| System | Type | Cadence | One-line purpose |
|---|---|---|---|
| /launch | skill | manual | First-run onboarding wizard; reads `intake.md`, populates `context/`, seeds `tools.md`. |
| /sweep | skill | scheduled | Weekly health check; reads `registry.md` + `CLAUDE.md` + `tools.md`, scores four dimensions, returns top-3 fixes. |
| /stretch | skill | scheduled | Weekly leverage interview; surfaces 1–3 automation candidates, scopes one, ships a single artifact + ledger entry. |

## Integrations used
- none (operates on local repo only)

## Handoffs
- **Calls:** `memory` (to append decisions, update tools/registry rows).
- **Called by:** user directly via slash-command, or the Automation Layer via scheduled trigger.
