---
name: bang-skill
description: Use when starting work in any repo or folder, when the project's topic, scope, data, or pipeline changes, when the user assigns tasks to the agent, or when an action could delete a database, code, files, or the project.
---

# bang-skill

Keeps every repo self-describing for any coding agent: `Project_proposal.md` (what the project is), `task_board.md` (what the AI was asked to do), `Process_phases/` (how the work went, one file per major phase).

## Rule 0 — NEVER delete without the user's confirmation

**Do not delete databases, code, or the project unless the user explicitly confirmed that exact action in this session.**

Covered: `DROP` / `TRUNCATE` / `DELETE` without `WHERE`, deleting DB files or data volumes, destructive migration reset/rollback, `rm -rf`, deleting files, folders or branches, `git reset --hard`, `git clean -fd`, `git push --force`, overwriting or emptying user files.

Before any of these: state exactly what would be deleted and the consequence, ask, wait. No answer = no action. One approval covers only that one action. Log each approved deletion in the current phase Work log (what, who approved, when).

| Red flag thought | Reality |
|---|---|
| "It's just temp/old files" | Ask. |
| "It can be regenerated" | Ask. |
| "The user said clean up" | "Clean up" is not approval to delete specific things. List them, ask. |
| "Faster to reset the DB" | Ask. |

## Step 1 — Ponytail ultra

If `ponytail:ponytail` is not in your available skills, tell the user to install it, then stop:
```
/plugin marketplace add DietrichGebert/ponytail
/plugin install ponytail@ponytail
```
(two separate prompts; other agents: https://github.com/DietrichGebert/ponytail/blob/main/INSTALL.md). Non-Claude agents without ponytail may continue without it.

Otherwise invoke `ponytail:ponytail` with argument `ultra`. Ultra's pushback goes into the proposal's "Open questions / Challenges" section; it does not block creating the files.

## Step 2 — First run? (`Project_proposal.md` missing at repo root)

Templates live in `templates/` next to this file. Headings stay English; write content in the user's language.

1. Scan: README, manifests (package.json, pyproject, go.mod, ...), directory tree, entry points, data folders, config, `git log -20`. Read deep only at entry points.
2. Write `Project_proposal.md` from `templates/Project_proposal.md`. Unknown facts -> write "unknown", add to Open questions. Never invent.
3. Write `task_board.md` from `templates/task_board.md`. Add tasks found (user requests, TODOs, open issues). T-000 = this bootstrap, in Done.
4. Create `Process_phases/README.md` (`templates/Process_phases_README.md`) and `Process_phases/01_<phase>.md` (`templates/phase_template.md`). You name the current phase from the repo's state.
5. Append `templates/agent_rules_block.md` to `CLAUDE.md` and `AGENTS.md` at repo root (create if missing). Skip a file that already contains `<!-- bang-skill:start -->`.

If any of these files already exist, update them in place; never overwrite.

## Step 3 — Every later run / every session

| Event | Update |
|---|---|
| Topic, scope, data, or pipeline changed | That section of `Project_proposal.md` + one Changelog row per area; fix the current phase's Goal/Scope/Exit criteria if now stale; add ultra pushback to Open questions |
| Task assigned or status changed | Its row in `task_board.md` (+ `Updated` date); dropped tasks -> `cancelled: <reason>` in Done |
| Work done | One Work log line in the current phase file |
| Phase exit criteria met | Close phase (Status, Ended), open `NN+1_<phase>.md`, update `Process_phases/README.md` |

## Common mistakes
- Rewriting a whole file for a small change -> edit only the affected rows/sections.
- Inserting the rules block twice -> check for the marker first.
- Changing scope/data/pipeline without a Changelog row.
- Deleting rows from the task board -> move them to Done instead.
