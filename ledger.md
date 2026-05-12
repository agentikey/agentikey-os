# Ledger — Append-Only Decision Record

One entry per non-trivial decision. Newest at the top. Never edit prior entries — supersede them with a new one.

**Format:**

```yaml
- date: YYYY-MM-DD
  decision: one-sentence statement of what was decided
  why: the reason — constraint, deadline, user preference, prior incident
  alternatives: what else was considered and why it lost
  owner: which branch (memory / productivity / ops / ...) or "conductor"
  supersedes: (optional) date of the entry this replaces
```

---

- date: 2026-05-12
  decision: Stand up Agentikey Claude OS at /Users/osoto/AgentikeyClaudeOS with two foundation branches (memory, productivity) and one swappable branch (ops).
  why: Need a multi-branch agent architecture that matches the org-chart mental model; one Claude session reading everything doesn't scale and doesn't isolate context per role.
  alternatives: Single-session OS with no branches (too coupled); every capability branch from day one (premature — add via /stretch when needed).
  owner: conductor
