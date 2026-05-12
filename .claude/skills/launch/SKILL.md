---
name: launch
description: First-run onboarding wizard for Agentikey Claude OS. Walks the questionnaire in intake.md, populates context/ (profile.md, voice.md, priorities.md), seeds rows in tools.md, and logs the launch event to ledger.md. Idempotent — on re-run, detects existing answers and prompts only for gaps or changes. Use on a fresh install, or when the user says "onboard me", "set up the OS", or "fill in my intake".
---

# /launch — First-run onboarding

## Purpose
Stand up the durable knowledge layer so the rest of the OS has something to read.

## Inputs
- `intake.md` — the 7-question source of truth. May be pre-filled or blank.
- Whatever already exists in `context/` (so re-runs are non-destructive).

## Steps

1. **Read `intake.md`.** For each question, classify the answer field as `filled` or `empty`.

2. **Read `context/`** for any of `profile.md`, `voice.md`, `priorities.md` that already exist. If a file exists and is non-empty, treat its corresponding intake question as already answered — don't re-prompt unless the user says they want to update.

3. **For each unanswered question**, ask the user. One question at a time. Use the exact wording from `intake.md`. Accept raw paste for voice samples — do not paraphrase.

4. **Write `context/profile.md`** with: identity/offer (Q1), priorities (Q3 → also goes in priorities.md), how-you-make-money (Q4), channels & tools list (Q5), top pain (Q6), task tracker (Q7), and an `active_client:` field (default: `none`).

5. **Write `context/voice.md`** with the raw voice samples from Q2, each in a separate `## Sample N` section.

6. **Write `context/priorities.md`** with just Q3 — 1–3 priorities, each as a header with one bullet of detail.

7. **Seed `tools.md`** with one row per tool listed in Q5. Mechanism column defaults to `not-yet-connected` for everything; the user wires real mechanisms later.

8. **Append to `intake.md`** the answers in-place under each question (so the file becomes self-documenting going forward).

9. **Log the launch** by appending an entry to `ledger.md` via the `memory` branch. Decision: "Ran /launch and populated context/." Owner: `productivity`.

10. **Print a summary** to the user: what got written, what's still empty, and the suggested next move (`/sweep` after a few days; `/stretch` weekly).

## Idempotency
- Re-running `/launch` when everything is filled: report "all 7 answered, nothing to do" and exit.
- Re-running with one stale answer: prompt only for that one.
- Never delete or overwrite a filled answer without explicit user confirmation.

## Outputs
- `context/profile.md`, `context/voice.md`, `context/priorities.md`
- Updated `tools.md` rows
- Updated `intake.md` (answers filled in)
- One new entry in `ledger.md`
