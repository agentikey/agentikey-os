# Branch: `memory`

## Role
Owns the durable knowledge layer. Everything the OS remembers between sessions lives here, and every write to it goes through this branch.

## Scope in
- Read/write to `context/` (identity, voice, priorities, active client)
- Read/write to `references/` (how-to docs, long-lived guides)
- Append to `ledger.md` (every non-trivial decision)
- Move retired files into `archives/`
- Maintain row integrity in `tools.md` and `registry.md` (those files are owned globally but writes are channeled here so the index stays clean)

## Scope out
- Generating new ideas or task plans — that's `productivity`.
- Running scheduled jobs — that's the Automation Layer.
- Talking to external APIs — that's `ops` or a capability branch.

## Owned systems
| System | Type | Cadence | One-line purpose |
|---|---|---|---|
| ledger maintenance | workflow | manual | Append a decision; check format; never edit prior entries. |
| archive trim | workflow | scheduled | Quarterly — move stale files out of `context/` and `references/` into dated subfolder under `archives/`. |

## Integrations used
- none (filesystem only)

## Handoffs
- **Calls:** none — leaf branch.
- **Called by:** every branch that needs to persist a decision or update a registry row.
