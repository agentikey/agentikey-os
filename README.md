# Agentikey Claude OS

A personal Agentic Operating System. Claude Code is the conductor; specialized branches do the work; an automation layer wakes them on cadence; integrations sit at the bottom.

## The Shape

```
                          ┌──────────────────┐
                          │       USER       │
                          └────────┬─────────┘
                                   │
                          ┌────────▼─────────┐
                          │    CONDUCTOR     │  ← parent Claude Code session (CLAUDE.md)
                          └────────┬─────────┘
                                   │ delegates via Agent tool
       ┌───────────────┬───────────┴───────────┬───────────────┐
       │               │                       │               │
  ┌────▼────┐    ┌─────▼─────┐           ┌─────▼─────┐   ┌─────▼─────┐
  │ MEMORY  │    │PRODUCTIVTY│           │    OPS    │   │   ...     │
  │foundation│   │foundation │           │ swappable │   │  (future) │
  └────┬────┘    └─────┬─────┘           └─────┬─────┘   └───────────┘
       │               │                       │
       │ owns          │ owns                  │ owns
       ▼               ▼                       ▼
  context/         /launch                vault-cleanup
  references/      /sweep                 skill-builder
  ledger.md        /stretch               cron-manager
  archives/        task ops               hook-config
                                          sub-agent-spawn

                          ─── AUTOMATION LAYER ───
                  schedule skill • local cron • hooks

                          ─── INTEGRATIONS ───
                       tools registered in tools.md
```

## How Routing Works

1. User speaks to the **Conductor** (Claude Code at the repo root).
2. Conductor reads [registry.md](registry.md) — the org chart in a table — to find the **branch** that owns the task.
3. Conductor invokes that branch's subagent via the `Agent` tool. Subagent definitions live in `.claude/agents/`.
4. The branch runs one or more of its **systems** — a skill, workflow doc, or script under `branches/<branch>/systems/`.
5. Cross-branch tasks: the conductor stays in the loop and calls multiple subagents in turn, synthesizing the result itself.
6. Writes to the durable layer (`context/`, `ledger.md`, `tools.md`) are always mediated by the **memory** branch so the index stays clean.

## First Run

```bash
cd /Users/osoto/AgentikeyClaudeOS
claude
> /launch
```

`/launch` walks the intake in [intake.md](intake.md) and seeds `context/`. After that, run `/sweep` weekly to check health and `/stretch` weekly to find one new automation to ship.

## Layout

- [CLAUDE.md](CLAUDE.md) — conductor manual + routing protocol (loads every session)
- [registry.md](registry.md) — the authoritative org chart
- [intake.md](intake.md) — first-run questionnaire
- [tools.md](tools.md) — external integrations registry
- [ledger.md](ledger.md) — append-only decision record
- [extending.md](extending.md) — how to add a branch, system, or scheduled job
- `branches/` — branch definitions and their owned systems
- `clients/` — per-client overrides for the swappable OPS branch
- `automation/` — schedules, crontab examples, hook docs
- `.claude/` — Claude Code config: subagents, skills, settings
