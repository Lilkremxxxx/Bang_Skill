# bang-skill (for any coding agent)

Copy this file into a project root, or tell your agent: "follow AGENTS.md".

## Rule 0 — NEVER delete without the user's confirmation
Do not delete databases, code, or the project unless the user explicitly confirmed that exact action in this session. This covers `DROP`/`TRUNCATE`/`DELETE` without `WHERE`, deleting DB files or data volumes, destructive migration resets, `rm -rf`, deleting files/folders/branches, `git reset --hard`, `git clean -fd`, `git push --force`, and overwriting or emptying user files. State exactly what would be deleted and the consequence, ask, wait. One approval covers one action only.

## Workflow
The full workflow is `skills/bang-skill/SKILL.md`; the templates are in `skills/bang-skill/templates/`. If they are not in this project, read them from:
- https://raw.githubusercontent.com/Lilkremxxxx/Bang_Skill/main/skills/bang-skill/SKILL.md
- https://raw.githubusercontent.com/Lilkremxxxx/Bang_Skill/main/skills/bang-skill/templates/ (`Project_proposal.md`, `task_board.md`, `Process_phases_README.md`, `phase_template.md`, `agent_rules_block.md`)

In short:
1. If the ponytail skill is available, work in ponytail ultra mode (install: https://github.com/DietrichGebert/ponytail/blob/main/INSTALL.md). Otherwise continue without it.
2. First run (no `Project_proposal.md` at repo root): scan the repo, then create `Project_proposal.md`, `task_board.md`, `Process_phases/README.md` + `Process_phases/01_<phase>.md` from the templates, and append the rules block to `CLAUDE.md` and `AGENTS.md` (skip if `<!-- bang-skill:start -->` already present).
3. Later: topic/scope/data/pipeline change -> update the proposal + Changelog row; task change -> update `task_board.md`; work done -> Work log line in the current phase; phase done -> open the next phase file.
4. Always edit these files in place; never overwrite them.
