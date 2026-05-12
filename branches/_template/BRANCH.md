# Branch: `<name>`

> Copy this folder to `branches/<name>/` and fill in every section. Then add a matching subagent file at `.claude/agents/<name>.md` and register the branch in `registry.md`.

## Role
One sentence: what this branch owns.

## Scope in
- (bullet — a kind of task that belongs here)
- (bullet — another)

## Scope out
- (bullet — explicitly NOT this branch's job; route to the named branch instead)
- (bullet — another)

## Owned systems
| System | Type | Cadence | One-line purpose |
|---|---|---|---|
| _example_ | _skill / workflow / script_ | _manual / scheduled / cloud / hooked_ | _what it does in plain language_ |

## Integrations used
- (pointer to a row in `tools.md`)

## Handoffs
- **Calls:** which other branches this one invokes mid-task
- **Called by:** which other branches invoke this one
