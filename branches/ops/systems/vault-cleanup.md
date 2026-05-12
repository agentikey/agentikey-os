# System: `vault-cleanup` (stub)

**Branch:** ops · **Type:** workflow · **Cadence:** scheduled (weekly) · **Status:** stub

## What it does
Tidies the user's primary notes vault (Obsidian by default — generalizes to any filesystem-backed vault).

## Recipe (intended)
1. Walk the vault's staging area (`/raw` or equivalent).
2. For each item, classify: promote → `/wiki`, file → `/projects`, archive, or delete.
3. Detect duplicates and near-duplicates; flag for human review.
4. Trim files in `/wiki` untouched in 180+ days into a dated archive folder.
5. Append a one-line summary to `ledger.md` (via `memory`): files moved, archived, flagged.

## Inputs
- Vault root path (from `tools.md` row for the vault tool)
- Active client overrides (decides whether to run at all)

## Outputs
- Moved/archived files in the vault
- Summary report (stdout when run interactively, or `archives/sweeps/vault-cleanup-YYYY-MM-DD.md` when scheduled)

## To implement
Promote this stub: write the actual logic (script or detailed workflow), add the vault path to `tools.md`, wire a local cron entry in `automation/crontab.example`, and flip the registry status from `stub` to `active`.
