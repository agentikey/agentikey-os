# System: `skill-builder` (stub)

**Branch:** ops · **Type:** workflow · **Cadence:** manual · **Status:** stub

## What it does
Scaffolds a new Claude skill: creates `.claude/skills/<name>/SKILL.md` with the right frontmatter and a template body, registers it in `registry.md`, and adds it to the appropriate branch's `BRANCH.md`.

## Recipe (intended)
1. Ask the user: skill name (kebab-case), one-sentence purpose, owning branch, when-to-invoke description.
2. Create the directory and `SKILL.md` with frontmatter: `name`, `description`.
3. Stub the body: short overview, inputs, steps, outputs.
4. Add a row to `registry.md`.
5. Append to the owning branch's `BRANCH.md` "Owned systems" table.
6. Log via `memory`.

## To implement
Currently a stub. Promote when the first user-built skill is being added — at that point the script/workflow has a real target to test against.
