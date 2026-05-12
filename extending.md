# Extending the OS

Three things you can add: a **branch**, a **system**, or a **scheduled job**. Each has a recipe.

---

## Add a new branch

A branch is a role-specialized sub-agent. Add one only when you have a genuine, recurring category of work that doesn't fit any existing branch — not on speculation.

1. Copy the template: `cp -r branches/_template branches/<name>`
2. Fill in `branches/<name>/BRANCH.md` — Role, Scope in/out, Owned systems (start empty), Integrations used, Handoffs.
3. Fill in `branches/<name>/cadence.md` with the recurring triggers (or "none yet").
4. Create the subagent: copy any file in `.claude/agents/` to `.claude/agents/<name>.md`, edit the frontmatter (`name`, `description`) and system prompt so it points at the new branch folder.
5. Add a row in `registry.md` for the branch (one row per system; placeholder row is fine if no systems yet).
6. Append the decision to `ledger.md`: why this branch exists.

---

## Add a new system to an existing branch

A system is a unit of execution: a skill, a workflow doc, or a script.

1. Decide the type:
   - **Skill** — create `.claude/skills/<name>/SKILL.md`. Use when the work is conversational/agentic and benefits from being a slash-command.
   - **Workflow doc** — create `branches/<branch>/systems/<name>.md`. Use when it's a deterministic recipe a human or agent follows.
   - **Script** — create the file under `branches/<branch>/systems/` and ensure `tools.md` lists any external dependency.
2. Add a row to `registry.md`: `branch | system | cadence | trigger | integrations`.
3. Add the system to the branch's `BRANCH.md` "Owned systems" list.
4. If the system has a recurring cadence, also follow "Add a scheduled job" below.

---

## Add a scheduled job

Three paths — pick the one that matches the trigger:

### Path A — Cloud routine (via `/schedule` skill)
Best for: recurring jobs that should run even when your laptop is asleep.
1. Run `/schedule` and answer its prompts.
2. After it confirms, append a row to `automation/schedules.md` so the registry stays human-readable.

### Path B — Local cron
Best for: recurring jobs that only need to run when your machine is on, with full access to your local filesystem/tools.
1. Add the desired line to `automation/crontab.example` (so it's documented).
2. Install it via `crontab -e` yourself. The OS does not touch system cron without consent.
3. Append a row to `automation/schedules.md`.

### Path C — Event hook
Best for: triggers tied to Claude Code session events (Stop, on file save, etc.).
1. Edit `.claude/settings.json` — add the hook.
2. Document the wiring in `automation/hooks.md`.

---

## Per-client OPS overrides

The `ops` branch is the swappable slot. For each client engagement:
1. Copy `clients/_template/` to `clients/<slug>/`.
2. Fill `clients/<slug>/brief.md`.
3. Edit `clients/<slug>/ops-overrides.md` to enable/disable specific OPS systems for that engagement.
4. The conductor reads the active client's overrides at the top of each session — set the active client in `context/profile.md`.
